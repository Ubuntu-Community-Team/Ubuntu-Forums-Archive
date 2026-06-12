---
title: "Difference between LIVE CD/USB &amp; Actual Installation?"
date: 2013-12-27
forum: Ubuntu, Linux and OS Chat
---

### Post by neu5eeCh on 2013-12-27
So, just to expand my knowledge of Linux a bit. Besides latency (which can be modified on a LIVE USB stick) what, practically speaking, is the difference between LIVE "media" and an actual install to a HDD. Does Linux install specific drivers, for specific hardware, when it's installed on a given system? Or does it, like LIVE media, configure itself each time it's booted. Could one treat a hard drive like a flash drive, plunk it in a different computer, and expect it to work?

---

### Post by lykwydchykyn on 2013-12-28
> **VTPoet said:**
> So, just to expand my knowledge of Linux a bit. Besides latency (which can be modified on a LIVE USB stick) what, practically speaking, is the difference between LIVE "media" and an actual install to a HDD. 

Live media generally boots from a read-only compressed file.  In scenarios where you can persist changes to a live image, it's usually in the form of a copy-on-write type file that is merged with the read-only filesystem.
> 
Does Linux install specific drivers, for specific hardware, when it's installed on a given system? 

Generally speaking, no.  Probably depends on the distro and kernel configuration, but apart from separately-packaged drivers like video or proprietary drivers, everything is just in the kernel.  I'm not aware of a system that specifically configures installed drivers according to hardware; after all, what would happen if you installed new hardware?

> Or does it, like LIVE media, configure itself each time it's booted. Could one treat a hard drive like a flash drive, plunk it in a different computer, and expect it to work?

It's been my experience over the years that Linux distros "just work" when you swap the hard drive to a new system.  Exceptions might include missing proprietary drivers, or the wrong graphics driver if you've manually configured X.  I've done this many many times when I was too lazy to reinstall.

---

### Post by stalkingwolf on 2013-12-28
Yes you can install on one computer then transfer that drive to another. I prefer to use this computer if im doing that it is faster and has better internet speed.  As mentioned the only problem i have encountered was with graphics.

---

### Post by neu5eeCh on 2013-12-28
Thanks. The tip on the graphics is a good one. In the past, I've preferred to install the proprietary drivers, but they often seem to cause more problems than they solve, so I stick with openGL if at all possible (I don't play 3D games).

Theoretically, I should be getting a [Cubox-i]("http://cubox-i.com/") sometime mid-January (pre-ordered it *way* back in August or September I think). They keep delaying. I got the one with all the bells and whistles (or I'd have it by now). I plan on installing Ubuntu to a microsd (the "HDD" of the Cubox-i) with a LiveCD on my laptop. Kind of cool, actually, cause I can just keep buying MicroSDs with different distros on them -- and totally play around. Anyway, that's some of the background to my question.

---

### Post by grahammechanical on 2013-12-28
Is a hard disk's data transfer rate better than a USB memory stick's data transfer rate? There you go. I find live session loading to be a lot slower than loading Ubuntu from a hard disk. I do believe that the live session has to identify the hardware. Whereas once Ubuntu is installed that information is in configuration files. Try running

```
sudo lshw -html > hardwareprofile.html
```

That will put a printout of the machine's hardware in a file called hardwareprofile.html and place it in the home folder. It can be read in a browser. I do not think that an ISO image has that information about my machine.

Many of the hardware devices are standard components. So, the kernel modules can cope when we put hard disks into machines with a different motherboard. Otherwise, the OS would be broken.

Regards.

---

