# Diff_Sys_Analysis_App
app for analysis of differential equations of the form dx/dt = f(x), x = [x1, x2, ..., xn], 1&lt;=n&lt;=4 

###Features of the app:

The app allows graphing the nullclines / nullplanes of functions with multiple variables and parameters (1 - 3D, no graph for 4d).
The steady states of the system are searched for numerically and symbolically. They are displayed on the graph
and in a separate section along with the Jacobian and are color coded based on their stability.
Clicking on a steady state button displays it's full coordinates, eigenvalues and stability description.
The graph can be resized to fit in an interval input by the user.
Jacobian and its eigenvalues can be evaluated at any custom point.
The user can input starting coordinates and a time frame to simulate the evolution of variables with time,
displaying the phase plane space graph (2 and 3D) and the variable / time graph.

###Some technical info:

The functions are parsed from user text input and variables and parameters are automatically detected.
Graphing will not start if functions are entered incorrectly (if python can't parse them).
Graphing complex systems can take a moment and the app can be unresponsive during the process, but it is still running.
Roots of the system f(x) = 0 are searched for with sympy's numerical and symbolic methods: sympy.solve & sympy.nsolve .
The starting points for the numerical search start as a grid based on the graphed interval, then are passed to the functions,
and if the values of the evaluated functions are sufficiently close to 0,
they are passed to sympy, so changing the interval will likely change the detected roots.
The symbolic search is limited to execute for at most 15s (2s in 4D case) because in some instances it will begin looking for complex roots
instead of real ones and there may be large / unlimited amount of those.
The trajectories are plotted from the functions by computing gradients and updating the value of the variable at every step.
For small times the number of samples taken is 15000 * time,
and the number decreases for large times to increase performance, down to 4300 * time for time = 999 which is the cap.

###Some issues:

The app will go unresponsive when performing large amount of calculations, but it is still working.
The steady states will not always be detected,
in those cases resizing the graph to increase density of search starting points around the root can help.
The app does not support graphing trajectories with varying parameters, so no steady state switch demonstrations are possible in a single graph,
but they can still be shown piecewise with multiple simulations.
