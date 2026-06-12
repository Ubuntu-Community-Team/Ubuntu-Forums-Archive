---
title: "HOWTO: enable 3d acceleration w/ Rage Mobility (mach64)"
date: 2004-12-05
forum: Tutorials
---

### Post by stateq2 on 2004-12-05
**[color=red]update 03-25-06[/color]**

I have been struggling w/ this for the past two weeks....and I finally got 3d acceleration to work w/ my ati rage mobility.  I'm using xorg, but I beleive that it works w/ xfree86 as well.  first of all, here's my card according to lspci
```

0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

```

it uses the mach64 chipset.  

now here's how I got direct rendering to work:

**[color=blue]GUIDE[/color]**
**1. get your updated kernel, headers, compilation tools**
```

sudo apt-get install linux-686 linux-headers-2.6-686 build-essential

```

**1.5 if you the kernel wasn't installed already, reboot to it**

**2. get the proper common AND mach64 dri software from [here](http://dri.freedesktop.org/snapshots/)...or get it like this (but make sure that you go to link in the future because these are daily snapshots that get updated regularly)**
```

wget http://dri.freedesktop.org/snapshots/common-20060325-linux.i386.tar.bz2

wget http://dri.freedesktop.org/snapshots/mach64-20060325-linux.i386.tar.bz2

```

**3. kill your X server.  if you using the default ubuntu configuration, press ctrl+alt+F1..then;**
```

sudo /etc/init.d/gdm stop

```

**4. unpack the common modules.  go into the directory where you downloaded the dri stuff, and:**
```

tar xjvf common-20060325-linux.i386.tar.bz2

tar xjvf mach64-20060325-linux.i386.tar.bz2

```

**5. go into the "common" directory first, and..**
```

sudo ./install.sh

```

**6. then go into the "mach64" directory, an..**
```

sudo ./install.sh

```

**7. start x again:**
```

sudo /etc/init.d/gdm start

```

**8. once you start X again, check for your direct rendering by opening a terminal and typing:**
```

glxinfo | grep "direct"

```

if it says "direct rendering: Yes", then congratulations, and try running "glxgears -printfps" to see your performance increase.
NOTE:  you may also get better performance by changing your bit depth to 16 instead of the default 24...look for this line in your /etc/X11/xorg.conf file under the "Screen" section
```

DefaultDepth    24

```
change "24" to "16"
**btw, depending on your kernel version, the names in step 1 & 2 may vary**

If not....then try the troubleshooting 8)


**[color=blue]TROUBLESHOOTING[/color]**
**1. see if the "mach64" module is loaded..**
```

lsmod | grep "mach64"

```

if not...load it by:
```

sudo modprobe -v mach64

```

**2. if you have problems after reboot:**
**a.) check if module is listed in "/etc/modules"**
```

cat /etc/modules | grep "mach64"

```

**b.) if not, add it**
```

sudo echo "mach64" >> /etc/modules

```

if you still have problems, you may want to search this thread for possible specific solutions, because many people seem to have resolved their problems

links:
[http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/)
[http://www.freedesktop.org/wiki/Software_2fdri](http://www.freedesktop.org/wiki/Software_2fdri)
[http://mandrakeusers.org/index.php?showtopic=17864](http://mandrakeusers.org/index.php?showtopic=17864)

---

### Post by stateq2 on 2004-12-05
**[color=red]disregard this post[/color]**

btw....it seem as if direct rendering only works when you run x via the "startx" command.  until someone comes along here and contributes a permanent workaround, you'll need to disable gdm from starting on bootup.

**EDIT**
ok...here how to do it:
```

mv /etc/rc2.d/S99gdm /etc/rc2.d/K99gdm

```

this will set the gdm service to (K)ill instead of (S)tart.  to restore, just mv it back.

now, when you disable gdm, you'll want x to start w/ your favorite window manager, or desktop environment.  If you want x to start w/ gnome, create a file named ".xinitrc" in your home dir...then edit it like this:
```

xterm &
gnome-session

```
this will start gnome when you start x....and you still get direct rendering :)  

if you prefer another environment, just replace "gnome-session" w/ the environment you want (fluxbox, wmaker, etc)...the end

---

### Post by Arbiter on 2004-12-05
I try to use your method of getting DRI to work with my mach64 based Rage 3d chip.  It fails to compile and it gives me this message in the logs...

make DRM_MODULES=mach64.o modules
make[1]: Entering directory `/home/arbiter/dripkg/drm/linux-2.6'
make -C /lib/modules/2.6.8.1-3-386/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.8.1-3-386'
/home/arbiter/dripkg/drm/linux-2.6/Makefile:313: *** CONFIG_X86_CMPXCHG needs to be enabled in the kernel.  Stop.
make[2]: *** [_module_/home/arbiter/dripkg/drm/linux-2.6] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.8.1-3-386'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/arbiter/dripkg/drm/linux-2.6'
make: *** [mach64.o] Error 2

I'm not sure what it means.  I'm using kernel 2.6.8.1-3-386.  Any help would be appreciated.

thanks

---

### Post by stateq2 on 2004-12-05
[QUOTE=Arbiter]I try to use your method of getting DRI to work with my mach64 based Rage 3d chip.  It fails to compile and it gives me this message in the logs...

make DRM_MODULES=mach64.o modules
make[1]: Entering directory `/home/arbiter/dripkg/drm/linux-2.6'
make -C /lib/modules/2.6.8.1-3-386/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.8.1-3-386'
/home/arbiter/dripkg/drm/linux-2.6/Makefile:313: *** CONFIG_X86_CMPXCHG needs to be enabled in the kernel.  Stop.
make[2]: *** [_module_/home/arbiter/dripkg/drm/linux-2.6] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.8.1-3-386'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/arbiter/dripkg/drm/linux-2.6'
make: *** [mach64.o] Error 2

I'm not sure what it means.  I'm using kernel 2.6.8.1-3-386.  Any help would be appreciated.

thanks[/QUOTE]
 apparently, your log says that "CONFIG_X86_CMPXCHG" needs to be enabled in your kernel...I'm not sure what this is, but this means that you'll have to compile your kernel w/ this enabled.

---

### Post by Arbiter on 2004-12-05
I finally got it to compile and install, but after checking to see if it worked after doing a 'startx', the glxinfo command still gives me a "no" on DRI.  Do I have to modify my XF86Config file or something?

---

### Post by stateq2 on 2004-12-05
[QUOTE=Arbiter]I finally got it to compile and install, but after checking to see if it worked after doing a 'startx', the glxinfo command still gives me a "no" on DRI.  Do I have to modify my XF86Config file or something?[/QUOTE]
 nope....just make sure that you enable "ati" driver in your XF86Config/xorg.conf.  here's my xorg.conf minus the comments

```

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/Speedo"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"speedo"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
	Load	"xtt"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xfree86"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Rage Mobility P/M (AGP)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option          "UseInternalAGPGART" "no"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	HorizSync	31.5-56
	VertRefresh	50-100.5
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage Mobility P/M (AGP)"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by Arbiter on 2004-12-05
There doesn't seem to be any obvious difference between our config files, although I did notice you are using X.Org whereas I'm still using XFree86.  Perhaps there is a problem there?

---

### Post by stateq2 on 2004-12-05
[QUOTE=Arbiter]There doesn't seem to be any obvious difference between our config files, although I did notice you are using X.Org whereas I'm still using XFree86.  Perhaps there is a problem there?[/QUOTE]

could be...although I doubt it because I think the driver is really for xfree86  8)   I guess it also shold be know that these are unofficial dri snapshots, but they say that they (freedesktop.org) plan on  making the official ones available in the future.

what exact card do you have? (lspci | grep "ati")

---

### Post by Arbiter on 2004-12-05
lspci gives these results...


0000:00:07.6 Communication controller: VIA Technologies, Inc. Intel 537 [AC97 Mo dem] (rev 30)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M A GP 2x (rev 64)

---

### Post by senectus on 2004-12-22
This looks great.. but can I do similar for my :
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 LX [Mobility FireGL 7800 M7]

Powered Laptop?

Should I use 
r200-20041215-linux.i386.tar.bz2
or
radeon-20041215-linux.i386.tar.bz2
??

Thanks

---

### Post by ankitmalik on 2005-01-04
> **stateq2]I have been struggling w/ this for the past two weeks....and I finally got 3d acceleration to work w/ my ati rage mobility.  I'm using xorg, but I beleive that it works w/ xfree86 as well.  first of all, here's my card according to lspci
```

0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

```

it uses the mach64 chipset.  

now here's how I got direct rendering to work:

1. backup your X11R6 and modules directorys just in case
```

sudo cp -r /usr/X11R6 /usr/X11R6.old

sudo cp -r /lib/modules/2.6.8.1-3-686 /lib/modules/2.6.8.1-3-686.old

```

2. get your kernel headers
```

sudo apt-get install linux-headers-2.6-686

```

3. get the proper mach64 dri software from [here](http://freedesktop.org/~fxkuehl/snapshots/mach64-20041123-linux.i386.tar.bz2)...or get it like this:
```

wget http://freedesktop.org/~fxkuehl/snapshots/mach64-20041123-linux.i386.tar.bz2

```

4. kill your X server.  if you using the default ubuntu configuration, press ctrl+alt+F1..then said:**
> http://freedesktop.org/~fxkuehl/snapshots/[/url]
[http://www.freedesktop.org/wiki/Software_2fdri](http://www.freedesktop.org/wiki/Software_2fdri)
[http://mandrakeusers.org/index.php?showtopic=17864](http://mandrakeusers.org/index.php?showtopic=17864)
 Cant get this to work :( Check this please

maliks@tuxido:~ $ cd dripkg
maliks@tuxido:~/dripkg $ sudo ./install.sh
Password:


DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.sourceforge.net](http://dri.sourceforge.net) ]

==========================================================================

Welcome to the DRI Driver Installation Script

The package you downloaded is for the following driver:

Driver Name    : mach64
Description    : ATI Mach64 Driver
Architecture   :
Build Date     : 20041215
Kernel Module  : mach64

Optional Information

Driver Version      :
Special Description :

Press ENTER to continue or CTRL-C to exit.



DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.sourceforge.net](http://dri.sourceforge.net) ]

==========================================================================

The script will need to copy the DRI XFree86 driver modules to
your XFree86 directory.

The script will use the following XFree86 directory:

 /usr/X11R6

If this is correct press ENTER, press C to change or CTRL-C to exit.










DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.sourceforge.net](http://dri.sourceforge.net) ]

==========================================================================

The script also needs to copy the DRM kernel modules to your
kernel module directory.

This version of the script supports 2.4.x and 2.6.x kernels.

Kernel Version   : 2.6.8.1-3-386
Module Directory : /lib/modules/2.6.8.1-3-386

If this is correct press ENTER, press C to change or CTRL-C to exit.









DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.sourceforge.net](http://dri.sourceforge.net) ]

==========================================================================

The script will now compile the DRM kernel modules for your machine.

Press ENTER to continue or CTRL-C to exit.


Compiling...
ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.

---

### Post by allio on 2005-01-06
[QUOTE=ankitmalik]Cant get this to work :( Check this please[/QUOTE]

Bumping for ankitmalik because I have the same problem :D

EDIT: On closer inspection, upgrading to x.org is mandatory.

> Binary snapshots only work with a recent X.org X server. If you're running a version of XFree86 then you must install an [WWW]X.org server (Xorg.bz2) and [WWW]driver modules (Xorg-modules.tar.bz2).

I'll give that a go.

---

### Post by allio on 2005-01-06
[QUOTE=Arbiter]I finally got it to compile and install, but after checking to see if it worked after doing a 'startx', the glxinfo command still gives me a "no" on DRI.  Do I have to modify my XF86Config file or something?[/QUOTE]

Ok, how did you get around that error? I hope you didn't have to actually recompile the kernel :(

---

### Post by stateq2 on 2005-01-08
just updated the howto...I added the common modules, plus the drivers were updated.  if you had problems before, you might want to try it again.

---

### Post by kultuur on 2005-01-28
Hi there

I installed Hoary Array 3 (with X.org 6.8.1) yesterday.  Enabling DRI for my ATI Rage Pro card (also based on mach64) was not so difficult. I didn't need the common-200xxxxx-linux.i386.tar.bz2 package, only  mach64-200xxxxx-linux.i386.tar.bz2.

**I followed these steps (based on the first post):**

1. install the necessary kernel-headers and gcc
```
sudo apt-get install linux-headers-686 build-essential
```
2. Download latest mach64 snapshot from [http://dri.freedesktop.org/snapshots](http://dri.freedesktop.org/snapshots) and untar.
```
wget http://dri.freedesktop.org/snapshots/mach64-20041215-linux.i386.tar.bz2
tar xjvf mach64-20041215-linux.i386.tar.bz2
```
3. Logout from gnome and change the runlevel with
```
sudo init 1
```
This stops the X.org server.

4. Build and install the mach64 drivers
```
cd /path_to_where_you_untarred_everything/dripkg
./install.sh
```
What does this script do ?  
It installs a new kernel-module for your graphics card
*/lib/modules/2.6.xxxxx/kernel/drivers/char/drm/mach64.ko*

and installs the necessary driver for X.org:
[I]/usr/X11R6/lib/modules/dri/mach64_dri.so
/usr/X11R6/lib/modules/drivers/ati_drv.o
/usr/X11R6/lib/modules/drivers/atimisc_drv.o[/I]

5. Restart X.org with
```
init 2
```
6. Check for direct rendering under gnome
```
glxinfo | grep direct
```
**What to do if it doesn't work?**

1. Check if your mach64 kernel-module is loaded
```
lsmod | grep mach64
```
Output must be similar to
```
mach64                117568  2
```
If it isn't loaded, try to load it with
```
sudo modprobe -v mach64
```
When it is missing after a reboot, add a line with 'mach64' to /etc/modules
```
sudo echo "mach64" >> /etc/modules
```
2. Check /etc/X11/xorg.conf
This file should contain:
```
Section "Module"
        ...
        Load    "dri"
        Load    "glx"
        ...
EndSection

Section "Device"
        ...
        Driver          "ati"
        ...
EndSection

Section "DRI"
        Mode    0666
EndSection
```

---

### Post by stateq2 on 2005-02-28
wow, nice update :smile:

---

### Post by mr_ed on 2005-03-08
[QUOTE=allio]Ok, how did you get around that error? I hope you didn't have to actually recompile the kernel :([/QUOTE]

bump!

```
Compiling...
ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.
```

I got the same error while trying to install the common files, too.  :(

---

### Post by allio on 2005-03-09
[QUOTE=kultuur]
1. Check if your mach64 kernel-module is loaded
```
lsmod | grep mach64
```
Output must be similar to
```
mach64                117568  2
```[/QUOTE]

```
allio@zinger:~ $ lsmod | grep mach64
mach64                 57888  0
drm                    72536  1 mach64
```

This appears to be wrong.

I can't actually for the life of me work out if my onboard video is even supported. lspci gives: ```
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)
```
...which looks like like it is, but I really can't be sure. Does the fact that the mach64 module succesfully loads on a modprobe mean that it is, or would it load with any video card?

Oh well, I'll try following your instructions from scratch, but I never seem to get anywhere. Maybe hoary will fix things :p

---

### Post by stateq2 on 2005-03-13
[QUOTE=mr_ed]bump!

```
Compiling...
ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.
```

I got the same error while trying to install the common files, too.  :([/QUOTE]
sorry for the delay.  you need to get the linux headers for your kernel.  if don't have them...
```

apt-get install linux-headers-686

```
....but if you do already have them, keep reading.

for some reason, the driver dosn't compile when you use the '386' kernel, complaining about something not being in the kernel.  the solution is to get the '686' kernel, along w/ it's headers.
```

apt-get install linux-686 linux-headers-686

```
then boot to the kernel, and run the script again.  hope this works for you

---

### Post by mr_ed on 2005-03-14
Hey, no problem.

Unfortunately, I have both of them.  :(

I went in and did a make in the right subfolder, and it appeared to have worked.

Only thing is that it only seemed to enable DRI when I set my laptop screen size to 1024x768.  (This laptop normally only has one setting:  1400x1050)

---

### Post by mr_ed on 2005-03-24
By the way, what are you getting for a glxgears score with a working DRI?

---

### Post by mr_ed on 2005-03-24
I got it working finally. : phew :

May I add a step 6.5?
6.5.  DELETE the dripkg directory before untarring the common files!

---

### Post by mt2 on 2005-03-24
[QUOTE=allio]```
allio@zinger:~ $ lsmod | grep mach64
mach64                 57888  0
drm                    72536  1 mach64
```

This appears to be wrong.

I can't actually for the life of me work out if my onboard video is even supported. lspci gives: ```
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)
```
...which looks like like it is, but I really can't be sure. Does the fact that the mach64 module succesfully loads on a modprobe mean that it is, or would it load with any video card?[/QUOTE]

I'm have the exact same problem. Did anyone ever work this out?

---

### Post by wernst on 2005-03-24
Thanks to Kultuur's tips (about loading modules) I did indeed get things working on Hoary (updated as of today).

The problem for me is that  DRI is only enabled (at least for me) at 1024x768 (or less) at a bit depth of 16 (or less). And this must be set in xorg.conf beforehand instead of with the Screen Resolution Gnome applet.

I normally run 24 bit depth at 1400x1050, which is my LCD's native resolution, which means that I don't really benefit from this mod.

This is really a shame, because the GL-based screen savers actually work.

That said, I can't see that I see any real different when DRI mode is enabled. The GL-based screen savers seem to be the only real-world difference/improvement I see here.

CPU Utilization when moving windows is just as high in Gnome. I don't see any difference in DVD playback speed or quality (which is to say that it is inferior to Windows on the same hardware with the same resolution.)

Using the GATO "ati.2" drivers (installed after doing all this DRI stuff) is sort of interesting, in the sense that it doesn't screw up the system at all once you install the binaries, but I don't see any improvement in video quality during DVDs.

Ultimately, I guess if you regularly run resoltions higher than 1024, this is a useless mod, and if you don't play 3d games or 3d screensavers, it is a questionable mod, since you'll need to do this all over again any time the kernel updates as part of the distro.

So, hat's off to everyone who figured this out.

But I'll be using Norton Ghost to go back to where I was this afternoon. ;-)

-Warr

---

### Post by makisushi on 2005-04-10
Thank you for this nice Howto : this is the first time I can enjoy the following with my good old mach64 :

glxinfo |grep direct
direct rendering: Yes

and glxgears gives something like 2500 fps

But still tuxracer runs slow, at 2fps...

I would greatly appreciate if anyone could help me on this.

---

### Post by Xanf on 2005-04-17
[QUOTE=mt2]I'm have the exact same problem. Did anyone ever work this out?[/QUOTE]

I've got the same problem on Hoary.
I use also an ATI 3D Rage Pro AGP 2x onboard card.

And after several exepiments I found the reason: if I had better read the information on the Mandrake forum (see the link #3 from the very first posting) - I'd notice the memory requirements.
And when I realized it - I got the the lower resolutions and bpp - and finallz got 3d acceleration working on 640x480, 15 bpp.  (glxgears fps about 140-145).
So, it works, but not usable for me - I returned back to the 1152x864, 24bpp, without 3d accel. (glxgears fps about 70-75).

---

### Post by c6aufa4 on 2005-05-06
a little feedback

Works fine on GERICOM Overdose II (CLEVO/KAPOK OEM laptop), sold in germany as "network" by "Saturn" markets.

with

0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc)

My way:
apt-get install linux-686 linux-headers-686 (synaptic didnt do ?!)
download/unzip snapshoot 20050506
quit xserver
do install.sh
paste "mach64" in /etc/modules (install.sh did not do) for autostart
xorg.conf was ok

Thanks 
to ankitmalik and kultuur


name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control,
    GLX_MESA_swap_frame_usage, GLX_SGI_video_sync, GLX_SGIS_multisample,
    GLX_SGIX_visual_select_group
OpenGL vendor string: Gareth Hughes, Leif Delgass, Jos\uffff Fonseca
OpenGL renderer string: Mesa DRI Mach64 [Rage Pro] 20030502 x86/MMX/SSE
OpenGL version string: 1.2 Mesa 6.3
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_transpose_matrix,
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture,
    GL_EXT_draw_range_elements, GL_EXT_histogram, GL_EXT_packed_pixels,
    GL_EXT_polygon_offset, GL_EXT_rescale_normal,
    GL_EXT_separate_specular_color, GL_EXT_subtexture, GL_EXT_texture,
    GL_EXT_texture3D, GL_EXT_texture_edge_clamp, GL_EXT_texture_object,
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_IBM_rasterpos_clip,
    GL_MESA_ycbcr_texture, GL_MESA_window_pos, GL_NV_light_max_exponent,
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix,
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp,
    GL_SGIS_texture_lod
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x24 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x25 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x26 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x27 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x28 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x29 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x2a 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x2b 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x2c 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x2d 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x2e 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x2f 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x30 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x31 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x32 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow

---

### Post by fishfork on 2005-05-12
Hello,

I'm getting the same error: CONFIG_X86_CMPXCHG needs to be enabled in the kernel.

But I can't use the 686 kernel, because it doesn't seem to work on my AMD K6-II. Does this mean I have to recompile the entire kernel then?

Any help would be greatly appreciated.

---

### Post by oggah on 2005-06-29
I'm wondering about applying this driver to a old toshiba laptop.
Ubuntu Hoary minimal install with Xfce4.

**Will it give me GUI boost?**
Right now the GUI is quite sloggish.

0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64) (prog-if 00 [VGA])
Subsystem: Toshiba America Info Systems: Unknown device ff00
Flags: bus master, stepping, medium devsel, latency 66, IRQ 10
Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
I/O ports at 2000 [size=256]
Memory at fc100000 (32-bit, non-prefetchable) [size=4K]
Capabilities: [50] AGP version 1.0
Capabilities: [5c] Power Management version 1

---

### Post by xav_38 on 2005-08-08
Hi,

I also get the "CONFIG_X86_CMPXCHG" error.

Do you know which option in "make menuconfig" does set this parameter to "Yes" ?

thanks
Xavier.

---

### Post by DamsFR on 2005-08-26
Hi,

I had the same problem with the Config_X86_XMFXCHG parameter during the installation process. After a check on google, it appears this paramater is not valid on i386 architecture.
 
The solution is to install ubuntu i686 kernel, boot on it, and uninstall i386 kernel (for space saving). This kernel is optimized for Pentium II, III and IV. (For AMD, may be try dedicated kernel).

One another trick is to delete the first dripkg directory before compile the common package (first method).

Hope it helps.

---

### Post by spd106 on 2005-09-11
I recently upgraded to Ubuntu 5.10 preview and found that I also needed to install gcc-3.4 to allow the install scripts to work. I think this is because breezy is moving onto gcc-4.0 as the latest build-essential v11.1 depends on gcc-4.0.

---

### Post by ChaoZ on 2005-11-22
hi from germany!

my xorg.conf seems to bee fine, the files have been copied by the ati-driver-script, but it doesn't work.

lsmod | grep mach
->
mach64   54720  0
DRM        76024  1  mach64

is this the problem?

---

### Post by clem-vangelis on 2005-11-24
hi all !
i got a mach64 base graphic card and I install the mach64 and common drivers
the install work perfectly but i have no direct rendering...
my xorg.conf is like all the other , lsmod give me :
mach64 54720 0
DRM 76024 1 mach64

anyone got an idea ?

bye

---

### Post by Major K on 2005-12-23
[QUOTE=clem-vangelis] lsmod give me :
mach64 54720 0
DRM 76024 1 mach64[/QUOTE]
same here! 
After a time of research I found the following info.
[http://www.gentoo.org/doc/de/dri-howto.xml#doc_chap3](http://www.gentoo.org/doc/de/dri-howto.xml#doc_chap3)
> "Einige Chips&#228;tze erfordern, dass xorg-x11 mit USE="insecure-drivers" neu gebaut wird. Dies gilt bei xorg-x11-6.8.2 f&#252;r mach64, ... . " 
In English: ... some chipsets (incl. mach64) require a new build of xorg-x11 with USE="insecure-drivers". 
Although this info is for Gentoo, it might be the solution for Ubuntu as well. Anyone capable of trying this, rebuilding xorg or  providing some links (How-Tos etc.)? 

Cheers,
Major K.

EDIT: I FOUND THE SOLUTION: 
see: [http://ubuntuforums.org/showthread.php?p=621585#post621585](http://ubuntuforums.org/showthread.php?p=621585#post621585)

---

### Post by swodah on 2006-02-10
Thanks for the advise...

I finally got the ATI mach64 3D acceleration working on my Compaq Armada E500 (old laptop - see relevant info bellow) using Ubuntu Breeze (5.10) with 2.6.12-10-686 kernel. I had installed (apt-get install...) linux-headers-2.6.12-10-686, build-essentials and gcc-3.4 (gcc-4.0 won't do...)

The key word really is the **RIGHT version** of driver (see thread: [[http://ubuntuforums.org/showthread.php?t=75393&page=5#post532200])](http://ubuntuforums.org/showthread.php?t=75393&page=5#post532200])). The problem for me was too new driver since Breezy uses X11R6.8 and all the newer driver are for X11R6.9/7.0. Install worked without errors and so on but direct rendering did not get enabled...

I wasn't able to find the driver mentioned in the above thread but for me these worked fine (from [[http://dri.freedesktop.org/snapshots/archive/]](http://dri.freedesktop.org/snapshots/archive/]) ):
 
mach64-20050628-linux.i386.tar.bz2
common-20050707-linux.i386.tar.bz2

The other instructions I followed can be found here:
[[http://ubuntuforums.org/showthread.php?t=7200]](http://ubuntuforums.org/showthread.php?t=7200]) 

briefly (; equals enter):
tar xjvf common* ;  cd dripkg;  sudo ./install; cd ..; rm dripkg;
tar xjvf mach*; cd dripkg;  sudo ./install; cd ..; rm dripkg;

To load the needed module for kernel during boot (so no need for modprobe mach64...)I also added to /etc/modules line:
mach64

restart x (or reboot if not manually modprobing...)

now 
*glxinfo | grep direct* 
shows **yes** :-D 

Also useful link is you have some problems with DRI (AGP or DRM) is:
[[http://dri.freedesktop.org/wiki/DriTroubleshooting]](http://dri.freedesktop.org/wiki/DriTroubleshooting])

Hope that this helps you with mach64 problems   \\:D/ 

   Thanks again for all...
      -Sami-

---
Relevant info:

sami@somewhre:/$  **lspci | grep AGP**
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

---

### Post by Amon_Re on 2006-02-25
I just did this install, and i came to face a problem, it seems, that, when i reboot, dri isn't working, yet, mach64 is loaded according to lsmod, any idea's?

The machine is also a Compaq E500

---

### Post by David Marrs on 2006-03-02
[QUOTE=swodah]The key word really is the **RIGHT version** of driver (see thread: [[http://ubuntuforums.org/showthread.php?t=75393&page=5#post532200])](http://ubuntuforums.org/showthread.php?t=75393&page=5#post532200])). The problem for me was too new driver since Breezy uses X11R6.8 and all the newer driver are for X11R6.9/7.0. Install worked without errors and so on but direct rendering did not get enabled...[/QUOTE]
Ah, thank you :) This was the final piece in the puzzle for me as well. The original poster should update his howto to include this info. Thank you OP :) Is there a way to test this? I tried glxgears and, although I got nice framerate (~115fps), my cpu is still working in overdrive to run the app.

---

### Post by reh4c on 2006-03-11
[QUOTE=swodah]
Also useful link is you have some problems with DRI (AGP or DRM) is:
[[http://dri.freedesktop.org/wiki/DriTroubleshooting]](http://dri.freedesktop.org/wiki/DriTroubleshooting])

Hope that this helps you with mach64 problems   \\:D/ 

   Thanks again for all...
      -Sami-

---
Relevant info:

sami@somewhre:/$  **lspci | grep AGP**
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)[/QUOTE]

Finally, I made some progress!  Based on info. from the Troubleshooting website, I reduced my default color depth to 16.  My video card only has 8MB, and a depth of 24 required 9600 KB of videor memory.  Direct rendering finally says "Yes", but when I run 'glxgears' my monitor "bleeds" color and slowly turns black.  It's really scary looking, and I'm sure it's not good for it.  I've been doing a hard shutdown to get out of it.  Any ideas?

---

### Post by fergus.b on 2006-03-14
I'm having some trouble getting on the freedesktop site. I keep getting gateway timeouts. Anybody else having the same problem?

---

### Post by Ariccanfly on 2006-03-17
I've been following this post for a while. Upgraded to 686
following the instructions on this post, common package installed without a hitch.
and whats with rm comonpkg, i dont understand that at all...

here's my DRI log for mach64-20060316-

make DRM_MODULES=mach64.o modules
make[1]: Entering directory `/hdb/mach64-20060316-linux.i386/drm/linux-core'
make -C /lib/modules/2.6.12-10-686/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
/usr/src/linux-headers-2.6.12-10-686/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
etc...

