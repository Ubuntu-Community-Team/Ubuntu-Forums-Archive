---
title: "ATI Catalyst 8.3 drivers released."
date: 2008-03-06
forum: The Cafe
---

### Post by Polygon on 2008-03-06
release notes: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_83_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_83_linux.html)

> 
**Resolved Issues**

The following section provide a brief description of resolved issues with the latest version of the ATI Catalyst™ Linux software suite. These include:

    * On workstation hardware 3D applications will no longer be corrupted if the screen width is not an integer multiple of 64 pixels, for example with a 1680x1050 wide screen display. Further details can be found in topic number 737-31720
    * Display flicker is no longer be noticed when the gnome screen-saver starts
    * Several image brightness and gamma-correction issues were resolved. Setting the gamma correction using xgamma, fglrx_xgamma, xorg.conf and in OpenGL games will all work as expected now.
    * Diagonal tearing will no longer be noticed when playing a video file using a video player that utilizes the XVideo extension
    * Video playback will no longer look blocky when playing a video file using a video player that utilizes the XVideo extension 

**Known Issues**

The following section provides a brief description of known issues associated with the latest version of ATI Catalyst™ Linux software suite. These issues include:

    * There is no support for video playback on the second head in dual head mode. Further details can be found in topic number 737-26985
    * Desktop corruption may be noticed when dragging the overlay/video when using dual-display mode. Further details can be found in topic number 737-29578
    * A black screen may be observed on some hardware when switching to the console or leaving the X window system when a Vesa framebuffer console driver is used. Further details can be found in topic number 737-30687
    * Video Playback may display wrong colors and additional shadow images when cropping or expanding a video file using a video player that utilizes the XVideo extension  

For further information and general help on driver or software installation, game issues, and more, visit the ATI FAQ website. 


as always, chmod +x the file then 

./ati-driver-installer-8-3-x86.x86_64.run --buildpkg Ubuntu/Gutsy

then 

sudo dpkg -i *.deb

to install them

Im at least happy they fixed the gnome screensaver thing. :D

---

### Post by TheOrangePeanut on 2008-03-06
Should I disable the restricted drivers before I create the deb and install the new drivers?

---

