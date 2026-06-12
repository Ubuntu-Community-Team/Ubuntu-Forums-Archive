---
title: "Jaunty kernel troubles"
date: 2009-08-14
forum: Ubuntu Studio
---

### Post by fela on 2009-08-14
Am I right in thinking that the kernel in ubuntu Jaunty has a much higher latency than other (older) versions? The audio regularly glitches out in Jaunty, but runs fine on Intrepid and all earlier versions. I don't know why but it seems that the kernel must be high-latency.

So I loaded the default generic kernel config from /boot in Jaunty into /usr/src/linux-2.6.30*. I checked make xconfig, and there was something - can't remember what it was :( - that was set to 250HZ when it should have been 1000HZ (for desktops). It was on the CPU options page though, near the latency options.

I compiled a kernel with this change plus optimized for k8 and XFS fs built in, but when it compiled it totally didn't run - It just came up with a blinking cursor after warning me that my graphics driver wasn't installed. I tried running X but of course it failed as there was something completely wrong with the kernel.

I never figured it out and I'm running fine now on Intrepid, I'd just like to know what all these problems were being caused by.

Thing to note: I was running ext4 on my jaunty installation (it happened on every different one of my multiple installations actually - it wasn't a one time thing - ext4 was the filesystem each time, unfortunately I didn't check it with ext3 or xfs). I'm now running xfs on my root partition on an intrepid installation (ext3 on boot partition due to GRUB complaints on XFS).

Any ideas? :confused:

---

