---
title: "cannot locate Boot info in Ubuntu 12"
date: 2012-03-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by gallicbear on 2012-03-12
Hi there. I recently installed Ubuntu 12.04 LTS. It was the only distro that my graphics card could handle. However, I am getting quite discouraged with it. I am trying to accomplish something which should be rather simple: edit the boot configuration to change the default OS that loads at boot. I find no menu.lst, no grub.cfg. andI noticed in forums that others have the same problem. My distro must be different from prior ones.
The only indication of grub I discovered through the 'find' function is in: usr\lib\grub\i386-pc\stage2. If I try to edit the file that should contain info, it just returns a blank screen.

ok, my other concern is that BCDEasy cannot connect to Linux. The NST directory has wrong info. How can I find the the right path top where boot is located? On the other hand, if menu.lst does not exist in ubuntu 12, it's of no use.

Last, but not least, there was a utility, called startup-manager (or startupmanager). It is no longer available through apt-get install. 

What now? How can I edit my grub file or which one? Regards and thanks for your help.

---

### Post by The Cog on 2012-03-12
Moved to Ubuntu+1

---

### Post by gallicbear on 2012-03-12
Thanks, The Cog for noticing the thread. Don't know what you mean by that. I am a newbie.

---

### Post by dino99 on 2012-03-12
> **gallicbear said:**
> Thanks, The Cog for noticing the thread. Don't know what you mean by that. I am a newbie.

you should take note that grub2 is actually used on Ubuntu :)  More info following the dedicated link below

---

### Post by gallicbear on 2012-03-12
Thanks, Dino99. That helped a lot to get a grasp of the situation.

---

### Post by grahammechanical on 2012-03-12
Why do you think this?

>  something which should be rather simple

A very complicated set of actions need to take place when more than one OS is present.

I have installed Grub Customizer. This is what makes it all very simple for me.

[http://ubuntuforums.org/showthread.php?t=1664134]("http://ubuntuforums.org/showthread.php?t=1664134")

Yes, I did study what is now called legacy Grub just so as to put a background image behind the Grub menu. It is simple when we know how to do. I could work out how to modify Grub 2 as well. But Grub Customizer does it all for me.

By the way. The developers of Grub 2 do not allow us to easily edit the Grub configuration file. They have provided secondary files that can be edited and then the actual Grub configuration file get re-written when the command

> sudo update-grub

is issued.


Regards.

---

### Post by gallicbear on 2012-03-12
Thanks, grahammechical, for your input. I'll work on that.

---

