---
title: "Flash device file ownership and permissions"
date: 2010-02-19
forum: Security
---

### Post by mmmmna on 2010-02-19
I use several distributions of Linux, as well as needing to exchange files with a Windows environment. to do this, the easiest way is to use a USB based Flash device.

Today, as a user, I tried to create a folder on the Flash drive during a file-save, and although I could click the 'new folder' button and obtain a folder where the name string was in edit mode, once I created the name I wanted and I pressed the enter key, I got an alert that the folder could not be created. I tried that several times (I ultimately saved the file on the fixed disk drive). I tried closing and reopening the application, and repeating the folder creation was no good. Tried logging out and restarting the Xserver, repeated the creation attempt, still no go.

I opened a console, ran sudo, started a bash session (so I could execute several commands in a row), there I learned that the folder permissions were user:root. After several attempts to change permissions of the root folder (and the mount point), I learned that I could not change the ownership of the files and folders on the Flash device. I exited Ubuntu and booted Toorox, repeated the same permission changes, no success there either. So, in total, I tried KDE, Gnome, and console logins, Konqueror permissions/ownership changes, Konsole permissions/ownership changes, Nautilus permissions/ownership changes, console login permissions/ownership changes, nothing worked. I repeated most of those in Toorox, as well as Ubuntu Desktop for 64 bit running as live CD.



All I want to be able to do is, as a daily user, have 100% of the same user abilities that I had a few days ago (this never happened before a security update was installed a day or two ago), and the functionality I seek is the same as I've ever had on prior distros. Probably this is caused by some newer security paradigm, but I was not asked if I wanted permissions to be this way.

The OS presently allows me to save as user:user on the internal hard disk, and when I copy files from the hard disk to the Flash device, they will have user:root permissions on the Flash drive. When I copy a file from the Flash drive into my home directory on the hard disk, it has user:user permissions in the destination.

Filesystem configuration files:

```
mmmmna@RC410L800M:~/Desktop$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=34a76b81-186c-4945-9d55-70a3713e8b55 /               ext3    errors=remount-ro 0       1
# /home/mmmmna/Maxtor40G was on /dev/sdb1 during installation
UUID=10984e86-1f69-4bab-8b9a-996ecd875cac /home/mmmmna/Maxtor40G ext3    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=bff36ab5-3b40-4dbb-9d40-388630b16dbd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
mmmmna@RC410L800M:~/Desktop$
```


and


```
mmmmna@RC410L800M:~/Desktop$ cat /etc/mtab
/dev/sda3 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/sdb1 /home/mmmmna/Maxtor40G ext3 rw 0 0
/dev/sdg /media/disk-1 vfat rw,nosuid,nodev,uhelper=hal,uid=1000,utf8,shortname=mixed,flush 0 0
gvfs-fuse-daemon /home/mmmmna/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=mmmmna 0 0
mmmmna@RC410L800M:~/Desktop$
```

What should I do to have the ability to create a folder on a Flash drive which is the Flash device that my daily user inserts? I could do it a few days ago, but not now.....

---

### Post by cdenley on 2010-02-19
The FAT filesystem has no support for any kind of permissions, as far as I know. It certainly doesn't store Linux permissions. They are assigned at mount time. It appears it is already mounted so your default user (uid 1000) should be the user, though.
```

grep " vfat " /etc/mtab
grep " vfat " /etc/mtab|cut -d " " -f 2|xargs ls -ld

```

---

### Post by DawieS on 2010-02-19
Check inside the Recycled/Trash bins of the flash drive using your file browser (Enable show hidden files first). They probably contain a nasty trojan/virus currently in circulation.

I tried to delete one from a flash-drive the other day, and was unable to. It just produces the message 'Operation Not Supported', and replicates itself inside the Trash with each click, each time producing a hidden folder containing an autorun.ini and NAME.exe hidden files, where NAME is the name of the parent folder.

If you delete the Recycled/Trash itself, it creates a new one, only this time containing twice as many hidden folders and files. It seems as if this virus is independant of the type of operating system, but specifically targets FAT32 file-systems. I had to re-format the flash-drive to get rid of it.