So i need to change my gcc from 4.0 to 3.4?

0000:00:0e.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro 215GP (rev 5c)

Also, i dont have a bios battery, so I'm allways "automatically reconfiguring"
And the Card in question, goes from showing 8megs of RAM, which it has, to complaining and displaying 6 megs, after i "automatically reconfigure"
actually this has allways happend, even with my old motherboard that died (i think it got some hanus virus from windows xp, which i recently nuked) so will i have to disable the last 2 megs? somehow?

in short should i bother, IE: will changing to gcc 3.4 have any other effects?
my wife will kill me if I destroy the computer again. Wishing mostly to learn more about GNU/linux

---

### Post by CedricSeah on 2006-03-23
> in short should i bother, IE: will changing to gcc 3.4 have any other effects?
my wife will kill me if I destroy the computer again. Wishing mostly to learn more about GNU/linux


just do:
sudo apt-get install gcc-3.4

It can coexist with gcc-4, as far as I know.

---

### Post by reh4c on 2006-03-23
[QUOTE=reh4c]Finally, I made some progress!  Based on info. from the Troubleshooting website, I reduced my default color depth to 16.  My video card only has 8MB, and a depth of 24 required 9600 KB of videor memory.  Direct rendering finally says "Yes", but when I run 'glxgears' my monitor "bleeds" color and slowly turns black.  It's really scary looking, and I'm sure it's not good for it.  I've been doing a hard shutdown to get out of it.  Any ideas?[/QUOTE]

Here's a guaranteed solution that works on my Fujitsu FMV-Biblo LOOX T86A.  It also fixes the "bleeding" problems that I mentioned before.  I filled a bug number 34590 in Malone.  It's not exactly a bug...more like a feature:

I'm a newbie to Linux, but I've finally managed to get DRI enabled on my Fujitsu FMV-Biblo LOOX T86A with help from the forums. This may be more of a feature/enhancement request than a bug. The following procedure enables DRI on this notebook, while the basic installation of Ubuntu Dapper Flight 5 does not. With the 386 vanilla kernel installed, I perform the following:
1. Manually change the color depth to 16 instead of Ubuntu's default 24 in the xorg.conf file. My 8MB graphics chip (ATI Rage Mobility P/M) will only support 16 due to memory requirements.
2. 'sudo apt-get install linux-headers-386 build-essential'
3. Download the latest common and mach64 snapshots from [http://dri.freedesktop.org](http://dri.freedesktop.org).
4. Untar the common file first, followed by the mach64 file.
4a.  Kill the X server with 'sudo /etc/init.d/gdm stop'
5. Change directory to the location of the unpacked common driver.
6. Run 'sudo ./install.sh' for the common modules and accept the default choices for the scripts.
7. Repeat steps 5 and 6 for the mach64 driver, using the default script choices.
8. Restart X and type 'glxinfo | grep "direct" to verify that direct rendering states "yes".

My laptop runs exceptionally better overall after completing this procedure. I'm certain it will help others as well. 3D gaming and GL are now possible...not exceptional. Can Ubuntu developers incorporate this script into the base install? Thanks.
:D

---

### Post by stateq2 on 2006-03-25
I updated the howto using many suggestions here...so if you have problems, try the first page again;)

---

### Post by Skinn3r on 2006-04-03
Well I'm having a bit of a problem with getting my Rage Mobility P/M AGP 2x (rev 64) card to work with DRI.

Since there are several people on this thread who managed to get it to work I wonder if you could help me out.

I follow the guide but glxinfo still says that I'm using Mesa GLX and not the mach64 driver.

Also Xorg.0.log says the following:

```

(II) ATI:  Shared PCI/AGP Mach64 in slot 1:0:0 detected.
(II) ATI:  Shared PCI/AGP Mach64 in slot 1:0:0 assigned to active "Device" section "ATI Technologies, Inc. Rage Mobility P/M (AGP)".
(--) ATI(0): ATI Mach64 adapter detected.
(II) ATI(0): Using Mach64 accelerator CRTC.
(WW) ATI(0): I2C bus Mach64 initialisation failure.
(II) ATI(0): I2C bus "Mach64" removed.

```

Any ideas?

---

### Post by ajack on 2006-04-11
Hi all,

I have followed this thread and now better understand and successfully installed everything.  However, the 3D acceleration produces a lot of flickering and tearing.  Has anybody experienced this before or have a solution?

I am using dapper with kernel 2.6.15-20-686 on a Compaq M700 laptop.

Any help is really appreciated... :confused:

---

### Post by ajack on 2006-04-12
[QUOTE=ajack]Hi all,

I have followed this thread and now better understand and successfully installed everything.  However, the 3D acceleration produces a lot of flickering and tearing.  Has anybody experienced this before or have a solution?

I am using dapper with kernel 2.6.15-20-686 on a Compaq M700 laptop.

Any help is really appreciated... :confused:[/QUOTE]

Hi all,

Just ran Synaptics update on my dapper build and the flickering/tearing issue has been resolved.

---

### Post by pinoy on 2006-05-16
Just read this thread, I followed its method of enabling 3d for mach64 (in a sudden whim)on my Vector5.1std ,once "tar xjvf common-20060403-linux.i386.tar.bz2","tar xjvf mach64-20060403-linux.i386.tar.bz2", "./install.sh", no error messages of installing(thought it should run with success)..... then restart X,  I only got blank screen and lock-up of sysytem, can only resort to restart button of the PC to escape the idle state...
still no X at at all....


I'd like to konw whether it's possible to uninstall "mach64"& "common"(installed by "./install.sh") and how should I recover back to former functional X(xorg 6.8.2), by which commands,......

---

### Post by morpheus2485 on 2006-05-25
I was following the instructions but the apt-get didn't work

$ sudo apt-get install linux-686 linux-headers-2.6-686 build-essential
Password:
Reading package lists... Done
Building dependency tree... Done
linux-686 is already the newest version.
E: Couldn't find package linux-headers-2.6-686

i went on ahead and mach didn't compile, the dri.log says:

make DRM_MODULES=mach64.o modules
make[1]: Entering directory `/home/david/mach64-20060325-linux.i386/drm/linux-core'
make -C /lib/modules/2.6.12-9-386/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
/home/david/mach64-20060325-linux.i386/drm/linux-core/Makefile:289: *** CONFIG_X86_CMP
XCHG needs to be enabled in the kernel.  Stop.
make[2]: *** [_module_/home/david/mach64-20060325-linux.i386/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/david/mach64-20060325-linux.i386/drm/linux-core'
make: *** [mach64.o] Error 2

any help?

---

### Post by ajack on 2006-05-26
[QUOTE=morpheus2485]I was following the instructions but the apt-get didn't work

$ sudo apt-get install linux-686 linux-headers-2.6-686 build-essential
Password:
Reading package lists... Done
Building dependency tree... Done
linux-686 is already the newest version.
E: Couldn't find package linux-headers-2.6-686

any help?[/QUOTE]

You will need to specify linux-headers-[kernel number] and to get the kernel number, use the command:

uname -r

Also, I believe you must boot into the kernel you want to compile with so once you have installed the linux-686 kernel, you need to reboot to that kernel to compile.  Please somebody tell me if I'm wrong anywhere in my post.

Used to have the mach64, but just upgraded my notebook an Acer which has kernel support so I can't be sure about the "need to reboot to the kernel to compile" thingy.

:mrgreen:

---

### Post by Neobuntu on 2006-05-31
I have a "ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)" in a Gateway Solo pro 9300 and I  compiling the listed and now newest (-20060403-linux.i386) Common and Mach64 sources from the site.

I renamed my directory (I keep this all in) "mach64" which is much shorter named and also rebooted(After changing to 16bit). Now the compiles/installs are both working!

I'm off to test. Woot!

It works! GL screen savers work (some slow but some FAST), Penguin Racer works playable and TORCS does NOT work playably. One can reduce the screen res and set to 16bit and drive all white cars (barely) but that's not what TORCS is all about. TORCS works well on another computer with minimal 32MB (Nvidia) DRI card. It works so well (on 32MB Nvidia or better) that it makes me dizzy. I think someone said the problem with these notebooks are these built in 3D graphics have only 8MB video memory.

Funny thing is, my boy is angry that I spead up his "Power Manga" game; so much. Now it may be a bit harder for him to get to level 33! Maybe it will waste less time though. :)

Anyway, hope this helps someone better use their notebook (a little.)

I hate this thing where the planets have to aline to get something installed but this was either at a moderate level or I am a uber geek. :)

Thank God for ubuntu where these things are rare and becoming more so! I love it. Things are truly getting better and Ubuntu is the best!

Hey! It looks like I'm in the wrong catagory. I did this in Dapper upgraded (And June 1st is in 13 minutes!)

---

### Post by David Marrs on 2006-06-03
Unfortunately, direct accelleration has stopped working for me now and  I can't get it working again :(

This is in dapper. I went throught the howto, for both the old drivers that got dri working in my earlier post, and with the latest drivers (I figured they'd work now that this is a newer kernel). Unfortunately, both fail to install. Running dmesg gives multiple errors all of the type:
```

[4327634.139000] mach64: disagrees about version of symbol drm_core_get_reg_ofs
[4327634.140000] mach64: Unknown symbol drm_core_get_reg_ofs
[4327634.141000] mach64: disagrees about version of symbol drm_pci_alloc
[4327634.142000] mach64: Unknown symbol drm_pci_alloc
[4327634.143000] mach64: disagrees about version of symbol drm_irq_uninstall
[4327634.144000] mach64: Unknown symbol drm_irq_uninstall
[4327634.145000] mach64: disagrees about version of symbol drm_get_dev
...etc...

```

I found a post at a mailing list that suggested this is because newer kernel versions are not supported ([http://lists.debian.org/debian-user/2005/04/msg01880.html)](http://lists.debian.org/debian-user/2005/04/msg01880.html)), but that was back in April, and clearly Neobuntu did ok on dapper. Any ideas, anyone?

---

### Post by Gabriele Persia on 2006-06-23
Hi all,

I've installed common-... and mach64-... (version 20060403).
Direct rendering is enabled but 3d-accelerated applications hangs the PC.

Chromium and gl screensaver (e.g. "AntSpotlight") runs for 0-to-2 seconds and then the system hangs (I need to power off).


Few weeks ago, I was running Breezy on the same computer, an Acer Travelmate 525txv w Rage Mobility Mach64, and everything was fine.

Installing older version of common/Mach64 didn't help.

Kernel (image, header and restricted-modules) version is 2.6.15-25-686,
gcc is 4.0.3.


Any suggestion?

Gabriele

---

### Post by gigahz on 2006-07-17
> **stateq2 said:**
> **[color=red]update 03-25-06[/color]**

I have been struggling w/ this for the past two weeks....and I finally got 3d acceleration to work w/ my ati rage mobility. 
...


Great! I just got my Dell Latitude with same ATI card working now, following these instructions. I did one bummer though - not getting the kernel headers correctly. I must have got something else and the X system went into coma. Anyway, getting all the specified packages it ran just as described!

Thank you for this good walkthrough.:D

---

### Post by fruchtschwert on 2006-08-06
Hallo everyone,

I have a Sony Vaio Laptop with a ATI Rage Mobility 8 MB graphics chip and Ubuntu Dapper running.
I tried to install the 3d accelerated dri driver as described in this thread. I'm already a little bit into Linux but I often encounter new problems, which are mostly not very serious.

According to this I have a problem with the tutorial  :o 

On my box I have **kernel 2.6.15-23-386** (the default dapper kernel) running.
I installed the appropriate **kernel-headers** and the **build essentials**.
I have the **gcc 4.0** compiler. Do I need more ?
On my AMD-machine there is no need for the linux-686-package, isn't it ?

Now to the main problem. I tried installing the dri-packages. But the installer seems not to determine the right installaltion directories.

> 
DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.freedesktop.org](http://dri.freedesktop.org) ]

==========================================================================

The script will need to copy the DRI Xorg driver modules to
your Xorg directories.

The script will use the following Xorg directories:

Xorg Dir         : /usr/X11R6
Xorg Modules Dir : /usr/X11R6/lib/modules
Xorg Library Dir : /usr/X11R6/lib

If this is correct press ENTER, press C to change or CTRL-C to exit.

==========================================================================

DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.freedesktop.org](http://dri.freedesktop.org) ]

==========================================================================

The following problems have occured:

        - Xorg module directory does not exist
        - Xorg extensions directory does not exist
        - Xorg Linux OS directory does not exist

The script can create these directories for you.

Press ENTER to continue or CTRL-C to abort.



[ATTACH]13900[/ATTACH]

It says that the 3 directories do not exist ...
I'm using version **common-20060403-linux.i386.tar.bz2** of the dri package.
I'm using the default Dapper xorg-installation.

**How do I determine the right paths for the installation ?**

Thanks in advance !
Greeting from Germany

fruchtschwert

---

### Post by segalion on 2006-08-29
I have same problem than fruchtschwert.

Seems that this howto dont work with dapper (X11R7). (new dir maybe /usr/lib/xorg/modules), but no doc available.

Seems that 3d support for old ATI rage (very common on old laptops) is break in dapper.

Another link...
[http://lists.freedesktop.org/archives/xorg/2006-March/014224.html](http://lists.freedesktop.org/archives/xorg/2006-March/014224.html)

My xorg log:
(WW) ATI(0): I2C bus Mach64 initialisation failure.
(II) ATI(0): I2C bus "Mach64" removed. 

maybe theese coluld be the problem?

Can any confirm X11R7 has dri 3d support for old mach64 ati cards? without patch them with this howto?

Help please for old poor laptop people who wants celestia!!!

Thanks.

---

### Post by fruchtschwert on 2006-09-04
Hi,

i think i could successfully determine the right installation paths.
While trying around a little bit i installed a xorg-development package (xorg-dev or something like this).
The installation now proposed realsitic paths, nevertheless the installation of the mach64-driver failed (while the common part worked).
The installer said:

> 
The script will now compile the DRM kernel modules for your machine.

Press ENTER to continue or CTRL-C to exit.


Compiling...
ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.


I have no idea how to fix this ...

---

### Post by xzhu on 2006-09-11
I have the same problem with my Sony laptop with RAGE MOBILITY M1.  I recently installed ubuntu dapper and this howto doesn't really work for me.  According to the Xorg.0.log, drmOpenDevice failed when trying to open /dev/dri/card0.

---

### Post by MASTo on 2006-09-25
same problem

---

### Post by MASTo on 2006-09-26
> 
The installation now proposed realsitic paths, nevertheless the installation of the mach64-driver failed 
(while the common part worked).
The installer said:

Quote:
The script will now compile the DRM kernel modules for your machine.

Press ENTER to continue or CTRL-C to exit.


Compiling...
ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.
I have no idea how to fix this ...
Reply With Quote


Solved it with the instructions of [http://dri.freedesktop.org/wiki/Building](http://dri.freedesktop.org/wiki/Building)

I have used instead of the mesa 3d drivers the common snapshot because the problem for me was in the mach64 drivers. To compile the mach64 I have followed the instructions in that page. Basically:


1. #git clone git://anongit.freedesktop.org/git/mesa/drm

2. #cd $mydownloadsnapshotspath/common2006xxxx

3. #./install.sh

4. #cd $thedirwhereyouhavedownloadeddrm/drm/linux-core

5. #make

6. #mkdir -p /lib/modules/$KERNEL/kernel/drivers/char/drm (if not exists)

7. #cp *.ko /lib/modules/$KERNEL/kernel/drivers/char/drm

8. #depmod -a

9. #modprobe mach64

restart gdm and... good luck!!

---

### Post by fruchtschwert on 2006-10-26
doesn't work :-(

---

### Post by fruchtschwert on 2006-10-26
Hi,

i tried to compile the mach64 module as masto described.
After facing several problems (to use git, you have to install git-core and cogito) i managed to compile the mach64 kernel module, which obviously loaded successfully. During the compilation i got some messages that some poniter values are pointing somewhere (i didn't understand it completely) but the script exited without error code.

When loading the module i've only got a message that something with the module isn't allright so that my kernel is tainted. But i read that this isn't important because it only says, that the module comes from a non trusted source. I hope that interpretation is correct.

But when starting gdm the screens gets black and nothing happens :-( still doesn't work !

Wheres the fault ? In my xorg.conf there are entries for dri and glx, the color depth is 16.

@masto: Is is right that i don't have to compile mesa and that libdrm-thing. That should be done by installing the common modules, right ?

Maybe the common part did not install correctly (although i got no errors).

Are the paths correct:

xorg dir: /usr
xorg modules dir: /usr/lib/xorg/modules
xorg library dir: /usr/lib

??

I hope someone can help me ...
I need XGL !

P.S.: Sorry for my bad english ... greetings from germany !

---

### Post by Ally_S on 2006-11-01
Here's how I got DRI with mach64 working in Edgy Eft. 

Before we begin, there seems to be an incompatibility between kernel 2.6.17-10 and the mach64 module so I had to modify ati_pcigart.c (attached in zip). I will not held responsible for any "damage" that using this file causes! :)

Download:
common-20060403-linux.i386.tar.bz2
mach64-20060403-linux.i386.tar.bz2

Extract both of above files to /usr/src/

Extract attached zip to (overwrite existing file): /usr/src/mach64-20060403-linux.i386/drm/linux-core/

Run:
sudo /usr/src/common-20060403-linux.i386/install.sh
sudo /usr/src/mach64-20060403-linux.i386/install.sh

log out.

restart X-Server (Ctr-Alt-Backspace)

log in.

Run:
glxinfo

DRI should be enabled!

---

### Post by fruchtschwert on 2006-11-02
Doesn't work for me ...

Upgrading to Edgy resulted in the same error.

The mach64 package does not compile.
The script reports the same error as in Dapper:

> The DRI drivers can not be installed without the latest kernel modules.

Why are there people, having no problems at all ?

Maybe the intel-specific-kernels have an advantage ?

---

### Post by Ally_S on 2006-11-02
Send me you DRI.log files from when you try to install common and mach64. I'll try to have a look at them when I have a minute and see if I can see the problem.

---

### Post by fruchtschwert on 2006-11-03
i tried to install the drivers on Dapper 2.6.15-23-386 with the according linux-source, linux-headers, linux-restricted-modules and xserver-xorg-dev (all 386).

Here are the logs:

the common part completes successfully, log is empty

the mach64 part shows the following message:

> Compiling...
ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.

with a dri.log like this:

> make DRM_MODULES=mach64.o modules
make[1]: Entering directory `/media/hda7/mach64-20060403-linux.i386.tar.bz2_FILES/mach64-20060403-linux.i386/drm/linux-core'
+ ln -s ../shared-core/drm.h drm.h
ln: Erzeugen der symbolischen Verknüpfung &#8222;drm.h&#8220; zu &#8222;../shared-core/drm.h&#8220;: Operation not permitted
make[1]: *** [drm.h] Fehler 1
make[1]: Leaving directory `/media/hda7/mach64-20060403-linux.i386.tar.bz2_FILES/mach64-20060403-linux.i386/drm/linux-core'
make: *** [mach64.o] Fehler 2

ln: Erzeugen der symbolischen Verknüpfung &#8222;drm.h&#8220; zu &#8222;../shared-core/drm.h&#8220;: Operation not permitted

means

ln: creation of symbolic link &#8222;drm.h&#8220; to &#8222;../shared-core/drm.h&#8220;: Operation not permitted

I've seen others having the same problem earlier in this thread but no solution was given.

I also tried compiling the mach64 module myself a few posts above, which nearly succeded (loading the module and restarting X gives a black screen)

Please help me !

Thanks in advance ...

---

### Post by crusader06 on 2006-11-06
I was trying all these with all these settings.. No luck so far. 
The module compiles/loads allright, but glxinfo still shows disabled. One thing I noticed from the Xorg.0.log is this:

"(WW) ATI(0): Not enough memory for local textures, disabling DRI"

Anybody knows how to overcome this? 

Thnx.

---

### Post by fruchtschwert on 2006-11-06
You should set your color depth to 16 bit, because 24 bit textures exceed the 8 MB of memory. Therefore you have to edit your xorg.conf in /etc/X11.

DefaultDepth	24 -> DefaultDepth	16

Eventually you also have to comment out (#) Subsections with a Depth of 24.

But why the hell do you have a working module ?

Could you please post your kernel version (uname -r in terminal), especially wheather you have an 386 or 686 one ...

Dapper or Edgy ?

And could you post the versions of your dri and mach64 binary snapshots ?

I have no idea why I don't get that working.
Thanks in Advance ...

fruchtschwert

---

### Post by crusader06 on 2006-11-06
My kernel version is 2.6.15-23-386. 
Using common-20060403-linux.i386.tar and mach64-20060403-linux.i386.tar

It was already 16 bit. Even then it doesn't work. Tried with 15 bits but DRI is supported only for 16 bit and 32 bit as found in the Xorg logs. I was trying to read through atiscreen.c in Xfree source. Was not of much help. Also the latest code doesn't seem to be having these sections!! I think we will have to use the 'correct' version of the driver. :( But, don't really know how to find that... 
Any more help?? :-k

---

### Post by shizeon on 2006-11-06
> **Ally_S said:**
> Here's how I got DRI with mach64 working in Edgy Eft. 

Before we begin, there seems to be an incompatibility between kernel 2.6.17-10 and the mach64 module so I had to modify ati_pcigart.c (attached in zip). I will not held responsible for any "damage" that using this file causes! :)
.....

Ally_S, your updated ati_pcigart.c did the trick for me with Edgy and a "01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)". 

I am getting a 
"libGL warning: 3D driver claims to not support visual 0x4b", but that is another story.

I used the latest snapshots from common-20060403-linux.i386.tar.bz2 &  mach64-20060403-linux.i386.tar.bz2 and running in 16-bit color.

So far so good and actually get around 160fps (from glxgears).  

Thanks!

---

### Post by deditri on 2006-11-07
It`s work for me too,thanks for your modification of agpart:p .

