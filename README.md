# Typical CMake Configure

Cross compiling with cmake could be pretty tedious. Normally you have to supply both c/c++ compiler to cmake + export compile target, so your vscode and/or emacs could find targets and stuff.

# Basic Features
- `-f` filters toolchain list
- `-p` passes installation prefix
- `-G` specifies generator (default: ninja)
- `-X` skip g++/clang++ check

# How to

If you want to build something for ARMv4t

```
mkdir build.armv4t
cd build.armv4t

cmake-configure .. -f armv4`
```

# Toolchain detection

`cmake-configure` looks into your `PATH` shell variable and filter all binaries containing `gcc` or `clang` in its path. Then tries to figure out C++ compiler.

You can test detection with `cmake-configure -l ..`

You can use `-f` with `-l`:

```
cmake-configure -l .. -f wine
{prefix: wine, cc: /usr/bin/winegcc-staging, cxx: /usr/bin/wineg++-staging}
```
