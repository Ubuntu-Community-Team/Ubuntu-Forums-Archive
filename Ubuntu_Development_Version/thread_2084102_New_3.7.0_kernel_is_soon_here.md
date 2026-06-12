---
title: "New 3.7.0 kernel is soon here"
date: 2012-11-14
forum: Ubuntu Development Version
---

### Post by Harry33 on 2012-11-14
The new 3.7.0 rc5 is building in Launchpad right now.
It will soon hit the RR repos.

Here:
[https://launchpad.net/ubuntu/+source/linux/3.7.0-1.7](https://launchpad.net/ubuntu/+source/linux/3.7.0-1.7)

---

### Post by wheeze on 2012-11-14
I just got it a few minutes ago on my daily update. Runs very nice, everything smooth and snappy.

---

### Post by VinDSL on 2012-11-14
> **Harry33 said:**
> The new 3.7.0 rc5 is building in Launchpad right now.
It will soon hit the RR repos.
Ah, that's better!

```
vindsl@Zuul:~$ uname -sr && cat /proc/version_signature
Linux 3.7.0-1-generic
Ubuntu 3.7.0-1.7-generic 3.7.0-rc5

```

Thanks, Harry!

---

### Post by jppr on 2012-11-15
I can´t understand what´s going wrong... :confused: cos... I don´t have any chance to start the machine 3.7 kernel, system freezes immediately. 3.5 kernel works without problems.

---

### Post by VinDSL on 2012-11-15
The only oddity I've noticed is...

There is a big difference in the sound volume, between the 3.7-rc5 mainline kernel, and the custom Ubu binary that's built on 3.7-rc5.

When I go back n' forth between the kernels, at boot -- the sound volume (at the same setting) is much louder in the mainline kernel.

---

### Post by zenarcher on 2012-11-15
Still not working for me.  When I boot up, the loading process stops at my KVM switch and that's as far as it goes.  All works fine with earlier kernels.

Could anyone suggest if this is something I should report as a bug, or should I just hold off and see if it is fixed in a later kernel release?  If I should report it, could you tell me where I should send a bug report?

Thanks,
zenarcher

---

### Post by ronacc on 2012-11-15
here too it is stopping very early in the boot , the last thing I see on the console is 2 of my drives being attached . 3.5 kernel is ok .

---

### Post by MWisBest on 2012-11-15
I haven't had any issues so far, minus the fact that the "linux" package was updated hours before the new 3.7 kernel image appeared for me.

---

### Post by VinDSL on 2012-11-15
I wonder if this is one of those 32-bit vs 64-bit "things"!?!?!?

I should have specified... the 32-bit version is working fine for me.  I just need to remember to turn the volume down, when booting into 3.7-rc5.  Otherwise, the "congo drums" and so forth, at login, is loud enough to wake the dead.  ;)

---

