---
title: "PSX (Playstation 1) Emulation With PCSX Howto"
date: 2006-04-13
forum: Tutorials
---

### Post by Kethinov on 2006-04-13
There is already a howto for doing PSX emulation with ePSXe posted [here](http://www.ubuntuforums.org/showthread.php?t=95835), however my howto may be more useful to you for the following reasons:

[LIST]
[*]PCSX is generally a more compatible emulator than ePSXe. (This is at the expense of speed. PCSX is slower than ePSXe. However, most of us have computers more than fast enough for both emulators.)
[*]PCSX has more controller configurability as it has an input plugin system whereas ePSXe is restricted to its built in controller config. (This does, however, add complexity to PCSX whereas ePSXe is simpler.)
[*]PCSX is open source software, whereas ePSXe is not.
[/LIST]

In the end they are both excellent emulators and we are lucky to have two great ones available to us in the Linux world. The choice is purely a matter of preference, and I prefer PCSX, so my guide is about PCSX!**

**Into the thick of things...**

My guide presumes the following:
[LIST]
[*]You are running Ubuntu Linux. (My guide reportedly works in Debian as well.)
[*]You have an NVIDIA card with their proprietary binary drivers installed. Sorry, ATI people. I can't help you. Anyone want to report success/failure or special configs specific for ATI people? I'll add it to the guide!
[/LIST]

**The easy way, download kethipcsx, my preconfigured PCSX package**
[list]
[*]The easy way to get up and running fast is to download my custom PCSX build designed for easy PCSX deployments on Linux systems. It contains PCSX 1.5 and every known Linux input, gpu, and spu plugin is properly installed. I compiled omnijoy for you, and I included my hidden config file patch. This package should contain everything you need to play PSX games in Linux. All you need to do is supply a BIOS image (don't ask me for one, Google is your friend...) and pick which plugins you want to use, then load a game! [Download it here](http://eric.halo43.com/downloads/kethipcsx.tar.bz2).
[/list]

**Screw you and your preconfigured package! I want to do it myself!** (Skip this section if you're just using my package.)

Okay, here's what you need to know.

[list]
[*]You will need a copy of PCSX which you can get [here](http://www.pcsx.net/).
[*]You will need Linux input, gpu, and spu plugins which you can get [from this website](http://www.ngemu.com/) (among others).
[*]When you're setting up your plugins, keep in mind there is a special thing you must do to get Pete's plugins to work correctly. You must place the plugins (the .so files) in the plugins directory, but you must place the binary configuration programs in the root emulator directory, with the emulator binary. Otherwise, the emulator cannot configure the plugins.
[*]There is a special thing you must do to get the padJoy plugin to work too. Like Pete's plugins, padJoy's config program needs to be moved somewhere (else) special. You must create a /cfg directory in your emulator's root folder. Place the plugin in the emulator's plugins folder, but place the binary configuration program in the /cfg directory you created. If you do not do this, the plugin will not work. (This is all true for Omnipad as well, should you compile it.)

[*]PCSX by default creates a configuration file in your home directory representing your settings named Pcsx.cfg. This annoyed the piss out of me, because every other UNIX program under the sun makes that a hidden file, so you never have to bloody see it there constantly. Luckily though, PCSX is open source. If you hate unhidden config files as much as I do, you can download the [PCSX source](http://www.pcsx.net/files.shtml) and replace the LnxMain.c with my [hacked version of LnxMain.c](http://sourceforge.net/tracker/index.php?func=detail&amp;aid=1115952&amp;group_id=42644&amp;atid=435782) in PcsxSrc-1.5/Linux. My hack changes the config file from Pcsx.cfg to .pcsx.cfg. Once you have replaced the LnxMain.c, simply [color=green]cd /path/to/PcsxSrc-1.5/Linux[/color] then [color=green]./configure[/color] then [color=green]make[/color]. You should get no errors doing that. If you do, you don't have gcc, libgtk or some of the other deps you need. Check the PCSX documentation for the list of deps, or you can simply download my [precompiled binary](http://eric.halo43.com/downloads/kethinovs_pcsx). Both the binary and source hack are use at your own risk stuff etc, etc, ad nauseum.
[/list]

**General Notes**
[list]
[*]I tried out all the GPU plugins thoroughly, and Pete's MesaGL Driver seems to be the fastest, most accurate, highest quality one.
[*]Unfortunately, Pete's MesaGL GPU plugin has severe issues with doing fullscreen. In the image below, PCSX is shown loading the BIOS in fullscreen mode. The red lines represent the visible screen area, proportional to the rest of my desktop. (For the record, no, this has nothing to do with my NVIDIA TwinView setup. I disabled the TwinView setup and tested it again to make sure and got the exact same results.)

(Click for full size)
[[IMG]http://eric.halo43.com/images/screenshots/2005-11-08-petes_mesagl_linux_fullscreen_bug1_thumb.jpg[/IMG]](http://eric.halo43.com/images/screenshots/2005-11-08-petes_mesagl_linux_fullscreen_bug1.jpg)

It looks like Pete's MesaGL Driver does fullscreen by simply removing the window border, maximizing the window, drawing the game screen at the desired resolution in the top left corner, changing the screen resolution, and moving the monitor viewport to the top left corner. This isn't real fullscreen, it's fake fullscreen and is subject to number of compatibility issues. For one, the gnome-panel at the top of my screen is forcing the maximized pseudo-fullscreen PCSX window down several pixels. Secondly, the viewport is not fixed. The resolution of the X11 session is still in fact 2880x1200, and you can move anywhere within this much larger real estate simply by moving the mouse. In some ways this can be an advantage though. You could use the mouse to carefully recenter the viewport over the game screen so that it's not cut off anymore. But that's annoying. And it won't work anyway... here's why:

(Click for full size)
[[IMG]http://eric.halo43.com/images/screenshots/2005-11-08-petes_mesagl_linux_fullscreen_bug2_thumb.png[/IMG]](http://eric.halo43.com/images/screenshots/2005-11-08-petes_mesagl_linux_fullscreen_bug2.png)

After PCSX is done doing its BIOS thing, Pete's MesaGL Driver moves the game screen to the bottom left of the viewport, for some odd reason. And since gnome-panel is forcing the absolutely sized PCSX window down several pixels, the bottom of the game screen is cut off once again. And this time no amount of recentering with the mouse can help you. What you can do, is move all your gnome-panels to the bottom of your screen and set them to auto hide. If you do that, then use your mouse to recenter the game screen to the bottom after you load PCSX, you can have a totally full screened PCSX with nothing cut off. Note: If you select a full screen resolution that is exactly the same as your monitor's current resolution, you won't need to recenter with the mouse. Also, if you use KDE, you shouldn't have to worry about its panel (kicker) doing this kind of stuff. But if your fullscreen resolution is smaller than your monitor's normal resolution, you will have to do the recentering stuff. Finally, another workaround you can use is to use P.E.Op.S. SoftX Driver. It does the same fake fullscreen nonsense that the Pete's MesaGL Driver does, but it also automatically (yay!) centers centers the viewport to where it needs to be, and don't pull any shenanigans on you moving the game screen around the viewport. It doesn't lock it there though. If you move the mouse while playing, you will reveal gnome-panel. See below.

[img]http://eric.halo43.com/images/screenshots/2005-11-08-petes_softx_linux_fullscreen_bug.png[/img]

Even with this, P.E.Op.S. SoftX Driver is still the much more convenient option so long as you don't touch the mouse once you go fullscreen. But personally I think Pete's MesaGL Driver looks and performs leaps and bounds better, and I'd rather play it windowed, or deal with its funny fullscreen behavior then use the more convenient, but less pretty, and slower P.E.Op.S. SoftX Driver instead.


[*]Given only two choices for SPU plugins, Eternal's and P.E.Op.S. OSS Audio Driver, I was forced to use P.E.Op.S. OSS Audio Driver when Eternal's wouldn't work. Luckily, P.E.Op.S. OSS Audio Driver works nicely. (This was tested with a Soundblaster Audigy.)
[/list]

**Troubleshooting**
[LIST]
[*]If when you try to load a plugin's config screens and they do not appear, try running it from the terminal. If the terminal output says something like [COLOR="red"]error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory[/color], then you need to [color=green]sudo apt-get install libgtk1.2[/color].
[*]If when you initially launch PCSX it says "PCSX needs to be configured" and then just closes, try running it from the terminal. If the terminal output when it closes says [COLOR="red"]libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory[/color], then you need to [color=green]sudo apt-get install libstdc++2.10-glibc2.2[/color].
[*]If you have spaces in any of your PSX BIOS files, PCSX will segfault. Remove all spaces from your PCSX BIOS files. 
[*]Last but most certainly not least, I've found that once you load a game into PCSX, if you press escape and load a different game, it will occasionally lockup X forcing you to reboot. To prevent this, if you want to load a different game, close PCSX and reopen it.
[/LIST]

**This guide is a modified version of the comprehensive Linux PSX howto [on my website](http://eric.halo43.com/linux_psx_emu.php).

---

### Post by inovermyheadd on 2006-04-21
hey, so I have the bios, and I have it all set up, but when I try to run a .bin (game) it just closes the window.  I really don't know what I'm doing wrong.

---

### Post by Kethinov on 2006-04-22
Try running PCSX from the terminal and see what error it spits out when it closes.

My guess is it's segfaulting because the format your cdimage is in can't be read by the cdr plugin, or the image is possibly corrupt. But it could be a number of things. Maybe you're missing a dependency.

---

### Post by KLineD on 2006-05-29
I hope you can help me.

I managed to get this emulator working under amd64 using the 1.5 build from pcsx page, The one that's in the repos for some reason can't read the plugins.

The only problem I have is that whenever I try to run the configuration for any of Pete's plugins I get:
> PeteMesaGL: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
However a locate libgtk-1.2.so.0 shows that it's under /usr/lib so I tried to symlink to the Plugins directory of pcsx but no luck.

With padjoy I get:
> padJoy: cannot open cfg/padJoy.cfgpadJoy: cannot open cfg/padJoy.cfg./cfg
When I start pcsx, but cfgPadJoy is in cfg directory!

Any clues?

---

### Post by Kethinov on 2006-06-05
You need the libgtk1.2 package installed. Open up Synaptic and do a search for it.

For padjoy, try making an empty file in cfg called padJoy.cfg.

---

### Post by KLineD on 2006-06-05
Thanks man, since I posted I installed x86 Dapper final (thinking it was a 64 bits related issue) and it gave me the same error. Then I found out about the libgtk1.2 lib, installed it and it all worked like you said.

So I'm already thinking into going 64 bits again, but I don't know... everything works so well here :grin:

---

### Post by BoyOfDestiny on 2006-07-07
Just as a heads up, there is a fork of pcsx, called pcsx-df. 

[http://rschultz.ath.cx/code.php#pcsx-df](http://rschultz.ath.cx/code.php#pcsx-df)

Just tested it with my SoTN (which is scratched sadly, but cdrdao still made a good bin/toc).

---

### Post by dashnak on 2006-07-09
I had problem running your package. After I configured every plugin, I clicked OK, and then PCSX segfaulted, with the following error:

> libstdc++.so.5: cannot open shared object file: The file or directory doesn't exist. Segfault.
 
This was translated from spanish.
Anyway, I solved it by installing libstdc++-5.
Just telling in case someone also runs into this.

Edit: OK, new problem here. I don't seem to be able to play a PSX CD from the drive,  it seems I need to make an image. Now, I am unable to do that. It chokes on I/O errors. So.... Any suggestions?

---

### Post by Hairy_Palms on 2006-07-09
ive been using ePSXe for ages now, i dont have enough hard disk space to ripmy games can this run the real CD's from the drive like ePSXe can?

---

### Post by BoyOfDestiny on 2006-07-10
> **Hairy_Palms said:**
> ive been using ePSXe for ages now, i dont have enough hard disk space to ripmy games can this run the real CD's from the drive like ePSXe can?

Yes.

---

### Post by Kratos on 2006-07-10
I can't seem to get PCSX to read from my CD drive. I was sure I had the plugin configured properly. But, when I try File -> Run CD ROM and select /dev/cdrom0 or /dev/hdb, it aborts.

---

### Post by sktx on 2006-07-11
howdy... i've got a few problems getting the sound to work.. it crashes and brings pcsx down when i try to open a game.. i'm running kethinovs pcsx package, with the scph1001.bin bios.  it seems i have everything but the audio config'ed fairly correctly.

but when i open up my game, using SDL it segfaults and under OSS it says that /dev/dsp is busy.  i remember running into a fix for this at some point down the line, but i can't for the life of me remember what it was, and i'm completely unable to find it on the forums.  

anyone have any ideas?

 .:://sktx//(ck)::.

---

### Post by dashnak on 2006-07-11
> **BoyOfDestiny said:**
> Yes.
And that way would be?

---

### Post by gaav on 2006-07-16
Hi, I downloaded the kethipcsx package and configured it, and when I tried to open a cd image (running in graphic mode, clicking the icon) the window opened and then closed. i then tried to run the pcsx file from the terminal and it throws out this error:
Missing ATI render-texture extension!NVIDIA Corporation
GeForce FX 5200/AGP/SSE/3DNOW!
padJoy: could not open /dev/input/js0
padJoy: pad already initialised
Then it segfaults

I have the SCPH1000.bin bios, running it from kubuntu drapper 6.06 and I configured the plugins and bios without problems...hope you can help me.

---

### Post by XVampireX on 2006-07-30
Is anyone kind enough to help me with a PSX emulator problem I'm having? No matter, be it either PCSX or ePSXe, all emulators for some reason cause movie skipping in all games... :(

---

### Post by Hairy_Palms on 2006-07-30
i still cant find a way to make this emulator run games from the cd....

---

### Post by XVampireX on 2006-07-30
You're supposed to run /dev/cdrom but who knows...

---

### Post by Hairy_Palms on 2006-07-30
yeah i know, but it doesnt work, when i try t orun /dev/hdb or /dev/cddrom it just aborts

---

### Post by Hairy_Palms on 2006-07-30
ive got to say, im not impressed with this, ill stick to ePSXe 
btw ePSXe can use all the padjoy and omnipad plugins that this can and it runs games from cdrom too this refuses to run anything but ripped games.

---

### Post by goonies on 2006-07-30
uhm, can someone please provide instructions on actually installing his custom package?

---

### Post by Hairy_Palms on 2006-07-30
u dont need to install it, just extract it then go into the directory and run the pcsx executable

---

### Post by goonies on 2006-07-30
> **gaav said:**
> Hi, I downloaded the kethipcsx package and configured it, and when I tried to open a cd image (running in graphic mode, clicking the icon) the window opened and then closed. i then tried to run the pcsx file from the terminal and it throws out this error:
Missing ATI render-texture extension!NVIDIA Corporation
GeForce FX 5200/AGP/SSE/3DNOW!
padJoy: could not open /dev/input/js0
padJoy: pad already initialised
Then it segfaults

I have the SCPH1000.bin bios, running it from kubuntu drapper 6.06 and I configured the plugins and bios without problems...hope you can help me.
```
Error: couldn't get fbconfig
Missing ATI render-texture extension!NVIDIA Corporation
GeForce FX 5200/AGP/SSE2
padJoy: could not open /dev/input/js0
padJoy: pad already initialised
Segmentation fault
```

i get a similar error =\

---

### Post by Hairy_Palms on 2006-07-30
do you have a gamepad plugged in? if not then you need to tell it not to use padjoy in the plugins i think

---

### Post by fabertawe on 2006-08-02
> **Kethinov said:**
> [*]If when you initially launch PCSX it says "PCSX needs to be configured" and then just closes, try running it from the terminal. If the terminal output when it closes says [COLOR="red"]libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory[/color], then you need to [color=green]apt-get install libstdc++2.10-glibc2.2[/color]

Hi... I'm guessing your build is i386? Apt-get reports no such file available here (all repos enabled). I'm using amd64-k8.

Cheers ... Paul

EDIT: This should be in ia32-libs (which I have) :confused:

---

### Post by fabertawe on 2006-08-04
Ok, we have lift off!

These are the steps I took to get it working on Ubuntu 6.06 amd64-k8...

Unpack Kethinov's package from the first post ([here]("http://eric.halo43.com/downloads/kethipcsx.tar.bz2") if you're really lazy ;)), thanks Kethinov :D 

From the directions on [this page]("http://pcburn.com/article.php?sid=941") I downloaded [compat-libstdc++-7.3-2.96.128.i386.rpm]("ftp://ftp.nluug.nl/pub/os/Linux/distr/startcom/ML-3.0.3/os/i386/StartCom/RPMS/compat-libstdc++-7.3-2.96.128.i386.rpm") and installed the package alien via apt-get...
```
sudo apt-get install alien
```
Turn it into a tarball to be uncompressed with
```
alien -t compat-libstdc++-7.3-2.96.128.i386.rpm
```
Extract (I did this in Nautilus)
libstdc++-3-libc6.2-2-2.10.0.so
libstdc++-libc6.2-2.so.3
from the tarball into your pcsx directory.

Next, get the following two packages
[http://packages.debian.org/stable/libs/libglib1.2 i386]("http://packages.debian.org/stable/libs/libglib1.2 i386")
[http://packages.debian.org/stable/libs/libgtk1.2 i386]("http://packages.debian.org/stable/libs/libgtk1.2 i386")
and extract
libglib-1.2.so.0
libglib-1.2.so.0.0.10
libgmodule-1.2.so.0
libgmodule-1.2.so.0.0.10
and
libgdk-1.2.so.0
libgdk-1.2.so.0.9.1
libgtk-1.2.so.0
libgtk-1.2.so.0.9.1
respectively into your pcsx directory.

I then made a shell script launcher in the pcsx directory called (surprisingly) pcsx.sh, the contents of which are
```
#!/bin/sh

pcsx_dir=/home/paul/games/emulation/pcsx

export LD_LIBRARY_PATH=$pcsx_dir:$LD_LIBRARY_PATH
cd $pcsx_dir
exec ./pcsx
```
Change 'pcsx_dir' to match your location ;)

Make sure it's executable with
```
chmod 755 pcsx.sh
```

Launch it from the terminal (opened in the pcsx directory in this example)
```
./pcsx.sh
```
and this way you can check if there are still any problems before you make a launcher.

If you have errors configuring plugins then try
```
chmod -R 755 cfg*
```
from the pcsx directory.

There's probably a more efficient way to do all this but hey, it works for me ;)

A word about Padjoy... I couldn't find much info on the config and found it a little puzzling but got my PSX pad (through a USB converter) working correctly with this padjoy.cfg...
```
[general]
pcsx_style      = 1
use_threads     = 1
use_analog      = 1
[pad 1]
devicefilename  = /dev/input/js0
minzero = -2500
maxzero = 2500
event_l2       = B0P4
event_r2       = B0P5
event_l1       = B0P6
event_r1       = B0P7
event_triangle = B0P0
event_circle   = B0P1
event_cross    = B0P2
event_square   = B0P3
event_select   = B0P8
event_lanalog  = B0P10
event_ranalog  = B0P11
event_start    = B0P9
event_up       = KP"w"
event_right    = KP"d"
event_down     = KP"s"
event_left     = KP"a"
event_lanax    = X0P0v0
event_lanay    = X0P1v0
event_ranax    = X0P3v0
event_ranay    = X0P2v0
[macro 1]
event_launch  = ???
events        =
interval      =
[macro 2]
event_launch  = ???
events        =
interval      =
[macro 3]
event_launch  = ???
events        =
interval      =
[pad 2]
devicefilename  = /dev/input/js0
minzero = -1250
maxzero = 1250
event_l2       = B1P4
event_r2       = B1P5
event_l1       = B1P6
event_r1       = B1P7
event_triangle = B1P0
event_circle   = B1P1
event_cross    = B1P2
event_square   = B1P3
event_select   = B1P8
event_lanalog  = B1P10
event_ranalog  = B1P11
event_start    = B1P9
event_up       = KP"w"
event_right    = KP"d"
event_down     = KP"s"
event_left     = KP"a"
event_lanax    = X1P0v0
event_lanay    = X1P1v0
event_ranax    = X1P3v0
event_ranay    = X1P2v0
[macro 1]
event_launch  = ???
events        =
interval      =
[macro 2]
event_launch  = ???
events        =
interval      =
[macro 3]
event_launch  = ???
events        =
interval      =
```
I have set pad 1 and 2 the same as some games seem to use port 1 and others port 2. I have also set non-analog (not the sticks) movement to use the keyboard otherwise I can't navigate the menus in QuakeII **and** use the sticks! You can alter the sensitivity of the sticks by changing the values of 'minzero' and 'maxzero'.

I hope this helps someone as it's good to give something back to these wonderful forums!

By the way... pressing F5 toggles 'Sio Irq Always Enabled' in the 'CPU' config which totally disables my contoller when ticked. This had me head scratching for a while!
 
Cheers ... Paul

---

### Post by rschultz on 2006-08-24
Hello, I'm the developer of PCSX-df and the maintainer of the PCSX and PSEmu packages in Debian (I guess no one maintains the Ubuntu ones?).

The really easy way to install it is to use Debian unstable or use Ubuntu edgy, neither of which you probably want to do. They both contain PCSX-df 1.7RC3 packages and plugins.

The PCSX in dapper is broken on Ubuntu because the Ubuntu X developers banished the lndir utility for some reason, which the PCSX environment script requires to use -- classic PCSX does not natively support a multi-user install like PCSX-df, so the script makes a little doghouse for it to live in inside your home directory. No one noticed this when PCSX was pulled into Ubuntu from Debian in the release cycle, I guess.

ePSXe is quite simply crap and shouldn't be used on any remotely modern system.

You can read the blurb about PCSX-df here: 
[http://rschultz.ath.cx/code.php](http://rschultz.ath.cx/code.php)

The highlights are: reworked and modernized GTK2/Glade GUI, a sensible plugin scanning system, a functioning gettext implementation, a modern autotooling for easy compiling and installation, GCC4 compatibility, and support for a ~/.pcsx directory for configuration data, and many fixed segfaults and minor performance issues.

PCSX-df is easy to install from source, if you don't want to try to use packages from Edgy or a Ubuntu backports site or something.

sudo apt-get build-dep pcsx-bin
wget [http://rschultz.ath.cx/code/pcsx-df-1.7rc3.tar.gz](http://rschultz.ath.cx/code/pcsx-df-1.7rc3.tar.gz)
tar xzvf pcsx-df-1.7rc3.tar.gz
cd pcsx-df-1.7rc3
./configure --prefix=/usr/local
make
sudo make install

You may want to remove any .pcsx directory in your home directory before running PCSX-df, as it will recreate this in a sane way.

The psemu-plugins that are in Dapper apt should work fine, although the edgy/Debian versions are improved, and the unreleased versions included in the pcsx-df tarball are even better, though they are still under development.

There are many plugins that cannot be included in Debian or Ubuntu due to them being closed source or badly licensed, including the hardware accelerated 3D plugins, the Eternal sound plugin, and the direct CD-ROM play plugin. I've packaged them all anyway >:3  Individual packages are available from [http://rschultz.ath.cx/debian.php;](http://rschultz.ath.cx/debian.php;) just search for "psemu-" on the page and download the .debs directly, rather than adding my archive, which is built for Debian. I suggest: psemu-video-mesagl psemu-video-xgl2 psemu-sound-eternal psemu-drive-cdrom

--------------------------------

**Here's the attention deficit version if you don't want to read everything.**

1. Install the PCSX and plugins in Dapper.
*sudo apt-get install pcsx*

2. Build PCSX-df from source.
[I]sudo apt-get build-dep pcsx-bin
wget [http://rschultz.ath.cx/code/pcsx-df-1.7rc3.tar.gz](http://rschultz.ath.cx/code/pcsx-df-1.7rc3.tar.gz)
tar xzvf pcsx-df-1.7rc3.tar.gz
cd pcsx-df-1.7rc3
./configure --prefix=/usr/local
make
sudo make install[/I]

3. Install plugins not in Debian or Ubuntu.
[I]wget 
[http://rschultz.ath.cx/debian/unstable/i386/psemu-sound-eternal_1.41-1_i386.deb](http://rschultz.ath.cx/debian/unstable/i386/psemu-sound-eternal_1.41-1_i386.deb) 
wget [http://rschultz.ath.cx/debian/unstable/i386/psemu-video-mesagl_1.75-1_i386.deb](http://rschultz.ath.cx/debian/unstable/i386/psemu-video-mesagl_1.75-1_i386.deb)
wget [http://rschultz.ath.cx/debian/unstable/i386/psemu-video-xgl2_2.5r2-1_i386.deb](http://rschultz.ath.cx/debian/unstable/i386/psemu-video-xgl2_2.5r2-1_i386.deb)
sudo dpkg -i psemu*.deb[/I]

4. Remove any classic PCSX cruft.
*rm -r ~/.pcsx/*

5. Enjoy. 
*pcsx*

It should also be available from your menu.

PCSX-df will automatically detect and pick plugins and you should be able to play right away, though you will almost certainly want to make your own choices. Use CDRmooby for ripped games, and the Linuzappz CD-ROM plugin for playing directly from the drive. Use MesaGL for minimum tweakage, or XGL2 with ATI support off for the best performance and graphics (IMO). Use the ALSA plugin unless the game sounds better with Eternal SPU.

I'll do my best to help with any problems; either email me directly (schultz dot ryan at gmail dot com), reply here, or contact me some other way ([http://rschultz.ath.cx/me.php)](http://rschultz.ath.cx/me.php)).

If anyone successfully installs PCSX-df from Edgy, please let me know; I dunno if that works, being a Debian guy.

---

### Post by Stewori on 2006-09-14
Hello all...
the lndir problem under dapper is rather easy to solve. 
Simply go to the Debian homepage and download xutils_4.3.0.dfsg.1-14sarge1_i386.deb
somewhere. You can't install that package via dpkg because there's typically a newer version of xutils installed which unfortunately doesn't include lndir.
So open xutils_4.3.0.dfsg.1-14sarge1_i386.deb whith some tar-tool like File-Roller, open the included tar named data and extract the file lndir to usr/bin. If you like you can also extract the man page (put the file called something like lndirx1.tar into some man-folder).
For me this worked - lndir is now present and the pcsx from the ubuntu-package runs under dapper.
Unfortunately the only PS-Game I tried didn't run (Spyro The Dragon for PS1). 
There anybody who got that game work? :rolleyes:

---

### Post by ammoQ on 2006-09-18
> **fabertawe said:**
> 
A word about Padjoy... I couldn't find much info on the config and found it a little puzzling but got my PSX pad (through a USB converter) working correctly with this padjoy.cfg...


I've just added a paragraph about the codes in the config file in the [FAQ page]("http://members.chello.at/erich.kitzmueller/ammoq/faq.html").

Erich aka ammoQ

---

### Post by antivert on 2006-09-24
I thought this was a good place to post this since you, the great ammoQ! :D has recently read this thread! Apparently I'm the only person this is happening to, since I haven't heard anyone else mention it. 

padJoy doesn't work for me at all. It opens its preferences window and it will accept my controller input to configure it, but when a game is launched, I get no response from the controller. It's a ps2 controller connected to usb with a very good ps2 -> pc adapter, which is recognized as a generic HID. It works in every other linux game or app I've tried it in. 

If I launch a game with padJoy selected for both controllers, I get : padJoy: pad already initialised. If I launch it with padJoy for the first controller and omniJoy with device /dev/null for the second controller, I get no error but the same result. Absolutely no response from the joystick. 

omnijoy will allow me to use my controller but it nearly immediately goes 'haywire' in-game, spastically moving around for no apparent reason. Both padJoy and omnijoy cause the main pcsx window to appear to lock up and not update video. 

I'm using the pcsx-df fork, padJoy 0.8 (both precompiled and self-compiled). It just seems a bit odd to me. All is not lost, however, as I was able to get *some* controller support working. xjoypad saves the day!! I set omnijoy to use the keyboard and use xjoypad to emulate keyboard strokes, then everything works smoothly. 

Just thought you should know! Plus, I'd really like to try padJoy's analog controller support. 

Thanks for your time.

edit: forgot to mention that I'm in Dapper. Also, I wanted to point out my main ponderances here: 

* Why does padJoy recognize my controller but then apparently not work in-game? (is it locking up?)

* Why does omnijoy go 'insane' in-game with my controller, but works fine with the keyboard? 

* Why does omnijoy go 'insane' when using my controller, but xjoypad does not? 

It's a mystery!

---

### Post by jawa83 on 2006-10-24
Hi!

I finally got PSX to work well... only to find it didn't actually work very well. I have tried both the version automatically "given" by synaptic package manager and the kethipcsx. The one from synaptic causes twitchy sound and video but the kethipcsx works fine. Both have one major problem with me, though. Neither one can use memory cards. Has anyone else experienced any problems with them?  When I tried to save the game (which happened to be Final Fantasy Tactics if that is any help) the emulator freaks out and corrupts the memory card. When I checked it on the configs there appeared to be something written in the first block. The entire card is now unreadable in the game, however. Could anyone assist?

Thank you!

---

### Post by Lystrodom on 2006-12-25
So, I've got a problem. I've gotten the PSX BIOS, but PCSX says it can't open the directory, no matter where I move it.


Edit: Turns out, I'm an idiot. I got it to accept the bios.

Anyway, now it still doesn't work. When trying to load a .bin, it just goes black for a few seconds, and then closes. Any ideas?

---

### Post by outphase on 2006-12-27
I've been wanting to make PSX isos with my Ubuntu machine, but whenever I insert the CD, it doesn't read it unlike windows which at least lets me browse the directories. Any ideas?

---

### Post by Simon-v on 2007-02-23
PCSX-df installs and runs pretty well from Synaptic, needing only minor tweaking. Yet, i am experiencing the same memory card (not) saving problem as described above and in [another thread]("http://www.ubuntuforums.org/showthread.php?t=341087") on the forums.

---

### Post by Arlanthir on 2007-03-31
EDIT: Nevermind, I was doing the wrong thing :P

---

### Post by RobinOfSweden on 2007-04-22
Greetings peps!
Another one bites the dust i guess. I am using Ubuntu 6.10 Edgy amd64 system and i tried the Synaptic version of PCSX-df and ... well what to say, i have nothing to configure >_<
Tried to find the config files to see if there was something i could edit myself but with total failure.

Using GamePad Pro (Gravis) as a joypad and i have a dev/js0 made (works fine with snes9x) however i cant seem to save this setting for the pcsx (cant even find the config file). I get the error for "not finding padjoy" when i start pcsx from terminal so i think the problem could be solved by doing a install from src (i atleast hope to get some config files).

Anyway this post was to let people know that Edgy 6.10 amd64 install through Synaptic didnt work for me =) (the game starts and i think it should be possible to get it running).
Oh well i will be back with news on the other 2 types of installation! (Kethipcsx and src install from pcsx-df)

**Edit**
Ok tried the Kethi installation and unlike my own source installation things seems to work
until i try to load a game. When it tries to load a game i recieve this message though the only thing i can get out of it seems to be something with my graphic driver...
Anyway hope it is of some use to people out there =) (with the scph1001.bin BIOS)

```

(<unknown>:14501): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
cfg/cfgPadJoy: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

(process:14519): Gdk-WARNING **: locale not supported by C library

(cfgOmniJoy:14519): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
OmniJoy Init: You are using v1.0.0 build 8
Error: couldn't get an RGBA, double-buffered visual
XRequest.143: BadValue (integer parameter out of range for operation) 0x9802
XRequest.143: BadMatch (invalid parameter attributes) 0x9802
Missing ATI render-texture extension!NVIDIA Corporation
GeForce 7900 GT/GTO/PCI/SSE2
OmniJoy: Using Joystick Gravis GamePad Pro USB  for controller 1
Segmentation fault (core dumped)

```

I tried other GPU's (Pete's Mesa and Pete's XGL2 etc) and i kept recieving this part when trying to open a game.
```

(<unknown>:14975): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
OmniJoy Init: You are using v1.0.0 build 8
libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
OmniJoy: Using Joystick Gravis GamePad Pro USB  for controller 1
Segmentation fault (core dumped)

```

I also tried to edit the GPU's with configure in the settings section and i recieved this message on all of them:
```

./cfg<name of GPU>: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

```

Oh and side note, my Gravis GamePad PRO doesnt work with PadJoy so i used OmniJoy which atleast doesnt complain and knows my gamepad
**End Edit**

Regards RobinOfSweden

---

### Post by the_it on 2007-05-16
after banging my head on the table for a while, I seem to be able to get it to work.  However, I'm an AMD64 user, (tooks me a while to figure out how to get the 32bit libstdc++), and I get THIS everytime I try to config pete's open source stuff.

> ./cfgPeteMesaGL: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

No windows popup, so I can't configure anything using the interface.

My workaround is to edit those things by hand, but is there a more elegant solution?

---

### Post by b4d on 2007-11-20
Hi, I am wondering how to make my keyboard work. If i put /dev/input/ts0 like I saw in one of the posts, it still does not work. Thanks in advance

---

### Post by jerome1232 on 2008-04-17
ok it seems to install just fine, I can open pcsx up, i've copied my video and sound plugins into the plugins directory etc...

when I goto select which plugin i want to use terminal spits out```
$ pcsx
symlink: /home/jeremy/.pcsx/pluginscfg -> /home/jeremy/.pcsx/plugins/cfg
symlink: /home/jeremy/.pcsx/pluginscfg -> /home/jeremy/.pcsx/plugins/cfg/cfg
symlink: /home/jeremy/.pcsx/pluginslibgpuPeteXGL2.so.2.0.8 -> /home/jeremy/.pcsx/plugins/libgpuPeteXGL2.so.2.0.8
symlink: /home/jeremy/.pcsx/pluginslibspuEternal.so.1.41 -> /home/jeremy/.pcsx/plugins/libspuEternal.so.1.41
unlink: /home/jeremy/.pcsx/plugins/cfg/cfg
/home/jeremy/.pcsx/plugins/libgpuPeteXGL2.so.2.0.8: wrong ELF class: ELFCLASS32
/home/jeremy/.pcsx/plugins/libspuEternal.so.1.41: wrong ELF class: ELFCLASS32

(<unknown>:21182): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(<unknown>:21182): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed
/home/jeremy/.pcsx/plugins/libgpuPeteXGL2.so.2.0.8: wrong ELF class: ELFCLASS32
/home/jeremy/.pcsx/plugins/libspuEternal.so.1.41: wrong ELF class: ELFCLASS32

(<unknown>:21182): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(<unknown>:21182): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed
symlink: /home/jeremy/.pcsx/plugins/cfg -> /home/jeremy/.pcsx/plugins/cfg
symlink: /home/jeremy/.pcsx/plugins/cfg -> /home/jeremy/.pcsx/plugins/cfg/cfg
symlink: /home/jeremy/.pcsx/plugins/libgpuPeteXGL2.so.2.0.8 -> /home/jeremy/.pcsx/plugins/libgpuPeteXGL2.so.2.0.8
symlink: /home/jeremy/.pcsx/plugins/libspuEternal.so.1.41 -> /home/jeremy/.pcsx/plugins/libspuEternal.so.1.41
/home/jeremy/.pcsx/plugins/libgpuPeteXGL2.so.2.0.8: wrong ELF class: ELFCLASS32
/home/jeremy/.pcsx/plugins/libspuEternal.so.1.41: wrong ELF class: ELFCLASS32
picking default GPU plugin: 
picking default SPU plugin: 
picking default CD-ROM plugin: 
picking default Controller 1 plugin: 
picking default Controller 2 plugin: 

(<unknown>:21182): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(<unknown>:21182): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

```
I have no idea what this ELFCLASS stuff it's complaining about means.

i've tried multiple plugins (all from ngemu) and i get the same stuff, i did enable backports and downloaded the pcsx-df package, when it opens i has the pre downloaded plugins selected but i have no iso to do a test run, the ps1 disc doesn't seem to mount so that i can make an iso either EDIT: btw Ubuntu 7.10 x86_64

---

### Post by Lee83 on 2008-11-02
i know this question has been asked a handful of times on this thread but with no answer,why oh why does every rom i try not work when trying to load from image file,are they in the wrong extension or something i.e should be .iso???? i also get the black screen then shutdown,although on a couple of occasions i have had the error cd failed?? what that means i dont know,as no cd is present of the physical sense...HELP !!!!! :P

---

### Post by kiloraw on 2008-12-23
Whats the command for the terminal, for PCSX? I tried finding it. Sorry for the dumb question.

---

### Post by Trixilver on 2009-02-04
How do I configure Pete's plugins? The OP says:

*When you're setting up your plugins, keep in mind there is a special thing you must do to get Pete's plugins to work correctly. You must place the plugins (the .so files) in the plugins directory, but you must place the binary configuration programs in the root emulator directory, with the emulator binary. Otherwise, the emulator cannot configure the plugins.*

But I don't understand the two most important parts:

**A)** What are the 'binary configuration programs'?
and
**B)** Where is the 'root emulator directory'?

---

### Post by Cloud x blue on 2009-04-09
Everytime i double click on pcsx it doesnt open up and even if i type it in terminal nothing happens i just get file does not exist.. how could i of messed this up

---

### Post by araxhiel on 2009-05-04
Well, I Read some solutions to connect a PSX Controller to Ubuntu through a USB conection... but.. I have a PSX --> Serial Port adapter (a veeeeeeeeeeeeeeeeeeery old adapter) and I can't make it works... (I can't find any PS-->USB adapter yet)

Any Idea to make work my Controller?

(BTW... In winbugs the controller works fine)

----------
My System

Ubuntu Intrepid Ibex 8.10
GNOME: 2.24.1 (Ubuntu 2008-10-24)
Kernel version: 2.6.27-11-generic (#1 SMP Wed Apr 1 20:57:48 UTC 2009)
GCC: 4.3.2 (i486-linux-gnu)
Xorg: 7.3 (or 7.4? :confused: whops) (09 March 2009  10:48:54AM)
Motherboard Details:
    Host bridge
        ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
        Subsystem: Hewlett-Packard Company Device 2a3d
    PCI bridge(s)
        ATI Technologies Inc RS480 PCI Bridge
        ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01)
        ATI Technologies Inc RS480 PCI Bridge
        ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01)
    USB controller(s)
        ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10)
        ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10)
        ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20)
        ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10)
        ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10)
        ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20)
    ISA bridge
        ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
    IDE interface
        ATI Technologies Inc IXP SB400 IDE Controller (rev 80) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company Device 2a3d

---

### Post by Duskao on 2009-10-20
I'm having issues with configuring my controller. I have a Logitech Dual Action game pad. I managed to configure it fine with pSX, but I prefer pcsx or epsxe (can't get epsxe to work).

---

### Post by Cenoforums on 2009-12-03
Is anyone having audio issues with this? I tried disabling pulseaudio but it did nothing, the sound is absolutely choppy. I had the same problem with mugen64plus...

---

### Post by synapticnode on 2009-12-31
yeah now i'm kinda sorry i chose the "screw you" option,
i have the same trouble as trixilver about misunderstanding placement of Pete's plugins.

"*When you're setting up your plugins, keep in mind there is a special thing you must do to get Pete's plugins to work correctly. You must place the plugins (the .so files) in the plugins directory, but you must place the binary configuration programs in the root emulator directory, with the emulator binary. Otherwise, the emulator cannot configure the plugins."*

Could someone explain the exact placement of the files? Does the "root emulator dir" mean the "program dir" ,where the program resides or perhaps the .pcsx folder? --to name a few questions...

---

### Post by citaworvk on 2010-06-11
Same problem as trixilver and synapticnode.
It was a bit of a problem even finding the cfgPeteXGL2

---

### Post by benmoran on 2010-06-11
Give PCSX-Reloaded a try. It's a fork, so some things are different. The Joystick setup and all the plugins come with it, so IMO it's way easier to use and set up. 

[http://pcsxr.codeplex.com/](http://pcsxr.codeplex.com/)

---

### Post by citaworvk on 2010-06-11
I am using Pcsx reloaded, but if you use the pete's plugin xgl2 everthing works better. I just can't configure it after I use the plugin.

---

### Post by jonasg on 2010-06-13
> **rschultz said:**
> 
1. Install the PCSX and plugins in Dapper.
*sudo apt-get install pcsx*

2. Build PCSX-df from source.
[I]sudo apt-get build-dep pcsx-bin
wget [http://rschultz.ath.cx/code/pcsx-df-1.7rc3.tar.gz](http://rschultz.ath.cx/code/pcsx-df-1.7rc3.tar.gz)
tar xzvf pcsx-df-1.7rc3.tar.gz
cd pcsx-df-1.7rc3
./configure --prefix=/usr/local
make
sudo make install[/I]



Can i just modify /etc/apt/sources.list and add the old dapper repository?
For the record I'm running Lucid right now.

---

### Post by Mazukambax on 2010-06-16
...

---

### Post by Sly Cooper on 2011-01-18
Hey, so I just set up PCSX on my 10.10 Ubuntu machine.
I have all the pluggins and the Bios, but I can't get the sound working.

If anyone can help me, please let me know ASAP and I'll send you anymore information that you may need.

---

### Post by robrocks07 on 2011-01-29
ive gotten kethipcsx up and running everything is set configures etc

i try to load ff7 .bin file and it flashes a black screen and poof its gone

heres what happens in terminal

> robert@robert:~/Downloads/kethipcsx/pcsx$ ./pcsx
Sound device not available!
NVIDIA Corporation
GeForce 8200M G/PCI/SSE2
padJoy: could not open /dev/input/js3
padJoy: pad already initialised
Segmentation fault

and it used to do this after i messed with different plugins

> robert@robert:~/Downloads/kethipcsx/pcsx$ ./pcsx
OmniJoy Init: You are using v1.0.0 build 8
Sound device not available!
Error OmniJoy Controller 1: No such file or directory
Segmentation fault
robert@robert:~/Downloads/kethipcsx/pcsx$ ./pcsx
OmniJoy Init: You are using v1.0.0 build 8
Sound device not available!
Error OmniJoy Controller 1: No such file or directory
Error OmniJoy Controller 2: No such file or directory
Segmentation fault

plugins im using are:
P.E.Op.S. OSS Audio Driver 1.1.8
ammoQ's padJoy Joy Device Driver 1.0.8
P.E.Op.S. MesaGL Driver 1.1.78
Mooby2 cd disk image driver 1.2.8

i swapped out petes for peops plugins a forum post told me they work a little better not sure cant get a game up so help me out here

---

### Post by itachi12596 on 2011-10-10
Not sure if this is the right place to ask this, but while playing a game, certain events seem to have already occured, despite me having just started a new game. What could cause this problem?

---

### Post by AJellyDonut on 2012-06-17
i'm running ubuntu 12.04 and i got the preconfigured thing, i think i have the stuff i need to run it too but it says it can't open or read my CDR plugin /PLUGIN and that it can't open to any of my bios :confused:

---