---

### Post by mmmmna on 2010-02-19
> **cdenley said:**
> The FAT filesystem has no support for any kind of permissions, as far as I know. It certainly doesn't store Linux permissions. They are assigned at mount time. It appears it is already mounted so your default user (uid 1000) should be the user, though.
```

grep " vfat " /etc/mtab
grep " vfat " /etc/mtab|cut -d " " -f 2|xargs ls -ld

```


With the Flash drive mounted:
```
mmmmna@RC410L800M:/media/disk-1$ grep " vfat " /etc/mtab
/dev/sdg /media/disk-1 vfat rw,nosuid,nodev,uhelper=hal,uid=1000,utf8,shortname=mixed,flush 0 0
mmmmna@RC410L800M:/media/disk-1$
mmmmna@RC410L800M:/media/disk-1$
mmmmna@RC410L800M:/media/disk-1$ grep " vfat " /etc/mtab|cut -d " " -f 2|xargs ls -ld
drwxr-xr-x 6 mmmmna root 16384 2010-02-19 16:10 /media/disk-1
mmmmna@RC410L800M:/media/disk-1$
```

I understand that FAT doesn't save Linux permissions, but, no matter how the permissions appear as being assigned to the files, something in Ubuntu makes the OS obey the permissions as if the filesystem was a native filesystem. I'm assuming hald does the work, and the mtab declares the permissions; however, mtab is dynamic, so what assigns the variables in mtab?

With the Flash drive 'safely removed':
```
mmmmna@RC410L800M:~$ cd /media/disk-1
bash: cd: /media/disk-1: No such file or directory
mmmmna@RC410L800M:~$
mmmmna@RC410L800M:~$
mmmmna@RC410L800M:~$ grep " vfat " /etc/mtab
mmmmna@RC410L800M:~$
mmmmna@RC410L800M:~$
mmmmna@RC410L800M:~$ grep " vfat " /etc/mtab|cut -d " " -f 2|xargs ls -ld
drwxr-xr-x 55 mmmmna mmmmna 4096 2010-02-19 19:46 .
mmmmna@RC410L800M:~$
```

---

### Post by mmmmna on 2010-02-19
> **DawieS said:**
> Check inside the Recycled/Trash bins of the flash drive using your file browser (Enable show hidden files first). They probably contain a nasty trojan/virus currently in circulation.

I tried to delete one from a flash-drive the other day, and was unable to. It just produces the message 'Operation Not Supported', and replicates itself inside the Trash with each click, each time producing a hidden folder containing an autorun.ini and NAME.exe hidden files, where NAME is the name of the parent folder.

If you delete the Recycled/Trash itself, it creates a new one, only this time containing twice as many hidden folders and files. It seems as if this virus is independant of the type of operating system, but specifically targets FAT32 file-systems. I had to re-format the flash-drive to get rid of it.

Nope, no Windows Trojans in the trash. Just a word processor document I deleted this morning. This Flash drive has not seen Windows since I reformatted it a month ago.

---

### Post by DawieS on 2010-02-19
The problem could be with the flash-drive itself. I also had the same updates as you, and have just tested with 2 different flash-drives without any problems in creating and copying files and folders to and from them.

If you have used the flash for a bootable installation drive, you have to re-format to get it in exactly the same condition as new (Just by deleting everything on it is not good enough). I found this out when my TV would not even mount such a flash, let alone play the movie that was copied on it!

Have you tried another flash? This would confirm whether or not something may have gone wrong with your installation, or whether the flash itself is to blame. If so, re-format the flash. If it is still not working, I am afraid it is time for a replacement.

---

### Post by rookcifer on 2010-02-19
The FAT filesystem does not allow for any concept of file permissions, even on Windows.  This is one reason why Win95-ME security sucked so badly -- everyone ran as a superuser with no way to restrict access.

It sucks that we are forced to use FAT, but sadly it is the case if you want the use a flash drive on both Windows and Linux machines.  

