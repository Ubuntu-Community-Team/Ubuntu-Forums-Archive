---
title: "Any laptops without hidden partitons"
date: 2008-08-03
forum: The Cafe
---

### Post by PCessna on 2008-08-03
Hey all,

I'm looking to see about a newer laptop, but so many brands hide their partitons in the Windows Registry, that it makes it hard to not only install another version of Windows or re-installl windows, but likely to Install windows.

Someone said HP locks theirs, Gateway hides, seen some about acer hiding.

Anyone know a good brand? IBM Possibly doesn't hide theirs (lenvo)

---

### Post by LaRoza on 2008-08-03
Get a Thinkpad with Linux on it.

---

### Post by PCessna on 2008-08-03
> **LaRoza said:**
> Get a Thinkpad with Linux on it.

Short and sweet good reply :D

---

### Post by lisati on 2008-08-03
My two-year old Toshiba laptop came with a recovery DVD instead of a recovery partition. I've no idea if they still use that approach.

---

### Post by PCessna on 2008-08-03
Can anyone link me their, It seems non obvious on their site, or do I need my Vanilla tea D:

---

### Post by PCessna on 2008-08-03
> **PCessna said:**
> Can anyone link me their, It seems non obvious on their site, or do I need my Vanilla tea D:

SUSE Linux? I'ma be sick, Hell no, If I got one it'd have Ubuntu in 3 min.

---

### Post by arpanaut on 2008-08-03
> **PCessna said:**
> SUSE Linux? I'ma be sick, Hell no, If I got one it'd have Ubuntu in 3 min.

At least you'd not have to deal with Windows favoring, Linux blocking "malware", and you could be pretty sure that the hardware is supported.

---

### Post by PCessna on 2008-08-03
> **arpanaut said:**
> At least you'd not have to deal with Windows favoring, Linux blocking "malware", and you could be pretty sure that the hardware is supported.

What..s

---

### Post by arpanaut on 2008-08-03
If you get any laptop with any version of Linux on it, that would be true.
I've got a 2 year old Compaq that I had no problem re-partitioning and getting a dual boot going.  I even was able to keep Quick Play working for the windows set-up

I don't think it's that big of an issue for newer systems, Vista is even more tolerant of coexisting with other OS...

And if you are just going to blow away the stock OS it is not going to make any difference anyway if you do a full format of the drive and install whatever... Just do your homework on the hardware, It will save you a lot of grief!

---

### Post by wrtpeeps on 2008-08-03
> **PCessna said:**
> Hey all,

I'm looking to see about a newer laptop, but so many brands hide their partitons in the Windows Registry, that it makes it hard to not only install another version of Windows or re-installl windows, but likely to Install windows.

Someone said HP locks theirs, Gateway hides, seen some about acer hiding.

Anyone know a good brand? IBM Possibly doesn't hide theirs (lenvo)

Just buy one and format it?

---

### Post by jflaker on 2008-08-03
> **PCessna said:**
> Hey all,

I'm looking to see about a newer laptop, but so many brands hide their partitons in the Windows Registry, that it makes it hard to not only install another version of Windows or re-installl windows, but likely to Install windows.

Someone said HP locks theirs, Gateway hides, seen some about acer hiding.

Anyone know a good brand? IBM Possibly doesn't hide theirs (lenvo)

ANY partition can be blown away.  When you install, you can opt to use the entire disk and the installer will blow away all partitions and partition it for Linux.  I have never seen a disk in 20 years that could not be repartitioned unless the drive was fubar'd

---

### Post by PCessna on 2008-08-03
> **jflaker said:**
> ANY partition can be blown away.  When you install, you can opt to use the entire disk and the installer will blow away all partitions and partition it for Linux.  I have never seen a disk in 20 years that could not be repartitioned unless the drive was fubar'd
So Linux just needs to know it see a HD? Because if I put XP disk on this computer, It will say

NO HD
No Partitions

Or not list any.

It's just Windows that can blow away the registry's hiding games, eh?

---

### Post by Icehuck on 2008-08-03
I have a HP laptop(bought in December) and the recovery partition was in no way hidden from me. I saw it removed it and recovered the space with no issues while in Windows.

---

### Post by LookTJ on 2008-08-03
These "hidden" partitions are not hidden, but are recovery partitions. Most recovery partitions use FAT file systems(at least the ones I used). So it's easily deletable, boot gparted and delete :)

