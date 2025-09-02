# Six Degrees of Separation

A Python implementation of the "Six Degrees of Separation" concept, finding the shortest path between two actors through their shared movies using breadth-first search algorithm.

## Overview

This project implements a graph search algorithm to find the minimum number of degrees of separation between two actors in the movie industry. It uses IMDB data to build a graph where actors are nodes and movies are edges, then finds the shortest path between any two actors.

## Features

- **Graph Search Algorithm**: Uses breadth-first search (BFS) to find the shortest path
- **IMDB Data Integration**: Works with real movie and actor data from IMDB
- **Interactive Interface**: Prompts users to input actor names and handles name disambiguation
- **Path Visualization**: Shows the complete chain of connections between actors
- **Flexible Data Sources**: Supports different data directories (small/large datasets)

## How It Works

1. **Data Loading**: Loads actor, movie, and relationship data from CSV files
2. **Graph Construction**: Builds a graph where:
   - Nodes represent actors (people)
   - Edges represent movies that connect actors
3. **Path Finding**: Uses BFS to find the shortest path between two actors
4. **Result Display**: Shows the degrees of separation and the complete connection chain

## Requirements

- Python 3.x
- CSV data files containing:
  - `people.csv`: Actor information (id, name, birth year)
  - `movies.csv`: Movie information (id, title, year)
  - `stars.csv`: Actor-movie relationships (person_id, movie_id)

## Usage

```bash
python degrees.py [directory]
```

- `directory`: Optional parameter specifying the data directory (defaults to "large")

### Example Usage

```bash
python degrees.py
```

The program will prompt you to enter two actor names:

```
Loading data...
Data loaded.
Name: Tom Hanks
Name: Kevin Bacon
2 degrees of separation.
1: Tom Hanks and Gary Sinise starred in Forrest Gump
2: Gary Sinise and Kevin Bacon starred in Apollo 13
```

## Data Structure

The program uses three main data structures:

- **`names`**: Maps actor names to sets of person IDs (handles name disambiguation)
- **`people`**: Maps person IDs to actor information (name, birth year, movies)
- **`movies`**: Maps movie IDs to movie information (title, year, cast)

## Algorithm Details

The shortest path algorithm uses:

- **Breadth-First Search (BFS)**: Ensures the shortest path is found
- **Queue Frontier**: FIFO data structure for BFS implementation
- **Explored Set**: Prevents revisiting already explored nodes
- **Path Reconstruction**: Backtracks from target to source to build the solution

## File Structure

```
├── degrees.py          # Main application logic
├── util.py            # Data structures (Node, StackFrontier, QueueFrontier)
├── README.md          # This file
└── [data_directory]/  # CSV files with IMDB data
    ├── people.csv
    ├── movies.csv
    └── stars.csv
```

## Key Functions

- `load_data(directory)`: Loads CSV data into memory
- `shortest_path(source, target)`: Finds shortest path using BFS
- `person_id_for_name(name)`: Resolves actor names to IDs
- `neighbors_for_person(person_id)`: Finds co-stars for a given actor

## Error Handling

- Handles missing actors gracefully
- Provides disambiguation for actors with similar names
- Manages cases where no connection exists between actors

## License

This project is open source. See the LICENSE file for details.
