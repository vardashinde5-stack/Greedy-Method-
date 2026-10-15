# Experiment No. 5

## Title

**Greedy Method: Dijkstra's Algorithm to Find Single Source Shortest Path**

## Aim

To implement Dijkstra's Algorithm using the Greedy Method to find the shortest paths from a given source vertex to all other vertices in a weighted connected graph and analyze its time and space complexity.

## Program

```c
#include <stdio.h>

#define INF 99999
#define MAX 20

int main()
{
    int n, source;
    int cost[MAX][MAX];
    int distance[MAX];
    int visited[MAX] = {0};

    printf("Enter number of vertices: ");
    scanf("%d", &n);

    printf("Enter the cost adjacency matrix:\n");

    for (int i = 0; i < n; i++)
    {
        for (int j = 0; j < n; j++)
        {
            scanf("%d", &cost[i][j]);

            if (i != j && cost[i][j] == 0)
                cost[i][j] = INF;
        }
    }

    printf("Enter source vertex (0 to %d): ", n - 1);
    scanf("%d", &source);

    for (int i = 0; i < n; i++)
    {
        distance[i] = cost[source][i];
    }

    distance[source] = 0;
    visited[source] = 1;

    for (int count = 1; count < n; count++)
    {
        int min = INF;
        int next = -1;

        for (int i = 0; i < n; i++)
        {
            if (!visited[i] && distance[i] < min)
            {
                min = distance[i];
                next = i;
            }
        }

        if (next == -1)
            break;

        visited[next] = 1;

        for (int i = 0; i < n; i++)
        {
            if (!visited[i] &&
                cost[next][i] != INF &&
                distance[next] != INF &&
                distance[next] + cost[next][i] < distance[i])
            {
                distance[i] = distance[next] + cost[next][i];
            }
        }
    }

    printf("\nShortest distances from source vertex %d:\n", source);

    for (int i = 0; i < n; i++)
    {
        if (distance[i] == INF)
            printf("Vertex %d: Unreachable\n", i);
        else
            printf("Vertex %d: %d\n", i, distance[i]);
    }

    return 0;
}
```

## Output

The sample terminal output of the Dijkstra's Algorithm program is shown below:

```text
Enter number of vertices: 5
Enter the cost adjacency matrix:
0 10 0 30 100
10 0 50 0 0
0 50 0 20 10
30 0 20 0 60
100 0 10 60 0
Enter source vertex (0 to 4): 0

Shortest distances from source vertex 0:
Vertex 0: 0
Vertex 1: 10
Vertex 2: 50
Vertex 3: 30
Vertex 4: 60
```

**Note:** This is an illustrative sample output. You can replace it with a screenshot of your actual terminal output.

## Algorithm

1. Start the program.
2. Read the number of vertices in the graph.
3. Read the cost adjacency matrix representing the weighted graph.
4. Replace zero values representing missing edges with infinity, except on the diagonal.
5. Read the source vertex.
6. Initialize the distance array using the edge costs from the source vertex.
7. Set the distance of the source vertex to zero and mark it as visited.
8. Find the unvisited vertex with the minimum tentative distance.
9. Mark the selected vertex as visited.
10. Update the distances of its unvisited neighboring vertices if a shorter path is found.
11. Repeat the process until all reachable vertices have been visited or no reachable unvisited vertex remains.
12. Display the shortest distance from the source vertex to every vertex.
13. Stop the program.

## Time Complexity

| **Operation**                       | **Time Complexity** |
| ----------------------------------- | ------------------- |
| Reading the adjacency matrix        | **O(n²)**           |
| Initializing distances              | **O(n)**            |
| Finding the minimum-distance vertex | **O(n²)**           |
| Updating neighboring distances      | **O(n²)**           |
| Overall Time Complexity             | **O(n²)**           |

### Explanation

The program uses an adjacency matrix to represent the graph.

* Reading the adjacency matrix takes **O(n²)** time.
* Initializing the distance array takes **O(n)** time.
* Finding the unvisited vertex with the minimum distance takes **O(n)** time per iteration.
* Updating distances takes **O(n)** time per iteration.

Since the algorithm performs up to `n` iterations, the overall time complexity is:

**Time Complexity = O(n²)**

## Space Complexity

The program uses the following data structures:

* `cost[MAX][MAX]` to store the adjacency matrix.
* `distance[MAX]` to store the shortest distances.
* `visited[MAX]` to track visited vertices.

The adjacency matrix requires **O(n²)** space, while the distance and visited arrays require **O(n)** space each.

Therefore:

**Space Complexity = O(n²)**

## Applications

1. Finding the shortest routes between locations in road networks.
2. Routing packets in computer networks.
3. Finding minimum-cost paths in weighted graphs.
4. Navigation systems and route-planning applications.
5. Network optimization and transportation planning.
6. Solving single-source shortest-path problems.

## Advantages

* Simple and easy to implement.
* Finds the shortest distances from a single source to all reachable vertices.
* Uses the Greedy Method to select the vertex with the minimum tentative distance.
* Efficient for graphs represented using adjacency matrices.
* Suitable for routing and navigation problems.

## Limitations

* Dijkstra's Algorithm does not support graphs containing negative-weight edges.
* The adjacency-matrix implementation requires **O(n²)** time and space.
* It finds shortest distances, but the given program does not display the complete paths.
* The program uses a fixed maximum capacity of 20 vertices.

## Conclusion

Dijkstra's Algorithm is a Greedy Method used to find the single-source shortest paths in a weighted graph with non-negative edge weights. It repeatedly selects the unvisited vertex with the minimum tentative distance and updates the distances of its neighboring vertices.

For the given adjacency-matrix implementation, the overall time complexity is **O(n²)**, and the space complexity is **O(n²)**.

## GitHub Repository

[Add your GitHub repository link here]

## Program File

[Add your Dijkstra's Algorithm C file link here]

## Output Image

<img width="1672" height="941" alt="dijakstra" src="https://github.com/user-attachments/assets/fba12031-3908-44cf-9aa2-caf505ce915c" />

