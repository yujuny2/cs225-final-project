# Finding The Shortest Path Between Two Airports
*Alyson Chu (alysonc3), Claire Chou (czchou2), Jane Liu (janeliu2), Yu Jun Yam (yujuny2)*


## Leading Question
Given the OpenFlights dataset of airline routes, can we produce a general search tool to evaluate the shortest route between two airports when restricted to using only specified airlines? 

To answer the leading question, we will implement three different algorithms (Breadth First Search, Dijkstra’s Algorithm, and A* Search) that will utilize the OpenFlights Airline Routes data to determine (if there exists) the shortest route between two airports using only specified airlines. The route may contain other airports, as long as the start and end destinations are of the source and destination airports respectively. The two airports, the allowed airlines, and the type of algorithm used to determine the route are user-specified. The program will also inform the user if a route cannot be found.

## Data Acquisition and Processing
### Data Format
Our input dataset is the OpenFlights/ Airline Route Mapper Route Database. The data represents the routes of airlines between airports. The data is in a csv format with 67,663 entries, each representing a directional route of an airline that connects two airports. We will only use the “Airline”, “Source airport”, “Destination airport” from each entry for our general search tool. 
### Data Correction
We will first clean the input data line by line. Each line represents an entry, with information separated by commas. There is a possibility that the OpenFlights IDs (Airline/ Source airport/ Destination airport) are left as a NULL value, so to avoid relying on the inconsistent OpenFlights IDs, we will assign our own IDs to the airlines and airports. If the actual Airline/ Source airport/ Destination airport information is missing in an entry (left as NULL), then that entry will be excluded. The final output after correcting the data will be a csv that only includes valid entries, with their OpenFlight IDs replaced with the IDs we assigned. Another output will also be generated which specifies the IDs that are mapped to the airlines and airports.
### Data Storage
As discussed previously, we will parse the input data set line by line to build a directed pseudo-adjacency matrix. In the adjacency matrix, the column index will represent the source airport and the row index will represent the destination airports. However, instead of an integer value, each element of the matrix will reference all the airlines connecting the source airport to the destination airport. The amount of airlines that connect a source airport to a destination airport represents the weight of that element in the adjacency matrix. The estimated total storage costs for our dataset is O(n^3).

## Graph Algorithms
We will use the Breadth First Search, Dijkstra’s Algorithm, and A* Search algorithms to answer the leading question. They will all use the adjacency matrix built from the previous data processing steps.
### Function Inputs
All the algorithms will be implemented through three main functions (one function consolidating sub-functions for each algorithm). The inputs will be the Airline codes, Source Airport ID, and Destination Airport ID. The user will specify the airline, source airport, and destination airport through their codes, but there will be an intermediary that converts the airport codes to their assigned IDs before being passed to the algorithms.
### Function Outputs
The output will be the shortest route from the source airport to the destination airport using only the specified airlines. The route will be a vector including the intermediary airports and the airline that was used to reach the airport.
### Function Efficiency
These are the following target Big O efficiencies that we would like to achieve: <br />
Breadth First Search: O(V+E) <br />
Dijkstra’s Shortest Path Algorithm: O(|E| + |V|log|V|) <br />
A* Search Algorithm: O(|E|) = O(b^d) with b as the branching factor and d as the depth of the search


## Timeline
We have established checkpoints for progress we’d like to achieve before each Friday.

### November 4
- Establish the github and create the branches for each of the algorithms we want to implement
- Begin efforts of correcting the data
- Research the algorithms and assign them to team members
- Begin drafting pseudocode for the selected algorithms and the overall structure of the program

### November 11
- Finish correcting the data, and use this processed data to construct our adjacency matrix, adjacency matrix should be saved in an output file to be used in the algorithms
- Finish researching (if needed) and drafting pseudocode of the selected algorithms

### November 18
- Finish implementation of the BFS algorithm, be close to finalizing the other algorithms
- Finish tests for the BFS algorithm
- Begin combining the algorithms and factoring in user input

### November 25
- Finish all the algorithms
- Finish the descriptive ReadMe
- Begin the written report and final presentation

### December 2
- Wrap up the code deliverables
- Finish the written report
- Finish the final presentation
