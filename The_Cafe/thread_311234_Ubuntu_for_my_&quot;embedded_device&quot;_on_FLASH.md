---
title: "Ubuntu for my &quot;embedded device&quot; on FLASH-Disk"
date: 2006-12-02
forum: The Cafe
---

### Post by info2 on 2006-12-02
Heya,

i have a very special project that i want to make for myself.

There is an older Notebook (P3-800, 256MB RAM). I have replaced the HDD with an IDE 44Pin to CompactFlash - Card adapter and installed a 1GB Disk.

Later I want to place the system in my car, using it as a kind of control center (using a touchscreen and a relais-interfacecard).

I don't need to say that Linux is the only choice for me. I really like Ubuntu and the "debian way". So i want to install a debian-linux on this Laptop.
It also must be small (yes, ubuntu would fit on this disk)
But Ubuntu doesn't provide JFFS2 during the installer. 
I don't want to use ext3 or something else created for normal disk drives.

Is there a way to install ubuntu with JFFS2 or is there another debianified distribution you can tell me that will fit my wishes ?

Thanks for any help you can give me.
I'm sorry for this bad english. :)

---

### Post by christhemonkey on 2006-12-02
How do you know the JFFS2 is not supported?
Im guessing you tried?

According to this:
[http://en.wikipedia.org/wiki/JFFS2](http://en.wikipedia.org/wiki/JFFS2)

> JFFS2 has been included in the Linux kernel since the 2.4.10 release.


Maybe try using the alternate cd?

Or using a previous ubuntu release?

Or you could try something like this:
[http://www.applieddata.net/forums/topic.asp?TOPIC_ID=2246](http://www.applieddata.net/forums/topic.asp?TOPIC_ID=2246)

---

### Post by info2 on 2006-12-02
Simply, the alternate-CD - Installer doesn't provide this option, but i like to have the root-disk formatted as jffs or something similar.

---

### Post by kerry_s on 2006-12-02
Ubuntu has JFS, which is just as good, does exactly the same thing.
If it were my project i would go with a command-line system build up. That way you can control the install & add just what you need that will keep the size down. You will also need to use light applications, maybe fluxbox or icewm for the WM, i don't think a DE will work for your needs, maybe a core/base DE, it all depends on what your after.Your going to have to do alot of tweaking to get it working right & not writing to the flash to prolong life.

If all else fails take a look at DSL linux or puppy, there made to run on flash & usb devices.

---

### Post by info2 on 2006-12-02
Yeah, i already tried to break down a standart-ubuntu - installation to a very small evel. I ended up with a 400MB system.
I'll take a look at DSL, didn't thought about using DSL. Maybe it can be what i need.

Thank you all for your answears.

---

### Post by kerry_s on 2006-12-02
> **info2 said:**
> Yeah, i already tried to break down a standart-ubuntu - installation to a very small evel. I ended up with a 400MB system.
I'll take a look at DSL, didn't thought about using DSL. Maybe it can be what i need.

Thank you all for your answears.


Yeah, with a little practice you can get lower than that, i'm at 527mb with a heck of alot installed. I'm using feisty on this test, for some reason it's bigger than it would be in edgy with exactly the same stuff. It's just a matter of playing with it, just make sure you grab synaptic that helps you see what the packages do & if you can remove it.

---

### Post by apfsdsdu on 2006-12-03
Ext3 is better than jffs2 for CompatFlash cards. Memory cards use hardware-based wear-leveling, and using software-based wear-leveling on top of that will be slow and actually worse for the flash chip.

---

### Post by dustinharriman on 2007-10-31
Actually, you do not want to use ext3 on any flash media, be it a USB flash drive, an SD card, compact flash, etc.  Why?  Read [this post]("http://lists.soekris.com/pipermail/soekris-tech/2002-May/000328.html") and you'll see why.  Basically, the filesystem will shred itself up badly after a week or two of usage, and fsck won't save you.  I know from experience, after learning the hard way, when [I installed Ubuntu to a USB flash drive in a project of mine, creating an entirely solid-state Ubuntu PC]("http://ca.blog.360.yahoo.com/blog-RkGSoVA1brWtXrVH9Gr5CzgVujwwGg--?cq=1&p=65").

You probably want to use reiserfs instead of ext3.  That has been working well for me for a couple of months now.

You also probably do not want to use jffs2.  jffs2 is only meant to be used on special embedded devices that are so cheap and minimal that they have no [wear-levelling]("http://en.wikipedia.org/wiki/Wear_levelling") hardware.  Virtually all manufacturers of consumer flash media now include wear-levelling in their hardware (and it would be wise to verify that this is true for the flash media you are about to buy before buying it, just to be prudent.  You can search the tech support areas of the manufacturer's web site, and ask if they don't state it).  For example, [OCZ has publically stated that all their USB flash drives have wear-levelling in them]("http://www.ocztechnologyforum.com/forum/showthread.php?t=26376&highlight=wear+levelling").  (BTW, I do not work for OCZ).  

So unless you are some serious embedded developer who is designing and working with developmental embedded hardware and the software that goes with it, and know the hardware has no wear-levelling, then you probably do not want to use jffs2.

---

### Post by feelmjawlk on 2007-11-22
Hi!

I've just installed Ubuntu Server 7.10 to a compact flash based system. I was hoping to be able to make my root filesystem read-only to minimize writing to my CF-card. I found a guide for doing this in SUSE:

[http://en.opensuse.org/How-To_Make_the_root_filesystem_read-only](http://en.opensuse.org/How-To_Make_the_root_filesystem_read-only)

But being an unexperienced linux sys-admin I'm not sure wheter the guide is applicable to ubuntu (my guess is that the boot-up scripts are designed differently). I've been searching the forums and the wiki, and google and I haven't really found anything useful. If anyone woul'd like to point me in the right direction I would very much appreciate it!

/Feelmjawlk

Edit: I've made the changes as suggested in Dustin Harrimans blog. (link above).

So now that's done I feel a bit better about the wear and tear of the rewriting. Though I'd still like to make the / ro

---

