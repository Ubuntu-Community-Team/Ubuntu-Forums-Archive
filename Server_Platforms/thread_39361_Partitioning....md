---
title: "Partitioning..."
date: 2005-06-04
forum: Server Platforms
---

### Post by Rohan on 2005-06-04
Hi guys I'm going to be using ubuntu as a file server/web/ftp/other things box and was wondering how I should go about partitioning

I have a bunch of drives that I'm going to put into LVM and one single 10gig drive outside of the LVM that will hold ubuntu itself

So... how should I partition the main drive. I've been using linux for a while now, but never really got into partitionining the drive into different system folders. Since this is a server, I thought I should start now.

Anyways.. like I said the main drive is 10gigs (more like 9.8 actual) and the computer has 512mb of ram. So how should I go about this?

Thanks

---

### Post by defkewl on 2005-06-05
At bootup time there is a choice on installing Ubuntu manually. When installing manually there's a partitioner.

---

### Post by rich on 2005-06-06
Your question doesn't have a straightforward answer (unfortunately). 

I spent a bit of time rubbing my chin about partition sizes. In the end, I went for the simplest. Until you can work out the space requirements of the file/web/other - then you can adjust on the next install. 

I like the gentoo docs, there is a nice overview here

[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=4](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=4)

I'm sure googling for partition will bring you a million answers - all different.


Rich

---

### Post by SNo0py on 2005-06-06
Right, there are a lot of different answers... but it's always good to have /var, /tmp and eventually /home on a different partition. Oh, and /boot can be a 20MB partition....

---

### Post by Gtaylor on 2005-06-06
This would be a great topic for a HOW-TO. In the case of a webserver, here's what I usually do. Assuming that I have 10 GB:

/, 750 MB to a Gig
/tmp, 400 MB
/var, 500 MB assuming your web content goes on /home
swap, 1.0 - 1.5 GB
/home, sucks up the rest of the space

For a workstation I'd just do something like:

swap, 1.0 - 1.5 GB swap
/, gets the rest

It's really not necessary to have a seperate /boot partition unless you're working with kernel development and want to preserve custom builds. But it definitely is important to have seperate /home, /tmp, and /var partitions for web servers. People can do unsavory things to fill up your logs and suck up space, which would cause problems for your entire system if the root partition filled to the brim and some program tried to do a write.

---

### Post by Rohan on 2005-06-09
thanks for all the info guys

---

### Post by garyng on 2005-06-09
I don't understand why people advice seperate /boot partition as modern day linux relies on more than the kernel image(that is installed to /boot). Without /lib/modules, the kernel is in general "incomplete".

I believe this /boot partition is a thing of the past that should be removed from any docs.

I would say two 4G partition then 2 swap area. This would be enough for having 2 ubuntu at the same time so it case you need to upgrade later(seperate installation, for parallel run), you would still have the space. And once the new one stablized, the old one can be retired and recyle in the same fashion.

The /var, /home needs to go to LVM anyway.

BTW, A typical debian server installation takes about 1.3G.

---

### Post by LordHunter317 on 2005-06-09
[QUOTE=garyng]I don't understand why people advice seperate /boot partition as modern day linux relies on more than the kernel image(that is installed to /boot).[/quote]If you're using LVM, you need to have a /boot that's not on LVM.  You cannot reliably ensure that you will be able to boot off a /boot on LVM.

>  Without /lib/modules, the kernel is in general "incomplete".It can boot without that.  Ever hear of an initrd.

> I believe this /boot partition is a thing of the past that should be removed from any docs.Perhaps if you read the documentation you'd understand why it's there.

> I would say two 4G partition then 2 swap area.Two swap areas makes no sense.

Here are my recommendations:
/ - 2 - 5 GB.  This will contain / and /usr.  Data in / is relatively tiny, 50MB tops of applications in /bin and /sbin (and usually more like 10MB) and a few megs (like 5) of data in /etc.  /usr however can be quite large, anywhere from 1GB to 5GB+ depending on what applications you're running on your box.    

