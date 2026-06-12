---
title: "FreeNAS going for linux"
date: 2009-12-06
forum: The Cafe
---

### Post by whoop on 2009-12-06
[http://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=5&t=3966](http://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=5&t=3966)

FreeNAS will be moving away from BSD and going for (Debian) Linux...
I have mixed feelings about this (ZFS), but I think it is a generally positive step.
It could even be possible in the future to apt-get install the FreeNAS functionality onto an Ubuntu server machine...
I believe it will be called CoreNAS.

What do you guys think?

---

### Post by The Real Dave on 2009-12-06
I've used FreeNAS for quite a while now, but always used the WebGUI, never really CLI to admin it. If they can keep the functionality, I'd love it to be on Debian, I'm much more used to the Debian CLI. 

That said, theres bound to be quite some teething issues going from BSD to Debian. I think I'm gonna hang on to my FreeNAS disks for the moment ;)

Sounds like a good move :) You can't exactly get more stable than Debian, and the added freedom of packages would be nice. Why the name change though? Is it really needed?

---

### Post by ugm6hr on 2009-12-06
Not strictly true: [http://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=5&t=4959](http://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=5&t=4959)

Although the developers are moving around.

I like my FreeNAS box; it does exactly what I ask of it, and runs from a 64MB USB stick.

---

### Post by whoop on 2009-12-06
More info:
[http://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=5&t=4959](http://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=5&t=4959)

Looks like FreeNAS is not dead...

@ugm6hr: Hey, I was just reading that:D

---

### Post by Paqman on 2009-12-06
Could be a great move if it means FreeNAS will run on ARM. For SOHO networks running a NAS box on a big hot x86 processor is ridiculously wasteful IMO.

---

### Post by earthpigg on 2009-12-06
> **Paqman said:**
> Could be a great move if it means FreeNAS will run on ARM. For SOHO networks running a NAS box on a big hot x86 processor is ridiculously wasteful IMO.

5 years from now, i would like to see one potential future of a lot of 'obsolete' ARM cell phones hooked into an external hard drive as NAS boxes.

---

### Post by The Real Dave on 2009-12-06
> **ugm6hr said:**
> Not strictly true: [http://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=5&t=4959](http://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=5&t=4959)

Although the developers are moving around.

I like my FreeNAS box; it does exactly what I ask of it, and runs from a 64MB USB stick.

Ya, thats one thing you gotta admire about FreeNAS, its damn flexible. 

Mine boots from a CD, loads itself into the RAM, and grabs its config file from a 128MB USB key. Means it doesn't use any harddrive space, and that the drives that are in there can spin down when they're not being used. Keeps it nice and cold, even for a PIV, and low power usage :)

---

### Post by handy on 2009-12-06
I've been using FreeNAS for many months, & love it.

I've not used Ubuntu Server, though I expect that it is far larger & therefore more complicated than the my little FreeNAS which is roughly 25MB in size.

The total dedication/specialisation of the FreeNAS system to doing just exactly what it does & no more, makes it smaller, more stable & secure.

I haven't read any of the links in this thread, though the idea I get is that perhaps there will be a FreeNAS fork that uses the Debian which provides ZFS support?

I personally like my FreeNAS just the way it is & see no reason to upgrade it, (& I believe that there are upgrades available) as it does the job perfectly in every way already, for my purposes anyway.

I do however like the idea of FreeBSD supporting the ARM processors, that would be an upgrade that I would eventually make use of on environmental grounds.

---

### Post by K.Mandla on 2009-12-06
I would be both happy and sad if FreeNAS moved to a different core; sad because as it is, I find it to be amazingly solid and speedy, although a change doesn't necessarily mean that would be different.

And I'd be happy because for every two or three machines that I try FreeNAS on, I have one or two with hardware difficulties that make it impractical to use. Again, maybe shifting to Debian would solve that, maybe not.

So long as the principle and presentation of ____NAS stays the same, I'll continue to be a fan.

---

