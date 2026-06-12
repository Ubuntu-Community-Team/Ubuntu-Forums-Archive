---
title: "Skype in Precise"
date: 2012-01-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by clivejo on 2012-01-05
I know this is at the bottom of most peoples list of important issues, but I just wondered if anyone had got Skype working in Precise?

I'm getting the following error :

skype: error while loading shared libraries: libXv.so.1

---

### Post by ronacc on 2012-01-05
I searched launchpad and didn't see that one reported so report it , that is the way to get it fixed .

---

### Post by clivejo on 2012-01-05
Its working now.

Removed Skype, cleaned out old files (as I upgraded from 11.10), installed all updated packages and installed Skype.

---

### Post by chmac on 2012-01-08
I did a fresh install of precise and had real hassles getting skype to work. I wrote up the steps I needed to get it working in the hope it'll save somebody else the hassle:
[http://www.callum-macdonald.com/2012/01/08/skype-in-ubuntu-precise-alpha/](http://www.callum-macdonald.com/2012/01/08/skype-in-ubuntu-precise-alpha/)

---

### Post by adyroman on 2012-02-16
The solution above no longer works. There are a number of packages that have already been updated and, at the time of this post, "apt-get -f install" suggests removing almost everything, including apt itself.

I was able to make Skype work by downloading the statically linked version off the Skype website. I took libXss.so.1.0.0 from libxss1:i386, copied it to /usr/lib32 and symlinked it there as libXss.so.1. Then started Skype. Needless to say, this is seriously borked and needs to be fixed the right way.

---

### Post by chmac on 2012-02-16
Glad you got it working. Skype still works for me, but I have to ignore ia32libs every time I update or it wants to install half the world. :-)

You downloaded the skype version labelled "statically linked" from skype.com, then downloaded the libxss1:i386 package (presumably from packages.ubuntu.com) and then opened it with archive explorer (or whatever the thing is called) and copied the libXss.so.1.0.0 to /usr/lib32, is that correct?

Sounds like an easier route than me, I wonder if I can un-install all that other stuff and go your way instead. Does skype work well for you?

---

### Post by adyroman on 2012-02-19
It seems to work fine. Well, as "fine" as Skype can work, I've had trouble with it on Lucid as well, and it was installed from the partner repos there.

I'm not sure that the installation is as simple as you stated it though. I first tried it your way, and some of the packages you mentioned were installed, others were not. Atm, I have 232 i386 packages on an AMD64 system, so I'm not sure it's as easy as I made it sound in my previous post. I meant it to be complementary to your instructions, not as another installation path. :)

[INDENT][FONT="Courier New"]adyroman@HyperPrecise:~$ dpkg -l | grep i386 | wc -l
232
adyroman@HyperPrecise:~$ uname -a
Linux HyperPrecise 3.2.0-17-generic #26-Ubuntu SMP Fri Feb 17 21:35:49 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
adyroman@HyperPrecise:~$[/FONT][/INDENT]

---

### Post by williammanda on 2012-02-19
Wonder when the proper deb will be available?

---

### Post by adyroman on 2012-02-21
Yesterday I installed Xubuntu on a test system. I downloaded skype-static and when I tried to run it, it didn't work because it was a 32-bit executable on a 64-bit system. So I installed ia32-libs from the repository with apt-get (which worked just fine, and installed a bunch of other i386 packages) and then skype-static worked ok.

Now I returned to Ubuntu and uninstalled the older version of ia32-libs with "apt-get purge ia32-libs", deleted libXss.1.0.0 and the symlink from /usr/lib32, installed the latest version of ia32-libs from the repository with "apt-get install ia32-libs" and installed the AMD64 Skype deb and it works. I suspect whatever conflict there was before with the libraries, it has been solved in the meantime.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-02-21
While testing Precise Alpha 1, I had some dependencies issues which resulted in Skype being uninstalled without a possibility to reinstall it. However, after a clean install of Precise Alpha 2 and system update, Skype works fine again.

