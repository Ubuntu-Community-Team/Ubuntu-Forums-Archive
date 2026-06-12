---
title: "2 OS in 1 Computer"
date: 2005-07-15
forum: The Cafe
---

### Post by Devon001 on 2005-07-15
Hello, I need some help.. I'm trying to boot Ubuntu from disk but my stupid Windows Xp won't boot it up  from the drive :-x ..  First, of all is it possible to have both Windows and Unbuntu in 1 computer? If so how do I do that? I would like to turn it to Unbuntu but it's a family computer.. Also, is Unbuntu similiar to Fedora Core and Redhat ?Thanks for your help... I'm planning on converting my computer into Unbuntu if it's even possible at the end of July, i'm goning to formatt my computer :).. alot of crap on her and run really dam slow  :???: . Thanks for your help :)

---

### Post by Knome_fan on 2005-07-15
Hi, having both windows and ubuntu on one computer is no problem. If you install Ubuntu on a seperate partition you'll have a login screen that lets you decide if you want to start Ubuntu or Windows on boot.

About Ubuntu and RedHat I don't really understand your question.

Also I don't understand what you mean with WinXP not booting it up from the drive. What exactly are you trying to do?
If you want to boot the Install or the LiveCD, just make sure that the Ubuntu CD is in your CD drive while you start your computer. If that doesn't work you probably need to check in your bios if your CD drive is indeed the first boot device (that is, if on startup your computer first tries to startup from CD and only if that isn't possible starts from your harddrive.)

Hope this helps.  :grin:

---

### Post by aysiu on 2005-07-15
[QUOTE=Devon001]Hello, I need some help.. I'm trying to boot Ubuntu from disk but my stupid Windows Xp won't boot it up  from the drive :-x .. [/quote] You have to change your BIOS so that it looks at the CD-ROM drive for bootable media before trying the hard drive. To get to the BIOS settings, you usually press Delete, Escape, or one of the F-keys (F1, F2, etc.) during bootup. It depends on your computer.

> First, of all is it possible to have both Windows and Unbuntu in 1 computer? If so how do I do that? Yes. Backup everything. Partition your hard drive (Use Partition Magic, DiskDrake, or QTParted). Put Windows on one partition. Put Ubuntu on the other partition. In that order (Windows first).

Of course, you can just resize Windows and create a Linux partition from the free space, but always make sure you back up your Windows installation and data.

> I would like to turn it to Unbuntu but it's a family computer.. During the Ubuntu installation process, you'll be asked if your other OS is Windows. Say, yes. Then, you'll be asked whether you want to install Grub on the MBR. You do. However, once you get everything set up, you'll have to edit the /boot/grub/menu.lst file and change default from 0 to 3 so that Windows is the default boot option (for the convenience of the rest of your family).

> Also, is Unbuntu similiar to Fedora Core and Redhat ? It's similar in some ways. It defaults to a Gnome desktop, for example. But it installs software using dpkg packaging (.deb files instead of .rpm files) and uses apt-get to install (with the Synaptic Package Manager GUI).

> Thanks for your help... I'm planning on converting my computer into Unbuntu if it's even possible at the end of July, i'm goning to formatt my computer :).. alot of crap on her and run really dam slow  :???: . Thanks for your help :) Uh, if you're going to reformat it anyway, reformat, fdisk to partition, install Windows on first partition, install Ubuntu on second partition.

---

### Post by WildTangent on 2005-07-15
assuming you dont want to ruin your current Win XP installation, i highly recommend not running the install CD yet... what you need to get is partition magic for windows. use this to shrink your windows partition, create around 10GB if you just want to experiment, the minimum youll need is 3GB i believe. when you run the install cd (buy putting it in the drive and restarting your computer) itll come to a part where itll ask you if you want to erase your whole hard drive. YOU DONT WANT TO! select install to largest free space or something along those lines. continue on as normal from there. make sure you backup any data you cant stand to lose first (family photos for example). and another little nitpick, this thread belongs in the Installation help forum, not community chat.

-Wild

---

### Post by Wolki on 2005-07-15
I recommend making a second partition for your home directory, it contains your user settings and files. That way, if you want to reinstall ubuntu (or switch to another distro) for whatever reason, it won't delete your files. When you partition the drive, instead of making one large Linux partition, simply make two. How big they have to be depends, Ubuntu needs around 3 gigs for system files, if you like to experiment and add different programs/environments add some gigs. Your home partition can be as small as a few hundered megabytes since the config files usually don't take that much space; you need more if you want to store a lot of data there.

Oh, and Ubuntu can read but not write to NTFS, the default file system of Windows 2000/XP. It can read and write FAT32 however, so a small partition in FAT that you can use to transfer files from Ubuntu to Windows might be a good idea.

---

### Post by WildTangent on 2005-07-15
[QUOTE=Wolki]I recommend making a second partition for your home directory, it contains your user settings and files. That way, if you want to reinstall ubuntu (or switch to another distro) for whatever reason, it won't delete your files. When you partition the drive, instead of making one large Linux partition, simply make two. How big they have to be depends, Ubuntu needs around 3 gigs for system files, if you like to experiment and add different programs/environments add some gigs. Your home partition can be as small as a few hundered megabytes since the config files usually don't take that much space; you need more if you want to store a lot of data there.

Oh, and Ubuntu can read but not write to NTFS, the default file system of Windows 2000/XP. It can read and write FAT32 however, so a small partition in FAT that you can use to transfer files from Ubuntu to Windows might be a good idea.[/QUOTE]
lets not confuse the guy and make him ruin his families computer. hes already said its got win XP on it, and i doubt he has an extra partition already on it, probly using the whole disk for XP, therefore he must resize, and wont be able to create extra partitions for /home or a FAT partition

-Wild

---

