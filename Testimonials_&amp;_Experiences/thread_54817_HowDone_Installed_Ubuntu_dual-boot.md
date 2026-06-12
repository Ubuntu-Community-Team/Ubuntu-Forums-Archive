---
title: "HowDone: Installed Ubuntu dual-boot"
date: 2005-08-06
forum: Testimonials &amp; Experiences
---

### Post by edwina on 2005-08-06
Not a question, but seeing as I managed to get Ubuntu dual-booting quite happily I thought it be worth setting-out how I did it. When I was messing about, I found it hard to find my exact problem so perhaps this will help somebody ...

1) Already had XP on a partition, with an empty, unformatted partition left free for Ubuntu (I did a little forward planning for once).

1.5) Changed my SATA hard-drive (my only hard-drive) to "Enhanced" in the BIOS, otherwise Ubuntu couldn't see it.

2) Tried to install Ubuntu on the spare partition and completely stuffed it up. Was trying to avoid messing with the Master Boot Record (MBR). Also didn't know what kind of format (ext2, fat, whatever) to use. Also didn't know where to mount it ("/..." wasn't very helpful).

3) Couldn't boot machine. Didn't want to mess with MBR via Knoppix, as MBR is on an NTFS partition.  ](*,) 

4) Used XP CD to boot into recovery mode. Tried "fixmbr" and "fixboot" but made no difference. Could see that MBR was pointing towards the incomplete/stuffed-up Ubuntu partition, not the XP partition, Didn't know how to change it. Panicked. Up until the small hours faffing about. Fortunately I had an ancient machine to run the internet through and do some more research.

5) Installed XP over Ubuntu, so that I could at least boot my machine. MBR automatically fixed by XP installation. Old XP installation and new one now available on Windows Boot Loader (whatever it's called).

6) Did more research. Installed Ubuntu over my new XP installation, this time using ext3 format disk and mounting as "/" (which I now realise is "root", which is for the main linux set-up). Set a boot flag, as advised by the help menu within the Ubuntu installer, and allowed GRUB to reside on my MBR.

7) Sweeeeeet! Ubuntu booted up happily.  \\:D/ 

8) Did some more research. Amended my fstab to auto-mount my XP partition as read-only (/dev/sda1       /media/WinXP    ntfs    user,ro,noexec,nls=utf8,umask=0222     0 0)

[I]note: I found WIKI page to be useless when it comes to mounting other partitions, but have since found:-
[https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions](https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions)[/I]

9) Deleted boot-loader reference to second XP installation, which no longer existed. Did that in XP, via right-click on My Computer/Advanced/Start-up and recovery/Edit.

10) Edited GRUB via "sudo gedit /boot/grub/menu.lst" to put XP at the top of the list, so that my wife doesn't throw a fit when it auto-boots into Ubuntu after 5 seconds.

That was it. Strangely, the effort of installing has got me up to speed on some basic commands. I had given up on Ubuntu previously, but thought I'd try it again.

It was still frustrating and, frankly, confusing that I couldn't play DVDs or MP3s without installing a few other things. That said, once you know where to look Synaptic makes it really very easy to pull in all of the neccessary files to get things working. I also understand that Ubuntu has restricted itself to totally open, free software by default, which makes sense in many ways.

Thanks for all of your help, Ubuntu forum and developers. I hope that this does somebody some good.

Ed

---

### Post by shinatru on 2006-10-18
Can you send me the step by step procedures (wilber06@smartwifi.com.ph) in dual booting xp and linux. I already had xp on my PC. Please help me guys, I spent almost a week in reformatting my OS, Im afraid to mess it up. Just send me the procedures on mu email address, I still need to visit other forums to see some informations about my problem. I will really appreciate your help. Thanks.

---

### Post by gn2 on 2006-10-18
This may be interesting: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by aysiu on 2006-10-18
I'm moving this to Testimonials.

To shinatru, if you're looking for good dual-boot guides with screenshots, try these:

**Desktop CD**: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

**Alternate CD**: [http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

---

