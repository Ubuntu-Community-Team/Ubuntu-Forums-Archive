---
title: "Kernel 3.10 Final is Here"
date: 2013-06-30
forum: Ubuntu Development Version
---

### Post by The Spectre on 2013-06-30
Kernel 3.10 is ready for Human Consumption...

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10-saucy/)

[https://www.kernel.org/](https://www.kernel.org/)

Kernel Changelog...
[http://kernelnewbies.org/Linux_3.10](http://kernelnewbies.org/Linux_3.10)

I have updated to Kernel 3.10 and so far everything is Rock Solid.

[ATTACH=CONFIG]244287[/ATTACH]

---

### Post by VinDSL on 2013-06-30
Thanks!  Working quite nicely...

[INDENT][ATTACH=CONFIG]244288[/ATTACH][/INDENT]

---

### Post by pqwoerituytrueiwoq on 2013-06-30
i just had the craziest install exp, turned my laptop on for the 1st time since before rc7 came out and was running apt-get update and it and it did not update the db so i ran it a few more times and then ran dist-upgrade, ran a dist-upgrade and installed the new kernel i got a error message about nvidia not compiling i don't even have that installed i am using Intel gpu on my laptop, i forgot i was using my desktop via SSH, then everything made sense
:lolflag:
edit: also seems grub put the RC at the top of the list and the final below them, SHIFT never works for me and i have to edit grub.cfg to anything other than the default to boot

---

### Post by Gavin77 on 2013-07-01
> **pqwoerituytrueiwoq said:**
> SHIFT never works for me and i have to edit grub.cfg to anything other than the default to boot

Took me ages a while ago to figure out how to access grub using the shift key.

Edit your /etc/default/grub

```
GRUB_HIDDEN_TIMEOUT="3"
```

This will make it wait 3 seconds for you to press the shift key before booting.

---

### Post by zika on 2013-07-01
> **Gavin77 said:**
> Took me ages a while ago to figure out how to access grub using the shift key.

Edit your /etc/default/grub

```
GRUB_HIDDEN_TIMEOUT="3"
```

This will make it wait 3 seconds for you to press the shift key before booting.
Even with value of &#8222;0&#8220; (default) Shift works...
Trick is to know when to start pressing Shift and not to stop until message &#8222;Grub is loading&#8220; (or something like that) appears...
If I've got a $ for every PC/owner that complained that it does not work... ;) They all were stunned to see that it (in fact) works... ;)

---

### Post by Gavin77 on 2013-07-01
I don't know about Ubuntu but on Kubuntu which I use it definitely does not work without changing that value.  It never worked for me until I increased the value to over 0.

---

### Post by zika on 2013-07-01
> **Gavin77 said:**
> I don't know about Ubuntu but on Kubuntu which I use it definitely does not work without changing that value.  It never worked for me until I increased the value to over 0.
As far as I know, K or U should not make the difference for Grub...

---

### Post by chenriques on 2013-07-01
With Kernel 3.9 and 3.10 most of my laptop FN keys don't work, just the volume keys and mute. With kernel 3.8.0 I had no problem and all the keys worked fine.

ASUS laptop (N56VZ) with Ubuntu 13.04 and kernel 3.10.0-031000-generic

---

### Post by pqwoerituytrueiwoq on 2013-07-01
> **chenriques said:**
> With Kernel 3.9 and 3.10 most of my laptop FN keys don't work, just the volume keys and mute. With kernel 3.8.0 I had no problem and all the keys worked fine.

ASUS laptop (N56VZ) with Ubuntu 13.04 and kernel 3.10.0-031000-generic

truy booting with [FONT=courier new]acpi_osi='!Windows 2012'[/FONT] in your kernel boot line

---

### Post by The Spectre on 2013-07-02
[COLOR=#000000]In case anyone wants to see what is new or changed in Linux Kernel 3.10 here is the [/COLOR]Changelog[COLOR=#000000]...[/COLOR]

[http://kernelnewbies.org/Linux_3.10](http://kernelnewbies.org/Linux_3.10)

So far Kernel 3.10 is running great on three different systems including an old Intel Pentium Dual Core Laptop that previously had problems (100% CPU Usage) with Linux Kernel v3.9.8.

And things should continue to improve with this new Kernel with the next couple of Maintenance Releases.:)

---

### Post by zika on 2013-07-02
Wait for 3.11...
As as I read, we're in for a treat...

---

### Post by pqwoerituytrueiwoq on 2013-07-03
Any one else having display corruption under 3.10, happening a lot in firefox after suspend
sandybridge cpu/gpu

it could be a issue with the old Xorg on 13.04, but i had no issues with 3.10 till the final, given i skipped the last rc

---

### Post by thotz on 2013-07-03
> **zika said:**
> Wait for 3.11...
As as I read, we're in for a treat...

Good point ;)

---

### Post by mrl586 on 2013-07-09
> **pqwoerituytrueiwoq said:**
> Any one else having display corruption under 3.10, happening a lot in firefox after suspend
sandybridge cpu/gpu

it could be a issue with the old Xorg on 13.04, but i had no issues with 3.10 till the final, given i skipped the last rc
I have same problem with 3.10.0-2.10 kernel on Kubuntu 13.04.

---

### Post by EricKit on 2013-07-09
> **pqwoerituytrueiwoq said:**
> Any one else having display corruption under 3.10, happening a lot in firefox after suspend
sandybridge cpu/gpu

it could be a issue with the old Xorg on 13.04, but i had no issues with 3.10 till the final, given i skipped the last rc

First off I want to say thanks for the update and it is working great!  I had no issues upgrading, it was seamless for me.

To answer this question, yes after a hibernate or suspend I get horizontal lines on my firefox, but it is seems to be for windows that firefox has generated (ie. already stored on my computer like the tiled pages when you first open it that it's cached or the title at the top or the firefox logo, etc. But the pages and downloaded content are fine.)

---

### Post by The Spectre on 2013-07-13
[COLOR=#000000]The first Maintenance Release Linux Kernel 3.10.1 out...[/COLOR]

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10.1-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10.1-saucy/)

[https://www.kernel.org/](https://www.kernel.org/)

[https://www.kernel.org/pub/linux/kernel/v3.x/ChangeLog-3.10.1](https://www.kernel.org/pub/linux/kernel/v3.x/ChangeLog-3.10.1)

---

### Post by VinDSL on 2013-07-13
> **The Spectre said:**
> [COLOR=#000000]The first Maintenance Release Linux Kernel 3.10.1 out...[/COLOR]
So far, so good.

Thanks!

---

### Post by fooman on 2013-07-13
got it, thanks!  :)

```
Current Date/Time: Sat Jul 13 22:01:12 EDT 2013
Distro Release: Ubuntu Saucy Salamander (development branch)
Kernel Release: Linux 3.10.1-031001-generic
Gnome Release: GNOME Shell 3.8.3
Unity Release: unity 7.0.2

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GTX 480/PCIe/SSE2
OpenGL version string:  4.3.0 NVIDIA 325.08

Xserver Xorg Core Branch:
Installed: 2:1.14.2+git20130705+server-1.14-branch.2767d9a1-0ubuntu0ricotz
```

---

### Post by zika on 2013-07-14
For ATI users: DMP has landed into 3.10-999 (daily)...
It was available for a week or so in drm-{next,intel-next,intel-nightly}...

---

### Post by JMB74 on 2013-07-15
3.11 RC1 [URL="http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11-rc1-saucy/"]http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11-rc1-saucy/
[/URL]

Incomplete for some archs though?

---

### Post by zika on 2013-07-15
> **JMB74 said:**
> 3.11 RC1 [URL="http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11-rc1-saucy/"]http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11-rc1-saucy/
[/URL]

Incomplete for some archs though?
Works here...

Update&#8321;: Created new thread just for 3.11...
[http://ubuntuforums.org/showthread.php?t=2162655](http://ubuntuforums.org/showthread.php?t=2162655)

---

### Post by dejavue on 2013-07-15
This kernel still does not work with proprietary AMD drivers for my HD6970 - reverted to 3.9.2 again, where the kernel + AMD drivers DON'T crash unity interface for good. Anyone know what bug that is? 
I tested against 3.9.8 and 3.9.6 and both crashed unity. 3.9.2 works with AMD drivers...

On my lenovo laptop (intel graphics) 3.10.1 works without a flaw...

---

### Post by deri on 2013-07-15
I suddenly lost sounds. I have only few updates. Trying saucy. Anyone else has the issue? I got ati --> hdmi --> amplifer --> speakers system.

---

### Post by zika on 2013-07-15
> **deri said:**
> I suddenly lost sounds. I have only few updates. Trying saucy. Anyone else has the issue? I got ati --> hdmi --> amplifer --> speakers system.
Did You try (if You use radeon, I could not conclude from Your post) with```
radeon.audio=1
```in kernel-boot-line
and/or


```
pcm.!default {type plug slave.pcm "hdmi"}
```in /etc/asound.conf or ~/.asoundrc...?

---

### Post by deri on 2013-07-15
I am pretty sure now that this is not a kernel issue. I really don't know what caused this and when this actually happened. Sounds worked yesterday. I don't use that much sounds on my system. I have noticed that the problem is somehow related to how linux sees my outputs. It doesn't "see" hdmi output. For some reason.

---

### Post by Hexxus on 2013-07-15
I just got the email about it too! Yay!

---

### Post by deri on 2013-07-15
This basically doesn't belong here. I got very irritating problem. 

I have working system. Except sounds doesn't work. I think I know the issue but I don't know how to fix it. 

Every setting, every cable, every spearker is as it should be. Only the problem is that if I boot hdmi cable connected I don't get picture on my dvi. If i unplug hdmi cable and boot it works fine. Adding hdmi when kde has succefully started doesn't fix the issue. So the problem is that I cannot use dvi and hdmi same time, because saucy doesn't see them seperately.

---

### Post by VinDSL on 2013-07-15
Well, drat!

3.11 kernel installed just fine, but nVidia 304.88 failed the initial module build.

Guess I'll have to switch back to Nouveau, until the mods come up with a 3.11.x patch for 304.88.

Isn't life on the edge exciting?  :D

---

### Post by deri on 2013-07-15
I have bought a wifi usb stick that connects to router. I got a lot of these errors. Is this normal? The distance between stick and router is around 1m.

"[ 1298.188461] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0"

Using latest kernel, but I have had this issue on earliers too. According to dmesg the stick is ra-link, but the package is telewell.

---

### Post by deri on 2013-07-15
I purged ati drivers and installed xorg edge instead and added radeon.audio=1 on grub and updated grub. 1st boot was kinda ok, I saw signal coming from my pc to amplifier (red spot on amplifier), but my resolution on my screen was a way too small to use. And xrandr didn't give me 1920x1080. So I rebooted, took off the hdmi cable and plugged it on when succefully booted into kde. 

no sounds...It doesn't see dvi and hdmi same time.

---