thanks alots :D

---

### Post by deditri on 2006-11-07
It`s work for my ati rage Mobility mach64 too,thanks for your modification of agpart:p .
First I`ve got the problem when installing the dri : I got this message Syntax error: Bad fd number, but after browse the web for a while I found the 
clue at:[http://diveintomark.org/archives/2006/09/19/bad-fd-number](http://diveintomark.org/archives/2006/09/19/bad-fd-number) , about what is the different in Edgy Eft

so the sh at the begining of command should be changed with bash.example..
usr:~$ bash install.sh

thanks alots :D

---

### Post by gregory_cooky on 2006-11-15
Hello

I did everything, and it works (Thank You VeRy MuCh), I mean direct rendering, but what does "libGL warning: 3D driver claims to not support visual 0x4b" mean?

---

### Post by fruchtschwert on 2006-11-20
Hi,

i solved my problem, not being able to compile the mach64 package by installing a 686 kernel on my Duron mobile and moving the installation files from a fat32 to an ext3-partition. Installing from ext3 probably was the primary solution ;) , because my dri.log said, that it could not create a symbolic link. ](*,) 

Now drm and mach64 seem to load perfectly, but i still get a black screen, when loading gdm. My xorg.conf is set up properly (dri, glx 16bit).
Also my Xorg.0.log says **direct rendering enabled** but that doesn't really help me without visible screen.

Here is the output of

lsmod | grep mach64
> mach64                 56032  0 
drm                    81240  1 mach64

lsmod | grep agp
> via_agp                10272  1 
agpgart                36784  2 drm,via_agp

dmesg | grep drm
> [4294696.030000] [drm] Initialized drm 1.0.1 20051102
[4294696.096000] [drm] Initialized mach64 1.0.0 20020904 on minor 0: 

dmesg | grep mach64
> [4294696.096000] [drm] Initialized mach64 1.0.0 20020904 on minor 0: 

dmesg | grep agp
> [4294691.806000] Linux agpgart interface v0.101 (c) Dave Jones
[4294691.816000] agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
[4294691.828000] agpgart: AGP aperture is 128M @ 0xf0000000

Here is my xorg.conf:

[ATTACH]19691[/ATTACH]

And here my Xorg.0.log:

[ATTACH]19694[/ATTACH]

Someone can help me ?
I'm near to (laptop) suicide :evil:

---

### Post by mrgamer on 2006-11-21
hi everyone, i've an old laptop Dell L400 with a mach64 onboard with 4MB of ram

the main problem is that i wish make the direct rendering work at 1024x768, but trying i get that:

