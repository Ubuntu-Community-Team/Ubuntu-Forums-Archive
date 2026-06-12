---
title: "Windows xp image"
date: 2009-12-11
forum: The Cafe
---

### Post by sudoer541 on 2009-12-11
I am about to install windows 7 on my computer and I was wondering is there a software that can make an image of my xp installation?

---

### Post by adaucourt on 2009-12-11
> **sudoer541 said:**
> I am about to install windows 7 on my computer and I was wondering is there a software that can make an image of my xp installation?

vmware converter
[http://www.vmware.com/download/converter/getconverter.html](http://www.vmware.com/download/converter/getconverter.html)

---

### Post by NoaHall on 2009-12-11
Either back it up from Windows XP using the backup and restore centre, or try a Windows Forum

And by image, do you mean a backup of how your system currently is, or making a image to run on VirtualBox/vmware?

---

### Post by alphaniner on 2009-12-11
What kind of image?  Do you want something that can be virtualized, or just something that you could restore to the physical machine?  If the latter, I suggest using ntfsclone.  It's on the [System Rescue CD]("www.sysresccd.org") Live CD and I use it frequently.

---

### Post by Tristam Green on 2009-12-11
Symantec Ghost.

---

### Post by sudoer541 on 2009-12-11
> **alphaniner said:**
> What kind of image?  Do you want something that can be virtualized, or just something that you could restore to the physical machine?  If the latter, I suggest using ntfsclone.  It's on the [System Rescue CD]("http://www.sysresccd.org") Live CD and I use it frequently.


non-virtual

is it possible to install windows 7 with xp like using a partitioner and making room for windows 7 on my xp hard disk? 

what are my options?

---

### Post by forrestcupp on 2009-12-11
Check out [Macrium Reflect](http://www.macrium.com/ReflectFree.asp).  They have a free version that will let you save your image onto CDs or DVDs.  You can even run it from within Windows.  Then it also has a Linux based live CD to restore your system if you need to.

---

### Post by Techsnap on 2009-12-11
You're looking for something like PING:

[http://ping.windowsdream.com/](http://ping.windowsdream.com/)

It will make an exact image of your hard drive which can choose where to store/burn, you can then restore this if you choose to.

---

### Post by FuturePilot on 2009-12-11
Clonezilla

---

### Post by sudoer541 on 2009-12-11
I have one more option: 

I want to tripple boot ubuntu 9.04, windows xp sp2 and windows 7 all 32bit

I just downloaded the easus partition manager and I am willing to give some space from windows xp disk to 7. ubuntu is on a separate disk (secondary slave)

how can I prevent booting problems (GRUB) and corruptions of files and OSes?

---

### Post by puzzler995 on 2009-12-11
how do you make a virtual image? that would give3 my ubuntu install more room. thx

---

### Post by u.b.u.n.t.u on 2009-12-11
> **sudoer541 said:**
> I am about to install windows 7 on my computer and I was wondering is there a software that can make an image of my xp installation?

I use True Image. Stay with version 10. I actually have a free badged version provided by Seagate, whose HDDs I use. Look for "Seagate DiscWizard".

Alternatively Clonezilla.

---

### Post by sudoer541 on 2009-12-11
ok so everything is good. Now when I try to install windows 7. I get an error during the installation.
It asks me for device drivers. and I cant go any further without installing them.

Is my PC too old for windows 7?
I have AMD athlon 64 with 1 GB ram and ATI 128 MB card (model 9250) 
I have two hard disks one for xp (main) and one for ubuntu (master slave)

what am I doing wrong?
btw I saw on a video on youtube that windows7 can run on much older PCs than mine.

---

### Post by murderslastcrow on 2009-12-11
Windows just doesn't have drivers for some XP-compatible machines. I had the same problems- sometimes they're just not available.

You may have to install the XP driver in compatibility mode, or just buy some new hardware. Or, you know, run it in VirtualBox (lulz).

---

### Post by sudoer541 on 2009-12-11
Can I download the vista drivers and let windows 7 install them during installation?
I have a discontinued video card so is there a workaround for that?

---

### Post by handy on 2009-12-11
> **FuturePilot said:**
> Clonezilla

+1.

I used to use Ghost for backing up customers windows systems, (mostly to enable quick recovery in an emergency).

Recently I cloned the internal 320GB drive in my iMac to a 1.5TB drive, using Clonezilla.  The original drive was near full, over 290GB & it had fat32, HPS+, 2 x Ext3 & JFS file systems on it.  Clonezilla used a variety of open-source tools, applying different tools to different file systems.  It did the job in about 4.5 hours & when I installed the new drive in the iMac I just had to do a very quick sync of the partitions for rEFIt's benefit & everything has been working like a charm ever since.

I installed the source & destination drives into another machine & booted the Clonezilla LiveCD to perform the operation, their are a variety of other ways also available with Clonezilla.

There are also a variety of options, re. cloning entire drives (as I did) or just selected partitions, creating images etc.

Clonezilla is also easy & straight forward to use.

---

### Post by sudoer541 on 2009-12-11
anyone know a workaround to install windows 7 on a 5~ year old pc? 
I saw plenty of videos on youtube running windows 7 on a much older computer than mine.

---

### Post by -grubby on 2009-12-11
> **sudoer541 said:**
> anyone know a workaround to install windows 7 on a 5~ year old pc? 
I saw plenty of videos on youtube running windows 7 on a much older computer than mine.

Just try it. I had Windows 7 running on a 5 year old PC with 768 MB of RAM and a 1.8 Ghz Sempron. Aero didn't run very well on the GeForce 6100 but it turned itself off anyways, so it was just me testing how it worked.

Right now I have Windows 7 running on a different, but similar in age PC, with 1.2 GB of RAM, an older ATI card (can't remember it specifically), and a Pentium 4 at 2.8 ghz.

---

### Post by K.Mandla on 2009-12-11
> **FuturePilot said:**
> Clonezilla
Another +1. Clonezilla is great stuff.

---

### Post by sudoer541 on 2009-12-11
> **-grubby said:**
> Just try it. I had Windows 7 running on a 5 year old PC with 768 MB of RAM and a 1.8 Ghz Sempron. Aero didn't run very well on the GeForce 6100 but it turned itself off anyways, so it was just me testing how it worked.

Right now I have Windows 7 running on a different, but similar in age PC, with 1.2 GB of RAM, an older ATI card (can't remember it specifically), and a Pentium 4 at 2.8 ghz.

did win 7 ask you for **missing device drivers** during installation? 
I cant install windows 7 until I find the drivers that is asking me.
btw win7 is not telling me what drivers it needs specifically.

---

### Post by cariboo on 2009-12-11
This has become a how do I install windows 7 thread. Thread closed.

---

