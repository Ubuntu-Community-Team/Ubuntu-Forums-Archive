---
title: "I need a partitioning tool"
date: 2005-01-05
forum: The Cafe
---

### Post by BWF89 on 2005-01-05
After the GIMP and GTK+2 stopped working on Window$ (45 minutes spent trying to unistall & reinstall them).  I decided I want to make a Linux partition on my PC. Do you know of any programs that will let me partition the HDD without looseing everything on my Windows partition? EDIT: That don't cost money...

Please post the link...

---

### Post by gamehack on 2005-01-05
[http://www.sysresccd.org/](http://www.sysresccd.org/) Check it out :)

---

### Post by BWF89 on 2005-01-05
[QUOTE=gamehack][http://www.sysresccd.org/](http://www.sysresccd.org/) Check it out :)[/QUOTE]
It said it would take 440 minutes to take 10GB off of my 53GB partition. I'll start the process before I go to bed...

Thanks...

---

### Post by BWF89 on 2005-01-05
When you go to finalize the partition it says something like "You may loose some data". Could this potentually ruin my Windows partition so that it doesn't work as well?

---

### Post by az on 2005-01-05
Try the debian Sarge install cd.  Even just the netinstall (40 megs)

It can do lossless resizing of ntfs partitions.  This will be the next installer for Ubuntu (Hoary)

Just boot from it and make your way to the partitionning.  Select your windows partition and then select size.  Enter a smaller number.  Make it go.  Reboot after it is done...

---

### Post by BWF89 on 2005-01-05
My XP partition is FAT32. The program I'm useing is a clone of Partition Magic, what could Debian Sarge do that it couldn't?

But does "You could loose some data" mean data on the partition I am about to make or my XP one? And if I lost some XP data would it ruin the OS?

---

### Post by TravisNewman on 2005-01-05
"You could lose some data" doesn't necessarily mean anything. Whenever you're doing anything major with drives you can lose data. Hell, you can lose data when checking the drive for errors. I've never had any problems with parted (which I'm assuming is the backend of what you're using on the system rescue cd), but that doesn't mean you won't either. It's always a gamble, you just have to be willing to either take the gamble or back up everything.

---

### Post by Rancoras on 2005-01-06
[QUOTE=BWF89]But does "You could loose some data" mean data on the partition I am about to make or my XP one? And if I lost some XP data would it ruin the OS?[/QUOTE]

You backed up your data, right?   :D

---

### Post by nocturn on 2005-01-06
[QUOTE=BWF89]
But does "You could loose some data" mean data on the partition I am about to make or my XP one? And if I lost some XP data would it ruin the OS?[/QUOTE]

No further than it has already been ruined ;-) 
(sorry, it was stronger then myself)

In general, no.
These tools always give out warnings like this because such operations carry some risks.   There is no resizing tool that is 100% safe to use AFAIK.

---

### Post by HiddenWolf on 2005-01-06
[QUOTE=BWF89]After the GIMP and GTK+2 stopped working on Window$ (45 minutes spent trying to unistall & reinstall them).  I decided I want to make a Linux partition on my PC. Do you know of any programs that will let me partition the HDD without looseing everything on my Windows partition? EDIT: That don't cost money...

Please post the link...[/QUOTE]

I felt freed. 
I deleted all my windows partitions! :-)

---

### Post by BWF89 on 2005-01-06
Well my parents are still attached to Windows. When I brought up that I had downloaded a free partitioning tool my dad hostially responded "Why do you incist on screwing up the computer? We had everything running smoothly until you started putting all this crap on it". Yesterday I deleted my ADMIN-ROOT name on Windows and made everyone admin because I got tired of switching names while trying to uninstall GTK. Now we can't open up Acrobat Reader files anymore. And my parents are going to think it's all my fault...

So I'm a little too scared to partition my hard drive. If I did I'd either use Ubuntu or mabye NetBSD. Does anyone know what file system BSD uses?

---

### Post by Quest-Master on 2005-01-06
Use Ubuntu.

In the times I've reinstalled it, messed with partitions, made new ones, resized them, I haven't had a single error yet.

---

### Post by machiner on 2005-01-07
I seriously recommend that you (and everybody) download the System Rescue Disc -- It's a gentoo disk that boots "live" and has all the tools you need.

Especially parted (run_qtparted) and partimage.  There are more tools, but all I ever use is partimage.

I used the qtarted app once to resize, delete, make .. all that some partitions on my drives. I was screwing around and never lost data. NTFS, FAT-32, and ext3 file systems are what I was working with.

Qtparted resized my partition fine with no data loss, but you can also get your hands on ntfsresizer .. it's a free utility to download. I used also in the past with NO ill effects.

Important is getting out of your running file system to perform any of this work....booting to the System Rescue Disk is a terrific idea...

It also lets me setup new harddrives, or prepare a used hdd for winxp, and or fix about any error I find on a friend's box.

Good luck

---

### Post by ubuntu.daemon on 2005-01-07
If you are in need of a relaible simple partioner.  Download the knoppix 2.6 Live cd, i think that is the newest.  Any just boot it up live, and in the programs somewheer it has a partioner that runs really smooth and quick.

---

### Post by Dylanby on 2005-01-07
I downloaded the SystemRescueCD. On my comp it hangs on hotplug detection (I think).

There's also the "Ultimate Boot CD":
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

& the "Ultimate Boot CD" for Windows:
[http://www.ubcd4win.com/](http://www.ubcd4win.com/)

---

### Post by machiner on 2005-01-12
turn your usb stuff off. DO you have a camera plugged in and turned on? 

On occassion I saw a lag on my system as well from hotplug - I had my perinter and camera plugged in and turned on.

I turned off my camera and whoosh - up it booted.

---

### Post by Dylanby on 2005-01-12
It hangs when detecting my usb keyboard &/or usb trackball.

On my current comp, some live-cds work & some hang (with their default settings).

Knoppix 3.6, Gnoppix 0.8.2.2, Warty Live-CD (Morphix) all hang on hardware detection.

Suse 9.2 Live-DVD, & SimplyMEPIS work fine (really slow tho').

---