grep WW /var/log/Xorg.0.log
```

(WW) ATI(0): DRI static buffer allocation failed -- need at least 4608 kB video memory

```
as explained on [DriTroubleshooting]("http://dri.freedesktop.org/wiki/DriTroubleshooting") page
```

If so, reduce your resolution or color depth. The video ram necessary for a given resolution/depth is width*height*(depth/8)*3 kilobytes. (The 3 is for front, back, and depth buffers). 

```
when i get the Warning, Xorg reverts to software rendering, and launches himself @ 1024x768 **WITHOUT** drm
the only way i succeeded to run direct rendering with the above HOWTO is @ 800x600 :( 

so the main problem is 1024*768*3*1 = more than mine 4MBs of onboard ram!

that means i will never get the direct rendering with a resolution of 1024x768 (that's also the "default" lcd resolution....)?

---

### Post by Ariccanfly on 2006-12-02
yeah, so if you follow the instructions
[http://dri.freedesktop.org/wiki/Building](http://dri.freedesktop.org/wiki/Building)
and if your a noob, make sure your sober! 
and use the modified ati_pcigart.c
it works! took 2 hs to compile everything on my old beater comp.
wow this video card is from 1998...

No direct rendering, but i think thats becasue 4 of the 8 megs on my card are broken.. well im not turning the rez down....

Youtube's videos run at full speed!

thanks alot ati_pcigart.c god person...

Xfe Edgy 700mhz celeron 256ram 4mg ati3d rage is all you need!

---

### Post by A2K on 2006-12-06
I have self-compiled kernel 2.6.18 and Xorg 7.1.1.
Installed everything like in 1st post.

Now when i start X-server, it writes to log:

(II) Module ati: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 6.5.7
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 0.8
(EE) module ABI major version (0) doesn't match the server's version (1)
(II) UnloadModule: "ati"
(II) Unloading /usr/lib/xorg/modules/drivers/ati_drv.so
(EE) Failed to load module "ati" (module requirement mismatch, 0)

does somebody know how to fix this?

---

### Post by stalefries on 2006-12-08
I just want to say thank you, the hacked Edgy version of the HOWTO worked splendidly! I can't thank you enough! My glxgears FPS went from ~80fps to ~160fps!

---

### Post by Bronco200 on 2006-12-09
HeyHo,

little feedback.
It works also with a Compaq EVO N400c with Edgy Eft Kernel 2.6.17-10 and the hacked Version. :cool: 
Thanks for your work :KS .

Now the next, did anyone of you makes a 3D Desktop to run with the Rage Mobility P/M ?


greetings 
Bronco

---

### Post by bodhi.zazen on 2006-12-15
Nice How-to

This thread has been added to the UDSF wiki.

[3daccelleration_-_mach64](http://doc.gwos.org/index.php/3daccelleration_-_mach64)

---

### Post by derflooh on 2006-12-16
It does not work for me. Here's a part of the log:

```
(II) ATI(0): [drm] SAREA 2200+1208: 3408
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
[drm] failed to load kernel module "mach64"
(II) ATI(0): [drm] drmOpen failed
(EE) ATI(0): [dri] DRIScreenInit Failed
```

Here you can see the full Xorg.0.log:

[http://paste.ubuntu-nl.org/37353/](http://paste.ubuntu-nl.org/37353/)

I hope you can help me.

greetz

---

### Post by sam2 on 2006-12-16
Thanks!

My card is
ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
Total Mem: 4096 kB

It works with Edgy Eft Kernel 2.6.17-10 and the hacked Version @ Depth 16 Modes "800x600".

$ glxgears -printfps
456 frames in 6.1 seconds = 75.109 FPS -> 601 frames in 5.0 seconds = 120.161 FPS

---

### Post by macozz on 2006-12-18
All was working fine up to today's update to kernel 2.6.20 (Feisty). I managed to compile the mach64 module a few days ago, but now it refuse to compile and the dri.log give me this:
make DRM_MODULES=mach64.o modules
make[1]: Entering directory `/home/mario/Download/Utils/mach64-20060403-linux.i
make -C /lib/modules/2.6.20-2-generic/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modu
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-2-generic'
  CC [M]  /home/mario/Download/Utils/mach64-20060403-linux.i386/drm/linux-core/
/home/mario/Download/Utils/mach64-20060403-linux.i386/drm/linux-core/drm_stub.c
make[3]: *** [/home/mario/Download/Utils/mach64-20060403-linux.i386/drm/linux-c
make[2]: *** [_module_/home/mario/Download/Utils/mach64-20060403-linux.i386/drm
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-2-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/mario/Download/Utils/mach64-20060403-linux.i3
make: *** [mach64.o] Error 2

An this is the error message after ./install.sh:
Compiling...
ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.

Modules and headers (as well as the kernel-source and all the other development packages) are there...
Some suggestion?

Thanks!

---

### Post by stalefries on 2006-12-20
Well, I had to redo the whole process because of the new kernel, but it worked fine. 
Edit: including the modified ati_pcigart.c
```
glxinfo | grep direct
libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: Yes

```

---

### Post by MASTo on 2006-12-29
I don't know why I obtain next message in dri.log ...

```

make -C /lib/modules/2.6.19-gentoo-r1/source  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-2.6.19-gentoo-r1'
  CC [M]  /usr/src/mach64-20060403-linux.i386/drm/linux-core/drm_auth.o
In file included from /usr/src/mach64-20060403-linux.i386/drm/linux-core/drm_auth.c:36:
/usr/src/mach64-20060403-linux.i386/drm/linux-core/drmP.h:44:26: error: linux/config.h: No such file or directory
make[3]: *** [/usr/src/mach64-20060403-linux.i386/drm/linux-core/drm_auth.o] Error 1
make[2]: *** [_module_/usr/src/mach64-20060403-linux.i386/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-2.6.19-gentoo-r1'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/mach64-20060403-linux.i386/drm/linux-core'
make: *** [mach64.o] Error 2

```


Please, any help ???

I'm in 2.6.19r1 kernel

---

### Post by ppg on 2006-12-31
It's dang obvious that mach64 is a sore point with Ubuntu. I've been trying to search for my own solution but no luck so far for me as well. I've tried using the binaries posted in the first post of this thread,  the latest binaries available on the snapshots page (failing with the mysterious 'struct_page' error on the mach64 driver) and even attempted to build from CVS (_since new snapshots are no longer being built_ and any issue with the kernel would not be resolved by using outdated code), all unsuccessfully.

One of the main developers on the mach64 branch has stated that his laptop with the Rage Mobility chip has died and the project no longer affects him personally. It seems that it will be a cold day in hell before there will be a rewrite of the mach64 driver to fix the potential security issues and its eventual incorporation into the main Xorg source trees.

It's frustrating and disenchanting to see this thread and its wiki version on 3dacceleration are the top hits on Google about getting DRI to work with a mach64-series card on Ubuntu. With close to 40 000 views of this thread, it's difficult to comprehend that there is no one out there with the technical expertise to make it work. If I knew how, I'd make it work.

Yes, the Rage Mobility is an old graphics chip, but as evidenced from the search results, people still use it.

So how the* hell* do you get DRI to work on Edgy Eft?!?

---

### Post by sysdemin on 2007-01-04
> **A2K said:**
> I have self-compiled kernel 2.6.18 and Xorg 7.1.1.
Installed everything like in 1st post.

Now when i start X-server, it writes to log:

(II) Module ati: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 6.5.7
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 0.8
(EE) module ABI major version (0) doesn't match the server's version (1)
(II) UnloadModule: "ati"
(II) Unloading /usr/lib/xorg/modules/drivers/ati_drv.so
(EE) Failed to load module "ati" (module requirement mismatch, 0)

does somebody know how to fix this?

Messing around with the suggestions from this page (first post + installing xorg-dev and using the modified ati_pcigart.c), I got a similar fault. It can be fixed by reinstalling the xserver-xorg-video-ati package (I'm on Edgy).

This can be done from the commandline as such
```
 sudo dpkg --ignore-depends xserver-xorg-video-ati -r xserver-xorg-video-ati
sudo apt-get install xserver-xorg-video-ati
```


However I still get direct rendering: No from glxinfo.
On the other hand the
OpenGL renderer string: Mesa DRI Mach64 [Rage Pro] 20051019 AGP 2x further down says something's right. mach64 module is loaded and theres no errormessages regarding direct rendering in Xorg.0.log.

oh, by the way, I had to make a symbolic link:
```
mkdir -p /home/felix/src/snapshots/inst/HEAD/lib/dri/
cd /home/felix/src/snapshots/inst/HEAD/lib/dri/
ln -s /usr/lib/dri/mach64_dri.so
```
Otherwise AIGLX complained about not finding mach64_dri.so

glxgears -iacknowledgethatthistoolisnotabenchmark goes from 150fps to 180-190 fps and the cpu utilisation is no longer dominated by user. So it works partly.

---

### Post by sysdemin on 2007-01-04
> **ppg said:**
>  It seems that it will be a cold day in hell before there will be a rewrite of the mach64 driver to fix the potential security issues and its eventual incorporation into the main Xorg source trees.

Maybe a complete rewrite is not nescessary, a lot of people seem not to worry about the potential security issues on their personal laptops. Of course the mach64 should not be enabled by default, but maybe it could be included into a nonsecure part, which is made available as a package "xserver-xorg-video-mach64-unsecure",

Alternatively place mach64.ko so it need to be actively enabled (mach64.so placed in a directory where it can't be loaded, so that it would be a matter of a mv command to enable it?).

Anyone with a working mach64 driver who knows how to build deb-packages?

Otherwise great thread with good suggestions, I almost got it working myself.

---

### Post by sanso on 2007-01-27
Worked for me! Cheers!!

I had to reinstall libgl1-mesa-glx because of some earlier experiments (the error message was something like can't open libGL.so.1 or such) 

Thanks a lot!

using googleearth still sucks, though, even if glxinfo tells me direct rendering is on :)
I guess the mach64 series are a little outdated by now ;)

---

### Post by Dominicus on 2007-01-30
How did you get this to work in Edgy?  Are you using the 686 kernel?
I haven't been able to get this to compile since get warning I need "latest" headers (which I do, but for the -generic kernel).

Thx!Dominicus

---

### Post by Dominicus on 2007-01-31
WOA!!! I finally got this to work!!!!!
I have Edgy 6.10 with the -generic kernel.

The KEY enabler was Ally_S 's hacked gpart (go to her post here [http://www.ubuntuforums.org/showthread.php?t=7200&page=7](http://www.ubuntuforums.org/showthread.php?t=7200&page=7))

After following these directions, the mach64 drivers compiled successfully.

I still didn't get DRI, because I had to modprobe the mach64 (see the troubleshooting section at the top of this how-to).

I also had to reconfigure xorg to permanently lower the resolution to 1024x768 with bit depth of 16.

After reboot....got this:
```
glxinfo | grep direct
libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: Yes
```

3D Screensavers are running....oh how much adrenaline can we still draw from these old clunkers?

---

### Post by GRD on 2007-02-01
Works =):D

---

### Post by oasick on 2007-02-07
Hi !!

I can't compile mach64-20060403-linux.i386 to have 3d acceleration for my compaq evo n400c graphic ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64) on Ubuntu feisty with the 2.6.20-6 kernel. I have the Linux headers, build-essential and gcc but I always have the same problem :


[I]The script will now compile the DRM kernel modules for your machine.

Press ENTER to continue or CTRL-C to exit.

Compiling...
ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.[/I]


Anyone to help me, please?? Thanxs

---

### Post by GRD on 2007-02-08
See page 7. You must change 1 file =):)

---

### Post by oasick on 2007-02-08
Thank you GRD , I know it. I had 3d acceleration in ubuntu edgy with this pach but now i can't compile it in feisty with de latest kernel 2.6.20-6 ...

---

### Post by GRD on 2007-02-08
Sorry. I think you must do some changes in this driver to support new kernel =(:confused:

---

### Post by Ally_S on 2007-02-12
Not checked this thread for a while, but I'm glad to see my modified ati_pcigart.c has helped some people out!

---

### Post by Dominicus on 2007-02-13
Thank You, Ally_S for your modification of ati_pcigart.c

This has been working great.  It's brought this older laptop back to daily use for my daughter.   This hardware was ultra-sluggish under windoze, but Ubuntu is running fast, and now with 3D the experience is more than utilitarian, she's got the fireworks going.
My daughter saw me doing Beryl on my desktop and has been asking if it's possible to run this with this Rage card.  Tried but failed to start.
Is this hopeless case?
Anyway...if you look back posts, you'll see someone thank the "pcigart god person"...I second that, ur a goddess.  cheers.

---

### Post by danomatika on 2007-02-15
Awesome ... got dri on my Xybernaut MA V mobile.  It's pretty sweet to have full 3d acceleration on a computer that fits in your hand.

Used the ati_pcigart.c hack and alls well so far ... hmm security, schmerity.

---

### Post by Dominicus on 2007-02-17
Well this was short-lived...just upgraded to the new Kernel linux-generic-17-11 and mach64 won't compile anymore, even with Ally_S's modified ati_pcigart.c

It was good while it lasted. Dominipater.

---

### Post by Sebastral on 2007-02-20
> **Dominicus said:**
> Well this was short-lived...just upgraded to the new Kernel linux-generic-17-11 and mach64 won't compile anymore, even with Ally_S's modified ati_pcigart.c

It was good while it lasted. Dominipater.
Well, it does compile for me with Ally_S's ati_pciart.c on a fresh generic-17-11 edgy..

The joy was short-lived as I soon discovered the LT Rage Pro in my compaq m300 notebook has only 4mb memory :(
> **mrgamer said:**
> hi everyone, i've an old laptop Dell L400 with a mach64 onboard with 4MB of ram

[..]

the only way i succeeded to run direct rendering with the above HOWTO is @ 800x600 :( 

so the main problem is 1024*768*3*1 = more than mine 4MBs of onboard ram!

that means i will never get the direct rendering with a resolution of 1024x768 (that's also the "default" lcd resolution....)?
I guess. For 1024x768 with 4mb to work DRI should be able to do 13 bit or lower :(. Btw, wether I set xorg.conf to 15,16 or 24 bit I get artifacts, you? Guess also cause of memory shortage, but I don't remember having this problem in windows.

---

### Post by audiophyl on 2007-04-04
The process detailed in this tutorial is for an old version of X.org.  I have successfully enable DRI with my ATI Rage Mobility M1 in 7.04 Feisty Fawn (X.org 7.2).  The steps are a bit involved, but it's all quite nicely documented on xorg.freedesktop.org.  Also, it's entirely possible that there is an easier way to grab the necessary sources than via GIT, but this way you will have the newest ATI driver.

**NOTE**: I have not tried this on anything other than 7.04!  Follow these steps at your own risk with earlier versions of Ubuntu.

**EDIT**: After the Ubuntu upgrade to 2.6.20-14, I downloaded everything again and tried to duplicate the process with these instructions with one hitch.  The source for /tmp/working/drm/linux-core/drm_compat.c needs to have the vm_insert_pfn() function block-commented out.  This is kind of a pain in the butt way to go about doing things!

**SOURCES**:
[Compiling Modular X.org Source]("http://xorg.freedesktop.org/wiki/ModularDevelopersGuide")
[Compiling DRI/DRM Support]("http://dri.freedesktop.org/wiki/Building")

The rough steps are as follows:

1. install the needed sources, headers, and software
```
sudo apt-get build-dep mesa
sudo apt-get build-dep libdrm
sudo apt-get install git-core autoconf automake libtool
sudo apt-get install libxmu-headers libxmu-dev libxi-dev libdrm-dev libxfixes-dev libxdamage-dev mesa-common-dev
sudo apt-get install xserver-xorg-dev
```

2. install the latest source trees for drm and mesa in a new directory
```
mkdir /tmp/working
cd /tmp/working
wget 'http://xorg.freedesktop.org/wiki/ModularDevelopersGuide?action=AttachFile&do=get&target=git_xorg.sh' -O git_xorg.sh
chmod a+x git_xorg.sh
./git_xorg.sh
git clone git://anongit.freedesktop.org/git/mesa/mesa
```
and finally, in the event that this doesn't download the 'drm' folder:
```
git clone git://anongit.freedesktop.org/git/mesa/drm
```

3. prepare the build directory
```
mkdir /tmp/build-dir
mkdir /tmp/build-dir/mesalibs
mkdir /tmp/build-dir/drm
```

4. prepare to build the new ati driver
sometimes running 'make' during steps 3 and 4 will result in a '**nothing to make**' message.  **don't panic!**  the documentation for the build states this is normal and to run the 'make' instruction prior to a 'make install' regardless.
```
cd /tmp/working/util/macros
./autogen.sh --prefix=/tmp/build-dir
make
make install
export PKG_CONFIG_PATH=/tmp/build-dir/lib/pkgconfig
export ACLOCAL="aclocal -I /tmp/build-dir/share/aclocal"
```

5. build the necessary protos for the driver build step
```
cd /tmp/working/proto/fontsproto
./autogen.sh --prefix=/tmp/build-dir
make
make install
cd /tmp/working/proto/xineramaproto
./autogen.sh --prefix=/tmp/build-dir
make
make install
cd /tmp/working/proto/xf86miscproto
./autogen.sh --prefix=/tmp/build-dir
make
make install
cd /tmp/working/proto/xf86driproto
./autogen.sh --prefix=/tmp/build-dir
make
make install
cd /tmp/working/proto/randrproto
./autogen.sh --prefix=/tmp/build-dir
make
make install
cd /tmp/working/proto/randerproto
./autogen.sh --prefix=/tmp/build-dir
make
make install
cd /tmp/working/proto/videoproto
./autogen.sh --prefix=/tmp/build-dir
make
make install
```

6. build the new ati driver
```
cd /tmp/working/driver/xf86-video-ati
./autogen.sh --prefix=/tmp/build-dir
make
make install
```

7. build dri in the mesa tree (use **make linux-dri-x86** for x86-specific optimizations)
```
cd /tmp/working/mesa
nano configs/linux-dri
//locate the line that begins 'DRI_DIRS = ....' (near the bottom) and edit it to be 'DRI_DIRS = mach64'
//this will build only the DRI module that you need
make linux-dri
cp -P /tmp/working/mesa/lib/* /tmp/build-dir/mesalibs
```

8. build drm **NOTE:** if you see "error: previous declaration of &#8216;vm_insert_pfn&#8217; was here", you will need to comment out the function "vm_insert_pfn" in drm_compat.c and run make again.
```
cd /tmp/working/drm/linux-core
make mach64.o
cp *.ko /tmp/build-dir/drm
```

9. make backups of files from the following locations:
/lib/modules/$KERNEL/kernel/drivers/char/drm/     (make a backup of drm.ko)
/usr/lib/xorg/modules/drivers/    (at least backup ati_drv.so, atimisc_drv.so, r128_drv.so, and radeon_drv.so)
/usr/lib/dri/   (backup everything)

10. install everything (the last command will cause X to quit, and it will come back using the new driver...  but you'll still need to reboot for DRI to load)
```
sudo cp -P /tmp/build-dir/mesalibs/* /usr/lib/dri/
sudo cp /tmp/build-dir/drm/* /lib/modules/$KERNEL/kernel/drivers/char/drm/
sudo depmod -a
sudo cp /tmp/build-dir/lib/xorg/modules/drivers/* /usr/lib/xorg/modules/drivers/
```

11. reboot and check glxinfo.  if X won't work, at least you made backups in step 9.  you DID do that, didn't you?

---

### Post by ellobo on 2007-04-20
when I'm doing ./autogen.sh --prefix=/tmp/build-dir , I get an error like this:
./configure: line 20021: syntax error near unexpected token 'XINERAMA,'
./configure: line 20021: 'XORG_DRIVER_CHECK_EXT(XINERAMA, xineramaproto)'

And it won't create Makefile, so I cannot continue. Could someone help me?

---

### Post by audiophyl on 2007-04-20
i did some searching regarding your error, and came across something related to libdrm needing to be rebuilt, as well.  give this a shot:

```
cd /tmp/working/drm
./autogen.sh
./configure --prefix=/tmp/build-dir
make install
```

this will create libdrm files in /tmp/build-dir/lib/, and these will need to be copied into your /usr/lib folder using the following command:

```
cd /tmp/build-dir/lib/
cp -P libdrm* /usr/lib/
```

after you've done this, back up in the build process to step 4.  hope this works out for you!  i may need to add this to the instructions...

-philip

p.s. - another possibility is that the source was broken at the time that you downloaded it...  in which case you can just run ./git_xorg.sh again and it will only download updates to the source.

---

### Post by ppg on 2007-04-21
I too am getting the 'syntax error near unexpected token' message after trying to run the autogen.sh for the ati driver (step 6). I thought it was a problem with XINERAMA so I tried commenting out that line to no avail; the error message just comes up with the next line.

If this is indeed faulty code, what would be a way to get older sources?

---

### Post by audiophyl on 2007-04-21
Out of curiosity, do you have the file /usr/include/xorg/xorg-server.h in your installation?

There was an omission in Step 1, as I had previously installed xserver-xorg-dev for a different reason...  It didn't even cross my mind that this would depend on it, as well.

```

sudo apt-get install xserver-xorg-dev
```

This is now included in Step 1 above.

---

### Post by ppg on 2007-04-21
Nope. There isn't even an xorg folder.

Edit: got the xserver-xorg-dev package and now there is. Trying it all again now.
[COLOR="Silver"]
Extra edit: turned out that I needed to download extra dev packages (randr, render and video) before it would go past step 5. I have completed all the steps but I still do not have DRI, according to GLXinfo.[/COLOR]

Edit 3: YES it works. Thank you, kind sir!

---

### Post by audiophyl on 2007-04-22
Thank YOU for helping me locate the error in my instructions!  I'm glad it works for you now.

-Philip

---

### Post by SparcMan on 2007-04-23
Well after hours of mucking around (I had tons of problems getting the modules to compile until I updated automake to ver 1.9), i got this working to a degree. I clearly have 3D accelleration working now, but missing things like some textures and transparency. in glxinfo I get 4 "DISPATCH ERROR!" Messages. 
DISPATCH ERROR! _glapi_add_dispatch failed to add glAreTexturesResident!
DISPATCH ERROR! _glapi_add_dispatch failed to add glGenTextures!
DISPATCH ERROR! _glapi_add_dispatch failed to add glIsTexture!
DISPATCH ERROR! _glapi_add_dispatch failed to add glGetVertexAttribPointerv!
followed by:
libGL warning: 3D driver claims to not support visual 0x4b

Any tweaks you could recommend? Thanks!
(using a Dell Inspiron 3800 with integrated Mobility M1 with Xubuntu 6.10)

---

### Post by Richieeeeeee on 2007-04-24
Hi!!

I am hanging on step seven: There is no directory /tmp/working/mesa

Whats my mistake?

Richie

---

### Post by ellobo on 2007-04-24
> **ppg said:**
> turned out that I needed to download extra dev packages (randr, render and video) before it would go past step 5. I have completed all the steps but I still do not have DRI, according to GLXinfo.

I had to autogenerate ja make install those randr, render and video. After that rest went smoothly to the end. But glxinfo states still Direct Rendering NO. xorg.conf has 16-bit color and everything should be ok, but something is still wrong I guess. :(

---

### Post by audiophyl on 2007-04-25
Make sure you ran the last command in step 2 while in /tmp/working/ to ensure you have downloaded mesa.

Hope this helps!

-Philip

---

### Post by popzz on 2007-04-27
hello all
Thanks for the tuto but:....

After have adding 
sudo apt-get install x11proto-render-dev
sudo apt-get install x11proto-video-dev
sudo apt-get install x11proto-randr-dev

and modified tmp/working/mesa/configs/linux-dri (to be 'DRI_DIRS = mach64')
and modified /tmp/working/drm/linux-core/drm_compat.c (comment out the function "vm_insert_pfn" )=> /*static int vm_insert_pfn

and do before step 4

cd /tmp/working/drm
./autogen.sh
./configure --prefix=/tmp/build-dir
make install
cd /tmp/build-dir/lib/
sudo cp -P libdrm* /usr/lib/ (must be su to copy)


seems that all is ok but at step 10
pop@pop-laptop:/tmp/working/drm/linux-core$ sudo cp -P /tmp/build-dir/lib/mesalibs/* /usr/lib/dri/

cp: ne peut évaluer `/tmp/build-dir/lib/mesalibs/*': Aucun fichier ou répertoire de ce type

(There is no directory /tmp/build-dir/lib/mesalibs/)

pop@pop-laptop:/tmp/working/drm/linux-core$ sudo cp /tmp/build-dir/drm/* /lib/modules/$KERNEL/kernel/drivers/char/drm/
cp: la cible `/lib/modules//kernel/drivers/char/drm/' n'est pas un répertoire: Aucun fichier ou répertoire de ce type

(and no directory /lib/modules//kernel/drivers/char/drm/)

pop@pop-laptop:/tmp/working/drm/linux-core$ sudo cp /tmp/build-dir/drm/* /lib/modules/$KERNEL/kernel/drivers/char/drm/


And then after reboot

pop@pop-laptop:~$ glxinfo | grep "direct rendering"Mach64 DRI driver expected DRM version 1.0.x but got version 2.0.0
libGL warning: 3D driver returned no fbconfigs.
libGL error: InitDriver failed
libGL error: reverting to (slow) indirect rendering
direct rendering: No

Don't know where i miss something?


Any help??

---

### Post by audiophyl on 2007-04-27
Oops, you spotted another typo in my list of steps...  The directory is /tmp/build-dir/mesalibs, not /tmp/build-dir/lib/mesalibs.

My apologies!

-Philip

---

### Post by popzz on 2007-04-27
hello
so... no luck i have to re-install fresh version from CD feisty (7.04) and then... it seems to work 

pop@pop:~$ glxinfo | grep "direct"
direct rendering: Yes

But it seems to be very slow for direct rending...

So i thing to go back to edgy util another way to enable direct rending

Thank you for all

POP

---

### Post by mrojas73 on 2007-05-05
How do comment out the vm_insert line?  I tried /* lllllllllll */ but that didn't work.

unlock:
	spin_unlock(&mm->page_table_lock);
	return ret;
}

 static int vm_insert_pfn(struct vm_area_struct *vma, unsigned long addr,
		  unsigned long pfn)

{
	int ret;
	if (!drm_pte_is_clear(vma, addr))
		return -EBUSY;


Thank you.

---

### Post by popzz on 2007-05-06
> **mrojas73 said:**
> How do comment out the vm_insert line?  I tried /* lllllllllll */ but that didn't work.

unlock:
	spin_unlock(&mm->page_table_lock);
	return ret;
}

 static int vm_insert_pfn(struct vm_area_struct *vma, unsigned long addr,
		  unsigned long pfn)

{
	int ret;
	if (!drm_pte_is_clear(vma, addr))
		return -EBUSY;


Thank you.

Hello
For i've done this:
/*static int vm_insert_pfn(struct vm_area_struct *vma, unsigned long addr,
		  unsigned long pfn)
{
	int ret;
	if (!drm_pte_is_clear(vma, addr))
		return -EBUSY;

	ret = io_remap_pfn_range(vma, addr, pfn, PAGE_SIZE, vma->vm_page_prot);
	return ret;
}*/

And it works
Bye

---

### Post by mrojas73 on 2007-05-06
Thank you.  Everything went fine after tht 8 step however I still don't have rendering enabled.

---

### Post by popzz on 2007-05-06
> **mrojas73 said:**
> Thank you.  Everything went fine after tht 8 step however I still don't have rendering enabled.

So ... What's the message?
don't forget to replace $KERNEL by the value on uname -r and  do before step 4

cd /tmp/working/drm
./autogen.sh
./configure --prefix=/tmp/build-dir
make install
cd /tmp/build-dir/lib/
sudo cp -P libdrm* /usr/lib/ (must be su to copy)

Bye

---

### Post by mrojas73 on 2007-05-06
> **popzz said:**
> So ... What's the message?
don't forget to replace $KERNEL by the value on uname -r and  do before step 4

cd /tmp/working/drm
./autogen.sh
./configure --prefix=/tmp/build-dir
make install
cd /tmp/build-dir/lib/
sudo cp -P libdrm* /usr/lib/ (must be su to copy)

Bye

I did, and got no erros as far as a remember.  I will try it again, thank you for your help.

---

### Post by redrum on 2007-05-07
Hello guys,

Thanks for the wonderful work concerning mach64.

I've got an old computer with very old video chipset :

```

01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)

```

I follow all the steps successfully.
I load the following module in /etc/modules :

```

agpgart
intel-agp
drm
mach64

```

But something goes wrong at the final reboot.

If I well understand, it seems to be a conflict between the new compiled drm module and already existed one loaded by the kernel. This conflict gives the following warning with dmesg :

```
[   77.887380] [drm] Initialized drm 1.1.0 20060810
[   78.030780] mach64: disagrees about version of symbol drm_open
[   78.030801] mach64: Unknown symbol drm_open
[   78.031163] mach64: disagrees about version of symbol drm_fasync
[   78.031174] mach64: Unknown symbol drm_fasync
[   78.031535] mach64: disagrees about version of symbol drm_poll
[   78.031546] mach64: Unknown symbol drm_poll
[   78.032047] mach64: disagrees about version of symbol drm_core_get_reg_ofs
[   78.032058] mach64: Unknown symbol drm_core_get_reg_ofs
[   78.032507] mach64: disagrees about version of symbol drm_pci_alloc
[   78.032518] mach64: Unknown symbol drm_pci_alloc
[   78.032879] mach64: disagrees about version of symbol drm_irq_uninstall
[   78.032891] mach64: Unknown symbol drm_irq_uninstall
[   78.033506] mach64: Unknown symbol drm_get_dev
[   78.033938] mach64: disagrees about version of symbol drm_ioctl
[   78.033950] mach64: Unknown symbol drm_ioctl
[   78.034308] mach64: disagrees about version of symbol drm_exit
[   78.034318] mach64: Unknown symbol drm_exit
[   78.034813] mach64: Unknown symbol drm_getsarea
[   78.035526] mach64: disagrees about version of symbol drm_core_ioremapfree
[   78.035538] mach64: Unknown symbol drm_core_ioremapfree
[   78.035900] mach64: disagrees about version of symbol drm_core_get_map_ofs
[   78.035912] mach64: Unknown symbol drm_core_get_map_ofs
[   78.036270] mach64: disagrees about version of symbol drm_init
[   78.036280] mach64: Unknown symbol drm_init
[   78.036795] mach64: disagrees about version of symbol drm_vbl_send_signals
[   78.036807] mach64: Unknown symbol drm_vbl_send_signals
[   78.037312] mach64: Unknown symbol drm_cleanup_pci
[   78.037687] mach64: disagrees about version of symbol drm_pci_free
[   78.037699] mach64: Unknown symbol drm_pci_free
[   78.038088] mach64: disagrees about version of symbol drm_core_ioremap
[   78.038101] mach64: Unknown symbol drm_core_ioremap
[   78.038459] mach64: disagrees about version of symbol drm_mmap
[   78.038470] mach64: Unknown symbol drm_mmap
[   78.038930] mach64: disagrees about version of symbol drm_core_reclaim_buffers
[   78.038942] mach64: Unknown symbol drm_core_reclaim_buffers
[   78.039297] mach64: disagrees about version of symbol drm_release
[   78.039308] mach64: Unknown symbol drm_release
[  271.328310] mach64: disagrees about version of symbol drm_open
[  271.328345] mach64: Unknown symbol drm_open
[  271.328707] mach64: disagrees about version of symbol drm_fasync
[  271.328718] mach64: Unknown symbol drm_fasync
[  271.329079] mach64: disagrees about version of symbol drm_poll
[  271.329090] mach64: Unknown symbol drm_poll
[  271.329592] mach64: disagrees about version of symbol drm_core_get_reg_ofs
[  271.329604] mach64: Unknown symbol drm_core_get_reg_ofs
[  271.330084] mach64: disagrees about version of symbol drm_pci_alloc
[  271.330097] mach64: Unknown symbol drm_pci_alloc
[  271.330459] mach64: disagrees about version of symbol drm_irq_uninstall
[  271.330471] mach64: Unknown symbol drm_irq_uninstall
[  271.331087] mach64: Unknown symbol drm_get_dev
[  271.331491] mach64: disagrees about version of symbol drm_ioctl
[  271.331502] mach64: Unknown symbol drm_ioctl
[  271.331860] mach64: disagrees about version of symbol drm_exit
[  271.331871] mach64: Unknown symbol drm_exit
[  271.332364] mach64: Unknown symbol drm_getsarea
[  271.333077] mach64: disagrees about version of symbol drm_core_ioremapfree
[  271.333089] mach64: Unknown symbol drm_core_ioremapfree
[  271.333452] mach64: disagrees about version of symbol drm_core_get_map_ofs
[  271.333464] mach64: Unknown symbol drm_core_get_map_ofs
[  271.333822] mach64: disagrees about version of symbol drm_init
[  271.333833] mach64: Unknown symbol drm_init
[  271.334365] mach64: disagrees about version of symbol drm_vbl_send_signals
[  271.334379] mach64: Unknown symbol drm_vbl_send_signals
[  271.334886] mach64: Unknown symbol drm_cleanup_pci
[  271.335261] mach64: disagrees about version of symbol drm_pci_free
[  271.335272] mach64: Unknown symbol drm_pci_free
[  271.335631] mach64: disagrees about version of symbol drm_core_ioremap
[  271.335643] mach64: Unknown symbol drm_core_ioremap
[  271.336001] mach64: disagrees about version of symbol drm_mmap
[  271.336012] mach64: Unknown symbol drm_mmap
[  271.336471] mach64: disagrees about version of symbol drm_core_reclaim_buffers
[  271.336484] mach64: Unknown symbol drm_core_reclaim_buffers
[  271.336840] mach64: disagrees about version of symbol drm_release
[  271.336851] mach64: Unknown symbol drm_release
```

How could I solve this ? Am I obliged to recompile xorg myself ?

Regards,

---

### Post by audiophyl on 2007-05-07
What modules did you rebuild?

Two possible problems are that you either didn't rebuild the drm.ko module or you didn't run depmod as per the instructions.

You shouldn't need to force the modules to load.

-Philip

---

### Post by redrum on 2007-05-07
Philip,  I made everything you described in your how-to. There was two *.ko (mach4 and drm) I copied in the proper location. Moreover I ran depmod as required.

---

### Post by Richieeeeeee on 2007-05-09
Hello!

After hours of trying to compile here a little question:

Why can't anybody just upload the successfully compiled driver for the current Feisty Kernel here? Then it would be easy to replace the files on my notebook and having direct rendering!

Or not?

Richie

---

### Post by audiophyl on 2007-05-10
Richie,

During the beta phase, a new kernel version was being released every few days.  That meant that, every few days, I would need to go through the process of compiling the necessary modules.  Now that Feisty has been released, I expect new kernels will be released less frequently, but the same problem remains: if you're using pre-compiled binaries and upgrade to a new kernel, you have to wait for new pre-compiled binaries.  In the long run, the simpler solution *is* to compile everything yourself.

Whoever releases binaries should also feel some level of responsibility to support them, as well...

-Philip

---

### Post by Richieeeeeee on 2007-05-10
Thank you for answering!!

You are right!! But I can't really compile it! I tryed it more than 5 hours - for nothing. And I would stay with one kernel, as long as I can! I considered even to "downgrade" my system to a earlier Ubuntu version - only for enjoying the drivers!

If you like, you can PM me these drivers for the current Feisty Kernel, so you don't have to maintain it. I will ask you not again.

Richie

---

### Post by Richieeeeeee on 2007-05-10
PS: Moreover we should bring the ubuntu developer to compile the driver with direct rendering. That would be better...

---

### Post by popzz on 2007-05-10
+1 like in anothers distributions  linux:) :grin:

---

### Post by acid on 2007-05-11
has anyone got detailed yet SIMPLE ..instructions on how to enable DRI ?
I have gone thru this Thred and see a bunch of instructions.....doing this ...that....Compiling....Can someone Just post one massive tut for us all to follow...and a WORKING tutorial at that.

---

### Post by audiophyl on 2007-05-13
redrum:

This guide assumes you are using 7.04 'Feisty Fawn'...  can you verify that?  Second, your log shows a DRM module date of August 10, 2006:```
[   77.887380] [drm] Initialized drm 1.1.0 20060810
```

What is the full output of an 'ls -la' within the drm subfolder of your kernel driver directory?  That directory should be something like /lib/modules/$KERNEL/kernel/drivers/char/drm.  The date on drm.ko and mach64.ko should be the same as each other, but different than all of the others.  If you compiled both the drm and mach64 module, then sudo cp'd them, then sudo depmod'd, there should be no version disagreements...  because the files will have the same version as each other.

Richieeeeeee and popzz (and everyone else wanting default Mach64 DRI):

Agreed!  There is a bug report at [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/34590](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/34590) that is presently classified as a "wishlist" item for this feature.  Go there and express your support for it!

Acid:

I've done my best to provide concise instructions for a process that works for me, as I only have my computer to test these steps on.  This can be found as comment #102 on page 11 of this thread.  As for "SIMPLE", I really do wish there were a simpler way.

My first time around cost nearly five hours of my time, writing up the instructions cost me another hour, submitting a feature request/bug report to launchpad cost me 15-30 minutes, and coming back to this forum every couple days to see if anyone is having problems with my instructions has cost me quite a bit of time as well.  Oh dear GOD, how I wish there were a simpler way.  :)

Since people tend to like the car analogy when it comes to technology  (I hate it)...  don't count on finding "SIMPLE" instructions for replacing your car engine at home with no tools and without needing to get grease on your hands.  Especially if nobody builds your engine anymore, so you're forced to build your own.  I am only able to attempt assistance if people provide the actual text of any error messages they receive while following these steps, during compilation or within their logs.  I really will help to the best of my abilities.

Assuming you have tried my tutorial, what part are you getting hung up on?

---

### Post by Tyr Norian on 2007-05-20
audiophyl is *awesome*. After trying no fewer than four separate HOWTOs online for this very problem, I ran through his guide without a hitch and now have both direct rendering and OpenGL functionality on my Rage Mobility card for this Compaq Armada E500, a problem I had thought was insoluble.

glxgears gives me a framerate of more than six times what I had previously, and the OpenGL screensavers I've tested look gorgeous. I'm now about to install Quake II in order to play it as God intended it.

Thank you very much audiophyl, it's folks like you that make the free software community great.

---

### Post by redrum on 2007-05-20
drwxr-xr-x  2 root root    1024 2007-05-08 16:53 .
drwxr-xr-x 11 root root    1024 2007-05-07 13:14 ..
-rw-r--r--  1 root root 3194321 2007-05-20 12:15 drm.ko
-rw-r--r--  1 root root   24580 2007-04-15 10:07 i810.ko
-rw-r--r--  1 root root   30544 2007-04-15 10:07 i830.ko
-rw-r--r--  1 root root   29884 2007-04-15 10:07 i915.ko
-rw-r--r--  1 root root  584550 2007-05-20 12:15 mach64.ko
-rw-r--r--  1 root root   69512 2007-04-15 10:07 mga.ko
-rw-r--r--  1 root root  127016 2007-04-15 10:07 radeon.ko
-rw-r--r--  1 root root   39868 2007-04-15 10:07 savage.ko
-rw-r--r--  1 root root   11004 2007-04-15 10:07 sis.ko
-rw-r--r--  1 root root    5564 2007-04-15 10:07 tdfx.ko
-rw-r--r--  1 root root   48840 2007-04-15 10:07 via.ko

but dmesg still gives me : [drm] Initialized drm 1.1.0 20060810

---

### Post by spieslikeus on 2007-05-22
I have followed the guide by audiophyl and compiled the mach64 and drm modules and loaded them, but glxinfo still reports no for direct rendering. I have changed my xorg config default color to 16 bit but that still does not help. I'm using feisty with kernel 2.6.20-15. I just don't understand how lsmod can show the modules that i compiled as being loaded but glxinfo still indicates no direct rendering.

---

### Post by swangsongforyou on 2007-05-23
Hi, first of all: sorry for my bad english :oops:

This solution works for me, very easy:

1. Aply **Ally_S** patch on mach64 driver: [http://ubuntuforums.org/showpost.php?p=1701080&postcount=63](http://ubuntuforums.org/showpost.php?p=1701080&postcount=63)

2. Delete this line in file **/mach64-20060403-linux.i386/drm/linux-core/drm_stub.c**:51:

module_param_named(debug, drm_debug, int, S_IRUGO|S_IWUGO);

3.  Remove all **linux/config.h** reference in every file that give us a compilation error.

Thats all... this works for me with the initial method.

If any error at restart (like "ati driver not found"), just reinstall **xserver-xorg-video-ati** package and restart again.


**Found it here**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/34590](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/34590)

Hope this helps someone ;)

---

### Post by audiophyl on 2007-05-24
Tyr Norian:  Many thanks for the kind words.  Nice Sinfest avatar, too.  Are you using 6.10 as your details show, or are you using 7.04?  Quake II was my main motivation for figuring this all out, honestly.  Once I got everything working, I discovered that Return to Castle Wolfenstein works, as well...  It never did in Windows!

redrum:  I should've checked this the first time around, but your version number is right.  Use this command and let me know what the output is - ```
dmesg | grep mach64
```

spieslikeus:  It's possible for the kernel modules to load (which lsmod will show) without the X.org modules loading.  Check the contents of /var/log/Xorg.0.log for any errors pertaining to mach64 or drm.  Hopefully we can find something there!

-Philip

---

### Post by spieslikeus on 2007-05-25
Hi audiophyl, thanks for responding... here are some relevant lines from my Xorg.0.log file...
Note that there are no errors in the file, only warnings as follows...this particular log was generated with the laptop in its docking station, but no direct rendering either way. I am open to any and all suggestions, thanks in advace ;)

(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies Inc Rage Mobility P/M AGP 2x"
...
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) ATI(0): [drm] loaded kernel module for "mach64" driver
(II) ATI(0): [drm] DRM interface version 1.3
(II) ATI(0): [drm] created "mach64" driver at busid "pci:0000:01:00.0"
(II) ATI(0): [drm] added 8192 byte SAREA at 0xe4c40000
(II) ATI(0): [drm] mapped SAREA 0xe4c40000 to 0xb724b000
(II) ATI(0): [drm] framebuffer handle = 0x40000000
(II) ATI(0): [drm] added 1 reserved context for kernel
(II) ATI(0): [drm] Will request asynchronous DMA mode
(==) ATI(0): [agp] Using AGP 2x Mode
(==) ATI(0): [agp] Using 8 MB AGP aperture
(II) ATI(0): [agp] Mode 0x1f000203 [AGP 0x8086/0x7190; Card 0x1002/0x4c4d]
(II) ATI(0): [agp] 8192 kB allocated with handle 0x00000001
(II) ATI(0): [agp] Using 16 kB for DMA descriptor ring
(==) ATI(0): [drm] Using 2 MB for DMA buffers
(II) ATI(0): [agp] Using 6016 kB for AGP textures
(II) ATI(0): [agp] ring handle = 0x50000000
(II) ATI(0): [agp] Ring mapped at 0xb7247000
(II) ATI(0): [agp] vertex buffers handle = 0x50004000
(II) ATI(0): [agp] Vertex buffers mapped at 0xb7047000
(II) ATI(0): [agp] AGP texture region handle = 0x50204000
(II) ATI(0): [agp] AGP Texture region mapped at 0xb6a67000
(II) ATI(0): [drm] register handle = 0x41000000
(II) ATI(0): [dri] Visual configs initialized
(II) ATI(0): [dri] Block 0 base at 0x41000400
(II) ATI(0): Memory manager initialized to (0,0) (1024,2047)
(II) ATI(0): Largest offscreen area available: 1024 x 1279
(II) ATI(0): Will use 511 kB of offscreen memory for XAA
(II) ATI(0): Will use back buffer at offset 0x37f000
(II) ATI(0): Will use depth buffer at offset 0x67f000
(II) ATI(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		10 256x256 slots
(==) ATI(0): Backing store disabled
(==) ATI(0): Silken mouse enabled
(II) ATI(0): X context handle = 0x1
(II) ATI(0): [drm] installed DRM signal handler
(II) ATI(0): [DRI] installation complete
(II) ATI(0): [drm] Added 128 16384 byte DMA buffers
(II) ATI(0): [drm] Mapped 128 DMA buffers at 0xb6867000
(II) ATI(0): [drm] Installed interrupt handler, using IRQ 11
(II) ATI(0): Direct rendering enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/mach64_dri.so
(II) GLX: Initialized DRI GL provider for screen 0

---

### Post by Tyr Norian on 2007-05-25
> **audiophyl said:**
> ... Are you using 6.10 as your details show, or are you using 7.04? 
I'm using 7.04. I forgot to change my profile after I upgraded.

---

### Post by audiophyl on 2007-05-25
spieslikeus:

Here is what my /etc/X11/xorg.conf looks like (just the pertinent spots, though):

...
Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection
...
//this is at the very bottom
Section "DRI"
        Mode    0666
EndSection

-Philip

---

### Post by rarefluid on 2007-05-25
First of all: Thanks for the excellent tutorial audiophyl! Helped me a lot!

spieslikeus: Had the same problem. Take a look at [http://dri.freedesktop.org/wiki/DriTroubleshooting](http://dri.freedesktop.org/wiki/DriTroubleshooting)
I found out what was wrong when I tried:

export LIBGL_DEBUG=verbose
glxinfo

It told me that the library /usr/X11R6/lib/modules/dri/mach64_dri.so couldn't be found. I made a link to the /usl/lib directory:

cd /usr/X11R6/lib
ln -s /usr/lib modules

then glxinfo said Direct Rendering: Yes.
Still some games are really slow, but that might just be the card :( I have a Duron 700 and the ATI Rage XL AGP 2X (aka Xpert 98 RXL AGP 2X) with 16MB VRAM here. What framerates should I expect from glxgears in 32bit? I get ~100fps...
The driver is identified as: " Mesa DRI Mach64 [Rage Pro] 20051019 AGP 2x x86/MMX+/3DNow!+" which seems pretty old to me...

hope it helps...

---

### Post by spieslikeus on 2007-05-25
"spieslikeus: Had the same problem. Take a look at [http://dri.freedesktop.org/wiki/DriTroubleshooting](http://dri.freedesktop.org/wiki/DriTroubleshooting)
I found out what was wrong when I tried:

export LIBGL_DEBUG=verbose
glxinfo

It told me that the library /usr/X11R6/lib/modules/dri/mach64_dri.so couldn't be found."

Yes yes this is what I get too thanks rarefluid!

I did:

cd /usr/X11R6/lib/modules/dri
sudo ln -s /usr/lib/dri/mach64_dri.so mach64_dri.so

"then glxinfo said Direct Rendering: Yes."

Now running glxgears gives:

DISPATCH ERROR! _glapi_add_dispatch failed to add glAreTexturesResident!
DISPATCH ERROR! _glapi_add_dispatch failed to add glGenTextures!
DISPATCH ERROR! _glapi_add_dispatch failed to add glIsTextures!
libGL warning: 3D driver claims to not support visual 0x4b

And I get 183 fps with my shiny old Rage Mobility P/M AGP 2x (rev 64)

Any ideas on these errors guys?
Thanks again audiophyl and rarefluid!

---

### Post by rarefluid on 2007-05-26
Those functions might reside in the new libGL(w?).<whaterver>.so, so you'd better link the whole directory as I did... try that and check if the errors are gone then.
You can check what dlls glxgears loads from where by using ldd, as described in DriTroubleshooting:

ldd /usr/X11R6/bin/glxgears

Also google and the mesa-dev mailing list might be your friends too: [http://www.mail-archive.com/mesa3d-dev@lists.sourceforge.net/msg01600.html](http://www.mail-archive.com/mesa3d-dev@lists.sourceforge.net/msg01600.html)

What bit depth did you get the 180fps in? 16 or 32 bit? and did you change the size of the glxgears window? What cpu do you have and what is your FSB speed? 

Is there some kind of commonly used 3D-benchmark around for Linux systems? I googled, but found nothing... (well [SPECviewperf 9]("http://www.spec.org/gpc/opc.static/vp9info.html"), but that might be overkill and has a CD-sizes download...)

Oh, yeah. And it might be a good idea to not download it to /tmp, because you might need to recompile someday and you will need to download everything again...

---

### Post by Offoffoff on 2007-05-29
I have Pentium III/256MB/ATI Rage Mobility AGP P/M x2. Here is my glxgears' log:
725 frames in 5.1 seconds = 142.286 FPS
319 frames in 5.4 seconds = 59.373 FPS
812 frames in 5.1 seconds = 159.982 FPS
870 frames in 5.2 seconds = 168.693 FPS
203 frames in 5.8 seconds = 34.955 FPS
493 frames in 5.3 seconds = 93.563 FPS
725 frames in 5.0 seconds = 144.301 FPS
783 frames in 5.1 seconds = 154.495 FPS
406 frames in 5.2 seconds = 78.006 FPS
812 frames in 5.1 seconds = 159.458 FPS
261 frames in 5.2 seconds = 50.391 FPS
435 frames in 5.1 seconds = 84.991 FPS

glxgears slows when it go to background. It is maximum for my videocard.

I have no special driver or something, my videocard works with drivers "right out-of-box". And of cause I have no hardware acceleration. 

"glxinfo | grep direct" shows "direct rendering: No OpenGL renderer string: Mesa GLX Indirect".

I see here some "hacks" to make my card to work well, but I also see that tends to some errors in logs... Is it right to do these hacks? Is my system going to die, if I'll did like I see here?

---

### Post by dgrafix on 2007-06-03
Hi,

This looks perfect for what i need, i have that same card, but i begin to loose heart when the instructions say "compile....." I have NEVER been able to compile anything in ubuntu. 

Sure enough i tried it and recieved the message unable to compile. In the dir.log im getting this:

make DRM_MODULES=mach64.o modules
make[1]: Entering directory `/home/dan/mach64-20060325-linux.i386/drm/linux-core'
make -C /lib/modules/2.6.20-16-generic/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/dan/mach64-20060325-linux.i386/drm/linux-core/drm_auth.o
In file included from /home/dan/mach64-20060325-linux.i386/drm/linux-core/drm_auth.c:36:
/home/dan/mach64-20060325-linux.i386/drm/linux-core/drmP.h:44:26: error: linux/config.h: No such file or directory
make[3]: *** [/home/dan/mach64-20060325-linux.i386/drm/linux-core/drm_auth.o] Error 1
make[2]: *** [_module_/home/dan/mach64-20060325-linux.i386/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/dan/mach64-20060325-linux.i386/drm/linux-core'
make: *** [mach64.o] Error 2


LOL I have absolutely no idea what this means :)

---

### Post by audiophyl on 2007-06-04
Offoffoff:

I'm using a Athlon XPm 1800+ (1.5GHz)/512MB/ATI Rage Mobility M1 AGP 2x (8MB) and average ~300fps in glxgears at the default window size, and ~47fps maximized on a 1024x768 screen.  Be reminded GLXGEARS IS NOT A REAL BENCHMARK!!!  :)

However, in Quake 2 with max settings for my laptop I'm seeing ~15fps@1024x768, ~20fps@800x600, and >25fps@640x480.  In Return to Castle Wolfenstein I'm seeing between 13-22fps with High Quality settings at 640x480.  Yes, that sucks...  but in Windows the best framerate I'd ever seen for Return to Castle Wolfenstein on this laptop was about 4fps.

dgrafix:

The linux/config.h error message is mainly because the source you're using is old enough to not take kernel source changes into account.  if you were using 7.04 instead of 6.06, I have documented the process at [http://ubuntuforums.org/showthread.php?p=2399695#post2399695](http://ubuntuforums.org/showthread.php?p=2399695#post2399695).

-Philip

---

### Post by Offoffoff on 2007-06-28
> **dgrafix said:**
> Hi,

This looks perfect for what i need, i have that same card, but i begin to loose heart when the instructions say "compile....." I have NEVER been able to compile anything in ubuntu. 

Sure enough i tried it and recieved the message unable to compile. In the dir.log im getting this:
... drmP.h:44:26: error: linux/config.h: No such file or directory
LOL I have absolutely no idea what this means :)

Just go to the /usr/src/linux-headers-..../include/linux and write down:
```

sudo ln -s autoconf.h config.h

```
Then go to the driver folder and find out drm_stub.c and delete 51th string.
Then install.sh!!!
Now it is Your turn!

---

### Post by minime666 on 2007-06-29
Hi
I've got a Compaq Armada m700 with a Rage Mobility that I desperately want to get acceleration running on.
I've tried everything in this forum multiple times, and the best I can get from glxinfo is

direct rendering : No
OpenGL renderer string: Mesa GLX  Indirect

What information would you need from me in order to help? (xorg.conf, etc)

---

### Post by Offoffoff on 2007-06-30
2 minime666: The best way - to read through this forum branch...

I made it on my EVO n400c!
But... I had to delete one line in to src-files:
drm_stub.c:51 
ati_pci_gart.c:87
In logs and visually I have no any errors concerning video.
Is it secure to use this self-made driver?

---

### Post by minime666 on 2007-06-30
In which step of audiophyl's tutorial would you delete those lines?
And which logs should I be checking?

Edit:
I just tried the full gammut of audiophyls tut with the modification you described..no go.
BTW...
I think
cd /tmp/working/proto/randerproto
should be "renderproto"
and 
cp *.ko /tmp/build-dir/drm
gives no files...
should this be " *.o "
I've tried with and without these corrections...
Still get "Mesa Indirect"

---

### Post by Offoffoff on 2007-07-03
minimi666: Don't panic. Calm down. Take a deeeeep breath... And re-read all topic... Do it again... Search for bugs in logs (xorg.0.org, messages)... And there will be a enlightenment!

I combined all things and hacks I found here in this branch. I deleted that lines (drm_stub.c:51
ati_pci_gart.c:87) after having problems with install.sh, included in the mach64-20060403-linux.i386.tar.bz2. And after compiling... I got working driver! But I am afraid of what am I doing, because I deleted two lines (one - advised here at forum, another one - I have done by myself).

P.S. By the way, I was playing with System\Preferences\Desktop Effects, then crushed, reloaded, and got the problem: I can see now bad artefact in left-upper corner, looks like a black square with some white lines. It appears for a 1 minute after Gnome loading and then it disappears... Does anyone knows how to heal it?

EDIT: Said artefact disappears when I start console and print some symbols. Also I can see this black-box artefact in GL-screensavers Settings in another place, near left from screensaver.

---

### Post by minime666 on 2007-07-03
I'll try building from the older snapshots as you did...
I was trying to build from the newer stuff as audiophyl suggested.
Everything builds fine, I just can't get it to work....

As to the aritifact, I haven't seen that particular one.  I had one on another system recently (running 7.04 and xfce) where the window borders got messed up.  But only when running WINE apps...

---

### Post by Offoffoff on 2007-07-06
By the way, Beryl, Compiz? Is it possible to install them for usage with mach64-device? Am I insane?

---

### Post by minime666 on 2007-07-06
I've made a bit of progress.. but have some more issues
I had to delete a bunch of references to config.h in a few files, and replace ati_agpgart with one I found in this thread to get mesa to compile.
Then when I restarted, xserver freaked out. (had to switch to vesa in xorg.conf)
I finally reinstalled the xorg ati driver and got it back.

got these errors in Xorg.O.log

[U]
**without** link to libGLcore.so in home/felix/src/snapshots/inst/HEAD/lib/dri[/U]
shows direct rendering enabled
......
(**) Option "dpms"
(**) ATI(0): DPMS enabled
(WW) ATI(0): Option "UseInternalAGPGART" is not used
(II) ATI(0): X context handle = 0x1
(II) ATI(0): [drm] installed DRM signal handler
(II) ATI(0): [DRI] installation complete
(II) ATI(0): [drm] Added 128 16384 byte DMA buffers
(II) ATI(0): [drm] Mapped 128 DMA buffers at 0xb688b000
(II) ATI(0): [drm] Installed interrupt handler, using IRQ 11
(**II) ATI(0): Direct rendering enabled**
(==) RandR enabled
......
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(EE) AIGLX error: dlopen of /home/felix/src/snapshots/inst/HEAD/lib/dri/mach64_dri.so failed (/home/felix/src/snapshots/inst/HEAD/lib/dri/mach64_dri.so: cannot open shared object file: No such file or directory)
(EE) GLX-DRI: reverting to software rendering
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) GLX: Initialized MESA-PROXY GL provider for screen 0


_GLcore compiled for 7.0.0, everything else in xorg compiled for 7.2.0 ex._
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1


_**with** link to libGLcore.so in home/felix/src/snapshots/inst/HEAD/lib/dri_
shows direct rendering enabled

(II) ATI(0): Direct rendering enabled
[I]
but gives a different message farther on[/I]

(EE) AIGLX error: Calling driver entry point failed(EE) GLX-DRI: reverting to software rendering

I'm going to reinstall xorg, by the way, as running glxinfo crashes it, possibly because libGLcore.so is compiled for xorg version 7.0.0  not 7.2.0.  Not sure how **that **happened.

Any ideas?

---

### Post by minime666 on 2007-07-07
Reinstalled xorg
the following is from glxinfo which no longer crashes xorg

[I]Mach64 DRI driver expected DRM version 2.0.x but got version 1.0.0
libGL warning: 3D driver returned no fbconfigs.
libGL error: InitDriver failed
libGL error: reverting to (slow) indirect rendering
display: :0  screen: 0
direct rendering: No[/I]

This error message is still in the xorg log...
*(EE) AIGLX error: Calling driver entry point failed(EE) GLX-DRI: reverting to software rendering*

Next I'm following the instructions on
[http://dri.freedesktop.org/wiki/Building#head-9a666490caaeaf3a8761e332220bb2e088e2e86e](http://dri.freedesktop.org/wiki/Building#head-9a666490caaeaf3a8761e332220bb2e088e2e86e)
and see what happens.
I'm hoping rebuilding DRM might get rid of the version conflict.

---

### Post by minime666 on 2007-07-07
The adventure continues...
After following the instructions in my previous post I get this

(EE) ATI(0): [dri] ATIDRIScreenInit failed because of a version mismatch.
[dri] mach64.o kernel module version is 2.0.0, but version 1.0 or greater is needed.
[dri] Disabling DRI.

*and*

(II) ATI(0): Direct rendering disabled

So I have version 2.0.0, but version 1.0 or greater is needed...hmmm...anyone see the problem with this? 

So when I have version 1.0 it tells me I need version 2.0.0, 
When I have version 2.0.0 it tells me I need greater than version 1.0.
Not quite banging my head on a wall yet, but getting close

---

### Post by minime666 on 2007-07-13
still no luck...has anyone seen this?

---

### Post by RamiK(*_-_*)RamiK on 2007-07-14
I wasn't successful in activating the DRI, but I did manage to compile on a somewhat clean install, heres exactly what i did :

00. sudo apt-get install linux-686 linux-headers-2.6-686 build-essential
*. you might want to reboot
01. "uname -r" to see your kernel version
02. cd /usr/src/linux-headers-"what ever you got with uname -r"/include/linux
03. sudo ln -s autoconf.h config.h
04. cd /usr/src
05. mkdir mach64_dri
06. cd mach64_dri
To date their hasn't been new daily snapshots for months since the devs are lazy and have too much faith in their git server - which I could never clone from :-( 
07. sudo wget [http://dri.freedesktop.org/snapshots/common-20060403-linux.i386.tar.bz2](http://dri.freedesktop.org/snapshots/common-20060403-linux.i386.tar.bz2)
08. sudo wget [http://dri.freedesktop.org/snapshots/mach64-20060403-linux.i386.tar.bz2](http://dri.freedesktop.org/snapshots/mach64-20060403-linux.i386.tar.bz2)
09. sudo tar xjvf common-20060403-linux.i386.tar.bz2
10. sudo tar xjvf mach64-20060403-linux.i386.tar.bz2
11. get Ally_S' ati_pcigart.zip:
[http://ubuntuforums.org/attachment.php?attachmentid=18707&d=1162424703](http://ubuntuforums.org/attachment.php?attachmentid=18707&d=1162424703)
Posted at: [http://ubuntuforums.org/showthread.php?t=7200&page=7](http://ubuntuforums.org/showthread.php?t=7200&page=7)
12. extract ati_pcigart.c to /usr/src/mach64*/drm/linux-core/
Back in xterm:
13. nano  /usr/src/mach64*/drm/linux-core/drm_stub.c
14. comment out line 51: add "//" to tell the compiler to ignore that line.
15. sudo /usr/src/common-20060403-linux.i386/install.sh
16. sudo /usr/src/mach64-20060403-linux.i386/install.sh
17. sudo /etc/init.d/gdm restart

So that what I did, more or less, supposedly at that point things should have worked and this should have been verified with glxinf | grep 'direct', unfortunately for me it didn't :-( 
Were did I go wrong ?

P.S: By my little comment you must have gathered I wasn't successful cloning with git so I used this method, I tried with three different machines, so its either my router which has no firewall, or my ISP which is evil...

P.S.S: Can anyone recommend a dist (live will be perfect) that comes with recent mach64 drivers and x.org already build ? just don't suggest some old dist cause I require a very recent build of alsa...

Edit: obviously lsmod shows mach64 module loaded...

---

### Post by Offoffoff on 2007-07-15
I have installed new kernel 2.6.20.16 and lose direct acceleration. Was trying to reinstall old driver and kill ati driver at all.... Now I have the same problem as Minime... Old driver doen't work...
Here is a part of install log for mach64 driver:
WARNING: /home/worker/TMP/mach64-20060403-linux.i386/drm/linux-core/drm.o - Section mismatch: reference to .exit.text:drm_exit from __ksymtab between '__ksymtab_drm_exit' (at offset 0x58) and '__ksymtab_drm_init'
WARNING: /home/worker/TMP/mach64-20060403-linux.i386/drm/linux-core/drm.o - Section mismatch: reference to .exit.text:drm_cleanup_pci from __ksymtab between '__ksymtab_drm_cleanup_pci' (at offset 0x68) and '__ksymtab_drm_poll'

And dmesg said that cannot find any ati driver....

I am going to try second Audiophil way of installing, but I am frustrated a little bit.

---

### Post by RamiK(*_-_*)RamiK on 2007-07-16
You say the new kernel gives trouble ? I didn't even try the drivers WITHOUT it, so maybe that's why I failed... 

What exactly should I be looking for ? and where (logs) ?

---

### Post by Old Pink on 2007-07-22
Been getting loads of crap trying to install this. Now glxinfo just kills X. :( 

> **Old Pink said:**
> Hi there,

I have a ATI Rage Mobility P/M AGP 2x card in my new laptop, which seemed to install fine (good resolution, etc) using a basic feisty install.

Trying to get a better driver installed to get direct rendering/desktop effects working, but all guides seem to be for Hoary/Breezy, and I know alot has changed since then.

Anyone point me in the right direction for what to do in a  Rage Mobility P/M AGP 2x?

glxinfo:

> **Old Pink said:**
> That hasn't been updated in over a year. 



Even the first stage is outdated and unable to install. 

I'm looking for something simple, and most importantly, Feisty friendly/recent.

> **Old Pink said:**
> Tried it anyway.


The first part worked, the second didn't. 

I just know when I restart X now, it won't start properly. Cheers. :( 

Anyway to fix this, preferably with direct rendering?

> **Old Pink said:**
> After the reboot, tried a recompile to this:again! 

Told you these old guides were ridiculous to even attempt, any chance you could save me?

> **Old Pink said:**
> dri.log says this:

> **Old Pink said:**
> Been working on this for hours now and it's getting **** off annoying, tried god knows how many 16 page threads packed full of solutions, thousands of reboots, hundreds of X restarts, millions of guides, billions of terminal commands and no change, just a system full of crap that doesn't work.

Anyone got an **easy, RECENT, WORKING** guide?!

> **Old Pink said:**
> ... anyone at all?

> **Old Pink said:**
> Tried this, which is frankly the worst written, most misspelt guess-guide ever written. Got half way through and the guide stopped working, 404 error on the packages. Tried to find them myself and continue, used info in the first post to help, installer complained kernel DRM modules wouldn't compile, rebooted.

glxinfo now kills X on the spot. Why? I have no idea.

Tried to reverse the guide, deleting all changes done by it, still, no fix. **HELP, PLEASE.**

> **Old Pink said:**
> **sudo dpkg-reconfigure xserver-xorg** 

... didn't fix it. Now **sudo aptitude reinstall**ing the kernel, image, headers, everything. ageilers, don't you have a two year old guide to get me out of this? :(

---

### Post by RamiK(*_-_*)RamiK on 2007-07-23
Sorry I can't help Old Pink, I haven't had much luck my self...
Isn't a clean install an option ? it took me 45mins to install xubuntu using the alternative cd and a cml box install, and that was on a Intel Pentium 200mhz MMX with 65mb RAM ...

On a brighter note, I was finally able to git clone git://anongit.freedesktop.org/git/mesa/drm,
 so I've compiled it on Gusty (beta), but still no luck with the dri...

Also I noticed the i915 module doesn't compile and that breaks the make process, so I've deleted the i915 source code files, went through all the files, including the make files, making sure to remove any references to i915, compiled and cp *.ko /lib/modules/$KERNEL/kernel/drivers/char/drm.

So except for the i915 part its all the same as it is found in the Readme...
I suppose I could also "dummied" the i915 source files by putting empty files by the same name to replace them so the make won't break, maybe adding some odd includes, or linking the files to one of the headers, but I prefer the "ugly" hack method ;-)...

I'm still unsuccessful at activating the dri, but with the double buffer and the updated xorg i got from gusty, I'm able to get some improvements to the point I'm now able to watch youtube quality .flv's :-)

I haven't tried to compile xorg and I'm not planning to in the near future, the git alone isn't likely to succeed on my loosy connection (for a lack of a better term to describe the results of a selective isp, without resorting to obscenity) let alone the dependencies...

I hope this helps you with your card cause I think I'm waiting until gusty to see if the devs are going too compile the module on their own, before I attempt to do it myself...

---

### Post by dougfractal on 2007-07-27
**[SIZE="4"]Direct Rendering on Mach64 (Feisty)[/SIZE]**
 
This is a script to use as a last resort, when all other guides have failed!
It is meant to be easy but it does use snapshots that are over a year old so may cause problems later. 


This script is OLD.  dri.freedesktop.org have newer snapshots.
new script at
[http://ubuntuforums.org/showpost.php?p=3264969&postcount=6](http://ubuntuforums.org/showpost.php?p=3264969&postcount=6)
Challenge: help me get Rage Mobility P/M with mach64 chip set DRI Working.

[COLOR="Silver"]Copy and paste into terminal
code:
echo -e "You need sudo active for this script\nIf you need to enter the password, do so and run this script again\n"
sudo apt-get install linux-headers-generic build-essential
cd /usr/src/linux-headers-`uname -r`/include/linux
if [ -f 'config.h' ] ; then echo -n ''; else sudo ln -s autoconf.h config.h; fi
cd /usr/src
if ! [ -d 'mach64_dri' ] ; then sudo mkdir mach64_dri; sudo chown $UID mach64_dri; fi
cd mach64_dri
if ! [ -d 'common-20060403-linux.i386' ] ; then  \
   wget [http://dri.freedesktop.org/snapshots/common-20060403-linux.i386.tar.bz2](http://dri.freedesktop.org/snapshots/common-20060403-linux.i386.tar.bz2) ;\
   tar xjvf common-20060403-linux.i386.tar.bz2 ; \
fi
if ! [ -d 'mach64-20060403-linux.i386' ] ; then  \
    wget [http://dri.freedesktop.org/snapshots/mach64-20060403-linux.i386.tar.bz2](http://dri.freedesktop.org/snapshots/mach64-20060403-linux.i386.tar.bz2) ; \
    tar xjvf mach64-20060403-linux.i386.tar.bz2  ; \
    sed -i '87s\__put_page\put_page\'  /usr/src/mach64_dri/mach64-20060403-linux.i386/drm/linux-core/ati_pcigart.c  ; \
    sed -i -e '51a\*/' -e   '51i\/*' /usr/src/mach64_dri/mach64-20060403-linux.i386/drm/linux-core/drm_stub.c ; \
fi
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.`date +%Y%m%d`
sudo sed -i 's\DefaultDepth    24\DefaultDepth    16\'  /etc/X11/xorg.conf
echo -n "sudo echo -e '\nYou must run this script as root.\n';
cd /usr/src/mach64_dri/common-20060403-linux.i386
sudo ./install.sh
cd  /usr/src/mach64_dri/mach64-20060403-linux.i386
sudo ./install.sh
echo -e '\nRestart X-Windows to activate driver\n'
echo -e 'type:    sudo /etc/init.d/gdm restart\n' " > ~/mach64driver.sh
sed -i '1i\#!/bin/bash' ~/mach64driver.sh
chmod 755 ~/mach64driver.sh
cat ~/mach64driver.sh
sudo ~/mach64driver.sh

[/COLOR]

You have a script called **~/mach64driver.sh** that you will need to run every kernel upgrade.


**_check with_**
```
glxinfo | grep direct
glxgears
```


**_FeedBack_**

Could you please list your working card model.
```
lspci | grep -i vga
```

I would really appreciate it if posts were concise, and what troubleshooting steps where made to get it working.


[B][U]
Troubleshooting[/U][/B]

linux-image-686|k7|386 has been obsoleted by: linux-image-generic
```
sudo apt-get install linux-image-generic
```

xorg and other packages have been so messed up you need to start a fresh before running the script
```
sudo dpkg-reconfigure xserver-xorg
sudo apt-get install --reinstall libgl1-mesa-dri
```


```
export LIBGL_DEBUG=verbose
glxinfo
```
It told me that the library /usr/X11R6/lib/modules/dri/mach64_dri.so couldn't be found."
```
cd /usr/X11R6/lib/modules/dri
sudo ln -s /usr/lib/dri/mach64_dri.so mach64_dri.so
```

```
cat /var/log/Xorg.0.log | grep EE
```
If the output has this somewheres...:
> (EE) RADEON(0): Static buffer allocation failed.  Disabling DRI.
(EE) RADEON(0): At least xxxxx kB of video memory needed at this resolution and depth.
Change your bit depth to 16 instead of the default 24...look for this line in your /etc/X11/xorg.conf file under the "Screen" section
```
DefaultDepth    16
```

I wanted 24 bit display not the 16bit you forced on me.
sorry I naively thought your card only had 8meg ram
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.`date +%Y%m%d`
sudo sed -i 's\DefaultDepth    16\DefaultDepth    24\'  /etc/X11/xorg.conf

```



*This howto has been put together off the backs of so many other members.*

---

### Post by dougfractal on 2007-07-27
This post is a place holder that allows me to post working cards to the above script  [http://ubuntuforums.org/showpost.php?p=3090744&postcount=161](http://ubuntuforums.org/showpost.php?p=3090744&postcount=161)

**WORKING**

**Card ID                                                                  ;  PC model                       ;    frame rate                        ; User**

ATI-Technologies Inc Rage Mobility P/M 2x (rev64) ; Compaq Armada E500 ; Smooth and about 136 fps  ; i386DX
ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc);Dell Inspiron 7000 ; 180+ fps;  kjander


---------------------------------------------------------------------------------
**NOT WORKING and UNLIKELY TO EVER WORK**

"(WW) ATI(0): Direct rendering is not supported for ATI chips earlier than the ATI 3D Rage Pro." Xorg.0.log

ATI Technologies Inc 3D Rage II+ 215GTB [Mach64 GTB]
"OLD PINK"'s ati card --  user mismatch

---

### Post by RamiK(*_-_*)RamiK on 2007-07-28
Since  I can't make out what went wrong,

Here's some details on my card:
ATI Technologies Inc 3D Rage II+ 215GTB [Mach64 GTB]

lspci -v:

00:09.0 VGA compatible controller: ATI Technologies Inc 3D Rage II+ 215GTB [Mach64 GTB] (rev 9a) (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc 3D Rage II+ 215GTB [Mach64 GTB]
        Flags: bus master, stepping, medium devsel, latency 64
        Memory at e0000000 (32-bit, non-prefetchable) [size=16M]
        I/O ports at 6100 [size=256]
        Memory at e1000000 (32-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 10000000 [disabled] [size=128K]




And heres my Xorg.0.log :
[http://ubuntuforums.org/attachment.php?attachmentid=39218&stc=1&d=1185630984](http://ubuntuforums.org/attachment.php?attachmentid=39218&stc=1&d=1185630984)

---

### Post by dougfractal on 2007-07-28
> **RamiK(*_-_*)RamiK said:**
> Since  I can't make out what went wrong,

Here's some details on my card:
ATI Technologies Inc 3D Rage II+ 215GTB [Mach64 GTB]

lspci -v:

00:09.0 VGA compatible controller: ATI Technologies Inc 3D Rage II+ 215GTB [Mach64 GTB] (rev 9a) (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc 3D Rage II+ 215GTB [Mach64 GTB]
 
And heres my Xorg.0.log :
[http://ubuntuforums.org/attachment.php?attachmentid=39218&stc=1&d=1185630984](http://ubuntuforums.org/attachment.php?attachmentid=39218&stc=1&d=1185630984)

Sorry to say, from Xorg.0.log
> (WW) ATI(0): Direct rendering is not supported for ATI chips earlier than the ATI 3D Rage Pro.

This is from the log of kjander's ATI Technologies Inc 3D Rage LT Pro AGP-133 before he got direct rendering working
> (WW) ATI(0): DRI static buffer allocation failed -- need at least 7680 kB video memory
(II) ATI(0): Using XFree86 Acceleration Architecture (XAA)
(II) ATI(0): Direct rendering disabled


I think it is very unlikely that you will get this working on this card.
google search for this  kororaa-xgl-livecd-0.2.iso it's a live CD with XGL enabled, It's a year old, but if it work's then there is hope.
Let me know what you find out.

Good Luck

Doug

---

### Post by Old Pink on 2007-07-29
[FONT=monospace]I do not recommend the use of dougfractal's above script.
 It rendered my system unusable, with Xorg broken, the ati driver package broken and no means of restoring it, with the backups all pointing to the destroyed ati driver.
 I had to download xserver-xorg-video-all and xserver-xorg-video-ati onto a memory stick from my other computer, purge them on the laptop in terminal then use sudo dpkg -i to reinstate them.
 Without another computer or a cable connection, and decent knowledge of terminal commands, you will not be able to recover your system, and may be forced to reinstall.
 Just hold out for an appearance in Gutsy, or use Mepis.
[/FONT]

---

### Post by dougfractal on 2007-07-29
**ATI-Technologies Inc Rage Mobility P/M 2x (rev64) SOVLED but not for Old Pink**

> **i386DX said:**
> @Dougfractal

Tested your script in Feisty (kernel 2.6.20-16-generic). It worked without any problems!

**Extra info**

_VGA-card_
ATI-Technologies Inc Rage Mobility P/M 2x (rev64) 
(Compaq Armada E500)

_Glxinfo_
LibGL warning:  3D driver claims to not support visual 0x4b
direct rendering: Yes

_Glxgears_
LibGL warning:  3D driver claims to not support visual 0x4b
Smooth and about 136 fps ;-)

Dear old pink i'm sorry that it doesn't work for you. But i386DX has confirmed that it works for your card with no problems, so there is nothing more that i can do. I guess i386DX had a fresh feisty install, as i believe that problem is in damage to the files from previous attempts or incomplete troubleshooting.

---

### Post by dougfractal on 2007-08-08
**TestX**

testx is a script that tests an alternative xorg.conf file as so to avoid the BSOD.

Usage: testx
a dialog box will open asking for the test xorg.conf file.Which must be in /etc/X11 directory 

before use to allow you to start an X session from xterm.(X may need restarting to take effect:   sudo /etc/init.d/gdm restart)
```
sudo sed -i 's\allowed_users=console\allowed_users=anybody\'  /etc/X11/Xwrapper.config
```


sudo gedit /usr/bin/testx
```

#!/bin/bash
# testx
# tests an xorg.conf file
# main part of script from jpereira 
#  http://ubuntuforums.org/showthread.php?t=518426
# Modded by dougfractal
# Requirements:
#   user must be able to run X terminal. Suggestion: set   allowed_users=anybody
#   on /etc/X11/Xwrapper.config
#if [  `grep -c "^allowed_users=console" /etc/X11/Xwrapper.config` -eq "1" ] ; then 
#    sudo sed -i 's\allowed_users=console\allowed_users=anybody\'  /etc/X11/Xwrapper.config
#     zenity --question  --title="Restart" --text="You were not an allowed user\nThis has been fixed but an X restart required.Then run this script again.\n\nAre you ready to Restart X?"
#     if [ $? -eq "0" ] ; then sudo /etc/init.d/gdm restart ; fi
#fi

# Run this application
#  change this to whatever you wanna run
#CMD="less /var/log/Xorg.1.log"

# Temporary screen number (anything will do)
SCREEN=2
CMD="less /var/log/Xorg.$SCREEN.log" 
#  Choose Xorg file
CONFIG="/etc/X11/$1"
cd  /etc/X11 ; if ! [ -f $CONFIG ] ; then CONFIG=`zenity --title="Select a xorg file" --file-selection` ; fi;  cd $OLDPWD
if [ $CONFIG -eq ''] ; then exit ; fi

# Launch the X server
X -config `basename $CONFIG` -nolisten tcp -terminate -br :$SCREEN vt9 &

# Get xauth for the current display and set new display
cookie="$(xauth -i nextract - $DISPLAY | cut -d ' ' -f 9)"
xauth -i add :$SCREEN . "$cookie"

#Launch xterm with the supplied command
DISPLAY=:$SCREEN.0 xterm -geometry 80x66+300+10 -e $CMD

# Ask user what to do
ERR=`grep "Fatal server error" /var/log/Xorg.$SCREEN.log | wc -l`
if [ $ERR -eq '0' ] ; then 
   ERR=$[`grep "(EE)" /var/log/Xorg.$SCREEN.log | wc -l` - 1]
   if [ $ERR -gt '0' ] ; then 
       zenity --warning --title "Update xorg.conf" --text "There were errors in `basename $CONFIG` \n`grep "(EE)" /var/log/Xorg.$SCREEN.log | tail -n $ERR`"
    fi
    TEXT=`basename $CONFIG`
    zenity --question --title "Update xorg.conf" --text "Would you like to use $TEXT from now on?" 
    if [ $? -eq '0' ] ;then 
             gksu cp /etc/X11/xorg.conf /etc/X11/xorg.conf.`date +%Y%m%d%H%M%S` 
             gksu cp $CONFIG /etc/X11/xorg.conf
#             sudo sed -i 's\allowed_users=anybody\allowed_users=console\'  /etc/X11/Xwrapper.config
             zenity --question  --title="Restart" --text="X restart required.\nAre you ready to Restart X?"
             if [ $? -eq "0" ] ; then sudo /etc/init.d/gdm restart ; fi
   fi
else 
    ERR=$[`grep "(EE)" /var/log/Xorg.$SCREEN.log | wc -l` - 1]
    zenity --error --title "Update xorg.conf" --text "There was a Fatal server error in `basename $CONFIG`\n`grep "(EE)" /var/log/Xorg.$SCREEN.log | tail -n $ERR`"
fi
```
make executable
```
chmod a+x /usr/bin/textx
```

When run and new X is open; `less /var/log/Xorg.1.log` is displayed. 
press "q" to quit and return to gnome.



Security Note:

This will let anybody to start X.
Don't forget to change it back when done with remastering. 
```
sudo sed -i 's\allowed_users=anybody\allowed_users=console\'  /etc/X11/Xwrapper.config
```

Please feedback :)

---

### Post by saltajose on 2007-08-17
Hi People,

I have a ancient  ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c) and following the steps in [http://ubuntuforums.org/showpost.php?p=2399695&postcount=102](http://ubuntuforums.org/showpost.php?p=2399695&postcount=102) of this thread (and follow up corrections and updates) I manage to enable the 3D acceleration on my ubuntu.

But, I get this message when executing glxinfo | grep direct
```
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try running with LIBGL_THROTTLE_REFRESH and LIBL_SYNC_REFRESH unset.
direct rendering: Yes
``` and the first two lines always appear when running a command that uses 3D (like glxgears). Everything seems to work nice, but do you have any idea what these two first lines want to say?

Cheers,

---

### Post by furumaro on 2007-08-20
I managed to enable 3D acceleration following the steps in [http://ubuntuforums.org/showpost.php?p=2399695&postcount=102](http://ubuntuforums.org/showpost.php?p=2399695&postcount=102) of this thread (and follow ups).

Many thanks to audiophyl!!!!

My video-card reports as:
     ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc)
I am on feisty with kernel  2.6.20-16-generic.

To save all the people who have the same kernel the trouble of compiling (including the installation of uncounted dev packages)
i uploaded the "build-dir" to here 
--> [http://www.mediafire.com/?ayyjvlms1d1](http://www.mediafire.com/?ayyjvlms1d1)

so if you are on feisty and have the same kernel, just unpack the archive to /tmp and you can jump in at step 9 of the above mentioned how to ([http://ubuntuforums.org/showpost.php?p=2399695&postcount=102](http://ubuntuforums.org/showpost.php?p=2399695&postcount=102))

Just replace $KERNEL with `uname -r` (including the `) in step 10.

But as already mentioned in step 9: make backups of the relevant files!!!!!

I uploaded the files in the hope that some people can use it to their advantage. If they don´t work for you: sorry. I cannot give support 
in case of any trouble.

---

### Post by nexius on 2007-08-22
Wow!!! Wonderful I can get 3D acceleration  on my old notebook thanks to you all. But now I still have a little question: Does anyone has just tried to use OpenGL transition effects in MythTv for picture slide-show or menu rendering? It seams that there isn't such hardware acceleration.... Anyone had the same experience? 
My notebook is a Dell Insiron 5000 PIII 500 256Mb Ram 12Gb HDD and Ati Rage Mobility P AGP x2 rev. 64 4Mb SGRAM and run MythTV ad a resolution of 840x525 (16/10).

---

### Post by siverium on 2007-08-25
in step 6. I have this problem. I have ubuntu fesity with 7.1 xorg

checking for XORG... configure: error: Package requirements (xorg-server >= 1.3 xproto fontsproto  xineramaproto randrproto renderproto videoproto xf86miscproto xextproto) were not met:

Requested 'xorg-server >= 1.3' but version of xorg-server is 1.2.0

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XORG_CFLAGS
and XORG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

I DONT KNOW why talk about xorg-server 1.2. I have 7.1 xorg.
How I could fix it!??

Thank's

---

### Post by alex.bb on 2007-08-29
Hi there

In my laptop get the following line from lspci:
VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc)

After three days work and testing i have functioning solution for Ubuntu feisty on my laptop with kernel 2.6.20-16-generic:

You needs three things:
1. Install xserver-xorg-video-ati backported from gutsy (compiled with --enable-dri)
2. Install xserver-xfree-core backported from gutsy (depended from xserver-xorg-video-ati)
       both are deb-packages from [http://www.bakarasse.de](http://www.bakarasse.de)

3. Download kernel modules drm.ko and mach64.ko from [http://www.bakarasse.de/linux/ubuntu/download](http://www.bakarasse.de/linux/ubuntu/download). 
    Modules are compiled from drm sources freedesktop.org (step 8 from
    [http://ubuntuforums.org/showpost.php?p=2399695&postcount=102](http://ubuntuforums.org/showpost.php?p=2399695&postcount=102))

To use the packages add the following line to /etc/apt/sources.list
```

deb http://www.bakarasse.de/linux/ubuntu/feisty-backports ./

```

You will also need to add my key to your list of trusted keys:
```

wget http://www.bakarasse.de/PublicKey.gpg -O- | sudo apt-key add - 

```

Install the packages:
```

apt-get update
apt-get upgrade -u

```
Download, unpack and copy the kernel modules to /lib/modules/2.6.20-16-generic/kernel/drivers/char/drm/
```

wget http://www.bakarasse.de/linux/ubuntu/download/mach64-2.6.20-16-generic.tar.gz
tar xzvf mach64-2.6.20-16-generic.tar.gz
(sudo) cp -iv 2.6.20-16-generic/kernel/drivers/char/drm/*.ko /lib/modules/2.6.20-16-generic/kernel/drivers/char/drm/

```

after ```
(sudo) depmod -a
``` restart the X-Server.

On my now fresh installed Feisty on other partition works that at once:
```
alex@max:~$ glxinfo | grep direct
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try running with LIBGL_THROTTLE_REFRESH and LIBL_SYNC_REFRESH unset.
**direct rendering: Yes**

alex@max:/tmp$ cat /var/log/Xorg.0.log | grep -A5 -B5 Direct
(II) ATI(0): [DRI] installation complete
(II) ATI(0): [drm] Added 128 16384 byte DMA buffers
(II) ATI(0): [drm] Mapped 128 DMA buffers at 0xb67dd000
(EE) ATI(0): [drm] Couldn't find IRQ for bus id 1:0:0
(II) ATI(0): [drm] Falling back to irq-free operation
**(II) ATI(0): Direct rendering enabled**
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD




```
glxgears and openGL-screensavers work.

IRQ-Problem remains unsolved, 
set it in BIOS on my laptop is not possible.

Alex

---

### Post by teucom on 2007-10-13
Very nce, Alex.

Installs and works flawless on our Compaq Evo n400c/n410c Notebooks also (Rage Mobility P/M AGP 2x), now using Feisty / 2.6.20-16 kernel.

Dont forget, max Display Depth must be set to 16 bit (xorg.conf) on these models before restarting X.

Thanks a lot
H.Th.

---

### Post by sythem on 2007-10-24
A few questions, I installed your packages *the only thing that's worked so far* but what driver do I need to point to in xorg.conf? currently it's set as ati. 2ndly, if this is right, it seems my direct rendering is not working. Any idea? Also, thank  you sooooooooo much for those packages, every other way of doing this so far failed with compiling issues...

P.S. I have a rage 3d pro desktop card that is supposed to use the mach64 driver so I just kinda assumed anything to do with the mach64 driver woiuld work for my desktop.

---

### Post by dougfractal on 2007-10-24
look at zerwas conf on [http://fractaldimension.org.uk/ubuntu/xorg/xorg.xml](http://fractaldimension.org.uk/ubuntu/xorg/xorg.xml)
he has a Rage Mobility.

Can you use my diagnostic tool as it will tell me lots of things about your setup.

```
mkdir ~/Xinfo
cd ~/Xinfo
wget -O xinfo.sh  http://fractaldimension.org.uk/ubuntu/xinfo.txt
chmod a+x ./xinfo.sh
./xinfo.sh
```

please attach the ***xinfo.tar.gz**

or try my guide on
[http://ubuntuforums.org/showpost.php?p=3264969&postcount=6](http://ubuntuforums.org/showpost.php?p=3264969&postcount=6)

---

### Post by sythem on 2007-10-24
Here is the results of xinfo, my computer is definently more responsive than it was now that I have to packaged drivers installed, but the direct rendering would be quite nice if you could help me get it working. Thank you so much!

---

### Post by dougfractal on 2007-10-25
> 4096 kB of SGRAM (1:1) detected (using 4095 kB).
(WW) ATI(0): Cannot shadow an accelerated frame buffer.

how much video memory have you got?

---

### Post by sythem on 2007-10-25
Acording to dell it has 4mb built in, but I can upgrade it to 8 if I can find a memory stick that fits the slot on the motherboard. Though if I have much more problems with this, I'll probably look into finding a copy of win2000 for this machine and wait till the new ati drivers come out so I can have linux on my lappy.

---

### Post by dougfractal on 2007-10-25
I've been trying to compare zerwas's log and yours

he has 8meg but gets a similar message "(WW) ATI(0): Cannot shadow an accelerated frame buffer."

he is using module version = 6.7.192 where you are on  6.7.194.
the difference i see is here
your log has no reference to drm  or "(II) AIGLX: Loaded and initialized /usr/lib/dri/mach64_dri.so"

I feel your install of the modules was incomplete.

I recomend the guide  [http://ubuntuforums.org/showpost.php?p=3264969&postcount=6](http://ubuntuforums.org/showpost.php?p=3264969&postcount=6)
although this may break X so be prepared.

The new ati drivers that are to come out are unlikely  to help your card, its just too old.


good luck.

---

### Post by sythem on 2007-10-25
I'll try that when I have time and if breaks x I'll just find my copy of win2000, but as for the new drivers, they're meant for my lappy with a x1400, not the old dell.

The link isn't working.

---

### Post by dougfractal on 2007-10-26
sorry I copied the displayed link not the actual link

[http://ubuntuforums.org/showpost.php?p=3264969&postcount=6](http://ubuntuforums.org/showpost.php?p=3264969&postcount=6)

---

### Post by lobiik on 2007-10-29
Hi, I have Compaq Evo N400c with this card

```
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

```

And running  2.6.22-14-generic kernel, but

```
root@evo:~/mach64-20060403-linux.i386# modprobe mach64
WARNING: Error inserting drm (/lib/modules/2.6.22-14-generic/kernel/drivers/char/drm/drm.ko): Invalid module format
WARNING: Error inserting drm '/lib/modules/2.6.22-14-generic/kernel/drivers/char/drm/mach64.ko': Invalid module format

```

And when I tried to compile modules from your howto, then common was compiled OK, but:

```
root@evo:~/mach64-20060403-linux.i386# cat dri.log
make DRM_MODULES=mach64.o modules
make[1]: Entering directory `/root/mach64-20060403-linux.i386/drm/linux-core'
make -C /lib/modules/2.6.22-14-generic/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /root/mach64-20060403-linux.i386/drm/linux-core/drm_auth.o
In file included from /root/mach64-20060403-linux.i386/drm/linux-core/drm_auth.c:36:
/root/mach64-20060403-linux.i386/drm/linux-core/drmP.h:44:26: error: linux/config.h: No such file or directory
make[3]: *** [/root/mach64-20060403-linux.i386/drm/linux-core/drm_auth.o] Error 1
make[2]: *** [_module_/root/mach64-20060403-linux.i386/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/root/mach64-20060403-linux.i386/drm/linux-core'
make: *** [mach64.o] Error 2

```

On one mailing list I found, that config.h is deprecated and removed from kernel sources 2.6.19+ (iirc).

I've also downloaded already precompiled modules, but they're for 2.6.18 kernel, so they will obviously not work. Any ideas?

In my xorg.conf is now being used driver "ati", but glxinfo says indirect mesa

And another thing - I've tried to compile older kernel, but it failed to boot 1st (can't recognize /dev/hda or sda, only UUID), solved that, but with same problems.

---

### Post by mr_meuble on 2007-10-29
Hi there !
Well I installed the dri drivers (i can't remember how but it was painful)

The device :
```
# lspci | grep VGA
00:14.0 VGA compatible controller: ATI Technologies Inc Rage MobilityP/M (rev 64)
```

The strange thing :
```
# lsmod | grep mach64
mach64     44896   0
drm       132824   1   mach64
```

The problem :
```
# glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
```

The complete diagnostic archive :
coming...

---

### Post by dougfractal on 2007-10-30
**lobiik**  please try this link as your drm is from 03/04/2006
use the git version
[http://ubuntuforums.org/showpost.php?p=3264969&postcount=6](http://ubuntuforums.org/showpost.php?p=3264969&postcount=6)

---

### Post by lobiik on 2007-11-02
ok, some more progress with 2.6.22 kernel, 1st part passed ok:

sh ../scripts/create_linux_pci_lists.sh < ../shared-core/drm_pciids.txt
make -C /lib/modules/2.6.22-2-686/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-2-686'
  CC [M]  /src/drm/linux-core/drm_auth.o
...
  LD [M]  /src/drm/linux-core/mach64.o
  Building modules, stage 2.
  MODPOST 2 modules
  CC      /src/drm/linux-core/drm.mod.o
  LD [M]  /src/drm/linux-core/drm.ko
  CC      /src/drm/linux-core/mach64.mod.o
  LD [M]  /src/drm/linux-core/mach64.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-2-686'

Success

But ati drivers:

In file included from atidripriv.h:40,
                 from atistruct.h:40,
                 from atimach64io.h:37,
                 from atibus.c:32:
/usr/include/GL/glxint.h:28:19: error: GL/gl.h: No such file or directory
In file included from atidripriv.h:40,
                 from atistruct.h:40,
                 from atimach64io.h:37,
                 from atibus.c:32:
/usr/include/GL/glxint.h:95: error: expected specifier-qualifier-list before 'GLboolean'
make[1]: *** [atibus.lo] Error 1
make[1]: Leaving directory `/src/xf86-video-ati-6.6.192/src'
make: *** [install-recursive] Error 1

---> [http://ubuntuforums.org/showthread.php?p=1646660](http://ubuntuforums.org/showthread.php?p=1646660)

Soulution:

make banged me with an error because gl.h was missing.

```
sudo apt-get install mesa-common-dev
```

fixed that.

Ok, modprobe mach64 loads module, but when I change settings to "mach64", then X doesn't startx. It says that module mach64 and module dri doesn't exists. With "ati" in xorg.conf it starts ok. Log output:

evo:~# cat /var/log/Xorg.0.log |grep dri
        X.Org XInput driver : 0.7
(II) LoadModule: "dri"
(WW) Warning, couldn't open module dri
(II) UnloadModule: "dri"
(EE) Failed to load module "dri" (module does not exist, 0)
        ABI class: X.Org XInput driver, version 0.7
        ABI class: X.Org XInput driver, version 0.7
        ABI class: X.Org XInput driver, version 0.7
(EE) No drivers available.

evo:~# cat /var/log/Xorg.0.log |grep mach64
(II) LoadModule: "mach64"
(WW) Warning, couldn't open module mach64
(II) UnloadModule: "mach64"
(EE) Failed to load module "mach64" (module does not exist, 0)

evo:~# slocate mach64.so
/usr/lib/directfb-0.9.25/gfxdrivers/libdirectfb_mach64.so

/lib/libdri.so
/usr/X11R6/lib/modules/extensions/libdri.so
/root/common-20060325-linux.i386/core/libdri.so

 so I did:
evo:~# cp /lib/libdri.so /usr/lib/xorg/modules/extensions/
evo:~# cp /usr/lib/directfb-0.9.25/gfxdrivers/libdirectfb_mach64.so /usr/lib/xorg/modules/extensions/

Result: 
evo:~# ldd /usr/lib/xorg/modules/extensions///libdri.so |grep drm
        libdrm.so.2 => /usr/lib/libdrm.so.2 (0xb7f6e000)

But X doesn't start saying undefined symbol: drmSetServerInfo, tried to do [http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg316110.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg316110.html)
but still the same

evo:~# ldd /usr/lib/xorg/modules/extensions/libdri.so
        linux-gate.so.1 =>  (0xffffe000)
        libdrm.so.2 => /usr/lib/libdrm.so.2 (0xb7f31000)
        libm.so.6 => /lib/i686/cmov/libm.so.6 (0xb7f0c000)
        libc.so.6 => /lib/i686/cmov/libc.so.6 (0xb7dc4000)
        /lib/ld-linux.so.2 (0x80000000)

And this is where I am currently stuck. Now it doesn't start even with ati driver. Will try to install again latest ati drivers (used in that scrip) and will see.

And if you will find anything usefull, feel free to add into howto's

---

### Post by dougfractal on 2007-11-02
xf86-video-ati-6.6.192  is last years ati driver (june 2006)   download the 6.7.192 or 6.7.195 from web site 

hope that works for you.

---

### Post by lobiik on 2007-11-03
Ok, started from scratch, done that script (manually, error appeared on line 26 - last line) and got it working :)

---

### Post by oasick on 2007-11-04
IMPORTANT: The xf86-video-ati_6.7.195 and mach64 modules compiled are ONLY for Ubuntu Gutsy 7.10 and kernel 2.6.22-14-generic (maybe works on 386 kernel too but i couldn't tried it)

This modules are compiled with the [dougfractal's post]("http://ubuntuforums.org/showpost.php?p=3264969&postcount=6") (thank's for your great work ;) )

1. Download this files:

[xf86-video-ati_6.7.196_gutsy.deb]("http://www.box.net/shared/2qkglnibcm")
[mach64 Kernel 2.6.22-14-generic.tar.gz]("http://www.box.net/shared/o0ay4u2ju0")

2. Uninstall xserver-xorg-video-ati

sudo apt-get uninstall --purge xserver-xorg-video-ati

3. install xf86-video-ati_6.7.196_gutsy.deb with gdeb or:

sudo dpkg -i /where/is/xf86-video-ati_6.7.196_gutsy.deb

4. uncompress mach64 Kernel 2.6.22-14-generic.tar.gz and enter the directory with console and:

sudo cp *.ko /lib/modules/`uname -r`/kernel/drivers/char/drm/

sudo depmod -a
sudo modprobe mach64

restart X and you have 3D acceleration :)

I hope that this solution works for you ;)


UPDATED xf86-video-ati 6.7.195 to xf86-video-ati 6.7.196

---

### Post by Offoffoff on 2007-11-12
Last solution works for me! Great thanks! For my friend's laptop Compaq Evo n400.
But why I can see Slackware Package?

---

### Post by oasick on 2007-11-13
Don't worry Offoffoff . Slackware package appears because i created the deb file with alien and by default put this. But the compilation is for ubuntu gutsy :)

---

### Post by oasick on 2007-11-13
This is ONLY for Ubuntu Gutsy. 
I compiled the new xf86-video-ati 6.7.196 [This is the announce and the fixes/new features]("http://lists.freedesktop.org/archives/xorg/2007-November/030120.html")

To install it you must uninstall xserver-xorg-video-ati first :

sudo apt-get uninstall --purge xserver-xorg-video-ati

Or uninstall the xf86-video-ati_6.7.195-2 if you enable the 3D acceleration with [this post]("http://ubuntuforums.org/showpost.php?p=3703906&postcount=188") 
If you want to enable the 3D acceleration you can do the same of [this post]("http://ubuntuforums.org/showpost.php?p=3703906&postcount=188") but you can use the latest xf86-video-ati 6.7.196

You can download the deb file from here:
[URL="http://www.box.net/shared/2qkglnibcm"]
xf86-video-ati_6.7.196_gutsy.deb[/URL]

---

### Post by alex.bb on 2007-11-13
Other deb-Package for Ubuntu Gutsy.
(version 6.7.195, simply built from Gutsy-Sources with option --enable-dri)

To use the package add the following line to /etc/apt/sources.list
```

deb http://www.bakarasse.de/linux/ubuntu/gutsy ./

```
and install it:
```

apt-get update
apt-get upgrade -u

```

Get kernel modules (drm and mach64) for kernel 2.6.22-14-generic:
```

wget http://www.bakarasse.de/linux/ubuntu/download/mach64-2.6.22-14-generic.tar.gz

```
copy the kernel modules to /lib/modules/2.6.22-14-generic/kernel/drivers/char/drm/ and set Display Depth to 16 bit (xorg.conf).
after depmod -a restart the X-Server.

---

### Post by nail.tw on 2007-11-25
> **oasick said:**
> 
...
This modules are compiled with the [dougfractal's post]("http://ubuntuforums.org/showpost.php?p=3264969&postcount=6") (thank's for your great work ;) )


First of all, I want to thank dougfractal and oasick. Very useful articles and sweet deb package for me such newbie to make DRI enabled in just few minutes.

Here's my problems: Its GUI STILL runs so slow that I can't use it, not like it works in Windows XP.

Yes I made DRI working now, glxinfo says "direct rendering: Yes" now. But it didn't make more fps. After I read someone's 3d fps datasheet here([http://fractaldimension.org.uk/ubuntu/xorg/xorg.xml]("http://fractaldimension.org.uk/ubuntu/xorg/xorg.xml")), his fps(in 5 seconds) is just like mine.. poor 181 fps(glxgears fps)

> ATI Technologies Inc Rage Mobility P/M AGP 2x
res:1024x768	
depths:24	
glxgears fps:181

So it's the limit of this old laptop running ubuntu? ([Travelmate 600ter]("http://www.acersupport.com/notebook/html/tm600_specs.html")) 
I just want to make use of this old laptop, like browse web and e-mail. I thought DRI is critical to normal 2D rendering and it seems not since DRI is enabled now. Any suggestion is welcome, or I think I'll make it XP again ;).

---

### Post by dougfractal on 2007-11-25
Hi nail.tw
fps:181 is fairly average for your card, the best i have seen is 257fps.
But your GUI shouldn't be slow. how was it  with the live CD?
You could reduce your defaultdepth 16 in the /etc/X11/xorg.conf
It maybe that AGLX  enabled may be an issue,
try adding this  (always backup conf files first) 
> Section "Extensions"
	Option		"Composite"	"0"
EndSection

If the problem is more about  slow application response, there might be a hostname lookup issue.  some mods to the /etc/hosts can fix this. Let us know how it goes.   

Have you looked at gOS. its another ubuntu derivertive and  uses Enlightenment E17 desktop. 

Doug

---

### Post by whardier on 2007-11-28
The modules provided by both alex.bb and oasick load fine, however I get the following when I start X (and a snippit from xorg.conf is included.

I'm convinced I need to recompile the kernel anyways, I'm a little intimidated because I need to recompile it for a transmeta host, including all the restricted drivers... sigh.. 

Anyhoot, any advice would be wonderful!  I don't understand why the driver still wants to load up radeon.ko

-------

FATAL: Error inserting radeon (/lib/modules/2.6.22-14-generic/kernel/drivers/char/drm/radeon.ko): Unknown symbol in module, or unknown parameter (see dmesg)
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.

-----

Section "Device"
        Identifier      "ATI Technologies Inc Radeon Mobility M6 LY"
        Driver          "ati"
        BusID           "PCI:0:20:0"
EndSection

----

---

### Post by dougfractal on 2007-11-29
"ATI Technologies Inc Radeon Mobility M6 LY"    I'm faily sure this** isn't** a  mach64 card. 
try [http://ubuntuforums.org/showthread.php?p=3818042](http://ubuntuforums.org/showthread.php?p=3818042)

also look in the 
less /var/log/Xorg.0.log
an look to see which module it loads.  search this thread for someones xinfo.tar.gz  and compare there log files


You could try to recomple the modules, (not the kernel)   change this part  and cp the radeon mods
see. [http://ubuntuforums.org/showpost.php?p=3264969&postcount=6](http://ubuntuforums.org/showpost.php?p=3264969&postcount=6)
make DRM_MODULES="radeon"

---

### Post by minime666 on 2007-12-02
I've tried oasick's deb file from above, carefully following his directions.
This is on a Compaq Armada M700, running Xubuntu 7.10.
I get the following results:

[I]lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

lsmod | grep mach64
mach64                 51968  1 
drm                   147224  2 mach64

glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

[/I]

This is a fresh(ish) install, I haven't tried anything at all funky with it.
It would be nice to not have to reboot into win 2K to play Unreal Tournament (yes I know how old it is...we have fun with it still).  I get decent frame rates in w2K, obviously not playable in linux without acceleration.

Any ideas?
I'm not sure how to "try setting LIBGL_DEBUG=verbose"

---

### Post by oasick on 2007-12-04
Hi minime666
I can't know what's happen with your laptop... Can you get more info about your problem and post here?

Sometimes this problem is because don't have installed libgl1-mesa-dri
If you don't have installed this library you can try install it

If you haven't 3D acceleration yet, you can try the [alex.bb]("http://ubuntuforums.org/showpost.php?p=3765722&postcount=192") metod... maybe in this way works for you.

---

### Post by minime666 on 2007-12-04
Thank you Oasick!!!
Your method combined with installing the *_libgl1-mesa-dri_* library
worked quite well.
Anyone noticing the same symptoms I listed in my earlier post would do well to check to see that this library is installed.

Success at last!!
Now I just need to get UnrealEd working, and I can dispose of w2K 
FOREVER!!
BAH HAA HAA!! (maniacal laughter)

I'm gonna go old school now and go play starcraft broodwar....

---

### Post by Scottydogg on 2007-12-15
Thanks  for all the work on this.
Unfortunately, I still can't get 3d acceleration working with my ATI Technologies Inc Rage Mobility P/M AGP 2x.
I installed oasic's deb package, and have the lib1-mesa-dri library,  and yet I get 
```
 glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

```

Um, what does this mean I should do...

---

### Post by oasick on 2007-12-18
Hi Scottydogg.

What can you see if you white in console:

modprobe mach64

?

It's strange your error... maybe you haven't complete your configuration...

---

### Post by Paingiver on 2007-12-28
First of all, i want to thank to all people involved in this matter. I have a Compaq Armada M700 laptop which is in fact my girlfriend's. I have formatted the XP installed on it and i am trying encourage her to use Xubuntu.

For feedback: Oasick`s method works for me after a fresh insall and updates on Xubuntu Gutsy Gibbon. Now everything is so clear like mirror. Thanks again to all community.

---

### Post by Glus on 2008-01-15
Hi Forum Users,

I've tried install fresh gOS 2.0 system on my Compaq Armada M700. It's very old notebook and I not expect fireworks (Pentium III 600MHz and 256RAM ATI Rage Mobility). I want only prepare station to browse the internet, it's all. I'm using Windows XP before, but I think that Linux OS will be work more stable and without any problems.
The gOS 2.0 system is based on Ubuntu Gutsy.

I have a silly problem with my lcd display.I see on my screen all icons and windows but I have a horizontal blank lane on 1/3 top my screen. If I move any object (like window or icon) from bottom then on near this band part of window is cutted (hidden) and displayed behind this lane on the top of screen. It's look like sometimes any person using two monitors and  drag window from one to second display behind monitor border (case).
My problem is because all elements of the screen is shifted to bottom and part of them is invisible and I have a border white lane inside screen about 2cm.

When I try install system again and select 1024x768x16  (not default 1024x768x24) all works fine on installation process  but after reboot problem was again.  

Technical details:
lspci | grep VGA
 01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

I try edit grub and add line like vga=785 --  vga=0x317 but nothing.
My be I doing something wrong. I'm new linux user (lame).

Any idea ?
Thank you in advanced.

---

### Post by JoshuaRL on 2008-01-15
Try to reconfigure xserver.  To do this, first backup xorg.conf in /etc/X11, and then boot into recovery console and try:

```

dpkg-reconfigure xserver-xorg

```

That seemed to work on the Latitude CPx that runs the same graphics card.  Just go through the options and pick most of the default options.  Pick the right resolution and finish.  From what I understand, the problems stems from that the application that detects and configures video hardware in "dpkg" works better than the one included in the install.  Hopefully they'll resolve this in Hardy.

Also you might need to update the "usplash" settings.  Try:

```

sudo gedit /etc/usplash.conf

```

After you set the "xres" and "yres" settings appropriately, update the theme with:

```

sudo update-usplash-theme usplash-theme-ubuntu

```

That will fix the initial resolution setting.  If you have noticed a really long time where the computer sits with a blank screen on bootup, this will fix that too.  Hope that helps.

---

### Post by Jay Jay on 2008-02-06
I could really do with some help sorting this out, especially as I have three machines that use this infernal chipset! :)

The previous scripts repeatedly broke my OS and [the most recent one]("http://ubuntuforums.org/showpost.php?p=3274249&postcount=172") ends in error messages when I run it.

> "You needs three things:
- backported xserver-xorg-video-ati 6.6.193 from gutsy compiled with --enable-dri
- backported xserver-xfree-core 1.3 from gutsy (depended from xserver-xorg-video-ati)" 

Can anyone offer some guidance or help to show me where I'm going wrong? I'd really appreciate it, thanks...

---

### Post by Jay Jay on 2008-02-07
Ok, not one to give up easily, I tried again and this time  reached here:

```
 cp -iv 2.6.20-16-generic/kernel/drivers/char/drm/*.ko /lib/modules/2.6.20-16-generic/kernel/drivers/char/drm/
```

Terminal responds with - 

> cp: overwrite `/lib/modules/2.6.20-16-generic/kernel/drivers/char/drm/drm.ko', overriding mode 0644?

I press 'Y' and the process halts:

> cp: cannot create regular file `/lib/modules/2.6.20-16-generic/kernel/drivers/char/drm/mach64.ko': Permission denied

Does anyone know what's going wrong here? After all, It's worked for others from what I could see.

---

### Post by Jay Jay on 2008-02-07
Alright, I cracked it with a little trial and error and initiative...

```
cp -iv 2.6.20-16-generic/kernel/drivers/char/drm/*.ko /lib/modules/2.6.20-16-generic/kernel/drivers/char/drm/
```

should be:

```
sudo cp -iv 2.6.20-16-generic/kernel/drivers/char/drm/*.ko /lib/modules/2.6.20-16-generic/kernel/drivers/char/drm/
```

Plus:

> depmod -a should be: > sudo depmod -a

Now comes the moment of truth...

```
glxinfo | grep direct
direct rendering: Yes
```

Hurrah, at last, I'm in business! Persistence pays I suppose. Thanks to Alex for his solution, but perhaps a revision is in order to include the necessary sudo's as other newbies in the same boat as me might not realise that the script needs a few minor edits...

---

### Post by dingdizzle on 2008-02-19
Hi guys,

I'm still having Problems with the 3D acceleration on my system. I'm using an older computer, and I've tried to get a stable system with 3D acceleration on Kubuntu 6.06.1, Kubuntu 7.10, Xubuntu 7.10, and now I'm back to Xubuntu 6.06.1.

The 7.10 Versions will easily freeze all the time after a while when I use them, 3D accleration successfully installed (Page 19 of this thread), or not.

Kubuntu 6.06.1 runs good and stable, a little slow though, and Xubuntu 6.06.1 works really good. The problem with either one of them though, once I install the 3D acceleration the computer will freeze regularly, which really is pretty annoying.

I therefore follow the instructions on Page 1 of this thread, and I have to set the default depth to 16 to make the 3D acceleration work.

```
glxinfo | grep direct
direct rendering: Yes
```

My graphics card is an "ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)".

I'm not very good at computers and Ubuntu, I get things to work with detailed instructions from the wiki's and forums, but other that that I'm just screwed.
Does somebody have an idea how I can solve this problem and get the system running stable with 3D? I ran Kubuntu Dapper without 3D for more than a year now without 3D acceleration, and it runs so much smoother with 3D acc., I would love to keep it.

Regards,

dingdizzle

---

### Post by dingdizzle on 2008-02-20
Maybe these can help to find out what's wrong, would be really nice if someone had a look:

[Xorg.0.log]("http://ubuntuusers.de/paste/42426/")

[xorg.conf]("http://ubuntuusers.de/paste/42428/")

I really appreciate any help with this. Thanks a lot.

dingdizzle

---

### Post by Paingiver on 2008-03-01
First what is your system configuration?The problem occurs only you use 3d accerelator? Do you have a cooling problem? Is Ubuntu slow without 3D? Or is it slow anyway. If you insist using a Desktop Environment i suggest go XFCE. Or you can use only Window Manager which will be faster(Fluxbox,Openbox etc..) 

Also you can make a custom Ubuntu or Debian install to fasten your computer.

And of course ArchLinux comes to mind when you think about speed. 

Its not so hard to set it up.Nowadays i installed an ArchLinux to an old machine. I am trying to get work "mach64" module. I read the forums, they have done it before. And if i am succesful i will help you also.

---

### Post by wvrn on 2008-03-09
i did the things described in this forum, including
  * backup my /usr/lib/xorg/modules (using xorg 7.1 the ati_drv.so and atimisc_drv.so compiled by the following packages does not work)
  * installing common-20060403-linux.i386 as described
  * install the patch "ati_pcigart.zip" as described
  * installing mach64-20060403-linux.i386  as described
  * trying several xorg-confs.

after that, i still got direct rendering=no

from [http://www.bsdforen.de/archive/index.php/t-15135.html](http://www.bsdforen.de/archive/index.php/t-15135.html) i got the hint for using atigetsysteminfo.sh - it summarizes some "cat proc" .. 
and reported that the /etc/driconf is missing. i simply installed the following driconf and got my "direct rendering=yes" and much faster glxgears-visuals.
:)
```

<driconf>

<device screen="0" driver="radeon">
  <application name="all">
    <option name="vblank_mode" value="0" />
    <option name="hyperz" value="true" />
  </application>
</device>

</driconf>

```

(now i'm working to get a usable googleearth... it still is as slow as before...)

---

### Post by Stroganoff on 2008-03-16
> **alex.bb said:**
> Other deb-Package for Ubuntu Gutsy.
(version 6.7.195, simply built from Gutsy-Sources with option --enable-dri)

To use the package add the following line to /etc/apt/sources.list
```

deb http://www.bakarasse.de/linux/ubuntu/gutsy ./

```
and install it:
```

apt-get update
apt-get upgrade -u

```

Get kernel modules (drm and mach64) for kernel 2.6.22-14-generic:
```

wget http://www.bakarasse.de/linux/ubuntu/download/mach64-2.6.22-14-generic.tar.gz

```
copy the kernel modules to /lib/modules/2.6.22-14-generic/kernel/drivers/char/drm/ and set Display Depth to 16 bit (xorg.conf).
after depmod -a restart the X-Server.

Is there a chance you could provide a .deb file and instructions for Hardy? Would be very much appreciated.

---

### Post by alex.bb on 2008-04-01
> **Stroganoff said:**
> Is there a chance you could provide a .deb file and instructions for Hardy? Would be very much appreciated.

As soon as Hardy is released, i will have the possibility to do the .deb packages. Until then please be patient. :popcorn:

---

### Post by Stroganoff on 2008-04-30
I'm trying to be patient. \\:D/

---

### Post by Arch2 on 2008-05-02
How I got DRI to work on my Dell latitude L400 with ubuntu 8.04

My computer has omly 4M of video memory so I had to Modify  **Section "Screen"** in xorg.conf to look like this...

sudo gedit /etc/X11/xorg.conf

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x786"
	EndSubSection
EndSection

If you want to go back to high resolution change DefaultDepth to 24 and reeboot; but DRI won't work.

Copy and paste these commands in Terminal (use Shift-Ctrl-v to paste in Terminal)

sudo apt-get install linux-headers-generic build-essential
sudo apt-get install autoconf-archive xorg-dev  git-core libdrm-dev mesa-common-dev
mkdir src
cd src
git clone git://anongit.freedesktop.org/git/mesa/drm
cd drm/linux-core
make DRM_MODULES="mach64" 
sudo cp *.ko /lib/modules/`uname -r`/kernel/drivers/char/drm/
sudo depmod -a

reboot your computer 


glxinfo | grep direct
direct rendering: Yes

glxgears
1103 frames in 5.0 seconds = 220.538 FPS

Caution: running DRI applications causes the CPU to heat-up pretty quick.
I installed sensors-applet so I can keep an eye on my CPU temp. 

This didn't improve the graphics in the SuperTux video game but it did improve the screensavers.
Next task is to see if I can get Compiz to work.

---

### Post by alex.bb on 2008-05-07
*Sorry, Stroganoff... All work and no play makes Jack...*#-o

It is not necessary to build an ati-driver for Hardy. I suspect, the driver is already compiled with --enable-dri...
You only need to build the kernel-modules:

```
sudo apt-get install git-core make gcc
git clone git://anongit.freedesktop.org/git/mesa/drm

cd drm/linux-core
```

For running kernel:
```
sudo apt-get install linux-headers-`uname -r`
make mach64.o
sudo cp *.ko /lib/modules/`uname -r`/kernel/drivers/char/drm/

```

For other kernel (for example 2.6.24-16-rt):
```

sudo apt-get install linux-headers-2.6.24-16-rt
make clean
export LINUXDIR=/usr/src/linux-headers-2.6.24-16-rt/
make mach64.o
sudo cp *.ko /lib/modules/2.6.24-16-rt/kernel/drivers/char/drm/

```

Here a few Kernel-Modules for download: [http://www.bakarasse.de/downloads.html]("http://www.bakarasse.de/downloads.html")

Here Hardy's xorg.conf with my **changes**:
```


Section "Device"
        Identifier      "Configured Video Device"
        **Option          "ForcePCIMode"  "True"**
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        [B]DefaultDepth    16
        SubSection "Display"
            Depth       16
            Modes           "1024x768"
        EndSubSection[/B]
EndSection


```

---

### Post by Tomguta on 2008-05-08
> **Arch2 said:**
> How I got DRI to work on my Dell latitude L400 with ubuntu 8.04

My computer has omly 4M of video memory so I had to Modify  **Section "Screen"** in xorg.conf to look like this...


I am forever-linux-noob, so I would like to ask, if this tutorial works for Armada E500 graphic card (**Ati Technologies Inc Rage Mobility P/M AGP 2x (rev 64)**, too. You write that you have only 4MB of video memory, so I suppose you have some other version of the graphic card.

Sorry for stupid newbie question, but I am not sure I would be able to restore faulty installation to previous working state.

Anyway, is there some difference between posts #215 and #216. Which one shall I use please?

---

### Post by Arch2 on 2008-05-09
I would recommend backing up you system just in case somthing disasterous happens. 

I don't know why I have less vedeo RAM I guess it just older.
My how-to should work for you, I don't think you need to change the resolution to 800x600 though.

I general terms what you want to do is change your video color depth to 16 (and in my case reduce the resolution).
Then add a file called mach64.ko to the /lib/modules/2.6.24-16-generic/kernel/drivers/char/drm/ directory. And update the drm.ko file in the same directory. Then depmod -a and reboot. 

You may want to back up xorg.conf and drm.ko before starting, just in case you want to undo that part.
I'm not sure what depmod does or how to undo it or if its possible.

The how-to's above compile the mach64.ko and drm.ko from the source code. I noticed alex.bb has a link to files already compiled. So you can just unzip and copy the files to the right directory, if you want to do it that way.

NOTE: The kernel version (i.e. 2.6.24-16-generic) changes quite often (from updates), you can verify it with uname-r in Terminal. You will need to change the directory name accordingly, or you can just use `uname-r` as seen in the how-to's. It automatically figures the version for you.

---

### Post by stansford on 2008-05-11
Arch2 - huge thanks and respect to you for your post. This got my rage mobility gaphics with direct rendering going a treat. Fantastic! - although I did modify it a bit re the xorg.conf file. I didn't bother with the sub section with different resolutions, just stuck in the line with 16 bit and left everything else the same. Hardy came up with 1024x768 no problem.

cheers!

---

### Post by ZakMcRofl on 2008-05-14
I'm having problems getting this to work.

I got the card described in [http://ubuntuforums.org/showthread.php?p=4959307](http://ubuntuforums.org/showthread.php?p=4959307) (ATI 3D Rage LT Pro AGP-133).

Should the above instructions by alex.bb apply? 

Here's what i did:
1) compiled the .ko modules and copied them to the folder. 
2) sudo depmod -a
3) Added the line "DefaultDepth 16" below "Configured Video Device" in /etc/X11/xorg.conf
4) Reboot

Ubuntu came up with an error and in low graphics mode, asking me to configure my graphics card.

Am I doing something wrong? I'm new to this but I see that Ubuntu has a lot of potential on this old machine. Sometimes I wonder why those legacy drivers aren't included out of the box.
I don't need 3D acceleration, just a proper 2D acceleration to play videos (youtube, XviD,...).

Cheers in advance.

Update 1: I don't if it helps but module mach64 wasn't loaded after reboot. I now added it to /etc/modules but it still comes up in low graphics mode.

Some debug output that might help:
```

benutzer@linuxkiste:~$ grep -n DRI /var/log/Xorg.0.log
220:(II) Loading extension XFree86-DRI
1692:(II) AIGLX: Screen 0 is not DRI capable

```

```

benutzer@linuxkiste:~$ glxinfo | grep render
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

```

Update 2:
I tried moving the DefaultDepth entry to the Screen section but that didn't work either.
Now I removed it and the system boots up as normal - without any 2D or 3D acceleration.

Update 3:
It works! Although only in 800x600 but here I go:
```

benutzer@linuxkiste:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Mach64 [Rage Pro] 20051019 AGP 2x x86/MMX/SSE

```
The key was to run "sudo displayconfig-gtk" and to select "Ati Mach64 Utah" as graphics card. Plus the low resolution probably. Will optimize some more, thanks for the great tutorial and other helpful commands!

Update 4: I have a feeling that Hardy doesn't like it if one uses displayconfig-gtk. I can't get it to run on 16bit and with 32bit all that works is 640x480. I guess I'm going back to Windows XP on that machine, without 2D acceleration using that system would be a pain.

---

### Post by alex.bb on 2008-05-15
output from... ```
cat /var/log/Xorg.0.log | grep EE
```
...?

---

### Post by geodescent on 2008-05-20
Hello. Many of these steps seem out of date. Has anybody tried this with Ubuntu 8.04 Hardy? If so, can you post the steps you took? (for instance, I'm not able to compile the latest kernel headers because the version supplied here cannot be found)

---

### Post by SubGothius on 2008-05-30
> **alex.bb said:**
> what does ```
cat /var/log/Xorg.0.log | grep EE
```?Heh, same thing as:```
grep EE /var/log/Xorg.0.log
```...only longer. :lol:

---

### Post by alex.bb on 2008-06-05
Hello.
With the debs gets a lot easier.

Kernel modules (deb-Packages) for Ubuntu Hardy.
(-generic and -rt kernel)

To install add the following line to /etc/apt/sources.list:
*deb [http://www.bakarasse.de/linux/ubuntu/hardy](http://www.bakarasse.de/linux/ubuntu/hardy) /*

and run:
**apt-get update**

Install for generic kernel:[B]
apt-get install linux-ati-mach64-drm-modules-generic[/B]
...for Real time kernel:[B] 
apt-get install linux-ati-mach64-drm-modules-rt[/B]

Dont forget, max Display Depth must be set in xorg.conf to 16 bit.

Best regards,
Alex

---

### Post by Chenko on 2008-06-06
Hi, I'd tried everything on Xubuntu Hardy, compiling modules (git method), installing packages from repos, using an script for install modules automatically, playing with xorg.conf with many options, and nothing worked.

I obtain these from 
```

glxinfo | grep render

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa DRI Mach64 [Rage Pro] 20051019 x86/MMX/SSE
```


and this from 

```
lsmod | grep mach64
mach64                 44800  2 
drm                   154792  3 mach64
```

Mi Laptop is a Compaq Armada E500 with a Ati Rage Mobility 8MB

Please Help!!

this is my xorg.conf

EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
	Option		"XkbVariant"	"alt-intl"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Rage Mobility P/M (AGP)"
	Option          "ForcePCIMode"  "True"

EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        DefaultDepth    16
        SubSection "Display"
            Depth       16
            Modes           "1024x768"
        EndSubSection

EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
        Mode 0666
EndSection


Best Regads,

Chenko

---

### Post by alex.bb on 2008-06-06
Hi Chenko,

```
cat /var/log/Xorg.0.log | grep EE
```
**?????**

---

### Post by Chenko on 2008-06-07
Thanks for your response alex.bb, here is the output:

$ cat /var/log/Xorg.0.log | grep EE
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"

Best Regards,

Chenko

---

### Post by alex.bb on 2008-06-11
> **Chenko said:**
> Thanks for your response alex.bb, here is the output:

$ cat /var/log/Xorg.0.log | grep EE
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"

Best Regards,

Chenko

Hi Chenko,

You need to reinstall the modules.

Not forget:
depmod -a
and restart X

---

### Post by sersoft on 2008-06-14
Hey this is probably a stupid question, but will this patch allow the 3D desktop(Beryl/Compiz) to work(even slowly)?:confused:

I would like to have it just to show how awesome linux is on an old laptop(Armada m700)

my card is an ATi Rage Mobility P/M1(it says "Ati Rage P" on the chip itself) 8mb AGP. and is running on a 440bx chhipset with a coppermine PentiumIII and 512ram.:)

---

### Post by psyke83 on 2008-06-15
> **sersoft said:**
> Hey this is probably a stupid question, but will this patch allow the 3D desktop(Beryl/Compiz) to work(even slowly)?:confused:

I would like to have it just to show how awesome linux is on an old laptop(Armada m700)

my card is an ATi Rage Mobility P/M1(it says "Ati Rage P" on the chip itself) 8mb AGP. and is running on a 440bx chhipset with a coppermine PentiumIII and 512ram.:)

No, it's not possible at all. Your graphics card does not support non-power-of-two textures which is necessary for compiz to work. I tried to make it work on my Mobility M4 some time ago and found out about the hardware requirements.

Sorry :(.

---

### Post by psyke83 on 2008-06-15
Is this guide necessary any more? Those DRI snapshots have not been updated in over two years (and will probably never get updated again) - Ubuntu's driver versions should be more recent. If it's necessary to get more recent code, then you should be using GIT, not two-year-old snapshots.

---

### Post by alex.bb on 2008-06-18
> **psyke83 said:**
> Is this guide necessary any more? Those DRI snapshots have not been updated in over two years (and will probably never get updated again) - Ubuntu's driver versions should be more recent. If it's necessary to get more recent code, then you should be using GIT, not two-year-old snapshots.

With my method only the mach64 kernel-modules are created:[ Post 216]("http://ubuntuforums.org/showpost.php?p=4906456&postcount=216")
Is this GIT:```

git clone git://anongit.freedesktop.org/git/mesa/drm

```
wrong ?

Could you show me a newer source for?

---

### Post by NoOp on 2008-08-01
Thanks! I finally managed to get DRI running on my old IBM Thinkpad A21M (8.04.1 - 2.6.24-19-generic - ATI Rage Mobility P/M AGP 2x). Any chance that you can provide a .deb for a -386 kernel? I normally boot into the -386 in order to use the built in Agere Systems WinModem.

---

### Post by alex.bb on 2008-08-03
> **NoOp said:**
> Any chance that you can provide a .deb for a -386 kernel?
Yes. Are ready. For Hardy.

To install add the following line to /etc/apt/sources.list
```
deb http://www.bakarasse.de/linux/ubuntu/hardy /
```
and run
```

apt-get update
apt-get install linux-ati-mach64-drm-modules-386

```

---

### Post by halitech on 2008-08-05
trying the deb file now and hoping it works on my old compaq armada with the ATI Rage Mobility P/M AGP 2x

edit: well, the good news is that yes the driver worked for the video but the bad news is it knocked out my sound.

edit2: booted back into the 2.6.24-19-generic kernel and everything is working properly.

---

### Post by Skimmer on 2008-08-10
A hearty thanks to Arch2 in post#215!
I have a Compaq P3 600mhz with an 8mb ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64) video card running Xubuntu-Hardy, and thanks to your guide I was able to get direct rendering going! Maybe because of the doubled memory (8mb instead of 4mb, Arch2) I am also able to use 24 bit depth as well (actually better!).

Some notes on glxgears performance:
Average of 293 fps over many counts for 16-bit depth
Average of 179 fps over many counts for 24-bit depth
I don't game much, but Neverball is working well with all lowest settings except shadows. I realize that my old setup can only do so much!!

Special Note:
Also had unrecoverable stops in X while at 16-bit depth using Firefox with enabled compositing. Seemed to happen while scrolling. Not sure where the fault is, but at 24-bit depth there have been no problems with any programs yet. Compositing is not on however, but I shall try it out.

Thanks to all the contributors here, without whom I would be severely disadvantaged--
--SK

---

### Post by JonMD on 2008-08-12
I am trying to compile mach64.o against a 2.6.26.2 kernel (from kernel.org) that I have compiled using the "Master Kernel Thread". Initially I got an error stating that /usr/src/linux-headers-2.6.26.2/arch/x86/Makefile_32.cpu couldn't be found so I copied makefile to that. After that I got

/usr/src/linux-headers-2.6.26.2/arch/x86/Makefile_32.cpu:223: warning: ignoring old commands for target `zlilo'
/usr/src/linux-headers-2.6.26.2/arch/x86/Makefile_32.cpu:223: warning: overriding commands for target `bzlilo'
/usr/src/linux-headers-2.6.26.2/arch/x86/Makefile_32.cpu:223: warning: ignoring old commands for target `bzlilo'
/usr/src/linux-headers-2.6.26.2/arch/x86/Makefile_32.cpu:226: warning: overriding commands for target `zdisk'
/usr/src/linux-headers-2.6.26.2/arch/x86/Makefile_32.cpu:226: warning: ignoring old commands for target `zdisk'
/usr/src/linux-headers-2.6.26.2/arch/x86/Makefile_32.cpu:226: warning: overriding commands for target `bzdisk'
/usr/src/linux-headers-2.6.26.2/arch/x86/Makefile_32.cpu:226: warning: ignoring old commands for target `bzdisk'
/usr/src/linux-headers-2.6.26.2/arch/x86/Makefile_32.cpu:229: warning: overriding commands for target `fdimage'
/usr/src/linux-headers-2.6.26.2/arch/x86/Makefile_32.cpu:229: warning: ignoring old commands for target `fdimage'
/usr/src/linux-headers-2.6.26.2/arch/x86/Makefile_32.cpu:229: warning: overriding commands for target `fdimage144'
/usr/src/linux-headers-2.6.26.2/arch/x86/Makefile_32.cpu:229: warning: ignoring old commands for target `fdimage144'
/usr/src/linux-headers-2.6.26.2/arch/x86/Makefile_32.cpu:229: warning: overriding commands for target `fdimage288'
/usr/src/linux-headers-2.6.26.2/arch/x86/Makefile_32.cpu:229: warning: ignoring old commands for target `fdimage288'
/usr/src/linux-headers-2.6.26.2/arch/x86/Makefile_32.cpu:229: warning: overriding commands for target `isoimage'
/usr/src/linux-headers-2.6.26.2/arch/x86/Makefile_32.cpu:229: warning: ignoring old commands for target `isoimage'
/usr/src/linux-headers-2.6.26.2/arch/x86/Makefile_32.cpu:232: warning: overriding commands for target `install'
/usr/src/linux-headers-2.6.26.2/arch/x86/Makefile_32.cpu:232: warning: ignoring old commands for target `install'
/usr/src/linux-headers-2.6.26.2/arch/x86/Makefile_32.cpu:236: warning: overriding commands for target `vdso_install'
/usr/src/linux-headers-2.6.26.2/arch/x86/Makefile_32.cpu:236: warning: ignoring old commands for target `vdso_install'
/usr/src/linux-headers-2.6.26.2/arch/x86/Makefile_32.cpu:239: warning: overriding commands for target `archclean'
/usr/src/linux-headers-2.6.26.2/arch/x86/Makefile_32.cpu:239: warning: ignoring old commands for target `archclean'
make[2]: execvp: /bin/sh: Argument list too long
make[2]: execvp: /bin/sh: Argument list too long
make[2]: execvp: /bin/sh: Argument list too long

This seemed to repeat several times before I hit Control-C.

What is the best way to get this to compile against this kernel?
P.S. I am using this kernel so that rt61pci module doesn't cause kernel panic when using wireless card.

---

### Post by JonMD on 2008-08-18
Solved this by using export LINUXDIR=/usr/src/linux instead of /usr/src/linux-headers.
For some reason the makefiles in the header package are different

glxgears achieving 298 FPS for 16 bit
Compositing efffects now working in xfce.

---

### Post by dcottingham on 2009-02-05
I've been trying the method of posts 215/216 to get a working mach64 kernel module for 8.10 (kernel 2.6.27-11-generic).  But no joy.

When I try depmod -a; modprobe mach64 I get Invalid module format.  I check dmesg and there's lots of lines about symbol version mismatches.  I check drm/README and it gives instructions for how to deal with this case: lose your Module.symvers file, make clean, and build again. So I do.

Now when I try to load it, I get the same complaint (Invalid module format) bu now dmesg says: No symbol version for struct_module.

Any ideas how I can get past this?

And has this thread set a new record for longevity yet?

---

### Post by ModelR on 2009-06-26
[COLOR=Red]Note: The git of the drm that I downloaded on June 26, 2009 caused my system to hang.  There is a bug write up that specifies that drm versions after 2.4.1 will cause the system to hang[/COLOR]

I was able to successfully get this working.  I made a blog post with a good amount of reference links to go through if your having troubles.

[Here is the link]("http://techkrunch.co.cc/index.php/2009/06/23/how-to-get-3d-graphics-on-a-dell-cpx-laptop-with-linux/")

The system that I Was able to get it running on was a Dell Latitude CPx series consisting of:

-Debian Lenny 5.01 with kernel version 2.6.26-2-686
-VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

If your using kernel version 2.6.30 be prepared for a lot of code hacking

By the way:
[dcottingham]("http://ubuntuforums.org/member.php?u=707303")
> Now when I try to load it, I get the same complaint (Invalid module format) bu now dmesg says: No symbol version for struct_moduleNot sure if this will work for you, try building the kernel with DRM support. I found that when DRM support was not enabled I would get errors such as this.

I tried too many things on different versions.
I tried to document as much as possible.
Was not able to get it successfully working with Jaunty, but I was able to get it working multiple times in Debian Lenny.

Good luck.

---

### Post by Nyvhek on 2009-07-17
Got this working on Jaunty on a Dell CPx. I mostly followed [216]("http://ubuntuforums.org/showpost.php?p=4906456&postcount=216"). Differences:

1) wget [http://cgit.freedesktop.org/mesa/drm/snapshot/libdrm-2.4.1.tar.gz](http://cgit.freedesktop.org/mesa/drm/snapshot/libdrm-2.4.1.tar.gz) instead of git cloning latest (thanks ModelR for the info about later versions not working)

2) sudo cp *.ko /lib/modules/`uname -r`/kernel/drivers/**gpu**/drm/ (instead of char/drm/) - this overwrites the default drm.ko and prevents mach64 complaining about incompatibilities

3) xorg.conf didn't exist by default, so I made a new one and pasted alex.bb's excerpt from 216 - worked fine with no additional changes.

Hope this helps.

---

### Post by gsker on 2009-11-14
**[SIZE="3"]Works with Sony Vaio Picturebook PCG-C1VPK[/SIZE]**.
Installed the necessary kernel build tools.  
Unpacked [http://cgit.freedesktop.org/mesa/drm/snapshot/libdrm-2.4.1.tar.gz](http://cgit.freedesktop.org/mesa/drm/snapshot/libdrm-2.4.1.tar.gz)
[FONT="Courier New"]**cd linux-core**[/FONT] therein.
[FONT="Courier New"]**make mach64.o**[/FONT]
(I did all this on a faster machine)
and copied the .ko files to the vaio.
[FONT="Courier New"]**depmod -a**[/FONT]
Loaded the modules and restarted X.
My glxgears rate went from 29 to 280 FPS.
I'm running Jaunty and here's my uname -srv output.
[FONT="Courier New"]**Linux 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:24 UTC 2009**[/FONT]
I experienced the dying with blinking lights when I used the version from the git repository.

---

### Post by alex.bb on 2009-11-15
> **gsker said:**
> **[SIZE="3"]Works with Sony Vaio Picturebook PCG-C1VPK[/SIZE]**.
Installed the necessary kernel build tools.  
Unpacked [http://cgit.freedesktop.org/mesa/drm/snapshot/libdrm-2.4.1.tar.gz](http://cgit.freedesktop.org/mesa/drm/snapshot/libdrm-2.4.1.tar.gz)
[FONT="Courier New"]**cd linux-core**[/FONT] therein.
[FONT="Courier New"]**make mach64.o**[/FONT]
(I did all this on a faster machine)
and copied the .ko files to the vaio.
[FONT="Courier New"]**depmod -a**[/FONT]
Loaded the modules and restarted X.
My glxgears rate went from 29 to 280 FPS.
I'm running Jaunty and here's my uname -srv output.
[FONT="Courier New"]**Linux 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:24 UTC 2009**[/FONT]
I experienced the dying with blinking lights when I used the version from the git repository.

Can you open a virtual terminal with CTRL-ALT-F1 wthout X crash?

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=542382](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=542382)

---

### Post by displacedTex on 2010-01-24
So, there is no linux-core folder after running the code below:

 ```
git clone git://anongit.freedesktop.org/git/mesa/drm

cd drm/linux-core
```I have read from [here]("http://wiki.archlinux.org/index.php/Mach64") that:

> The source is no longer maintained in freedesktop.org's libdrm git repo (git://anongit.freedesktop.org/git/mesa/drm). The people maintaining libdrm who own that repo have deleted the drm kernel modules (like the one this package packages), because these modules are being developed in the kernel's git tree ([http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git)).Any ideas how to proceed?

Thanks!

---

### Post by displacedTex on 2010-01-25
The post above mine is spam and should be deleted.

Ok... I was able to compile the kernel module using code from [here]("http://www.linuxquestions.org/questions/linux-software-2/git-780222/") by reverting back to a version that had the missing linux-core directory:

```
mark@debian:~$ cd mach64
mark@debian:~/mach64$ cd drm
mark@debian:~/mach64/drm$ git checkout 2.4.15
Note: moving to "2.4.15" which isn't a local branch
If you want to create a new branch from this checkout, you may do so
(now or later) by using -b with the checkout command again. Example:
  git checkout -b <new_branch_name>
HEAD is now at a107e5b... Bump to 2.4.15 for release.
mark@debian:~/mach64/drm$ git checkout -b 2.4.15
Switched to a new branch "2.4.15"
mark@debian:~/mach64/drm$ cd linux-core
mark@debian:~/mach64/drm/linux-core$
```

Now, when I copy both compiled kernel modules (drm.ko and mach64.ko) to /lib/modules/2.6.26-2-686/kernel/drivers/char/drm, my machine will not boot.  I get two flashing leds (don't know what that means).  I had to start in single user mode and revert drm.ko back to the original (thank goodness I kept a backup copy).

When I get it to successfully boot and run modprobe mach64 I get:

```
[  592.857090] mach64: disagrees about version of symbol drm_open
[  592.857127] mach64: Unknown symbol drm_open
[  592.857298] mach64: disagrees about version of symbol drm_fasync
[  592.857305] mach64: Unknown symbol drm_fasync
[  592.857475] mach64: disagrees about version of symbol drm_poll
[  592.857482] mach64: Unknown symbol drm_poll
[  592.857714] mach64: disagrees about version of symbol drm_core_get_reg_ofs
[  592.857722] mach64: Unknown symbol drm_core_get_reg_ofs
[  592.857924] mach64: disagrees about version of symbol drm_pci_alloc
[  592.857932] mach64: Unknown symbol drm_pci_alloc
[  592.858102] mach64: disagrees about version of symbol drm_irq_uninstall
[  592.858110] mach64: Unknown symbol drm_irq_uninstall
[  592.858514] mach64: Unknown symbol drm_get_dev
[  592.858721] mach64: disagrees about version of symbol drm_ioctl
[  592.858728] mach64: Unknown symbol drm_ioctl
[  592.858896] mach64: disagrees about version of symbol drm_exit
[  592.858903] mach64: Unknown symbol drm_exit
[  592.859072] mach64: disagrees about version of symbol drm_getsarea
[  592.859079] mach64: Unknown symbol drm_getsarea
[  592.859423] mach64: disagrees about version of symbol drm_core_ioremapfree
[  592.859431] mach64: Unknown symbol drm_core_ioremapfree
[  592.859603] mach64: disagrees about version of symbol drm_core_get_map_ofs
[  592.859611] mach64: Unknown symbol drm_core_get_map_ofs
[  592.859780] mach64: disagrees about version of symbol drm_init
[  592.859787] mach64: Unknown symbol drm_init
[  592.860195] mach64: Unknown symbol drm_handle_vblank
[  592.860466] mach64: Unknown symbol drm_cleanup_pci
[  592.860644] mach64: disagrees about version of symbol drm_pci_free
[  592.860651] mach64: Unknown symbol drm_pci_free
[  592.860821] mach64: disagrees about version of symbol drm_core_ioremap
[  592.860828] mach64: Unknown symbol drm_core_ioremap
[  592.861057] mach64: disagrees about version of symbol drm_mmap
[  592.861064] mach64: Unknown symbol drm_mmap
[  592.861286] mach64: disagrees about version of symbol drm_core_reclaim_buffers
[  592.861294] mach64: Unknown symbol drm_core_reclaim_buffers
[  592.861464] mach64: disagrees about version of symbol drm_release
[  592.861471] mach64: Unknown symbol drm_release
[  766.778915] mach64: disagrees about version of symbol drm_open
[  766.778955] mach64: Unknown symbol drm_open
[  766.779129] mach64: disagrees about version of symbol drm_fasync
[  766.779136] mach64: Unknown symbol drm_fasync
[  766.779306] mach64: disagrees about version of symbol drm_poll
[  766.779313] mach64: Unknown symbol drm_poll
[  766.779545] mach64: disagrees about version of symbol drm_core_get_reg_ofs
[  766.779553] mach64: Unknown symbol drm_core_get_reg_ofs
[  766.779755] mach64: disagrees about version of symbol drm_pci_alloc
[  766.779763] mach64: Unknown symbol drm_pci_alloc
[  766.779933] mach64: disagrees about version of symbol drm_irq_uninstall
[  766.779941] mach64: Unknown symbol drm_irq_uninstall
[  766.780410] mach64: Unknown symbol drm_get_dev
[  766.780624] mach64: disagrees about version of symbol drm_ioctl
[  766.780632] mach64: Unknown symbol drm_ioctl
[  766.780800] mach64: disagrees about version of symbol drm_exit
[  766.780807] mach64: Unknown symbol drm_exit
[  766.780975] mach64: disagrees about version of symbol drm_getsarea
[  766.780982] mach64: Unknown symbol drm_getsarea
[  766.781328] mach64: disagrees about version of symbol drm_core_ioremapfree
[  766.781336] mach64: Unknown symbol drm_core_ioremapfree
[  766.781508] mach64: disagrees about version of symbol drm_core_get_map_ofs
[  766.781516] mach64: Unknown symbol drm_core_get_map_ofs
[  766.781685] mach64: disagrees about version of symbol drm_init
[  766.781692] mach64: Unknown symbol drm_init
[  766.782017] mach64: Unknown symbol drm_handle_vblank
[  766.782267] mach64: Unknown symbol drm_cleanup_pci
[  766.782444] mach64: disagrees about version of symbol drm_pci_free
[  766.782451] mach64: Unknown symbol drm_pci_free
[  766.782620] mach64: disagrees about version of symbol drm_core_ioremap
[  766.782628] mach64: Unknown symbol drm_core_ioremap
[  766.782857] mach64: disagrees about version of symbol drm_mmap
[  766.782864] mach64: Unknown symbol drm_mmap
[  766.783109] mach64: disagrees about version of symbol drm_core_reclaim_buffers
[  766.783118] mach64: Unknown symbol drm_core_reclaim_buffers
[  766.783288] mach64: disagrees about version of symbol drm_release
[  766.783295] mach64: Unknown symbol drm_release

```

I am eager to resolve this if someone is willing to help.

Is it possible to use the mach64 kernel module on a recent kernel?

I can't be the only one who would like to get hardware acceleration working on an older laptop.

Thanks!

---

### Post by Erik500002 on 2010-03-06
Hi, i seem to be having a problem compiling the drivers. I have tried everything .. the modified pcigart, but unfortunately no luck.. i have the latest linux kernel which is 2.6.28-11 generic running jaunty on a evo n400c i'm desperate here for some help always end up with Error: Kernel modules did not compile .. i would really appreciate any help... Thanks.

---

### Post by jdos2 on 2010-07-27
Not to be too editorial, but this is has been on the issues list with this old a20m for YEARS now.
See, I can either have great and fast graphics (Fedora COMES with the DRM module working for Mach64!) BUT (and it's an important BUT) the ALSA that they have does NOT work with the CS46xx.
Ubuntu must be trying to copy Fedora, as the symptoms are identical- and the bug report has been open for a LONG time now ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/428619](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/428619) September 2009)
Debian gave up in Lenny, and doesn't even include support for the CS46xx OR Mach64- the first because someone asked several years ago for permission to include the binary blob (permission granted, it seems, as code is in SID!) but the Mach64 is not included as it's unsafe- and will wipe your Zip drive, beacon your Token Ring, split your FDDI, mutilate your job card, scratch all your records, freeze your printer chains, unsynchronize your carbs, bend your rode draft tube, fill all available spool (and put your operator to sleep!)...
Debian Backports DOES have, though, a way to build the CS46xx driver. It does NOT yet have a way that I can find to build the Mach64 Direct Rendering driver. 

So Linux on an old laptop is really "pick your poison, and hope for the best." 
I went with good audio on the a20m, so Debian, with Backports, and recompiling several things I like. Direct Rendering would help with some things and so video ain't great, but it's better than terrible sound and good frame rates (Fedora).

Ya picks your bugs, ya takes your chances.

Hope someone finds a way to get this working. It's a Real Pain!

---

### Post by photor on 2011-01-17
any ideas about how to make this work with ubuntu 10.04lts?

---

### Post by searchfgold6789 on 2011-08-26
Hello,
I run the './common/install.sh' and I get the following error when the installations part actually happens (at the very end):
```
install.sh: line 708: syntax error: Bad fd number
```
Is there a solution for this?
Thank you for the great guide!
My computer has the same card as mentioned in the first post.

---

### Post by searchfgold6789 on 2011-08-26
> **searchfgold6789 said:**
> Hello,
I run the './common/install.sh' and I get the following error when the installations part actually happens (at the very end):
```
install.sh: line 708: syntax error: Bad fd number
```Is there a solution for this?
Thank you for the great guide!
My computer has the same card as mentioned in the first post.
**Solved.**
I just had to install "bash"... slitaz ~.~

---

### Post by Harry777 on 2012-07-21
I'm running xubuntu 10.04lts on a very old acer laptop. I have an external monitor connected but the system only sees one display. My vga card is ATI 3D Rage P/M Mobility AGP 2x. Is there a way to get the external display recognized separately without building the mach64 driver? I don't need 3D acceleration.

Any help would be much appreciated.

---

### Post by searchfgold6789 on 2012-07-21
> **Harry777 said:**
> I'm running xubuntu 10.04lts on a very old acer laptop. I have an external monitor connected but the system only sees one display. My vga card is ATI 3D Rage P/M Mobility AGP 2x. Is there a way to get the external display recognized separately without building the mach64 driver? I don't need 3D acceleration.

Any help would be much appreciated.
There might be a button on your keyboard that does this. For mine, I have to press the blue-type "Fn" button and F8 at the same time; below F8 I can read the blue words "CRT/LCD". 
You shouldn't have to build the driver from source. Open Source drivers come preinstalled.

---

### Post by Harry777 on 2012-07-22
> **searchfgold6789 said:**
> There might be a button on your keyboard that does this. For mine, I have to press the blue-type "Fn" button and F8 at the same time; below F8 I can read the blue words "CRT/LCD". 
You shouldn't have to build the driver from source. Open Source drivers come preinstalled.

I can flip between displays with Fn-F5 but the system only sees one display. xrandr gives this:

> Screen 0: minimum 320 x 175, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        63.0*    61.0     59.0  
   640x480        63.0     62.0     61.0  
   720x400        60.0  
   640x400        60.0  
   640x350        57.0  
   512x384        65.0  
   400x300        63.0     61.0     59.0  
   320x240        63.0     62.0     61.0  
   360x200        60.0  
   320x200        61.0  
   320x175        57.0 During boot there is a message that says something like "WMI module not supported, unable to load"

I'm stuck with 800x600 even though the vga output can give higher resolution.

---

### Post by flamboyant on 2012-10-01
hello!

i've got an old Fujitsu LifeBook on my hands. i installed Lubuntu 12.04 on it and tried glxgears which gave me about 10 FPS. should i follow this howto to improve the graphics card performance or that's all i can expect from this hardware?

> $ lspci | grep VGA
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Rage Mobility P/M AGP 2x (rev 64)

thank you!

---

### Post by searchfgold6789 on 2012-10-01
The drivers are now built in to Ubuntu and offer the bet possible performance.

---

### Post by flamboyant on 2012-10-02
> **searchfgold6789 said:**
> The drivers are now built in to Ubuntu and offer the bet possible performance.

thanks for the reply, but i'm not so sure this performance is the best possible, as the same glxgears on Wary Puppy gave me 100-110 FPS on the same machine with the same resolution, albeit the depth was 16 instead of 24, even in the Live CD mode. can anyone explain that, please?

---

