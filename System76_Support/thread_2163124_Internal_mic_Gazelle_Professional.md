---
title: "Internal mic Gazelle Professional"
date: 2013-07-17
forum: System76 Support
---

### Post by sivlardemalle on 2013-07-17
Hi,

I have the Gazelle Professional since 2 week. I'm wondering how to get the internal mic working. When I go to sound settings, input: I can see that the 'Internal Microphone' is the device, my input volume is 100 % but the input level bars never react to the sounds I make.

Any ideas?

Thanx,
Rob.

---

### Post by sivlardemalle on 2013-07-17
Strange, suddenly it worked after a reboot. While I was sure it wasn't woking before. I am puzzled.

---

### Post by rorschachwalter on 2013-07-17
Just one of the many bugs I've reported to System76 about this machine.

There are two workarounds for when it's not working:
[LIST=1]
[*]Plug, then unplug, a device into the external microphone jack. The device can be anything -- speakers or microphone. Then you should see your internal mic respond.
[*]Run alsamixer in a terminal, hit F6 and select the last sound device listed, hit F4 to select only capture devices, then toggle your first "Input Source" to Internal Mic. If it's already selected, select away from it, then back to it. This should enable the mic.
[/LIST]

---

### Post by sivlardemalle on 2013-07-19
Thanx for the information.

---

### Post by KlipperKyle on 2013-07-20
Here is a thread with the same issue:

[http://ubuntuforums.org/showthread.php?t=2140216](http://ubuntuforums.org/showthread.php?t=2140216)

---

