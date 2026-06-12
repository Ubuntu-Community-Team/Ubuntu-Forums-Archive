---
title: "My server crashed ... nothing under /boot"
date: 2014-09-11
forum: Server Platforms
---

### Post by cwmoser on 2014-09-11
I have an Ubuntu Server that ... well just runs and needed little attendence.
I note now that it will not boot.
I booted a rescue CD and got a command prompt and noted that all my files
are there excect that everything under /boot is missing -- its empty.
Of course update-grub can't fix it.

So, what is the best course of action that I can do to maintain all my Apache settings
so I won't have to go through that exercise again?

I'm not all that interested in "technical excellence", just get the server back up
hosting my website as before.

Thanks

Carl

---

### Post by oldfred on 2014-09-11
Is that a separate /boot partition or the /boot folder?
And which was your system using? Many servers have the separate /boot partition and then the /boot inside / is not used. 
Your fstab will tell if mounting a separate partition as /boot.

If you are using live installer as rescue disk install Boot-Repair and post link to BootInfo report so we can see details.

 [       ]("https://help.ubuntu.com/community/DiskSpace")
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by cwmoser on 2014-09-11
I got my server up now but I don't understand some things.

I could use a Rescue Disk, drop to command prompt and see my files but not anything under /boot.

mount showed something odd like this:
/dev/mapper/serverm2-root  226G  94G  121G  44%   /

The name of my server is "serverm2"

So, what I did was take out the Hard Drive, stuff it in a USB drive enclosure, and hook it to my 
desktop PC.  There I could only mount the first partition and see some boot files like:

abi-3.2.0-32-server
initrd.img-3.2.0-32-server
System.map-3.2.0-32-server
vmlinuz-3.2.0-32-server

Soooo, I copied these files to a Thumb Drive.
Then remounted the Hard Drive in the Server, connected the Thumb Drive.
Booted the Server using the Rescue Disk and copied the boot files from the 
Thumb Drive to my empty /boot folder.

Rebooted the Server and now it works.

I think I am ignorant about the partitioning going on with my Server.
Its Ubuntu 12.04 command prompt only.

Carl

---

### Post by oldfred on 2014-09-11
It sounds like you have or had a separate /boot in fstab, but that got deleted and then system expected to boot from /boot folder in /?
But with LVM not sure how grub would then work at all unless system was reset and grub reinstalled.

You can document install with Boot-Repair from Live installer.

Or from server with bootinfoscript which is the first part of Boot-Repair's report.
       Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/latest/download](http://sourceforge.net/projects/bootinfoscript/files/latest/download)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by cwmoser on 2014-09-11
Yes, you are right -- I also had the rescue CD to reinstall Grub.

---

### Post by cwmoser on 2014-09-11
I don't uinderstand this when I ran the **mount** command:
/dev/mapper/serverm2-root 226G 94G 121G 44% /

What is this "mapper/serverm2-root" construct?????

---

### Post by sotiris2 on 2014-09-11
It is a [LVM](https://help.ubuntu.com/community/UbuntuDesktopLVM) partition, if you don't know why it's there I think ubuntu needs LVM to encrypt whole system, so you may have chosen that option during install.

---

### Post by oldfred on 2014-09-11
LVM was another way around the 4 primary partition limit. It offers some advantages but is a logical overlay over physical partitions, so is more complicated. You cannot use gparted, but must use LVM tools to modify partitions.

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
2014_02_22_Preparing Logical Volumes For Ubuntu Installations
[http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html](http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html)
Issues on very large 19TB LVM ext4 64 bit partition
[http://ubuntuforums.org/showthread.php?t=2213785](http://ubuntuforums.org/showthread.php?t=2213785)
lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)
sudo apt-get install lvm2
sudo vgchange -ay
LVM gui tool:
[http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/](http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/)
sudo apt-get install system-config-lvm

---

### Post by cwmoser on 2014-09-12
oldfred, sotiris2.  Thanks for the info on LVM.  I never knew I had that setup.
Its 12.04 and no GUI.  

I can't Clone the drive with Clonezilla.  It gets errors on /dev/sda1, and when Clonezilla gets 
to /dev/sda5 its so slow that I just aborted the process.

I have backed up all of /etc and www folders in case I need to rebuild this server.
I did not intentionally select to encrypt when I installed the OS.
When I rebuild it, I'm going to try to get it setup with partitions like on the desktop Ubuntu OS's.

Carl

---

### Post by slickymaster on 2014-09-12
*Moved to the ***Server Platforms*** sub-forum*

---

### Post by cariboo on 2014-09-14
Just out of curiosity, did you run fsck on the partition before making any changes?

---

