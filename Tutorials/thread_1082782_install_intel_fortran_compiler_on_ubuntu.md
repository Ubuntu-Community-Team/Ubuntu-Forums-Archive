---
title: "install intel fortran compiler on ubuntu"
date: 2009-02-28
forum: Tutorials
---

### Post by byulent on 2009-02-28
First go to the intel web site "http://software.intel.com", click on 'Downloads', 
click on 'Free Non-commercial Downloads', 
click on 'accept', 
click on 'intel fortran compiler professional edition for linux',  
provide an email address where you will receive the serial number,
download the suitable file, for instance 'l_cprof_p_11.0.081.tgz'.
 
On terminal write the following commands and follow the instructions:

1- sudo apt-get install rpm build-essential
2- sudo apt-get install libstdc++6
3- sudo apt-get install ia32-libs
go to the folder which contains the downloaded file and then
4- tar xvzf l_cprof_p_11.0.081.tgz
5- cd l_cprof_p_11.0.081
6- sudo ./install.sh

Follow the installation instructions:

7. choose Option 1 to install Intel Fortran, 
8. choose Option 1 to proceed with a serial number.
9. type in the serial number (case-sensitive) given in the email. (XXXX-XXXXXXXX). Choose 1 for a default install.
10. Press Enter to read the license agreement. The spacebar speeds through this quickly. Type 'accept' to accept the license agreement. 
11. At some point the installation may stop to ask for some 'optional' packages to be installed. Skip this warning.

After the installation is finished go to the terminal and:

12- cd
13- nano .bashrc
the nano editor will open ".bashrc" file, 
go to the end of this file and add the following lines:

PATH="/opt/intel/Compiler/11.0/081/bin/intel64:$PATH"
export PATH
LD_LIBRARY_PATH="/opt/intel/Compiler/11.0/081/lib/intel64:$LD_LIBRARY_PATH"
export LD_LIBRARY_PATH

Note: The lines above are for 64 if you use 32 replace 'intel64' by 'intel32'. As the versions of the compiler change the installation path will change so make sure that you enter the right path in the lines above.

Exit the file by saving the changes. 

let the system read the updated paths by the command:
14- source .bashrc
 
The installation is finished.

Now you can compile (on terminal) your code by the command:

ifort yourcode.f

and run the created executable ('a.out' in this case) by

./a.out


