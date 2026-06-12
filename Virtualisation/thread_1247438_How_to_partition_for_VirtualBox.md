---
title: "How to partition for VirtualBox"
date: 2009-08-22
forum: Virtualisation
---

### Post by Stevo0687 on 2009-08-22
Hey all!

I've been running various forms of dual- and triple- boot setups on my Inspiron 1405 for the past year or two.  I would set up VirtualBox quickly in Xubuntu and really liked how it worked.  My problem was that when I tried to do it another time, it said that I didn't have enough disk space.  So my question is how to partition my hard drive for my setup.  

What I would like is to have Xubuntu as my "main/host" OS.  I would like to be able to run Windows XP and Windows 7 via VirtualBox.  I also want a a separate partition (FAT 32) that I can keep all of my files on.  I'm just not a huge fan of how the file systems work in Linux and the trouble I've had trying to access Linux files from Windows, so that is my reasoning for my separate partition for that.  So...

My question is, do I assign a particular amount of space for Xubuntu (say 10 GB), and allocate the rest to my "shared files partition".  Or do I allocate say 40 GB to Xubuntu because it will be running the virtual OSs and the rest to shared partition.  OR do I give Xubuntu about 10 GB, my shared partition a particular amount, and then leave a certain amount unallocated for VirtualBox to use?

I guess what I need to know is what hard drive space, if any, VirtualBox uses to run the OSs.  I'm not sure why I got the error about not having enough space.  I want to back up all my files this week and install Xubuntu and then be able to install VirtualBox for Windows, but I just need to know the correct way to partition. 

Any help is greatly appreciated.  Thanks in advance!

---

### Post by bodhi.zazen on 2009-08-23
Get a larger hard drive =)

In terms of your partitioning, 10 Gb is my "default" or "standard" size I use for linux root partitions.

For Virtualization I make a separate partition to store all the virtual hard drives. For a virtual machine I use 4 Gb hard drivers + anticipated data.

---

### Post by jocampo on 2009-08-23
Like Bodhi said, a bigger drive will allow you more flexibility when creating and playing with your VMs. But, as an alternative, you can also get an external Hard Drive, with 7200rpms, and put your vdi files there. I tried that months ago with my Dell Inspiron and worked ok. You can get external USB drives of 200GB, 500GB...really big, and they are in FAT32 so you can unplug and run that from Windows if you want.

Regarding Xubuntu or any other Ubuntu flavor, 10gb should be more than enough (just for Linux or / partition) You can mount /home in the remaining space and your VMs will be there also; a good way to keep your data away from Os also.

---

### Post by Stevo0687 on 2009-08-23
Thank you for your replies.  I am not worried about enough hard drive space.  I have a 120 GB hard drive in my laptop which has been enough for me to run Linux, XP, and Vista with a triple-boot at one time.  I do have an external hard drive, but I use that for files that I don't access as much.  I want to be able to use any of my OSs without an external drive.

My question is just a matter of whether VirtualBox uses the hard drive space allocated to the host OS, or if it uses unallocated hard drive space, or if the virtual OSs need a formated partition.  

I hope that makes my question clearer.  I'm sorry if I'm not understanding things correctly.  I just need to know how to set up my partitions. Thanks again.

---

### Post by bodhi.zazen on 2009-08-23
You can run Virtualbox in more then one way.

The standard way is to use a file as a virtual hard drive. This file will be 10 Gb, or howerver large you make th evirtual hard drive, and will be stored on a formatted partition somewhere, either / or /home or a data partition. The virtual hard drive is a large file. I suggest you go this route.

You can boot a physical partition in which case the VM will format the partition. Note this is in Beta at best and you will loose the ability to manage your partitions with gparted as the VM partition is not recognized by gparted (or parted).

No OS can use unpartitioned free space, there must be a file system or formatting.

---

### Post by Stevo0687 on 2009-08-23
b.z., 
Thanks so much for your help.  So...if the virtual OS needs file space in the host OS, I should make make my Linux partition a reasonable size and use that space.  

Currently, I'm using 30 GB for XP, 60 GB for shared data, and 30 GB for Xubuntu.  So, if I want to run Xubuntu only and use XP and 7 via VB, I should just make Xubuntu bigger.  Or I guess I could use space on my shared data partition.  Either way, I've got a much better idea of how it works.  I want to do a complete re-install of Xubuntu and then give Windows 7 a whirl.  This should be fun!

---

### Post by bodhi.zazen on 2009-08-23
Personally I would install Xubuntu into a 10 GB partition and save the virtual disks on the (large) data partition. This way you can access them from Windows if you wish and re-install xubuntu without having to back up or move 5-10 Gb hard drive images.

---

