# Brutus-debricated

# Brutus has been depricated as of January 2026.

**The development is continued on:** git@gitlab.strw.leidenuniv.nl:spz/brutus-newton.git <br />
**Which can be cloned from:** git@gitlab.strw.leidenuniv.nl:spz/brutus-newton.git <br />

Apologies for the inconvenience. <br />
Simon Portegies Zwart

<HR>
<HR>

Brutus is an N-body code with arbitrary precision and accuracy.
Written as part of the PhD thesis of Tjarda Boekholt <tjardaboekholt@gmail.com>
under the supervision of Simon Portegies Zwart <spz@astronomy.nl> at Leiden Observatory of Leiden University.


Dependencies are the arbitrary-precision libraries:
  gmp		: https://gmplib.org/
  mpfr		: http://www.mpfr.org/
  mpfr c++	: http://www.holoborodko.com/pavel/mpfr/
  mpreal	: https://github.com/advanpix/mpreal/

To build the code:
  1) Adjust the paths in makefile
  2) Type make

mpreal: best is to install it in a separate directory, and include the link to the makefile
        MPRLIB  = $(LOCAL)/src/mpreal
The other packages can be installed through conda.

To Run the code:
  1) specify initial condition in the get_initial_condition() function in main.cpp
  2) in terminal run: ./main.exe file_out t_begin t_end dt e Lw
    file_out = input initial snapshot
    t_begin  = begin time
    t_end    = end time
    dt       = snapshot time interval
    e        = bulirsch-stoer tolerance parameter (1e-6, 1e-8, 1e-10, ...)
    Lw       = number of digits                   (  56,   64,    72, ...)
  output snapshot is stdout and stderr

  mpreal tolerance = argv[1];
  int numBits = atoi(argv[2]);
  mpreal t_begin = argv[3];
  mpreal t_end = argv[4];
  mpreal dt = argv[5];
  int N = atoi(argv[6]);

Example:
%> ./brutus 1.e-2 64 0 1 0.25 16 testcase.txt > data.out

Produces test.out with the snapshots, and the log data to stderr

word_length = int(4*|log10(bs_tolerance)| + 32)