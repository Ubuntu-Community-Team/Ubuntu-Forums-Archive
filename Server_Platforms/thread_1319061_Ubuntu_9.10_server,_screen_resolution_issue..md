---
title: "Ubuntu 9.10 server, screen resolution issue."
date: 2009-11-08
forum: Server Platforms
---

### Post by PageUp on 2009-11-08
Hello ubuntu community,

For the past couple of weeks now, I've been fighting with the resolution issue I'm having with the new upgrade. After reading post after post as well as articles posted in the past seem irrelevant to the new installation. I nor a good friend of mine have the previous menu.lst in the /boot/grub directory. After going though pain staking examination of just what can help change the default 680x480 resolution. I've come up short, and here I am.

I should mention that I'm running ubuntu 9.10 server in VMware 7.0 workstation.


Thanks,
-PageUp

---

### Post by koenn on 2009-11-08
unless i missed some recent development, ubuntu server is text only, most often something like 25 lines of 80 characters or so

what resolution are you talking about ? and why would it have anything to do with the boot menu ?

---

### Post by Vegan on 2009-11-08
The screen resolution goes back to the original monochrome display adapter that IBM offered users of the original PC.

The MDA uses 80x25 on s green screen. Connection to a mainframe could use the 8250 emulator easily.

Linux uses the VT100 ANSI terminal which is on par with the Color Graphics Adapter. The CGA had poor text but supported 8 colors with intensity.

---

### Post by yeleek on 2009-11-11
Is there a 9.10 version of this?
[http://ubuntuforums.org/showthread.php?t=352663](http://ubuntuforums.org/showthread.php?t=352663)

---

