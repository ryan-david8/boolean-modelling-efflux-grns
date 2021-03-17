# Dynamic Boolean Modelling of Regulatory Networks.

Python code for the analysis of the dynamics of regulatory networks for bacterial efflux pump acrAB. Module 'matplotlib' are used for visualisation with python.

## Requirements

Before running, ensure you have access to:
- Python (version 3.7.4 used here)
  - Required packages:
    - numpy
    - pandas
    - random
    - csv
    - sys
    - os
    - matplotlib
    - matplotlib.pyplot
    - math
    - scipy.cluster.hierarchy
    - scipy.cluster
    - datetime
    - matplotlib.ticker
    - module_rk (available on Github repository)
    - argparse


## Github files

The analysis proceeds through two files (1) & (2), requiring module (3) for execution:
1) heatmaps.py
2) timeseries.py
3) module_rk.py
4) timeseries-multi-stress.py
5) timeseries-vary-energy.py

--- File 1 ---
** heatmaps.py -- applies energy-dependent Boolean modelling framework to regulatory networks to gather state space data i.e. the accessible transitions for each network state.

--- File 2 ---
** timeseries.py -- applies energy-dependent Boolean modelling framework to regulatory networks to gather time evolution data for the mean activation of each network component.

--- File 3 ---
** module_rk.py -- self-defined functions for executing tasks in (1) & (2).

--- File 4 ---
** timeseries-multi-stress.py -- similarly to File 2, except multiple stress periods are now applied.

--- File 5 ---
** timeseries-vary-energy.py -- similarly to File 2, except the energy level is not constant and can be increased or decreased within the simulation.


The figures in the corresponding manuscript are produced by:
  - Fig 1 -- (schematic plot)
  - Fig 2 -- timeseries.py
  - Fig 3 -- timeseries.py
  - Fig 4 -- heatmaps.py
  - Fig S1 -- (schematic plot)
  - Fig S2 -- timeseries.py
  - Fig S3 -- timeseries.py
  - Fig S4 -- timeseries.py
  - Fig S5 -- timeseries.py
  - Fig S6 -- heatmaps.py
  - Fig S7 -- timeseries-multi-stress.py
  - Fig S8 -- timeseries-vary-energy.py

## Simulation of regulatory network dynamics

--- Getting Started ---

The below steps describe the steps to run the model code with chosen regulatory architecture, update method, update rule and energy levels.

Create a clone of Github files locally on your computer through method (i) or (ii):
- (i) Download directly using the 'Code' --> 'Download' buttons.
- (ii) Open Terminal (on Mac). Change the current working directory to the location where you want the cloned directory. Type git clone, and then paste the HTTPS clone URL found from clicking the 'Code' button. Press Enter. A directory named 'boolean-efflux' will now be found in the specified location. It will look like this:<br/>
```sh
cd <user-specified-location>
git clone https://github.com/StochasticBiology/boolean-efflux.git
Cloning into 'boolean-efflux'...
```

--- Code ---

Invoke heatmaps.py with
```sh
python <path-to-file>/heatmaps.py [motif] [signal_status] [length_index]
```

Invoke timeseries.py with
```sh
python <path-to-file>/timeseries.py [motif] [signal_status] [signal_0] [signal_length] [length_index]
```

Invoke timeseries-multi-stress.py with
```sh
python <path-to-file>/timeseries-multi-stress.py [motif] [length_index]
```

Invoke timeseries-vary-energy.py with
```sh
python <path-to-file>/timeseries-vary-energy.py [motif] [signal_status] [signal_start] [signal_length] [length_index] [direction] [switchpoint]
```

for example
./scripts/timeseries.py ecoli True 15 1 3

Note: When executing timeseries scripts, if signal_status = False, values for signal_0 and signal_length are to be set as 0.

--- Command-line arguments ---

In addition to invoking each python script, they take some of these additional command-line parameters:

[motif] -- motif being considered.

[signal_status] -- tells the script whether the stressor is active or inactive through a boolean input, True or False.

[length_index] -- the length of the simulation. Script will run for 2*10^([length index]) steps, so 2 = 200, 3 = 2000 etc.

[signal_0] -- an integer initialising the starting time-step of a stressor.

[signal_length] -- length of the stressor.

[direction] -- whether the energy level increase from low to high, or decreases from high to low in timeseries-vary-energy.py

[switchpoint] -- time-step when the energy level changes.


--- Data and input files ---

In the 'boolean-efflux' directory, the 'input-data' sub-directory homes the information about the regulatory network(s) that are considered. The files used for *E. coli* and *Salmonella* in the manuscript are included in this repository.

For new regulatory networks, create initial condition and regulatory architecture comma-separted values files, using the example files in the 'input-data' directory for layout help.
   - Initial condition file: If left empty, the script runs through all possible global states (2^M, with M = number of elements in regulatory architecture).
   - Regulatory architecture files: Split into two indivudual files, a node-node and node-edge regulation file respectively.


--- Output files ---

Script will execute and outputs can be found within 'boolean-efflux' directory.

If there are any questions regarding the included files, email ryan.mathbio@gmail.com
