---
title: "SAMBA &amp; File Permissions"
date: 2011-03-18
forum: Server Platforms
---

### Post by theprintingplace on 2011-03-18
Hi everyone. I am working on setting up a small office file server and am still new to Ubuntu server. Everything has gone smooth so far but I am having a problem with file permissions. It is likely a stupid mistake but if anyone has some input, please let me know.
Thanks!

I have two hard drives in the system. One is only used for the OS and the other will only be used for the SAMBA shares. It is formatted as FAT32 (VFAT) (RAID is not yet in the budget) I have mounted the second hard disk to /mnt/drive2 and created a folder on it called "shares". (I still have to figure out how to automount it upon boot.) I created two dir's I want to be SAMBA shares in the "shares" folder. We want everyone to access these without permission problems. I tried to change the permissions to rwx for everyone but it will not change, even using "sudo" as root. See below:



nick@server:/mnt/drive2$ mkdir shares
mkdir: cannot create directory `shares': Permission denied
nick@server:/mnt/drive2$ sudo mkdir shares
nick@server:/mnt/drive2$ ls
shares
nick@server:/mnt/drive2$ ls -l
total 16
drwxr-xr-x 2 root root 16384 2011-03-18 09:54 shares

nick@server:/mnt/drive2$ chmod 777 shares
chmod: changing permissions of `shares': Operation not permitted
nick@server:/mnt/drive2$ sudo chmod 777 shares
nick@server:/mnt/drive2$ ls -l
total 16
drwxr-xr-x 2 root root 16384 2011-03-18 09:54 shares

What am I doing wrong? I also tried it without binary shorthand using a+rwx it accepts the command but doesn't change anything. Any ideas would be great. Thanks!

---

### Post by pricetech on 2011-03-18
First of all, why did you format it fat32 ??  A Linux file system would be efficient and Samba will make the filesystem type irrelevant.

It should also make permissions irrelevant.

Install, if you haven't already, system-config-samba which will give you an easy to use Samba configuration tool.  Set up your shares there with whatever permissions you need.

One other thing I've noticed a few times is that before Samba starts working properly I have to go to the command line and add a user there.  Some kind of bug from what I've read.  It just became a habit after the first time.

```
sudo smbpasswd -a username
```

Substituting your username of course.  You'll be prompted for your password by sudo, then again twice by smbpasswd.  Once that's done things should just plain work.  They always have for me.

---

