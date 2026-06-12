---
title: "Cannot login as regular user, only as root"
date: 2017-10-27
forum: Server Platforms
---

### Post by qajaq on 2017-10-27
Using Ubuntu Server 16.04.3 - command-line only (no GUI): login screen allows me to enter my regular user-name (***qajaq***) and password, but then merely flashes the usual welcome message for an instant before clearing the screen and showing the following messages:
.   Stopped Getty on tty1
.   Stopped User Manager for UID 1000
.   Removed user User Slice of qajaq
After displaying these messages for several seconds, the screen clears again and displays the login prompt.

I *_am_* able to login as root.

As root, I tried the command: **su qajaq** and got the error message: "Cannot execute /bin/bash: Permission denied"
Then I tried the command: **su - qajaq** and got the error message: "Unable to cd to 'home/qajaq'"
I checked the **/etc/passwd** file and found nothing unusual: the **qajaq** user is listed with **UID 1000**, home directory as **/home/qajaq**, and **/bin/bash** as my login shell. I also checked the **/etc/shadow** file and though I cannot interpret the hashed password for qajaq, the file did not have a recent write-date.

As root, then, I created a new user (**willy**), checked the **/etc/passwd** and **/etc/shadow** files and found them both as expected. But I had the same results when I tried to **su** (with or without the hyphen) to the **willy** account.

As root, I am able to **cd** to both of these users' **/home** directories and list their content. On this machine, **/home** is the mount-point for a separate partition on the first hard drive (**sda**). The partition is 4 GB in size, and the **du** command shows only 100 MB used. I double-checked that with **gParted** on a live-USB and got the same reading, so it doesn't appear that the problem is a fully-filled partition.

I don't know where to go from here, so any ideas will be welcome.

---

### Post by LHammonds on 2017-10-27
Sounds like a permission issue.

What is the results of this command?

```
ls -l / | grep home
```

LHammonds

---

### Post by qajaq on 2017-10-27
That looks like it may be the source of the trouble. The permissions are **rwxr-xr-x** and the owner and group are **root root**. (The individual subdirectories for **qajaq** and **willy** are appropriately owned by those users and groups.)

But if I change the permissions of **/home** to **rwxrwxrwx**, I am still unable to **su** to either of those regular users, and I get the same error messages as before. And when I re-boot, the permissions have reverted to **rwxr-xr-x**.

---

### Post by darkod on 2017-10-27
It is normal /home to be owned by root:root. Only the subfolders that belong to specific users are owned by those users.

On another note, root is disabled by default on ubuntu. If you took some steps to enable it, maybe it affected other users?

---

### Post by qajaq on 2017-10-27
Ownership of **/home** by root is understandable; anything else would limit some users on a multi-user system. What does surprise me is the permissions settings, the fact that even when those are changed, I still cannot change user to a regular user. And I'm also surprised at the way those permissions revert on re-boot.

And yeah, I'm aware of the no-root-login default setting on Ubuntu, so I was a little surprised when I was able to login as root when the other user logins failed. I wouldn't know what steps to take to enable root login, so if I did something to change that, it must have been an unintended consequence of something else.

---

### Post by darkod on 2017-10-27
Is this a hosted VPS or something, or it is a server at your home/work that you installed yourself with the standard ubuntu server ISO?

Hosted VPS can usually have root enabled. But if this is a server you installed, enabling root is not something that just happens accidentaly. And that is my point, if you did some user management that you might not even be aware of (unintended), then the problems you are seeing with other users might easily be a result of that...

Can you please post the output of:
```
df -h
cd /home
ls -l
```

---

### Post by LHammonds on 2017-10-27
This is the default setting and it matches yours so that isn't the issue:
```
drwxr-xr-x   5 root root  1024 Jun 20 09:31 home
```

The permissions of the home folders on my default install are as follows:
```
drwxr-xr-x 3 administrator administrator  1024 May  4 17:53 administrator
drwx------ 2 root          root          12288 Apr 14  2017 lost+found
```

Might be how the /home is mounted.

Take a look at /etc/fstab and make sure nothing looks abnormal.

This is what my entry looks like:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/LVG-home /home           ext4    defaults        0       2

