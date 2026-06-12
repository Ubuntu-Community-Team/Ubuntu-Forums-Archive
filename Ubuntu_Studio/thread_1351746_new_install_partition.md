---
title: "new install partition ?"
date: 2009-12-10
forum: Ubuntu Studio
---

### Post by garyed on 2009-12-10
I'm running the 64 bit version of U-studio 9.10 on ext4 file system.
I'm trying to install the 32 bit version ext3 on a different partition of the same HD. 
I used Gparted to make a 50 gig ext3 partition for the new install then booted the install CD. When I get to the partitioning part I'm lost.
I use the new partition & when it asks for a mount point I use "/".
Then when I ready to write changes it warns me about overwriting different
files /usr /lib or something like that so I abort because I'm not sure where to go. I thought I could just install the new version onto my newly created partition but I don't see that as an option.
What am I missing?

---

### Post by indytim on 2009-12-11
> I used Gparted to make a 50 gig ext3 partition for the new install then booted the install CD. When I get to the partitioning part I'm lost.
I use the new partition & when it asks for a mount point I use "/".
Then when I ready to write changes it warns me about overwriting different
files /usr /lib or something like that so I abort because I'm not sure where to go. I thought I could just install the new version onto my newly created partition but I don't see that as an option.
What am I missing?

Assuming during the install that you have selected the Manual Partition option:
1.  Identify your new "/" partition.  You WILL have to check the "Format" checkbox on this partition to proceed with the installation.  This is the case even if the partition is already formatted.  The installation WILL OVERWRITE ANYTHING THAT IS ALREADY IN THE PARTITION FOR "/".
2. Identify any other partitions that you want mounted at the time of bootup.  For these partitions, you will want to click the "Edit" option.  Identify the mount point etc while editing.  Note, for mount points it is usually "/media/< insert the name of the media folder here>".

Hope this helps,

IndyTim

---

### Post by garyed on 2009-12-11
> **indytim said:**
> Assuming during the install that you have selected the Manual Partition option:
1.  Identify your new "/" partition.  You WILL have to check the "Format" checkbox on this partition to proceed with the installation.  This is the case even if the partition is already formatted.  The installation WILL OVERWRITE ANYTHING THAT IS ALREADY IN THE PARTITION FOR "/".
2. Identify any other partitions that you want mounted at the time of bootup.  For these partitions, you will want to click the "Edit" option.  Identify the mount point etc while editing.  Note, for mount points it is usually "/media/< insert the name of the media folder here>".

Hope this helps,

IndyTim
Thanks for the help,
I thin I should give a little more info:
I have 3 HD's starting out with this setup:
1 - Windows XP - all one partition
2 - Windows fat32 all one partition
3 -Ubuntu Studio Gusty partition ext3 all one partition
    
I don't want to touch the first two HD's with Windows on them so 
I installed Ubuntu Studio 64 bit on HD 3 in a 100 gig ext4 partition
leaving Gusty on about 50 gig partition. I was having better sound performance out of Gusty than Karmic so i decided to try the Standard version of Karmic on ext3 so I used Gparted to split the 100 gig partition in half & make a new 50 gig partition to install the standard version of Karmic U-studio.
So on HD 3 I want:
U-Studio Gusty ext3
U-Studio Karmic 64 ext4
U-Studio Karmic 386 ext3 
  
Now back to the installation:
I did choose the manual partition & selected the ext3 partition that I made with Gparted & when it asked for a mount point I used "/" .
When it asked me to write the changes to partition thats when I got all the warnings about those different files like /usr.. & a few other folders being overwritten. Since I didn't have anything like that on the first installation of Karmic 64 I figured I'd better abort & not try another installation until I know what I'm doing. That's where I'm at now.

---

