---
title: "Ubuntu Server 16.04 on HP Server with multiple Operating systems"
date: 2016-07-26
forum: Server Platforms
---

### Post by ubu-tt on 2016-07-26
I have slowly been moving my home system to use Ubuntu but have to maintain Windows for a while still. I have created some tools to help me (a Ubuntu install usb with persistence and a Kali Linux usb with persistence) but have hit a problem.

I have a lap-top with Win10 and Ubuntu 16.04 (on one drive) - that works fine and I get the Ubuntu grub menu on boot.

1. I also have a HP Server. The HP server was setup with WHS2011 (Win 2008 r2 engine). It had 3 drives in originally (2 ntfs data drives). I had to mirror the 2008 r2 OS to a new drive (to expand OS space) and in doing so had to change the OS drive to a Dynamic drive.

2. The BIOS on the HP server is a very basic one.

3. I then added a new drive to install Win10 and Ubuntu side by side - to also live with 2008 r2. Win10 and 2008 r2 live fine and I get the win bootloader options to access either. 

4. The system now has 4 drives (2008 r2 environment on Disk0, Win10 and Ubuntu Server on Disk1 and 2 x data drives on Disk2 and Disk3). Disk1 is a Basic drive and Disk0 is a dynamic drive.

5. After installing Ubuntu Server 16.04 on Disk1 (alongside Win 10 on Disk1) I am unable to get the Ubuntu Server to show up on the boot menu - which is still a Win bootloader. The Ubuntu Server installation went fine.

6. The Ubuntu Server 16.04 installation is on an extended partition on Disk1 and contains the following partitions in this order <\boot, \, \home and linux-swap>.

7. Using <bcdedit> when booted from either of the Win OS there are only 2 entries - Win Boot Manager and Win Boot Loader. The Win Boot Loader is pointing to the Win10 boot path. The Win Boot Manager is pointing to <partition=\Device\HarddiskVolume14>. I cannot determine which disk or partition this #14 is referring to. If I use <diskpart> on Windows I only get 10 Volumes. If I use Gparted (Ubuntu usb) I can see about  17 partitions across the server estate as follows;
>sda -win 2008 only, r2 has 4 of which: sda1(1MB) is windows partition, sda2(100MB) is flagged as a boot partition,  sda3(265GB) is the r2008 r2 OS, sda4(200GB) contains support applications for 2008 r2.
>sdb -ntfs data drive has 2
>sdc -ntfs data drive has 3 partitions
>sdd -Win 10 and Ubuntu have 8 partitions collectively of which: sdd1(340GB) is Win10 OS, sdd2(450MB) is a Win10 reserved area flagged as -diag, sdd3 is simply a shared space to be used later, sdd4 is an extended partition with Ubuntu environment with the following: sdd5(1GB) =/boot, sdd6(35GB) = ubuntu root "/", sdd7(214GB) = /home and sdd8(8GB) = linux-swap. 
 
I have tried to use <boot-repair> from the Ubuntu usb with persistence - but am being faced with a menu of "paths" that I am not sure how to complete/configure relative to my environment setup above.

I have tried to use <grub-customizer> but as I am new to that I am struggling a bit.

A long story to say I can't get the Ubuntu grub menu to show (or add to the Win bootloader settings) and therefore have no boot access to the Ubuntu Server 16.04 OS.

If you can help I would be most thankful (and will carry on trying in the meanwhile).

---

### Post by yancek on 2016-07-26
If you ran boot repair, you should post the output which you can get by selecting the option to Create BootInfo Summmaary.

The dynamic disk thing is a problem.  Some info at the link below.

[http://askubuntu.com/questions/90643/windows-dynamic-disk-not-reading-in-ubuntu](http://askubuntu.com/questions/90643/windows-dynamic-disk-not-reading-in-ubuntu)

You do not indicate whether you are using the default UEFI install with windows 10?

I'm not aware of any windows bootloader that will detect a Linux install.  What steps have you taken to manually add the Ubuntu entry with bcdedit?
The link below explains adding a Linux entry using bcdedit.  It's specific to Slackware Linux but it works with any Linux and I've used it with Ubuntu.


[http://alien.slackbook.org/blog/adding-linux-to-the-windows7-boot-menu/](http://alien.slackbook.org/blog/adding-linux-to-the-windows7-boot-menu/)

---

### Post by howefield on 2016-07-27
Thread moved to the "*Server Platforms*" forum.

---

### Post by darkod on 2016-07-27
It might be simply a case of not booting from the correct disk. I'm not sure if the ubuntu installer selects the disk where the install is by default. If it does, it might have installed grub on disk1 while you seem to be booting from disk0.

Did you look into the bios if there is option to specify which hdd you boot from? Not just hdd as device, but which one. Sometimes it is like a submenu.

Also, if the board has like quick boot menu and if you can select a specific disk in there, try booting from disk1 to see what will happen.

You always have the option to add grub to disk0 if you want to, or to all disks that you have. That way it doesn't matter from which one the system boots. :)

But that would delete the windows bootloader on disk0 and you better keep that if possible until you are sure everything works as expected.

---

### Post by ubu-tt on 2016-07-28
OK - I have fixed the system.

First - I took 2 days of my personal time to get around Grub. I took the server (2008 r2) drives out so that I could just work on the Win 10 and Ubuntu environment Tried just about everything! No luck. I had 6 menu options using all sorts of configurations in grub.d/40_custom (and updated grub after each change).

Got frustrated as I thought it was something simple and didn't have the time for debugging.

Solution:
I put the entire disk environment back and booted off Win 2008 r2. I then downloaded  'Easy BCD" after looking around (and I really hate adding apps as I have enough to deal with in real life), installed and had about a 10 minute look around.
Within 15 minutes I added the Ubuntu (Linux) option to the boot menu and can now boot to <Win 2008, Win 10 or Ubuntu). That is special. Yay to "Easy BCD".

Note: I am 58 years old - a former programmer and now a professional in many IT domains. I do this for fun and to keep up with what youngsters are championing. This is my hobby and has been for some 35 years. I love it - but at my age I need easy solutions not convoluted posts that generally "compete" or "contradict" people's needs.

Thanks yancek, howefield and darkod for your respective responses.

Thank you Ubuntu!

---

