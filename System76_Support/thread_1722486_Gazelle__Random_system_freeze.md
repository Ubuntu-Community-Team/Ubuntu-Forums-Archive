---
title: "Gazelle : Random system freeze?"
date: 2011-04-05
forum: System76 Support
---

### Post by Max-P on 2011-04-05
Hi again, for the second time in the first week with my new laptop!

My new Gazelle laptop seems to hang, or freeze randomly and I think the problem is hardware-related. Here are the symptoms:

- It happens a few times during the day, since maybe the second or third day since the shipping pickup.

- The whole system hangs: no way to get back to a console or anything.

- Sometimes (but not always), the system gets really slow. X usually starts eating the CPU just like if it was running some really heavy software rendering, and ends by locking up too.

- Also happens in a console, for no reasons.

- It happens even in recovery mode, where nothing is supposed to be running

- It seems to be related to networking. It crashed a few times in a row while disabling network.


When I was in recovery mode, I saw two messages that didn't looked normal, one says "Too many connections", the other one was about the jme driver disabling RX timeout.


I tried many things, like updating the NVidia driver because I though it was its fault (mostly because it crashed a few times when using LibreOffice), it didn't fix anything so I uninstalled it and installed back the nvidia-current package.

I also though it was the wireless card (which I deleted the N disable configuration), so I disabled N wireless again.

I checked the startup services, everything is fine. I didn't install any other kernel module or anything.

I'm really out of ideas, so I ask for your help. 

Thanks!

(I saw this post: [http://ubuntuforums.org/showthread.php?t=1720944](http://ubuntuforums.org/showthread.php?t=1720944) but it's not the same bug, my system hangs, no coming back to gdm or anything)

---

### Post by isantop on 2011-04-06
You might also try running MemTest86. Issues like this a often caused by bad RAM, so that's usually the first thing to check. If that doesn't get it, go ahead and send us an email at
support...at...system76...dot...com.

---

