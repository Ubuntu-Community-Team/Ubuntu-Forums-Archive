---
title: "System won't boot after installation"
date: 2013-10-30
forum: Ubuntu Studio
---

### Post by UZeytindali on 2013-10-30
Hello everyone!
I've just decided to go with Ubuntu Studio because It offers plenty of features that I might want in an OS.
But I have to say that I'm a little disappointed at the beginning, because after a smooth installation, system won't boot.

From the inserting installation disk to "Reboot system now", everything went better than expected..
But after rebooting the system for the first time, nothing happens..

-Motherboard Logo
-Blank black screen with a flashing "-" on upper left of screen...

That is what happens..
Waited like 15-20 minutes like that, but nothing changes...

What could or might have I possible done wrong to make it be like that?
I'm kinda new to Ubuntu, but I have never experienced something like that in other distros...

I'm not writing this in a "Try Ubuntu without installing" mode, and everything seems to be just perfect.

My system is:
8 gigabytes of Ram
GeForce 640 Graphic Cards
Intel Core i3 Processor


I had no problems with Ubuntu, or Windows 7/8.

Any help is appreciated!
Thanks!

---

### Post by jejeman on 2013-10-31
Edit the kernel line in GRUB, erase "quiet splash" parameters in order to see what is going on.

---

### Post by UZeytindali on 2013-10-31
Unfortunately.. that didn't work...
I mean, there's so much going on, I couldn't understand...

I am now trying Boot-Repair, thinking something might be wrong with the Bootloader...

I'll let you know, whether It worked or not..

Fingers crossed...

---

### Post by UZeytindali on 2013-10-31
Yes! It worked like a charm!

Thank you very much for your interest in answering, [**[COLOR=#000000]jejeman[/COLOR]**]("http://ubuntuforums.org/member.php?u=609757")! I appreciate that.


For anyone out there, having the same problem, I followed the steps right here and problem solved! 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Thank you!

---