At any rate, try backing up the files and then formatting it fresh.  And try navigating the flash drive as root when you are viewing it from Linux.  This might help overcome any perceived "permissions" problems.

---

### Post by cdenley on 2010-02-20
I guess I misunderstood your first post, because all your permissions appear correct. They are owned by "mmmmna", not root. The filesystem's permissions are set at mount time. You appear to be allowing nautilus to mount the filesystem. It used to pull the mount options from gconf, but not anymore apparently.

You should have permission to create new directories in the device root directory as the user "mmmmna". If not, I don't think this is a permissions issue, but a device issue. Is there a write-protect switch on the device?

---

### Post by mmmmna on 2010-02-21
The problem is not just on one Flash device, it is, so far, EVERY removable device, and only if it is inserted as the only removable device.

Some history...

Installed 'Ubuntu 9.10 Desktop for 64 Bit' onto this system about Feb 2.

Used Gnome for the first week or so, used the first Flash drive as I expected - created folders, renamed folders, deleted files.

Feb 12, I installed KDE 4.3.2 (which oddly called itself Kubuntu during boot screens), and I use the Plasma desktop. I really didn't pay too much attention to Flash drives.

Used KDE/Kubuntu until the day I posted the first post in this thread. That day is when I noticed the situation where I could not create nor rename anything on a Flash device which I use daily.

I recall that there was a software update message on either the 10th or the 11th of Feb. I _believe_ I had no problems before that software update (after installing KDE) but I an not certain.

Along the way, I'm exploring KDE 4.3.2, which is new to me (I just left 3.5.x), and I'm trying to setup Dolphin in a way that I like.

Today, using KDE, I insert an SD card that has been working fine under Ubuntu Netbook Remix 9.10 (in my EeePC 900A which I disassembled 2 days ago for amajor upgrade and this cannot use the EeePC 900A), and that SD card has the permissions problems, and I verified the problem in Dolphin (tried renaming a folder), and at the bash prompt (CD /media/disk-1, cannot touch a file) Of note is that this device is an SDHC, 8Gigs, so cannot be the older FAT (FAT16?).

Today, using KDE, WHILE the 8Gig SDHC card was still mounted, I then mounted the initial Flash drive (the one where I first discovered the permissions problem). It mounts at /media/disk-2 (the SDHC card is using the /media/disk-1 mount point, so hald/whatever is mounting the next Flash device at /media/disk-2). And guess what? The Flash device acts normally, I can touch files at the command prompt, and the permissions that Dolphin is displaying are mmmmna:root.

I just looked at the permissions of the media directory:

```
mmmmna@RC410L800M:/media$ ls -la
total 44
drwxr-xr-x  6 root   root  4096 2010-02-21 12:34 .
drwxr-xr-x 22 root   root  4096 2010-02-09 13:20 ..
lrwxrwxrwx  1 root   root     6 2010-02-02 14:24 cdrom -> cdrom0
drwxr-xr-x  2 root   root  4096 2010-02-02 14:24 cdrom0
lrwxrwxrwx  1 root   root    45 2010-02-12 15:12 .directory -> /etc/kubuntu-default-settings/directory-media
drwxr-xr-x  2 root   root  4096 2010-02-19 14:59 disk
drwxr-xr-x  8 mmmmna root  8192 1969-12-31 19:00 disk-1
drwxr-xr-x  6 mmmmna root 16384 1969-12-31 19:00 disk-2
-rw-r--r--  1 root   root   193 2010-02-21 12:34 .hal-mtab
-rw-------  1 root   root     0 2010-02-21 11:01 .hal-mtab-lock
lrwxrwxrwx  1 root   root    42 2010-02-12 15:12 .hidden -> /etc/kubuntu-default-settings/hidden-media
mmmmna@RC410L800M:/media$
```


and as before:
```
mmmmna@RC410L800M:/media$ grep " vfat " /etc/mtab
/dev/sdc1 /media/disk-1 vfat rw,nosuid,nodev,uhelper=hal,uid=1000,utf8,shortname=mixed,flush 0 0
/dev/sdg /media/disk-2 vfat rw,nosuid,nodev,uhelper=hal,uid=1000,utf8,shortname=mixed,flush 0 0
mmmmna@RC410L800M:/media$
```

