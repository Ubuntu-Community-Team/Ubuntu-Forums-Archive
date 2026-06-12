---
title: "Lattice Diamond on LinuxMint 11 AMD64"
date: 2011-08-20
forum: The Cafe
---

### Post by stanley82 on 2011-08-20
Keywords, Debian, Ubuntu, LinuxMint, Lattice, Diamond
	;How to get Lattice diamond SW up on a Ubuntu/Mint AMD64 installation.
	;This article is based on ;-

[HTTP://effluviaofascatteredmind.blogspot.com/2010/10/lattice-diamond-on-ubuntu-1004-64-bit.html](HTTP://effluviaofascatteredmind.blogspot.com/2010/10/lattice-diamond-on-ubuntu-1004-64-bit.html)
	;I'm running LinuxMint 11 (same as Ubuntu 11:04) on an AMD 64 with 4G of RAM.
Step 1 is okay

Step 2 is okay

	;What follows is what I suggest.  Following that is the convolutions I ran through.
	;Note I put the files in ~/Lattice
==============================================================================
Step 3 Clarification, not sure if this is what he means?  I did ---
Go to [HTTP://frozenfox.freehostia.com/cappy/](HTTP://frozenfox.freehostia.com/cappy/) and put "getlibs-all.deb" into directory with the Diamond file.  Then cd to that directory.
sudo dpkg -i --force-all  getlibs-architecture.deb

apt-get install ia32-libs	;maybe ia-32libs seems to be Ubuntu version dependant.
	;libmotif3		;seems okay without doing this.  Don't use 4

	;Best I can tell it's not possible to convert a 32 bit rpm package to deb
	;using a 64 bit system.

	;My Solution.  Step 5 on 32 bit system
	;Use my old Ubuntu 8:04 socket 7 AMD-k6 450MHz and 250 Meg antique.
	;Moved over the diamond_1_2-base-92-i386-Linux.rpm
	;You should not need ia32-libs or get libs even though I installed them on 32bit.
sudo alien -d diamond_1_2-base-92-i386-Linux.rpm	;Wait 12 hours for prompt
	;I'm moving it back to my AMD64 machine.
Step 5 on AMD64
sudo dpkg  -i --force-architecture  diamond-1-2-base_1.2-93_i386.deb
dpkg: warning: overriding problem because --force enabled:

/usr/local/diamond/1.2/bin/lin/diamond	;Should make it run
	;Ignore warning about unsupported architecture.
	;It ran but eventually missing libqt-mt.so.3: wrong ELF class: ELFCLASS64
	;Guess it's missing the 32 bit version.

	;GOTO
[HTTP://packages.ubuntu.com/hardy/i386/libmotif3/download](HTTP://packages.ubuntu.com/hardy/i386/libmotif3/download) and get the 32 bit version of what you may have in 64 bit.
	;Download libmotif3_2.2.3-2_i386.deb from one of the mirrors.
sudo dpkg -x libmotif3_2.2.3-2_i386.deb /home/me/where/u/wnat/it
	;This unpacks the deb and creates directories below.
	;cd to ~/Lattice/usr/share/qt3/lib
$sudo getlibs -l libqt-mt.so.3		;This seems to put the 32 bit dot.so where it's needed.
	;After that I generated a .jed file and all is great.
	;I could not program the FPGA so pulled over ispVM.
	;What I did to get that up is at the end of this verbage.

===============================================================================
	;My convolutions from which I think all that you need is the above.

Step 3 Clarification, not sure if this is what he means?
Go to [HTTP://frozenfox.freehostia.com/cappy/](HTTP://frozenfox.freehostia.com/cappy/) and put "getlibs-all.deb" into directory with the Diamond file.  Then cd to that directory.
i32 getlibs-all.deb	;think I only clicked it.
  

Step 4 Fails
Should be
apt-get install ia32-libs	;ia-32libs seems to be Ubuntu version dependant.
sudo getlibs -p libmotif3	;not found do not bother, 
				;DO NOT use libmotif4
	;mistake, libmotif4 stopped whatever is there working till dis-installed.

Step 5 Fails
Problem.  How to convert an i32.rpm to i32.deb using an AMD64 system?
This is/may not be possible.

	;My Solution.
Use my old Ubuntu 8:04 socket 7 AMD-k6 450MHz and 250 Meg antique.
Moved over the diamond_1_2-base-92-i386-Linux.rpm and getlibs-all.deb
sudo dpkg -i getlibs.deb
sudo apt-get install ia32-libs	;failed this time
sudo apt-get install ia-32libs	;Okay on this system
sudo getlibs -p libmotif3	;Okay this time try 4 if not found
	;The above may not be necessary to run alien on 32 bit.
sudo alien -d diamond_1_2-base-92-i386-Linux.rpm	;Wait 12 hours for prompt
	;I got a diamond_1_2-base-92-i386-Linux.deb and I suspect the original article
	;failed to make a .deb file.  After all Alien converts .rpm to .deb.
	;I'm moving it back to my AMD64 machine.

Step 5 on AMD64
sudo dpkg  -i --force-architecture  diamond-1-2-base_1.2-93_i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package diamond-1-2-base:i386.
(Reading database ... 163241 files and directories currently installed.)
Unpacking diamond-1-2-base:i386 (from diamond-1-2-base_1.2-93_i386.deb) ...
Setting up diamond-1-2-base:i386 (1.2-93) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
	;Looks like it may be okay, try running it

sudo /usr/local/diamond/1.2/bin/lin/diamond
/usr/local/diamond/1.2/bin/lin/pnmain: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
	;It's in this file.
sudo apt-get install libmotif3
[sudo] password for stan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libmotif3 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However, the following packages replace it:
  libmotif4

E: Package 'libmotif3' has no installation candidate

	;I worked on it for a bit eventually disinstalling libmotif4
	;with package manager and that seems to have fixed it.
	;try running again

sudo /usr/local/diamond/1.2/bin/lin/diamond
[sudo] password for stan: 

	;This looks bad but it's only a warning that;---
 
Warning: You are running on an unsupported platform 
  'synplify_pro' only supports Red Hat Enterprise Linux 4.0 and above
 
  current platform: Linux Mint 11 Katya 
---------------------------------------------------------
	;Diamond seems to run oops missing libqt-mt.so.3 got libqt-mt from package manager.
	;Now it's libqt-mt.so.3: wrong ELF class: ELFCLASS64
	;using package manager I dis installed ia32-libs THEN
 sudo aptitude install ia32-libs
The following NEW packages will be installed:
  ia32-libs 
The following packages will be REMOVED:
  freeglut3{u} gir1.2-clutter-1.0{u} gir1.2-clutter-gtk-0.10{u} 
  gir1.2-gnomegamessupport-1.0{u} gir1.2-gstreamer-0.10{u} 
  gir1.2-json-glib-1.0{u} gnome-games-common{u} gnome-js-common{u} 
  libclutter-1.0-0{u} libclutter-1.0-common{u} libclutter-gtk-0.10-0{u} 
  libgtkglext1{u} libseed0{u} python-gtkglext1{u} python-opengl{u} 
  python-rsvg{u} seed{u} 
0 packages upgraded, 1 newly installed, 17 to remove and 145 not upgraded.
Need to get 0 B/60.3 MB of archives. After unpacking 186 MB will be used.
Do you want to continue? [Y/n/?] y
(Reading database ... 186583 files and directories currently installed.)
Removing python-gtkglext1 ...
Removing python-opengl ...
Removing freeglut3 ...
Removing seed ...
Removing libseed0 ...
Removing gir1.2-clutter-gtk-0.10 ...
Removing gir1.2-clutter-1.0 ...
Removing gir1.2-gnomegamessupport-1.0 ...
Removing gir1.2-gstreamer-0.10 ...
Removing gir1.2-json-glib-1.0 ...
Removing gnome-games-common ...
Removing gnome-js-common ...
Removing libclutter-gtk-0.10-0 ...
Removing libclutter-1.0-0 ...
Removing libclutter-1.0-common ...
Removing libgtkglext1 ...
Removing python-rsvg ...
Processing triggers for python-support ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for man-db ...
Selecting previously deselected package ia32-libs.
(Reading database ... 185380 files and directories currently installed.)
Unpacking ia32-libs (from .../ia32-libs_20090808ubuntu13_amd64.deb) ...
Processing triggers for libglib2.0-0 ...
Setting up ia32-libs (20090808ubuntu13) ...
==========================================================
	;same problem libqt-mt.so.3: wrong ELF class: ELFCLASS64

stan@Ian ~/IanStuff/Lattice $ sudo getlibs -i libmotif3_2.2.3-2_i386.deb
[sudo] password for stan: 
Installing libraries ...
	;Try again to make a .jed file on Diamond  *** same problem.
	;I'd already unpacked using dpkg -x libmotif3_2.2.3-2_i386.deb
	;Maybe it failed try this 
stan@Ian ~/IanStuff/Lattice/usr/share/qt3/lib $sudo getlibs -l libqt-mt.so.3
libqt-mt.so.3: libqt3-mt
The following i386 packages will be installed:
libqt3-mt
Continue [Y/n]? y
Downloading ...
Installing libraries ...
	;I now have a .jed file.
=======================================================================================
	:ispVM installation.
=======================================================================================
	;With all the previous work it ran.  I think all I did was to get the latest 
	;version of ispVM from lattice and de-gunzip and de-tar, set up the .bashrc file
	;per Lattice instructions.  Don't try any of the .sh files and do not get csh
	;They ain't right for Ubuntu.
	;I seem to remember it saying missing a dot.so file but must have been tired
	;as I got nowhere trying to fix it.
	;Anyway ispVM ran but problem with usb programmer.
	;After a lot of research and f*** 
stan@Ian /dev $ sudo chmod a+rw /dev/lattice-6 
	;Got the programmer usb driver going.
	;AT THIS POINT ALL SHOULD BE OKAY.
	;I tried the following at one point but seem to run into major security block
	;so maybe that saved me from messing up Ubuntu so try not to do it.
	;Any way somehow it got done by Ubuntu or Lattice BUT NOT me.

	;Try not to do this.
sudo gedit /etc/udev/rules.d/10-local.rules	;Try not to do this.

Append this line but it will not let you save it:
#lattice
BUS=="usb",ACTION=="add",SYSFS{idVendor}=="1134",SYSFS{idProduct}=="8001",MODE=="0660",OWNER=="root",SYMLINK+="lattice-%n"
	;I must have been really tired because the lattice installation have a different place for rules.
	;Maybe that's where it is in unix.
==========================================================================================

---