I have a different problem with Skype. Non-latin (Cyrillic) text everywhere (Contacts' names, Menu options etc.) are displayed in a very ugly and small font, with Serbian specific letters (&#1113;,&#1114;,&#1106;,&#1112;,&#1115;,&#1119;) missing. Only empty boxes instead. How do I change font in Skype?

---

### Post by pressureman on 2012-02-21
I'm running Skype ok on Precise amd64. Don't install ia32-libs - that method is outdated. Use the multiarch method instead.

```

echo foreign-architecture i386 | sudo tee /etc/dpkg/dpkg.cfg.d/multiarch 
apt-get update
apt-get install skype

```

Maybe that should go in the Ubuntu wiki somewhere.

I do still find Skype a bit crashy - sometimes I have to start it 2 or 3 times before it's stable, but it's usually ok from there. Occasionally it will freeze at the end of a call, but can be restarted ok.

One thing I did notice that stopped working recently was the self-video picture-in-picture during a video call (eg. the small preview of what your webcam sees). The other person sees my video fine, but it just makes it difficult to know whether you're sitting in the right place to ensure a good image.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-02-21
It is buggy, indeed. My Skype also doesn't show an icon on the top panel. So if I click on "close" button, it will keep running, but its window will disappear. No way to restore it back unless kill the process from System Monitor and start it up again.

---

### Post by chmac on 2012-02-21
&#1058;&#1086;&#1084;&#1080;&#1094;&#1072;, You need to whitelist the icon in the new Unity dash. There's some info that might get you started on that [here]("http://ubuntuforums.org/showthread.php?t=1861843#p11353038").

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-02-21
chmac thanks for the info. Didn't know it's a known issue. Unfortunately, none of the things from the other thread helped me. I still can't get Skype icon in the top panel. Maybe I should restart my computer first...

Edit: Correction. It does work after log off / log on. Thanks. It's strange though, because it worked out of the box in my earlier installations of Oneiric and Precise.

---

### Post by chmac on 2012-02-21
&#1058;&#1086;&#1084;&#1080;&#1094;&#1072;, I believe you will have to restart your session (logout, login) but a reboot probably won't do any harm.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-02-21
> **chmac said:**
> &#1058;&#1086;&#1084;&#1080;&#1094;&#1072;, I believe you will have to restart your session (logout, login) but a reboot probably won't do any harm.

Yep, works fine now. Thanks. Now just to fix the other 49 problems I'm having with Skype :)

---

### Post by rajeev1204 on 2012-02-22
> **&#1058 said:**
> It is buggy, indeed. My Skype also doesn't show an icon on the top panel. So if I click on "close" button, it will keep running, but its window will disappear. No way to restore it back unless kill the process from System Monitor and start it up again.


Same here. No way to tell if it is running. Except from the system monitor.

---

### Post by Whoopie on 2012-02-22
Have you whitelisted Skype in the systray as explained [here]("http://www.webupd8.org/2011/04/how-to-re-enable-notification-area.html") ?

---

### Post by balloons on 2012-02-22
> **pressureman said:**
> I'm running Skype ok on Precise amd64. Don't install ia32-libs - that method is outdated. Use the multiarch method instead.

```

echo foreign-architecture i386 | sudo tee /etc/dpkg/dpkg.cfg.d/multiarch 
apt-get update
apt-get install skype

```

Maybe that should go in the Ubuntu wiki somewhere.

I do still find Skype a bit crashy - sometimes I have to start it 2 or 3 times before it's stable, but it's usually ok from there. Occasionally it will freeze at the end of a call, but can be restarted ok.

One thing I did notice that stopped working recently was the self-video picture-in-picture during a video call (eg. the small preview of what your webcam sees). The other person sees my video fine, but it just makes it difficult to know whether you're sitting in the right place to ensure a good image.

Wow.. this whole time skype had been installed then uninstalled by an upgrade on my precise install and I couldn't get it back. Thanks, this worked very nicely.

---

### Post by chmac on 2012-02-22
Where are you getting skype from? There's not yet a version for precise in the Canonical partner repos as far as I can tell [here]("http://archive.canonical.com/ubuntu/pool/partner/s/skype/").

I just uninstalled ia32-libs as suggested, but `sudo apt-get install skype` I get:
> dpkg: dependency problems prevent configuration of skype:
 skype depends on ia32-libs; however:
  Package ia32-libs is not installed.

---

### Post by pressureman on 2012-02-22
> **chmac said:**
> Where are you getting skype from? There's not yet a version for precise in the Canonical partner repos as far as I can tell [here]("http://archive.canonical.com/ubuntu/pool/partner/s/skype/").

I just uninstalled ia32-libs as suggested, but `sudo apt-get install skype` I get:

The partner repos usually don't get flipped over until very late in the beta testing. Until then you'll have to use the oneiric version. Ensure that both oneiric and precise partner repos are in your /etc/apt/sources.list:

```

deb http://archive.canonical.com/ubuntu oneiric partner
deb http://archive.canonical.com/ubuntu precise partner

```

I don't know why your system wants to pull in ia32-libs. I don't have it installed on my system, and indeed skype no longer depends on it:

```

daniel@thinkpad:~$ apt-cache depends skype
skype:i386
  Depends: libasound2:i386
  Depends: libc6:i386
  Depends: libgcc1:i386
  Depends: libqt4-dbus:i386
  Depends: libqt4-network:i386
  Depends: libqtcore4:i386
  Depends: libqtgui4:i386
  Depends: libstdc++6:i386
  Depends: libx11-6:i386
  Depends: libxext6:i386
  Depends: libxss1:i386
  Depends: libxv1:i386
  Recommends: sni-qt:i386
  Conflicts: <skype-common>
  Conflicts: <skype-common:i386>
  Conflicts: <skype-mid>
  Conflicts: <skype-mid:i386>
  Replaces: <skype-common>
  Replaces: <skype-common:i386>
  Replaces: <skype-mid>
  Replaces: <skype-mid:i386>

```

Maybe you should uninstall skype and reinstall it. You may have the amd64 package of it, which used to depend on ia32-libs. You need to install the i386 package of it, which will then pull in the i386 packages shown above.

If you don't see a ":i386" after the package name skype in 'dpkg -l', then you have the old amd64 package.

---

### Post by cariboo on 2012-02-22
The partner repository won't be updated to Precise, until after it's release, so I use the Oneiric repository, and just install skype-i386. The 64-bit version is just a kludge of the 32-bit version anyhow. That's what multiarch is for, to allow you to install 32-bit applications on a 64-bit system.

If you open the 64-bit .deb with file-roller, then open /DEBIAN/control, you'll see that it depends on 32-bit libraries.

> Package: skype
Version: 2.2.0.35-1
Section: non-free/net
Priority: extra
Architecture: amd64
Depends: lib**32**stdc++6 (>= 4.1.1-21), lib**32**asound2 (>> 1.0.14), ia**32**-libs, libc6-i**386** (>= 2.7-1), lib**32**gcc1 (>= 1:4.1.1-21+ia**32**.libs.1.19)
Installed-Size: 28722
Maintainer: Skype Technologies <info@skype.net>
Description: Skype
 .
 Skype is software that enables the world's conversations.
 Millions of individuals and businesses use Skype to make free video and voice calls,
 send instant messages and share files with other Skype users.
 Everyday, people also use Skype to make low-cost calls to landlines and mobiles.
 .
 * Make free Skype-to-Skype calls to anyone else, anywhere in the world.
 * Call to landlines and mobiles at great rates.
 * Group chat with up to 200 people or conference call with up to 25 others.
 * Free to download.

---

### Post by psych1610 on 2012-03-09
Can someone lend me a hand? Here's what I've done. 

Add the multi-arch file as suggested here: ```
echo foreign-architecture i386 | sudo tee /etc/dpkg/dpkg.cfg.d/multiarch 
apt-get update
apt-get install skype
```

and updated. (Did not install skype yet). I then added the Oneiric partner repository as suggested and tried to install Skype.

No matter if Skype is downloaded from its own website (the 10.04 32 bit version) or from Oneiric I'm either left with it wanting to remove things like Unity2d and a bunch of qt4 and Ubuntu One packages, or I'm left with dependency errors that don't seem to be resolvable. 

Can anyone post a brief step by step that works for them.

---

### Post by cariboo on 2012-03-09
Do you get the same thing if you try to install skype-i386?

---

### Post by psych1610 on 2012-03-09
Hi, thanks very much for the response. Right as I was checking to see if there were any answers here I seem to have solved it. I disabled the Oneiric partner repo, left the multi arch file in dpkg.cfg.d, and attempted to install the 10.04 i386 build from Skype. It hasn't asked to remove anything and looks to be adding a whole bunch of *:i386 libs to my system. 

It seems that's what is supposed to be happening. Install Skype i386 on 64 bit system without the ia32 libraries.

If this works out I'll consider it solved.

Edit: I know I said I had done that before, but maybe it was the addition of the Oneiric repository that was throwing it off.

---

### Post by CsabaBo on 2012-04-16
I upgraded my 64 bit kubuntu to Precise. Could apt-get install skype but now just after starting skype it is minimised and is getting it's icon green and when I click it to see my partners, it's crashing the Xserver.

This is happening with the downloaded static version also, all the time.

I use Nvidia drivers for X and two monitors in TwinView configuration.

Anyone got this problem? 

How do I start to troubleshoot it? (No logs...)

---

### Post by chmac on 2012-04-16
If you start skype from a terminal you might get debugging output. :-)

