---
title: "ubuntu or windows 7"
date: 2013-11-06
forum: Ubuntu, Linux and OS Chat
---

### Post by arnavkumartechno on 2013-11-06
I have been using Windows XP since a long time. I never wanted to work on any other OS. Recently I had to move on Windows 7, I found there were no much differences in both of them. Now i want to use Ubuntu (just for fun). Is it possible for me to have both the OS in my system at the same time? If yes, How?

---

### Post by TheFu on 2013-11-06
Yes.  Dual boot or virtualization.  Virtualization is less risky, but it requires a more powerful PC and more RAM.  Basically, a Core2Duo CPU or better and more than 2G of RAM is a minimal requirement to be happy with virtualization.

With virtualization, you don't need to partition the HDD.
With dual-booting, you will need to add 2 or 3 partitions to the HDD. 

So, there are many, many how-to guides for running Ubuntu under a VM on a Win7 PC. You'll figure that out. After you do it once, you will probably be unhappy with the performance since the default settings are crap, IMHO.

There are many different choices for virtualization on Windows --- vmware player, virtualbox, vmware workstation.  Most people here will point you towards virtualbox.  [http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox) has the settings to make Ubuntu work faster. With a few good decisions during VM setup, performance can be really good for non-GUI-heavy things.

If the CPU is slower than a C2D ... dual boot really is the only option. Please post run **fdisk** on Windows to dump the partition layout data and paste the results here so we can make suggestions. Ubuntu needs 10-20G of storage to be relatively happy.  Hopefully the HDD is not already using too many partitions - there is a limit which is easy to hit and will make this harder.

Please, please, please use Ubuntu 12.04, nothing newer.

---

### Post by Bucky Ball on 2013-11-06
12.04 LTS is a good place to start, yes. Download the ISO, burn a disk, boot from it, 'Try Ubuntu,' and see how it rolls.

Dual-boot. But you need space on the drive. Shrink whatever partition you need to and leave enough free space for the Ubuntu install. It will make partitions during install.

As mentioned, there are a ton of install how-tos online.

[https://duckduckgo.com/?q=dual+boot+win+7+12.04](https://duckduckgo.com/?q=dual+boot+win+7+12.04)

If you get confused, just ask. ;)

---

### Post by TheFu on 2013-11-06
> **Bucky Ball said:**
> 12.04 LTS is a good place to start, yes. Download the ISO, burn a disk, boot from it, 'Try Ubuntu,' and see how it rolls.
If you get confused, just ask. ;)
**GREAT Idea on the "Try Ubuntu" first BuckyB!**  Also, you can use a flash drive instead of burning a CD/DVD.  Start with the ISO, an empty flash drive and use a tool  like Yumi from pendrivelinux to create a bootable flash drive with Ubuntu. Flash will be 20x faster than optical media ... but still slower than HDD or SSD.  Both will give a good idea whether the hardware in the machine will be happy with Ubuntu or not.  Check video, audio, networking (wifi especially) ... using the "Try Ubuntu".

If you are really stuck, search of a local LUG - Linux Users Group - in your area.  I organize 1 and attend 2 others in my metro area. Every Sunday we meet informally and welcome people new to Linux, help them install, learn from, teach others, and make business contacts. Home and business users are welcome.  I'd like to setup an informal mentoring system, but that is harder.

Web search on "city linux LUG" to see if one is nearby. Often, Universities will have a LUG open to everyone.  We work with 2 schools and a pizza place. :0

---

### Post by Bucky Ball on 2013-11-06
LUGs, also referred to as LOCOs here. Try this:

[http://community.ubuntu.com/help-information/meeting-other-ubuntu-users/local-communities/](http://community.ubuntu.com/help-information/meeting-other-ubuntu-users/local-communities/)

There will, of course, be others, so do the suggested search from TheFu also. ;)

BTW: Trying Ubuntu from the CD/USB will NOT alter anything on your disk. You are running the OS wholly and solely from the install media (so don't panic that it's going to mess with anything).

If you like, backup what you need to and install by clicking the install icon on the desktop (or wherever it is in Unity desktop).

---

