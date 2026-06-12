---
title: "Linux distribution low on disk space requirements?"
date: 2012-04-29
forum: The Cafe
---

### Post by GameX2 on 2012-04-29
Hi!


The very few reasons why I keep Windows 7 on my laptop are as follow:

- I'm working with a lot of Adobe products at school; I can still use a Windows XP VM, which do the job;
- A few games still don't work on Wine;
- Wonder if removing Windows will be dangerous for the laptop (I doubt);
- It's always good to have a second operating system, if Ubuntu goes crazy and is nearly unusable.

I would like to have your opinion about this last apspect: if I have to choose a Linux distribution that would be used if Ubuntu stop working proprely?
A distribution that would allow me to do my work and recover my Ubuntu stuff, if Ubuntu become unusable?

I would be looking for a distribution that is light.  Not exacly light on RAM (Lubuntu ?), but most importantly light on disk space.  What would you recommend?

I've looked at DamnSmallLinux, but I don't think it'll be fine.
Lubuntu still use 4,5 GB, but is there anything better - with a graphical user interface ?


Thanks you!

---

### Post by Penguinnerd on 2012-04-29
Well, if 4 to 5 Gb is too much, then options are limited. Damn Small Linux is not being developed at this point, and it's very old.

I know from experience that Debian Squeeze can fit in 2 Gb, but the installer is more technical, and a new user might accidentally erase their Win7 install.

Also, you asked about a second distro that could be used for system recovery if Ubuntu got messed up, right? 
Well, I recommend... Ubuntu! Ubuntu can be run from a CD without installing it, so you can use it for it's own recovery. There's no need for a second distro to fix it.

So I really think Lubuntu is the best option you're going to find.

---

### Post by GameX2 on 2012-04-29
Ok.
I've just tested Debian for the first time, yesterday, in a virtual machine (Actually, the only distribution I've tried is Ubuntu).  I was surprised it looked so similar to Ubuntu, the interface.  I just found it harder to use, just a bit.  No software center, no Synaptic.  I had no idea how to install anything.

> Also, you asked about a second distro that could be used for system recovery if Ubuntu got messed up, right?

Yup.  I did thought about the LiveCD, but maybe it'll be more productive to use an installed system.  Right now, I'm typing from Windows 7, since my Wifi is buggy on Ubuntu, got to find a way to disable 802.11n and force the use of 802.11g. :/

4GB is pretty good, especially that Windows 7 use 20GB. Oo  I was just wondering if there were anything smaller.  Apparently not so much.

I would probably give Lubuntu a shot, I'll see what it look like - Why would I make a second partition for a second Ubuntu, I don't know. :P

Thanks for the reply

---

### Post by dniMretsaM on 2012-04-29
> **GameX2 said:**
> Ok.
I've just tested Debian for the first time, yesterday, in a virtual machine (Actually, the only distribution I've tried is Ubuntu).  I was surprised it looked so similar to Ubuntu, the interface.  I just found it harder to use, just a bit.  No software center, no Synaptic.  I had no idea how to install anything.



Yup.  I did thought about the LiveCD, but maybe it'll be more productive to use an installed system.  Right now, I'm typing from Windows 7, since my Wifi is buggy on Ubuntu, got to find a way to disable 802.11n and force the use of 802.11g. :/

4GB is pretty good, especially that Windows 7 use 20GB. Oo  I was just wondering if there were anything smaller.  Apparently not so much.

I would probably give Lubuntu a shot, I'll see what it look like - Why would I make a second partition for a second Ubuntu, I don't know. :P

Thanks for the reply

SliTaz is a really small distro. Version 4.0 (currently the latest stable release) can be installed on a hard drive with as little as 48MB of space (according to the SliTaz Web site). Because it's so small it's obviously not fully featured, but it's pretty usable.  If you want something with more "stuff," you might look at Crunchbang, although it runs at about 4GiB. You could also roll your own with an Ubuntu Minimal CD, although that's a more advanced option. You might also consider runny Puppy from a USB stick. No space issues on your PC, since it's all contained on the USB drive, but you can take it with you and use it anywhere (and it's really sight, so you can use it on old computers).

---

### Post by Copper Bezel on 2012-04-29
[QUOTE=GameX2]Yup. I did thought about the LiveCD, but maybe it'll be more productive to use an installed system.[/QUOTE]
It's really not, though. Your recovery options are limited if you're booting from the same drive you're trying to fix.

---

### Post by CharlesA on 2012-04-29
> **Copper Bezel said:**
> It's really not, though. Your recovery options are limited if you're booting from the same drive you're trying to fix.

This.

As for a distro that is fairly light, go with Debian Squeeze. 5GB really isn't that much space.

It's easier to just resize the Windows partition and install the distro of your choice and not bother worrying about how much disk space it takes.

---

### Post by OpenSourceRules on 2012-04-29
Get a USB stick of far size (something like 16G to 32G) and run Dreamlinux on it.  
(I can never try it; my computer is back from 2004, and it cannot be booted on an USB drive.)

---

### Post by Bandit on 2012-04-29
I have a ton of stuff installed and currently the main system folder is only using 10.1GB. If your having space issues just save your media on a thumb drive like mentioned. There really isnt nothing you can really do if your running out of disk space, buy a hard drive.

---

### Post by OpenSourceRules on 2012-04-29
Media and games are the most space-consuming parts.  
If your hard drive is still IDE, I would suggest getting a new computer if you are that desperate for space.

---

