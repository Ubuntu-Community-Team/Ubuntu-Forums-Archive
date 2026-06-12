---
title: "snd-rtctimer module &amp;&amp; ubuntu studio"
date: 2009-10-31
forum: Ubuntu Studio
---

### Post by bawig1 on 2009-10-31
I am trying to use rosegarden with ubuntu but when it starts it says that;

'System timer resolution is too low'

and

'Rosegarden was unable to find a high-resolution timing source for MIDI performance.'

It says I need to load the snd-rtctimer module for rosegarden to work properly, and I cannot seem to find it anywhere. I was thinking of changing to Ubuntu Studio.. Does Ubuntu Studio have a  RTC timer kernel module?

thanks,

Brett.

---

### Post by AutoStatic on 2009-11-01
Hell bawig1, are you using 9.04? Then you should add an extra udev rule to change the GID of /dev/rtc (at least that's what I think what causes this):> real-time clock

MIDI sequencers and such will benefit from being able to use the real-time clock, /dev/rtc. Make sure the 'audio' group has read permissions on it.

A simple 'chown' might not be persistent across reboots - to make the change last, create a new 40-rtc-permissions.rules file in /lib/udev/rules.d with the following line:

KERNEL=="rtc0", GROUP="audio"

… and reboot. See also: [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/306458](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/306458) 
From the [Linuxmusicians Wiki]("http://wiki.linuxmusicians.com/doku.php?id=system_configuration").

---

