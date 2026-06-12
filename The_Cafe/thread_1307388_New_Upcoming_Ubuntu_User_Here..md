---
title: "New Upcoming Ubuntu User Here."
date: 2009-10-31
forum: The Cafe
---

### Post by Kronus_Arm on 2009-10-31
Hi!

Call me by my username Kronus_Arm (Joel), I'm a new and upcoming Ubuntu user, as of this writing I am downloading a copy of the OS. I'm going to be a former Windows XP user, and I wanted to experience, just experience, on what a Linux user feels like. :)

An online friend of mine, while we were chatting, introduced and recommended me Ubuntu as one of the best Linux kernel distros out there. 

I've heard wondrous things about using Ubuntu across from different tech websites, this aspired me to give this thing a go.

I'm really looking forward to enjoy using Ubuntu as much as I enjoyed using Windows XP for the past 7 years now, and of course enjoy hanging out at this forum. ;)

By the way, a question comes in my mind: How do I Install the latest Ubuntu (9.10) via a Virtual Hard Drive? I'm using Daemon Tools Lite for WinXP.

---

### Post by CorruptedRonin on 2009-10-31
Congrats on making the move. I made the move from XP to Ubuntu about a month ago and it's great, you'll enjoy it! On the matter of the question, I can't answer that because I'm not running on a virtual machine, so sorry but I can't help.

---

### Post by Kronus_Arm on 2009-10-31
> **CorruptedRonin said:**
> Congrats on making the move. I made the move from XP to Ubuntu about a month ago and it's great, you'll enjoy it! On the matter of the question, I can't answer that because I'm not running on a virtual machine, so sorry but I can't help.

Thanks, but I'm not running any Virtual Machine, I'm trying to install Ubuntu via Virtual drive. Both are different and not the same at all.

[http://en.wikipedia.org/wiki/Virtual_drive](http://en.wikipedia.org/wiki/Virtual_drive)
[http://en.wikipedia.org/wiki/Virtual_machine](http://en.wikipedia.org/wiki/Virtual_machine)

---

### Post by CorruptedRonin on 2009-10-31
Whoops, misread haha. My bad.

---

### Post by cariboo on 2009-10-31
I would really suggest you burn the iso to disk, using something like [Imgburn]("http://www.imgburn.com/"). That way you can test things with out actually having to do an installation.

Running the Live CD will allow you to check your hardware, to make sure it is compatible. Test everything you can think of, Video, Sound and Networking especially.

You will have to boot from the Live CD to do the testing, so make sure you have your BIOS set to boot from a CD.

---

### Post by Kronus_Arm on 2009-10-31
> **cariboo907 said:**
> I would really suggest you burn the iso to disk, using something like [Imgburn]("http://www.imgburn.com/"). That way you can test things with out actually having to do an installation.

Running the Live CD will allow you to check your hardware, to make sure it is compatible. Test everything you can think of, Video, Sound and Networking especially.

You will have to boot from the Live CD to do the testing, so make sure you have your BIOS set to boot from a CD.

Thanks for the tips, I guess I'll burn it then. :popcorn:

---

### Post by earthpigg on 2009-10-31
[WUBI]("http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29") is a great way to test drive Ubuntu -- A WUBI install can later be painlessly removed via Window's add/remove programs (a skill you already have), if you wish. a true dual boot install is a bit more involved to remove, but certainly not a task of epic proportions.

for the long haul, though, i strongly suggest a true [dual boot]("http://en.wikipedia.org/wiki/Dual_boot").

if/when moving from wubi to true dual boot, ask and we can walk you through the simple procedure of migrating settings and other customizations you will inevitably have built up on such a ridiculously flexible and customizable platform such as Ubuntu.

if you have a WUBI install that is still there and being used 2 weeks after installing, then the test drive is over and it's time to dual boot properly.

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-10-31
+1 for wubi

---

### Post by Khakilang on 2009-10-31
I too was Window XP user just like you and only recently install Ubuntu on my old notebook. Download from the website as an ISO image and burn into a CD and install. If you have an old computer lying around why not give it a try and rejuvenate your old PC or notebook. You will be surprise how well it run.

---

### Post by PorkyPie on 2009-10-31
I started dual booting Vista and Hardy Heron, and then I decided to take windows off. Now, I'm using Karmic, no windows at all.

I think you'll like Ubuntu. :)

---

### Post by Kronus_Arm on 2009-10-31
> **earthpigg said:**
> [WUBI]("http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29") is a great way to test drive Ubuntu -- A WUBI install can later be painlessly removed via Window's add/remove programs (a skill you already have), if you wish. a true dual boot install is a bit more involved to remove, but certainly not a task of epic proportions.

for the long haul, though, i strongly suggest a true [dual boot]("http://en.wikipedia.org/wiki/Dual_boot").

if/when moving from wubi to true dual boot, ask and we can walk you through the simple procedure of migrating settings and other customizations you will inevitably have built up on such a ridiculously flexible and customizable platform such as Ubuntu.

if you have a WUBI install that is still there and being used 2 weeks after installing, then the test drive is over and it's time to dual boot properly.

It seems very complicated for me (on my current computer skills), but I'll try.

---

### Post by earthpigg on 2009-10-31
> **Kronus_Arm said:**
> It seems very complicated for me (on my current computer skills), but I'll try.

installing via wubi is no more difficult than installing any windows video game, except you need to tell the installer how big to make your virtual hard drive. i suggest at least 15gb unless that will fill your hard drive past 85% full. if you don't that much space, let us know and we can do the cost/benefit analysis with you of devoting less space to ubuntu, and thus save you headaches down the road. :)

---

### Post by 3rdalbum on 2009-10-31
> A virtual drive in computing is a drive that to the operating system appears to be an ordinary physical disk drive,

You can't install Ubuntu to an existing "virtual drive" on Windows, because there needs to be an operating system running in order to recognise such a virtual drive.

You'd need to use Wubi, which creates a kind of virtual drive on your NTFS partition, that the GRUB bootloader can recognise and boot. On Linux, everything is a file (even a disk), so that's why this is possible here.

The "virtual drive" method used by Wubi has a number of drawbacks:

1. Lower performance (more so if the file is fragmented)
2. No hibernation because there's no swap partition
3. If Windows crashes, you can't boot Ubuntu until you have successfully booted and shut down Windows (Ubuntu can't mount your Windows NTFS filesystem if it is unclean)
4. If Windows plain stops booting, you can't boot Ubuntu at all.
5. If your Windows filesystem gets corrupted, it can affect the Ubuntu image and stop it from booting
6. You are limited to (I think) 30 gigabytes of disk space.
7. You cannot use more than 4 gigabytes of disk space if you install to a fat32 partition

I'd still recommend a real dual-boot - it's easy and fairly safe. The Ubuntu installer can resize your Windows partition and put itself into the free space. The resizing step might take a while if it has to move fragmented files out of the way. Also make sure you move the slider on the bottom bar graph to the left, so as to give Ubuntu some space.

**Always** back up **all** important data before doing **any** partitioning. I can't stress that enough.

---

### Post by Teber on 2009-10-31
hi there our new friend! the wise ones have spoken on the subject of your questions. so all i can do is say: welcome on board!

---

### Post by automaton26 on 2009-10-31
Welcome - and prepare to learn a great many things !

Using *Wubi* is usually recommended, although my experience when straying away from Windows was to try the Intrepid 8.10 LiveCD first, and then I went straight to *dual-boot*. And now I'm on Karmic 9.10 which is just brilliant, so far.

There'll be ups and downs, but you'll be glad you made the journey :)

