[![Build Status](https://travis-ci.org/pollen-coin/pollen.svg?branch=master)](https://travis-ci.org/pollen-coin/pollen)
# Pollen
Pollen is a [cryptonote](https://cryptonote.org/) based cryptocurrency. 

Read more at [pollen-coin.org](pollen-coin.org)

## Building Pollen 

### On *nix

Dependencies: GCC 4.7.3 or later, CMake 2.8.6 or later, and Boost 1.55.

You may download them from:

* http://gcc.gnu.org/
* http://www.cmake.org/
* http://www.boost.org/
* Alternatively, it may be possible to install them using a package manager.

On Debian/Ubuntu:
`sudo apt-get install build-essential libboost-all-dev`

To build, change to a directory where this file is located, and run `make`. The resulting executables can be found in `build/release/src`.

**Advanced options:**

* Parallel build: run `make -j<number of threads>` instead of `make`.
* Debug build: run `make build-debug`.
* Test suite: run `make test-release` to run tests in addition to building. Running `make test-debug` will do the same to the debug version.
* Building with Clang: it may be possible to use Clang instead of GCC, but this may not work everywhere. To build, run `export CC=clang CXX=clang++` before running `make`.

### On Windows
Dependencies: MSVC 2013 or later, CMake 2.8.6 or later, and Boost 1.55. You may download them from:

* http://www.microsoft.com/
* http://www.cmake.org/
* http://www.boost.org/

To build, change to a directory where this file is located, and run these commands: 
```
mkdir build
cd build
cmake -G "Visual Studio 12 Win64" ..
```

## Running with docker

Dependencies: docker

To build container and source:

`docker build -t pollen .`

To run container:

`docker run -it -v /pollen/chain:/root/.bitpollen -v /pollen/wallet:/wallet -p 31313:31313 pollen`

By default, the container starts the daemon when it runs.  You can adjust the daemon parameters or run other commands by adjusdting the last line of the Dockerfile.

The `-p` flag publishes the P2P port (31313).  You can publish the RPC port by adding `-p 41414:41414`.
