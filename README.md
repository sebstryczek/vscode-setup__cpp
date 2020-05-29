# vscode-setup__cpp

## Formatting
1. Go to settings of @ext:ms-vscode.cpptools
2. Change: `C_Cpp: Clang_format_fallback Style`
   to: `{ BasedOnStyle: Google, IndentWidth: 4, ColumnLimit: 0}`
Source:
- https://medium.com/@zamhuang/vscode-how-to-customize-c-s-coding-style-in-vscode-ad16d87e93bf

Issues:
MacOS
```
Formatting failed:
/usr/bin/clang -style=file -fallback-style= -assume-filename=/Users/sebastian/Desktop/stryczek/vscode-setup__cpp/src/main.cpp
clang: error: unknown argument: '-style=file'
  clang: error: unknown argument: '-fallback-style='
  clang: error: no input files
```
-- solution:
```
You're using clang, not the GNU gcc, as noted by the output:

/usr/bin/gcc --version
Apple LLVM version 7.3.0 (clang-703.0.31)
libaec is known to have compatibility issues with clang, using the real gcc instead should fix your problem:

brew install gcc
export CC=gcc-9   # Use the version listed in `ls /usr/local/bin/gcc-*`, not clang gcc
export FC=gfortran
make
```

Linters:
- https://marketplace.visualstudio.com/items?itemName=jbenden.c-cpp-flylint
- https://marketplace.visualstudio.com/items?itemName=mine.cpplint