and

```
mmmmna@RC410L800M:/media$ grep " vfat " /etc/mtab|cut -d " " -f 2|xargs ls -ld
drwxr-xr-x 8 mmmmna root  8192 1969-12-31 19:00 /media/disk-1
drwxr-xr-x 6 mmmmna root 16384 1969-12-31 19:00 /media/disk-2
mmmmna@RC410L800M:/media$
```
Interesting modification date....

```
mmmmna@RC410L800M:/media$ date
Sun Feb 21 14:54:15 EST 2010
mmmmna@RC410L800M:/media$
```

---

### Post by cdenley on 2010-02-21
I still don't see a permissions problem. All output you posted is what I would expect to see.
```

ls -ld /media/disk-1
id
mkdir /media/disk-1/test

```

---

### Post by mmmmna on 2010-02-22
Freshly booted, have not mounted ANY Flash media:
```
mmmmna@RC410L800M:~$
mmmmna@RC410L800M:~$ grep " vfat " /etc/mtab
mmmmna@RC410L800M:~$
mmmmna@RC410L800M:~$ grep " vfat " /etc/mtab|cut -d " " -f 2|xargs ls -ld
drwxr-xr-x 57 mmmmna mmmmna 4096 2010-02-22 08:39 .
mmmmna@RC410L800M:~$
mmmmna@RC410L800M:~$ ls -ld /media/disk-1
ls: cannot access /media/disk-1: No such file or directory
mmmmna@RC410L800M:~$
mmmmna@RC410L800M:~$ id
uid=1000(mmmmna) gid=1000(mmmmna) groups=4(adm),20(dialout),24(cdrom),46(plugdev),104(lpadmin),115(admin),120(sambashare),1000(mmmmna)
mmmmna@RC410L800M:~$
```

Inserted a 2Gig Compact Flash card that has not been used with Ubuntu 9.10 64 bit. I have not yet opened the device as a user, KDE device notifier shows it as present but the safely remove ability is not presented, safely remove is only presented after I open the device using KDE device notifier.
```
mmmmna@RC410L800M:~$ grep " vfat " /etc/mtab
mmmmna@RC410L800M:~$
mmmmna@RC410L800M:~$ grep " vfat " /etc/mtab|cut -d " " -f 2|xargs ls -ld
drwxr-xr-x 57 mmmmna mmmmna 4096 2010-02-22 08:39 .
mmmmna@RC410L800M:~$
mmmmna@RC410L800M:~$ ls -ld /media/disk-1
ls: cannot access /media/disk-1: No such file or directory
mmmmna@RC410L800M:~$
```

