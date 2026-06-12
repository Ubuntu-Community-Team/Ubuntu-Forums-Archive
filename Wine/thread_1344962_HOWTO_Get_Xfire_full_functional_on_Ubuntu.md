---
title: "HOWTO: Get Xfire full functional on Ubuntu"
date: 2009-12-03
forum: Wine
---

### Post by rocky5051 on 2009-12-03
Ever since Wine version 1.1.31 (I think) a problem with Wine was resolved that was causing newer version of Xfire to crash when you clicked anywhere on the Window. While this is good news for those like me who use Xfire on a daily basis for games and general communication, the fixes only work if GCC 4.5 is used to build the source code. Even worse, 4.5 hasn't even been released yet, and is still being developed.

Obviously this implies that it hasn't been included by most (if any) distros. Several users might find it challenging to build the Wine source code with the development gcc. Several might not even know how to do it!

Even after building Wine with the development gcc version, there is still some other problems that make Xfire a PITA to work with. But, having done this several times I thought I'd put together a HOWTO for others to show how to do it (and that in reality Ubuntu makes it very easy to do this).
[B][I]
Before I begin, I'd like to mention that because this involves using sudo, and implies possible modification of your Ubuntu installation, I claim no responsibility for any damage this procedure may (but probably won't) inflict upon your system, and by following my instructions you accept the risks involved with following them.[/I][/B]

Now with that out of the way, let's begin. :)

**_[SIZE="5"]STEP 1: Prerequisites[/SIZE]_**
The Ubuntu versions I have tested this with are Ubuntu 9.04 and 9.10. These instructions _should_ work with versions as old as Hardy (8.04), but I can't be sure. Wine can be built on 64 bit Ubuntu as well, but there are some extra preparation steps (you will see below).

After this, to get the rest of the build dependencies you can use apt to scan and retrieve a list of them for both gcc and wine. To do this you open a terminal, update your repositories and use the build-dep option for each:

```
sudo apt-get update
sudo apt-get build-dep wine
sudo apt-get build-dep gcc
sudo apt-get build-dep gcc-4.x
sudo apt-get install g++
```

Where "x" is in that code on 'gcc-4.x', replace it with the number that would appear there for the newest available version of gcc for your version of Ubuntu. For example, the latest version available for Karmic (Ubuntu 9.10) is 4.4, so you would put gcc-4.4 there. The reason build-dep must be used for gcc and gcc-4.x separately is due to the fact they obtain different dependencies, all of which are required to build gcc.

You might also need to obtain subversion, which is required to download a trunk build of gcc.

```
sudo apt-get install subversion
```

**64 bit users** will need to fix two problematic libs, libmpg123 and libmpc, before continuing or gcc will fail to build, and Wine will fail to build properly. **32 bit users can skip to STEP 2.**

==libmpc
First, remove libmpc entirely:
```
sudo apt-get remove libmpc libmpc-dev
```

Obtain the latest version and save the archive to your home folder. Open a terminal and use wget to obtain it since the rest of the steps will require a terminal anyway.

```
cd $HOME && wget http://www.multiprecision.org/mpc/download/mpc-0.8.1.tar.gz
```

Extract the archive, change into the source code directory, and make/make install it. This will install the binary libmpc and it's source code.

```
tar -xjf mpc-0.8.1.tar.gz
cd mpc-0.8.1
./configure && make && sudo make install
```

==libmpg123
One of libmpg123's header files are incompatible with the 64 bit environment, and cause wine to fail when building. To resolve this, download (and rename) the patch, then use the patch command to apply the patch to the header file.

You will need to enter the filepath to the header file, when asked. The path to that header file I've included in the next code comment.

```
cd $HOME
wget http://bugs.winehq.org/attachment.cgi?id=24513
mv attachment.cgi?id=24513 mpg123_patch.patch
sudo patch -p1 < mpg123_patch.patch
/usr/include/mpg123.h #Path to enter when prompted
```

This will prevent a compile failure when building wine later on.