### Post by Stevo0687 on 2009-08-23
Alright, thanks.  I'll certainly look into that way.  I'm just excited to get it all set up.  I was really enjoying Xubuntu and want to give Win7 a try.  I'm in XP now and am ready for a change.  Xubuntu developed a few glitches, but I didn't want to make any major changes or spend too much time on anything when I plan on reinstalling it.

---

### Post by SolarOnline on 2009-08-24
Yep i agree with a few suggestions here.

I would install ubuntu into a separate partition and save the virtual disks on an additional partition which is large enough for your needs.

this may help also: [http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/](http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/)

---

### Post by Stevo0687 on 2009-08-24
Sounds good.  Should I do 2 partitions, 1 for Xubuntu, 1 for my data and the virtual disks OR should I do 3 partitions, 1 for Xubuntu, 1 for my virtual disks, and 1 for my shared data?  If I go the 2nd route, should my parition be formated in Fat32 (as my shared data partition will be) or NTFS, since it will be for Windows?

---

### Post by bodhi.zazen on 2009-08-24
Any way you wish , partitioning is more an art then a science and either choice should work well for you.

IMO the most important principle here: Keep the data separate from the OS.

---

### Post by Stevo0687 on 2009-08-27
Ok, things are going fairly well.  I've got one more question, I hope.  I've set up an NTFS partition that is 54 GB for my virtual operating systems.  My question is, when I set up my virtual hard disk and save it to that partition...do I need to create a seperate hard disk saved on that partition for XP and for Windows 7  or will one hard disk work.  I didn't know how that works since I can't really partition that partition in VirtualBox.  Any help would be great.  A quick reply would be even better so that I can get this done.  THANKS!

---

### Post by bodhi.zazen on 2009-08-27
One disk should work just fine, should be able to add it to your virtual machines in every os (you will have to manually create a new VM and add the HD).

---

### Post by Stevo0687 on 2009-08-27
So in the Virtual Machine Manager, can I create just one file "hard drive" for XP and Win 7?  I don't need to create two "files", one for each?

---

### Post by bodhi.zazen on 2009-08-27
I am not sure what you are asking. You will need to create a virtual machine on each OS.

When you make a VM you can share a single virtual hard drive across OS, just do not do anything fancy, such as snapshots.

---

### Post by jocampo on 2009-08-27
Let me illustrate you with my own experience and Dell Inspiron Laptop ;-)

Partitions (3)

-One for Windows XP (used like 1% of the time) -  20gb-NTFS
-One for my beloved Ubuntu - 10gb-ext4
-One for data (shared between partitions) - 20gb-fat32

I used create VMs via Ubuntu with VirtualBox and save the vdi file on the Data partition (really small files, btw, now I have an Ubuntu Server for play with that). You can boot into Windows and use it too if you want but the point is, fat32 will let you use and see the data there between Os.

If your Data partition is big enough, you can create several VMs (vdi files) and boot those via VirtualBox/Ubuntu and play with them. You will need one vdi file per VM. So...if you create Xubuntu, Vista, Ubuntu server, via VirtualBox, you will have three vdi files inside Data partition: one for Xubuntu, one for Vista and one for Ubuntu Server.

---

### Post by theZoid on 2009-09-06
> **jocampo said:**
> Let me illustrate you with my own experience and Dell Inspiron Laptop ;-)

Partitions (3)

-One for Windows XP (used like 1% of the time) -  20gb-NTFS
-One for my beloved Ubuntu - 10gb-ext4
-One for data (shared between partitions) - 20gb-fat32

I used create VMs via Ubuntu with VirtualBox and save the vdi file on the Data partition (really small files, btw, now I have an Ubuntu Server for play with that). You can boot into Windows and use it too if you want but the point is, fat32 will let you use and see the data there between Os.

If your Data partition is big enough, you can create several VMs (vdi files) and boot those via VirtualBox/Ubuntu and play with them. You will need one vdi file per VM. So...if you create Xubuntu, Vista, Ubuntu server, via VirtualBox, you will have three vdi files inside Data partition: one for Xubuntu, one for Vista and one for Ubuntu Server.

Jo...that FAT32 partition of yours can be NTFS...there's no need to use FAT32 these days as Linux reads and writes to NTFS.  That's the way it was done a few years ago, just saying as I'm not much of a fan of FAT32.

---

### Post by jocampo on 2009-09-06
> **theZoid said:**
> Jo...that FAT32 partition of yours can be NTFS...there's no need to use FAT32 these days as Linux reads and writes to NTFS.  That's the way it was done a few years ago, just saying as I'm not much of a fan of FAT32.

You're right on that... but unfortunately (or lucky me) hard drive died couple of days ago; in fact, is agonizing, some times works some times does not  ... so I got a new laptop. New one has no dual boot but I'll install XP as virtualbox. And immediately got rid of that ugly Win Vista, lol ... got rid of that and put Jaunty. Nvidia drivers were tricky, had to tweak that a bit, but working as a charm now.

---