```

EDIT: Also, if you didn't enable the root password, this was not a standard install from the ISO images.  If it wasn't an install from the standard ISO images, the source of the problem might be with how the image was configured before you ever touched it.

---

### Post by qajaq on 2017-10-27
This is a home system. I installed it about a year ago from an ISO image I downloaded from Ubuntu. It was specifically a server version.

**darkod**, **[FONT=Courier New]df -h[/FONT]** returns this:
Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G     0  1.9G   0% /dev
tmpfs           386M  6.1M  380M   2% /run
/dev/sda2       262G   74G  175G  30% /
tmpfs           1.9G     0  1.9G   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/sdc1       459G  237G  199G  55% /share/libvid
/dev/sdb2       3.9G  227M  3.5G   7% /share/libmail
/dev/sde2       458G  237G  198G  55% /backup/Jamaica
/dev/sda1       7.9G  153M  7.3G   3% /boot
/dev/sdd1       458G  341G   94G  79% /share/Dauphin
/dev/sda6       3.9G  8.2M  3.7G   1% /home
/dev/sdb1       454G   68G  364G  16% /share/libdata
/dev/sda5       3.9G  8.2M  3.7G   1% /usr/local
/dev/sda7       7.9G  645M  6.8G   9% /share/miscback
/dev/sdd2       459G  322G  114G  74% /backup/Cayman
tmpfs           386M     0  386M   0% /run/user/0

**darkod & LHammonds**, **[FONT=Courier New]ls -l[/FONT]** returns this:
total 24
drwx------ 2 root  root  16384 Dec 23  2016 lost+found
drwxr-xr-x 4 qajaq qajaq  4096 Oct 27 00:10 qajaq
drwxr-xr-x 2 willy willy  4096 Oct 27 10:28 willy

**LHammonds**, the relevant line from my **[FONT=Courier New]fstab[/FONT]** is:
UUID=96d9970e-9e3f-465d-b246-39fed9a4b0d4  /home  ext3  defaults  0  2

The only work I've done recently on this machine has been to encrypt a partition that's on /dev/sde, an external HDD. Several months ago, I had to re-install the complete SSH system for this machine and two laptops. At that time, I did set **PermitRootLogin yes** in the **sshd_config** file, though I thought that applied only to login through SSH, not from bootup.

---

### Post by darkod on 2017-10-28
All parameters look correct, I have no idea what it might be. I would try the following:

1. When mounting sda6 as /home you have to make sure it mounts correctly each time. If one day it doesn't out of whatever reason, the OS could start writing files in the home folder on sda2 which should be empty. So I would boot it again from live-USB and open sda2 and check that the home folder is empty. Because all user folders should be on sda6.

2. After that I would boot the server as normal, try the login with your user and let it fail. After that log in with root and open /var/log/syslog to check any messages giving more details about the failed login attempt. Also check other logs like auth.log and similar...

See if that helps you find some reason that makes sense.

---

### Post by qajaq on 2017-10-28
Thanks for your suggestions, darkod. The **/home** directory is empty when the **sda6** partition is not mounted.

I tried the re-boot and log inspection and found nothing useful. I filtered by date-stamp and got a list of only five files in **/var/log** that have been touched today. Of these, only three were touched at the time of re-boot, the others being time-stamped before I even crawled out of bed this morning. The syslog is empty: zero bytes, and is one of the crack-o'-dawn files. Files **lastlog** and **wtmp** are data files, illegible to human eyes. The **apport.log** has six lines, all of which are time-stamped hours before I attempted the **qajaq** login.

Unless you (or anyone else) has any further suggestions, I am going to download a new ISO of the Ubuntu Server 16.04 and re-install the OS. It's beginning to look as though that will be more time-effective than further trouble-shooting.

---

### Post by darkod on 2017-10-28
Unfortunately I have no more ideas. If reinstalling and recreating your configuration is not too much time consuming, you are right, it will be much faster than troubleshooting this one.

---

### Post by qajaq on 2017-10-28
Thanks again for your effort, darkod. The only major configuration (apart from recreating the fstab, which I'll save on a backup disk and re-create, one line at a time, testing in between) will be setting up the SSH system. And I'll take the opportunity to check for root-login both before and after that process, to see if that may have been the trigger for allowing it.

---

