---
title: "Backups"
date: 2012-01-15
forum: Server Platforms
---

### Post by bubylou on 2012-01-15
The basic goal i wish to achieve is that i can have my /Share directory (which is being shared via samba) be backed up across my network to a windows 7 machines Shared folder called Backup. I just want to ensure that those files have a safety net just in case anything were to happen to the server. i would most likey do each backup manually since the windows machine is not always on and is my personal computer and i am also the only admin for this home server.
so far i have edited fstab to include the following line

//192.168.1.3/Backup /mnt/Backup  cifs credentials=/home/buby/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

Next i attempt to use rsync to backup the directory using the line below

rsync -avz /Share /mnt/Backup

which does make the file appear on the shared file on the windows machine but also uses local storage space which cause my server to run out of hd space.
im sure im just misunderstanding something or forgot some simple step. Let me know if you can help with my current backup plan or if you have a better idea.

---

### Post by volkswagner on 2012-01-15
You need to make sure the Windows folder is properly mounted prior to syncing.

A couple things to do...

Verify it is mounted:
```
mount
```

Then go to the windows machine an make a temporary folder and see if it shows up on the server.

```
ls -alt /mnt/Backup
```

---

### Post by bubylou on 2012-01-16
/mount


/dev/mapper/Bubylou-root on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda1 on /boot type ext2 (rw)
//192.168.1.3/Backup on /mnt/Backup type cifs (rw)

and ls -alt /mnt/Backup works

---

### Post by bubylou on 2012-01-16
Thank you for your help i believe its working now.

---

### Post by CharlesA on 2012-01-16
What was the problem/solution?

---

### Post by bubylou on 2012-01-16
Some issues with it not mounting properly. I retraced my steps, rebooted, mounted it again, and double checked to make sure it worked. Now everything works as it was intended.

---

### Post by CharlesA on 2012-01-16
Awesome. Don't forget to mark the thread as solved from thread tools. :)

---

