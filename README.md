# BrownianDipolar

The purpose of this program is to simulate the motion of Brownian particles
in dimensions 2. They
interacting via a soft-sphere potential, some of the particles being driven
by an external force.

## Dependancies
* [Boost](http://www.boost.org/) for program options and gzip compression
* [SFML](http://www.sfml-dev.org/) for on-the-fly visualization of particles
in 2d (can be disabled)

## Compilation
For compiling the source code, your compiler should support
[C++11](http://en.wikipedia.org/wiki/C%2B%2B11) (both
[g++](https://gcc.gnu.org/) and [clang++](http://clang.llvm.org/) do).

The compilation was only tested on Linux. It should in theory also work
on Windows and MacOS.

## Executable files and compilation flags
If the source code is compiled with the `Makefile` provided (and all the
dependancies are met), three executable files are created:
* `brownianDipolar` for simulations in dimension 2
* `brownianDipolar-visu` same as the previous one with on-the-fly
visualization of the system

At the `Makefile` level, this behavior is enabled by compilation flags:
* `-DDIM=d` (with `d` any striclty positive integer) is a mandatory flag
to indicate the dimension of the system
* `-DVISU2D` is an optional flag that enables visualization in dimension 2.

## Use of the program
Arguments to the program can be defined either via the command-line or
via a configuration file.  
The configuration file is defined via `--config`
and should be made of lines of the type `arg=value` (e.g. `particles=40000` or
`gzip=`).

### Mandatory arguments
* `--particles` Number of particles of the system
* `--tracers` Number of particles going to the right
* `--density` Density of the system (1 means on average 1 particle per cube of
unit size)
* `--temperature` Temperature (the mobility being set to 1)
* `--wca` Strength of the WCA potential
* `--dip` Strength of the dipolar potential
* `--temperature` Temperature (the mobility being set to 1)
* `--force` External force (the mobility being set to 1)
* `--timestep` Time step of the simulation
* `--iters` Number of iterations of the simulation

### Export
If the visualization is disabled, it is mandatory to provide at least one of
the following arguments:
* `--mobility` Export data for mobility
* `--correl` Export data for correlations
* `--livepos` Export positions every given number of iterations 

### Optional arguments
* `--thermalization` Number of iterations of thermalization (i.e. without
recording any observable) (`default=0`)
* `--resolution` Resolution for the correlations (`default=0.25`)
* `--sleep` Wait for given number of milliseconds between iteractionsi
(`default=0`)
* `--path` Directory in which the files are saved (`default=Results/`)
* `--fileMobility` (resp. `--fileCorrel`) File name (without directory)
for data for mobility (resp. correlations).
If undefined the file name will be
`BT<dimension>d-<day>-<time>-<6randomCharacters>-<mobility|correl>.dat`
(e.g. `BT2d-20150320-102714-sUfrH-mobility.dat`)
* `--filePos` File name (without directory and extension) for positions
(default format if not defined)
* `--gzip` Compress output with gzip format (useful for the
correlation file if the resolution is small)

### Command-line only arguments
* `--config` Configuration file in which the previous arguments can be read
(if an argument is both in the command-line and in the file, the priority goes
to the command-line)
* `--verbose` Verbose mode
* `--help` Display help message and exit

## License
The code belongs to [Sorbonne Université](http://www.sorbonne-universite.fr/)
and is released under
[CeCILL 2.1](http://www.cecill.info/) license, a
French license similar to and compatible with
[GNU GPL](https://www.gnu.org/licenses/gpl.html). Feel free to modify the
code and redistribute it under either CeCILL or GPL.

* Boost is released under
[Boost Software License](http://www.boost.org/users/license.html).
* SFML is released by Laurent Gomila under
[zlib/png licence](http://www.sfml-dev.org/license.php).
* This repository includes the font Ubuntu Mono Regular (`font.ttf`) released
under [Ubuntu Font Licence](http://font.ubuntu.com/licence/).
