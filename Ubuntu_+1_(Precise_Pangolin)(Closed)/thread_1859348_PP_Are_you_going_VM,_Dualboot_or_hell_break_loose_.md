---
title: "PP: Are you going VM, Dualboot or hell break loose /dev/sda1?"
date: 2011-10-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-10-13
I'm considering VM for the first weeks this time. Don't have the guts for primary OS so soon anymore LOL... And dual booting is boring, don't you think?

---

### Post by thatguruguy on 2011-10-13
I have a couple spare external hard drives, one of which I use for backups and the other I use for testing.

---

### Post by ronacc on 2011-10-13
I have a test box with 6 drives and more partitions than I (or grub) can keep track of .

---

### Post by MacUntu on 2011-10-13
Live on two productive systems. Why? Because it takes less time (testing WHILE using) and actually finds those bugs that would influence my productive systems. Often enough bugs didn't show on clean VM installs. Obviously I have backups and backup Ubuntus in place.

Come get some! :D

---

### Post by cariboo on 2011-10-13
I plan on dual booting, as I always do, With Oneiric as my stable install just in case, and Precise for everyday usage. I'll probably set up 3 machines that way.

---

### Post by effenberg0x0 on 2011-10-13
> **MacUntu said:**
> Live on two productive systems. Why? Because it takes less time (testing WHILE using) and actually finds those bugs that would influence my productive systems. Often enough bugs didn't show on clean VM installs. Obviously I have backups and backup Ubuntus in place.

Come get some! :D

I totally agree with this. I hate dual booting. And I can't have many machines (seriously, I may have DDA or something lol... I end up confused which machine is which, which is doins what, etc..)..

---

### Post by jerrylamos on 2011-10-13
1.  There are two Ubuntu's on /dev/sda, a Meerkat and an Ocelot (as well as windows 7)

2.  I have a USB hard drive /dev/sdb.  There are two Ocelots on it, one for I presume replacing oneiric with precise when the /etc/apt/sources.list files are ready.

So this is a quad boot, two on the main hard drive, and two on the USB hard drive.  I had a left over laptop 2.5" drive and bought a $20 case for it.  

Having said that, I had quite a struggle installing Ocelot from a USB stick.  It gets up to the point of putting grub on /devsdb and then gets an "error" which is undefined.  Launchpad bug #872845.  Rather complicated to recover.

Jerry

---

### Post by ventrical on 2011-10-13
I'm already there with a multi-boot system.  I have  6 other systems and most of my everyday stables are on pendrives. So I'm pushing it.  It's always been a knack of mine to push hardware to the limit. I got more hardrives laying around .. that I use them for the power magnets :)  I just love the way you can swap drives with Ubuntu installs.  

 So I'm going for the gusto.  I want to lay some rubber so to speak.

 I think about how Mark Shuttleworth rode 5 million pounds of Thunder  all the way to the International space Station on that Russian Rocket .. so , why should we hold back :)

---

### Post by VinDSL on 2011-10-13
> **effenberg0x0 said:**
> [,..]dual booting is boring, don't you think?
Dual-booting UbuMM here and, yes, it's boring, but...

I *know* I'll be happy, when the devs get back from holiday, and all *you-know-what* breaks loose.  ;)

---

### Post by ranch hand on 2011-10-13
We have, in the past, been asked what the point of testing the tool chain is.  There is little to test until after A1, this is true, or has been in the past.  The thing that we can do, and no one else can, is test the OS and, more importantly, the dailies (when they start) and the A1 ISO.

This all needs done on real hardware.  The devs work in virtualization.  The need is for hardware testing.  The more folks testing, the more diverse the hardware on which it is being tested.  VB negates this completely.

In VB what you are really testing is if VB is compatible with the dev release.  While this is by no means worthless it is not what we are really here for.

---

### Post by ubupirate on 2011-10-13
Possible vbox on desktop, or testing on my laptop.

---

### Post by linuxman94 on 2011-10-13
Gonna clone my oneiric partition and change the repos to precise.

---

### Post by TerminX on 2011-10-13
Live install on my primary workstation and on my rackmount, no VMs, dual booting or anything else.  Working around bugs is fun. :p

---

### Post by Zeta-K on 2011-10-13
7 computers in my house, all with multiple hard drives. I just throw an os in one of them whenever I need to. I have one hard drive with my music, videos, games, and schoolwork; one with ubuntu 10.04; and one with gentoo. The rest of my ten-dozen drives are re-formatted about every month. I almost never dual-boot. I've never needed to.

---

### Post by MAFoElffen on 2011-10-14
> **ranch hand said:**
> We have, in the past, been asked what the point of testing the tool chain is.  There is little to test until after A1, this is true, or has been in the past.  The thing that we can do, and no one else can, is test the OS and, more importantly, the dailies (when they start) and the A1 ISO.

This all needs done on real hardware.  The devs work in virtualization.  The need is for hardware testing.  The more folks testing, the more diverse the hardware on which it is being tested.  VB negates this completely.

