# vityarthi_24mim10064
# Autonomous Delivery Agent in a 2D Grid City

## Project Overview
This repository contains **CSA2001 - Fundamentals of AI and ML (Project-Based Learning) Project 1**.  
I designed and implemented an **autonomous delivery agent** that navigates a 2D grid city to deliver packages under constraints of time, cost, and dynamic obstacles.

The agent models:
- **Static obstacles** (walls, buildings).
- **Varying terrain costs** (movement cost ≥ 1).
- **Dynamic moving obstacles** (vehicles/pedestrians with schedules).

The rational agent uses multiple planning strategies:
- **Uninformed Search**: BFS (Breadth-First Search), UCS (Uniform-Cost Search).
- **Informed Search**: A* Search with admissible heuristic.
- **Local Search + Replanning**: Hill-Climbing with Random Restarts.

Dynamic replanning is implemented: when an obstacle blocks the path, the agent detects it and replans in real-time.

---

## Repository Structure
├── maps/
│ ├── map_small.txt
│ ├── map_medium.txt
│ ├── map_large.txt
│ └── map_dynamic.txt
├── dynamic_obstacles/
│ ├── dyn_small.json
│ ├── dyn_medium.json
│ ├── dyn_large.json
│ └── dyn_dynamic.json
├── logs/
│ ├── bfs_log.txt
│ ├── ucs_log.txt
│ ├── astar_log.txt
│ └── hill_log.txt
├── delivery_agent.ipynb #CLI entry point
├── README.md
├── report
├── Screen Recording
└── requirements.txt

---

## Installation
git clone https://github.com/shamanthula24mim10064-hasini/vityarthi_24mim10064.git
cd vityarthi_24mim10064
pip install -r requirements.txt

### Dependencies
- Python 3.8+  
- `numpy`  
- `matplotlib`  

---

## Maps
Each map is represented in a text file with grid dimensions, terrain costs, obstacles, start, and goal.

**Format:**
- `S` = Start  
- `G` = Goal  
- `#` = Obstacle  
- Integer ≥ 1 = Movement cost of the cell  

**Example (map_small.txt):**

5 5
S 1 1 1 1
1 1 1 1 1
1 1 1 1 1
1 1 1 1 1
1 1 1 1 G


---

## Dynamic Obstacles
Dynamic obstacles are described in JSON files, specifying their cyclic paths and start times.

Example from `dyn_small.json`:
[
{"path": [,,,], "start_time": 0}
]
python src/main.py --planner {bfs|ucs|astar|hill} --map maps/{map_file.txt} [--dyn dynamics/{dyn_file.json}]

Example runs:
- BFS on small map:
python src/main.py --planner bfs --map maps/map_small.txt
- A* with dynamic obstacles:
python src/main.py --planner astar --map maps/map_dynamic.txt --dyn dynamics/dyn_dynamic.json

---

## Logs and Replanning Proof
Logs for each run, including path length, planner used, and replanning events, are saved in the `logs/` directory.

Sample log entry:
/content/drive/MyDrive/CSA2001_Project1/maps/map_medium.txt - Planner: astar, Path length: 15, Replanning: Yes

This shows replanning triggered due to moving obstacles.

---

## Experimental Results
- BFS: Simple, finds shortest steps ignoring terrain cost, slow on large maps.  
- UCS: Accounts for terrain cost but slower in node expansion.  
- A*: Fastest with admissible heuristics, optimal paths, best replanning.  
- Hill-Climbing: Suitable for dynamic environments but less optimal paths.

---

## Testing and Reproducibility
No automated tests are currently included.  
Reproducibility is achieved by running planners via CLI on provided maps and dynamic files.

---

## Deliverables Checklist
- Source code (Python with CLI, well documented)  
- Four test maps (`small`, `medium`, `large`, `dynamic`)  
- Four dynamic obstacle files  
- Logs demonstrating dynamic replanning  
- Setup and usage instructions in this README  

---

## Maintainer
**CSA2001 - Fundamentals of AI and ML Project 1**  
Author: *Shamanthula Hasini*  
Institution: *VIT Bhopal University*  

---
<img width="568" height="313" alt="image" src="https://github.com/user-attachments/assets/407f25df-4ab2-4c6e-a834-7f9289cc2b31" />
<img width="864" height="540" alt="image" src="https://github.com/user-attachments/assets/8682ff9c-dbfb-4cca-b9ad-834cb58c171d" />