**_[SIZE="5"]STEP 2: Get Wine and GCC-4.5[/SIZE]_**
For this tutorial, we will be using the source code for 1.1.33, which can be obtained from SourceForge [here]("http://prdownloads.sourceforge.net/wine/wine-1.1.33.tar.bz2"). Download it, and save it to your Desktop. Then open a terminal, move to your desktop and extract the archive:

```
cd $HOME/Desktop
tar -xjf wine-1.1.33.tar.bz2
```

Next, we need to obtain the gcc devel trunk using subversion. Drop back to your Desktop in the terminal, then enter this command to checkout a snapshot of gcc:

```
svn checkout svn://gcc.gnu.org/svn/gcc/trunk gcc-svn
```

If your internet connection blocks the svn protocol, replace the "svn://" in that line with "http://".

This may take a few minutes. Just be patient, make a sandwich or something while you wait. :popcorn:

By the end of this step, you should have two new folders on your Desktop. One named "gcc-svn", and "wine-1.1.33".


**_[SIZE="5"]STEP 3: Building and Installing GCC[/SIZE]_**

You are now ready to build GCC :). This is fairly simple if you don't have any special needs, but regardless of what you do, building gcc WILL take a long time (hours), especially if you don't have a multi-core/multi-cpu system to run make in parallel mode (explained later).

To compile gcc from the snapshot you've obtained, navigate into the gcc-svn folder in a terminal, create a directory for objects spawned during the build process (suggested by gnu.org to keep the build clean), navigate into that directory, then run the configure script, and make && make install it.

```
cd $HOME/Desktop/gcc-svn
mkdir objdir
cd objdir
.././configure
make
sudo make install
```

NOTE:If you use 64-bit Ubuntu 8.04 (Hardy Heron), you may need to enter the prefix to look for build dependencies. Instead of using the ./configure line above, use this instead:

```
.././configure --prefix=/usr
```

At your option, you can have make build gcc in parallel mode. What this does is utilize multi-threading to build several parts of the code at once. To do this, replace append the make command with the -j switch like this:

```
make -j x
```

Where the x is, replace it with the number of logical cores your cpu(s) have in total. You can set a larger number, but that isn't a necessarily a good idea. (NOTE: This will saturate your cpu big time and slow your system down alot while building). If you have a dual core system, you can effectively cut build time in half using a value of "2".

Also, if the build process ends in error, where the error says it's waiting for the other process to catch up, just run make again and it will continue from where it left off and complete successfully.

After you've make install'd it, the new gcc will be available for use on your system.


**_[SIZE="5"]STEP 4: Building and Installing Wine[/SIZE]_**

This part isn't nearly as complex, but building still may take a good hour to complete. You also need to specify where the gcc binary for your build of gcc is to the configure script, which if you didn't change it when building gcc is at /usr/local/bin

```
cd $HOME/Desktop/wine-1.1.33
./configure CC=/usr/local/bin/gcc
make depend && make
sudo make install
```

At your option, you may also use checkinstall to automatically build a deb package of your build. Just know that checkinstall might not (as it has done to me) include symlinks for various parts of the Wine build and result in a semi-broken installation. If you're willing to try this or just aren't too worried about it, you can give it a try:

```
sudo apt-get install checkinstall
sudo checkinstall
```

For checkinstall, just follow the prompts and fill in information where it asks. It will reinstall Wine, but in a way compatible with dpkg and synaptic so it can be managed with apt and synaptic.

At this point you now have a working build of Wine that will run Xfire properly :). You can also delete the source files you used to build gcc and Wine. This is probably a good idea since both take up a good chunk of space from making binary objects and files.

```
rm -rf $HOME/Desktop/wine-1.1.33
rm -rf $HOME/Desktop/gcc-svn
```

**_[SIZE="5"]STEP 5: Install Xfire on Wine[/SIZE]_**
This part is rather straightforward normally, but you may wish to create a seperate prefix for Xfire, since in STEP 6, should you choose to follow it, you will be using winetricks to install stuff that can occassionally interfere with various applications on Wine. To do so, just run this command:

```
cd $HOME && wineprefixcreate --prefix ~/.XFIREANDGAMES
```

If it wasn't obvious looking at that code, you need to install your games to that prefix as well if you expect Xfire to detect them and work in game. To run any program in that specific prefix, such as the winecfg tool for that prefix, you would do something like this:

