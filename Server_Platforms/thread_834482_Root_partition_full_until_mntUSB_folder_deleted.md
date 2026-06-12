---
title: "Root partition full until /mnt/USB folder deleted"
date: 2008-06-19
forum: Server Platforms
---

### Post by retsofbob on 2008-06-19
Hello,

I am running 6.06.2 Server as an email server and have been backing things up with a daily rsync to an external USB drive.  This morning, following the cron.daily jobs my root partition was full.  I could not find any problems with big log files or anything else.  After looking all over I decided to unmount the USB drive and finally tried deleting the /mnt/USB/migration/zimbra folder that held my backups.  That did the trick.  But I do not understand why.  Anybody out there know why? 

Here's how I mount the USB drive:
sudo mount -t ext3 /dev/sda1 /mnt/USB/

Here's the output from my console while I was hosed:

$ sudo df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/cciss/c0d0p2      19G   18G     0 100% /
varrun                2.0G   48K  2.0G   1% /var/run
varlock               2.0G  4.0K  2.0G   1% /var/lock
udev                  2.0G  112K  2.0G   1% /dev
devshm                2.0G     0  2.0G   0% /dev/shm
/dev/cciss/c0d0p3     437G   80G  335G  20% /opt

$ sudo du -s -h * 
3.1M    bin
9.6M    boot
0       cdrom
224K    dev
6.3M    etc
112K    home
4.0K    initrd
0       initrd.img
76M     lib
48K     lost+found
8.0K    media
18G     mnt
80G     opt
du: `proc/23471': No such file or directory
du: `proc/23573': No such file or directory
915M    proc
24K     root
8.0M    sbin
4.0K    srv
0       sys
1.3M    tmp
182M    usr
502M    var
0       vmlinuz

So, I did the following:
$ sudo umount /mnt/USB
umount: /mnt/USB: not mounted

$ sudo df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/cciss/c0d0p2      19G   18G     0 100% /
varrun                2.0G   48K  2.0G   1% /var/run
varlock               2.0G  4.0K  2.0G   1% /var/lock
udev                  2.0G  112K  2.0G   1% /dev
devshm                2.0G     0  2.0G   0% /dev/shm
/dev/cciss/c0d0p3     437G   80G  335G  20% /opt

/$ cd /mnt
/mnt$ ls -l
total 4
drwxr-xr-x 3 root root 4096 2008-06-19 06:25 USB
/mnt$ cd USB
/mnt/USB$ ls -l
total 4
drwxr-xr-x 3 root root 4096 2008-06-19 06:25 migration

/mnt/USB$ sudo rm -r -d migration/zimbra/

$ sudo df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/cciss/c0d0p2      19G  916M   17G   6% /
varrun                2.0G   48K  2.0G   1% /var/run
varlock               2.0G  4.0K  2.0G   1% /var/lock
udev                  2.0G  112K  2.0G   1% /dev
devshm                2.0G     0  2.0G   0% /dev/shm
/dev/cciss/c0d0p3     437G   80G  335G  20% /opt

---

### Post by firecat53 on 2008-06-19
It looks like for some reason, the USB drive was not mounted when the backup ran, or failed to mount properly, or had some other issue. In any case, if the drive is not mounted, remember that /mnt/USB is still a valid directory under the root / directory. So if you are expecting your backup to go the the drive and the drive isn't mounted, it will still go into the /mnt/USB directory....causing big problems if you don't have a huge root partition!

I wrote a little script for my backups. First part is for an internal hard drive that's normally unmounted to mount it after checking that it's not already mounted ....

```
if [ `mount | grep /mnt/backup1 | wc -l` = 0 ]; then
  mount /mnt/backup1
  if [ $? != "0" ]; then
	echo "Could not mount share"
	exit
  fi
fi
```
Second part checks a samba share to make sure it's mounted by checking the existence of one of the directories in it:

```
if [ ! -d /mnt/mediacenter/Pictures ]; then
   mount /mnt/mediacenter
   if [ $? != "0" ]; then
        echo "Could not mount share"
        exit
   fi
fi
```

I'm no scripting expert, so there very well be a MUCH better way to do this!! This is just part of the script that would speak to your issue, btw.

Good luck!
Scott

---

### Post by retsofbob on 2008-06-19
firecat53,

Thank you for your reply.

I think you're right-on with that explanation.  I don't know how it was not mounted as it has been in use for several weeks, but something must have happened to that mount point.  Thanks for the script that checks the mount before accessing it.  I think I will implement something along those lines.

Bob

---