A useful reference thread, which has been used for the preparation of the current thread:
[http://ubuntuforums.org/showthread.php?t=89571](http://ubuntuforums.org/showthread.php?t=89571)

Further information: [http://software.intel.com/en-us/articles/using-intel-compilers-for-linux-with-ubuntu/](http://software.intel.com/en-us/articles/using-intel-compilers-for-linux-with-ubuntu/)

---

### Post by Dougie187 on 2009-03-02
You should also know that this edition is not for use in academia either.

The free version is only for personal use while sitting at home. It is a very limited usage requirement. I think you might want to add something about this into your post.

---

### Post by jugoof on 2009-05-18
Is Ubuntu 8.10 Intrepid Ibex 64-bit supported? I get an error about missing optional pre-requisite

-- operating system type is not supported
-- sytem glibc or kernel version not supported or not detectable
-- binutils version not supported or not detectable

---

### Post by mrphd on 2009-06-02
> **jugoof said:**
> Is Ubuntu 8.10 Intrepid Ibex 64-bit supported? I get an error about missing optional pre-requisite

-- operating system type is not supported
-- sytem glibc or kernel version not supported or not detectable
-- binutils version not supported or not detectable

you can safely ignore these errors, and just proceed with the installation. see, e.g. [http://software.intel.com/en-us/articles/using-intel-compilers-for-linux-with-ubuntu/](http://software.intel.com/en-us/articles/using-intel-compilers-for-linux-with-ubuntu/)

---

### Post by rchasman on 2009-07-06
The instructions were very useful to me. However for the 32 bit installation there are some small corrections.1) For the 32 bit system, one needs libstdc++5 and this can be gotten from synaptic. A gcc version gets installed with it, but that's ok. 2)No need to install ia32-libs. 3)When editing the .bashrc file, one wants  to put in 

    PATH="/opt/intel/Compiler/11.0/083/bin/ia32:$PATH"; export PATH

    LD_LIBRARY_PATH="/opt/intel/Compile/11.0/lib:$LD_LIBRARY_PATH"; export LD_LIBRARY_PATH

---

### Post by yosh_ghoul on 2009-08-29
Sorry, i have the same problem whit intel fortran 11.1 ia32 running Ubuntu 9.04; and i did everything byulent said, but when i run a my program i dont really know if the compiler is runnig. Also when i try to read the manual "~$:man ifort" it doesn't exist, but "~$:ifot -hepl" it shows what i think it's the manual. Before i tried in many ways to run ifort, and the next lines where usefull for one sesion:
:~$ source /opt/intel/Compiler/11.1/046/bin/ifortvars.sh ia32
i really don't know what did i do but it works :)
I have another question, when i saw my program were compiled in my school, some line said: vectorized *.f
but now when i compile in my laptop it doesn't say anything, what does this mean? it's ifort working?
Thank you

---

### Post by ecrisfield on 2009-10-04
Great instructions. As noted, paths change over time. I installed today and the following paths were appropriate:

PATH="/opt/intel/Compiler/11.1/056/bin/ia32:$PATH";export PATH

LD_LIBRARY_PATH="/opt/intel/Compiler/11.1/056/lib/ia32:$LD_LIBRARY_PATH";export LD_LIBRARY_PATH

After you edit the .bashrc type at the command line:

source .bashrc

(I think this just prompts the machine to actually read the edits you just made.)

Thanks for the thread...

Elizabeth

---

### Post by Choragos on 2010-03-08
Even if you're installing the 64 bit version, you still need these libraries, which come with libstdc++5.

libstdc++
libstdc++5
glibc
libgcc

---

### Post by nis17sep on 2010-07-24
hey i have installed intel fortran compiler and also added the path in .bashrc file.

on giving a command to compile like ifort new.for it gives an error - 

/Desktop$ ifort new.for
/opt/intel/Compiler/11.1/064/bin/ia32/fortcom: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
ifort: error #10273: Fatal error in /opt/intel/Compiler/11.1/064/bin/ia32/fortcom, terminated by 0x7f


well m not able to understand that... new to linux plz help :(

---

### Post by UlrihRekkenin on 2010-09-19
> **Choragos said:**
> Even if you're installing the 64 bit version, you still need these libraries, which come with libstdc++5.

libstdc++
libstdc++5
glibc
libgcc


Hi There!


Firstly,
[I][B]sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ia32-libs
[/B][/I] 
Secondly,
I try  [I][B]"sudo apt-get install ibstdc++ (or libstdc++5 or or or glibc or libgcc)"
in terminal I see
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libgcc
[/B][/I]
And in the setup I see 

[I][B]Step no: 4 of 7 | Installation configuration - Missing Critical Pre-requisite
--------------------------------------------------------------------------------
There is one or more critical unresolved issue which prevents installation to
continue. You can fix it without exiting from the installation and re-check. Or
you can quit from the installation, fix it and run the installation again.
--------------------------------------------------------------------------------
Missing critical pre-requisite
-- missing system commands
--------------------------------------------------------------------------------
    1. Show the detailed info about issue(s) [default]
    2. Re-check the pre-requisites

    h. Help
    b. Back to the previous menu
    q. Quit
[/B][/I]
And ***Re-check the pre-requisites*** give me the same result.

I`m sure there is a problem))
Oleg.

---

### Post by someone101 on 2011-04-28
I'm trying to install the most recent Intel fortran compiler on my Ubuntu 10.10. However, I don't seem to be able to install ia32-libs:

$ sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ia32-libs

I still have some ambiguities whether I'm having a 32 or 64 bit system, but it seems to me that I must have ia32-libs in both cases.

I have tried out all the tips from this forum already...

Could someone please give me a hint on how to install ia32-libs on Ubuntu 10.10?

Thank you in advance.

---

### Post by Mrunalinee on 2011-07-22
I have used these instructions and installed the compiler. But I am getting the syntax "command not found" when I tried using ifort.

Please help me to fix the problem..

---

### Post by rapuy on 2011-08-09
This is exactly what I am trying to do right now, but I have a newer version of Unbuntu 11.04 and Interl Fortran Compiler (l_fcompxe_2011.4.191.tgz). I have just installed unbuntu on my computer and I am new to Linux.

I would like to follow the instructions on the first post. But I am not sure if Im doing it right. Is there any pre-requisits before doing the commands in post #1?

Here are some massages in my terminal window.

_______________________________________________________________________
raprap@raprap-eM350:~$ sudo apt-get install rpm build-essential
[sudo] password for raprap: 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package rpm is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'rpm' has no installation candidate
raprap@raprap-eM350:~$ sudo apt-get install libstdc++6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libstdc++6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
raprap@raprap-eM350:~$ sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ia32-libs
__________________________________________________________

Please help.

Thanks.

---

### Post by Morpholinux on 2011-08-12
ok guys, this is very easy
not gonna write everything as it is
took pics! :)
I am running Ubuntu Natty today is 12 -08 -2011
step 0>>
 following code in terminal, how I know?  -> [HTML]http://software.intel.com/en-us/articles/using-intel-compilers-for-linux-with-ubuntu/[/HTML]
>>>>>>>>>>
Ubuntu 11.04  25 May 2011:
These notes are still applicable to Ubuntu 11.04.  Composer XE 2011 (aka version 12.0) prerequisites for Ubuntu Desktop, assuming that gcc and g++ are installed already:
```
apt-get install build-essential
apt-get install gcc-multilib
apt-get install rpm
apt-get install ia32-libs
apt-get install openjdk-6-jre-headless
```

during the install, you can ignore any warnings about the missing Java prerequisite - it may not recognize openjdk-6-jre-headless.
<<<<<<<<<<<
*must say that line 4 is useless

step 1>>
download (http fast internet )Intel® Fortran Composer XE for Linux* (formerly Intel® Fortran Compiler Professional Edition for Linux*) 
* 32 bit (my case)
** code gets sent to your mail account which you must provide

step 2>> 
mv package from ~/Downloads to ~

step 3>>
uncompress the thing 
cd into new dir
run ./install.sh with superpowers

step 4>>
follow instructions

step 5>>
finally write something like
source /opt/intel/composerxe-2011.5.220/bin/compilervars.sh ia32
 in .bashrc
attachment contains pics step by step basis!
good day!

---

### Post by sukantamech on 2011-08-13
Hi..

 I am using 64bit destop. I have just recently installed ifort, Intel composerXE12 on ubuntu 11.04. just after installing, in the next step i have given the following command...
 now i am facing the following  problem during the environment setup...

Please suggest me what to do.....!!!



sukanta@Energy:~$ /opt/intel/composerxe-2011.5.220/bin/compilervars.sh intel64
[: 121: intel64: unexpected operator
[: 121: intel64: unexpected operator
[: 121: intel64: unexpected operator
[: 121: intel64: unexpected operator
[: 121: intel64: unexpected operator
[: 121: intel64: unexpected operator
[: 121: intel64: unexpected operator
[: 121: intel64: unexpected operator

ERROR: Unknown option 'intel64'

Syntax:
  /opt/intel/composerxe-2011.5.220/bin/compilervars.sh <arch> [MKL_interface] [mod]

   <arch> must be one of the following
       ia32         : Set up for IA-32 target
       intel64      : Set up for Intel(R) 64 target
       mic          : Set up for Intel(R) MIC target

   mod (optional) - set path to MKL F95 modules

   MKL_interface (optional) - MKL programming interface for intel64
                              Not applicable without mod
       lp64         : 4 bytes integer (default)
       ilp64        : 8 bytes integer

sukanta@Energy:~$

---

### Post by Morpholinux on 2011-08-13
I am not an expert, but I think you miss the "source" command

/opt/intel/composerxe-2011.5.220/bin/compilervars.sh intel64
source /opt/intel/composerxe-2011.5.220/bin/compilervars.sh intel64


```
murpholinox@eva01:~$ /opt/intel/composerxe-2011.5.220/bin/compilervars.sh ia32
[: 121: ia32: unexpected operator
[: 121: ia32: unexpected operator
[: 121: ia32: unexpected operator
[: 121: ia32: unexpected operator
[: 121: ia32: unexpected operator
[: 121: ia32: unexpected operator
[: 121: ia32: unexpected operator
[: 121: ia32: unexpected operator

ERROR: Unknown option 'ia32'

Syntax:
  /opt/intel/composerxe-2011.5.220/bin/compilervars.sh <arch> [MKL_interface] [mod]

   <arch> must be one of the following
       ia32         : Set up for IA-32 target
       intel64      : Set up for Intel(R) 64 target
       mic          : Set up for Intel(R) MIC target

   mod (optional) - set path to MKL F95 modules

   MKL_interface (optional) - MKL programming interface for intel64
                              Not applicable without mod
       lp64         : 4 bytes integer (default)
       ilp64        : 8 bytes integer

murpholinox@eva01:~$ source /opt/intel/composerxe-2011.5.220/bin/compilervars.sh ia32
murpholinox@eva01:~$ echo $?
0

```
*0 means exit that the exit status of the last command used was successful
  good luck

---

### Post by kourlandreas on 2011-12-08
hello all!i have succesfully installed intel fortran composer xe 2011 in my Ubuntu 10.04 but when i try to compile a program i have all i get is:
/opt/intel/composer_xe_2011_sp1.7.256/compiler/lib/ia32/for_main.o: In function `main':
/export/users/nbtester/x86linux_nightly/branch-12_1/20111012_000000/libdev/frtl/src/libfor/for_main.c:(.text+0x50): undefined reference to `MAIN__
apparently i am missing ipp,arbb and tbb libraries.any ideas how to fix this???thanks in advance

---

### Post by Eleftheria on 2011-12-21
Thanks for the detailed instructions.However,

If I type
   eleftheria@ubuntu:~$ sudo ifort 
I get
   sudo: ifort: command not found

BUT If I type
   eleftheria@ubuntu:~$ source /opt/intel/composer_xe_2011_sp1/bin/compilervars.sh ia32
   eleftheria@ubuntu:~$ ifort
I get
  ifort: command line error: no files specified; for help type "ifort -help"

Do I always have to  first run the source command before I run ifort?
Is there a step I have omitted?

---

### Post by KauP on 2012-03-16
Thanks for your valuable words ecrisfield a.k.a elizabeth, without your updating technique of the .bashrc file my ifort was not compiling. 

Kaushik

---

### Post by Olihargon on 2013-03-14
Hallo!
I'm new here, in ubuntu and in fortran too!

I would like to start working with fortran,
reading this topic you said that there's the non-commercial version
I gone on that website, but I admit that the words:

"[COLOR=#666666][FONT=Verdana]You may be contacted by Intel or an authorized reseller"

[/FONT][/COLOR]are scaring me a little, 
anyone has been contacted for something?

no money to pay for this version, right?

thanks for the answers!

---