---

### Post by The Real Dave on 2009-10-31
:KS Welcome to Ubuntu :KS

I've made the switch about a year ago, and am now a full time Linux user, XP exists only to game, everything else is disabled :) 

Enjoy the experience mate, because it most definately is an experience =]

---

### Post by NoaHall on 2009-10-31
> **Kronus_Arm said:**
> Hi!
An online friend of mine, while we were chatting, introduced and recommended me Ubuntu as one of the best Linux kernel distros out there. 


Either tell your friend he's the best converter, or that you just like the facts. Nice to see a newbie using the correct term.

---

### Post by Bölvaður on 2009-10-31
It will take approximately a year to become a normal linux user.

These are the phases you will probably go through:
- Newbie that has problems doing the most simple things like.. install software
- Linux zealot telling everyone what a wonderful thing you just discovered.. but still is kind of a beginner.
- A normal user


Most people that discover something that they think is wondrous will be all hyped about what ever that thing is and try to make others join in on that. Too bad those zealots never know what they are talking about :(


Your goal is to skip the zealot stage and do not stop using Linux until you understand it... that is when you've become a normal user that has enough knowledge to use your computer.

---

### Post by mwalimu54 on 2009-10-31
> **Bölvaður said:**
> It will take approximately a year to become a normal linux user.

These are the phases you will probably go through:
- Newbie that has problems doing the most simple things like.. install software
- Linux zealot telling everyone what a wonderful thing you just discovered.. but still is kind of a beginner.
- A normal user


Most people that discover something that they think is wondrous will be all hyped about what ever that thing is and try to make others join in on that. Too bad those zealots never know what they are talking about :(


Your goal is to skip the zealot stage and do not stop using Linux until you understand it... that is when you've become a normal user that has enough knowledge to use your computer.

+6 or 7

---

### Post by lightningfox on 2009-10-31
I used to use Windows XP, then I removed Windows XP and 
installed Ubuntu.

Ubuntu is much better than Windows in my opinion.


I think you'll enjoy Ubuntu.

---

### Post by scout4536 on 2009-10-31
I made the move to Ubuntu last month and I do not regret it.  I will never go back to windows now.  Ubuntu is just too fun, and I feel so secure using it.  Welcome to Ubuntu!:D

---

### Post by Kronus_Arm on 2009-10-31
Well, thanks everyone! I feel very welcomed. :p 

I'm still using WinXP by the way, Can I now be guided through the whole Dual-booting process now?

And thanks for answering my questions, it has been more likely clear for me, now I am more confident, with no doubts, to convert to Ubuntu Linux now.

---

### Post by mamamia88 on 2009-10-31
well i definitely suggest making a bootable usb flash drive rather than using a cd.  the cd medium is too slow

---

### Post by hoppipolla on 2009-10-31
Welcome! ^_^

---

### Post by Kronus_Arm on 2009-10-31
Will the installation work via an SD card and using a card reader?

---

### Post by HappyFeet on 2009-10-31
> **&#1057 said:**
> +1 for wubi
It's OK for testing, but......

---

### Post by ugm6hr on 2009-11-01
> **Kronus_Arm said:**
> Will the installation work via an SD card and using a card reader?

Providing your machine will boot from it, yes.

Creating a bootable SD (or USB) requires either an existing CD, downloading the Netbook Remix, or Unetbootin.

I generally recommend just using the Netbook img, since it is ready to go on your USB / SD; you will have to install some additional packages afterwards though, so if you don't have broadband, I'd go with Unetbootin.

---

