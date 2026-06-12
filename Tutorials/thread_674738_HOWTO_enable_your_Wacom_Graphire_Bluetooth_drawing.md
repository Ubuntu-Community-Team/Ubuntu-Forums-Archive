---
title: "HOWTO: enable your Wacom Graphire Bluetooth drawing tablet"
date: 2008-01-22
forum: Tutorials
---

### Post by mesilliac on 2008-01-22
[SIZE="4"][B]This HOWTO has been moved to the wiki!

Please read the updated howto, with instructions for Jaunty, Intrepid and Hardy at:

[https://help.ubuntu.com/community/WacomGraphireBluetooth](https://help.ubuntu.com/community/WacomGraphireBluetooth)
[/B][/SIZE]

---

### Post by awoehler on 2008-02-03
Thanks mesilliac. I only had to do the first set of on my ASUS F3SA-A1 to get it working in Ubuntu 7.10.

---

### Post by Clochard on 2008-02-05
The device names in your xorg.conf aren't quite right, if you follow the instructions.  They should read tablet-wacom, as per the original guide, I believe.

Any idea if we can get the two buttons on the tablet working?  Also, where do we find info on the various xorg.conf options for these things?  Or is there some kind of GUI to configure absolute vs relative, etc?

Thanks for the tips too!  Using the compiled driver really does produce a much smoother and usable experience


Edit - answered my own question: man wacom will show all the options available.  Still wonder if there's a GUI available to configure it all though....  As for the device name, when my tablet powered off during a long while and I powered it back on, the device name actually is just wacom.  Strange things are afoot.

---

### Post by mesilliac on 2008-02-05
@ awoehler: that's good to hear :). My tablet seemed to work after the first step, but it was very jerky and I couldn't get the absolute positioning or pressure sensitivity to work, so you still might get a better tablet experience by following the rest of the directions.

@ Clochard: the device name symlink "/dev/input/wacom" should be dynamically created when the tablet is turned on. The name of it just depends on what we set in the udev rules (/etc/udev/rules.d/50-xserver-xorg-input-wacom.rules). I'm not sure if you need to restart udev for these rules to take effect, so if anyone else has the same problem with it being called tablet-wacom, try turning the tablet off, then on again and tell me if that works so I can update the howto.

I've updated the howto with a section which should get the buttons on the tablet working. You have to add a section like the "cursor", "stylus" and "eraser" ones, except called "pad". Try that and see if it works :). I don't use the buttons at all, so I didn't notice that I forgot to add it.

Yes "man wacom" will show you the driver options. And boy are there a lot of them! I wish there were a GUI for this too! I added the options to set absolute and relative positioning in the howto.

The other options can be found at:
[http://linuxwacom.sourceforge.net/index.php/howto/inputdev](http://linuxwacom.sourceforge.net/index.php/howto/inputdev)

Probably the most useful one is the "PressCurve" option. I find the default linear pressure curve to be fine, but it's something you might want to tweak until you get it just how you like it.

Another useful page is the ubuntu community help docs for wacom tablets:
[https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)
I'm thinking of adding a help page to the wiki for the graphire bluetooth, but wanted to make sure I get some feedback on the instructions first.

---

### Post by Clochard on 2008-02-06
Great stuff - the wacom link is the right one as you say.

I had it all working last night, then some update was applied in the background and things went to pot this morning

I've now got it back up and running, but I can't seem to run xsetwacom to update the xorg settings on the fly.  It was nice last night being able to modify these things on the fly, to test them out.

Now when I try to even list the devices I just get a blank line .... I'm not really sure how to handle this problem.  Any ideas?

Oh, and there is a GUI for this stuff, a python app called [wacom-config.]("http://alavaliant.googlepages.com/")  But it is really raw right now.

---

### Post by Clochard on 2008-02-06
Oh, and another thing.  Should we be using the Option USB On, for this device?  Since we're probably using a BT-USB adapter, I suppose it is USB?  Maybe?  I haven't been using it so far and am wondering if doing so might solve some of the weird problems.

---

### Post by Clochard on 2008-02-06
> **Clochard said:**
> 
Now when I try to even list the devices I just get a blank line .... I'm not really sure how to handle this problem.  Any ideas?
.

Aye carumba - I reinstalled wacom-tools, logged out, restarted X, and now xsetwacom is back in working order.  Some very strange things that I can't figure out the pattern yet.  Now that it is working, I'm afraid to touch anything in case it stops working.  I suppose I could just hard-code it all into xorg.conf.

---

### Post by mesilliac on 2008-02-06
The annoying thing with compiling kernel modules is that you have to do it again every time your kernel gets updated :(.

I've been having trouble since the kernel update the other day too - I tried to test to see if my tablet buttons were working, and wacdump didn't register anything at all! Everything seems to be working as normal though, and I confirmed the buttons do work in the GIMP after adding the "pad" section to my xorg.conf.

When I was first trying to get my tablet to work, I did try the "USB = on" option. I don't remember the exact result, but it didn't improve anything.

If you're feeling brave you're welcome to try it though :).

I'd recommend harcoding your preferred settings into xorg.conf, then using xsetwacom if you want to change something temporarily.

I didn't have to go through all of this on the previous kernel update before this one - just recompiled the module and all was fine, so I'm hoping wacom-tools needing a reinstall is a one-off thing.

I'll go try reinstalling it and see if wacdump works now.

EDIT: still not working :(.

For the record, the only real problem I have with my tablet's functionality is that I have to restart X every time I turn it on.

Oh, and another option I tried was the "resolution" one (I tried setting it as the tablet's resolution of 2032 lpi), but it didn't change anything. The" KeepShape" option doesn't seem necessary at first, but if you have a widescreen it feels a little odd if you don't have it set to on!

---

### Post by Clochard on 2008-02-08
I believe you can just switch to a different virtual terminal when you turn the tablet on, then back to the graphical one.  This is the same as restarting X for these modules, or so I've read.

So turn it on, CTL-ALT-F1, CTL-ALT-F7 and that should do the trick.

I'm seeing periodic lags in the cursor and pen.  Any idea what causes this?  Is it lack of memory?  Horsepower? Driver problems?  It makes the things pretty much useless so I'd like to solve it if possible.  Is it that I need to reinsert the module again?

I really do wish this just worked.

---

### Post by Clochard on 2008-02-09
Just confirmed that for unknown reasons, xsetwacom sometimes isn't actually doing anything (xsetwacom list dev returns nothing).

In this case, dpkg-reconfigure wacom-tools, then restarting X results in a working xsetwacom.

---

### Post by mesilliac on 2008-02-11
Huh, you're quite right about switching to another virtual terminal and then back!

I'm not getting any sort of periodic lags like those you mention, so probably your guess is as good as mine as to the cause. I'd be tempted to blame the driver; I was surprised that it worked at all as it is based on the hidp module from the 2.6.6 kernel, and hasn't been updated since then. However as I said, it is working perfectly well for me :S.

Have you tried simple things like moving closer to the bluetooth adapter and plugging it into a different USB port, to see if they affect anything?

I would try recompiling and reinserting the module, but if that doesn't work I'm pretty much out of ideas :(.

---

### Post by mesilliac on 2008-02-12
I just realised that the two links I gave to the driver point to different versions... ironically the one on the guy's website is the older one...

If you downloaded from the first link, try using the other one :S

I'll edit it so only the most recent version is linked.

---

### Post by Clochard on 2008-02-12
I'll try the driver again, I can't remember which one I used.

I also posted a bug in LP about the lag:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/191374](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/191374)

---

### Post by Clochard on 2008-02-12
When running the make command I'm getting the linux/config.h error message and the make fails.  The driver page you linked (original authors) has the workaround of removing some #include commands - you might want to consider that in your guide?  All the guide says is you shouldn't see errors ... but what do we do if/when we do see errors?

Did you not see the errors?  I wonder if that's the problem.  You're running gutsy?

---

### Post by mesilliac on 2008-02-14
I don't get any errors when I run make. This is the output I get:

```

tommy@foxtrot:~/src/wacom-bt-driver$ make
make CONFIG_DEBUG_INFO= -C /lib/modules/2.6.22-14-rt/build M=/home/tommy/src/wacom-bt-driver/hidp
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-rt'
  LD      /home/tommy/src/wacom-bt-driver/hidp/built-in.o
  CC [M]  /home/tommy/src/wacom-bt-driver/hidp/core.o
  CC [M]  /home/tommy/src/wacom-bt-driver/hidp/boot.o
  CC [M]  /home/tommy/src/wacom-bt-driver/hidp/tablet.o
  CC [M]  /home/tommy/src/wacom-bt-driver/hidp/sock.o
  LD [M]  /home/tommy/src/wacom-bt-driver/hidp/hidp.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/tommy/src/wacom-bt-driver/hidp/hidp.mod.o
  LD [M]  /home/tommy/src/wacom-bt-driver/hidp/hidp.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-rt'

```

I'm running the realtime kernel but I can't see how it would make a difference...

Can you post the output you get from trying to make the driver?

Oh UGH, I just checked and even the newly linked driver doesn't seem to be as recent as the version I have... :confused:


Okay, after a little searching, I think this is the version I have that is compiling fine:

[http://octesian.com/wacom-bt-driver.tar.gz](http://octesian.com/wacom-bt-driver.tar.gz)

This was linked to from a post by "octesian", who perhaps deserves credit for updating it...

Found in this thread:
[http://ubuntuforums.org/showthread.php?t=381751](http://ubuntuforums.org/showthread.php?t=381751)


I'm sorry about this :(. This driver seems to have a couple more changes, as well as removing the linux/config.h includes.

The state of support for this tablet in linux is pretty horrendous... but I'm hoping if I can at least construct a working HOWTO, someone who knows a bit more about it than me might use this as a start for constructing a better working driver.

---

### Post by Clochard on 2008-02-14
The driver you linked to this time compiled without any errors, so I'll see if they resolve my lag problems.  However after logging in and opening a terminal, xsetwacom still fails to see any devices, even though they're in the /dev/input location.

I'll investigate more after work today.

---

### Post by Clochard on 2008-02-18
I've moved my USB BT receiver closer to the tablet.  It was originally about 3 feet away through a desktop and a piece of wood.  Should hardly stop the BT signal but just in case ... I moved it to a USB port on my monitor, so now it is about 2 feet away with only the monitor in between (LCD).

So with this change, and your latest driver link, I've only seen a single case of lag - much less than before.  I'd consider the device now usable, though I really hate the lags still.  I'll continue to look at it ... some strange things going on and I don't know how to troubleshoot it.

The bug in launchpad was changed to wacom-tools, and no other action.  I checked wacom-tools package and see that it provides 3 tools ... wacdump, xidump, and xsetwacom.

Right now, as I am typing, the mouse and tablet are working fine.  However if I use xidump to test things it crashes Compiz, leaving me with windows without a window manager (no title bars).  Are you seeing the same thing?

Try running xidump -v cursor and clicking around to see if Compiz crashes for you, if you please.

---

### Post by mesilliac on 2008-02-19
xidump does crash compiz for me too.

you can just restart compiz by typing "compiz --replace" . Once in the terminal, then once compiz is running again, ALT-F2 and "compiz --replace" again (so it's not tied to the terminal process). But that is a bit of a pain.

I was using "sudo wacdump /dev/input/wacom" to test my tablet until it completely stopped working a couple kernel revisions ago :-?. Currently I just fire up GIMP and see if everything works as it should.

If you just want to check buttons and positioning quickly, use "xev". But it won't show you pressure sensitivity readings at all.

Re: the distance to the USB reciever... with my bluetooth logitech keyboard it had occasional lags more than 1m (3 ft) from my computer... until I took the usb reciever out of the back and plugged it into the front of the computer. Technically this seems rather silly to me, but both my keyboard and tablet work fine from at least 3-4m (10-12 ft) away with the usb adapters directly visible.

---

### Post by Clochard on 2008-02-20
Another question - I right now am using my tablet mouse to move the cursor around.  When I run sudo wacdump /dev/input/wacom I get the wacdump interface, but it isn't registering any of the mouse input.  The mouse is, in fact, sending events and the cursor responds normally (though laggy, which is why I'm looking at wacdump in the first place).

Has this ever happened to you?  It strikes me as odd that wacdump isn't seeing any of these events.

---

### Post by mesilliac on 2008-02-22
wacdump is completely broken for me right now. It doesn't do anything.

The lag will be at the driver level... you can see the events lagging with "sudo cat /dev/input/wacom". As far as I remember, I had this problem with cursor lag when I hadn't installed the kernel driver properly, so simply recompiling and reinserting it, then restarting fixed it.

---

### Post by Clochard on 2008-02-22
Nice to hear you're having so much success with the tablet right now :(

I've moved my BT receiver closer still, and have not yet seen the lag happening again.

I'm also seeing really weird stuff with wacdump.

Maybe Hardy will be the answer.  For now I have it working, though a little flakey on reboot.  At least it is usable, and I thank you for this great resource.

---

### Post by KaiserM on 2008-03-06
After an all night marathon, I have pressure sensitivity working in gimp using the original posts instructions, and some modifications to xorg.conf with commands I fished from the web with the Graphire CTE-630BT.  Theres still a bug where the tablet discalibrates if I power it off and back on, but thats survivable and only requires a ctrl+alt+backspace to recalibrate.  With both the pen and the eraser set to screen, everything seems to be working fantastically.  Xorg reads as follows:

> Section "InputDevice"
	Driver		"wacom"
	Identifier	"wacom pen"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
        Option          "ForceDevice"   "ISDV4" # Tablet PC ONLY
	Option		"Mode"	"absolute"
        Option          "USB"   "on"
        Option          "TVResolution" "1024x768,1024x768"
        Option          "ScreenNo"     "0"
        Option 		"KeepShape" 	"on"
        Option          "PressCurve"     "50,0,100,50"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"wacom eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
        Option          "ForceDevice"   "ISDV4" # Tablet PC ONLY
	Option		"Mode"	"absolute"
        Option          "USB"   "on"
        Option          "TVResolution"  "1024x768,1024x768"
        Option          "ScreenNo"     "0"
        Option 		"KeepShape" 	"on"
       
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"wacom mouse"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
        Option          "ForceDevice"   "ISDV4" # Tablet PC ONLY
        Option          "USB"   "on"
	Option		"Mode"	"relative"
        Option          "TVResolution" "1024x768,1024x768"
        Option          "ScreenNo"     "0"
        Option          "Twinview"      "horizontal"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"pad"
        Option          "ButtonsOnly" "on"
        Option          "Button9" "1"
        Option          "Button13" "3"
        Option          "ForceDevice"   "ISDV4" # Tablet PC ONLY
        Option          "USB"   "on"
        Option          "TVResolution" "1024x768,1024x768"
        Option          "ScreenNo"     "0"
        Option          "Twinview"      "horizontal"
EndSection

> # Uncomment if you have a wacom tablet
	Inputdevice	"wacom pen"	"SendCoreEvents"
	Inputdevice	"wacom mouse"	"SendCoreEvents"
	Inputdevice	"wacom eraser"	"SendCoreEvents"
	Inputdevice	"pad"           "SendCoreEvents"

I basically just added commands I fished out until it worked.  Some of this may not be doing anything/and or do i look like an idiot yet?  :/

---

### Post by mesilliac on 2008-03-06
Ooh, you have it working with TwinView? nice :)

That bug that happens when you turn the tablet off and on is a known problem with the wacom X driver. It happens for USB tablets too, if you unplug them then plug them back in again.

It's usually sufficient to switch to another virtual terminal and then back to fix it. CTRL-ALT-F1 then CTRL-ALT-F7 to change back.

re: the USB option: did you find that it made a difference? It didn't seem to change anything for me, but I didn't test it much.

re: that "PressCurve" line... you probably don't want 50,0,100,50. on your stylus. afaik this will really break your pressure sensitivity! try something subtler: e.g. 5, 0, 100, 95 would make it a little "harder" than normal, 0, 5, 95, 0 a little "softer" (this taken from "man wacom").

EDIT: Also, were those button options necessary for the pad to function properly? I never use the pad buttons, so I'll update the howto if they are. I'll be putting the howto on the wiki and updating it sometime in the next couple days, as it seems to have helped :).


On another note: I now have my wacom graphire bluetooth working in hardy! I had to update the driver to compile with the latest kernel, and I also updated it to compile on 64 bit systems. I'll update the HOWTO closer to hardy's release after I've tested it a bit more. If anyone wants the updated driver to test on hardy, post here or pm me.

---

### Post by KaiserM on 2008-03-11
most of what you see there is completely unnecessary :/

---

### Post by chinatony on 2008-03-11
:)Too difficult, cannot understand.

---

### Post by mesilliac on 2008-03-13
> **chinatony said:**
> :)Too difficult, cannot understand.

Sadly, it is difficult to get this tablet working with Linux :(.

I've committed the howto to the Ubuntu Community Docs. You can find (and edit) it at:
[https://help.ubuntu.com/community/WacomGraphireBluetooth](https://help.ubuntu.com/community/WacomGraphireBluetooth)

At some point I will add the howto for Hardy. There are still some issues with Xorg 7.3 and the linux wacom drivers though. Perhaps they will be resolved. Currently I'm having to compile and install the latest linux wacom drivers, as well as the modified kernel module.

---

### Post by octesian on 2008-03-24
Sorry, that file I linked to a few months ago was not the one I intended to.  This one has instructions to go with it. [http://octesian.com/ubuntu-bt-graphire.tar.gz]("http://octesian.com/ubuntu-bt-graphire.tar.gz") 

Again, I've only tested this in feisty and gutsy 64 and 32.

---

### Post by laharrin on 2008-03-25
@mesilliac: I could use some help with compiling linuxwacom-0.7.9-8 if you have had any luck.  Here is the output from ./configure --enable-wacom, and I think my problem may lay with the fact that wacom_drv.so is not being built.

laharrin@laharrin:~/linuxwacom-0.7.9-8$ ./configure --enable-wacom
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gawk... (cached) gawk
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for arch type... i486-linux-gnu
checking for kernel type... Linux
checking for linux-based kernel... yes
checking for kernel source/headers... /lib/modules/2.6.24-12-generic/build
checking kernel version... 2.6.24-12-generic
checking for kernel module support... yes
checking for Xlib... yes
checking for XSERVER... checking for valid Xorg SDK... "xf86Version.h missing"
Tried /usr/include, /usr/include/xorg, and /usr/xc/include
checking for X... no
checking for tclsh... /usr/bin/tclsh
checking for tcl version... 8.4
checking for tcl header files... configure: WARNING: not found; tried /usr/include, tcl, and tcl8.4; 
***
*** The tcl development environment can not be found.
*** The header file tcl.h does not appear at the normal
*** (or provided) include path. Some build features
*** will be unavailable.
***
checking for tk header files... configure: WARNING: not found; tried /tk.h and /usr/include/tk.h
***
*** The tk development environment can not be found.
*** The header file tk.h does not appear at the normal
*** (or provided) include path. Some build features
*** will be unavailable.
***
checking ncurses.h usability... yes
checking ncurses.h presence... yes
checking for ncurses.h... yes
checking if libwacomcfg should/can be built... yes
checking if libwacomxi should/can be built... configure: WARNING: tcl environment missing, libwacomxi not built
checking if wacdump should/can be built... yes
checking if xidump should/can be built... yes
checking if xsetwacom should be built... yes
checking for Wacom X driver module path... /usr/lib/xorg/modules/input
checking for dynamic driver loading support... yes
checking if wacom_drv.{o,so} should be compiled... configure: WARNING: requires Xorg SDK or XFree86 build environment, wacom_drv not built
checking if gcc accepts -fno-merge-constants... yes
checking if gcc accepts -fno-stack-protector... yes

configure: creating ./config.status
config.status: creating Makefile
config.status: creating mkxincludes
config.status: creating src/Makefile
config.status: creating src/util/Makefile
config.status: creating src/xdrv/Makefile
config.status: creating src/2.4/Makefile
config.status: creating src/2.4.22/Makefile
config.status: creating src/2.6.8/Makefile
config.status: creating src/2.6.9/Makefile
config.status: creating src/2.6.10/Makefile
config.status: creating src/2.6.11/Makefile
config.status: creating src/2.6.13/Makefile
config.status: creating src/2.6.14/Makefile
config.status: creating src/2.6.15/Makefile
config.status: creating src/2.6.16/Makefile
config.status: creating src/2.6.18/Makefile
config.status: creating src/2.6.19/Makefile
config.status: creating src/2.6.22/Makefile
config.status: creating src/2.6.24/Makefile
config.status: creating src/wacomxi/Makefile
config.status: creating src/wacomxi/wacomcpl
config.status: creating src/include/xdrv-config.h
config.status: src/include/xdrv-config.h is unchanged
config.status: creating src/include/kernel-config.h
config.status: src/include/kernel-config.h is unchanged
config.status: creating src/include/util-config.h
config.status: src/include/util-config.h is unchanged
config.status: executing depfiles commands

----------------------------------------
  BUILD ENVIRONMENT:
       architecture - i486-linux-gnu
       linux kernel - yes 2.6.24
  module versioning - no 
      kernel source - yes /lib/modules/2.6.24-12-generic/build
     XFree86 source - no 
           Xorg SDK - no 
          XSERVER64 - no
           dlloader - yes
               XLib - yes /usr/lib
                TCL - no 
                 TK - no 
            ncurses - yes

  BUILD OPTIONS:
            wacom.o - yes
            wacdump - yes 
             xidump - yes 
        libwacomcfg - yes
         libwacomxi - no
          xsetwacom - yes
              hid.o - no 
         usbmouse.o - no
            evdev.o - no
         mousedev.o - no
            input.o - no
       wacom_drv.so - no /usr/lib/xorg/modules/input 
        wacom_drv.o - no
  wacom*_drv quirks -
----------------------------------------

---

### Post by mesilliac on 2008-03-25
Hi laharrin,

it looks like you don't have the X development libraries installed. If you do "sudo apt-get build-dep xserver-xorg-input-wacom" it should install all the necessary -dev packages to compile the wacom driver :).

I have the tablet running just as well in Hardy as it did in gutsy, but I did have to compile the wacom X driver. Also, I had to modify the hidp module somewhat; here's a link to the new hidp kernel module that should work on hardy.

[http://sourceforge.net/tracker/download.php?group_id=69596&atid=525126&file_id=269307&aid=1908703](http://sourceforge.net/tracker/download.php?group_id=69596&atid=525126&file_id=269307&aid=1908703)

I've been meaning to write a howto for hardy, but I haven't found the time yet.

[quote="octesian"]Sorry, that file I linked to a few months ago was not the one I intended to. This one has instructions to go with it. [http://octesian.com/ubuntu-bt-graphire.tar.gz](http://octesian.com/ubuntu-bt-graphire.tar.gz)

Again, I've only tested this in feisty and gutsy 64 and 32. [/quote]
I wondered about that :). It looks like your instructions are what I ended up with in the howto anyway. When you upgrade to hardy you'll probably find it won't compile against the 2.6.24 kernel (the version I just posted should work ok).

---

### Post by m.musashi on 2008-03-26
> **mesilliac said:**
> I've been meaning to write a howto for hardy, but I haven't found the time yet.

+1 for that. I'm loving hardy but some of the old solutions no longer work - party because they are not needed but not everything is working yet either (too impatient, I know).

EDIT: oops, I see this is probably for the bluetooth model. I have the USB model graphire4.

---

### Post by laharrin on 2008-03-26
Thanks mesiliac for the tip about the development packages.  It did compile with the correct options, but it still doesn't work.  We will be on the look-out for your Hardy how-to if you find the time.

thanks again!

---

### Post by mesilliac on 2008-03-27
I can't seem to log into the wiki, so here's a quick rundown of how I got the tablet working in hardy. This is from memory, hopefully I won't miss anything.

1) Pair the tablet:
* press "connect" button on the tablet
* System>Prefs>Bluetooth --> Services tab
* click "Input service", select the WACOM tablet (should appear in the bottom pane) and click "add"

hidd isn't needed anymore

2) Compile and install the kernel driver
* get the driver source from [http://sourceforge.net/tracker/download.php?group_id=69596&atid=525126&file_id=269307&aid=1908703](http://sourceforge.net/tracker/download.php?group_id=69596&atid=525126&file_id=269307&aid=1908703)
* follow the same steps as in the gutsy howto
*** note: you don't need to reboot afterwards, just do:
* sudo modprobe -r hidp
* sudo modprobe hidp

3) get the tablet working in X
This step should be just the same as for gutsy, except the wacom lines in your Xorg.conf might not be there already.
* modify /etc/udev/rules.d/... as for gutsy
* add the wacom bits from the gutsy howto to Xorg.conf in the appropriate places

You shouldn't need to reboot, just log out and log back in again.

For the tablet to work correctly, you MUST have it turned on when you log in. Otherwise the wacom X driver will not be loaded for the tablet. If you turn the tablet off and on again after this, you can get it back to normal by pressing CTRL-ALT-F6 to switch to another virtual terminal, then CTRL-ALT-F7 to switch back to X. This problem exists for the USB tablets too, just they're usually plugged in all the time.

---

### Post by mesilliac on 2008-03-29
Ahh, it looks like the latest wacom X driver is now in hardy :).

---

### Post by laharrin on 2008-03-31
Thanks.  I've finally got it working with the new packages from the repository and compiling the kernel driver manually.

---

### Post by KaiserM on 2008-03-31
Got it, thanks a ton

---

### Post by KaiserM on 2008-04-03
So what do I do now that the kernel updated to 2.6.24.14?  Does the same hipd.ko work or do I need to find one for the current kernel?

---

### Post by mesilliac on 2008-04-08
When the kernel version changes, you need to do the step compiling and copying hidp.ko again :(.

Just reboot into the new kernel, then do step 2) again, with the new kernel headers.

after the modprobe lines, it should be back to normal (you'll still have to log out and in to get X to recognise it)

---

### Post by Clochard on 2008-04-28
I've upgraded to Hardy and wanted to know if anyone else is having trouble here.

I followed the howto, including the gutsy steps again.  My tablet pairs, and works, but I can't seem to do basic things like set my cursor to relative rather than absolute.  I've set it to relative in xorg.conf, but it seems to be ignoring it?

I've tried running "xsetwacom list dev" and it returns nothing.

In Gutsy, I simply had to dpkg-reconfigure wacom-tools, logout, login and this would resolve the problem.  However this isn't fixing it this time.

The input nodes seem to be there, but the wacom tools aren't seeing them?

kirk@Creativity:~/Desktop$ ls -l /dev/input
total 0
drwxr-xr-x 2 root root     80 2008-04-27 23:03 by-id
drwxr-xr-x 2 root root    120 2008-04-27 23:03 by-path
crw-rw---- 1 root root 13, 64 2008-04-27 23:03 event0
crw-rw---- 1 root root 13, 65 2008-04-27 23:03 event1
crw-rw---- 1 root root 13, 66 2008-04-27 23:03 event2
crw-rw---- 1 root root 13, 67 2008-04-27 23:03 event3
crw-rw---- 1 root root 13, 68 2008-04-28 10:56 event4
crw-rw---- 1 root root 13, 63 2008-04-27 16:02 mice
crw-rw---- 1 root root 13, 32 2008-04-27 16:02 mouse0
crw-rw---- 1 root root 13, 33 2008-04-27 16:02 mouse1
crw-rw---- 1 root root 13, 34 2008-04-28 10:56 mouse2
lrwxrwxrwx 1 root root      6 2008-04-28 10:56 tablet-graphire_bt-6x8a -> event4
lrwxrwxrwx 1 root root      6 2008-04-28 10:56 tablet-wacom -> event4

---

### Post by mesilliac on 2008-05-03
It sounds a bit like the new hidp module isn't being used. Have you tried recompiling and recopying the kernel module?

Other than that I'm not really too sure what the problem could be :(.

---

### Post by valmont27 on 2008-05-03
what's your dmesg output?

---

### Post by valmont27 on 2008-05-03
have you done a modprobe for the wacom tablet?

---

### Post by Clochard on 2008-05-03
Hardy just got a new kernel - I'll update and follow the howto again.

What modules should I be modprobing manually for the tablet?

---

### Post by Clochard on 2008-05-08
Hmm, well, it's all working now.  Must have missed a step last time or something.  Back into tablet-ly goodness!

---

### Post by mesilliac on 2008-06-14
I just updated the makefile on the driver to make installing it a little easier.

Now when your kernel version changes, all you have to do is reboot into the new kernel, "make" then "sudo make install" (no more figuring out where to copy it to, what to modprobe, etc.).

[http://sourceforge.net/tracker/download.php?group_id=69596&atid=525126&file_id=282125&aid=1908703](http://sourceforge.net/tracker/download.php?group_id=69596&atid=525126&file_id=282125&aid=1908703)

---

### Post by Clochard on 2008-06-19
Hey mesilliac, that file won't open as it doesn't seem to be a tar archive.

```
kirk@Creativity:~/Desktop$ tar zfx wacom-bt-driver-2008-06-14.tar.gz 
tar: This does not look like a tar archive
tar: Skipping to next header
tar: Error exit delayed from previous errors
kirk@Creativity:~/Desktop$ 
```

---

### Post by mesilliac on 2008-06-22
Hmm. The file it's downloading isn't the file I uploaded.

I tried reuploading it and the problem persists. The old driver won't download correctly either. How annoying.

Guess I'll tell Sourceforge about it. Thanks for letting me know.

---

### Post by nebulus-design on 2008-10-25
Is it possible to disable the events from the tablet from being sent to the Xserver?  I'm not concerned with controlling the mouse, but want to get access to the tablet directly (just like wacdump).

I've removed all tablet related stuff from the xorg.conf file, but still it sends events to X.

Any ideas?

---

### Post by mesilliac on 2008-10-26
AFAIK this can be achieved simply by setting the relevant "SendCoreEvents" option in your xorg.conf to "false" in stead of "true" :).

---

### Post by nebulus-design on 2008-10-28
Well!

I've tried a number of combinations of SendCoreEvents in the xorg.conf file, and none worked.  

I've removed all the sections mentioning wacom from this file, and moved out of the way the wacom_drv.so file as I spotted that it was being loaded in the Xorg.0.log file.

Yet still!  X is getting event data from the tablet!

So there must be some autoconfiguration going on somewhere, anyone have any ideas?

---

### Post by mesilliac on 2008-10-29
What version of Ubuntu are you running?

In 8.10 (intrepid), the tablet will autoconfigure based on the HAL rules specified in /usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi

I don't think this applies to previous versions but I could be wrong.

If it's being autoconfigured in this way you can change the settings by adding a custom .fdi file to /etc/hal/fdi/policy

I've tested the following one and it disables the X cursor movement due to my tablet while still allowing programs to capture the input:

/etc/hal/fdi/policy/mytabletrules.fdi
```

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">

  <device>
    <match key="info.capabilities" contains="input">
      <match key="info.product" contains="Wacom">
	<merge key="input.x11_options.TPCButton" type="string">on</merge>
	<merge key="input.x11_options.KeepShape" type="string">on</merge>
	<merge key="input.x11_options.SendCoreEvents" type="string">false</merge>
      </match>
    </match>
  </device>

</deviceinfo>

```

The TPCButton and KeepShape options are just non-default options that I prefer, the SendCoreEvents one is the relevant one.


Additionally with the graphire bluetooth, you want to make sure you've compiled and installed the kernel module as per the instructions on [https://help.ubuntu.com/community/WacomGraphireBluetooth](https://help.ubuntu.com/community/WacomGraphireBluetooth) ... if the module hasn't installed correctly you might get a compatibility mode which may not react correctly and won't give pressure sensitivity as it is not using the wacom driver at all.

You do want to make sure the wacom driver is working normally, as you'll need it to decipher the tablet commands in any case.

One last thing: in 8.10 if you want to configure your tablet using xorg.conf, you need to add these lines to turn off autoconfiguration (again, not sure if this applies to earlier versions of ubuntu):

```

Section "ServerFlags"
        Option "AutoAddDevices" "False"
EndSection

```

---

### Post by nebulus-design on 2008-10-29
Ah great stuff!

I'm running 7.10 at the moment, but will be upgrading to 8.10 at the weekend, so all this is great info.

I'm pretty sure that hal (or some other thing) is doing the automagic configuration at the moment, can't quite work out where its happening, but given you've had success, I'll wait till I upgrade and then give it another bash.

Many thanks for your help!

---

### Post by mesilliac on 2008-11-05
I've updated the modified hidp kernel module and updated the link on [https://help.ubuntu.com/community/WacomGraphireBluetooth](https://help.ubuntu.com/community/WacomGraphireBluetooth) .

No real changes, just made it easier to maintain and updated it to sync with the version in the 2.6.27 kernel. The module should be compatible with other bluetooth HID devices now.

The changes will also make it much easier to convert this to a proper driver for kernel 2.6.28 and later.

New modified hidp module source is at [https://sourceforge.net/tracker2/download.php?group_id=69596&atid=525126&file_id=300353&aid=1908703](https://sourceforge.net/tracker2/download.php?group_id=69596&atid=525126&file_id=300353&aid=1908703)

If anyone has any problems with the new version, let me know here. It should work just the same as the old one.

---

### Post by Clochard on 2008-11-07
Just upgraded to Intrepid.  Frankly I like the hal approach better, though I miss being able to configure things to my liking.

With the hal approach - is there a way to control the behavior of the stylus buttons?  Right now it looks like the bottom button is a double click, but only if I hold it down and tap the tip of the stylus to the tablet.  Using the xorg method in Hardy I could assign the button itself to double click, for example.  Now it is as though the two buttons are just modifiers for the stylus tip.

So using hal, if I want to right click something, I have to hold down the top button, and while holding it down tap and release onscreen.  Typically my hands aren't delicate enough for this and the desktop interprets my tap and release as a drag event.  It would be much easier if I could just click the button rather than having to then tap the tablet.

I tried adding the following to the fdi file, straight from my xsetwacom script from hardy, but it doesn't seem to have any effect at all.

Does anyone have any success in changing this behavior without resorting to xorg?  I really hated having to switch terminal every time the tablet was powered off.
```

<merge key="input.x11_options.button3" type="string">3</merge>
<merge key="input.x11_options.button2" type="string">2</merge>
<merge key="input.x11_options.button1" type="string">1</merge>
```

---

### Post by mesilliac on 2008-11-07
The behaviour of only clicking the buttons when you touch with the tip of the stylus comes from the "TPCButton" option, which was in the example .fdi file at [https://help.ubuntu.com/community/Wacom.fdi](https://help.ubuntu.com/community/Wacom.fdi), were you using this? :)

I think it was the non-default option, but in any case you should be able to change it to the normal behaviour by adding a merge line to your custom .fdi file:
```

<merge key="input.x11_options.TPCButton" type="string">off</merge>

```

You should be able to set most options using the custom .fdi file method, detailed at [https://help.ubuntu.com/community/Wacom.fdi](https://help.ubuntu.com/community/Wacom.fdi).

The options are the same as the xorg.conf options, and as the xsetwacom options, so you can see what can be set via "man wacom", or at [http://linuxwacom.sourceforge.net/index.php/howto/inputdev](http://linuxwacom.sourceforge.net/index.php/howto/inputdev).

Also, I think xsetwacom still works, but you have to pass the exact name of the device to it, and it won't list it for you. The exact name should be "Wacom Graphire 6x8 BlueTooth", you'll need to keep the quotes for the xsetwacom command. "xinput list" should list the tablet, giving the exact name, in case it's different.

---

### Post by Clochard on 2008-11-07
Awesome - that was it.  Sorry, should have read up on that option.  Now that I've been using it for some time it is starting to feel natural though :)  I'll fiddle and find what works - thanks!

---

### Post by mesilliac on 2008-11-16
I just found out that setting up your tablet xorg.conf does NOT remove the hotplug functionality...

If you set up your tablet in xorg.conf, as well as using the custom .fdi file method, then it seems to work as follows:

 * You need to have your tablet turned on when you log in for the xorg.conf setup to be recognised
 * After this when you turn your tablet on it works as currently, with only the stylus working
 * Switching VTs and back (CTRL-ALT-F6 then CTRL-ALT-F7) gives you the xorg.conf functionality (stylus, cursor, eraser, pad).

This is the most useful setup for me: hotplug works fine if I just need to quickly use the stylus, but if I need to do some serious work I can use the old tricks to activate the eraser etc.

---

### Post by mertulas on 2008-11-23
Hi,

I have a problem connecting my wacom graphire bt device with my ubuntu intrepid 8.10

I did everything mentioned in this [wiki topic]("https://help.ubuntu.com/community/WacomGraphireBluetooth") but no luck.

After pairing my device from bluetooth settings, it recognises the wacom pen tablet and connects successfully, but my mouse cursor doesn't move at all. I know the tablet is connected cause it is even giving me the green color whenever I move the stylus on it but I guess x.org just doesn't recognise it as a input device.

I did all the things mentioned in that wiki, even tried modifying x.org file mentioned in [this wiki topic]("https://help.ubuntu.com/community/Wacom") as well. Still no luck :(

Any help will be appreciated. Thanks.

---

### Post by mesilliac on 2008-11-24
Hi mertulas,

It seems the prebuilt version of the linuxwacom drivers that the wiki page tells you to use doesn't install cleanly anymore. Did you try compiling the linuxwacom drivers manually?

If you used the install script ("./install" method) this could be the problem. There are instructions at [https://help.ubuntu.com/community/Wacom/LatestDriver](https://help.ubuntu.com/community/Wacom/LatestDriver) for compiling manually but I'll summarise here:

If you've deleted it, re-download the latest linuxwacom driver and extract to your desktop. Then run the following commands in a terminal:

```

cd Desktop/linuxwacom-0.8.1-6/prebuilt
sudo ./uninstall
cd ..

sudo apt-get install build-essential
sudo apt-get build-dep wacom-tools
./configure --prefix=/usr
make
sudo make uninstall
sudo make install

```

Then restart X by logging out then logging back in.

If it's still not working can you tell me the output of ```
xidump -l
```? There should be either "stylus", "eraser", "cursor" devices or a "Wacom Graphire 6x8 BlueTooth" device. You can usually test the tablet input with one of ```
xidump stylus
  or
xidump "Wacom Graphire 6x8 BlueTooth"

```

I'll update the wiki page to only advise compiling in stead of using the prebuilt drivers.

---

### Post by mertulas on 2008-11-24
Hey mesilliac,

It just works perfect now :popcorn: Thanks a lot for the advice. Oh by the way, the speed of the mouse/stylus was very low so I had to take sensitivity and acceleration settings to max from mouse settings. Is there any other ways to improve sensitivity and speed? Also the mouse wheel works but it is inverted (upside-down) Is there a way to normalize it?

Thanks a lot again,

Mert

---

### Post by mesilliac on 2008-11-24
You should be able to tweak most of the tablet settings by running "wacomcpl".

After you have the settings how you like them, take a look at the "xsetwacom" lines in the ".xinitrc" file that wacomcpl saves in your home directory. You can either add these settings to your xorg.conf as options, or you can make a script containing the xsetwacom lines and set it to run at startup :).

e.g. .xinitrc:
```
xsetwacom set cursor Button5 "Button 4"
xsetwacom set cursor Button4 "Button 5"
```
 --> xorg.conf
```
  Option "Button5" "Button 4"
  Option "Button4" "Button 5"
```
 --> mywacomscript.sh
```
#!/bin/bash
xsetwacom set cursor Button5 "Button 4"
xsetwacom set cursor Button4 "Button 5"
```

---

### Post by mesilliac on 2008-11-24
Oh, seems you can't invert the scrollwheel by swapping the buttons... the correct options are "RelWDn" and "RelWUp":

```

xsetwacom set cursor RelWDn 5
xsetwacom set cursor RelWUp 4

```


edit: grr, new page... check previous page for the main post

---

### Post by mesilliac on 2008-11-25
I've just posted a new version of the graphire-bt modified kernel module:

[https://sourceforge.net/tracker2/download.php?group_id=69596&atid=525126&file_id=302852&aid=1908703](https://sourceforge.net/tracker2/download.php?group_id=69596&atid=525126&file_id=302852&aid=1908703)

This version should fix numerous issues:
 * mouse scrollwheel is no longer inverted
 * mouse cursor no longer jumps around when waking up / scrolling
 * tablet buttons work
 * touching screen corners / edges is much easier

Let me know if there are any problems :).

---

### Post by mertulas on 2008-11-29
The new version is just perfect, no complaints at all =D>

---

### Post by Clochard on 2008-11-29
How do you get the tablet buttons working?  For example I'd like to configure them to be PgUp and PgDn.  This line is the .fdi file doesn't seem to work because I think it is modifying the stylus button setting, rather than the pad button setting.

<merge key="input.x11_options.button6" type="string">core key pgup</merge>

I also tried button 4, as a wild guess.  I couldn't see using xev what the input looked like, and pad buttons don't make anything happen in xev.  Maybe I'm using the wrong tool?

If we can't configure them, what's the default action when you say they work?

Also, since I'm using the .fdi file approach, wacomcpl doesn't detect my device to help with configuration.  Maybe that should go on the wiki if it is expected behaviour?

One final thing ... is it true that Jaunty is going back to the xorg.conf mechanism rather than the .fdi approach?

---

### Post by mesilliac on 2008-11-29
Unfortunately the buttons will only work if you configure via xorg.conf, as they are handled by the "pad" device, which is not set up when hotplugging.

For now I recommend configuring using both the .fdi file and xorg.conf.

For testing the button functionality I used ```
xsetwacom set pad Button1 "core key whatever"
xsetwacom set pad Button2 "core key whatever"
```

It looks at this point like Jaunty **will** go back to using xorg.conf for tablet setup by default. There hasn't been much progress with getting the wacom devices set up properly via HAL, and there are still problems like the one you mention with wacomcpl (the device names "stylus" "eraser" etc are actually hardcoded into wacomcpl so it doesn't work with devices named anything else)

It should still be just as easy to use the custom .fdi file in Jaunty to get stylus hotplug... but unfortunately it doesn't look like hotplug support will be improved for the other devices.

---

### Post by riesengreen on 2008-12-04
Hello all, 

Just want to confirm:

As of now, there is NO WAY to configure a Wacom tablet to work with Ubuntu without compiling a kernel on the command line? Is this correct? 

I read somewhere that kernels can be installed in the Synaptic Package Manager...

Thanks for the help,

A Beginner

---

### Post by Clochard on 2008-12-04
There's no need to compile an entire kernel, just a module, which is inserted into the kernel.  Kind of like a driver.

I'd urge you to try it, the work in this thread has resulted in it being quite easy and well documented.  Plus there's lots of eyes on this thread to help out.

---

### Post by riesengreen on 2008-12-05
Thanks for the encouragement Clochard!

I will be back--definitely with questions and eventually with a working tablet!

---

### Post by nebulus-design on 2008-12-07
> **mesilliac said:**
> I've just posted a new version of the graphire-bt modified kernel module:

[https://sourceforge.net/tracker2/download.php?group_id=69596&atid=525126&file_id=302852&aid=1908703](https://sourceforge.net/tracker2/download.php?group_id=69596&atid=525126&file_id=302852&aid=1908703)

This version should fix numerous issues:
 * mouse scrollwheel is no longer inverted
 * mouse cursor no longer jumps around when waking up / scrolling
 * tablet buttons work
 * touching screen corners / edges is much easier

Let me know if there are any problems :).
I found that after updating to this new wacom-bt-driver package the buttons around the edge of the tablet stopped working, the earlier code from 2008-10-06 does work fine still. 
Was going to investigate further, however my favorite tool for checking and merging files and directories kdiff3 isn't in 8.10, so I haven't been able to dig into this issue yet.

---

### Post by mesilliac on 2008-12-12
> **nebulus-design said:**
> I found that after updating to this new wacom-bt-driver package the buttons around the edge of the tablet stopped working, the earlier code from 2008-10-06 does work fine still.
Ahh, I didn't think anyone would be using that functionality... It was a bunch of extra code unique to this driver (entirely implemented in software), so when I synced with the linuxwacom USB graphire driver it was much easier and cleaner to simply remove it. 

I think the margins are better used the same way as USB tablets do - to extend the surface area of the screen edges and corners. Extra functionality for screen edge clicks should really be in higher-level software.

Was the emulated button functionality very important to you? I can't think of a way to leave it in without removing the ability to use screen edges / corners.

---

### Post by mertulas on 2008-12-18
Ok here is another question, whne I log on to ubuntu for the first time, only my pen works, after I logged on pressing the F6(or F1)-F7 combination doesn't enable the mouse. Only after logging out my mouse gets activated in the login screen. Is there any way to have the mouse active on the first time?

---

### Post by mesilliac on 2008-12-18
Hmm, if the mouse is not working at the login screen you can try hitting CTRL-ALT-BACKSPACE (from the login screen, with the tablet on), which should forcibly restart the X server.

Not a great solution I know, but better than having to log in and out repeatedly.

---

### Post by BatPenguin on 2009-03-22
Hello everybody. First of all, thanks for the great how-to's to all who are contributing, I'm looking into buying a drawing tablet, and wanted to make sure I get something that's well supported. Looks like Wacom is pretty much the only option for Linux, I was very happy to see these forums with such nice how-to's and all.

Anyhow, I'd like a bluetooth tablet instead of a USB one, and since I can't find a list of "supported hardware", I thought I'd ask here: do all wacom bluetooth tablets work? Or is there a compatibility list somewhere? 

At the moment, I'm looking at that:

[http://www.wacom.eu/index2.asp?pid=163&lang=en](http://www.wacom.eu/index2.asp?pid=163&lang=en)

That's the Wacom Wireless Pen Tablet, Graphire3 Classic XL, A5, Bluetooth. Anybody using it? This would be probably for GIMP use, my wife could use one and I think our kids would love a drawing tool as well. TuxPaint is a great hit here, do these pens work in it?

Thanks in advance - and sorry if these are very simple questions, very new to these drawing tablets.

---

### Post by Clochard on 2009-03-28
I have the bluetooth model, and the info in this thread and the linked-to Howto's applies directly to this model.

---

### Post by tullis on 2009-04-16
> **mesilliac said:**
> I've just posted a new version of the graphire-bt modified kernel module:

[https://sourceforge.net/tracker2/download.php?group_id=69596&atid=525126&file_id=302852&aid=1908703](https://sourceforge.net/tracker2/download.php?group_id=69596&atid=525126&file_id=302852&aid=1908703)

This version should fix numerous issues:
 * mouse scrollwheel is no longer inverted
 * mouse cursor no longer jumps around when waking up / scrolling
 * tablet buttons work
 * touching screen corners / edges is much easier

Let me know if there are any problems :).

Can you (or someone) please post a link to to the *list* of hidp modules, rather than just the download links, because these links just go dead.

The link above is dead, for example.
I have got the module dated 2008-06-14 compiled and working in Jaunty (beta), but the mouse scroll wheel is reversed.

When I search Sourceforge for wacom-bt-driver it returns nothing. If I select the linuxwacom project it does not list the Bluetooth driver amongst the available files.

Many thanks.
Ben

---

### Post by mesilliac on 2009-04-18
**The most recent driver *does not* work in jaunty.**
        *(update: see next post for an updated driver)*

I'm currently working on updating the driver for jaunty. With the changes in the kernel I should be able to write a proper driver for it now.

If anyone knows anything about making an ubuntu package for a kernel module, could they PM me? :)

For now, on intrepid you can still use the previous drivers, and tullis reports that the 2008-06-14 version works with jaunty. You can download them from:
[https://sourceforge.net/tracker/index.php?func=detail&aid=1908703&group_id=69596&atid=525126](https://sourceforge.net/tracker/index.php?func=detail&aid=1908703&group_id=69596&atid=525126)


@BatPenguin:
Sorry for the late reply :(. I believe that wacom are still using the same models (it has the Graphire3 base) for wireless tablets, just with a different name. So "Graphire Bluetooth", "Graphire Wireless", "Wireless Pen Tablet" are probably all the same.

I still would strongly recommend a wired model for family use though, mainly because the wireless tablets aren't officially supported.


@tullis:
The link above should be what you want. The page the downloads are on is on linuxwacom's sourceforge tracker, under "patches" (search for bluetooth). Unfortunately its link changes as often as the download link does.

I'm hoping I can get a proper driver written soon, which could be included in the linuxwacom project.

---

### Post by mesilliac on 2009-04-26
Okay I've got a new driver written and it seems to be working perfectly...

***[SIZE="3"]This driver will only work in jaunty[/SIZE]***

[https://sourceforge.net/tracker/?func=detail&aid=2781875&group_id=69596&atid=525126](https://sourceforge.net/tracker/?func=detail&aid=2781875&group_id=69596&atid=525126)

(scroll down to attached files to download)

To install, extract it somewhere and cd there in a terminal, then:

```
make
sudo make install
```

The tablet should (hopefully) immediately work, with no need to reboot or anything.

If you have a custom .fdi file in /etc/hal/fdi/policy/ you should remove it, or update it somehow (details in the next post).

[size=3]**To get the tablet driver to load automatically at boot:**[/size]
```
gksudo gedit /etc/modules
```
Open /etc/modules and add the following on a new line:
```
hid_wacom_bt
```
After saving, the wacom module will be loaded at boot, so the tablet should work asap. (I'm not sure of the proper way to do this but this works for now)

[size=3]**Things that should be working:**

* stylus, mouse, eraser, pad (top buttons)
* hotplug (turn it on anytime, no more logging out/in)
* all tablet features

**I could use some feedback before updating the wiki, is this working for anyone?**[/size]

---

### Post by mesilliac on 2009-04-27
I've got the custom .fdi file method of configuration working great. It seems that all tool types can now be configured in this way (stylus, eraser, etc).

Here's mine as an example (adjust to taste):

[size=3]**/etc/hal/fdi/policy/custom_wacom.fdi**[/size]
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">

  <device>
    <match key="input.x11_driver" contains="wacom">
      <match key="input.x11_options.Type" contains="stylus">
        <merge key="input.x11_options.TPCButton" type="string">on</merge>
        <merge key="input.x11_options.KeepShape" type="string">on</merge>
        <merge key="input.x11_options.Threshold" type="string">1</merge>
        <merge key="input.x11_options.PressCurve" type="string">50,0,100,50</merge>
      </match>
    </match>
    <match key="input.x11_driver" contains="wacom">
      <match key="input.x11_options.Type" contains="eraser">
        <merge key="input.x11_options.TPCButton" type="string">on</merge>
        <merge key="input.x11_options.KeepShape" type="string">on</merge>
        <merge key="input.x11_options.Threshold" type="string">1</merge>
        <merge key="input.x11_options.PressCurve" type="string">50,0,100,50</merge>
      </match>
    </match>
  </device>

</deviceinfo>
```

The option lines are the <merge> ones, and these may be modifed, added or removed.

I assume for the cursor and pad you can also set options if necessary.

wacomcpl doesn't work at all for me currently, but as mentioned above xsetwacom works if you use the name of the device as reported by "xinput list --short", for example:

```
xsetwacom set "Wacom Pen Tablet" RawSample "2"
xsetwacom set "Wacom Pen Tablet" ClickForce "1"
xsetwacom set "Wacom Pen Tablet" PressCurve "50 0 100 50"
xsetwacom set "Wacom Pen Tablet eraser" RawSample "2"
xsetwacom set "Wacom Pen Tablet eraser" ClickForce "1"
xsetwacom set "Wacom Pen Tablet eraser" PressCurve "50 0 100 50"
xsetwacom set "Wacom Pen Tablet" TPCButton "on"
```

[size=3]***NOTE**: the xsetwacom commands and the <merge> options sometimes have different names... watch out*[/size]

---

### Post by Corvix on 2009-04-27
Works like a charm, even the fdi config is quite convenient! Just turn off the tablet, change custom fdi, turn on again and changes take effect.
I only wonder how I can assign the two buttons on the graphire to zoom in and out in Gimp?

Thanks soo much Tommy!

---

### Post by Clochard on 2009-04-29
I upgraded to Jaunty and have confirmed that your driver and instructions work perfectly.

I haven't played with the fdi file yet and haven't set up the eraser or pad buttons as I've grown used to not using them.  I'll report back once I get those changes in.

Thanks a bunch for making this completely awesome!

---

### Post by Clochard on 2009-05-01
Yikes, just when things seem smooth ...

I've been seeing strange black artifacts on non-focused windows etc, so I used envyng to re-install the latest nvidia drivers as those weren't upgraded for jaunty (I don't think).  After installing I rebooted (not the first time rebooting since installing the drivers I think).

Upon coming back up, my tablet didn't seem to work at all.  Neither the mouse nor the pen.  In Intrepid I often saw this and simply had to repair the tablet (using keyboard only to do so).  This time I tried repairing and even after several successful attempts, had no success getting the tablet pen or mouse working.

I then re-installed the hid driver and find now that the mouse works, and the pen.

Somehow reinstalling the nvidia drivers required that I reinstall the wacom driver?  I'm afraid to reboot now as I don't want to spend another hour trying to get it working again.  I can reboot though if you want me to check if it is reproducible.

---

### Post by mesilliac on 2009-05-01
I think this is a packaging problem. Every time something messes with the kernel, the tablet module gets cleaned away, so needs to be reinstalled.

It should stay working until the next kernel (or nvidia) update in any case.

If it does break again, just reinstalling the hid_wacom_bt driver should be enough to fix it. Let me know if it does break again next boot, but I think it should be ok :).

---

### Post by A.Wingrove on 2009-05-04
Just wanted to let you know it's working great me. I just installed the driver and my tablet is working fine. Pen and mouse are OK, as is pressure in GIMP. Great work!

---

### Post by Clochard on 2009-05-07
A few strange things to report:

1 - after using the mouse, the pen doesn't work.  The light changes colour but the input is not put through the the desktop.  I power off and then on the tablet and the pen works fine.  I can move from pen to mouse without problems.

2 - I use gestures via EasyStroke.  After upgrading, the scale of my strokes are way off.  A small stroke now rips across the screen, being highly over sensitive.  A slight movement is interpreted as a large movement, so even slight shakes of my hand are being interpreted as gestures.  This is causing a lot of misfired gestures, making it much less enjoyable.  Not sure if this is the driver or not.  I've tried tweaking easystroke and when painting the stroke on the screen I can see that the gesture is vastly over sized.

Not sure if there's anything you can do about this, but you asked :P

---

### Post by silentsnake on 2009-05-13
I seem to be having it somewhat working, other than that my Wacom tablet is responding veeeeeery slow. Pretty much up a level where it is not usable. I followed the procedure described here and also used the same .fdi file. Is there anything else I can check or other info required? FWIW, I use a Dell Latitude D830 with an external USB Bluetooth dongle. The tablet itself seems to work apart from the speed.

Thanks for the help in advance, I really would like my tablet to be working again.

---

### Post by Clochard on 2009-05-13
Not sure what you mean by speed.  I initially had problems with responsiveness, where moving my mouse or pen resulted in a lagged movement onscreen.

That I think was solved by making sure the tablet was close enough to my bluetooth adapter.  At the time I had it several feet away, and moving to within a few inches solved the problem.

However that was in Hardy or something I think.  Since Intrepid I've had the adapter around a meter away under my desk and have no problems.

If this wasn't what you meant by slow, could you elaborate a bit?

---

### Post by silentsnake on 2009-05-14
Yes, sorry, I was refering to the responsiveness. It is indeed having a lagged movement on screen, where the movement has about 1-2 seconds delay before it actually starts moving the mouse cursor. Which makes it, quite frankly, pretty much unusable.

I have already tried having my tablet very close to my bluetooth adaptor, but that didn't really seem to help. Note that I am running Jaunty, so it cannot be an old version issue either. I did manage to have my tablet working on 8.04, but in 9.04 it seems to be no avail.

I hope that this elaborates some.

---

### Post by Clochard on 2009-05-14
It does help - it sounds exactly like the problem I was having.

Check back on page 2 of this thread, mesilliac and I both had this problem and it looks like it was a driver issue, and reinstalling resolved it.

Try following the steps one by one again?

---

### Post by silentsnake on 2009-05-14
Thanks for your reponse, Clochard. Unfortunately, having my tablet in 5 cm range of my bluetooth adaptor still has the same lag effect as I have when keeping it 2 meters away. Also, after disconnecting my Bluetooth adaptor it doesn't seem to be getting released by xinput, as re-inserting my bluetooth adaptor produces the error:

(II) XINPUT: Adding extended input devide "Wacom Pen Tablet" (type: Wacom Stylus)
(EE) Wacom Pen Tablet: Top/Bottom area overlaps with other devices
(II) UnloadModule: "wacom"
(EE) config/hal: NewInputDeviceRequest failed (1)

If I turn off the tablet and turn it back on again it does actually work, but I still have the same lag of my mouse cursor as I always have. Should I post my Xorg.log or won't that be any use?

I also tried renstalling the driver by turning off my tablet, removing the adaptor and ran make + make install again on the source code. It compiles normally but it still has the same problem.

---

### Post by mesilliac on 2009-05-15
Hi silentsnake,

I think you have found the relevant part of your xorg.log, but i have to admit  i'm kind of stumped.

Have you tried removing your custom .fdi file?

You can check if x thinks the tablet is still connected with:
```

    xinput list --short
or  xinput list

```

---

### Post by mesilliac on 2009-05-15
Hmm, I just ran "xinput list" and noticed some ghost devices on my own machine... they weren't affecting anything but I managed to really mess things up by fiddling with the loaded kernel modules.

I can't seem to reproduce it now, tho.

silentsnake, Clochard, can either of you find a reproducible way of getting the xinput devices to fail to unload? (check with "xinput list", the ghost devices have no properties other than a name)


@Clochard

I tried to reproduce your problem with EasyStroke, but it works normally for me.  Do you have an "accelleration" or "speed" (i forget the name) value in your custom_wacom.fdi?  It sounds a little like a cursor acelleration thing.

I think the other problem with the mouse and pen might be the same problem as silentsnake's, that I haven't consistently reproduced yet.

---

### Post by riesengreen on 2009-05-16
I would like to say how awesome it is that tablets can be used with ubuntu, and to say thank you to everyone who has been involved with the programming.



So, you are saying that there is no GUI to install the Wacom driver for Jaunty. If not, then I would like to ask:

In the following sentence,

"To install, extract it somewhere and cd there in a terminal, then:"

what does this part

"...and cd there in a terminal"

I know that I need to use the command line terminal, and I know that I will enter some text strings in at the command line, that will change my...setup--but beyond this point I am a little shaky. 

Some screenshots of the process would be awesome...

---

### Post by mesilliac on 2009-05-16
Hi riesengreen,

Just to make sure: this is specifically for the Wireless Wacom tablet (uses bluetooth, has various names). Other Wacom tablets should work "out of the box" now in Jaunty, with no extra install necessary.

For these tablets though, you're right in saying that there is no GUI for the install.

Screenshots on the wiki page ([ here ](https://help.ubuntu.com/community/WacomGraphireBluetooth)) and a proper description of the process would be really helpful, but I haven't yet found the time for it.

In fact if you, or someone else, were to do this it would be greatly appreciated :).

In any case, the missing pieces of info are:

Download the file to your desktop and right-click->Extract_Here to extract (the desktop is easiest for instructions).

Open a terminal (Accessories>Terminal) then:
```

user@computer:~$ sudo apt-get install build-essential linux-headers-generic
[sudo] password for user:
   [...]
user@computer:~$ cd Desktop/hid-wacom-bt
user@computer:~/Desktop/hid-wacom-bt$ make
   [...]
user@computer:~/Desktop/hid-wacom-bt$ sudo make install
   [...]
```
 * The top line just makes sure your system has everything it needs to run "make".
 * The "cd" command changes to the folder "hid-wacom-bt" on your desktop,
 * "make" compiles the kernel module against your current kernel,
 * "make install" installs the module into your curent kernel.

The "make" / "sudo make install" needs to be done again if your kernel version changes (i.e. any update which requires a full computer restart), as it only installs to the current kernel.

---

### Post by Clochard on 2009-05-18
> **mesilliac said:**
> 
I tried to reproduce your problem with EasyStroke, but it works normally for me.  Do you have an "accelleration" or "speed" (i forget the name) value in your custom_wacom.fdi?  It sounds a little like a cursor acelleration thing.


Here's my .fdi - nothing about acceleration.

```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">

  <device>
    <match key="info.capabilities" contains="input">
      <match key="info.product" contains="Wacom">
        <merge key="input.x11_options.TPCButton" type="string">on</merge>
        <merge key="input.x11_options.KeepShape" type="string">on</merge>
        <merge key="input.x11_options.Mode" type="string">Relative</merge>
        <merge key="input.x11_options.Suppress" type="string">3</merge>
<!--        <merge key="input.x11_options.button3" type="string">3</merge>
        <merge key="input.x11_options.button2" type="string">2</merge>
	<merge key="input.x11_options.button1" type="string">1</merge>

	<merge key="input.x11_options.button6" type="string">core key pgup</merge>	
-->
      </match>
    </match>
    <match key="input.x11_driver" contains="wacom">
      <match key="input.x11_options.Type" contains="eraser">
        <merge key="input.x11_options.TPCButton" type="string">on</merge>
        <merge key="input.x11_options.KeepShape" type="string">on</merge>
        <merge key="input.x11_options.Threshold" type="string">1</merge>
        <merge key="input.x11_options.PressCurve" type="string">50,0,100,50</merge>
      </match>
    </match>
  </device>

</deviceinfo>
```

Maybe it is in my easystroke preferences?  See the two attached screenshots.  Any idea what that wacom timing setting is related to?

---

### Post by riesengreen on 2009-05-25
Thank you Messiliac!

No, I have a Wacom Graphire Bluetooth Tablet.

I'm gonna keep reading...

---

### Post by riesengreen on 2009-05-25
BTW:

Yes, as soon as I figure it out I will be certain to get screenshots for the page you mentioned.

BMR

---

### Post by LittleBot on 2009-05-28
Hey all, thanks for putting up this thread.  

I'm trying to get a graphire bt tablet working on a new install of 9.04.  I've downloaded and installed the module as describe previously, but after a short time, it stops working and eventually X crashes.

What I see in dmesg looks like the tablet loses connection, gets closed, then reopened by the hid_wacom_bt driver.  Unfortunately, in the X log, I start seeing hal error messages when this happens, eventually leading to a crash and X restart.

Any ideas?

Logs attached, cut to wacom sections.  Let me know if you need anything else.

---

### Post by brainsick on 2009-05-28
I have a USB mouse/keyboard hooked up to my computer.  If I get the Wacom Graphire Bluetooth device, will the mouse and the pen play nicely with my existing mouse/keyboard?  Do I end up with two mice controlling my X cursor?

---

### Post by LittleBot on 2009-05-28
It also turns out that there are multiple devices listed by 'xinput list'

$ xinput list --short
"Virtual core pointer"	id=0	[XPointer]
"Virtual core keyboard"	id=1	[XKeyboard]
"AT Translated Set 2 keyboard"	id=2	[XExtensionKeyboard]
"Macintosh mouse button emulation"	id=3	[XExtensionPointer]
"Video Bus"	id=4	[XExtensionKeyboard]
"AlpsPS/2 ALPS GlidePoint"	id=5	[XExtensionPointer]
"PS/2 Mouse"	id=6	[XExtensionPointer]
"Wacom Pen Tablet eraser"	id=7	[XExtensionKeyboard]
"Wacom Pen Tablet cursor"	id=8	[XExtensionKeyboard]
"Wacom Pen Tablet pad"	id=9	[XExtensionKeyboard]
"Wacom Pen Tablet"	id=10	[XExtensionKeyboard]
"Wacom Pen Tablet eraser"	id=11	[XExtensionKeyboard]
"Wacom Pen Tablet cursor"	id=12	[XExtensionKeyboard]
"Wacom Pen Tablet pad"	id=13	[XExtensionKeyboard]
"Wacom Pen Tablet"	id=14	[XExtensionKeyboard]
"Wacom Pen Tablet eraser"	id=15	[XExtensionKeyboard]
"Wacom Pen Tablet cursor"	id=16	[XExtensionKeyboard]
"Wacom Pen Tablet pad"	id=17	[XExtensionKeyboard]
"Wacom Pen Tablet"	id=18	[XExtensionKeyboard]
"Wacom Pen Tablet eraser"	id=19	[XExtensionKeyboard]



I would think that if I could clear hal's db, then this wouldn't be an issue.  Can't seem to find how to do that w/o restarting X or reboot.  Restart hal doesn't work.

---

### Post by LittleBot on 2009-05-28
> **brainsick said:**
> I have a USB mouse/keyboard hooked up to my computer.  If I get the Wacom Graphire Bluetooth device, will the mouse and the pen play nicely with my existing mouse/keyboard?  Do I end up with two mice controlling my X cursor?


Yes, they will both control the cursor since they register as input devices.  I can switch from pen to touchpad to laptop nipple w/o issue... 

when X doens't crash that is!

---

### Post by Clochard on 2009-05-29
I'm seeing strange things related to USB devices in jaunty, which sounds like yours somewhat.  Twice now when I've connected a device that is attached to my computer via a USB plug (once the tablet, another a media player) my X session has crashed, and I have had to hard power off the computer to recover.

I haven't checked my logs but I will next time it occurs.  It might be that your tablet isn't actually the problem here though - that's the point of my post.  it might be the reconnecting of the tablet that is throwing the problem.

Sorry I can't help more.

---

### Post by Clochard on 2009-05-29
Has anyone been able to assign keyboard shortcuts to the pad buttons with the new driver?  Anyone get them to work at all to do ... something?  if so please share how.

---

### Post by LittleBot on 2009-05-30
> **Clochard said:**
> I'm seeing strange things related to USB devices in jaunty, which sounds like yours somewhat.  Twice now when I've connected a device that is attached to my computer via a USB plug (once the tablet, another a media player) my X session has crashed, and I have had to hard power off the computer to recover.

I haven't checked my logs but I will next time it occurs.  It might be that your tablet isn't actually the problem here though - that's the point of my post.  it might be the reconnecting of the tablet that is throwing the problem.

Sorry I can't help more.

I'm reasonably convinced that the problem isn't with this driver specifically, but am not sure as it's the first hid driver I've looked at.  Even so, I get no error statements in syslog.

So you're not seeing this frequently, Clochard?  I get it every time, exactly 3 mins after turning the tablet on.  I did notice this in my syslog:

[INDENT] usb 2-2.4: USB disconnect, address 4
 btusb_intr_complete: hci0 urb ffff88003d8f43c0 failed to resubmit (19)
 btusb_bulk_complete: hci0 urb ffff88003d8f4600 failed to resubmit (19)
 btusb_bulk_complete: hci0 urb ffff88003d8f4240 failed to resubmit (19)
 btusb_send_frame: hci0 urb ffff88002611de40 submission failed
 wacom_bt_remove()
 usb 2-2.4: new full speed USB device using uhci_hcd and address 6
 usb 2-2.4: configuration #1 chosen from 1 choice
 wacom_bt_probe start[/INDENT]

Interestingly, it still responds and calls wacom_bt_raw_event afterwards, but no longer controls the cursor.

---

### Post by Clochard on 2009-05-31
Not frequently at all - twice since I upgraded to jaunty a week or so after its release.

Mind you I don't do a lot of USB hot plugging.

next time it happens I'll check dmesg and syslog for something interesting.

---

### Post by riesengreen on 2009-06-02
> **riesengreen said:**
> BTW:

Yes, as soon as I figure it out I will be certain to get screenshots for the page you mentioned.

BMR
Still working on it (slowly)...
Got this far and then stopped.

[IMG]http://upload.wikimedia.org/wikipedia/commons/0/03/Screenshot-5.png[/IMG]

[http://upload.wikimedia.org/wikipedia/commons/0/03/Screenshot-5.png]("http://upload.wikimedia.org/wikipedia/commons/0/03/Screenshot-5.png")

---

### Post by riesengreen on 2009-06-06
I feel like I should say sorry--

I really haven't yet had a chance to sit down and properly give the entire process a try. I promise not to post any more unclear messages (like my last one), etc., 'till I do.

Thanks all...

---

### Post by Clochard on 2009-06-08
OK, I've just experienced the USB-plugging problem.  Looking at the /var/log/messages output it does look like it is Wacom related.  Here's the story and related messages:

I've been using my tablet and computer for days now.  I turn off the monitor and tablet when I leave the computer.  That means I push the blue circle button to power it off.  When I return I power it back on, hit CTRL to get rid of the screensaver, and turn my monitor on.

Tonight, after using the tablet fine for several hours, it just turns off.  In the middle of using it, it just turns off.  This has happened before and it annoys me to no end - and only started occuring once I upgraded to the latest hid driver.

It is not battery related, as the thing has been plugged in for days and was plugged in when it turned off.

Here's messages when this happened:

```
Jun  7 22:31:11 Creativity kernel: [10257.286949] wacom_bt_remove() 
```

5 seconds later I realize the cursor isn't moving with me anymore, roll my eyes, and power it back on:

```
Jun  7 22:31:16 Creativity kernel: [10262.207512] wacom_bt_send_ctrl_message: session ffff880094969e00 data ffff88011d96da58 size 2
Jun  7 22:31:16 Creativity kernel: [10262.207516] wacom_bt_send_ctrl_message: session ffff880094969e00 data ffff88011d96da58 size 2
Jun  7 22:31:16 Creativity kernel: [10262.207570] input: Wacom Pen Tablet as /devices/pci0000:00/0000:00:04.0/usb4/4-2/4-2:1.0/bluetooth/hci0/hci0:11/input5
Jun  7 22:31:16 Creativity kernel: [10262.246961] wacom_bt 0005:056A:0081.0002: input,hidraw1: BLUETOOTH HID v1.00 Mouse [Wacom Pen Tablet] on 00:02:72:0F:5E:33
Jun  7 22:31:16 Creativity logger: device input5 is bound to the driver
Jun  7 22:31:16 Creativity logger: must rebind 
```

However when it comes back on (the blue light does that on, off, on again as it associated with the BT device) I cannot control my cursor with my pen.  I can see the blue light turning green as I touch the surface, so I know it is receiving it at the tablet level.

Sometimes I leave the thing alone and it seems to pick itself off the floor and work, so I leave it for a minute.  Sometimes it senses a problem with turns itself off, thinking the BT connection has gone away.  Not this time so after the minute I turn it off again

```
Jun  7 22:32:11 Creativity kernel: [10317.182445] wacom_bt_remove() 
```

I turn it back on

```
Jun  7 22:32:21 Creativity kernel: [10327.363520] wacom_bt_send_ctrl_message: session ffff88011d8b1d00 data ffff88011d96da58 size 2
Jun  7 22:32:21 Creativity kernel: [10327.363524] wacom_bt_send_ctrl_message: session ffff88011d8b1d00 data ffff88011d96da58 size 2
Jun  7 22:32:21 Creativity kernel: [10327.363578] input: Wacom Pen Tablet as /devices/pci0000:00/0000:00:04.0/usb4/4-2/4-2:1.0/bluetooth/hci0/hci0:11/input6
Jun  7 22:32:21 Creativity kernel: [10327.404582] wacom_bt 0005:056A:0081.0003: input,hidraw2: BLUETOOTH HID v1.00 Mouse [Wacom Pen Tablet] on 00:02:72:0F:5E:33
Jun  7 22:32:21 Creativity logger: device input6 is bound to the driver
Jun  7 22:32:21 Creativity logger: must rebind 
```

Still no control though it looks like it bound to the BT.  Giving up I say screw it and plug in my spare USB mouse.

```
Jun  7 22:32:44 Creativity kernel: [10350.588148] usb 3-5: new low speed USB device using ohci_hcd and address 3
Jun  7 22:32:44 Creativity kernel: [10350.800514] usb 3-5: configuration #1 chosen from 1 choice
Jun  7 22:32:45 Creativity kernel: [10350.830367] usbcore: registered new interface driver hiddev
Jun  7 22:32:45 Creativity kernel: [10350.837481] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.0/usb3/3-5/3-5:1.0/input/input7
Jun  7 22:32:45 Creativity kernel: [10350.868246] generic-usb 0003:046D:C51B.0004: input,hidraw3: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:02.0-5/input0
Jun  7 22:32:45 Creativity kernel: [10350.872873] generic-usb 0003:046D:C51B.0005: hiddev96,hidraw4: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:02.0-5/input1
Jun  7 22:32:45 Creativity kernel: [10350.872873] usbcore: registered new interface driver usbhid
Jun  7 22:32:45 Creativity kernel: [10350.872873] usbhid: v2.6:USB HID core driver 
```

As soon as I plug the mouse in I can contrl my mouse cursor.  I start to move it across the screen and blammo!  Black screen.  X has crashed.

```
Jun  7 22:32:47 Creativity kernel: [10353.010135] Xorg[3249]: segfault at 10 ip 00007f7329aa6c35 sp 00007fff3832f840 error 4 in wacom_drv.so[7f7329a98000+16000]
Jun  7 22:32:47 Creativity kernel: [10353.140612] NVRM: failed to unregister from the ACPI subsystem!
Jun  7 22:32:49 Creativity kernel: [10354.910382] NVRM: failed to register with the ACPI subsystem!
Jun  7 22:32:49 Creativity kernel: [10354.914583] ACPI Exception (utmutex-0263): AE_BAD_PARAMETER, Thread FFFF88010DD88000 could not acquire Mutex [1] [20080926]
Jun  7 22:32:50 Creativity kernel: [10356.008516] Xorg[9098]: segfault at 40 ip 0000000000496786 sp 00007ffff3bade20 error 4 in Xorg[400000+1c3000]
Jun  7 22:32:50 Creativity kernel: [10356.027134] NVRM: failed to unregister from the ACPI subsystem!
Jun  7 22:32:51 Creativity kernel: [10357.201214] NVRM: failed to register with the ACPI subsystem!
Jun  7 22:32:51 Creativity kernel: [10357.205543] ACPI Exception (utmutex-0263): AE_BAD_PARAMETER, Thread FFFF88010DD8D980 could not acquire Mutex [1] [20080926]
Jun  7 22:32:52 Creativity bonobo-activation-server (kirk-9132): could not associate with desktop session: Failed to connect to socket /tmp/dbus-sTsMfcuooe: Connection refused
Jun  7 22:32:52 Creativity kernel: [10358.400661] Xorg[9124]: segfault at 60 ip 0000000000496786 sp 00007fffc5f341a0 error 4 in Xorg[400000+1c3000]
Jun  7 22:32:52 Creativity kernel: [10358.408769] NVRM: failed to unregister from the ACPI subsystem!
Jun  7 22:32:54 Creativity kernel: [10360.345071] usb 3-5: USB disconnect, address 3
Jun  7 22:32:54 Creativity kernel: [10360.698415] NVRM: failed to register with the ACPI subsystem!
Jun  7 22:32:54 Creativity kernel: [10360.702608] ACPI Exception (utmutex-0263): AE_BAD_PARAMETER, Thread FFFF88011CC8D980 could not acquire Mutex [1] [20080926]
Jun  7 22:32:55 Creativity kernel: [10361.760874] Xorg[9157]: segfault at 20 ip 0000000000496786 sp 00007fff73b27da0 error 4 in Xorg[400000+1c3000]
Jun  7 22:32:55 Creativity kernel: [10361.779562] NVRM: failed to unregister from the ACPI subsystem!
Jun  7 22:33:00 Creativity kernel: [10365.953681] NVRM: failed to register with the ACPI subsystem!
Jun  7 22:33:00 Creativity kernel: [10365.958088] ACPI Exception (utmutex-0263): AE_BAD_PARAMETER, Thread FFFF88011D285980 could not acquire Mutex [1] [20080926]
Jun  7 22:33:01 Creativity kernel: [10367.065208] Xorg[9198]: segfault at 20 ip 0000000000496786 sp 00007fff23702960 error 4 in Xorg[400000+1c3000]
Jun  7 22:33:01 Creativity kernel: [10367.073673] NVRM: failed to unregister from the ACPI subsystem!
Jun  7 22:33:13 Creativity kernel: [10379.393715] NVRM: failed to register with the ACPI subsystem!
Jun  7 22:33:13 Creativity kernel: [10379.397924] ACPI Exception (utmutex-0263): AE_BAD_PARAMETER, Thread FFFF880115578000 could not acquire Mutex [1] [20080926]
Jun  7 22:33:14 Creativity kernel: [10380.438033] Xorg[9226]: segfault at 20 ip 0000000000496786 sp 00007fffb586bae0 error 4 in Xorg[400000+1c3000]
Jun  7 22:33:14 Creativity kernel: [10380.460274] NVRM: failed to unregister from the ACPI subsystem!
Jun  7 22:33:31 Creativity kernel: [10397.638036] NVRM: failed to register with the ACPI subsystem!
Jun  7 22:33:31 Creativity kernel: [10397.642217] ACPI Exception (utmutex-0263): AE_BAD_PARAMETER, Thread FFFF880112E85980 could not acquire Mutex [1] [20080926]
Jun  7 22:33:32 Creativity kernel: [10398.767161] Xorg[9251]: segfault at 20 ip 0000000000496786 sp 00007fffcb7e9a60 error 4 in Xorg[400000+1c3000]
Jun  7 22:33:33 Creativity kernel: [10398.789911] NVRM: failed to unregister from the ACPI subsystem!
Jun  7 22:35:36 Creativity kernel: [10521.875565] NVRM: failed to register with the ACPI subsystem!
Jun  7 22:35:36 Creativity kernel: [10521.879962] ACPI Exception (utmutex-0263): AE_BAD_PARAMETER, Thread FFFF88011557C320 could not acquire Mutex [1] [20080926]
Jun  7 22:35:37 Creativity kernel: [10522.942830] Xorg[9290]: segfault at 20 ip 0000000000496786 sp 00007fff7bcdbf20 error 4 in Xorg[400000+1c3000]
Jun  7 22:35:37 Creativity kernel: [10522.952442] NVRM: failed to unregister from the ACPI subsystem!
Jun  7 22:35:38 Creativity kernel: [10524.114441] NVRM: failed to register with the ACPI subsystem!
Jun  7 22:35:38 Creativity kernel: [10524.118685] ACPI Exception (utmutex-0263): AE_BAD_PARAMETER, Thread FFFF880115578000 could not acquire Mutex [1] [20080926]
Jun  7 22:35:39 Creativity kernel: [10525.270976] Xorg[9315]: segfault at 20 ip 0000000000496786 sp 00007fff70847aa0 error 4 in Xorg[400000+1c3000]
Jun  7 22:35:39 Creativity kernel: [10525.290502] NVRM: failed to unregister from the ACPI subsystem!
Jun  7 22:35:41 Creativity kernel: [10527.572437] NVRM: failed to register with the ACPI subsystem!
Jun  7 22:35:41 Creativity kernel: [10527.576874] ACPI Exception (utmutex-0263): AE_BAD_PARAMETER, Thread FFFF880112E84320 could not acquire Mutex [1] [20080926]
Jun  7 22:35:42 Creativity kernel: [10528.627178] Xorg[9340]: segfault at 20 ip 0000000000496786 sp 00007fff4c0262a0 error 4 in Xorg[400000+1c3000]
Jun  7 22:35:42 Creativity kernel: [10528.641066] NVRM: failed to unregister from the ACPI subsystem!
Jun  7 22:35:44 Creativity kernel: [10529.847158] ACPI Exception (utmutex-0263): AE_BAD_PARAMETER, Thread FFFF880094991660 could not acquire Mutex [1] [20080926]
Jun  7 22:35:45 Creativity kernel: [10530.971358] Xorg[9367]: segfault at 20 ip 0000000000496786 sp 00007fff7a0b9320 error 4 in Xorg[400000+1c3000]
Jun  7 22:35:51 Creativity kernel: [10537.275468] ACPI Exception (utmutex-0263): AE_BAD_PARAMETER, Thread FFFF88011557C320 could not acquire Mutex [1] [20080926]
Jun  7 22:35:52 Creativity kernel: [10538.323826] Xorg[9395]: segfault at 20 ip 0000000000496786 sp 00007fffa1a70ce0 error 4 in Xorg[400000+1c3000]
Jun  7 22:36:03 Creativity kernel: [10549.545620] ACPI Exception (utmutex-0263): AE_BAD_PARAMETER, Thread FFFF8801154A5980 could not acquire Mutex [1] [20080926]
Jun  7 22:36:04 Creativity kernel: [10550.652557] Xorg[9451]: segfault at 20 ip 0000000000496786 sp 00007fff005507a0 error 4 in Xorg[400000+1c3000]
Jun  7 22:36:24 Creativity kernel: [10569.962752] ACPI Exception (utmutex-0263): AE_BAD_PARAMETER, Thread FFFF88011CC8D980 could not acquire Mutex [1] [20080926]
Jun  7 22:36:25 Creativity kernel: [10571.029800] Xorg[9490]: segfault at 20 ip 0000000000496786 sp 00007fff1a976be0 error 4 in Xorg[400000+1c3000] 
```

I try to get it going again, it tries on its own.  All I can do is SSH in from another machine and reboot the system.  And here I am.  Tablet worked right off the bat as usual after the reboot.

Anyhow, as you can see the Xorg segfaults due to an error in wacom_drv.so, which is why I think this is related to the Wacom driver provided here.

If I can provide any more info please let me know.  I can't reproduce it as it always seems to revolve around when the tablet driver just stops working - which seems random.

Maybe at least you enjoyed my story!?

---

### Post by riesengreen on 2009-07-10
Messilliac and everyone:

Thanks for all of the advice!

Still trying to install the driver for my Wacom Bluetooth tablet here.

[http://sourceforge.net/projects/linuxwacom/]("http://sourceforge.net/projects/linuxwacom/")

I think that I remember reading in a forum post that in order to install tar.bz files, you first need to add a few packages with synaptic. I haven't done this, so maybe that's why it didn't work the first time I tried the process with the additional instructions that you sent...

Is this right, that I need to install something first before doing this kind of operation? If so, what do I need to install? I can't seem to find the post that I am thinking of here...

---

### Post by Clochard on 2009-07-13
You need to ensure the meta-package 'build-essential' is installed in order to compile anything.  You'll also need to make sure the header files for your particular kernel are installed too.  Use 'uname -r' to find out your kernel you're running.  Then install a package named something like "linux-kernel-headers-xx_version_xx", replacing xx_version_x with the output from uname -r.

This is all from memory so please let me know if this doens't work, or you need more details and I'll copy/paste from my Ubuntu box later tonight.

Here's [Ubuntu's documentation on compiling]("https://help.ubuntu.com/community/CompilingEasyHowTo").  It's more than what you want to do, but it is a good resource.  The checkinstall software is only useful if you want to generate a .deb package out of the software you compile for easy installation later or on other machines.  So in this case there's not much value in using it.

---

### Post by CraigMcW on 2009-07-19
guys, I've been out of practice with Linux for several years and am new to Ubuntu.  I cannot get my Wacom Bluetooth to work on a 64 bit HP Pavillion although it works great under Vista.

I've run the sudo apt-get install .....
I've followed all the other instructions, and the tablet's various devices are listed in gkinput.  

However, there is no response from the mouse or pen on the screen.

Here's the output of the make and sudo make install commands:
[INDENT]me:~/Public/hid-wacom-bt$ make
make CONFIG_DEBUG_INFO= -C /lib/modules/2.6.28-13-generic/build M=/home/me/Public/hid-wacom-bt/hid
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
  LD      /home/me/Public/hid-wacom-bt/hid/built-in.o
  CC [M]  /home/me/Public/hid-wacom-bt/hid/hid-wacom-bt.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/me/Public/hid-wacom-bt/hid/hid-wacom-bt.mod.o
  LD [M]  /home/me/Public/hid-wacom-bt/hid/hid-wacom-bt.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'

me@me-ubuntu-laptop:~/Public/hid-wacom-bt$ sudo make install
cp /home/me/Public/hid-wacom-bt/hid/hid-wacom-bt.ko /lib/modules/2.6.28-13-generic/kernel/drivers/hid/hid-wacom-bt.ko
depmod -a
modprobe -r hidp
modprobe -r hid_wacom_bt
modprobe hid_wacom_bt
me@me-ubuntu-laptop:~/Public/hid-wacom-bt$ 
[/INDENT]Is there something very basic that I am missing?  how can I trouble shoot this further please?

---

### Post by Clochard on 2009-07-20
I'd found that I have to have the tablet on and paired before logging in.   Have you tried logging out, ensuring the tablet is on and paired, and then logging in?

If that doesn't do it, can you post the last 50 lines of /var/log/syslog when you power your tablet on and off?

---

### Post by Clochard on 2009-07-20
On a separate topic, though related (I think): has anyone been able to get GIMP's pressure sensitive brushes working with the latest driver?

I've tried following [the official docs]("https://help.ubuntu.com/community/Wacom#Configuring%20the%20%22Extended%20Input%20Devices%22") on getting them set up.  If I change a device in GIMP to be "Screen" or "Window" then the brush stops working.  The symptom is when painting with the pencil or paint brush the actual contact is not registered in GIMP.  So even though I'm scribbling away on my tablet nothing shows on the screen and nothing happens in the undo history.  This tells me that GIMP is not even seeing the input.

As soon as I set the device to "Disabled" in the GIMP then the brush returns to normal.  Normal however does not have pressure sensitivity.

Do I need to enable something on the fdi side of things to get this working?  Any suggestions are welcome.

---

### Post by CraigMcW on 2009-07-25
> **Clochard said:**
> I'd found that I have to have the tablet on and paired before logging in.   Have you tried logging out, ensuring the tablet is on and paired, and then logging in?

If that doesn't do it, can you post the last 50 lines of /var/log/syslog when you power your tablet on and off?
Thank you Clochard.  I"m sorry it's been 5 days, I had to travel without this laptop.  

Amazing, thank you.  As I wanted to quote the lines in syslog after starting the tablet, I started Ubuntu with it off.  I turned it on, authorized its connection.... AND IT WORKED!

I haven't tested everything (pen) yet, but let's see.

---

### Post by Clochard on 2009-07-25
You can still see the same messages in syslog right now by turning it off and then on again - syslog has the same info as it would if you were booting.  The key difference (I think) is that X.org needs to see it when launching to load the correct drivers.  It doesn't seem to do that on the fly.  Once they're loaded you can turn it on and off all you want and it will work.  It just needs to be on during X.org launching.

This is all just observational mind you.

---

### Post by riesengreen on 2009-08-07
> **Clochard said:**
> You need to ensure the meta-package 'build-essential' is installed in order to compile anything.  You'll also need to make sure the header files for your particular kernel are installed too.  Use 'uname -r' to find out your kernel you're running.  Then install a package named something like "linux-kernel-headers-xx_version_xx", replacing xx_version_x with the output from uname -r.

This is all from memory so please let me know if this doens't work, or you need more details and I'll copy/paste from my Ubuntu box later tonight.

Here's [Ubuntu's documentation on compiling]("https://help.ubuntu.com/community/CompilingEasyHowTo").  It's more than what you want to do, but it is a good resource.  The checkinstall software is only useful if you want to generate a .deb package out of the software you compile for easy installation later or on other machines.  So in this case there's not much value in using it.
*
Everyone:

I feel like this might be surrender. 

Planning on heading to Free Geek this weekend to donate the Bluetooth tablet. 
Or I could give it to a school or laboratory.
I'll just look out for a USB tablet on the cheap.
It feels kind of lame...and in fact I enjoy all that I have learned thus far, but I just don't wanna wait anymore on using a tablet.

Everyone involved is doing a great thing in making tablets more accessible to use on Linux. I am lookin' forward to using a USB tablet in Jaunty and of course in the next versions.

I have written to Wacom more than once telling them how great it would be if they offered a Linux driver download for the masses...even Amazon has a Linux mp3 downloader package available!

Maybe if everybody hit their [Graphire Wireless Linux driver download page]("http://www.wacom.com/downloads/linux-drivers.php") (which is actually a paragraph and a link to [The Linux Wacom Project]("http://linuxwacom.sourceforge.net/")) it would send them a message.

(Kind of) Giving Up for Now

---

### Post by yafisb on 2009-11-02
wacom tablet in karmic


   I  have reinstalled the packages got it working but there seems to be a couple of seconds lag. I have a bluetooth wacom graphire tablet, I wasn't having these issues with jaunty. Is there a fix 'cuz the tablet is unusable

---

### Post by octesian on 2009-11-23
> **yafisb said:**
> wacom tablet in karmic


   I  have reinstalled the packages got it working but there seems to be a couple of seconds lag. I have a bluetooth wacom graphire tablet, I wasn't having these issues with jaunty. Is there a fix 'cuz the tablet is unusable
I'm having the same problem.

---

### Post by Niels Olson on 2009-11-25
same issue. PM'd mesilliac, just to let him know the issue exists. At least my issue is similar to this launchpad report: [https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/483453](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/483453)

---

### Post by Niels Olson on 2009-11-25
a bit more info. According to mesilliac's post on the sourceforge project, the bluetooth wacom has [kernel support as of 2.6.31]("http://sourceforge.net/tracker/?func=detail&aid=2781875&group_id=69596&atid=525126"). Kernelnewbies provides [a little amplification]("http://kernelnewbies.org/Linux_2_6_31") and provides a [link to the commit]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=ca2dcd40f54c8928b3994712a6cadd2078a087fa").

So now I'm doubly confused. Isn't a kernel driver the gold standard for peformance?

---

### Post by Corvix on 2009-11-26
Similar issue here ...
Tablet pairs with bluetooth, hid_wacom loads, stylus, eraser and cursor seem to be registered with X.org according to X.org Log no movement is recognised even though stylus clicks seem to be handled as mouse pointer clicks.

X.org Log excerpt:

	Information	config/hal: Adding input device WACOM Pen Tablet eraser
	From config file	WACOM Pen Tablet eraser: always reports core events
	From config file	WACOM Pen Tablet eraser device is /dev/input/event11
	From config file	WACOM Pen Tablet eraser is in absolute mode
	From config file	WACOM: suppress value is 2
	From config file	Option "BaudRate" "9600"
	From config file	WACOM Pen Tablet eraser: serial speed 9600
	Information	XINPUT: Adding extended input device "WACOM Pen Tablet eraser" (type: Wacom Eraser)
	From config file	Option "Device" "/dev/input/event11"
	Information	WACOM Pen Tablet eraser Wacom X driver grabbed event device
	Default setting	Wacom using pressure threshold of 30 for button 1
	Default setting	Wacom USB Graphire4 tablet speed=9600 (38400) maxX=16704 maxY=12064 maxZ=511 resX=2032 resY=2032  tilt=disabled
	Default setting	Wacom device "WACOM Pen Tablet eraser" top X=0 top Y=0 bottom X=16704 bottom Y=12064 resol X=2032 resol Y=2032
	Information	config/hal: Adding input device WACOM Pen Tablet cursor
	From config file	WACOM Pen Tablet cursor: always reports core events
	From config file	WACOM Pen Tablet cursor device is /dev/input/event11
	From config file	WACOM Pen Tablet cursor is in relative mode
	From config file	WACOM: suppress value is 2
	From config file	WACOM Pen Tablet cursor: reading USB link
	From config file	WACOM Pen Tablet cursor: threshold = 30
	From config file	WACOM Pen Tablet cursor: max x set to 16704 by xorg.conf
	From config file	WACOM Pen Tablet cursor: max y set to 12064 by xorg.conf
	From config file	WACOM Pen Tablet cursor: max z = 511
	From config file	Option "BaudRate" "9600"
	From config file	WACOM Pen Tablet cursor: serial speed 9600
	Information	XINPUT: Adding extended input device "WACOM Pen Tablet cursor" (type: Wacom Cursor)
	Default setting	Wacom device "WACOM Pen Tablet cursor" top X=0 top Y=0 bottom X=16704 bottom Y=12064 resol X=2032 resol Y=2032
	Information	config/hal: Adding input device WACOM Pen Tablet
	From config file	WACOM Pen Tablet: always reports core events
	From config file	WACOM Pen Tablet device is /dev/input/event11
	From config file	WACOM Pen Tablet is in absolute mode
	From config file	WACOM: suppress value is 2
	From config file	WACOM Pen Tablet: reading USB link
	From config file	WACOM Pen Tablet: threshold = 30
	From config file	WACOM Pen Tablet: max x set to 16704 by xorg.conf
	From config file	WACOM Pen Tablet: max y set to 12064 by xorg.conf
	From config file	WACOM Pen Tablet: max z = 511
	From config file	Option "BaudRate" "9600"
	From config file	WACOM Pen Tablet: serial speed 9600
	Information	XINPUT: Adding extended input device "WACOM Pen Tablet" (type: Wacom Stylus)
	Default setting	Wacom device "WACOM Pen Tablet" top X=0 top Y=0 bottom X=16704 bottom Y=12064 resol X=2032 resol Y=2032
	Information	wacom: rel event recv'd (0)!
	Information	wacom: rel event recv'd (1)!
	Information	wacom: rel event recv'd (0)!
	Information	wacom: rel event recv'd (1)!

---

### Post by mesilliac on 2009-12-09
Hi, sorry this has taken so long. I'm not sure why the tablet isn't working as it should with the driver in kernel 2.6.31, and unfortunately I don't have much time to look into it :(.

The driver I was using in Jaunty seems to still work ok though. I changed the name to overwrite the kernel driver and removed a couple unnecessary lines.

I'll attach it to this post, see if it works for you.

---

### Post by Liz.nogan on 2009-12-09
Heya! I just got a graphire tablet as well. I have an Inspiron B130. You need a bluetooth adapter

---

### Post by mesilliac on 2009-12-17
I've uploaded a modified version of the bluez package to a ppa. This should allow the graphire bluetooth to work with no extra fiddling.

Please add this ppa to your Software Sources and let me know if the updated packages enable the tablet.

[https://launchpad.net/~yobbobandana/+archive/ppa]("https://launchpad.net/~yobbobandana/+archive/ppa")

If you've installed the driver I uploaded previously you can uninstall it via the terminal:
```

sudo aptitude reinstall linux-image-`uname -r`

```
(backticks are important)

If the tablet doesn't work at first, try turning it off then back on again once.

---

### Post by Clochard on 2009-12-17
Thanks Tommy - seems to work.

it's been a little while since I've had to config the tablet - how is this done in Karmic?  For example switch the mode to relative, change the button mapping, etc?

---

### Post by mesilliac on 2009-12-18
The custom .fdi file method seems to still work:

[https://help.ubuntu.com/community/Wacom.fdi](https://help.ubuntu.com/community/Wacom.fdi)

You can also use xsetwacom from the wacom-tools package, but it needs to be run each time. The full name of the device must be used (found with "xinput list --short"), like
```

xsetwacom set "WACOM Pen Tablet" Mode "Relative"
xsetwacom set "WACOM Pen Tablet" Button2 "button 3"

```

for the .fdi file the mode and button option lines were something like:
```

  <merge key="input.x11_options.Mode" type="string">Relative</merge>
  <merge key="input.x11_options.Button2" type="string">button 3</merge>

```

---

### Post by Favux on 2009-12-18
Hi everyone,

I'd appreciate it if someone would test the rc2 .fdi in [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176") on the "Re: Wacom tablets in Ubuntu guide/howto" and see if it works for your bluetooth tablet.  You should be able to configure and calibrate with wacomcpl if it works for you.

---

### Post by MacAnkka on 2009-12-21
> **mesilliac said:**
> I've uploaded a modified version of the bluez package to a ppa. This should allow the graphire bluetooth to work with no extra fiddling.

Please add this ppa to your Software Sources and let me know if the updated packages enable the tablet.

[https://launchpad.net/~yobbobandana/+archive/ppa]("https://launchpad.net/%7Eyobbobandana/+archive/ppa")

If you've installed the driver I uploaded previously you can uninstall it via the terminal:
```

sudo aptitude reinstall linux-image-`uname -r`

```(backticks are important)

If the tablet doesn't work at first, try turning it off then back on again once.
It seems to work fine otherwise, but the pointer lags behind the pen a lot. 

The same tablet and same bluetooth adapter worked on a different computer with Jaunty and your drivers just fine. And the lag is the same when the tablet and adapter are right next to each other and when they are meters apart. So I don't think it's bad signal.

---

### Post by tullis on 2009-12-22
I can confirm that this method works for me too.

---

### Post by the_exodus on 2009-12-28
I can also vouch that between the tweaked Bluez, and adding the custom .fdi file using copied commands from the relevant Ubuntu documentation page that mine works as well.

It does not connect right away, but if I follow the procedure of pressing the connect button on the Wacom, then pressing the connect icon for the Wacom Device in Bluez (paired in a previous session), promptly turning it off and back on, and then it responds and works fine.

But there is a consistent 2 second lag between input and cursor action, rendering it still unusable and me frustrated. Had it for over a year now, and I still can not use the damn thing.

---

### Post by Reason NL on 2010-02-16
Still issues getting this device to work in 9.10. Someone else has started a thread concerning this issue in combination with blueman which renders the ppa fix unusable:

[http://ubuntuforums.org/showthread.php?t=1401033](http://ubuntuforums.org/showthread.php?t=1401033)

Anyone any thoughts on this?

---

### Post by Reason NL on 2010-03-10
Does anybody now what the fix within the bluez package is so it can be applied to the newest version? Or even better, included in the project itself?

---

### Post by Chronon on 2010-04-12
If you don't get a response you can probably get a decent idea by taking a diff of the PPA source against the proper revision of the bluez trunk.  Are you planning to work on this?

---

### Post by Reason NL on 2010-04-28
Well if you could somehow define the version of the trunk used by mesilliac to build his patch on, that would be a possibility, but if he would give us just that, he could also give us the changes he made. ;)
By the way, this tablet still doesn't work in Lucid Lynx (10.04) RC.
Starting to be sorry I ever bought the damn thing in the first place.. :(

---

### Post by mesilliac on 2010-05-04
Hi, I updated the version in the ppa for lucid. It can be added to Software Sources as ppa:yobbobandana/ppa

The version of bluez patched is just as listed in the package archive at [https://launchpad.net/~yobbobandana/+archive/ppa](https://launchpad.net/~yobbobandana/+archive/ppa)

I believe the patch is directly available there, as I do not upload the bluez source to the ppa, just the changes. But in any case I'll attach it here.

I don't have the time to get this patch included in ubuntu / upstream. If someone else would do this I'm sure it would be greatly appreciated.

The bluez patch simply sends a signal to the tablet when it connects to change out of it's basic low-speed HID compatibility mode to the high-speed mode with full functionality.

---

### Post by Chronon on 2010-05-07
Everything seems to be working fine for me now with the packages from the PPA (running Lucid here).  I also used a custom .fdi, but I'm not certain if it's necessary or not.

---

### Post by Reason NL on 2010-05-10
First things first. Thanks Mesilliac!

But unfortunately it still isn't working for some reason.
With no VDI i get mouse clicks registered, like it did without the patch. With the VDI it doesn't do anything at all.
What did you do exactly Chronon? I'm running a 10.04 upgrade from 9.10 here.

---

### Post by Chronon on 2010-05-10
This is also an upgraded system from 9.10 to 10.04.  I got updated packages from Mesilliac's PPA and I used custom .fdi from here:
[http://ubuntuforums.org/showpost.php?p=8519407&postcount=126](http://ubuntuforums.org/showpost.php?p=8519407&postcount=126)

I'm still trying to get pressure sensitivity working in the GIMP, but I can properly set and get pressure settings using xsetwacom, so it's probably my unfamiliarity with the GIMP that's at fault here.

---

### Post by Reason NL on 2010-05-11
Installed the custom fdi, but that still didn't do the trick.
Reinstalled bluez and now everything is working! Thanks all!

---

### Post by the_exodus on 2010-05-16
I can now confirm as of 10.04 that my Wacom runs flawlessly using this Bluetooth edit. Even the buttons and pressure sensitivity.

The consistent 2 second lag I had is gone, and it is running essentially straight out of the installation of the Bluetooth alteration.

Finally. Had to have had this thing almost two years now.

---

### Post by brainsick on 2010-08-02
Are there any changes to the procedures for Ubuntu 10.04?  Can someone update the wiki?

---

### Post by landandy on 2010-10-17
@[Favux]("http://ubuntuforums.org/member.php?u=699990") thank you for your reply.

root@X300:/home/llandthand# uname -r
2.6.35-22-generic-pae

To enable bluetooth-support to my intuos4 i tried this:
root@X300:/home/llandthand# sudo add-apt-repository ppa:yobbobandana/ppa
Then I changed with synaptic the version of the source from Karmic to Lucid.
Then apt-get update
Then sudo aptitude reinstall linux-image-`uname -r`
I did a reboot and made a new bluetooth-connection. 

My dmesg | grep wacom output looks different now, because there are now more devices. But it does not work.
root@X300:/home/llandthand# dmesg | grep wacom
[    3.679720] usbcore: registered new interface driver wacom
[    3.679725] wacom: v1.52:USB Wacom tablet driver
[   20.440986] wacom 0005:056A:00BD.0001: input,hidraw0: BLUETOOTH HID v1.06 Mouse [PTK-540WL] on 00:1F:3A:F3:47:51
[   46.087832] wacom 0005:056A:00BD.0002: input,hidraw0: BLUETOOTH HID v1.06 Mouse [PTK-540WL] on 00:1F:3A:F3:47:51
[  147.674280] wacom 0005:056A:00BD.0003: input,hidraw0: BLUETOOTH HID v1.06 Mouse [PTK-540WL] on 00:1F:3A:F3:47:51

Thank you for helping me!
Andy

---

### Post by landandy on 2010-10-17
update:
When I push with the pencil at the tablet, it is the same as when i click with the mouse. But it recognises no movements.
by
Andy

---

### Post by Favux on 2010-10-17
Hi mesilliac and everyone,

As you can see there's a new bluetooth Wacom tablet, the Intuos4-wireless.  It came out about February of 2010.  Sorry to intrude, but this seemed to be the place to go.

landandy posted on the Maverick development forum and I answered him a few hours before it was closed:  [http://ubuntuforums.org/showthread.php?t=1591510](http://ubuntuforums.org/showthread.php?t=1591510)

Trying to use the bluetooth:
xinput --list
> &#9116; &#8627; PTK-540WL id=14 [slave pointer (2)]
dmesg | grep wacom
> [ 3.966187] usbcore: registered new interface driver wacom
[ 3.966191] wacom: v1.52:USB Wacom tablet driver
[ 4167.809538] wacom 0005:056A:00BD.0001: input,hidraw0: BLUETOOTH HID v1.06 Mouse [PTK-540WL] on 00:1F:3A:F3:47:51
lsmod | grep wacom
> hid_wacom 4604 0
hid 67742 2 hid_wacom,hidp
wacom 27784 0
more /proc/bus/input/devices
> ...
I: Bus=0005 Vendor=056a Product=00bd Version=0106
N: Name="PTK-540WL"
P: Phys=00:1F:3A:F3:47:51
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/bluetooth/hci0/hci0:1
1/input10
U: Uniq=00:10:60A:58:F2
H: Handlers=mouse2 event9
B: EV=1f
B: KEY=1c63 0 70003 0 0 0 0 0 0 0 0
B: REL=103
B: ABS=3000003
B: MSC=11

Tablet connected by usb (also used to charge it):
xinput --list
> &#9116; &#8627; Wacom Intuos4 WL eraser id=15 [slave pointer (2)]
&#9116; &#8627; Wacom Intuos4 WL cursor id=16 [slave pointer (2)]
&#9116; &#8627; Wacom Intuos4 WL pad id=17 [slave pointer (2)]
&#9116; &#8627; Wacom Intuos4 WL stylus id=18 [slave pointer (2)]
more /proc/bus/input/devices
> ...
I: Bus=0003 Vendor=056a Product=00bc Version=0127
N: Name="Wacom Intuos4 WL"
P: Phys=
S: Sysfs=/devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input11
U: Uniq=
H: Handlers=mouse3 event10
B: EV=1f
B: KEY=1cff 0 1f01ff 0 0 0 0 0 0 0 0
B: REL=100
B: ABS=100 f000167
B: MSC=1
Notice that the product ID 00bd is different as you'd figure but it seems to change from bluetooth to 00bc when using usb.

So I'm hoping that you're updating your ppa/patch to enable mode 2 (high speed) bluetooth for the Maverick bluez package.  And while you're doing that could you include the product ID for the Intuos4-wireless along with the Graphire?

And also, to echo a request a few posts back, could someone update the wiki or post on this thread, more detailed instructions/explanations about what's going on with the fix.  Lacking the context I'm a little lost.  Thank you.


Hi Andy,

It seems you're ahead of me now.  Where did you come up with the reinstall of linux-image?

It looks like there's a couple of reasons it's not working for you:
1)  PPA hasn't been updated for Maverick
2)  The Intuos4-wireless product ID needs to be added.  Right now the patch only has the Graphire product ID.

Without mesilliac's or someone's help we'd have to try manually patching the bluez package.  We need to find the device.c file in the /input directory of the bluez source code and see if we can sensibly insert the Lucid changes (the +'s) in it without breaking it:
>          err = write(sk, buf, sizeof(buf));
     }
 
+    if (req->vendor == 0x056a && req->product == 0x81) {
+        unsigned char buf[3];
+        int sk = g_io_channel_unix_get_fd(iconn->ctrl_io);
+
+        buf[0] = 0x53; /* HIDP_TRANS_SET_REPORT | HIDP_DATA_RTYPE_FEATURE */
+        buf[1] = 0x03; buf[2] = 0x00;
+        write(sk, buf, sizeof(buf));
+
+        buf[0] = 0x71; /* HIDP_TRANS_SET_REPORT | HIDP_DATA_RTYPE_FEATURE */
+        /* 0x06 - high reporting speed, 0x05 - low speed */
+        buf[1] = 0x06; buf[2] = 0x00;
+        write(sk, buf, sizeof(buf));
+    }
+
     err = ioctl_connadd(req);
when we recompile it.  At least I think that's what we'd need to do.  And it's likely the code changed otherwise you'd think the patch would apply.  Of course we'd have to change the product ID to yours:
```
+    if (req->vendor == 0x056a && req->product == 0xbd) {
```
You can see why I'm hoping for help.

---

### Post by landandy on 2010-10-17
Hi Favux,

thank you for your reply. I just tried to reinstall linux-image, even if I didn't know if it would help.
Now I was searching for the config.c file at my computer and there is nothing! (search with nautilus in /)
So I downloaded [SIZE=2][COLOR=Black][ [COLOR=Navy]_Release of bluez-4.76_[/COLOR]]("http://www.bluez.org/bluez-476/")[/COLOR][/SIZE] there is a device.c file.
But there seems to be a lot of changes. If I open the file and search for the place to input the additional lines (search: "err = write(sk, buf, sizeof(buf));"), there is no result!

---

### Post by Favux on 2010-10-17
Hi Andy,

Good find.  That seems to be too new (4.76 version from 10-15-10) for the version in Maverick .  A wild guess would be line # 666.  What does Synaptic Package Manager say the version number is?  We need to compare that one to the Lucid one:  [http://www.bluez.org/download/](http://www.bluez.org/download/)  I think they'll be earlier versions.  Hopefully less code change.  The diff on the page before calls the lucid one "bluez (4.60-0ubuntu8 ) lucid".


Edit:  It's "bluez-4.60" in Lucid (bluez 4.60-)ubuntu8 ).  Let me download it and compare device.c's.

---

### Post by landandy on 2010-10-17
Synaptic says: 4.69-0ubuntu2
So I downloaded 4.69
The device.c is attached.

---

### Post by Favux on 2010-10-17
Hi Andy,

Bad news like we figured.  Looks like they reorganized the code between 4.60 and 4.69.  Looking at the two with my Diffuse Merge Tool shows quite a mess, i.e. extensive code shifting.  Usually there's only a few dozen lines changed.  Anyway there's little chance I'll be able to figure out where the functionally equivalent location is and what changes are needed.  At about 2500 lines it's just too long and complicated for my very limited skills.

So we're going to need help.

Lucid's 4.60 is at [http://www.bluez.otg/page/4/](http://www.bluez.otg/page/4/)

Maverick's 4.69 is at [http://www.bluez.otg/page/2/](http://www.bluez.otg/page/2/)

---

### Post by niroshansl on 2010-10-18
Thanks  :)

---

### Post by Hishgraphics on 2011-04-11
Hi. I'm on ArtistX 1.0 which is based on Lucid.

I am still unable to use my Wacom Graphire Bluetooth.

I was unable to look for a proper xorg.conf, so when I typed in Terminal **locate xorg.conf**

I was returned with this:

```
/xorg.conf.new
/etc/X11/userful.Mxorg.conf
/etc/X11/userful.xorg.conf.all
/etc/X11/userful.xorg.conf.one
/usr/lib/X11/xorg.conf.d
/usr/lib/X11/xorg.conf.d/05-evdev.conf
/usr/lib/X11/xorg.conf.d/10-evtouch.conf
/usr/lib/X11/xorg.conf.d/10-joystick.conf
/usr/lib/X11/xorg.conf.d/10-synaptics.conf
/usr/lib/X11/xorg.conf.d/10-vmmouse.conf
/usr/lib/X11/xorg.conf.d/10-wacom.conf
/usr/share/man/man5/xorg.conf.5.gz
/usr/share/xresprobe/xorg.conf
```

I used **gksudo gedit /usr/lib/X11/xorg.conf.d/10-wacom.conf**, and I got:

```
Section "InputClass"
	Identifier "Wacom class"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
        #Option "Button2" "2"
        #Option "Button3" "3"
        Option "KeepShape" "on"
EndSection

Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001|N-Trig Pen"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "Button2" "3"
EndSection
```

**xinput --list** returned:

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; HID 062a:0000                           	id=10	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]

```

I've already upgraded bluez. Should I use a custom fdi? I've already used Favux's fdi [here]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176") at my **/usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi**. The stylus still doesn't work although clicking on the tablet with the stylus causes paragraphs of text where the cursor is over gets selected. I am at a loss on how to proceed. 

Thanks.

---

### Post by Favux on 2011-04-11
You used the PPA in mesilliac's [post #134]("http://ubuntuforums.org/showpost.php?p=9232133&postcount=134")?  That should switch it to high speed mode.  In Maverick it should work out of the box.

Since you aren't using Lucid did the PPA throw an error?  There might be a directory path where you have to substitute whatever ArtistX 1.0 uses instead of Lucid.

The *xinput list* indicates bluetooth communication hasn't been established.  I think the USB snippet in the 10-wacom.conf works for bluetooth also, although I'm not 100% sure.

Starting with Lucid you may not have a xorg.conf unless you use the Nvidia proprietary video drivers.  That's because Lucid uses X server 1.7.  You can create and use a xorg.conf if you want, but it usually isn't needed.  Also Lucid no longer uses HAL/.fdi files.  It uses xorg.conf.d/.conf files instead.  And that's because the X server 1.7 in Lucid is actually a hybrid with an early version of X server 1.8.  Debian and Ubuntu did the hybridization so they could get rid of HAL/.fdi as soon as possible.  But that means the .conf files are located in a non-standard xorg.conf.d location.  Maverick uses the standard location.

---

### Post by Hishgraphics on 2011-04-12
> **Favux said:**
> You used the PPA in mesilliac's [post #134]("http://ubuntuforums.org/showpost.php?p=9232133&postcount=134")?  That should switch it to high speed mode.  In Maverick it should work out of the box.

Since you aren't using Lucid did the PPA throw an error?  There might be a directory path where you have to substitute whatever ArtistX 1.0 uses instead of Lucid.

I got an error when I reloaded software sources.

```
Failed to fetch https://launchpad.net/~yobbobandana/+archive/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz
The requested URL returned error: 404
```

---

### Post by Favux on 2011-04-12
The directory path looks good.  I'm hoping Launchpad.net was temporarily out of service because the PPA still seems to be there:  [https://launchpad.net/~yobbobandana/+archive/ppa](https://launchpad.net/~yobbobandana/+archive/ppa)
as is the Lucid version:  [https://launchpad.net/~yobbobandana/+archive/ppa?field.series_filter=lucid](https://launchpad.net/~yobbobandana/+archive/ppa?field.series_filter=lucid)

---

### Post by Favux on 2011-10-19
Hi,

Just an FYI.  Przemo Firszt is working on support for the Intuos4 wireless/bluetooth tablet.  He's submitted a second version of his patchset:  [http://sourceforge.net/mailarchive/forum.php?thread_name=CAGzDe_aiOaTp4NFBfe8iTsFSUjcYRZ1P91Mep_FE4HUXTw18wA%40mail.gmail.com&forum_name=linuxwacom-devel](http://sourceforge.net/mailarchive/forum.php?thread_name=CAGzDe_aiOaTp4NFBfe8iTsFSUjcYRZ1P91Mep_FE4HUXTw18wA%40mail.gmail.com&forum_name=linuxwacom-devel)

---

### Post by kayzu on 2012-01-06
Is there a way to use those patches yet? I've installed the kernel modules with Przemo's patches, but don't know where to go from there. My Intuos4 WL still only works like a mouse when connected via Bluetooth.

---

### Post by Favux on 2012-01-07
Hi kayzu,

I had the impression once you applied the patches to hid (hid-core.c, hid-ids.h, hid-wacom.c) and copied the newly compiled hid-wacom.ko into place, /lib/modules/`uname -r`/kernel/drivers/hid, you were good.  I don't think anything needs to be changed in xf86-input-wacom.  So the patches applied cleanly and no errors on compile?

You could post on linuxwacom-discuss:  [https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss](https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss) and ask.  Przemo would probably find you within a couple of days.  Or contact Przemo Firszt directly.  Either way I'm sure he'd be happy to talk to a tester.

---

### Post by Reason NL on 2012-05-23
It's working for me under 12.04 (Still no buttons though), but somehow Ubuntu thinks it contains a laptop battery.
Although the features it exposes (charge history etc.) are nice to have, it also suspends my machine when it's empty ([https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/994013](https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/994013))..

Couldn't resist smiling when my desktop computer told me it had to suspend immediately because it's battery was drained, and so it did.. ;)

---

### Post by Favux on 2012-05-23
lol  Now you have a nice anecdote to entertain other linux users with.  :)

Just let Przemo or Chris know about that one on linuxwacom-discuss.  Chris just submitted a battery patch:  [http://www.spinics.net/lists/linux-input/msg20966.html](http://www.spinics.net/lists/linux-input/msg20966.html)

---

### Post by Reason NL on 2012-06-10
Yeah, although it gets annoying pretty fast it does remain funny. ;)

Are implying they patched it?
Or does it still needs to be brought to attention of those peeps?

---

### Post by Favux on 2012-06-10
I don't know if the new patch would have addressed your bug.  So I'd go ahead and report it.  Besides it's funny.  :)

[linuxwacom-discuss]("https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss")

---

### Post by Reason NL on 2012-06-10
Although I would like to post this somewhere else, I'm not really interested in joining a mailing list just for this purpose.
I'll just wait until someone on launchpad will assign this to someone who will be able to fix / delegate this.
In the mean time I'll keep my charger with me all time. :D

---

### Post by Favux on 2012-06-10
That's not likely to get you anywhere in any reasonable amount of time.  Would you like me to post your report on linuxwacom-discuss for you?

---

### Post by Reason NL on 2012-06-11
>  		That's not likely to get you anywhere in any reasonable amount of  time.  Would you like me to post your report on linuxwacom-discuss for  you? 	

Sure, if you don't mind! ;)

---

### Post by Reason NL on 2012-07-06
And so any use of this tablets ends (once again).
I've installed 12.04 from scratch (new harddisk) and from now on the tablet connects but that's it. It completely stopped working (again).
It does show up in xinput, but just doesn't do anything anymore.
Well almost nothing, the light still blinks when touching it with the pen.

---

### Post by Reason NL on 2012-07-09
After some searching it seems to be a crashing module introduced in the 3.2.* kernel.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1021069](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1021069)

---

### Post by Reason NL on 2012-07-09
Installed 3.4-rc6-precise from the mainline and it's working again.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-rc6-precise/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.4-rc6-precise/")

This kernel however, does not contain the sources to compile the nVidia driver from the repo.

Update:

Installed [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4.4-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4.4-quantal/) nVidia driver is working again.

---

### Post by Favux on 2012-07-09
Hi Reason NL,

Given that it is a kernel bug I'd like to call your attention to some available resources for Wacom tablets you may not be aware of.  The first is the Wacom-kernel repository:  [http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/wacom-kernel;a=summary](http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/wacom-kernel;a=summary)

And the wiki page on how to use it:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Wacom-kernel_Repository](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Wacom-kernel_Repository)

The Launchpad bug page doesn't seem to say where the sysfs bug is but my guess is in the kernel's HID section.  Either way you should be able to use the Wacom-kernel repo to fix the issue without upversioning the kernel.  It sounds like you know your way around the kernel, better than I do, but for completeness sake I'll include a HOW TO that deals a little with HID issues:  [http://ubuntuforums.org/showthread.php?t=1946486](http://ubuntuforums.org/showthread.php?t=1946486)

I was given to understand the battery issue was fixed when Przemo Firszt (who did the blue tooth and just added the Intuos4 wireless) collaborated with Chris Bagwell (working on the new Wacom wireless kit).  I think with Jason's Intuos5 stuff the wireless stuff should all be working at this point.

---

### Post by Reason NL on 2012-07-10
Thanks Favux!

Even thought I would be capable compiling my own kernel I try to avoid it whenever possible. I'm not using (especially) this computer to play with it's OS, it just has to work. So I would rather stick with deb packages to avoid breaking package management and missing any upstream fixes resulting in hours of compiling, searching and fixing dependency issues when something messes up something because it expected otherwise.
Installing the upstream kernel was nothing more then installing the deb packages provided for your systems architecture from the link in my previous post, I wouldn't have attempted it otherwise.
It also fixed some other issues I had and thus it resulted in more benefits besides the fix for the tablet.

I also installed the wacom driver package 0.15, but the default 0.14 seemed to work just fine as well. ([https://launchpad.net/~irie/+archive/wacom/+build/3579922]("https://launchpad.net/%7Eirie/+archive/wacom/+build/3579922"))

---