### Post by jppr on 2012-11-15
There is coming new kernel version [https://lists.ubuntu.com/archives/raring-changes/2012-November/001340.html](https://lists.ubuntu.com/archives/raring-changes/2012-November/001340.html)

I have 64-bit system

---

### Post by ronacc on 2012-11-15
todays 64 bit daily live fails to boot at the same place as the 3.7 kernel for me .

---

### Post by zenarcher on 2012-11-15
Same here.  Stops at the KVM switch in my system.

zenarcher

---

### Post by MWisBest on 2012-11-15
The newest 3.7.0 kernel (-2) is having issues with audio for me. The -1 revision worked fine. KDE's startup sound works, but that's about it. Flash, etc, not working.

EDIT: Looked at another thread in this forum section, explained that pulseaudio had the 32-bit version installed when doing the upgrades and to install the 64-bit version. Worked a treat.

---

### Post by jppr on 2012-11-16
That's the latest version of the kernel doesn´t work for me ... = (

---

### Post by VinDSL on 2012-11-16
Everything still working fine, here...

```

vindsl@Zuul:~$ uname -sr && cat /proc/version_signature
Linux 3.7.0-2-generic
Ubuntu 3.7.0-2.8-generic 3.7.0-rc5

```

```

vindsl@Zuul:~$ echo && echo "~ VinDSL Unity Debug Script 12.9.30 (vindsl.com) ~" && echo -n "Current Date/Time: " && date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Xserver Xorg Core Branch:" && apt-cache policy xserver-xorg-core | grep Installed && echo || echo && echo "Tree Map of PCI Devices:" && lspci -tv && echo || echo && echo "Display Properties:" && echo -n " lcd monitor:    Dell UltraSharp 1907FP (analog input)" && echo  && xdpyinfo | grep -E '(resolution|dimensions)' && echo

~ VinDSL Unity Debug Script 12.9.30 (vindsl.com) ~
Current Date/Time: Fri Nov 16 03:52:58 MST 2012
Distro Release: Ubuntu Raring Ringtail (development branch)
Kernel Release: Linux 3.7.0-2-generic
Unity Release: unity 6.12.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.64

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
Installed-Size: 132
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

Xserver Xorg Core Branch:
  Installed: 2:1.13.0+git20120920.70e57668-0ubuntu0ricotz

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82875P/E7210 Memory Controller Hub
           +-01.0-[01]----00.0  NVIDIA Corporation G73 [GeForce 7600 GT]
           +-06.0  Intel Corporation 82875P/E7210 Processor to I/O Memory Interface
           +-1d.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
           +-1e.0-[02]--+-07.0  U.S. Robotics USR5660A (USR265660A, USR5660A-BP) 56K PCI Faxmodem
           |            \-0c.0  Lite-On Communications Inc LNE100TX
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

---

### Post by jerrylamos on 2012-11-16
Continues Raring's miserably slow "autoconnect" tp hidden wireless WPA.  Example 4 minutes 25 seconds trying to get any response out of the extremely sluggish "network manager".
Intel Corporation Centrino Wireless-N 1000

I tried to install WICD which has reports of working where network manager doesn't want to.  That involved editing network manager configuration.  No idea what that did but the 3.7.0.0 refused to boot.

O.K., this is unstable, boot the latest .iso and re-onstall.  Neither Nov 14 or Nov 15 would boot - "initramfs".

I had a back level from Nov 8 which booted installed and updated fine, except bug #1017738 is still very much present.  Systems settings > network manager the drop down window try to enter anything and the window just totally ignores keyboard input.  For minutes.

On topic, 3.7.0.0 running fine on netbook, notebook, tower with no more bugs and quirks than quantal had.

---

### Post by PaulW2U on 2012-11-16
I'm not sure what I'm doing wrong or may be I just have the right hardware but the latest kernel is running fine here.

```
paul@G620:~$ uname -a
Linux G620 3.7.0-2-generic #8-Ubuntu SMP Thu Nov 15 16:20:48 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

I'm still getting a couple of warnings when I install the latest kernel. I suppose they should be reported?

---

### Post by wheeze on 2012-11-16
> **PaulW2U said:**
> I'm not sure what I'm doing wrong or may be I just have the right hardware but the latest kernel is running fine here.

```
paul@G620:~$ uname -a
Linux G620 3.7.0-2-generic #8-Ubuntu SMP Thu Nov 15 16:20:48 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```I'm still getting a couple of warnings when I install the latest kernel. I suppose they should be reported?

Same here, no problem with today's, or any other day's, kernel update. Everything running peachy keen :)

```
steve@ubu-raring:~$ uname -a
Linux ubu-raring 3.7.0-2-generic #8-Ubuntu SMP Thu Nov 15 16:20:48 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

Paul, what kind of warnings are you getting when installing the kernel? I get one about a missing modules directory or something like that. Seems to install and run OK though.

---

### Post by PaulW2U on 2012-11-16
> **wheeze said:**
> Paul, what kind of warnings are you getting when installing the kernel? I get one about a missing modules directory or something like that.

That's the one! :)

---

### Post by ventrical on 2012-11-16
The new kernel sees to have solved the firefox hi-cpu  problem.

```

ventrical@ventrical-P4M266A-8237:~$ echo && echo "~ VinDSL Unity Debug Script 12.9.30 (vindsl.com) ~" && echo -n "Current Date/Time: " && date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Xserver Xorg Core Branch:" && apt-cache policy xserver-xorg-core | grep Installed && echo || echo && echo "Tree Map of PCI Devices:" && lspci -tv && echo || echo && echo "Display Properties:" && echo -n " lcd monitor:    Dell UltraSharp 1907FP (analog input)" && echo  && xdpyinfo | grep -E '(resolution|dimensions)' && echo

