---
title: "VirtualBox error: -102  (VERR_FILE_NOT_FOUND)"
date: 2008-04-15
forum: Virtualisation
---

### Post by rififi on 2008-04-15
I had a VDI file on "media/sda1/Virtualbox/VDI/vhome.vdi" which was working very fine (Windows XP on Ubuntu Gutsy).
After I upgrade from Gutsy 32 bits to Hardy 64 bits and reinstall Virtualbox, I can't open the VDI file and get the message:

"PIIX3 cannot attach drive to the secondary master
vbox status code: -102 (VERR_FILE_NOT_FOUND)"

I tried to copy my VDI file to my Home directory (and modify the path in Virtualbox), but got the same message.

I have a very important program in the VDI file that I can't transfert to a new installation, so it's very critical for me to find a solution.

I hope you will help me and thank you for all.

---

### Post by CoryLuLu on 2008-04-16
I am actually having the same problem.

My power went out and it unmounted one of my hard drives which before was /media/disk-15 but after it remounted is now /media/disk-16 and VirtualBox was booting an ISO from there. Now it reads when I start the program

Invalid image file path: '/media/disk-15/Microsoft Windows XP Professional SP2.iso' (VERR_ACCESS_DENIED).

I cant change the setting because the program wont open until its fixed.

---

### Post by CoryLuLu on 2008-04-16
Okay, I solved the problem. 
Its actually an easy fix.

All the information is in 
/home/USER_NAME/.VirtualBox/VirtualBox.xml

Just open the file in the text editor and change or remove the paths that its not reading correctly.

NOTE: the .VirtualBox is a hidden file

---

### Post by gesy on 2008-04-16
Thanks, CoryLuLu for your answer. It doesn't work, but you gave me an idea:

I indeed delete VirtualBox and all the entries in the ".VirtualBox" and "VirtualBox" directory (but not the VDI's file), so I had to install VirtualBox as it was for the first time.

In VirtualBox, I build a new Machine and select my VDI's file and.....

It's work !!!!

Thanks a lot!

---

### Post by CoryLuLu on 2008-04-16
Yeah I guess that works too.

Well it worked fine for me, but then again I am familiar with XML and I realize that some people might have more trouble editing the file, so I guess my advise is to just delete the file and reinstall if you aren't able to fix the code manually.

---

### Post by rififi on 2008-04-16
Thanks again.

---

### Post by Ubuntwan on 2008-04-28
The post by Rytron in this thread solved this problem for me: [http://ubuntuforums.org/showthread.php?t=767451&highlight=PIIX3]("http://ubuntuforums.org/showthread.php?t=767451&highlight=PIIX3")
I had a cd mounted last time virtualbox was running and it was missing this cd now, and gave this error. In the settings menu I unchecked the mount cd/dvd drive checkbox and everything was fine again.

---

### Post by punong_bisyonaryo on 2008-05-04
Following Gesy's suggestion, I was able to get my old WinXP vbox to work (transferred from a WinXP vbox install). However, do you know how I can also add my snapshots back in?

---

### Post by gesy on 2008-05-05
No, sorry.

I even doubt it's possible.

Best Regards.

---

### Post by mrfelker on 2008-09-24
It is possible VERR_FILE_NOT_FOUND.  Enabled USB host driver.  My host is openSUSE 11.0 x64).  That's all it took.  Installing Helix 3 as I'm typing.Using VirtualBox 2.02.

Your mileage may vary.

Cheers.

Marty

---

### Post by saneojseje on 2010-08-25
> **CoryLuLu said:**
> Okay, I solved the problem. 
Its actually an easy fix.

All the information is in 
/home/USER_NAME/.VirtualBox/VirtualBox.xml

Just open the file in the text editor and change or remove the paths that its not reading correctly.

NOTE: the .VirtualBox is a hidden file

Hey CoryLuLu, though this post is old but this is of great help! You have a great idea! I experienced the same problem when I accidentally unplugged the power supply. The harddisk or medium I used was renamed with an underscore as suffix. What I did was I just edit the VirtualBox.xml file corresponding to the renamed medium. :popcorn:

---

### Post by npascut1 on 2010-10-31
I was having this problem as well, with a Vista 64 bit image running on a physical partition. When I rebooted, the disk was assigned a new ID in /dev/, from /dev/sdh* to /dev/sdb*. I took a look at the UUID's in the VirtualBox.xml file, and it didn't match up with the output from blkid. I then went into the .VirtualBox/HardDisks/<disk name>.vmdk file, saw that it was ASCII text with file, and saw that there is a place where it stores the location of the disk in /dev/. I changed it from /dev/sdh to /dev/sdb, and it booted! Something to try if your disk is reassigned to a new letter.

---