Next, I opened the Flash device using KDE device notifier (safely remove feature activates):```
mmmmna@RC410L800M:~$
mmmmna@RC410L800M:~$ grep " vfat " /etc/mtab
/dev/sdd /media/2G\040CF vfat rw,nosuid,nodev,uhelper=hal,uid=1000,utf8,shortname=mixed,flush 0 0
mmmmna@RC410L800M:~$ grep " vfat " /etc/mtab|cut -d " " -f 2|xargs ls -ld
ls: cannot access /media/2G040CF: No such file or directory
mmmmna@RC410L800M:~$ ls -ld /media/disk-1
ls: cannot access /media/disk-1: No such file or directory
mmmmna@RC410L800M:~$ id
uid=1000(mmmmna) gid=1000(mmmmna) groups=4(adm),20(dialout),24(cdrom),46(plugdev),104(lpadmin),115(admin),120(sambashare),1000(mmmmna)
mmmmna@RC410L800M:~$ mount
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sdb1 on /home/mmmmna/Maxtor40G type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mmmmna/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mmmmna)
/dev/sdd on /media/2G CF type vfat (rw,nosuid,nodev,uhelper=hal,uid=1000,utf8,shortname=mixed,flush)
mmmmna@RC410L800M:~$ ls -la /media/
total 24
drwxr-xr-x  5 root   root 4096 2010-02-22 08:50 .
drwxr-xr-x 22 root   root 4096 2010-02-09 13:20 ..
drwxr-xr-x  3 mmmmna root 4096 1969-12-31 19:00 2G CF
lrwxrwxrwx  1 root   root    6 2010-02-02 14:24 cdrom -> cdrom0
drwxr-xr-x  2 root   root 4096 2010-02-02 14:24 cdrom0
lrwxrwxrwx  1 root   root   45 2010-02-12 15:12 .directory -> /etc/kubuntu-default-settings/directory-media
drwxr-xr-x  2 root   root 4096 2010-02-19 14:59 disk
-rw-r--r--  1 root   root   95 2010-02-22 08:50 .hal-mtab
-rw-------  1 root   root    0 2010-02-22 08:50 .hal-mtab-lock
lrwxrwxrwx  1 root   root   42 2010-02-12 15:12 .hidden -> /etc/kubuntu-default-settings/hidden-media
mmmmna@RC410L800M:~$ touch /media/2G\ CF/test
mmmmna@RC410L800M:~$ mkdir /media/2G\ CF/test
mkdir: cannot create directory `/media/2G CF/test': File exists
mmmmna@RC410L800M:~$ mkdir /media/2G\ CF/testa
mmmmna@RC410L800M:~$
```
Ok, maybe this is device by device?

ADDING the same device as before - the 131Meg Flash drive.
```
mmmmna@RC410L800M:~$ grep " vfat " /etc/mtab
/dev/sdd /media/2G\040CF vfat rw,nosuid,nodev,uhelper=hal,uid=1000,utf8,shortname=mixed,flush 0 0
/dev/sdg /media/disk-1 vfat rw,nosuid,nodev,uhelper=hal,uid=1000,utf8,shortname=mixed,flush 0 0
mmmmna@RC410L800M:~$
mmmmna@RC410L800M:~$ grep " vfat " /etc/mtab|cut -d " " -f 2|xargs ls -ld
ls: cannot access /media/2G040CF: No such file or directory
drwxr-xr-x 6 mmmmna root 16384 1969-12-31 19:00 /media/disk-1
mmmmna@RC410L800M:~$
mmmmna@RC410L800M:~$ ls -ld /media/disk-1
drwxr-xr-x 6 mmmmna root 16384 1969-12-31 19:00 /media/disk-1
mmmmna@RC410L800M:~$ mount
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sdb1 on /home/mmmmna/Maxtor40G type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mmmmna/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mmmmna)
/dev/sdd on /media/2G CF type vfat (rw,nosuid,nodev,uhelper=hal,uid=1000,utf8,shortname=mixed,flush)
/dev/sdg on /media/disk-1 type vfat (rw,nosuid,nodev,uhelper=hal,uid=1000,utf8,shortname=mixed,flush)
mmmmna@RC410L800M:~$ ls -la /media/
total 40
drwxr-xr-x  6 root   root  4096 2010-02-22 08:57 .
drwxr-xr-x 22 root   root  4096 2010-02-09 13:20 ..
drwxr-xr-x  4 mmmmna root  4096 2010-02-22 08:54 2G CF
lrwxrwxrwx  1 root   root     6 2010-02-02 14:24 cdrom -> cdrom0
drwxr-xr-x  2 root   root  4096 2010-02-02 14:24 cdrom0
lrwxrwxrwx  1 root   root    45 2010-02-12 15:12 .directory -> /etc/kubuntu-default-settings/directory-media
drwxr-xr-x  2 root   root  4096 2010-02-19 14:59 disk
drwxr-xr-x  6 mmmmna root 16384 1969-12-31 19:00 disk-1
-rw-r--r--  1 root   root   191 2010-02-22 08:57 .hal-mtab
-rw-------  1 root   root     0 2010-02-22 08:50 .hal-mtab-lock
lrwxrwxrwx  1 root   root    42 2010-02-12 15:12 .hidden -> /etc/kubuntu-default-settings/hidden-media
mmmmna@RC410L800M:~$ touch /media/disk-1/test
mmmmna@RC410L800M:~$ mkdir /media/disk-1/testa
mmmmna@RC410L800M:~$
```

Well, what can I say...? Does something in that last update need 8 or more cold boots to get fully configured?

Next, plugged in 2 more flash devices, totalling 4 devices mounted at one time (I have yet 2 more usb ports and 2 more flash drives).
```
mmmmna@RC410L800M:~$
mmmmna@RC410L800M:~$ mount
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sdb1 on /home/mmmmna/Maxtor40G type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mmmmna/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mmmmna)
/dev/sdd on /media/2G CF type vfat (rw,nosuid,nodev,uhelper=hal,uid=1000,utf8,shortname=mixed,flush)
/dev/sdg on /media/disk-1 type vfat (rw,nosuid,nodev,uhelper=hal,uid=1000,utf8,shortname=mixed,flush)
/dev/sdc1 on /media/disk-2 type vfat (rw,nosuid,nodev,uhelper=hal,uid=1000,utf8,shortname=mixed,flush)
mmmmna@RC410L800M:~$ grep " vfat " /etc/mtab
/dev/sdd /media/2G\040CF vfat rw,nosuid,nodev,uhelper=hal,uid=1000,utf8,shortname=mixed,flush 0 0
/dev/sdg /media/disk-1 vfat rw,nosuid,nodev,uhelper=hal,uid=1000,utf8,shortname=mixed,flush 0 0
/dev/sdc1 /media/disk-2 vfat rw,nosuid,nodev,uhelper=hal,uid=1000,utf8,shortname=mixed,flush 0 0
mmmmna@RC410L800M:~$ grep " vfat " /etc/mtab|cut -d " " -f 2|xargs ls -ld
ls: cannot access /media/2G040CF: No such file or directory
drwxr-xr-x 6 mmmmna root 16384 2010-02-22 09:01 /media/disk-1
drwxr-xr-x 8 mmmmna root  8192 1969-12-31 19:00 /media/disk-2
mmmmna@RC410L800M:~$ ls -la /media/
total 48
drwxr-xr-x  7 root   root  4096 2010-02-22 09:02 .
drwxr-xr-x 22 root   root  4096 2010-02-09 13:20 ..
drwxr-xr-x  4 mmmmna root  4096 2010-02-22 08:54 2G CF
lrwxrwxrwx  1 root   root     6 2010-02-02 14:24 cdrom -> cdrom0
drwxr-xr-x  2 root   root  4096 2010-02-02 14:24 cdrom0
lrwxrwxrwx  1 root   root    45 2010-02-12 15:12 .directory -> /etc/kubuntu-default-settings/directory-media
drwxr-xr-x  2 root   root  4096 2010-02-19 14:59 disk
drwxr-xr-x  6 mmmmna root 16384 2010-02-22 09:01 disk-1
drwxr-xr-x  8 mmmmna root  8192 1969-12-31 19:00 disk-2
-rw-r--r--  1 root   root   288 2010-02-22 09:02 .hal-mtab
-rw-------  1 root   root     0 2010-02-22 08:50 .hal-mtab-lock
lrwxrwxrwx  1 root   root    42 2010-02-12 15:12 .hidden -> /etc/kubuntu-default-settings/hidden-media
mmmmna@RC410L800M:~$ touch /media/disk-2/test
mmmmna@RC410L800M:~$ mkdir /media/disk-2/test
mkdir: cannot create directory `/media/disk-2/test': File exists
mmmmna@RC410L800M:~$ mkdir /media/disk-2/testa
mmmmna@RC410L800M:~$
mmmmna@RC410L800M:~$ mkdir /media/disk-3/testa
mmmmna@RC410L800M:~$ touch /media/disk-3/test
mmmmna@RC410L800M:~$
```Just wonderful.
Until it repeats... 
Thanks for the help, this problem is now vapor.

---

