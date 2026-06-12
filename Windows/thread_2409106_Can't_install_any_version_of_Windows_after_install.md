---
title: "Can't install any version of Windows after installing Ubuntu"
date: 2018-12-27
forum: Windows
---

### Post by samuelporcellis on 2018-12-27
If I try to boot any Windows version from USB, it just gives me a black screen.
[ATTACH=CONFIG]282029[/ATTACH]
I tried formating my SSD partition using NTFS, but it didn't work.

---

### Post by yancek on 2018-12-27
What software did you use to create the bootable windows installer?
What software did you use to format the partition(s) on the drive(s)?
Since you are posting on an Ubuntu forum, are we save in believing you have some unknown version (??) of Ubuntu installed?
Is it using the entire drive?  
Are you able to boot Ubuntu?

---

### Post by samuelporcellis on 2018-12-27
I tried using Etcher, Rufus, UNetbootin, Boot Camp, but it didn't seem to make any difference.
I used GParted to format the partition on the drive.
Yes, I am currently using Ubuntu Budgie 18.04.1 since I couldn't install Windows.
Yes, any Linux distro seems to boot normally.

Edit:
I did successfully format the drive, it's just that it still didn't boot Windows from USB.

---

### Post by Topsiho on 2018-12-28
I have this hunch: You write you successfully formatted your drive. Did you format the entire drive? Then your Windows is gone :( . If you formatted the entire drive and then installed Ubuntu, you can boot into Ubuntu but not in Windows, as Windows is no more. You'll have to reinstall Windows.
As far as I know (I know nothing of the modern Windows) you'll have to install Windows first, and then Ubuntu or whatever, this time taking care not to erase your Windows partitions.

Success,

Topsiho

---

### Post by samuelporcellis on 2018-12-28
I can't install Windows because the install USB doesn't boot, it just gives me this black screen. I tried many versions of Windows, none of their installers boot, but Linux works fine.

---

### Post by yancek on 2018-12-28
I'm not familiar with Boot Camp but Unetbootin will definitely not create a bootable windows usb.  That is stated on their home page, it is only used to create a Linux bootable usb.  Thee Rufus download page only has an .exe file so that means it has to be installed and used on a windows system.  Do you have another computer with windows to which you are downloading it and trying to create the bootable usb?

Etcher has a Linux version on the page at the link below, scroll down and select to download the Linux version.  When you run it, I would suggest you make notes of progress/warnings/ or error messages you get and post here whatever problems you have.

[https://www.balena.io/etcher/](https://www.balena.io/etcher/)

---

### Post by samuelporcellis on 2018-12-28
I do have a MacBook and an Windows laptop which I can use for making the bootable USB.
I used Etcher on Mac, had no problems. But when I try to boot the USB, it still gives me this black screen.

---

### Post by howefield on 2018-12-28
Thread moved to the "*Windows*" forum.

---

### Post by yancek on 2018-12-28
You're using your Mac to try to create a bootable usb of  a windows installer?  Not sure why you would be posting on this forum.  Have you tried a windows forum or the microsoft site?
If you have Ubuntu installed with Grub, you should be able to follow the steps at the link below to put the windows files on a usb and boot from the the currently installed Grub.  You can skip the steps in the linked page about installing Grub on the usb.

[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

---

