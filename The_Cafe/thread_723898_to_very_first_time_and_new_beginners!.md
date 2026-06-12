---
title: "to very first time and new beginners!"
date: 2008-03-14
forum: The Cafe
---

### Post by savagenator on 2008-03-14
To all beginners new to linux (specifically ubuntu) and have NEVER used it before, or do not understand how to use it! 

I recently have thought out and realized that if you point to linux and say "go!", people will try it. Yes, and then go right back to windows. Here are some tips to the new users in Ubuntu specifically!

**1.** You do not need to go program hunting! To get everything you need program wise, find "Synaptic Package Manager" Look through the menus so you know what is there (there are only three). The names of programs may strange, but read the description so you know what to download and install. 
[COLOR="Red"]NOTE: Programs are not the same in Linux as in Windows! They will look and feel different, but also do the same jobs as those programs which you paid for in Windows![/COLOR]
[B]
2.[/B] Codecs, Web Browser video players, and extra fonts are not installed by default! You need to find them in the Synaptic Package Manager. The package "Ubuntu-restricted-extras" holds some of these, and "mozilla-mplayer" has the video player! This can also be found in "add-remove programs" under the applications menu, but it is good practice to use the Synaptic manager.

**3.** Don't be scared of the Terminal. If you want help, search these forums, it is not that hard. It is almost guaranteed someone had asked that same question. 

**4.** Drives and Partitions are not hard to set up. If you are reading this, you probably already set up a ubuntu setup, but generally it is good to know what you did and what you need to do with partitions. Partitions are peices of the Hard Drive that you store files on, but Hard Drives do not always need partitions. Windows Does not use partitions at all, but Ubuntu can be set up with multiple Partitions. As the default setup, Ubuntu makes 2 partitions, one for the main system, and one for Swap, which is meant to be used if you run out of RAM, very necessary. It calls the first partition /dev/sda1 and /dev/sda2 or anything else depending on the drive (like /dev/sdb1) You can make a third partition when you are setting up ubuntu. This is usually setup as ext3 format, which is like NTFS for those with Windows Backrounds. It is what runs your files.

For Example: When going to manual partition setup, you can do whatever you want with your setup. Lets say you give /dev/sda1 10gb, and make a new /dev/sda2 with 29gb, and a /dev/sda3 with 1gb. The first one will be for the system files with mount point of /. The second one will be for you home files with a mount point of /home. And the third one will be for swap, formatted in the swap format instead of ext3. This will enable you to reinstall a Linux operating system without erasing your personal files, or it might save you drive if your main partition gets corrupted. **The "root" is the top, or highest level of the hard drive, much like C:\ in windows.**

**[SIZE="4"]Advanced Information:[/SIZE]**

PARTITIONS: 
Partitions are mounted in a file: /etc/fstab. This file may look like this: 
```
# 
# /etc/fstab: static file system information
#
# <file system>        <dir>         <type>    <options>          <dump> <pass>
none                   /dev/pts      devpts    defaults            0      0
none                   /dev/shm      tmpfs     defaults            0      0


#/dev/cdrom /mnt/cdrom   iso9660   ro,user,noauto,unhide   0      0
#/dev/dvd /mnt/dvd   udf   ro,user,noauto,unhide   0      0
/dev/fd0 /mnt/fd0   vfat   user,noauto   0      0
/dev/sda1 /boot ext2 defaults 0 1
/dev/sda3 / ext3 defaults 0 1
/dev/sda2 /home ext3 defaults 0 1
```

This example is from another distribution (flavor, or different version of linux, call it whatever you like). The reason I posted this instead of the ubuntu default fstab is because they have the same format and use. At the bottom you see there is partitions. I have no swap, but I have a boot, root, and home partition. These are all placed in a friendly manner:
<partition> <mountpoint> <file system type> <extra flags (usually default)> 0 1
The partition could also be hardware, such as a cdrom and floppy drive.



I wrote this guide as an aftermath of my frustration after the first ever install of Linux! I didn't understand these simple tips, and now I do. Also, I understand that this title will not be noticed by many users searching for help, so therefore they might not find it. As frustrating as that realization is (it may not be true, but most users searching for problems do not search for "beginners!") I wroter this anyway in hopes of clearing things up. 

I apologize if a similar article was written. I wrote this in my own belief that people would benefit just by reading these 3 tips.

---

### Post by Talahan on 2008-03-14
Thanks! That was actually pretty helpful. I had no idea about the codecs thing. The rest I can't do cause the machine Linux is on doesn't have an internet connect, but thanks anyhow ;)

---

### Post by 3rdalbum on 2008-03-14
This, and other information, should be collated into a post and stickied.

---

### Post by savagenator on 2008-03-15
Please comment and tell me what I can do to make this better, to add or to edit the text.

---

### Post by handy on 2008-03-15
> **savagenator said:**
> Please comment and tell me what I can do to make this better, to add or to edit the text.

I think at least a link to info' on the fstab file would be very useful in a beginner look here first file, many new users have problems tying to get set up another drive/partition.  Even if it points the user to their own installed online help.  They often have no idea that the ***/etc/fstab*** file even exists.  

Following is a link with good information on the subject, though it is not Ubuntu specific, someone may know a better one? :

***_[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html) _***

---

### Post by corney91 on 2008-03-15
You could mention to look in System>Administration>Restricted Manager if something like screen resolution/internet connection doesn't work well.

---

### Post by savagenator on 2008-03-15
Thank you. So far I updated with Partitions and Hard Drives. I do not think I sbould mention /etc/fstab at all, since It is complicated and messing with it can really mess up your partitions.

I prefer that new users explore the Operating system first, and not be told where to go constantly. Tell them to be like Lewis and Clark.

---

### Post by handy on 2008-03-15
> **savagenator said:**
> Thank you. So far I updated with Partitions and Hard Drives. I do not think I sbould mention /etc/fstab at all, since It is complicated and messing with it can really mess up your partitions.

I prefer that new users explore the Operating system first, and not be told where to go constantly. Tell them to be like Lewis and Clark.

I think you should at least mention that /etc/fstab exists & link to more details, due to the fact that it can stop someone from being able to access a drive/partition.  They won't even know the name of the file, as it is totally different than the Windows system & a new user will easily become frustrated by their ignorance at being lost in the new world of *nix,  to the point of tossing it in & going back to Windows.

---

### Post by savagenator on 2008-03-26
added an advanced section with fstab in it. I wonder if I should just make a bunch of links from the advanced section to other threads with the information (such as fstab) People don't like reading long threads

---