```
WINEPREFIX="$HOME/.XFIREANDGAMES" winecfg
```

The format of which is really:

```
WINEPREFIX="/path/to/prefix" [COMMAND]
```

Since some people may not care about intermixing Windows elements with their software, and for the sake of simplicity, I will not mention the WINEPREFIX part in the command, but the commands I do use can be appended with the prefix on your own.

Install xfire by right clicking the installer and choosing to run using Wine Windows Program Launcher, or from terminal (especially if you're using a different prefix than default):

```
cd /path/to/installer
wine xfire_installer_xxxxx.exe
```

Where the xxxxx is, replace it with the number in the actual installers filename. This will start the xfire installer and allow you to install Xfire. (NOTE: The XO toolbar won't work with the native Linux version of Firefox, only the Windows version of Firefox, and possibly IE).

Xfire should now be installed, and can now be run by clicking it's shortcut, or running it from terminal.


**_[SIZE="5"]STEP 6: (Optional) Correct GUI issues.[/SIZE]_**
The xfire friend's list still has a bug that causes it to appear white, but the difference post-fix of Xfire's crash problems is that the names legible, and not as boxes.

However, for people who do not like this, ie6 and the common controls library can be installed with winetricks, which completely resolves the GUI bug. (NOTE: This _may_ make xfire in game fail to work, but won't break detection of running games).

To do this, install cabextract, then download and run the winetricks script, choosing the comctl32 and ie6 options for installation (all in a terminal of course :P):

```
sudo apt-get install cabextract
cd $HOME
wget http://www.kegel.com/wine/winetricks
sh winetricks comctl32 ie6
wineboot -esr

```

Start xfire, log in and you should now have xfire looking like [this]("http://s125.photobucket.com/albums/p63/rockinup1231/?action=view&current=Screenshot-1-1.png").

You can also use winetricks to install Microsoft fonts to further improve the appearance of text in the program, as well as in other software. Just run winetricks without any options, and a window should pop up with an option among others to install them.


**_[SIZE="5"]Conclusion[/SIZE]_**
Xfire works in game for me, as well as voice chat, game recording, normal chat and chatrooms. File transfers too.

However, with in game features, it's proven to be kinda hit and miss depending on the game, though it doesn't seem to depend on whether or not they run Direct3D for their renderer over OpenGL. This seems to be worse after installing comctl32 and ie6 stuff, but it doesn't bother me.

Hope this helps everyone. :D

**_[SIZE="5"]People Who Have Contributed to This in Some Way[/SIZE]_**
misha680
KaoriKandiez

---

### Post by beastrace91 on 2009-12-03
First off - awesome guide! Lack of in game community on Steam is a HUGE annoyance when gaming under Ubuntu for me... so if I can get XFire working that would be awesome :)

Secondly:

> **rocky5051 said:**
> Also, Wine requires certain packages that aren't available for x64 versions of Ubuntu, so Wine won't build without being partly broken on 64 bit systems. As such, you shouldn't try this unless you're on 32 bit.

I've compiled Wine from source several times on my 64bit Ubuntu install and it always works just fine (in fact I'm about 99% sure the .deb files for 64bit Wine have to be compiled on 64bit systems - so it must work for some people...). Would you mind elaborating on why you say this? (That being said I plan to follow this guide on said 64bit system when I get home and will report back if it works or not ;) )

Also - what games do you successfully use the in-game community with? I'd be looking to use it with L4D/TF2/Starcraft personally.

Regards,

---

### Post by rocky5051 on 2009-12-03
Thanks, I'm happy you like it.

And also, Wine is not built natively for 64 bit. Instead when it is installed on x64, several 32 bit compatibility libs are downloaded along with it and installed. It can be built on 32 bit, packaged on 32 bit, and run on both 32 bit and 64 bit, but it doesn't run natively on 64 bit.

Secondly, the last time I built Wine on Ubuntu x64 was with 9.04, and while it _did_ build, there were a few things that didn't get built in. I think mpeg audio support was among them. I suppose it could be done, but it's not the best way to do it. Ultimately, I stick to 32 bit to work with Wine right now.

