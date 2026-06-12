---
title: "I am a new Newbie..."
date: 2015-08-23
forum: Ubuntu, Linux and OS Chat
---

### Post by dustin22 on 2015-08-23
Hello there everyone. As you may have guessed, this is all brand new to  me. So first of all, let me start from the beginning. When I was  approximately ten years old... (kidding). The laptop that I am currently  using has no hard drive. It is a Compaq CQ57. I also have a brand new  Acer laptop running Windows 10. My wife brought me the Compaq the other  night and told me to do something with it or toss it out. With a few  Google searches later, here I am. I found that I could make a boot-able  usb. I do realize that without a hard drive I cannot install the  software. My question is, will I be able to learn all that I could from using the trial Ubuntu? I've read a little about some people doing a dual-boot, and changing partitions. I am way to new to even know how to think about all that. Any help would be greatly appreciated. 

Thanks, Dustin

---

### Post by coldraven on 2015-08-23
Hello and welcome to the forum. If your Compaq works OK when booting from a USB stick then why not buy a drive for it? If you want to go hi-tech you could buy a SSD. I recently replaced my neighbours failing hard drive with a SSD which cost about $90. Its a five year old dual-core laptop, a bit faster than your Compaq. Running Ubuntu 14.04 it now boots from cold in 11 seconds!  A regular HDD is cheaper, you could pick one up for $30 to $40.

---

### Post by grahammechanical on 2015-08-23
With a new hard drive, whether SSD or SATA or even IDE (I have no idea how old that CQ57 is) you will not need to know anything about Linux partitioning. You simply choose the option to Eraze disk and install Ubuntu. When I first installed Ubuntu 8 years ago it was on a self-built machine with a new hard drive. I used the Eraze disk and install Ubuntu option and every thing was done for me.

You can indeed use that machine for experimentation. After installing. Do it again and this time use the Something Else option and put /home (folder) on a partiition that you create for it. You do not have to worry if you mess up because a new install will correct everything. This will show ypou what to expect during the installation process

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

This will help with partitoning

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

This one is from a guide to installing one of the Ubuntu flavours called Lubuntu. The install process is the same as with Ubuntu be this guide shows what to do with the Something Else option. Go down the page until the heading Advanced partitioning.

[https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu](https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu)

By the way, the advantage of having /home on its own partition is that we can reinstall Ubuntu using the Something Else option without losing our data in the /home folder.

Regards and have fun.

---

### Post by Petro Dawg on 2015-08-23
I have used bootable USB installs in the past, both full and persistent.  I doubt your PC has USB3.0 so a full USB install (where the USB is basically a hard-drive) would be rather slow, and a persistent boot session is limited to just a few Gigs of changes before you run out of space in the Casper-rw file.  So you are really limited in what you can do with a USB.  

I would go with coldraven's suggestion and just get a HD to fit it and make it a fully functional PC again.  I found some that will work for you with plenty of room and good enough speed for an Ubuntu (or any Linux) install for under $25.  [Generic 2.5 SATA Internal Hard Drive (120 GB)]("http://www.amazon.com/Generic-SATA-Internal-Hard-Drive/dp/B00AAKF8N4/ref=sr_1_1?s=pc&ie=UTF8&qid=1440384016&sr=1-1&keywords=Hard+Drive+160gb+SATA+2.5%22&refinements=p_n_feature_keywords_six_browse-bin%3A6158681011")  Any 2.5" SATA internal drive will work for you, and you probably really don't need much more than 100 Gig if this is going to be a 100% Linux "practice" system.

---

### Post by sol8712 on 2015-08-23
Yes you can learn a lot from just booting from USB, don't get too invested with installing packages though, be sure to have Dropbox or Google Drive available to save files on when you do get a hard drive to install on. Start here for the easiest way to start booting from USB. 
[http://www.pendrivelinux.com/put-lubuntu-on-a-flash-drive-using-windows/](http://www.pendrivelinux.com/put-lubuntu-on-a-flash-drive-using-windows/)

---

### Post by dustin22 on 2015-08-24
Cool. All of that is very helpful. I don't think I am quite ready to dual boot just yet tho. My long time goal with all of this is to learn Linux inside and out. I've even thought about taking some computer classes to learn more about op systems in general. Maybe, Microcomputer Support Specialist, or something similar. I would eventually like to build my own distro. I do realize that I have an extremely long way to go, but I believe I have what it takes. Any suggestions on where a newbie like I should start their education on Ubuntu? What are the basics anyone should learn?

---

