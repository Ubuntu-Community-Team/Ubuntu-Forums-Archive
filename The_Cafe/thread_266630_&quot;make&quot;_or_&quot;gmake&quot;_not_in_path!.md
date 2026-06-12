---
title: "&quot;make&quot; or &quot;gmake&quot; not in path!?"
date: 2006-09-27
forum: The Cafe
---

### Post by radiojef on 2006-09-27
Hey, Im trying to compile qT and im told:
> You don't seem to have 'make' or 'gmake' in your PATH.
Cannot proceed.
 
Here is my current PATH:
> bash: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin: No such file or directory



That last piece of the PATH looks a little wack to me, but I only know enough about the PATH variable to hurt myself. Can someone tell me what needs to be there. and Where make and/or gmake are? When I 'Whereis' them i just get 'make:' What?

---

### Post by croak77 on 2006-09-27
Did you install build-essential

---

### Post by radiojef on 2006-09-27
Hadn't, Did now. Thanks.

---

### Post by offbyte on 2006-11-21
I have the same problem when trying to install postgresql...

and I've installed build-essentials and also the latest make 3.81 through source

but I don't know how to edit my path...

---

### Post by .t. on 2006-11-21
You shouldn't really need to... but it's as simple as:
"export VARIABLE=VALUE"

In your case, it would be:
"export PATH=$PATH:addition"

This keeps the old path intact at the same time, using the old variable as part of the new ($PATH). Variables are accessed by using a $ sign. So, to print the path, run "echo $PATH".

To have any command, such as the above, run at every terminal session, edit ~/.bashrc and add your command in somewhere, say, at the bottom. ;)

---

### Post by newsman on 2006-12-12
initial errors were gmake not found, and gnumake not found.


apparently still no effect

even did sudo aptitude install build-essential

still no effect



ln -s make /usr/bin/gmake


not effect

added
ln -s make /usr/bin/gnumake

command
./COMPILE

new output
./COMPILE: 8: gnumake: not found
gnumake: *** No targets specified and no makefile found.  Stop.
gmake: *** No targets specified and no makefile found.  Stop.
make: *** No targets specified and no makefile found.  Stop.

I am trying to install uisp for tinyos ([www.tinyos.net](www.tinyos.net)) anyone got a method let me know...

---

### Post by newsman on 2006-12-12
what i am trying to do is to run the ./COMPILE command as stated in its install readme file as follows:


Installation for TinyOS-specific uisp:

Execute
  ./COMPILE
(you can run the commands it contains directly if you prefer)

Then:
  make install
(you must be root on Linux to perform this step)

WARNING: if you don't use the COMPILE script, you may get compilation
errors (depending on whether you've installed autoconf/etc, and what
versions you have)

---

### Post by newsman on 2006-12-12
this is what the ./COMPILE script looks like
#!/bin/sh
if [ ! -f .dates-set ]; then
  . ./set-dates
  touch .dates-set
  ./configure
fi

gnumake || gmake || make

---

### Post by newsman on 2006-12-12
i looked ahead and tried to run ./configure without ./COMPILE, i got the following error

./configure
loading cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal-1.4... missing
checking for working autoconf... found
checking for working automake-1.4... missing
checking for working autoheader... found
checking for working makeinfo... missing
checking for gcc... gcc-4.0
checking whether the C compiler (gcc-4.0  ) works... yes
checking whether the C compiler (gcc-4.0  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc-4.0 accepts -g... yes
checking for c++... g++-4.0
checking whether the C++ compiler (g++-4.0  ) works... no
configure: error: installation or configuration problem: C++ compiler cannot create executables.


how do figure this... this is really upsetting me

---

### Post by newsman on 2006-12-12
ok i thought i would try installing something else in meanwhile for tinyos and i tried to install mspggc

i need to do this as root,,,

but if i do sudo INSTALL_DIR=/opt/msp430 ./build-mspgcc install

i get error INSTALL_DIR is not a command......

how do i run ./build-mspgcc install with an setting INSTALL_DIR=/opt/msp430 in sudo mode????

---

### Post by newsman on 2006-12-12
i entered that setting in normal mode INSTALL_DIR=/opt/msp430 and then sudo ./build-mspgcc


and for some reason it worked...it installed a lot of things as well and fetched some programs from ftp sites etc etc

when i came back to ./configure for uisp it was working and it installed when i prompted make install after configuration command.....according to this method,, i didn't use ./COMPILE and didn't require gnumake or gmake thus... strange huh... i think so..

---

### Post by locutus42 on 2007-03-12
yup, that'll work and the reason is because the "sudo" command is expecting the next thing on the line to be either some option/switch or the command/program to run as super-user. A more accurate way to do it all on one line would be like this:

```

INSTALL_DIR=/opt/msp430 ; sudo ./build-mspgcc

```

it sets that INSTALL_DIR environment variable first and then runs the ./build-mspgcc as super-user using your normal login environment, including INSTALL_DIR. Ofcourse, doing it on separate lines also works.

FYI, did you know that you can also install Eclipse and the C/C++ dev kit( Eclipse CDT ) in Ubuntu to develop and debug apps for the TI MSP430 chips? 

The 'tricks' are as follows:
```

1) create a normal managed C/C++ make project
2) in the project Properties -> Tool Settings
2a) change the compiler/linker/assembler to use msp430-xxx and add " -mmcu=msp430xXXXX" on these lines too.
3) in the project Properties -> Build Settings
3a) insert "elf" to the Artifact extension
4) in the Run -> Debug... dialog Create a new Debug project
5) in the Main tab:
5a )set the C/C++ Application to Debug/XXXX.elf ( XXXX is your app name )
6) in the Debugger tab:
6a) set Debugger to "gdb Debugger"
6b) still in the Debugger tab but in its "Debugger Options" section:
6b1) enter the "GDB Debugger:" command, msp430-gdb
6b2) enter the "GDB command file:" as gdbinit (note: I just removed the "." )
7) create a "gdbinit" file at your project level and add one line:
   load Debug/XXXX.elf
(note: XXXX is your application name. Also, you can not put this command in )
( the Eclipse Run->Debug...->(x)Arguments->Program arguments section )
8) outside of eclipse, create the file ~/.gdbinit with the following lines:
  set remoteaddresssize 64
  set remotetimeout 999999
  target remote localhost:2000
  monitor erase all

```

You should now be able to compile, build, and debug TI MSP430 applications in Eclipse.

---

