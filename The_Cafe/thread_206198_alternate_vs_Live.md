---
title: "alternate vs Live"
date: 2006-06-29
forum: The Cafe
---

### Post by brentoboy on 2006-06-29
Ok, so what is your favorite way to install a new copy of ubuntu?


OOPS - could someone please move this to the **cummunity discussion** area where it belongs.

---

### Post by ahaslam on 2006-06-29
[QUOTE=brentoboy]Ok, so what is your favorite way to install a new copy of ubuntu?[/QUOTE]
I found the 'live' cd offers a very fast & simple install. The live cd could also serve as a recovery tool, among other things.
I would recommend the live cd to anyone with 256MB (or more) of RAM, I've heard of problems with older/slower hardware. In this case I would recommend Xubuntu or the 'alternate' install disc.

---

### Post by barbarian on 2006-06-29
The only difference is, that Alternate CD for older machines, IMHO.

---

### Post by woedend on 2006-06-29
I liked alternate MUCH better...but I must say I loved being able to run ubuntu from the disk and install packages and download things from the live CD when my hard drive died and was removed.
But, I wish the gui installer didn't load every service by default, it takes 5 minutes to boot for geebs sake.

---

### Post by az on 2006-06-29
I like that the default cd is the Desktop cd and that is what people get when they order Shipit cds.

I don't have a favorite, though.  It rocks to have the choice!  "Use the right tool for the right job." (Scotty)


And BTW, the expert install is bollocks. Nobody should use it unless one part of the installer does not play nice with your box and you need to tweak it by hand.  The *only* time someone should use the expert installer is when the traditional ways keep failing and they want to debug.

People shouldn't pimp the expert install, since it often just installs a broken system and people end up blaming the distro.  The expert install does less, not more.

It's also tedious and boring.

'nuff said.

---

### Post by Kilz on 2006-06-29
The live cd always hangs on me. The text based installer works flawless.  :grin:

---

### Post by mlind on 2006-06-29
alternate. 

less error prone because it's more mature. LiveCD installer was bit rushed.
I had the impression that live method doesn't support lvm partitioning yet?

---

### Post by aamukahvi on 2006-06-30
I couldn't partition my drive with the Live CD (maybe I'm just stupid). A separate /home is a *musthave*. With the alternate CD, no probs.

---

### Post by yatt on 2006-06-30
[QUOTE=aamukahvi]I couldn't partition my drive with the Live CD (maybe I'm just stupid). A separate /home is a *musthave*. With the alternate CD, no probs.[/QUOTE]
Seperate /home and vfat ftw. All the livecd could do was a giant Ext3 that took up all the remaining space (even if I told it to do a 100MB ReiserFS, I got a 40GB Ext3).

---

### Post by asimon on 2006-06-30
My choice is the alternate installer. I think it was a failure to make the Live CD installer the default. It's not mature, has too many bugs, too many missing features. At least I couldn't use the Live CD for installation at all.

---

### Post by yaztromo on 2006-06-30
Prefer the alternate CD for two reasons

- More powerful partioning program. (The livecd one crashed and was just generally crap and unintuitive)
- Availability of ReiserFS.

EDIT:
I see the GUI partioner is everyones main gripe too.

---

### Post by bluenova on 2006-06-30
Normally, I would choose the Live -GUI but on a couple of machines it hasn't worked (or even booted the GUI, just freezes) and I've had to revert to the Atl Disk.

---

### Post by %hMa@?b&lt;C on 2006-06-30
I wanted to do the "live" but it would not run on my hardware. Probably something with my video card. I had to alternate cd and go from there.

---

### Post by hizaguchi on 2006-06-30
Server install and add stuff later with aptitude.  I discovered last night that if I pick the right packages I can cut my memory usage by around 50 megs without losing anything that matters.

---

### Post by tsb on 2006-06-30
The Live CD would be OK if you could choose ReiserFS.  Why they left it or is beyond me.

---

### Post by lexxonnet on 2006-07-02
I prefer the alternate install simply because QTparted on the kubuntu live cd is really bad! I cant format to ReiserFS(I'm sure Gparted did this), and also it just takes too long to load the desktop, and then load the install...

The alternate one is so much better, but then again... new users would love the desktop installer :)

---

### Post by K.Mandla on 2006-07-02
I got started on Arch linux a little bit ago and I find it more gratifying now to start with an Ubuntu server installation, drop out the packages I don't use, then start stacking stuff on top. It's a bass-ackwards way of doing it, but the results are interesting.

---

### Post by G Morgan on 2006-07-02
The live CD would be useful if you can do anything with it. As it is unless you want a full HDD mono distro setup use the alternate CD. A text based installer just makes more sense and in the future Canonical would be well advised to include a text based installer on the live CD for those of us that have needs beyond the default.

It's really annoying, my CD-R is playing up and ship it only sends discs that work on more modern machines. I thought the point was to be able to reach as many people as possible how is making older hardware worthless supposed to achieve that.

---

### Post by benplaut on 2006-07-02
the fstab setup in the livecd is HORRIBLE.  Horrible!

you can't do anything with it!!

---

### Post by Steve1961 on 2006-07-02
I've heard that the live cd doesn't give you the option of installing grub in the root partition rather than the mbr, so I used the alternative cd instead.

---

### Post by Ubunted on 2006-07-02
Live CD installer.

Faster, lets me surf while it works, nice and intuitive and doesn't scare new users like a command line can.

---

### Post by maagimies on 2006-07-02
Alternate.
I just can't live without LVM and ReiserFS.
Although if these 2 would work with the live installer, I would surely use it. Livecd's were my favorite way of installing Gentoo too, because you can surf the net while you install :)
And I've heard several horror stories from the live install :-|

---

### Post by Hyperknuck on 2006-07-03
Alternative...
It just starts quicker...
But i think the live cd is nice too... (so you can browse while installing... :p )

When you NEED your pc when installing, you should use Live, but when you just want do install everything quickly, choose alternative..

---

### Post by GuyveR800 on 2006-07-05
[QUOTE=yaztromo]Prefer the alternate CD for two reasons

- More powerful partioning program. (The livecd one crashed and was just generally crap and unintuitive)
- Availability of ReiserFS.

EDIT:
I see the GUI partioner is everyones main gripe too.[/QUOTE]

I managed to get the LiveCD installer to use ReiserFS, but it was a pain. And it tried to reformat my Windows NTFS partitions! I had move back/forwards a few times between the partitioner and the formatter step and manually correct the choices it made. No such issues with the text-mode installer.

It would be a HUGE improvement if you could just set the filesystem in the partitioning step, like it works in the text-mode installer.

Another problem with the LiveCD was that it didn't detect my Samsung SyncMaster 957MB so I was stuck at 640x480, which is too small to use the installer! (I had to edit xorg.conf before I could use it)

I still voted for the LiveCD installer, because with these problems fixed it's great.

---