If you install / on LVM and use ext3 or XFS don't be afraid to undersize.  Enlarging / if you find out you're wrong is a trivial exercise then.  

Whether you need a seperate /var is dependent on what you'll being doing.  Most people don't need a fully seperate /var but a seperate /var/www or /var/lib/mysql or /var/lib/pgsql.    Remember to account for /var/logs which will use at 50MB of space minimum, more on any real server.  This filling up / can cause all sorts of bad behavior, so it may be worthwhile to make /var/log seperate as a safety precaution.

Also, /var contains the apt cache in /var/cache/apt.  I've found that this needs at least 768MB of space to be usuable.  Be sure to reserve this space in /var or / depending on how you partition.  Also, being aggressive about running apt-get autoclean helps here too. 

The rest is role dependent, frequently.

---

### Post by garyng on 2005-06-09
Let me try :

1. I use LVM ONLY for data or that needs to exend, not for the rootfs. So in this case I still don't need seperate /boot.

2. Will you put the whole /lib/module/`uname -r` in initrd ? I doubt. Therefore, it still depends on the rootfs and as I explained in (1), I don't need rootfs to be on LVM, in fact, I don't want rootfs on LVM.

3. if swap is only used for swap, two seperate one makes no sense. However, there is things that people may want, like swsusp. Sharing swap would then steps on others foot. 

There are always case one can think of to make a seperate boot partition, but I don't find it to be convincing for most cases. How about :

what is the advantage of boot partition if I don't use LVM for rootfs ?

---

### Post by LordHunter317 on 2005-06-09
[QUOTE=garyng]1. I use LVM ONLY for data or that needs to exend, not for the rootfs. So in this case I still don't need seperate /boot.[/quote]Yes, but the point is that some situations still exist where /boot is required.  Therefore, it's perfectly valid to recommend /boot, and will probably always be valid to recommend /boot in some situations. 

Is it required in most?  No.  Are there some specific situations that require it?  Yes.  LVM is one of them.  Root RAID-5 is another.

> 2. Will you put the whole /lib/module/`uname -r` in initrd ? I doubt.You can, but there's no need.

> Therefore, it still depends on the rootfsNo, it doesn't, if you understood how an initrd works.  An initrd is an image containing enough modules to allow you to mount your real root (including the LVM modules and tools if necessary).  After which point, the fact the kernel depends on /lib/modules to be able to load other modules is irrelevant, as / is mounted.

/boot really does contain everything your kernel needs to boot.  You don't need the entire modules tree to boot.

> depending on the pr and as I explained in (1), I don't need rootfs to be on LVM, in fact, I don't want rootfs on LVM.Just because it's what you want doesn't mean it's what everyone wants.  You're using inductive logic here, and it's invalid.  You can't assume just because you do it one way that it's correct in all 
cases.

And why don't you want LVM /?  It's quite useful.

> 3. if swap is only used for swap, two seperate one makes no sense. However, there is things that people may want, like swsusp. Sharing swap would then steps on others foot. Yes, but swsup is not likely to be used on a server.

> what is the advantage of boot partition if I don't use LVM for rootfs ?You need it to do / SW RAID-5.  You may need if you have a BIOS that can't properly bootstrap the whole disk (very rare these days, but I still come across BIOSes that don't do LBA correctly, *sigh*).

---

### Post by garyng on 2005-06-09
we are switching roles :-)

I actually started as seperate "/boot" is in general not needed(which you seemed to agreed) but the wording was definitely wrong, stand corrected.

But you seemed to be doing the same thing when saying 2 swap makes NO SENSE. I explained why it make sense. Again, not many people may use it but that again is up to individual :-)

Now for another scenario(for the sake of why it make sense), seperate swap could potentially allows forensic if that distro died.