### Post by NuSuey on 2008-03-06
not working for me.. got a black screen :( 

first i tried only

sudo ./ati.. blah blah blah.deb

after reboot black screen, so i tryied the "aticonfig --initial -f" .. after reboot, still black screen..


then i tried yours.. not working again :(

---

### Post by sloggerkhan on 2008-03-06
nice drivers. definite improvements to xv.

---

### Post by NuSuey on 2008-03-06
so can somebody help how to fix this? 

got a MSI EX610 notebook ( AMD X2 TK55 2X1.8Ghz, 2048 Mb, 160 Gb, DVD+/-RW DL, 15.4", ATI Radeon HD 2400 )

---

### Post by tom-ubuntu on 2008-03-06
What is the advantage of creating a deb-file instead of using the installer directly?

I used the installer and it works without any problem. Haven't had the time to really test, as I installed quickly before going to work.

---

### Post by Polygon on 2008-03-06
the debs just make it a whole lot easier to remove if you decide to downgrade or just remove em

And if you get a black screen...i dunno...is your ATI card supported in the release notes? I know once i installed them i had to run aticonfig --initial but since you have already done that i dunno

and you dont have to disable the restricted drivers, as the new drivers will just upgrade whats already installed.

---

### Post by Tristam Green on 2008-03-06
I must be out of my mind....where am I finding this driver @.@

Searching through the Driver-search applet on amd.ati.com isn't yielding any results for my card, although the chipset is supported in the release notes.

---

### Post by Polygon on 2008-03-06
ati.com

support and drivers

get latest drivers (under graphics support)

then you can go through the little thing to select your card....linux x86...radeon....whatever

---

### Post by Tristam Green on 2008-03-06
> **Polygon said:**
> ati.com

support and drivers

get latest drivers (under graphics support)

then you can go through the little thing to select your card....linux x86...radeon....whatever

Yup, I'm in the Radeon Xpress 1100 family (integrated).  Doesn't show up in the list.  :confused:

---

### Post by amazingtaters on 2008-03-06
> **Tristam Green said:**
> Yup, I'm in the Radeon Xpress 1100 family (integrated).  Doesn't show up in the list.  :confused:

It never has, at least for as long as I can remember. I have an Xpress 1100 and just click on the Xpress 1250 or whatever. I've not had any problems with it.

---

### Post by Tristam Green on 2008-03-06
Thanks taters, that was the answer I was looking for.  I'm always leery of downloading drivers for a different chipset ;-)

---

### Post by pbpersson on 2008-03-06
This stupid ATI Radeon 9550 card will be the death of me yet.  I have tried like a half dozen different ways to get this to work with Kubuntu on my other machine and just when I think it is working, it gets me into some crazy vertical refresh rate the monitor can't handle.

Last night I tried Envy and now xServer won't work at all

I am replying to this thread just so I can find this tonight and try these instructions.

---

### Post by Tristam Green on 2008-03-06
```
Configuration file `/etc/xdg/compiz/compiz-manager'
 ==> Deleted (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : background this process to examine the situation
 The default action is to keep your current version.
*** compiz-manager (Y/I/N/O/D/Z) [default=N] ? n
 * Starting atieventsd                                                          /usr/sbin/atieventsd: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
                                                                         [fail]

Setting up xorg-driver-fglrx-dev (8.471-0ubuntu1) ...
Errors were encountered while processing:
 fglrx-amdcccle_8.471-0ubuntu1_i386.deb
 fglrx-kernel-source

```


thoughts?  i currently don't see any difference, but i also haven't restarted X.

---

### Post by Tristam Green on 2008-03-06
Restarted X, and it hangs after GDM login, and then returns to the GDM screen.

---

### Post by Hobbes87 on 2008-03-06
I got this when I entered
./ati-driver-installer-8-3-x86.x86_64.run --buildpkg Ubuntu/gutsy
in the terminal


Generating package: Ubuntu/Gutsy
Automatically detected gutsy
Resolving build dependencies...
./packages/Ubuntu/ati-packager.sh: 311: sh -c '/usr/sbin/synaptic --set-selections --non-interactive --hide-main-window < /tmp/filecQTNr1': not found
Unable to resolve  ia32-libs.  Please manually install and try again.
Removing temporary directory: fglrx-install.Le5929
michael@michael-desktop:~$ 


Don't know where to go from here

---

### Post by sloggerkhan on 2008-03-06
tristam, you probably need to manually purge any old fglrx setups as well as change compiz manager back to how it was.

---

### Post by Tristam Green on 2008-03-06
well, i think i've hosed it up fairly well now.

I attempted ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` based off info found in other threads, and that left me not being able to get into failsafe gnome, and only into failsafe terminal.  that's ok though.  it can be fixed command-line, and i'm hoping to plod along until i salvage.

in failsafe-terminal,  ran ```
sudo apt-get remove fglrx*
```

apt removed a load of items. now i'm blank as to where to go....

truth be told, if i gotta fresh install, i backed up my home directory today so there's no real loss, lol.

---

### Post by aaaantoine on 2008-03-06
What's this I'm reading about using 8.3 in Gutsy?

[quote="Ubuntu Gutsy Installation Guide"]Note: The newest 8.471.0 does not enable DRI using gutsy. It needs a more recent X.org for this, but 2D does work. "(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0"[/quote]

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

I'm gonna stick to Catalyst 8.2 for now.  Maybe later I'll look into installing a newer X.org.

---

### Post by Resonance378 on 2008-03-06
^^^ good catch ^^^

Good summary of the what from Phoronix.com
[http://www.phoronix.com/scan.php?page=article&item=catalyst_803&num=1](http://www.phoronix.com/scan.php?page=article&item=catalyst_803&num=1)

And the link to the drivers
[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

---

### Post by melenor on 2008-03-06
Does anyone know if theses or which set of ATI Drivers are going to be in 8.04?

---

### Post by forrestcupp on 2008-03-06
> **pbpersson said:**
> This stupid ATI Radeon 9550 card will be the death of me yet.  I have tried like a half dozen different ways to get this to work with Kubuntu on my other machine and just when I think it is working, it gets me into some crazy vertical refresh rate the monitor can't handle.
I think that card should work perfectly with the open source drivers.  You shouldn't even need to use the proprietary ones.

> **Tristam Green said:**
> well, i think i've hosed it up fairly well now.
Try booting to the recovery console and type:
```
envy --uninstall-all
```
then try again
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
then
```
envy -t
```
which will give you the text mode of Envy so you can install the drivers again.

If you do things in this order, Envy will uninstall your current setup, then just to be safe, you will reconfigure X, then install the drivers to a clean setup.

That has worked for me before.

---

### Post by AceRimmer on 2008-03-06
I got this error

```
aaron@Odin:~/downloads$ sudo dpkg -i *.deb
[sudo] password for aaron:
Selecting previously deselected package fglrx-amdcccle.
(Reading database ... 102694 files and directories currently installed.)
Unpacking fglrx-amdcccle (from fglrx-amdcccle_8.471-0ubuntu1_i386.deb) ...
dpkg: error processing fglrx-amdcccle_8.471-0ubuntu1_i386.deb (--install):
 trying to overwrite `/usr/bin/amdcccle', which is also in package xorg-driver-fglrx
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Selecting previously deselected package fglrx-kernel-source.
Unpacking fglrx-kernel-source (from fglrx-kernel-source_8.471-0ubuntu1_i386.deb) ...
Preparing to replace xorg-driver-fglrx 7.1.0-8.37.6+2.6.22.4-14.10 (using xorg-driver-fglrx_8.471-0ubuntu1_i386.deb) ...
Unpacking replacement xorg-driver-fglrx ...
Selecting previously deselected package xorg-driver-fglrx-dev.
Unpacking xorg-driver-fglrx-dev (from xorg-driver-fglrx-dev_8.471-0ubuntu1_i386.deb) ...
dpkg: dependency problems prevent configuration of fglrx-kernel-source:
 fglrx-kernel-source depends on dkms; however:
  Package dkms is not installed.
dpkg: error processing fglrx-kernel-source (--install):
 dependency problems - leaving unconfigured
Setting up xorg-driver-fglrx (8.471-0ubuntu1) ...

Configuration file `/etc/xdg/compiz/compiz-manager'
 ==> Deleted (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : background this process to examine the situation
 The default action is to keep your current version.
*** compiz-manager (Y/I/N/O/D/Z) [default=N] ? y
Installing new version of config file /etc/xdg/compiz/compiz-manager ...
 * Starting atieventsd                                                                                                            /usr/sbin/atieventsd: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
                                                                                                                           [fail]

Setting up xorg-driver-fglrx-dev (8.471-0ubuntu1) ...
Errors were encountered while processing:
 fglrx-amdcccle_8.471-0ubuntu1_i386.deb
 fglrx-kernel-source
aaron@Odin:~/downloads$ 

```

---

### Post by Polygon on 2008-03-07
AceRimmer and whoever has problems with 'package dkms is required by not installed'

run this

sudo apt-get -f install

and it should resolve the dependency problems and then finish installing those packages. Dont forget to run sudo aticonfig --initial afterwards.

---

### Post by el-mar01 on 2008-03-07
> * Diagonal tearing will no longer be noticed when playing a video file using a video player that utilizes the XVideo extension
* Video playback will no longer look blocky when playing a video file using a video player that utilizes the XVideo extension

Diagonal tearing has been fixed but now theres a weird line that runs down the screen if there is light flashing in the video.

They haven't fixed the blocking .... only reduced it slightly ... *sigh* when can my Ubuntu video playback look as good as it did on Windows.

---

### Post by TheOrangePeanut on 2008-03-07
Okay, I think I got the drivers install correctly.  However, I'm not getting direct rendering, or at least, I don't think I am.  I installed the drivers, ran sudo aticonfig --initial, and rebooted.  Now, when I do glxinfo | grep direct I get this:

```
nelson@alpha-pc:~$ glxinfo | grep direct
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)

```

Here is my xorg.conf.  It seems way more barren than my xorg.conf before I updated the driver...

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"SyncMaster"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection 
```

---

### Post by AceRimmer on 2008-03-07
> **Polygon said:**
> AceRimmer and whoever has problems with 'package dkms is required by not installed'

run this

sudo apt-get -f install

and it should resolve the dependency problems and then finish installing those packages. Dont forget to run sudo aticonfig --initial afterwards.

Thanks I'll give it a shot when I get home.

---

### Post by zukini220 on 2008-03-07
So I installed the 8.3 drivers on my laptop yesterday (Mobility X300, which I think is R300?), and i noticed some significant improvements:

* The authentication popup (when you open Synaptic, for example) now fades the background smoothly

* The screensaver now fades smoothly

* Transparency in the terminal seems to be more efficient (no tearing)

* Firefox scrolls more smoothly

* In general, higher framerates for me all around with compiz

Only issue is I still can't set overlay-type=Xv because I get no video output. I have to have it set to opengl. Anyone else notice this issue? Xv seems like it would be much more efficient. Is there a workaround?

---

### Post by mra122 on 2008-03-07
mmm....
I just installed these...
and...mmm...I lost compiz...it works, but its too damn slow and barely responds...


:-   (:confused:

---

### Post by frogotronic on 2008-03-07
Can some explain the following statement to me?  (from the install [wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.3_Driver_Manually"))

```
Method 2: Install the Catalyst 8.3 Driver Manually

    This is just an alternative installation method for the section above. It might help if you still get 'DRI missing' errors. 

    * Note: The newest 8.471.0 does not enable DRI using gutsy. It needs a more recent X.org for this, but 2D does work. "(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0" (Citation needed!) 
```


Does this mean the new 8.3 drivers will install, but if you use Gutsy there will be no DRI (Direct Rendering Infrastructure), thus no OpenGL capacity?

And, this would be due to the "older" XOrg driver that Gutsy uses?  Am I interpreting this correctly?

Thanks,
CH

:confused:

---

### Post by 50words on 2008-03-07
I set it up and got it running.

But what does this command mean? ```
--overlay-type=Xv
```

I ran it, but I didn't know why or what it did. But CCC would not start up until after I did it.

Also, I ran ```
--dtop=horizontal
``` to get the Big Desktop working. But I did not use ```
--overlay-on=1
``` as mentioned in the aticonfig manual. Should I use that? If so, what does it do?

In short, what is overlay and what does it do?

Finally, I am running Big Desktop with a spare monitor at work, but this is my laptop, and obviously I only have one screen otherwise. Is there a way to switch automatically when the screen is not present (and then back when it is), or do I have to restart X every time I want to switch to dual monitors (or back to a single monitor)?

---

### Post by black_mamba on 2008-03-07
Maya doesn't work any more.... :( It worked with 8.2, but now it doesn't. Here's my output:

mamba@mamba-laptop:~$ maya


maya encountered a fatal error

Signal: 11 (Unknown Signal)
Fatal Error. Attempting to save in /usr/tmp/mamba.20080307.2329.ma

I'm not using compiz with maya.

EDIT: maya works, I didn't install the driver properly at first, now I reinstalled and everything works. I apologize for spamming :redface:

---

### Post by bkraptor on 2008-03-08
The latest Envy installs the latest Catalyst without problems. Still flickering 3D with Compiz enabled, and it somehow broke my hibernation. When I try to hibernate, it goes back to the password screen right away.

---

### Post by dashnak on 2008-03-08
> **bkraptor said:**
> The latest Envy installs the latest Catalyst without problems. Still flickering 3D with Compiz enabled, and it somehow broke my hibernation. When I try to hibernate, it goes back to the password screen right away.

I seem somehow unable to tell Envy to install the latest version, how did you do it?

---

### Post by bkraptor on 2008-03-08
I just installed the latest Envy and told it to install the ATI Catalyst driver. It downloaded the 8.3 version and installed it, all by itself.

---

### Post by frogotronic on 2008-03-08
Installed the 8.3 drivers on a HP6910p laptop.

No improvement with Compiz & video (still flickers).

- CH

---

### Post by forrestcupp on 2008-03-08
> **cement_head said:**
> Installed the 8.3 drivers on a HP6910p laptop.

No improvement with Compiz & video (still flickers).

- CH

According to some things said in the Phoronix forums, they probably will never fix it.  It would take reworking the entire framework.  I think they're waiting for that problem to get fixed in Xorg, and I don't know how excited Xorg is about tackling that problem.  That knowledge is the very reason I switched to nvidia, because they have already fixed that in their hacked GLX.

---

### Post by frogotronic on 2008-03-08
> **forrestcupp said:**
> According to some things said in the Phoronix forums, they probably will never fix it.  It would take reworking the entire framework.  I think they're waiting for that problem to get fixed in Xorg, and I don't know how excited Xorg is about tackling that problem.  That knowledge is the very reason I switched to nvidia, because they have already fixed that in their hacked GLX.

bummer...well, we'll see if Hardy takes care of this.  I don't use compiz, but it would be nice

---

### Post by sloggerkhan on 2008-03-08
If you use the current fglrx with xv video overlay and set the 3-D workaround for full screen, you can more or less use it with no problems. XV videos play fine in compiz, and the full screen workaround makes it so games are fine with compiz running, at least in full screen mode. And yeah, my understanding is that the flickering issue is an xorg problem.
Personally, I'd rather they stick to spec than go off and make something even more hacked and specialized, so I don't really think it's something to complain to ati about.

---

### Post by softtower on 2008-03-08
Damn you ATI... I have subscribed to their drivers RSS feed and I get notifications every time a new driver comes out.

This crap never works right. This version, while finally (!) managing to run Compiz, hangs my ThinkPad T60 when I try to hibernate, although they claim they fixed it.

Moreover, I get random garbage on screen around mouse cursor at times, and Compiz performance is nothing to write home about - scrolling and window resizing is much slower than on a regular 2D desktop.

@#ick it, I am going back to Feisty and its default fglrx driver. It may not support this useless 3D "slide show" but it works, never hangs, and suspend/hibernate work just fine.

I have Mobility FireGL v5250 - the video card from hell, when it comes to Linux.

---

### Post by excogitation on 2008-03-09
On Hardy running 
>  ./ati-driver-installer-8-3-x86.x86_64.run --buildpkg Ubuntu/Hardy
output:
```

Created directory fglrx-install.o18031
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.471.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/Hardy
Automatically detected hardy
Package /home/excogitation/downloads/ati/xorg-driver-fglrx_8.471-0ubuntu1_i386.deb has been successfully generated
Package /home/excogitation/downloads/ati/xorg-driver-fglrx-dev_8.471-0ubuntu1_i386.deb has been successfully generated
Package /home/excogitation/downloads/ati/fglrx-kernel-source_8.471-0ubuntu1_i386.deb has been successfully generated
Package /home/excogitation/downloads/ati/fglrx-amdcccle_8.471-0ubuntu1_i386.deb has been successfully generated
Removing temporary directory: fglrx-install.o18031

```
then
> sudo dpkg -i *.deb
gives
```
(Reading database ... 113717 files and directories currently installed.)
Preparing to replace fglrx-amdcccle 8.471-0ubuntu1 (using fglrx-amdcccle_8.471-0ubuntu1_i386.deb) ...
Unpacking replacement fglrx-amdcccle ...
Preparing to replace fglrx-kernel-source 8.471-0ubuntu1 (using fglrx-kernel-source_8.471-0ubuntu1_i386.deb) ...
Unpacking replacement fglrx-kernel-source ...
Preparing to replace xorg-driver-fglrx 8.471-0ubuntu1 (using xorg-driver-fglrx_8.471-0ubuntu1_i386.deb) ...
 * Stopping atieventsd                                                   [ OK ] 
Unpacking replacement xorg-driver-fglrx ...
Preparing to replace xorg-driver-fglrx-dev 8.471-0ubuntu1 (using xorg-driver-fglrx-dev_8.471-0ubuntu1_i386.deb) ...
Unpacking replacement xorg-driver-fglrx-dev ...
dpkg: dependency problems prevent configuration of fglrx-kernel-source:
 fglrx-kernel-source depends on dkms; however:
  Package dkms is not installed.
dpkg: error processing fglrx-kernel-source (--install):
 dependency problems - leaving unconfigured
Setting up xorg-driver-fglrx (8.471-0ubuntu1) ...
 * Starting atieventsd                                                          /usr/sbin/atieventsd: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
                                                                         [fail]

Setting up xorg-driver-fglrx-dev (8.471-0ubuntu1) ...
Setting up fglrx-amdcccle (8.471-0ubuntu1) ...

Errors were encountered while processing:
 fglrx-kernel-source

```

So how do I get  xorg-driver-fglrx  to install properly?

Is after this update aticonfig --lsp (more importantly --set-powerstate) 
working without > Error: Unable to obtain POWERplay information.
?

---

### Post by forrestcupp on 2008-03-09
> **sloggerkhan said:**
> If you use the current fglrx with xv video overlay and set the 3-D workaround for full screen, you can more or less use it with no problems. XV videos play fine in compiz, and the full screen workaround makes it so games are fine with compiz running, at least in full screen mode. And yeah, my understanding is that the flickering issue is an xorg problem.
Personally, I'd rather they stick to spec than go off and make something even more hacked and specialized, so I don't really think it's something to complain to ati about.

For some reason, the full screen workaround didn't work for me.  I had flickering issues with our without it.  nvidia drivers work for me without any faults.  I really don't care how they did it, as long as they got it to work.

If the ATI workarounds work for you, then more power to ya, and I'm happy for you.

---

### Post by krazyd on 2008-03-09
> **el-mar01 said:**
> They haven't fixed the blocking .... only reduced it slightly ... *sigh* when can my Ubuntu video playback look as good as it did on Windows.
Dammit, I thought they had finally done something about this when I saw the changelog. Should have know better. Have to also report here that video is still blocky on resize.. how frustrating!!

---

### Post by Polygon on 2008-03-09
excogitation, run 'sudo apt-get -f install' and it should resolve the dependency problems apt is experiencing and then should install the package that failed.

also, be sure to run aticonfig --initial afterwards

---

### Post by uDanimal on 2008-03-09
I finally had my ATI card up and running Big Deskto last night, and the "new updates" icon got my attention.  I let it upgrade to the new drivers, and spent the next hour or two reinstalling the PREVIOUS driver.  I got the one from the repositories, not from the ATI site though, but I am sticking with what works...if it aint broke, fix it until it IS....wait....I mean if it aint broke, leave it the heck alone and be happy, lol.

---

### Post by excogitation on 2008-03-10
Thanks, Polygon, but unfortunately the second package still fails.

```
Unpacking replacement xorg-driver-fglrx ...
Preparing to replace xorg-driver-fglrx-dev 8.471-0ubuntu1 (using xorg-driver-fglrx-dev_8.471-0ubuntu1_i386.deb) ...
Unpacking replacement xorg-driver-fglrx-dev ...
Setting up fglrx-kernel-source (8.471-0ubuntu1) ...
Adding Module to DKMS build system

Error! DKMS tree already contains: fglrx-8.471
You cannot add the same module/version combo more than once.
Doing initial module build

Error! This module/version has already been built on: 2.6.24-12-generic
Directory: /var/lib/dkms/fglrx/8.471/2.6.24-12-generic/i686
already exists.  Use the dkms remove function before trying to build again.
Installing initial module

Error! This module/version combo is already installed
for kernel: 2.6.24-12-generic (i686)
Done.

Setting up xorg-driver-fglrx (8.471-0ubuntu1) ...
 * Starting atieventsd                                                          /usr/sbin/atieventsd: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
                                                                         [fail]

Setting up xorg-driver-fglrx-dev (8.471-0ubuntu1) ...
Setting up fglrx-amdcccle (8.471-0ubuntu1) ...

aticonfig --initial
Found fglrx primary device section
Nothing to do, terminating.

fglrxinfo
fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

```

System -> Preferences -> Appearance -> Visual Effects  ->
switching to Extra still fails with "Desktop effects could not be enabled" (no surprise there).

My update Manager shows 
fglrx-kernel-source 1:8-02+2.6.24.10-12.30
xorg-driver-fglrx and xorg-driver-fglrx-dev 1:7.1.0-8-02+2.6.24.10-12.30

but when I run those Ubuntu switches back to Vesa on next boot and
I have to run sudo dpkg -i *.deb inside the ati folder again,
to get my 1680*1050 native resolution back.

I'm fairly new to Linux so basically I don't really know sh*t what I'm talking about :-(

---

### Post by himynameiskevin on 2008-03-10
i'm getting this error while running  sudo dpkg -i *.deb

> (Reading database ... 94943 files and directories currently installed.)
Preparing to replace fglrx-amdcccle 8.471-0ubuntu1 (using fglrx-amdcccle_8.471-0ubuntu1_i386.deb) ...
Unpacking replacement fglrx-amdcccle ...
Preparing to replace fglrx-kernel-source 8.471-0ubuntu1 (using fglrx-kernel-source_8.471-0ubuntu1_i386.deb) ...
Unpacking replacement fglrx-kernel-source ...
Preparing to replace xorg-driver-fglrx 8.471-0ubuntu1 (using xorg-driver-fglrx_8.471-0ubuntu1_i386.deb) ...
 * Stopping atieventsd                                                   [ OK ] 
Unpacking replacement xorg-driver-fglrx ...
Preparing to replace xorg-driver-fglrx-dev 8.471-0ubuntu1 (using xorg-driver-fglrx-dev_8.471-0ubuntu1_i386.deb) ...
Unpacking replacement xorg-driver-fglrx-dev ...
Setting up fglrx-kernel-source (8.471-0ubuntu1) ...
Adding Module to DKMS build system

Error! DKMS tree already contains: fglrx-8.471
You cannot add the same module/version combo more than once.
Doing initial module build

Error! This module/version has already been built on: 2.6.22-14-generic
Directory: /var/lib/dkms/fglrx/8.471/2.6.22-14-generic/i686
already exists.  Use the dkms remove function before trying to build again.
Installing initial module

Error! This module/version combo is already installed
for kernel: 2.6.22-14-generic (i686)
Done.

Setting up xorg-driver-fglrx (8.471-0ubuntu1) ...
 * Starting atieventsd                                                          /usr/sbin/atieventsd: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
                                                                         [fail]

Setting up xorg-driver-fglrx-dev (8.471-0ubuntu1) ...
Setting up fglrx-amdcccle (8.471-0ubuntu1) ...


i'm only able to login using failsafe gnome right now.. logging in regularly just fails and goes back to the login screen.

---

### Post by Polygon on 2008-03-10
try installing envy both of you and using the text version (envy -t ) if your stuck in command line and then select uninstall all ati drivers, then try it again. dkms is complaining that its already installed

---

### Post by himynameiskevin on 2008-03-10
okay, i just installed using envy.. appears to be working but not very well

after i installed with envy i was getting a LOT of tearing. i went and reactivated the ATI driver in the restircted driver manager (was i supposed to do this?) and the tearing is still there. the whole system is running considerably slower than before.

..any ideas? i'm using an ati xpress 1150, it worked decent enough with the old ATI drivers

okay just for an update... when compiz isn't running it runs much better, tried reinstalling compiz and it's still really slow. was never really that much of an issue with the old drivers. tried reinstalling the old drivers and that was a disaster, finally got the new ones working again. i'm pretty stuck..

also it may be worth mentioning that failsafe gnome runs flawlessly

---

### Post by cabez0n on 2008-03-11
> **excogitation said:**
> Thanks, Polygon, but unfortunately the second package still fails.

```
Unpacking replacement xorg-driver-fglrx ...
Preparing to replace xorg-driver-fglrx-dev 8.471-0ubuntu1 (using xorg-driver-fglrx-dev_8.471-0ubuntu1_i386.deb) ...
Unpacking replacement xorg-driver-fglrx-dev ...
Setting up fglrx-kernel-source (8.471-0ubuntu1) ...
Adding Module to DKMS build system

Error! DKMS tree already contains: fglrx-8.471
You cannot add the same module/version combo more than once.
Doing initial module build

Error! This module/version has already been built on: 2.6.24-12-generic
Directory: /var/lib/dkms/fglrx/8.471/2.6.24-12-generic/i686
already exists.  Use the dkms remove function before trying to build again.
Installing initial module

Error! This module/version combo is already installed
for kernel: 2.6.24-12-generic (i686)
Done.

Setting up xorg-driver-fglrx (8.471-0ubuntu1) ...
 * Starting atieventsd                                                          /usr/sbin/atieventsd: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
                                                                         [fail]

Setting up xorg-driver-fglrx-dev (8.471-0ubuntu1) ...
Setting up fglrx-amdcccle (8.471-0ubuntu1) ...

aticonfig --initial
Found fglrx primary device section
Nothing to do, terminating.

fglrxinfo
fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

```

System -> Preferences -> Appearance -> Visual Effects  ->
switching to Extra still fails with "Desktop effects could not be enabled" (no surprise there).

My update Manager shows 
fglrx-kernel-source 1:8-02+2.6.24.10-12.30
xorg-driver-fglrx and xorg-driver-fglrx-dev 1:7.1.0-8-02+2.6.24.10-12.30

but when I run those Ubuntu switches back to Vesa on next boot and
I have to run sudo dpkg -i *.deb inside the ati folder again,
to get my 1680*1050 native resolution back.

I'm fairly new to Linux so basically I don't really know sh*t what I'm talking about :-(

Do you have libGL ??
libGL.so.1: cannot open shared object file: No such file or directory
                                                                         [fail]
do # dpkg - l | grep -i libgl

---

### Post by frogotronic on 2008-03-11
excogitation, you need to cleanly remove the FGLRX driver and reinstall.


From the install wiki:

```
$ sudo dkms remove -m fglrx -v 8.471 --all
```

then reinstall

Further instructions/troubleshooting at the[ wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide").

- CH

---

### Post by qwerion on 2008-03-11
I have nx9420 laptop. Been using 8.42.3 drivers, no compiz, Big Desktop in "3360x1050" resolution.
At home I would connect my LCD as second monitor with res 1240x1024, at job second LCD was 1650x1050. Worked just fine.

Before few minutes, I've installed new drivers - 8.3.

Like, everything works but not so - second monitor is recognized as CRT, and would not switch to resolution higher than 1024x768.

When I turn compiz on, I can see mouse on second monitor, but can't move stuff on it, turns garbage.

Main question: how to get higher res for other monitor?

---

### Post by mech7 on 2008-03-11
mmm great seems a little faster then 8.2 :D getting better each time

---

### Post by lundish on 2008-03-11
i have ati 9550 and i intstalled the latest drivers.

i fallowed this instruction [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)
and everything works perfectly along with compiz

---

