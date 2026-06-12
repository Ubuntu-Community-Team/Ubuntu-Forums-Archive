---
title: "XP seperate hard drive in virtualbox"
date: 2008-12-19
forum: Virtualisation
---

### Post by BigBig5 on 2008-12-19
:confused: How to run XP from a seperate hard drive in virtualbox.
I can't get it to work at all try many ways with other virtualization software, but none work. :confused:

---

### Post by Calmor on 2008-12-19
Hmm, seems I stand corrected... I wasn't under the impression that you could boot a native Windows partition.

Thanks for the tips!

---

### Post by HotShotDJ on 2008-12-19
There are several "HOWTO" threads that address this issue that have been linked in the [Virtualizion Mega-thread]("http://ubuntuforums.org/showthread.php?t=973756") (the first one at the top of the Virtualization forum).

Here is one to get you started: [http://ubuntuforums.org/showthread.php?t=769883](http://ubuntuforums.org/showthread.php?t=769883)

I would be remiss if I didn't include the following warning directly from the [VirtualBox user manual]("http://www.virtualbox.org/wiki/Downloads"):> **Warning**: Raw hard disk access is for expert users only. Incorrect use or use of an outdated configuration can lead to total loss of data on the physical disk. Most importantly, do not attempt to boot the partition with the currently running host operating system in a guest. This will lead to severe data corruption.


Of course, if you have any problems or further questions, go ahead and ask. :)

---

### Post by howefield on 2008-12-19
Make sure the drive you want to use is mounted and point to it when you create the space for the vm. 

Load up VirtualBox.
Select New, then next.
Type name and OS type, then next.
Give it the RAM you want and press next.

Then press New button, next, select dynamic or fixed, then next,
Click the folder icon to the right of the Location field and navigate to the disk that you want to use. Probably in the /media folder. 

The rest should be fairly self explanatory.

---