In VB what you are really testing is if VB is compatible with the dev release.  While this is by no means worthless it is not what we are really here for.
+1  I really try to break it on hardware.  Virtual is not as much fun with that.

3 test boxes on desktop- 1 with nVidia... ATI and Intel GPU's.
2 servers- 1 Server on 32bit, 1 Server on 64bit.  
(They are the same test boxes i had from the last 2 go rounds...)

---

### Post by effenberg0x0 on 2011-10-14
I'm convinced off the VMs... I'll buy a KVM at least, hate having many keyboards/mouses on table lol.

Regards,
Effenberg

---

### Post by xeizo on 2011-10-14
This is perfect timing: the Linux-box just got some leftovers when I upgraded the gamingbox to i7 2600k!

**Vbox it is**, as the Linux-box now has a 45nm C2Q @ 3.2GHz with VT-d and 8GB RAM(Ubuntu seldom uses that much RAM on the desktop, so a VM is a perfect use for it). I may even place the VM on the SSD to speed it up :)

I'll continue to run Kubuntu 11.10 as the main-OS as it is quite stable by now.

---

### Post by Johnb0y on 2011-10-14
> **ventrical said:**
> I'm already there with a multi-boot system.  I have  6 other systems and most of my everyday stables are on pendrives. So I'm pushing it.  It's always been a knack of mine to push hardware to the limit. I got more hardrives laying around .. that I use them for the power magnets :)  I just love the way you can swap drives with Ubuntu installs.  

 So I'm going for the gusto.  I want to lay some rubber so to speak.

 I think about how Mark Shuttleworth rode 5 million pounds of Thunder  all the way to the International space Station on that Russian Rocket .. so , why should we hold back :)

what a way to say it... couldnt have said it better myself! lol! 

" I want to lay some rubber so to speak." lol!

---

### Post by ventrical on 2011-10-14
Here , from the automotive capital of Canada .. we lay rubber in our youth (and even when we become pcgeezers :) lol

 Ubuntu and Linux distros in general offer us the end_user a lot of latitude that we don't get from other commercial distros..

regards..

---

### Post by Gyokuro on 2011-10-15
I'm testing it on a real machine (spare hd's), VBOX,KVM, Server and desktop edition and my interest is more in LTS releases and I do not care whether something breaks :-) during dev cylces.

---

### Post by sumski on 2011-10-15
I'm going for /dev/sda - upgrading Oneiric

---

### Post by jerrylamos on 2011-10-15
> **sumski said:**
> I'm going for /dev/sda - upgrading Oneiric

sumski, 

Good luck.  Typical experience somewhere around Alpha and/or Beta images updating the "unstable" new development release will crash, even blowing up grub on /dev/sda.  The Ubuntu community wiki has a good entry on recovering grub using a live CD or live USB....

I always have running partitions available for recovery.  In this case, Pangolin is running on a USB hard drive.  I had a 2.5" hard drive laying around.  USB cases can be had for $10 to $20.  Cheap insurance.

Jerry

---

### Post by ronacc on 2011-10-15
If you have multiple drives and multi boot you can have another install write its grub to the second ( or third etc ) drives MBR and if your install on the first drive barfs big time you can switch boot drive order in BIOS and get something up and running to attempt recovery .

---

### Post by jppr on 2011-10-15
I don´t have any dual boot problems :popcorn:
I have /dev/sda1 windows 8 and /dev/sdb1 windows 7 and ubuntu 12.04

Grub menu works fine, which I choose to turn on the machine system

---

### Post by BwackNinja on 2011-10-15
Ubuntu development has been my primary partition for the past few releases. Not naive, I've been hit by bugs deleting my home folder and file-roller randomly chmod 700'ing "/". After a while, you forget that your operating system was ever supposed to "just work".

---

### Post by SushiR on 2011-10-15
On my netbook there's place for 3 OSes. I'm running Oneiric as my main system, which will (probably) became my backup sys once PP Alpha1/2 is ready. The 3rd one is a fallback of the two other ones - just in case...

---

### Post by ranch hand on 2011-10-15
> **BwackNinja said:**
> Ubuntu development has been my primary partition for the past few releases. Not naive, I've been hit by bugs deleting my home folder and file-roller randomly chmod 700'ing "/". After a while, you forget that your operating system was ever supposed to "just work".
When running dev releases as my production OS, I cheated by having 3 installs that were pretty identical.  They didn't have any other purpose than to run.  They were all updated at the same time and then I would upgrade one of them and see if it worked.  Then the second.  The one that was designated "main" was done last if the others survived.

Did have to switch "main" to one of the others a couple of times.  But I always had one running.

Boinc was installed in my /home/user directory.  All 3 had the same computer name an user name.  If I had to switch then all I had to do was grab the boinc folder and put it on the running one.  The boinc server never even new there was a change.

If you run boinc set at 99% and your OS doesn't break it is doing pretty well.  Gives all of 1% of you cpu(s) to the OS and whatever else is running.  Only lost 1/2 days worth of work in 2 dev cycles.

---

