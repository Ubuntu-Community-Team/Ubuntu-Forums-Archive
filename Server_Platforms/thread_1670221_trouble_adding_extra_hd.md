---
title: "trouble adding extra hd"
date: 2011-01-18
forum: Server Platforms
---

### Post by faridym on 2011-01-18
Hi guys,

I've build a NAS to share it on my network with windows computers and want to use Ubuntu Server as my platform. The install and everything went fine.
I added 2 extra disks (each 2TB) and made sure I can see it in the bios. To start I wanted first just 1disc to be mounded to make sure if I do everything correct and followed this guide:

[http://www.mikestechblog.com/joomla/operating-systems-section/operating-systems-ubuntu/53-add-a-second-hard-drive-in-ubuntu.html](http://www.mikestechblog.com/joomla/operating-systems-section/operating-systems-ubuntu/53-add-a-second-hard-drive-in-ubuntu.html)

for the filesystem, instead of ext3 I used ext 4 and instead of /mnt/sdb1 I renamed it to mnt/NAS. After configuring it to be auto mounted, I went to bed. Today there was a powerfailure in the house and my NAS turned off. 
When it was turned on again, I wanted to connect like always via putty to my nas and noticed I couldnt get a connection.
When i wanted to logon locally I saw it didn't boot anymore. 
So what I've done now is installed ubuntu server again (since I didnt have any data yet written to my drives,coz im new to linux and still learn a lot) 

But how can I prevent this from happening again?
Did I do something wrong when I tried to configure the 2nd disk?

---

### Post by Kakers on 2011-01-18
Thats really strange, if you've followed those instructions (obviously changing ext3 to ext4 like you've said) it should work fine...

You should be able to have both off, turn on your NAS, then turn on your Ubuntu system and it should automatically mount as you've added it into the fstab.

Are you still able to see the drive in 'sudo fdisk -l' ? If not, it could be a problem with your NAS unit. Sometimes happens during the powercut if there was a serge before the power went out...

---