~ VinDSL Unity Debug Script 12.9.30 (vindsl.com) ~
Current Date/Time: Fri Nov 16 15:14:05 EST 2012
Distro Release: Ubuntu Raring Ringtail (development branch)
Kernel Release: Linux 3.7.0-2-generic
Unity Release: unity 6.12.0

OpenGL vendor string:   X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on ATI RV350
OpenGL version string:  2.1 Mesa 9.0

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

dpkg-query: package 'mesa-utils' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

Xserver Xorg Core Branch:
  Installed: 2:1.13.0-0ubuntu6

Tree Map of PCI Devices:
-[0000:00]-+-00.0  VIA Technologies, Inc. P4M266 Host Bridge
           +-01.0-[01]--+-00.0  Advanced Micro Devices [AMD] nee ATI RV350 AQ [Radeon 9600]
           |            \-00.1  Advanced Micro Devices [AMD] nee ATI RV350 AQ [Radeon 9600] (Secondary)
           +-0a.0  ADMtek NC100 Network Everywhere Fast Ethernet 10/100
           +-0f.0  VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
           +-10.0  VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
           +-10.1  VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
           +-10.2  VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
           +-10.3  VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
           +-10.4  VIA Technologies, Inc. USB 2.0
           +-11.0  VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
           +-11.5  VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller
           \-12.0  VIA Technologies, Inc. VT6102 [Rhine-II]

Display Properties:
 lcd monitor:    Dell UltraSharp 1907FP (analog input)
  dimensions:    1024x768 pixels (270x203 millimeters)
  resolution:    96x96 dots per inch

ventrical@ventrical-P4M266A-8237:~$ 

```

---

### Post by jerrylamos on 2012-11-16
Boot amd64 doesn't, Nov 16 zsync'd iso dd'd to USB.

```
Busybox
/mount: mounting aufs on /root failed.
No such device
aufs mount failed
```
So in busy box I did an ls and there root is along with a bunch of other directories.

?

---

### Post by rtalcott on 2012-11-16
I have been getting this error for the last few days...AMD64...so it's not just me.

---

### Post by Chdslv on 2012-11-16
The kernel 3.7.0-2 is working very well for me. have a look; [http://ubuntuforums.org/showthread.php?t=2084921](http://ubuntuforums.org/showthread.php?t=2084921)

---

### Post by nm_geo on 2012-11-17
Package linux 3.7.0-2.8-amd64 
Worked for me in Lubuntu amd64 13.04 current 20121116.
Interesting Lubuntu spins come in later than Ubuntu   
Ubuntu 16-Nov-2012 08:35 
Lubuntu  16-Nov-2012 17:32

---

### Post by 3vi1 on 2012-11-17
Both the 3.7 kernels have had problems with my CR-48.  When they begin to boot, the video mode doesn't change properly and I'm stuck at a black screen forever instead of seeing plymouth and lightdm (and alt-Fx appears to have no effect).

Now here's the really bad part:  After this happens, on every subsequent boot... even after completely powering off... the system will no longer see it's primary hd/ssd.  All reboots tell me there's no bootable device.

The only way to recover is to go in to the BIOS and reload the optimal defaults.  Then - it will see the SSD on the next boot.

I *can* get 3.7 to boot up successfully, if I hold the shift key during boot and let the boot process halt on the grub screen for a few seconds.

3.5 has/had no problems.

Odd, huh?

---

### Post by jerrylamos on 2012-11-17
Nov 17 daily build did boot and did install, amd64 that is.  At least Nov 16, 15, 14, ... did not.  Nov 8 did.

Why re-install?  the partition space used was 

3262656 after a week of apt-get update, dist-upgrade, clean, autoclean, autoremove, and then make sure any old linux-images and linux headers were removed.

2799492 after new install and first update, dist-upgrade.

 463164 bytes of left over stuff I couldn't find in the updated one that's not in the new install.

?

Yes, I know I've got disk space, it just is of interest there's almost half a MB laying around doing nothing....

---

