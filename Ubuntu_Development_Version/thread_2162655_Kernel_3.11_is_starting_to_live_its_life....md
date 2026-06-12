---
title: "Kernel 3.11 is starting to live its life..."
date: 2013-07-15
forum: Ubuntu Development Version
---

### Post by zika on 2013-07-15
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11-rc1-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11-rc1-saucy/)

[http://ubuntuforums.org/showthread.php?t=2158852&p=12731599#post12731599](http://ubuntuforums.org/showthread.php?t=2158852&p=12731599#post12731599)
[http://ubuntuforums.org/showthread.php?t=2158852&p=12731625#post12731625](http://ubuntuforums.org/showthread.php?t=2158852&p=12731625#post12731625)

Just to make a new tread and not to mess up 3.10 thread...

---

### Post by jfernyhough on 2013-07-15
Oh, go on then. Let's see how many of my kernel modules fail to build. :D

Edit: Surprisingly, fglrx 13.101 builds ok. Unsurprisingly, SPL (for ZoL) fails to build.

---

### Post by slickymaster on 2013-07-15
First attempt... no luck.

My VirtualBox Guest Additions crashed:```
~/Downloads$ sudo dpkg -i linux-headers-3.11.0-031100rc1-generic_3.11.0-031100rc1.201307141935_i386.deb
Selecting previously unselected package linux-headers-3.11.0-031100rc1-generic.
(Reading database ... 167699 files and directories currently installed.)
Unpacking linux-headers-3.11.0-031100rc1-generic (from linux-headers-3.11.0-031100rc1-generic_3.11.0-031100rc1.201307141935_i386.deb) ...
Setting up linux-headers-3.11.0-031100rc1-generic (3.11.0-031100rc1.201307141935) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.11.0-031100rc1-generic /boot/vmlinuz-3.11.0-031100rc1-generic
Error! Bad return status for module build on kernel: 3.11.0-031100rc1-generic (i686)
Consult /var/lib/dkms/virtualbox-guest/4.2.10/build/make.log for more information.
```

Keepin' the ride :)

---

### Post by deri on 2013-07-15
I was able to build ati as module. Not so sure about the ati version. I had ready on my hdd. But it's the latest offical or the latest beta. Not 100% sure, but pretty sure.

---

### Post by VinDSL on 2013-07-15
> **jfernyhough said:**
> Oh, go on then. Let's see how many of my kernel modules fail to build. :D
3.11 installed okay, but nVidia 304.88 failed the initial module build. I assume 304.88 needs to be patched for 3.11.

In the meantime, I attempted to revert to Nouveau.  This 3.11 / Nouveau combo hard locks @ Plymouth.

However, Nouveau works shockingly good in 3.10.

So, here I sit, broken-hearted, waiting for the devs to make the next move... LoL!  :D

---

### Post by fooman on 2013-07-15
tried the 3.11 kernel early this morning before leaving for work and the nvidia driver (325.08 from Xedgers) failed to build.  just got home awhile ago,  ran an update and was glad to see that it included an updated nvidia 325.08 (again from Xedgers).  ran the updates, rebooted and i am in!! :P

```
Current Date/Time: Mon Jul 15 15:36:34 EDT 2013
Distro Release: Ubuntu Saucy Salamander (development branch)
Kernel Release: Linux 3.11.0-031100rc1-generic
Gnome Release: GNOME Shell 3.8.3
Unity Release: unity 7.0.2

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GTX 480/PCIe/SSE2
OpenGL version string:  4.3.0 NVIDIA 325.08
```

edit: forgot to thank the devs!  ...great work, incredibly fast!!

---

### Post by VinDSL on 2013-07-15
w00t!  That was f-a-s-t!!!  :D

Installed the nvidia-304 (304.88-0ubuntu5+xedgers~saucy1) hybrid and I'm in.

```
vindsl@Zuul:~$ echo && echo "~ VinDSL Unity Debug Script 13.07.08 (vindsl.com) ~" && echo -n "Current Date/Time: " && TZ='UTC' date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Gnome Release: " && gnome-shell --version && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Package: mesa-common-dev" && dpkg -s mesa-common-dev | sed 's/^/  /' | grep Version && echo || echo && echo "Package: xserver-xorg-core" && apt-cache policy xserver-xorg-core | grep Installed && echo || echo && echo "Package: xserver-common" && apt-cache policy xserver-common | grep Installed && echo || echo && echo "Package: xserver-xephyr" && apt-cache policy xserver-xephyr | grep Installed && echo || echo && echo "Tree Map of PCI Devices:" && lspci -tv && echo || echo && echo "Display Properties:" && echo -n " lcd monitor:    Dell UltraSharp 1907FP (analog input)" && echo && xdpyinfo | grep -E '(resolution|dimensions)' && echo

~ VinDSL Unity Debug Script 13.07.08 (vindsl.com) ~
Current Date/Time: Mon Jul 15 21:07:05 UTC 2013
Distro Release: Ubuntu Saucy Salamander (development branch)
Kernel Release: Linux 3.11.0-031100rc1-generic
Gnome Release: GNOME Shell 3.9.4
Unity Release: unity 7.0.2

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.88

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 115
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.1.0-0ubuntu1
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

Package: mesa-common-dev
  Version: 9.2.0~git20130711.c451619d-0ubuntu0sarvatt

Package: xserver-xorg-core
  Installed: 2:1.14.2+git20130715+server-1.14-branch.3608d9f3-0ubuntu0ricotz

Package: xserver-common
  Installed: 2:1.14.2+git20130715+server-1.14-branch.3608d9f3-0ubuntu0ricotz

Package: xserver-xephyr
  Installed: 2:1.14.2+git20130715+server-1.14-branch.3608d9f3-0ubuntu0ricotz

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82875P/E7210 Memory Controller Hub
           +-01.0-[01]----00.0  NVIDIA Corporation G73 [GeForce 7600 GT]
           +-06.0  Intel Corporation 82875P/E7210 Processor to I/O Memory Interface
           +-1d.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
           +-1e.0-[02]----0c.0  Lite-On Communications Inc LNE100TX
           +-1f.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801EB (ICH5) SATA Controller
           +-1f.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller
           \-1f.5  Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller

Display Properties:
 lcd monitor:    Dell UltraSharp 1907FP (analog input)
  dimensions:    1280x1024 pixels (339x271 millimeters)
  resolution:    96x96 dots per inch

vindsl@Zuul:~$ 
```

Kudos, to the edgers devs!

Working perfect...

---

### Post by EgoGratis on 2013-07-15
[http://www.h-online.com/open/news/item/Linux-for-Workgroups-Linux-3-11-s-feature-set-now-confirmed-1917712.html](http://www.h-online.com/open/news/item/Linux-for-Workgroups-Linux-3-11-s-feature-set-now-confirmed-1917712.html)

---

### Post by VinDSL on 2013-07-15
Had a couple of (I assume) hardware-related episodes, since posting above.

[LIST=1]
[*]Hard locked in the middle of a session.  Required rebooting via power button, on computer case.
[*]Next session, everything went BaNG!  Thought it was a power outage.  Spit me to the BIOS screen.
[/LIST]

I'm back on 3.10 for now.  Don't want to puke a drive...


**EDIT**


2 1/2 hours on 3.10 -- no more episodes.

Think I'll wait for 3.11-rc2 before trying it again...  :)

---

### Post by slickymaster on 2013-07-16
Had to disable [COLOR=#000000]VirtualBox Guest Additions in order to install it, but it's done:```
[/COLOR][COLOR=#000000]~$ lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy
3.11.0-031100rc1-generic[/COLOR][COLOR=#000000]
```

The only issue so far is that I'm not able to use the Auto-resize Guest Display option of my VM.[/COLOR]

---

### Post by slickymaster on 2013-07-16
[COLOR=#000000]Auto-resize Guest Display of my VM is back in business, just had to rebuild [/COLOR][COLOR=#000000]VirtualBox Guest Additions. Everything is running smoothly.[/COLOR]

---

### Post by synaptix on 2013-07-16
Though I'm not using the 13.10 alpha 1 anymore and went back to xubuntu 13.04, I'm currently using the 3.11-rc1 kernel and it's working absolutely perfectly here, no problems or issues at all.

---

### Post by VinDSL on 2013-07-16
I accidentally booted into 3.11 this morning.

Didn't realize it for about a half-hour, when I closed Chromium & opened Firefox. Hard-locked again.

Back to 3.10.1...  ;)

---

### Post by synaptix on 2013-07-16
> **VinDSL said:**
> I accidentally booted into 3.11 this morning.

Didn't realize it for about a half-hour, when I closed Chromium & opened Firefox. Hard-locked again.

Back to 3.10.1...  ;)

New rc kernel must not like your hardware or something, lol.

---

### Post by VinDSL on 2013-07-16
> **synaptix said:**
> New rc kernel must not like your hardware or something, lol.
I'm starting to think it's memory-related.  

Linux will generally put up with a lot of hardware nonsense, but it's V picky about memory.

I run Crucial Ballistix Tracer RAM, with little twinkly LEDs all over them, which change colors/brightness/speed et cetera with any RAM activity.

When 3.11 hard-locks, those LEDS are dead as a hammer -- no activity whatsoever...

BTW, been on 3.10 for 6 hours with no probs...

---

### Post by synaptix on 2013-07-16
> **VinDSL said:**
> I'm starting to think it's memory-related.  

Linux will generally put up with a lot of hardware nonsense, but it's V picky about memory.

I run Crucial Ballistix Tracer RAM, with little twinkly LEDs all over them, which change colors/brightness/speed et cetera with any RAM activity.

When 3.11 hard-locks, those LEDS are dead as a hammer -- no activity whatsoever...

BTW, been on 3.10 for 6 hours with no probs...

Interesting. I'm using the stock RAM sticks that came with my tower, so have no idea who the manufacterer is. Been running on rc1 since it came out and been running it against Xubuntu 13.04 without issues.

Lucky me I suppose.

---

### Post by VinDSL on 2013-07-16
They might have pulled something from 3.11-rc1 that this machine needs (or failed to include it).  Who knows?

If worse_comes_to_worse, I'll compile it later (takes hours on this machine).  It's still V early in the cycle.  

I'm surprised any rc1 build works.  Many times they don't, on this box  LoL!

---

### Post by VinDSL on 2013-07-16
> **VinDSL said:**
> I'm starting to think it's memory-related.
Er... Excuse me for quoting myself, but...

I was doing a little digging, and ran across this:

SOURCE: [http://www.phoronix.com/scan.php?page=news_item&px=MTQwODI](http://www.phoronix.com/scan.php?page=news_item&px=MTQwODI)

> Zswap is a feature for the Linux kernel that provides compressed swap caching. It's been in development for a long time and was finally merged into the mainline Linux kernel for the 3.11 release. 

Making the Linux 3.11 kernel an even more exciting release was the merger on Wednesday of the Zswap support. Per the Linux kernel documentation, "Zswap is a lightweight compressed cache for swap pages. It takes pages that are in the process of being swapped out and attempts to compress them into a dynamically allocated RAM-based memory pool. zswap basically trades CPU cycles for potentially reduced swap I/O. This trade-off can also result in a significant performance improvement if reads from the compressed cache are faster than reads from a swap device." [...]

**[COLOR="#0000CD"]The merge to mainline of Zswap happened with this commit. "Zswap is a thin backend for frontswap that takes pages that are in the process of being swapped out and attempts to compress them and store them in a RAM-based memory pool."[/COLOR]**

I *think* I found the culprit...  ;)

---

### Post by Doug S on 2013-07-16
For some continuing work on [another thread]("http://ubuntuforums.org/showthread.php?t=2151440"), I have been keeping up to date with the various 3.10RC kernels, and now 3.11RC1. There are a significant number of kernel configuration changes between the final 3.10 and 3.11RC1, so I decided to load the ubuntu 3.11RC1 just to get the ubuntu version of the kernel config. However, when trying to compile the kernel with that configuration, it takes much much longer than normal and ends up absolutely enormous. I guess I'll go back to the config I was using (basically, the 3.10 one with defaults accepted for the new stuff), and then try again with 3.11RC2.```
  .
  .
  .
  INSTALL include/sound (10 files)
  INSTALL include/video (3 files)
  INSTALL include/xen (2 files)
  INSTALL include/uapi (0 file)
  INSTALL include/asm (64 files)
dpkg-deb: building package `linux-firmware-image' in `../linux-firmware-image_3.11.0-rc1-u-24_amd64.deb'.
dpkg-deb: building package `linux-headers-3.11.0-rc1-u' in `../linux-headers-3.11.0-rc1-u_3.11.0-rc1-u-24_amd64.deb'.
dpkg-deb: building package `linux-libc-dev' in `../linux-libc-dev_3.11.0-rc1-u-24_amd64.deb'.
dpkg-deb: building package `linux-image-3.11.0-rc1-u' in `../linux-image-3.11.0-rc1-u_3.11.0-rc1-u-24_amd64.deb'.

real    38m44.731s    [COLOR=#ff0000]<<< A compile should take about 15 mintes worst case[/COLOR]
user    121m49.813s
sys     9m58.557s

doug@s15:~/temp-k-git-3.10rc4$ ls -l linux-image-3.11*
-rw-r--r-- 1 doug doug  46285246 Jul 16 15:26 linux-image-3.11.0-031100rc1-generic_3.11.0-031100rc1.201307141935_amd64.deb
-rw-r--r-- 1 doug doug  49677592 Jul 15 09:12 linux-image-3.11.0-rc1+_3.11.0-rc1+-21_amd64.deb
-rw-r--r-- 1 doug doug  49676560 Jul 16 09:08 linux-image-3.11.0-rc1-nohzn_3.11.0-rc1-nohzn-23_amd64.deb
-rw-r--r-- 1 doug doug [COLOR=#ff0000]731616634[/COLOR] Jul 16 16:29 linux-image-3.11.0-rc1-u_3.11.0-rc1-u-24_amd64.deb
-rw-r--r-- 1 doug doug [COLOR=#ff0000]731613260[/COLOR] Jul 16 16:58 linux-image-3.11.0-rc1-u_3.11.0-rc1-u-25_amd64.deb
```Edit: I found the problem. For whatever reason debug info was being requested in the Ubuntu 3.11RC1 version.```
-rw-r--r-- 1 doug doug  [COLOR=#ff0000]51214734[/COLOR] Jul 16 17:38 linux-image-3.11.0-rc1-u_3.11.0-rc1-u-26_amd64.deb
doug@s15:~/temp-k-git-3.10rc4$ cd linux
doug@s15:~/temp-k-git-3.10rc4/linux$ diff .config .config.ubuntu
3c3
< # Linux/x86 3.11.0-rc1 Kernel Configuration
---
> # Linux/x86_64 3.11.0-031100rc1-generic Kernel Configuration
6772c6772,6773
< # [COLOR=#ff0000]CONFIG_DEBUG_INFO is not set[/COLOR]
---
> [COLOR=#ff0000]CONFIG_DEBUG_INFO=y[/COLOR]
> # CONFIG_DEBUG_INFO_REDUCED is not set


```

---

### Post by VinDSL on 2013-07-16
> **Doug S said:**
> [...] trying to compile the kernel with that configuration, it takes much much longer than normal and ends up absolutely enormous.
Yikes!

I'm envious of your time(s), but the size does seem enormous.

Well, I'm giving 3.11-rc1 another shot.

First try didn't last for 30 seconds before hard-locking.  I misspelled "enabled"  (left the 'd' off the end)  :D

Second try has lasted 15 minutes, so far, after disabling Zswap in the kernel boot parameters.

See what happens...  ;)

EDIT

Okay, that's it.  Lasted 49 minutes, this time.

I figured out a way to crash 3.11-rc1 every time, on this machine -- goto ->FB and play a Zynga flash game in Firefox. BooM! Repeatable time-after-after.  LoL!

Patiently awaiting rc2...

---

### Post by paul_in_london on 2013-07-17
> **VinDSL said:**
> Yikes!

I'm envious of your time(s), but the size does seem enormous.

Well, I'm giving 3.11-rc1 another shot.

First try didn't last for 30 seconds before hard-locking.  I misspelled "enabled"  (left the 'd' off the end)  :D

Second try has lasted 15 minutes, so far, after disabling Zswap in the kernel boot parameters.

See what happens...  ;)

EDIT

Okay, that's it.  Lasted 49 minutes, this time.

I figured out a way to crash 3.11-rc1 every time, on this machine -- goto ->FB and play a Zynga flash game in Firefox. BooM! Repeatable time-after-after.  LoL!

Patiently awaiting rc2...

Thanks for the heads-up Vin.

Can't remember why, but I've been using nvidia-304-updates for quite a long time now. This wouldn't build when I first installed 3.11-rc1, but thanks to one of your earlier posts I switched to nvidia-304 (the xorg-edgers version) and that did build ok.

I also experienced some hard lock-ups last night (during some package updates). I don't think it's necessarily or specifically because of the new kernel in my case because:

1) A few times during this cycle I can definitely remember getting exactly the same problem with earlier kernels when upstart was being upgraded from the desktop (as opposed to in recovery mode)

2) I only run fluxbox from a text login usually and I don't use a swap partition (or a swap file). I find that I rarely get near usiing even half of my paltry 2GB of RAM so I don't think the zram thing could be affecting me.

3) This old box actually has ECC RAM so I'm fairly confident my RAM is ok

No hard-lock-ups tonight I'm pleased to say... :)

Just feeling a little more cautious with updates at the moment!

---

### Post by VinDSL on 2013-07-17
> **paul_in_london said:**
> Just feeling a little more cautious with updates at the moment!
Definitely!  Me too.

Things are very brittle, right now, and easily broken.  ;)

---

### Post by paul_in_london on 2013-07-17
> **VinDSL said:**
> Definitely!  Me too.

Things are very brittle, right now, and easily broken.  ;)

Yep after the problems I had last night, I started off in recovery mode tonight and updated that way first before a normal boot! :)

---

### Post by VinDSL on 2013-07-17
Hrm...  Here's a weird one for you.

I was poking around, and found out zram was enabled on this box.

```
vindsl@Zuul:~$ sudo parted -l
[sudo] password for vindsl: 
Model: ATA MAXTOR STM316081 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  10.7GB  10.7GB  primary   ext4            boot
 3      10.7GB  78.9GB  68.2GB  primary   ext4
 4      78.9GB  80.0GB  1078MB  primary   linux-swap(v1)
 2      80.0GB  160GB   80.0GB  extended
 5      80.0GB  90.8GB  10.7GB  logical   ext4
 7      90.8GB  159GB   68.2GB  logical   ext4
 6      159GB   160GB   1076MB  logical   linux-swap(v1)

[B][COLOR="#0000CD"]Error: /dev/zram0: unrecognised disk label                                

Error: /dev/zram1: unrecognised disk label [/COLOR][/B]                               

vindsl@Zuul:~$
```

I have no idea when, where, why, how, zram was installed, but now I'm wondering if that has anything to do with 3.11-rc1/zswap crashing n' burning.

Maybe it's a module in 3.11-rc1  :confused:

Anyway, I purged it...

```
vindsl@Zuul:~$ sudo parted -l
Model: ATA MAXTOR STM316081 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  10.7GB  10.7GB  primary   ext4            boot
 3      10.7GB  78.9GB  68.2GB  primary   ext4
 4      78.9GB  80.0GB  1078MB  primary   linux-swap(v1)
 2      80.0GB  160GB   80.0GB  extended
 5      80.0GB  90.8GB  10.7GB  logical   ext4
 7      90.8GB  159GB   68.2GB  logical   ext4
 6      159GB   160GB   1076MB  logical   linux-swap(v1)


vindsl@Zuul:~$ 

```

Only 'problem' now is, I purged 3.11-rc1 last night, so I cannot test it.  :D

Guess I'll wait for rc2...

---

### Post by paul_in_london on 2013-07-18
> **VinDSL said:**
> Hrm...  Here's a weird one for you.

I was poking around, and found out zram was enabled on this box.

```
vindsl@Zuul:~$ sudo parted -l
[sudo] password for vindsl: 
Model: ATA MAXTOR STM316081 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  10.7GB  10.7GB  primary   ext4            boot
 3      10.7GB  78.9GB  68.2GB  primary   ext4
 4      78.9GB  80.0GB  1078MB  primary   linux-swap(v1)
 2      80.0GB  160GB   80.0GB  extended
 5      80.0GB  90.8GB  10.7GB  logical   ext4
 7      90.8GB  159GB   68.2GB  logical   ext4
 6      159GB   160GB   1076MB  logical   linux-swap(v1)

[B][COLOR="#0000CD"]Error: /dev/zram0: unrecognised disk label                                

Error: /dev/zram1: unrecognised disk label [/COLOR][/B]                               

vindsl@Zuul:~$
```

I have no idea when, where, why, how, zram was installed, but now I'm wondering if that has anything to do with 3.11-rc1/zswap crashing n' burning.

Maybe it's a module in 3.11-rc1  :confused:

Anyway, I purged it...

```
vindsl@Zuul:~$ sudo parted -l
Model: ATA MAXTOR STM316081 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  10.7GB  10.7GB  primary   ext4            boot
 3      10.7GB  78.9GB  68.2GB  primary   ext4
 4      78.9GB  80.0GB  1078MB  primary   linux-swap(v1)
 2      80.0GB  160GB   80.0GB  extended
 5      80.0GB  90.8GB  10.7GB  logical   ext4
 7      90.8GB  159GB   68.2GB  logical   ext4
 6      159GB   160GB   1076MB  logical   linux-swap(v1)


vindsl@Zuul:~$ 

```

Only 'problem' now is, I purged 3.11-rc1 last night, so I cannot test it.  :D

Guess I'll wait for rc2...

Still on 3.11.rc1.

Here's what I have (didn't have to purge anything):

```
paul@lubuntu-64:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003bcbd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    78125055    39061504   83  Linux
/dev/sda2   *    78125056   160045055    40960000   83  Linux
/dev/sda3       160045056   243931135    41943040   83  Linux
paul@lubuntu-64:~$
```

```
paul@lubuntu-64:~$ sudo parted -l
Model: ATA SAMSUNG HD160JJ/ (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  40.0GB  40.0GB  primary  ext4
 2      40.0GB  81.9GB  41.9GB  primary  ext4         boot
 3      81.9GB  125GB   42.9GB  primary  btrfs


paul@lubuntu-64:~$
```

---

### Post by VinDSL on 2013-07-19
> **paul_in_london said:**
> Still on 3.11.rc1 [...]
On a lark, I installed 3.11-rc1 (19-jul-2013 daily) today.

Been using it for 90 min without issue(s).  Actually, it's quite perky!

Knock_on_wood... 

EDIT

10 hours and counting -- no probs with the 3.11-rc1 daily.

I think getting rid of zram took care of the locks-ups.  ;)

---

