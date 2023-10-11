# Valgrind Exercise

## Standard install via command-line
```bash
# Configure the project and generate a native build system:
  # Must re-run this command whenever any CMakeLists.txt file has been changed.
  cmake -S ./ -B build/
# Compile and build the project:
  # rebuild only files that are modified since the last build
  cmake --build build/
  # or rebuild everything from scracth
  cmake --build build/ --clean-first
  # to see verbose output, do:
  cmake --build build/ --verbose
# Run program:
  ./build/app/shell-app
# Clean
  cmake --build build/ --target clean
# Clean and start over:
  rm -rf build/
```

## Identified bugs before fix

1. Uninitialized variable 'terminator' used for an if loop
2. std::vector\<int\> * not freed before read is called

## valgrind outputs 

1. results/valgrind_bug_output is the valgrind output before bug fix
2. results/valgrind_bug_fix_output is the valgrind output after bug fix

## Extra Credit

1. if the executable is statically linked, valgrind cannot detect the potential memory leak , and it also detects ghost uninitialized variables.
2. in a statically linked executable, i think valgrind doesnt have a way to intercept malloc and free calls because all of them are contained in a single binary. it might also be detecting random variables in glibc/libc++