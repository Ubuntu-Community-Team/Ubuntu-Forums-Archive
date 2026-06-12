---
title: "Urgent: Problems with HDDs (server backup)"
date: 2008-11-14
forum: Server Platforms
---

### Post by Titan8990 on 2008-11-14
I have had countless issues with the backups on my server (check my started threads).

My current problem, I have no idea how to solve.


If I run sudo fdisk -l, it hangs. If i try to list a directory on my backup drive, it hangs. CTRL+C interupts do nothing.

If I try to umount the backup drive to remount it:


```
jordan@einstein:~$ sudo umount /dev/sda1
umount: /media/backup: device is busy
umount: /media/backup: device is busy

```

```
jordan@einstein:~$ mount
/dev/sdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sda1 on /media/backup type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)

```

I found two of my backup scripts were still running and hanging. I killed those processes but the drive still remains flagged as busy.

Anyways, does anyone have any advice to resolve this issue without a reboot?

Thanks in advance for any help.

edit:

This is my backup scripts:

```
jordan@einstein:~$ cat /scripts/rsync.sh
#!/bin/sh

# %Y     year
# %m     month (01..12)
# %d     day of month (e.g, 01)
# %s     seconds since 1970-01-01 00:00:00 UTC

# Variable for the Program
BACKUPDIR=/
THEDATE=`date '+%Y%m%d-%s'`
LOGDIR=/var/log/backup
EXCLUDEFILE=/scripts/exclude
LOGFILE=/var/log/backup/rsync-$THEDATE.log
GZFILE=/var/log/backup/rsync-$THEDATE.gz
DESTINATION=/media/backup/backup0
LAST=/media/backup/backup5
MNTPOINT=/media/backup/
BACKUPD=/dev/sda1

#Check to make sure that our backup drive is mounted - To be included later


#If the log directory does not exist then create it

if [ ! -d $LOGDIR ]; then
    mkdir -p $LOGDIR
fi

#If the destination directory does not exist then create it

if [ ! -d $DESTINATION ]; then
        mkdir -p $DESTINATION
fi

#Rotate the backups

rm -rf $LAST
mv /media/backup/backup4 $LAST
mv /media/backup/backup3 /media/backup/backup4
mv /media/backup/backup2 /media/backup/backup3
mv /media/backup/backup1 /media/backup/backup2
cp -al $DESTINATION /media/backup/backup1

#Now run rsync to backup the filesystem

rsync -altvr --delete --delete-excluded --exclude-from=$EXCLUDEFILE --log-file=$LOGFILE $BACKUPDIR $DESTINATION

# gunzip the logfile
gzip -c $LOGFILE > $GZFILE

# delete the original, uncompressed logfile
rm $LOGFILE
```

---

### Post by jimv on 2008-11-14
Sounds like the drive is dying/dead.  You should test it in another machine, and if the same problem continues, get a new one.

---

### Post by Titan8990 on 2008-11-14
The drive is only about 6 months old. There is no clicking etc. This drive is hooked up via usb. I had issues with the drive being hooked up via eSATA in combination with my 3com RAID card where the BIOS would not detect it.

Should I just hook it up to another machine without worrying about umounting the drive???

---

### Post by Titan8990 on 2008-11-14
Update:

I plugged the drive into a different computer and was able to mount and view the contents of the drive....


Recently I added the lt arguments to my rsync script. Could that be the cause?

---

### Post by cariboo on 2008-11-14
If you are having problems with the drive using different methods of connection, I would suggest as the previous poster said that you drive is probably defective. As you said it is only six months old so getting a warranty replacement should be no problem. 

The best thng to do, is to go to the hard drive manufacturers web site and download the diagnostic tools for your hard drive then run them on your device. If it is defective, the diagnostic program will tell you when the warranty ends and it will give you a diagnostic code that you will need to get an RMA.

Jim

---

### Post by Titan8990 on 2008-11-14
Warrenty is 5 years and we buy these HDDs by the boxes. I will follow your instructions however, I do not think that hardware failure is the case here.


Edit:


lsusb also hangs. Because CRTL+C didn't not work I had to go through and manually kill the processes.

---

### Post by Titan8990 on 2008-11-17
I ended up rebooting the machine. All the backups over the weekend happened successfully. 

Still not sure what happened. It is fixed for now but I have a feeling this problem will occur again.

---

### Post by jimv on 2008-11-17
LOL, the good old reboot comes through again.

---

### Post by The Cog on 2008-11-17
I know it's a long shot, but I have seen a dodgy USB cable cause problems similar to those you describe. I was very surprised at the transformation a cable swap made.

---

### Post by Titan8990 on 2008-11-18
last bump

---

### Post by Titan8990 on 2008-11-19
Well, I said last bump but the problem has now began to occur again.

If I can't resolve this issue than my Linux server is a failure. I have been trying to push for a less proprietary environment at my work which relies heavily on Windows Servers. I will fail to do so if I can't keep this machine going. Rebooting every couple days is not an option.

Oddly enough in my time with this company the Linux box is the only one that I didn't get to pick the parts for. My boss picked out at the time, was one of the first AMD integrated NBs *sigh*. Probably couldn't have been a worse choice in terms of compatibility but it is what I have to work with.

Suggestions are always appreciated.

---

### Post by bapoumba on 2008-11-19
Moved to Servers.

---

### Post by Titan8990 on 2008-11-20
dump for new section

---

