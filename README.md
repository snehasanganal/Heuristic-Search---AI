**Heurisctic Search**  

**Problem Statement:**  

Multiple bombings have been sighted in different locations in Hyderabad. Each is located at
position (xi, yi), having possible casualty counts of ci. Bomb at each location has a time (ti)
to go off. The city has only a single bomb squad team. The time taken to diffuse a bomb is
constant. The time taken by the team to reach from one place to another place is proportional
to the distance between the two points. Your task is to design a search algorithm with proper
heuristics that may help in minimising the casualty count. Reason out why you have picked
certain heuristics. Analyse the space and time complexity of your algorithm  

**Heuristic Function:**

The heuristic function prioritizes locations with:

- Higher Casualty Counts: Locations with more potential casualties are favoured.
  
- Shorter Travel Distances: Closer locations are preferred to minimize travel time and
maximize the chance of reaching them before detonation.

- Less Remaining Time: Locations with less remaining time have a higher urgency and are
prioritized.

**Explanation:**

- The heuristic calculates a value for each neighbouring location by dividing the casualty
count by the sum of travel distance and 1 (to avoid division by zero).

- For locations other than the starting position, it further reduces the value based on the
remaining time as a fraction of the total blast time. This gives higher priority to locations with
less remaining time relative to their total blast duration.

**Algorithm:**
The provided code implements a Heuristic Search algorithm to find the path that minimises
the total casualty count. Here's a breakdown of the algorithm:

**1. Initialization:**

- Initialize a priority queue (`priority_queue`) to store potential next locations.
  
- Initialize a visited list (`visited`) to track visited locations.
  
- Identify all neighbouring locations (`neighbours`).
  
- Calculate the sum of all casualties (`sum_casualty`).
  
- Set `time_rem` to the initial blast times.
  
- Calculate initial heuristics for all neighbours considering their casualty counts and
distances from the starting position (assumed to be [0,0]).

- Add the initial heuristics with negative values (for max-heap) to the priority queue.
  
  
**2. Iteration:**

- While the priority queue is not empty:
  
- Pop the location with the highest heuristic value (indicating potentially fewer casualties)
from the priority queue.

- Mark the popped location as visited.
  
- Update the remaining time for neighbouring locations based on the distance travelled
from the previous location.

- Calculate new heuristics for remaining neighbours considering their casualty counts,
distances from the current location, and remaining blast times.

- Add the new heuristics with negative values to the priority queue.

- Update the total casualty count by adding the casualty count of the visited location.

**3. Termination:**

- The loop breaks when the priority queue becomes empty (no more neighbours to visit).
  



