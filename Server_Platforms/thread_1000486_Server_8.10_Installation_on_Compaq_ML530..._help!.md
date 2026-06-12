---
title: "Server 8.10 Installation on Compaq ML530... help!"
date: 2008-12-02
forum: Server Platforms
---

### Post by ryanender on 2008-12-02
I'm new to Ubuntu Server, but not new to Ubuntu.  That being said, here's my problem:

1.  I obtained a Compaq Proliant (not HP) ML530 with a Smart Array 3200 Controller.

2.  I used the SmartStart disk to configure the RAID successfully.

3.  I installed Ubuntu Server 8.10 successfully (note: when asked to enable the Array, I selected yes, and continued installation).  Also, I saw Grub installed, but it doesn't show up after reboot.

4.  I rebooted, but the OS isn't found.

I've searched the forums, and there are references to using a custom .iso to support Smart Arrays.  Tried it, no luck.

I've also found posts stating I should blacklist 85c3xxx.  No luck

Finally, I've found references to the "cpqarray", but I've tried to /mount /dev/ida/c0d0p1 in the command line using the disk.  FAIL.

Is there anybody in the community that can help me with this.  I'm about to give up, and I really don't want to.  Here's (hopefully) what I'm trying to find out:

1.  Is there a simple workaround to get to the user login?

2.  Is there a piece of software, like Ultimate Bood CD, that I can use to boot the extfs partition?  By the way, SuperGRUB says it isn't a supported filesystem when I try to use it.

3.  Is there a way to mark the extfs partition for boot within the BIOS or SmartStart?

I'm not sure I'm getting everything down.  I just know Ubuntu installed, but it won't boot.  Please, anybody that has any ideas, I'd really apprecaite any help.

Cheers,
Ryan

Bump

---

### Post by ryanender on 2008-12-03
Bump.

---

### Post by thomsonm on 2009-03-04
I'm having the same issue with my DL380. I've got a 3 disk raid 5 (with a raid controller) and Ubuntu Server 8.10 installed. Everything appears fine but upon booting it sits at ...booting from harddisk. Apparently 8.10 doesn't like my raid controller and the only quick fix I've come upon is to try Ubuntu Server 8.04LTS. I'll update as soon as I've tested this out.

---

### Post by matey3 on 2009-03-04
I had the same problem and so after a week of installing and reinstalling I took 2 of the damn disks out and then installed and it worked.
I dont know how many disks you have but I had 4 , the raid BIOS showed 2 but the Linux saw 3 of them!?
Dont ask me I inherited this...
any way when I took the 2 disks on the second set out, the fdisk stuck and I was able to boot, put the 2 disks back in and it still worked.

---

### Post by thomsonm on 2009-03-10
Installed Ubuntu Server 8.04 LTS and have not experienced any problems while booting up.

---

### Post by MountainX on 2009-03-10
I might be able to help. I am in a similar position. I installed Ubuntu several times on desktop computers without any unusual problems. Then I took the next challenge and installed Ubuntu on a server with 10 hard disks (and 2 raid controllers). I worked on that from last August until last week -- that's how long it took me to learn enough to understand what the problems were.

I finally understand the issues I was having and I have everything resolved now. Maybe I can help here.

It sounds like your raid controller is true hardware raid (not fakeRaid and not software raid). If so, you should not have "selected yes, and continued installation". 

When using a hardware raid controller that has driver support in Ubuntu (I use an Areca 1220 and an LSI MegaRAID 320-2E), the Ubuntu installer will not even deal with the actual raid array -- it simply sees the volumes that the raid controller presents. You do not need to enable any raid functionality in the Ubuntu installation.

The other thing you need to know that is different when installing on a server is that device identifiers (sda, sdb, etc.) will often change. Here's my thread on this issue:
[http://ubuntuforums.org/showthread.php?t=1080832](http://ubuntuforums.org/showthread.php?t=1080832)

---

### Post by rblairo3 on 2009-03-19
Sorry, I have no help for you.  Same thing is happening to me on a Dell 2550 and no one has responded.  Black screen and blinking cursor.  Ubuntu 6 (some version) has worked on this server before but I wiped that installation and RAID 5 drive and tried to install 8.1.  Will watch your tread to see if you get better results than my attempt at help.

---

### Post by MountainX on 2009-03-19
> **rblairo3 said:**
> Sorry, I have no help for you.  Same thing is happening to me on a Dell 2550 and no one has responded.  Black screen and blinking cursor.  Ubuntu 6 (some version) has worked on this server before but I wiped that installation and RAID 5 drive and tried to install 8.1.  Will watch your tread to see if you get better results than my attempt at help.

Did you see the [link]("http://ubuntuforums.org/showthread.php?t=1080832") I posted above? It contains a solution for "Black screen and blinking cursor" when the computer has more than one hard disk (or RAID, etc.).

---

### Post by rblairo3 on 2009-03-19
Hi MountainX, There were not posts to this thread when I started my post so I didn't see your reply.  When the Dell 2550 is correctly configured for raid 5 Ubuntu 8.1 sees the drive as a single logical volume of the correct size and not 3 independent disks.  I also did not have to enable raid during the Ubuntu install.  I attempted to install 8.04 prior to 8.1 but after downloading 3 different ISO images I could only get part way through the install before the server could no longer read the image off the CD.  Ubuntu desktop on my laptop has been so much easier.  The only successful Ubuntu server install on this server has been with 6.x .

---

### Post by MountainX on 2009-03-19
> **rblairo3 said:**
> Hi MountainX, There were not posts to this thread when I started my post so I didn't see your reply.  When the Dell 2550 is correctly configured for raid 5 Ubuntu 8.1 sees the drive as a single logical volume of the correct size and not 3 independent disks.

Yes, that is the way things should work with hardware raid.

> **rblairo3 said:**
> I also did not have to enable raid during the Ubuntu install. 

This is also expected because Ubuntu includes drivers for most popular RAID controllers now. Furthermore, because you have hardware RAID, you do not need to enable software RAID in Ubuntu.

> **rblairo3 said:**
> I attempted to install 8.04 prior to 8.1 but after downloading 3 different ISO images I could only get part way through the install before the server could no longer read the image off the CD.  Ubuntu desktop on my laptop has been so much easier.  The only successful Ubuntu server install on this server has been with 6.x .

I went through a similar experience. I'm sure you can resolve this just as I ultimately resolved my issue with the help of the other thread.

How many disk volumes do you have in the computer? The RAID array is one logical disk. Are there others? And what partitions are you setting up?

Also, check the other thread (at link I provided) for bootinfoscript.

---

### Post by rblairo3 on 2009-04-02
MountainX,

I keep getting distracted from the solution to my problem.  The computer only has one volume.  I used the guided partition setup trying each option at least 2x.  The weird thing I found was that it never created the directory /boot/grub and no menu.lst.  I ran install-grub by booting from the install disk and selecting the fix option allowing me access to the hard drive.  From /usr/bin on the hard drive I ran install-grub which created the /boot/grub and files.  Still not sure how to edit the menu.lst file.  This has been an interesting way to find my way around the file structure and some of the aps.  Should have been documenting this in more detail.  I was able to boot to some basic grub (or something) that gives you a list of things you can do by hitting TAB.  Not sure what to do here.

---

### Post by MountainX on 2009-04-02
rblairo3 can you attach the results of the boot info script?

---

### Post by rblairo3 on 2009-04-03
Too much time spent on 8.1 so I tried 9.04 Beta and the install was faster and flawless.  No problem with the raid issue whatsoever.

---

