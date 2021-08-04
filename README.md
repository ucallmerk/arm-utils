# arm-utils
A collection of cross compiled utilities for arm platforms such as raspberry pi. Tools like iozone.

## Usage
### iozone -a #should let you run all iotests on current filesystem , use --help for more options
### get-edid > /tmp/myedid 
### parse-edid < /tmp/myedid

## How to cross compile and statically link?
### Cross compilation
Download crosscompiler toolchain from linaro https://releases.linaro.org/components/toolchain/binaries/latest-7/armv8l-linux-gnueabihf/
Install the cross compiler.
Edit your makefile to use <.INSTALL_DIR.>/bin/arm-linux-gnueabihf-gcc instead of cc
- Update the line where c-compiler binary is mentioned
  CC   = cc to CC = arm-linux-gnueabihf-gcc //Add installation directory to PATH variable of the bash environment, export PATH=$PATH:<INSTALL_DIR>/bin
Just compile and you should have a cross compiled binary that will work on your arm target system , but it's dynamically linked.

### To statically link
Use linker ocmmand option "-static" in the compilation command or using LDFLAGS=-static.
e.g. gss foo.c -static -o foo
