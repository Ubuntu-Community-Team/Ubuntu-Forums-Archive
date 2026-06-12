---
title: "[SOLVED] Windows XP Home: pagefile questions..."
date: 2007-12-30
forum: Windows
---

### Post by ryanVickers on 2007-12-30
I now have 2GB of RAM and will never come close to using it all - my life's record is 1.73Gb, but on average, I'd say that 1.2Gb would be just fine...

My point being, I have **zero** need for a page file anymore, and I got rid of it, and thats actually all good, but here's the problem: yes, everything works "fine", but the system appears to reserve memory, about 300 to 600 Mb worth, regardless if there is a page file or not, and I want this to go away!!!  I want to use ALL my RAM :p

*I have attached an image of what I mean - I have 2Gb, but only between 1.6 and 1.4 tends to be "available" :mad:

I realize in Linux this would not be a problem and it all works perfectly actually, but I would like help with this in windows... :( lol

---

### Post by LinuxIsInnovation on 2007-12-30
The pagefile isnt located on your RAM, nor does windows have any reserve memory in the RAM.. Rather, the pagefile is created on the hard disk
To modify pagefile:
Start the System Control panel applet (start - settings - control         panel - system)
       Click the Performance tab
       Under the Virtual Memory section it will tell the currently         configured amount. Click Change.
There, select no pagefile on the drives and click Set button
Click apply and reboot your computer

---

### Post by ryanVickers on 2007-12-30
I know that - it's the file on your disk, and it's the equivalent of the Linux swap partition, but I said I removed it, and trust me I know everything about changing the size, moving it, etc. I'm asking why exactly there is a difference between my total RAM and "available" RAM, and why whatever this "system cache" thing is, is taking up about 650Mb of RAM (I don't know if I actually can use it and it's just saying that, or if it IS actually is reserved, I just want to know* what* it is, and if it DOES reserve that much and make it unusable, then I want to know how to shrink or remove it! :p)

---

### Post by LinuxIsInnovation on 2007-12-31
Even Linux caches the RAM. To check it, add the System Monitor applet to a panel and click on it. From there, tick the Memory graphs. You will find cached memory there.
Any OS caches something to facilitate faster access to the area. Say if you have 2GB RAM. The speed of the system would be faster if 1GB is cached, 0.5 GB is used and 0.5GB is free, and slower if 0.5 GB is used and 1.5GB is free. For example, do you know ReadyBoost in Vista. All it does is that the OS caches the free space on a flash disk to increase speed.
Softwares like FreeRAM delete the cached area. They actually don't have any effect on speed. FreeRAM does not work with Vista.

---

### Post by ryanVickers on 2007-12-31
Ok thanks :p


Yeah, I know about Linux caching some things and I guess windows does too..., but in Linux, it shows the "cache" as "free" because, really,... well it is!
In windows, i just says it's used as "cache", and whats worse, the graph - you get a line of used, and the bottom is 0, and the top is all RAM and pagefile *available -* the top is not out of 2Gb, it's out of the *available*, causing people to assume the cache would not go away to hold "real" data in the event it has to... :p

---

### Post by ryanVickers on 2007-12-31
Sorry - [COLOR=Red]**important update**[/COLOR] :p

[COLOR=Black]I just wasn't looking closely enough - the Total is total, the available is what is not used, and the cache is how much is cached but does not appear to consume RAM in a way that make it unusable for anything else :D[/COLOR]

---