And as for games (I've played more than these on Wine of course, these I've tried with Xfire), I've tried several. To list some that I can remember...

Call of Duty 1
Trackmania Forever
Age of Mythology
Halo
Alice

And I think that's the only ones I've really attempted to use with Xfire on Wine, but in theory Xfire should at least detect any game run on Wine, granted it runs in the first place. Xfire in game worked well in CoD and Halo, though sometimes it can cause big fps drops. That might be due to the lack of proper video overlay support, but I couldn't tell you for sure.

---

### Post by rocky5051 on 2010-01-19
I'm making some updates (not all of them tonight) to the tutorial, as going over the steps I seemed to have missed some minor details. I've also figured out how to build wine in 64 bit Ubuntu, but this is only for Ubuntu 9.10. The steps I add for x64 users may (and probably won't) be the same for 9.04 users so the best advice I can offer is either test the methods yourself on older Ubuntu versions, or upgrade if you encounter issues.

Namely, the updates address:
-Fixing an error in compiling Wine (stops on an error comping wine mpeg audio support) on 64 bit Ubuntu

-Adding a step to insure the user gets all the gcc build dependencies.

---

### Post by misha680 on 2010-01-19
Dear Sirs or Madams:

Thank you so much. Am trying to compile svn trunk on Ubuntu Hardy 8.04 amd64. I get the following errors on the configure step:
```

checking how to compare bootstrapped objects... cmp --ignore-initial=16 $$f1 $$f2
checking for objdir... .libs
checking for correct version of gmp.h... yes
checking for correct version of mpfr.h... buggy but acceptable
checking for the correct version of mpc.h... no
configure: error: Building GCC requires GMP 4.2+, MPFR 2.3.2+ and MPC 0.8.0+.
Try the --with-gmp, --with-mpfr and/or --with-mpc options to specify
their locations.  Source code for these libraries can be found at
their respective hosting sites as well as at
ftp://gcc.gnu.org/pub/gcc/infrastructure/.  See also
http://gcc.gnu.org/install/prerequisites.html for additional info.  If
you obtained GMP, MPFR and/or MPC from a vendor distribution package,
make sure that you have installed both the libraries and the header
files.  They may be located in separate packages.
make: *** No targets specified and no makefile found.  Stop.
make: *** No targets specified and no makefile found.  Stop.

```

Any ideas?

Thank you
Misha Koshelev

---

### Post by rocky5051 on 2010-01-19
Actually, that is one of the steps I was going to ammend for 64 bit users in the tutorial today. Ubuntu x64 is shipped with an older version of libmpc, which gcc refuses to build with. You can do the following.

First, remove libmpc entirely:
```
sudo apt-get remove libmpc libmpc-dev
```

Obtain the latest version and save the archive to your home folder. Open a terminal and use wget to obtain it since the rest of the steps will require a terminal anyway.

```
cd $HOME && wget http://www.multiprecision.org/mpc/download/mpc-0.8.1.tar.gz
```

Extract the archive, change into the source code directory, and make/make install it. This will install the binary libmpc and it's source code.

```
tar -xjf mpc-0.8.1.tar.gz
cd mpc-0.8.1
./configure && make && sudo make install
```

Configure gcc again after you've done this and it will work.

EDIT: Read the tutorial over again for the prerequisites part as I've just added some additional instructions now for 64 bit users.

---

### Post by misha680 on 2010-01-19
Thank you so much for the quick response. Gcc now building (fingers crossed).

Thank you again!

Misha

---

### Post by misha680 on 2010-01-19
Btw I would use
```

./configure --prefix=/usr

```
for libmpc2. Otherwise gcc has already complained for me :(

Thank you
Misha

---

### Post by rocky5051 on 2010-01-19
> **misha680 said:**
> Btw I would use
```

./configure --prefix=/usr

```
for libmpc2. Otherwise gcc has already complained for me :(

Thank you
Misha

Hmm...that must be a problem specific to Hardy because I didn't encounter that issue. Then again, I built a build a deb package using checkinstall of mpc so I didn't have to re build it later on. Chances are it was installed differently. I don't really know that much about how they're installed but it looks as if all checkinstall does is make installs it before building the package.

In any case I'll add that to the tutorial. :)

---

### Post by misha680 on 2010-01-19
> **rocky5051 said:**
> Hmm...that must be a problem specific to Hardy because I didn't encounter that issue. Then again, I built a build a deb package using checkinstall of mpc so I didn't have to re build it later on. Chances are it was installed differently. I don't really know that much about how they're installed but it looks as if all checkinstall does is make installs it before building the package.

In any case I'll add that to the tutorial. :)

Thank you so much. It is quite helpful indeed!

Misha

---

### Post by rocky5051 on 2010-02-04
The mpg123 problem doesn't appear to be an issue on Jaunty. At least, trying to apply the patch to the stock mpg123 headers doesn't seem to work. I think it's using a compatible version of mpg123, and I haven't attempted to compile against it yet, but I that's what I think.

---

### Post by KaoriKandiez on 2010-02-07
Hi, thanks so much for making this. I got to here:

> **rocky5051 said:**
> 
**_[SIZE=5]STEP 3: Building and Installing GCC[/SIZE]_**

You are now ready to build GCC :). This is fairly simple if you don't have any special needs, but regardless of what you do, building gcc WILL take a long time (hours), especially if you don't have a multi-core/multi-cpu system to run make in parallel mode (explained later).

To compile gcc from the snapshot you've obtained, navigate into the gcc-svn folder in a terminal, create a directory for objects spawned during the build process (suggested by gnu.org to keep the build clean), navigate into that directory, then run the configure script, and make && make install it.

```
cd $HOME/Desktop/gcc-svn
mkdir objdir
cd objdir
.././configure
**[COLOR=Red]make[/COLOR]**
sudo make install
```

before I got this (if you want the full thing just ask):

```
checking for i686-pc-linux-gnu-gcc... /home/kaori/Desktop/gcc-svn/objdir/./gcc/xgcc -B/home/kaori/Desktop/gcc-svn/objdir/./gcc/ -B/usr/local/i686-pc-linux-gnu/bin/ -B/usr/local/i686-pc-linux-gnu/lib/ -isystem /usr/local/i686-pc-linux-gnu/include -isystem /usr/local/i686-pc-linux-gnu/sys-include   
checking for suffix of object files... configure: error: in `/home/kaori/Desktop/gcc-svn/objdir/i686-pc-linux-gnu/libgcc':
configure: error: cannot compute suffix of object files: cannot compile
See `config.log' for more details.
make[2]: *** [configure-stage1-target-libgcc] Error 1
make[2]: Leaving directory `/home/kaori/Desktop/gcc-svn/objdir'
make[1]: *** [stage1-bubble] Error 2
make[1]: Leaving directory `/home/kaori/Desktop/gcc-svn/objdir'
make: *** [all] Error 2

```Not sure what to do *sadface*

**Edit:** Here is the config.log in the objdir directory generated after the error:

```
This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by GNU C Runtime Library configure 1.0, which was
generated by GNU Autoconf 2.64.  Invocation command line was

  $ /home/kaori/Desktop/gcc-svn/libgcc/configure --cache-file=./config.cache --enable-multilib --enable-languages=c,c++,fortran,java,objc --program-transform-name=s,y,y, --disable-option-checking --with-target-subdir=i686-pc-linux-gnu --build=i686-pc-linux-gnu --host=i686-pc-linux-gnu --target=i686-pc-linux-gnu --srcdir=../../.././libgcc --disable-intermodule --enable-checking=yes,types --disable-coverage --enable-languages=c

## --------- ##
## Platform. ##
## --------- ##

hostname = TheLulzMachine
uname -m = i686
uname -r = 2.6.31-19-generic
uname -s = Linux
uname -v = #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = unknown
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
/usr/bin/hostinfo      = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/games


## ----------- ##
## Core tests. ##
## ----------- ##

configure:1730: loading cache ./config.cache
configure:1899: checking for --enable-version-specific-runtime-libs
configure:1912: result: no
configure:1960: checking for a BSD-compatible install
configure:2028: result: /usr/bin/install -c
configure:2044: checking for gawk
configure:2071: result: gawk
configure:2091: checking build system type
configure:2105: result: i686-pc-linux-gnu
configure:2125: checking host system type
configure:2138: result: i686-pc-linux-gnu
configure:2209: checking for i686-pc-linux-gnu-ar
configure:2236: result: ar
configure:2301: checking for i686-pc-linux-gnu-lipo
configure:2328: result: lipo
configure:2393: checking for i686-pc-linux-gnu-nm
configure:2420: result: /home/kaori/Desktop/gcc-svn/objdir/./gcc/nm
configure:2485: checking for i686-pc-linux-gnu-ranlib
configure:2512: result: ranlib
configure:2577: checking for i686-pc-linux-gnu-strip
configure:2604: result: strip
configure:2666: checking whether ln -s works
configure:2670: result: yes
configure:2687: checking for i686-pc-linux-gnu-gcc
configure:2714: result: /home/kaori/Desktop/gcc-svn/objdir/./gcc/xgcc -B/home/kaori/Desktop/gcc-svn/objdir/./gcc/ -B/usr/local/i686-pc-linux-gnu/bin/ -B/usr/local/i686-pc-linux-gnu/lib/ -isystem /usr/local/i686-pc-linux-gnu/include -isystem /usr/local/i686-pc-linux-gnu/sys-include   
configure:2983: checking for C compiler version
configure:2992: /home/kaori/Desktop/gcc-svn/objdir/./gcc/xgcc -B/home/kaori/Desktop/gcc-svn/objdir/./gcc/ -B/usr/local/i686-pc-linux-gnu/bin/ -B/usr/local/i686-pc-linux-gnu/lib/ -isystem /usr/local/i686-pc-linux-gnu/include -isystem /usr/local/i686-pc-linux-gnu/sys-include    --version >&5
xgcc (GCC) 4.5.0 20100207 (experimental)
Copyright (C) 2010 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:3003: $? = 0
configure:2992: /home/kaori/Desktop/gcc-svn/objdir/./gcc/xgcc -B/home/kaori/Desktop/gcc-svn/objdir/./gcc/ -B/usr/local/i686-pc-linux-gnu/bin/ -B/usr/local/i686-pc-linux-gnu/lib/ -isystem /usr/local/i686-pc-linux-gnu/include -isystem /usr/local/i686-pc-linux-gnu/sys-include    -v >&5
Reading specs from /home/kaori/Desktop/gcc-svn/objdir/./gcc/specs
COLLECT_GCC=/home/kaori/Desktop/gcc-svn/objdir/./gcc/xgcc
COLLECT_LTO_WRAPPER=/home/kaori/Desktop/gcc-svn/objdir/./gcc/lto-wrapper
Target: i686-pc-linux-gnu
Configured with: .././configure
Thread model: posix
gcc version 4.5.0 20100207 (experimental) (GCC) 
configure:3003: $? = 0
configure:2992: /home/kaori/Desktop/gcc-svn/objdir/./gcc/xgcc -B/home/kaori/Desktop/gcc-svn/objdir/./gcc/ -B/usr/local/i686-pc-linux-gnu/bin/ -B/usr/local/i686-pc-linux-gnu/lib/ -isystem /usr/local/i686-pc-linux-gnu/include -isystem /usr/local/i686-pc-linux-gnu/sys-include    -V >&5
xgcc: '-V' must come at the start of the command line
configure:3003: $? = 1
configure:2992: /home/kaori/Desktop/gcc-svn/objdir/./gcc/xgcc -B/home/kaori/Desktop/gcc-svn/objdir/./gcc/ -B/usr/local/i686-pc-linux-gnu/bin/ -B/usr/local/i686-pc-linux-gnu/lib/ -isystem /usr/local/i686-pc-linux-gnu/include -isystem /usr/local/i686-pc-linux-gnu/sys-include    -qversion >&5
xgcc: unrecognized option '-qversion'
xgcc: no input files
configure:3003: $? = 1
configure:3019: /home/kaori/Desktop/gcc-svn/objdir/./gcc/xgcc -B/home/kaori/Desktop/gcc-svn/objdir/./gcc/ -B/usr/local/i686-pc-linux-gnu/bin/ -B/usr/local/i686-pc-linux-gnu/lib/ -isystem /usr/local/i686-pc-linux-gnu/include -isystem /usr/local/i686-pc-linux-gnu/sys-include    -o conftest -g -O2   conftest.c  >&5
/home/kaori/Desktop/gcc-svn/objdir/./gcc/cc1: error while loading shared libraries: libmpc.so.2: cannot open shared object file: No such file or directory
configure:3022: $? = 1
configure:3210: checking for suffix of object files
configure:3232: /home/kaori/Desktop/gcc-svn/objdir/./gcc/xgcc -B/home/kaori/Desktop/gcc-svn/objdir/./gcc/ -B/usr/local/i686-pc-linux-gnu/bin/ -B/usr/local/i686-pc-linux-gnu/lib/ -isystem /usr/local/i686-pc-linux-gnu/include -isystem /usr/local/i686-pc-linux-gnu/sys-include    -c -g -O2  conftest.c >&5
/home/kaori/Desktop/gcc-svn/objdir/./gcc/cc1: error while loading shared libraries: libmpc.so.2: cannot open shared object file: No such file or directory
configure:3236: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "GNU C Runtime Library"
| #define PACKAGE_TARNAME "libgcc"
| #define PACKAGE_VERSION "1.0"
| #define PACKAGE_STRING "GNU C Runtime Library 1.0"
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE_URL "http://www.gnu.org/software/libgcc/"
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:3250: error: in `/home/kaori/Desktop/gcc-svn/objdir/i686-pc-linux-gnu/libgcc':
configure:3253: error: cannot compute suffix of object files: cannot compile
See `config.log' for more details.

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_build=i686-pc-linux-gnu
ac_cv_env_CC_set=set
ac_cv_env_CC_value='/home/kaori/Desktop/gcc-svn/objdir/./gcc/xgcc -B/home/kaori/Desktop/gcc-svn/objdir/./gcc/ -B/usr/local/i686-pc-linux-gnu/bin/ -B/usr/local/i686-pc-linux-gnu/lib/ -isystem /usr/local/i686-pc-linux-gnu/include -isystem /usr/local/i686-pc-linux-gnu/sys-include   '
ac_cv_env_CFLAGS_set=set
ac_cv_env_CFLAGS_value='-g -O2'
ac_cv_env_CPPFLAGS_set=set
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_LDFLAGS_set=set
ac_cv_env_LDFLAGS_value=
ac_cv_env_LIBS_set=
ac_cv_env_LIBS_value=
ac_cv_env_build_alias_set=set
ac_cv_env_build_alias_value=i686-pc-linux-gnu
ac_cv_env_host_alias_set=set
ac_cv_env_host_alias_value=i686-pc-linux-gnu
ac_cv_env_target_alias_set=set
ac_cv_env_target_alias_value=i686-pc-linux-gnu
ac_cv_host=i686-pc-linux-gnu
ac_cv_prog_AR=ar
ac_cv_prog_AWK=gawk
ac_cv_prog_CC='/home/kaori/Desktop/gcc-svn/objdir/./gcc/xgcc -B/home/kaori/Desktop/gcc-svn/objdir/./gcc/ -B/usr/local/i686-pc-linux-gnu/bin/ -B/usr/local/i686-pc-linux-gnu/lib/ -isystem /usr/local/i686-pc-linux-gnu/include -isystem /usr/local/i686-pc-linux-gnu/sys-include   '
ac_cv_prog_LIPO=lipo
ac_cv_prog_NM=/home/kaori/Desktop/gcc-svn/objdir/./gcc/nm
ac_cv_prog_RANLIB=ranlib
ac_cv_prog_STRIP=strip

## ----------------- ##
## Output variables. ##
## ----------------- ##

AR='ar'
AWK='gawk'
CC='/home/kaori/Desktop/gcc-svn/objdir/./gcc/xgcc -B/home/kaori/Desktop/gcc-svn/objdir/./gcc/ -B/usr/local/i686-pc-linux-gnu/bin/ -B/usr/local/i686-pc-linux-gnu/lib/ -isystem /usr/local/i686-pc-linux-gnu/include -isystem /usr/local/i686-pc-linux-gnu/sys-include   '
CFLAGS='-g -O2'
CPP=''
CPPFLAGS=''
DEFS=''
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EXEEXT=''
INSTALL_DATA='/usr/bin/install -c -m 644'
INSTALL_PROGRAM='/usr/bin/install -c'
INSTALL_SCRIPT='/usr/bin/install -c'
LDFLAGS=''
LIBOBJS=''
LIBS=''
LIPO='lipo'
LN_S='ln -s'
LTLIBOBJS=''
MAINT='#'
NM='/home/kaori/Desktop/gcc-svn/objdir/./gcc/nm'
OBJEXT=''
PACKAGE_BUGREPORT=''
PACKAGE_NAME='GNU C Runtime Library'
PACKAGE_STRING='GNU C Runtime Library 1.0'
PACKAGE_TARNAME='libgcc'
PACKAGE_URL='http://www.gnu.org/software/libgcc/'
PACKAGE_VERSION='1.0'
PATH_SEPARATOR=':'
RANLIB='ranlib'
SHELL='/bin/bash'
STRIP='strip'
ac_ct_CC=''
asm_hidden_op=''
bindir='${exec_prefix}/bin'
build='i686-pc-linux-gnu'
build_alias='i686-pc-linux-gnu'
build_cpu='i686'
build_libsubdir='build-i686-pc-linux-gnu'
build_os='linux-gnu'
build_subdir='build-i686-pc-linux-gnu'
build_vendor='pc'
datadir='${datarootdir}'
datarootdir='${prefix}/share'
decimal_float=''
docdir='${datarootdir}/doc/${PACKAGE_TARNAME}'
dvidir='${docdir}'
enable_decimal_float=''
enable_shared='yes'
exec_prefix='NONE'
extra_parts=''
fixed_point=''
host='i686-pc-linux-gnu'
host_alias='i686-pc-linux-gnu'
host_cpu='i686'
host_noncanonical='i686-pc-linux-gnu'
host_os='linux-gnu'
host_subdir='.'
host_vendor='pc'
htmldir='${docdir}'
includedir='${prefix}/include'
infodir='${datarootdir}/info'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
libgcc_topdir='../../.././libgcc/..'
localedir='${datarootdir}/locale'
localstatedir='${prefix}/var'
mandir='${datarootdir}/man'
oldincludedir='/usr/include'
pdfdir='${docdir}'
prefix='NONE'
program_transform_name='s,y,y,'
psdir='${docdir}'
sbindir='${exec_prefix}/sbin'
set_have_cc_tls=''
sharedstatedir='${prefix}/com'
slibdir='$(libdir)'
sysconfdir='${prefix}/etc'
target_alias='i686-pc-linux-gnu'
target_subdir='i686-pc-linux-gnu'
tmake_file=''
vis_hide=''

## ----------- ##
## confdefs.h. ##
## ----------- ##

/* confdefs.h */
#define PACKAGE_NAME "GNU C Runtime Library"
#define PACKAGE_TARNAME "libgcc"
#define PACKAGE_VERSION "1.0"
#define PACKAGE_STRING "GNU C Runtime Library 1.0"
#define PACKAGE_BUGREPORT ""
#define PACKAGE_URL "http://www.gnu.org/software/libgcc/"

configure: exit 1
```Appreciate any help you can provide! 2 million cupz of Ubuntu if I can get it working!!!! :P

**Edit 2: **I think I solved the error. If anyone on Karmic Koala (9.10) gets this error try this:

```
sudo apt-get install g++
```

and it should continue. It's making progress again! Yay!

---

### Post by rocky5051 on 2010-02-08
Are you using 32 bit Karmic? I can't say I ran into that same issue. It could possibly be an issue with 32 bit exclusively, or something is broken in the snapshot you obtained.

EDIT: Nevermind, now that I looked at the architecture (dhar). I guess I'll add that into the tutorial for 32 bit users. Thanks :).

---

### Post by Zenmij on 2010-07-24
Anyone had any joy getting this to work on Karmic.

I start it up multiple times, but no dice.

Gotten a bit further - it was a zombie process - but the minute I try to click anything in xfire - crash

---