---

### Post by CsabaBo on 2012-04-17
Here it is how I logged the crash:

. Stopped kdm.
. startx &
. export DISPLAY=localhost:0.0
. skype
. switched to the Xorg's terminal, click on the skype's greened notification icon. Crash happened:

```
bcs@ubacs:~$ startx
X.Org X Server 1.11.3
Release Date: 2011-12-16
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
Current Operating System: Linux ubacs 3.2.0-23-generic #36-Ubuntu SMP Tue
Apr 10 20:39:51 UTC 2012 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic
root=UUID=2105d6f1-e59e-443d-af60-619a9dfc4a50 ro
Build Date: 05 April 2012  04:32:37AM
xorg-server 2:1.11.4-0ubuntu10 (For technical support please see
http://www.ubuntu.com/support)
Current version of pixman: 0.24.4
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Apr 17 20:09:47 2012
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Symbol map for key <RALT> redefined
>                   Using last definition for conflicting fields
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server

bcs@ubacs:~$ export DISPLAY=localhost:0.0
bcs@ubacs:~$ skype
xcb_connection_has_error() returned true

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x26) [0x7fbd689cc2d6]
1: /usr/bin/X (0x7fbd68844000+0x18c17a) [0x7fbd689d017a]
2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7fbd67b6a000+0xfcb0)
[0x7fbd67b79cb0]
3: /usr/bin/X (doListFontsWithInfo+0x10b) [0x7fbd6889319b]
4: /usr/bin/X (ProcessWorkQueue+0x21) [0x7fbd68896991]
5: /usr/bin/X (WaitForSomething+0x65) [0x7fbd689c9585]
6: /usr/bin/X (0x7fbd68844000+0x4e4b2) [0x7fbd688924b2]
7: /usr/bin/X (0x7fbd68844000+0x3d68a) [0x7fbd6888168a]
8: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7fbd669ff76d]
9: /usr/bin/X (0x7fbd68844000+0x3d97d) [0x7fbd6888197d]
Segmentation fault at address 0x10

Caught signal 11 (Segmentation fault). Server aborting

Please consult the The X.Org Foundation support
         at http://wiki.x.org
 for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional
information.

 ddxSigGiveUp: Closing log
Server terminated with error (1). Closing log file.
xinit: connection to X server lost
bcs@ubacs:~$

```