---

### Post by jflaker on 2008-08-03
> **PCessna said:**
> So Linux just needs to know it see a HD? Because if I put XP disk on this computer, It will say

NO HD
No Partitions

Or not list any.

It's just Windows that can blow away the registry's hiding games, eh?

You can use the livecd to resize any of the partition or delete them altogether....Windows is saying there is no room for a NTFS partition.  If you are installing Ubuntu you can choose to resize the partitions or just use the whole disk.......

If I am not making sense it may be that I didn't understand what you want to do.

---

### Post by FuturePilot on 2008-08-03
> **PCessna said:**
> So Linux just needs to know it see a HD? Because if I put XP disk on this computer, It will say

NO HD
No Partitions

Or not list any.

It's just Windows that can blow away the registry's hiding games, eh?

From experience XP only says that if you have a SATA drive.

---

### Post by LaRoza on 2008-08-04
It actually is possible to have hidden partitions that cannot be seen.

---

### Post by p_quarles on 2008-08-04
> **FuturePilot said:**
> From experience XP only says that if you have a SATA drive.
That's correct. The XP installation disk does not contain the drivers necessary for reading or writing a SATA disk.

This has nothing to do with partitioning.
> **LaRoza said:**
> It actually is possible to have hidden partitions that cannot be seen.
The ways I know of require the use of an logical volume tool, i.e., software. So, the worst they could do is keep you from accessing it. You can certainly still format the disk or overwrite the "hidden" partition.

---

### Post by LaRoza on 2008-08-04
> **p_quarles said:**
> 
The ways I know of require the use of an logical volume tool, i.e., software. So, the worst they could do is keep you from accessing it. You can certainly still format the disk or overwrite the "hidden" partition.

[http://en.wikipedia.org/wiki/Host_Protected_Area](http://en.wikipedia.org/wiki/Host_Protected_Area)

---

### Post by Barrucadu on 2008-08-04
Toshiba laptops don't have hidden/recovery partitions - they use the good old fashioned recovery disc approach :)

---

### Post by PCessna on 2008-08-04
> **Barrucadu said:**
> Toshiba laptops don't have hidden/recovery partitions - they use the good old fashioned recovery disc approach :)

Yeah,  but for Laptops, If I can't get an Apple, I'd get Gateway or HP. HP makes me sick. I'd even get a Dell with Ubuntu. Dell isn't too bad. Comaq + Toshiba = Sickningly unawesome D:

I know Gateway plays hiding games, But someone said HP just locks.

I don't know what I can use to format over hidden partitions, Like this comp im using now, Recovery and Main partition is completly hidden, Nothing but somehow wubi and Vista can detect I even have a HARD DRIVE. I use Wubi (yeah I know :[), 64-bit ubuntu. 32-bit said 'Can't create swap space', not matter what. 64-bit installed and was up and running in a couple min (what im using now). It was also only because Wubi couldn't connect to 32-bit mirror  :D

This computer's warranty has 2 more years, and I don't need Gateway to deny helping mew with any Vista issues or hardware issues if I truly install Ubuntu on this computer, So I'm gonna wait and keep with Wubi.

---

### Post by plb on 2008-08-19
I just picked up a toshiba satellite a215 and it has no recovery partition...just a disk.

---

### Post by andamaru on 2008-08-19
My Gateway came with a recovery partition + a QEM copy of windows xp, and you can make a copy of the recovery partition with a tool they provided. Then I got a linux disk and wiped the hard drive.

---

### Post by Nepherte on 2008-08-19
I have a Sony Vaio. It comes with a recovery partition, as so many laptops. I just burned the partition on two cds (Sony gives you a tool for it) and removed the partition.

---

### Post by Daveski on 2008-08-19
> **PCessna said:**
> This computer's warranty has 2 more years, and I don't need Gateway to deny helping mew with any Vista issues or hardware issues if I truly install Ubuntu on this computer, So I'm gonna wait and keep with Wubi.

If it is a standard 2.5" HDD and it is easy to remove, then why not put the current drive in a box and buy a new one? Pop it in the laptop and format it / create as many Linux partitions as you like. If you need to call for help or invoke a warranty call, just bung the old drive back in.

---

