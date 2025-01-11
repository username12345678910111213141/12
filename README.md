# 12import random

def echo_maze():
    print("Welcome to Echo Maze!")
    print("Find your way out of the maze using echoes. Listen carefully to the clues!")
    
    # Maze dimensions
    maze_size = 5
    exit_x, exit_y = random.randint(0, maze_size - 1), random.randint(0, maze_size - 1)
    player_x, player_y = random.randint(0, maze_size - 1), random.randint(0, maze_size - 1)
    steps = 0

    def get_echo(player_x, player_y):
        distance = abs(player_x - exit_x) + abs(player_y - exit_y)
        if distance == 0:
            return "You hear no echo. The exit is here!"
        elif distance <= 2:
            return "The echo is sharp and strong nearby."
        elif distance <= 4:
            return "The echo is clear but a bit faint."
        else:
            return "The echo is distant and weak."

    while (player_x, player_y) != (exit_x, exit_y):
        print("\nYou are standing in a pitch-black maze.")
        print(get_echo(player_x, player_y))
        move = input("Move (up/down/left/right): ").strip().lower()

        if move == "up" and player_y > 0:
            player_y -= 1
        elif move == "down" and player_y < maze_size - 1:
            player_y += 1
        elif move == "left" and player_x > 0:
            player_x -= 1
        elif move == "right" and player_x < maze_size - 1:
            player_x += 1
        else:
            print("You hit a wall or went out of bounds. Try a different direction.")
            continue

        steps += 1

    print("\nCongratulations! You found the exit!")
    print(f"It took you {steps} steps to escape the maze.")

# Run the game
echo_maze()