"/var/log/Xorg.0.log" contents:


```
[   839.871] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[   839.877] X Protocol Version 11, Revision 0
[   839.878] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[   839.880] Current Operating System: Linux ubacs 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64
[   839.882] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic root=UUID=2105d6f1-e59e-443d-af60-619a9dfc4a50 ro
[   839.884] Build Date: 05 April 2012  04:32:37AM
[   839.886] xorg-server 2:1.11.4-0ubuntu10 (For technical support please see http://www.ubuntu.com/support) 
[   839.887] Current version of pixman: 0.24.4
[   839.889] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   839.892] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   839.896] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Apr 17 20:15:13 2012
[   839.897] (==) Using config file: "/etc/X11/xorg.conf"
[   839.898] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   839.900] (==) ServerLayout "Layout0"
[   839.900] (**) |-->Screen "Screen0" (0)
[   839.900] (**) |   |-->Monitor "Monitor0"
[   839.900] (**) |   |-->Device "Device0"
[   839.900] (**) |-->Input Device "Keyboard0"
[   839.900] (**) |-->Input Device "Mouse0"
[   839.900] (**) Option "Xinerama" "0"
[   839.900] (==) Automatically adding devices
[   839.900] (==) Automatically enabling devices
[   839.900] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   839.900] 	Entry deleted from font path.
[   839.900] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   839.900] 	Entry deleted from font path.
[   839.900] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   839.900] 	Entry deleted from font path.
[   839.900] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   839.900] 	Entry deleted from font path.
[   839.900] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   839.900] 	Entry deleted from font path.
[   839.900] (**) FontPath set to:
	unix/:7100,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[   839.900] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   839.900] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[   839.900] (WW) Disabling Keyboard0
[   839.900] (WW) Disabling Mouse0
[   839.900] (II) Loader magic: 0x7f53d2229b00
[   839.900] (II) Module ABI versions:
[   839.900] 	X.Org ANSI C Emulation: 0.4
[   839.901] 	X.Org Video Driver: 11.0
[   839.901] 	X.Org XInput driver : 16.0
[   839.901] 	X.Org Server Extension : 6.0
[   839.901] (--) PCI:*(0:1:0:0) 10de:06e4:1458:34ed rev 161, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/131072
[   839.901] (II) Open ACPI successful (/var/run/acpid.socket)
[   839.901] (II) LoadModule: "extmod"
[   839.902] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   839.902] (II) Module extmod: vendor="X.Org Foundation"
[   839.902] 	compiled for 1.11.3, module version = 1.0.0
[   839.902] 	Module class: X.Org Server Extension
[   839.902] 	ABI class: X.Org Server Extension, version 6.0
[   839.902] (II) Loading extension MIT-SCREEN-SAVER
[   839.902] (II) Loading extension XFree86-VidModeExtension
[   839.902] (II) Loading extension XFree86-DGA
[   839.902] (II) Loading extension DPMS
[   839.902] (II) Loading extension XVideo
[   839.902] (II) Loading extension XVideo-MotionCompensation
[   839.902] (II) Loading extension X-Resource
[   839.902] (II) LoadModule: "dbe"
[   839.902] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   839.902] (II) Module dbe: vendor="X.Org Foundation"
[   839.902] 	compiled for 1.11.3, module version = 1.0.0
[   839.902] 	Module class: X.Org Server Extension
[   839.902] 	ABI class: X.Org Server Extension, version 6.0
[   839.902] (II) Loading extension DOUBLE-BUFFER
[   839.902] (II) LoadModule: "glx"
[   839.902] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[   839.916] (II) Module glx: vendor="NVIDIA Corporation"
[   839.916] 	compiled for 4.0.2, module version = 1.0.0
[   839.916] 	Module class: X.Org Server Extension
[   839.916] (II) NVIDIA GLX Module  295.40  Thu Apr  5 21:57:38 PDT 2012
[   839.916] (II) Loading extension GLX
[   839.916] (II) LoadModule: "record"
[   839.916] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   839.916] (II) Module record: vendor="X.Org Foundation"
[   839.916] 	compiled for 1.11.3, module version = 1.13.0
[   839.916] 	Module class: X.Org Server Extension
[   839.916] 	ABI class: X.Org Server Extension, version 6.0
[   839.916] (II) Loading extension RECORD
[   839.916] (II) LoadModule: "dri"
[   839.917] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   839.917] (II) Module dri: vendor="X.Org Foundation"
[   839.917] 	compiled for 1.11.3, module version = 1.0.0
[   839.917] 	ABI class: X.Org Server Extension, version 6.0
[   839.917] (II) Loading extension XFree86-DRI
[   839.917] (II) LoadModule: "dri2"
[   839.917] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   839.917] (II) Module dri2: vendor="X.Org Foundation"
[   839.917] 	compiled for 1.11.3, module version = 1.2.0
[   839.917] 	ABI class: X.Org Server Extension, version 6.0
[   839.917] (II) Loading extension DRI2
[   839.917] (II) LoadModule: "nvidia"
[   839.917] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[   839.918] (II) Module nvidia: vendor="NVIDIA Corporation"
[   839.918] 	compiled for 4.0.2, module version = 1.0.0
[   839.918] 	Module class: X.Org Video Driver
[   839.918] (II) NVIDIA dlloader X Driver  295.40  Thu Apr  5 21:38:35 PDT 2012
[   839.918] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   839.918] (--) using VT number 8

[   839.923] (II) Loading sub module "fb"
[   839.923] (II) LoadModule: "fb"
[   839.924] (II) Loading /usr/lib/xorg/modules/libfb.so
[   839.924] (II) Module fb: vendor="X.Org Foundation"
[   839.924] 	compiled for 1.11.3, module version = 1.0.0
[   839.924] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   839.924] (II) Loading sub module "wfb"
[   839.924] (II) LoadModule: "wfb"
[   839.924] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   839.924] (II) Module wfb: vendor="X.Org Foundation"
[   839.924] 	compiled for 1.11.3, module version = 1.0.0
[   839.924] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   839.924] (II) Loading sub module "ramdac"
[   839.924] (II) LoadModule: "ramdac"
[   839.924] (II) Module "ramdac" already built-in
[   839.924] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[   839.924] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   839.924] (II) Loading /usr/lib/xorg/modules/libfb.so
[   839.924] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[   839.924] (==) NVIDIA(0): RGB weight 888
[   839.924] (==) NVIDIA(0): Default visual is TrueColor
[   839.924] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   839.924] (**) NVIDIA(0): Option "NoLogo" "True"
[   839.924] (**) NVIDIA(0): Option "TwinView" "1"
[   839.924] (**) NVIDIA(0): Option "MetaModes" "CRT: nvidia-auto-select +0+150, DFP: nvidia-auto-select +1680+0"
[   839.924] (**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "CRT-1"
[   839.925] (**) NVIDIA(0): Enabling 2D acceleration
[   841.039] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (CRT-1)) does not support NVIDIA
[   841.039] (II) NVIDIA(GPU-0):     3D Vision stereo.
[   841.107] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[   841.107] (II) NVIDIA(GPU-0):     3D Vision stereo.
[   841.109] (II) NVIDIA(0): NVIDIA GPU GeForce 8400 GS (G98) at PCI:1:0:0 (GPU-0)
[   841.109] (--) NVIDIA(0): Memory: 524288 kBytes
[   841.109] (--) NVIDIA(0): VideoBIOS: 62.98.74.00.06
[   841.109] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[   841.109] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[   841.112] (--) NVIDIA(0): Connected display device(s) on GeForce 8400 GS at PCI:1:0:0
[   841.112] (--) NVIDIA(0):     Samsung SyncMaster (CRT-1)
[   841.112] (--) NVIDIA(0):     Samsung SyncMaster (DFP-0)
[   841.112] (--) NVIDIA(0): Samsung SyncMaster (CRT-1): 400.0 MHz maximum pixel clock
[   841.112] (--) NVIDIA(0): Samsung SyncMaster (DFP-0): 330.0 MHz maximum pixel clock
[   841.112] (--) NVIDIA(0): Samsung SyncMaster (DFP-0): Internal Dual Link TMDS
[   841.112] (**) NVIDIA(0): TwinView enabled
[   841.112] (II) NVIDIA(0): Display Devices found referenced in MetaMode: CRT-1, DFP-0
[   841.112] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   841.112] (**) NVIDIA(0):     device Samsung SyncMaster (CRT-1) (Using EDID frequencies
[   841.112] (**) NVIDIA(0):     has been enabled on all display devices.)
[   841.125] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   841.125] (**) NVIDIA(0):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[   841.125] (**) NVIDIA(0):     has been enabled on all display devices.)
[   841.184] (II) NVIDIA(0): Assigned Display Devices: CRT-1, DFP-0
[   841.189] (II) NVIDIA(0): Validated modes:
[   841.189] (II) NVIDIA(0):    
[   841.189] (II) NVIDIA(0):     "CRT:nvidia-auto-select+0+150,DFP:nvidia-auto-select+1680+0"
[   841.189] (II) NVIDIA(0): Virtual screen size determined to be 3600 x 1200
[   841.219] (--) NVIDIA(0): DPI set to (92, 88); computed from "UseEdidDpi" X config
[   841.219] (--) NVIDIA(0):     option
[   841.219] (--) Depth 24 pixmap format is 32 bpp
[   841.220] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[   841.227] (II) NVIDIA(0): Setting mode
[   841.227] (II) NVIDIA(0):     "CRT:nvidia-auto-select+0+150,DFP:nvidia-auto-select+1680+0"
[   841.252] (II) Loading extension NV-GLX
[   841.372] (==) NVIDIA(0): Disabling shared memory pixmaps
[   841.372] (==) NVIDIA(0): Backing store disabled
[   841.372] (==) NVIDIA(0): Silken mouse enabled
[   841.373] (**) NVIDIA(0): DPMS enabled
[   841.373] (II) Loading extension NV-CONTROL
[   841.373] (II) Loading extension XINERAMA
[   841.373] (II) Loading sub module "dri2"
[   841.373] (II) LoadModule: "dri2"
[   841.373] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   841.373] (II) Module dri2: vendor="X.Org Foundation"
[   841.373] 	compiled for 1.11.3, module version = 1.2.0
[   841.373] 	ABI class: X.Org Server Extension, version 6.0
[   841.373] (II) NVIDIA(0): [DRI2] Setup complete
[   841.373] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[   841.373] (==) RandR enabled
[   841.373] (II) Initializing built-in extension Generic Event Extension
[   841.373] (II) Initializing built-in extension SHAPE
[   841.373] (II) Initializing built-in extension MIT-SHM
[   841.373] (II) Initializing built-in extension XInputExtension
[   841.373] (II) Initializing built-in extension XTEST
[   841.373] (II) Initializing built-in extension BIG-REQUESTS
[   841.373] (II) Initializing built-in extension SYNC
[   841.373] (II) Initializing built-in extension XKEYBOARD
[   841.373] (II) Initializing built-in extension XC-MISC
[   841.373] (II) Initializing built-in extension SECURITY
[   841.373] (II) Initializing built-in extension XINERAMA
[   841.373] (II) Initializing built-in extension XFIXES
[   841.373] (II) Initializing built-in extension RENDER
[   841.373] (II) Initializing built-in extension RANDR
[   841.373] (II) Initializing built-in extension COMPOSITE
[   841.373] (II) Initializing built-in extension DAMAGE
[   841.375] (II) Initializing extension GLX
[   841.396] (II) XKB: reuse xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   841.400] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   841.400] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   841.400] (II) LoadModule: "evdev"
[   841.400] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   841.401] (II) Module evdev: vendor="X.Org Foundation"
[   841.401] 	compiled for 1.11.3, module version = 2.7.0
[   841.401] 	Module class: X.Org XInput Driver
[   841.401] 	ABI class: X.Org XInput driver, version 16.0
[   841.401] (II) Using input driver 'evdev' for 'Power Button'
[   841.401] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   841.401] (**) Power Button: always reports core events
[   841.401] (**) evdev: Power Button: Device: "/dev/input/event1"
[   841.401] (--) evdev: Power Button: Vendor 0 Product 0x1
[   841.401] (--) evdev: Power Button: Found keys
[   841.401] (II) evdev: Power Button: Configuring as keyboard
[   841.401] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[   841.401] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   841.401] (**) Option "xkb_rules" "evdev"
[   841.401] (**) Option "xkb_model" "pc105"
[   841.401] (**) Option "xkb_layout" "us"
[   841.402] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   841.402] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   841.402] (II) Using input driver 'evdev' for 'Power Button'
[   841.402] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   841.402] (**) Power Button: always reports core events
[   841.402] (**) evdev: Power Button: Device: "/dev/input/event0"
[   841.402] (--) evdev: Power Button: Vendor 0 Product 0x1
[   841.402] (--) evdev: Power Button: Found keys
[   841.402] (II) evdev: Power Button: Configuring as keyboard
[   841.402] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[   841.402] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[   841.402] (**) Option "xkb_rules" "evdev"
[   841.402] (**) Option "xkb_model" "pc105"
[   841.402] (**) Option "xkb_layout" "us"
[   841.403] (II) config/udev: Adding input device CHICONY USB Keyboard (/dev/input/event2)
[   841.403] (**) CHICONY USB Keyboard: Applying InputClass "evdev keyboard catchall"
[   841.403] (II) Using input driver 'evdev' for 'CHICONY USB Keyboard'
[   841.403] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   841.403] (**) CHICONY USB Keyboard: always reports core events
[   841.403] (**) evdev: CHICONY USB Keyboard: Device: "/dev/input/event2"
[   841.403] (--) evdev: CHICONY USB Keyboard: Vendor 0x4f2 Product 0x833
[   841.403] (--) evdev: CHICONY USB Keyboard: Found keys
[   841.403] (II) evdev: CHICONY USB Keyboard: Configuring as keyboard
[   841.403] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.0/input/input2/event2"
[   841.403] (II) XINPUT: Adding extended input device "CHICONY USB Keyboard" (type: KEYBOARD, id 8)
[   841.403] (**) Option "xkb_rules" "evdev"
[   841.403] (**) Option "xkb_model" "pc105"
[   841.403] (**) Option "xkb_layout" "us"
[   841.404] (II) config/udev: Adding input device CHICONY USB Keyboard (/dev/input/event3)
[   841.404] (**) CHICONY USB Keyboard: Applying InputClass "evdev keyboard catchall"
[   841.404] (II) Using input driver 'evdev' for 'CHICONY USB Keyboard'
[   841.404] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   841.404] (**) CHICONY USB Keyboard: always reports core events
[   841.404] (**) evdev: CHICONY USB Keyboard: Device: "/dev/input/event3"
[   841.404] (--) evdev: CHICONY USB Keyboard: Vendor 0x4f2 Product 0x833
[   841.404] (--) evdev: CHICONY USB Keyboard: Found keys
[   841.404] (II) evdev: CHICONY USB Keyboard: Configuring as keyboard
[   841.404] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.1/input/input3/event3"
[   841.404] (II) XINPUT: Adding extended input device "CHICONY USB Keyboard" (type: KEYBOARD, id 9)
[   841.404] (**) Option "xkb_rules" "evdev"
[   841.404] (**) Option "xkb_model" "pc105"
[   841.404] (**) Option "xkb_layout" "us"
[   841.405] (II) config/udev: Adding input device A4TECH USB Device (/dev/input/event4)
[   841.405] (**) A4TECH USB Device: Applying InputClass "evdev keyboard catchall"
[   841.405] (II) Using input driver 'evdev' for 'A4TECH USB Device'
[   841.405] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   841.405] (**) A4TECH USB Device: always reports core events
[   841.405] (**) evdev: A4TECH USB Device: Device: "/dev/input/event4"
[   841.405] (--) evdev: A4TECH USB Device: Vendor 0x9da Product 0x9090
[   841.405] (--) evdev: A4TECH USB Device: Found 1 mouse buttons
[   841.405] (--) evdev: A4TECH USB Device: Found scroll wheel(s)
[   841.405] (--) evdev: A4TECH USB Device: Found relative axes
[   841.405] (--) evdev: A4TECH USB Device: Found absolute axes
[   841.405] (--) evdev: A4TECH USB Device: Found absolute multitouch axes
[   841.405] (--) evdev: A4TECH USB Device: Found x and y absolute axes
[   841.405] (--) evdev: A4TECH USB Device: Found keys
[   841.405] (II) evdev: A4TECH USB Device: Configuring as mouse
[   841.405] (II) evdev: A4TECH USB Device: Configuring as keyboard
[   841.405] (II) evdev: A4TECH USB Device: Adding scrollwheel support
[   841.405] (**) evdev: A4TECH USB Device: YAxisMapping: buttons 4 and 5
[   841.405] (**) evdev: A4TECH USB Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   841.405] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0/input/input4/event4"
[   841.405] (II) XINPUT: Adding extended input device "A4TECH USB Device" (type: KEYBOARD, id 10)
[   841.405] (**) Option "xkb_rules" "evdev"
[   841.405] (**) Option "xkb_model" "pc105"
[   841.405] (**) Option "xkb_layout" "us"
[   841.406] (II) evdev: A4TECH USB Device: initialized for relative axes.
[   841.406] (WW) evdev: A4TECH USB Device: ignoring absolute axes.
[   841.406] (**) A4TECH USB Device: (accel) keeping acceleration scheme 1
[   841.406] (**) A4TECH USB Device: (accel) acceleration profile 0
[   841.406] (**) A4TECH USB Device: (accel) acceleration factor: 2.000
[   841.406] (**) A4TECH USB Device: (accel) acceleration threshold: 4
[   841.406] (II) config/udev: Adding input device A4TECH USB Device (/dev/input/js0)
[   841.406] (II) No input driver specified, ignoring this device.
[   841.406] (II) This device may have been added with another device file.
[   841.407] (II) config/udev: Adding input device A4TECH USB Device (/dev/input/event5)
[   841.407] (**) A4TECH USB Device: Applying InputClass "evdev pointer catchall"
[   841.407] (II) Using input driver 'evdev' for 'A4TECH USB Device'
[   841.407] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   841.407] (**) A4TECH USB Device: always reports core events
[   841.407] (**) evdev: A4TECH USB Device: Device: "/dev/input/event5"
[   841.407] (--) evdev: A4TECH USB Device: Vendor 0x9da Product 0x9090
[   841.407] (--) evdev: A4TECH USB Device: Found 20 mouse buttons
[   841.407] (--) evdev: A4TECH USB Device: Found scroll wheel(s)
[   841.407] (--) evdev: A4TECH USB Device: Found relative axes
[   841.407] (--) evdev: A4TECH USB Device: Found x and y relative axes
[   841.407] (II) evdev: A4TECH USB Device: Configuring as mouse
[   841.407] (II) evdev: A4TECH USB Device: Adding scrollwheel support
[   841.407] (**) evdev: A4TECH USB Device: YAxisMapping: buttons 4 and 5
[   841.407] (**) evdev: A4TECH USB Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   841.407] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.1/input/input5/event5"
[   841.407] (II) XINPUT: Adding extended input device "A4TECH USB Device" (type: MOUSE, id 11)
[   841.407] (II) evdev: A4TECH USB Device: initialized for relative axes.
[   841.407] (**) A4TECH USB Device: (accel) keeping acceleration scheme 1
[   841.407] (**) A4TECH USB Device: (accel) acceleration profile 0
[   841.407] (**) A4TECH USB Device: (accel) acceleration factor: 2.000
[   841.407] (**) A4TECH USB Device: (accel) acceleration threshold: 4
[   841.408] (II) config/udev: Adding input device A4TECH USB Device (/dev/input/mouse0)
[   841.408] (II) No input driver specified, ignoring this device.
[   841.408] (II) This device may have been added with another device file.
[   842.700] (II) XKB: reuse xkmfile /tmp/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[   842.711] (II) XKB: reuse xkmfile /tmp/server-5A8096C9A1B5302FB1D5173C7471B8413D22FE8F.xkm
[   853.339] (II) XKB: reuse xkmfile /tmp/server-33F396737E466D728CC875B91D836232C5920BE1.xkm
[   930.480] (II) evdev: Power Button: Close
[   930.480] (II) UnloadModule: "evdev"
[   930.480] (II) Unloading evdev
[   930.512] (II) evdev: Power Button: Close
[   930.512] (II) UnloadModule: "evdev"
[   930.512] (II) Unloading evdev
[   930.564] (II) evdev: CHICONY USB Keyboard: Close
[   930.564] (II) UnloadModule: "evdev"
[   930.564] (II) Unloading evdev
[   930.668] (II) evdev: CHICONY USB Keyboard: Close
[   930.668] (II) UnloadModule: "evdev"
[   930.668] (II) Unloading evdev
[   930.728] (II) evdev: A4TECH USB Device: Close
[   930.728] (II) UnloadModule: "evdev"
[   930.728] (II) Unloading evdev
[   930.856] (II) evdev: A4TECH USB Device: Close
[   930.856] (II) UnloadModule: "evdev"
[   930.856] (II) Unloading evdev
[   931.318]  ddxSigGiveUp: Closing log
[   931.319] Server terminated successfully (0). Closing log file.

```

---

### Post by chmac on 2012-04-17
Might be worth opening a new thread to discuss your specific issue.

---

### Post by CsabaBo on 2012-04-18
Agree. Thanks anyway!

---