My understanding of seperate /boot is that it gives the loader an easier way to find the kernel/initrd but it is usually recommended(as some don't ask, it is good for you rule) without explaining why it is needed. For those who needs it, they will know and don't need to be told(as it is a necessity, not an option). For those who don't need it, what is the point of recommending it ?

As for why I don't like LVM for rootfs, I prefer to treat them as one single partition(or loopback file) which I can easily move and peek. That way, I can boot with almost anything(say a KNOPPIX CD) and fix things.

---

### Post by LordHunter317 on 2005-06-09
[QUOTE=garyng]Now for another scenario(for the sake of why it make sense), seperate swap could potentially allows forensic if that distro died.[/quote]Not useful forsenics.  Linux doesn't have kernel debugging tools where having a complete dump of swap is going to yield any new information.

> For those who don't need it, what is the point of recommending it ?Because it's eaiser to make a blanket recommendation than explain all the situations?  It's not like having a /boot is a bad thing or a real disadvantage.

> As for why I don't like LVM for rootfs, I prefer to treat them as one single partition(or loopback file) which I can easily move and peek. That way, I can boot with almost anything(say a KNOPPIX CD) and fix things.You can do this just as easily with LVM.   Your reasoning here doesn't make any sense.

---

### Post by garyng on 2005-06-09
forensic is forensic, whether there is tools available(and what to do with it) is not up to me or you to decide. For some, even just dumping the content byte by byte is useful. 

In order to fix a random distro(rootfs) installed on LVM, I need to find something else that first knows about LVM, then I may need to reconstruct the volumes too(I am not sure if the sequence of adding PV to VG matters).

With the rootfs(and also the kernel on the same partition), I can almost grab any live CD or whatever quick boot distro and peek into a regular fs on regular partition. 

As for seperate boot has no  disadvantage, what if I change the recommendation to :

"Whatever HD you buy, just leave the first 2G alone and don't touch it, just trust me but I am not going to tell you why right now ". This also has no disadvantage or a bad thing.

---

### Post by LordHunter317 on 2005-06-09
[QUOTE=garyng]forensic is forensic, whether there is tools available(and what to do with it) is not up to me or you to decide.[/quote]But it is. 

>  For some, even just dumping the content byte by byte is useful.The very **small** class of users where this is true already know they potentially need a second swap parition and would have ignored  what I've said. 

If you were going to do it that way, which wouldn't make much sense to.

> In order to fix a random distro(rootfs) installed on LVM, I need to find something else that first knows about LVM,And every rescue CD I've used in recent memory has the LVM tools.

>  then I may need to reconstruct the volumes too(I am not sure if the sequence of adding PV to VG matters).No, you won't.  The LVM tools handle all this for you. 

You really need to go read up on these things you lambast so heavily, as you don't seem to understand them, how they're designed, how they're implemented, or most importantly, how to use them.

> This also has no disadvantage or a bad thing.Not true.  It's unecessarily wasting space without reason.  Having a /boot doesn't do that.

---

### Post by garyng on 2005-06-09
A boot partition is not wasting space ? Unless you can use it to full, you are wasting space as that is something cannot be shared(unlike when /boot is on the same rootfs).

In fact, I would rather create one more swap for say 250M so I can use it initially as swap and if and when I need a seperate partition for boot, use that instead. This way, I waste no space as when I don't need seperate boot and turn it into one when I need to.

Still no convincing reason of why a seperate boot partition when not needed.

I have one rescue CD that I burnt 2 years ago that I used happily don't. I have an USB boot disk that don't. Can I find one that can ? Of course.

It is a matter of convenience.

What have I lambast heavily ? LVM ? I believed I recommend to use it as well, just I personally don't use it on rootfs.

Seperate boot partition when the need is not there yet ? I still can't find a scenario that makes a difference before I need that.

---

### Post by LordHunter317 on 2005-06-09
[QUOTE=garyng]A boot partition is not wasting space ?[/quote]The tiny bit of space that's being wasted can generally be ignored.  It's not like /boot ever needs to be larger than about 50M.  

2G is 40x larger than 50M.  

> This way, I waste no space as when I don't need seperate boot and turn it into one when I need to.Except for the fact it's not likely you're really using that swap.  So if we're talking using every last bit of data storage available, having more swap than needed is still wasteful.

> I believed I recommend to use it as well, just I personally don't use it on rootfs.Yes, but your reasons for not doing so are not logical .

> I still can't find a scenario that makes a difference before I need that.As I said eariler, I believe most people do it because it's eaiser to make blanket recommendations.

---

### Post by garyng on 2005-06-09
I use the 2G as an example, it can be just 50M or whatever size. The point I wanted to make is a seperate /boot(when not needed) is no difference than doing the same as leaving certain space alone on the disk.

Why  I cannot use the swap space fully ? Instead of one 500M swap, I make it 2 250M. Or may be 50M and 450M.

As for my reasoning of not using LVM on /, the only reason I gave is that I want to have them as one single large block of bytes that EASE(not as if cannot otherwise be done) my way of handling things. I can't see what logic is involved here so arguing whether it is logical seems to be strange. 

you said root on LVM is very useful, I am curious to know why. As my be there is some usage pattern that I haven't encountered that make it so. RAID on root, I can understand but LVM I cannot see a particular advantage(as I consider rootfs to be very static). Of course, for some, it could be as simple as I want everything be under LVM, except swap and boot, which I don't find the need.

---

### Post by LordHunter317 on 2005-06-09
[QUOTE=garyngWhy  I cannot use the swap space fully ?[/quote]Because if you have the swap with the potential intent to conver it latter, ytou still need enough swap to run your system. Implying the second partition is excessive.

> As for my reasoning of not using LVM on /, the only reason I gave is that I want to have them as one single large block of bytes that EASE(not as if cannot otherwise be done) my way of handling things.So it's no more than personal perference?  That's a valid reason.  Trying to extropolate that to other things is silly and illogical though.

And my point in response that is simply that having / off LVM isn't really making your life eaiser.  It's not like finding rescue tools that support LVM is hard or anything.  I fail to see the gain here and you've not given any valid gains.

> you said root on LVM is very useful, I am curious to know why.I can expand / if necessary.  I can leverage all the other tools LVM provides (mirroring, snapshots, etc.).  It means all disk partitions (save for pesky /boot) are together at once.  It makes managing the physical disk / is stored on much eaiser.

> I can understand but LVM I cannot see a particular advantage(as I consider rootfs to be very static).On many system / is the most changing filesystem.

---

### Post by garyng on 2005-06-09
Having / off LVM make MY life easier, I haven't said that make YOURS or anyone else. I gave the reason, you can agree, you can disagree but I don't see any "logic" involve here. 

As I expected, it seems to be "your" preference(I assume you follow it and use LVM/RAID on every single setup you have done, if not I would be very interested to know why not) and potential advantage of LVM on /. 

This is no more than preference, it make YOUR life easier.

---

### Post by LordHunter317 on 2005-06-10
[QUOTE=garyng]Having / off LVM make MY life easier, I haven't said that make YOURS or anyone else.[/quote]

>  I gave the reason, you can agree, you can disagree but I don't see any "logic" involve here. There's more to decisions when it comes to computers than simple personal preferences.  Which is what I've been pointing out repeatedly: your personal preference doesn't having any good reasoning.  It's just a choice you've made.  But that doesn't mean it's necessarily a very good choice and I'm trying to show you the logical underpinnings of why it may not be.

> (I assume you follow it and use LVM/RAID on every single setup you have done, if not I would be very interested to know why not)All my new installs use LVM, but not RAID everywhere.  I don't have the hardware for that.

>  and potential advantage of LVM on /. It's not potential, the advantages are very real.

> This is no more than preference,Yes it is.  Not using LVM provides limitations on what you can do with your system.  That's only not an issue if you know you'll never run into those limitations.  On a desktop, you probably won't.  On a server, it's quite likely you will.

---

