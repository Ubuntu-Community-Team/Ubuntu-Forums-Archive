---
title: "Partition and backup help!"
date: 2012-10-24
forum: Server Platforms
---

### Post by sanumala on 2012-10-24
Hi 

I am planning to install ubuntu 12.04 LTS server on my computer which has new 2TB hdd. I need help on following.

1. What is the best way of partitioning this HDD. Basically I wanted to create a backup partition on the same drive as /backup
2. Once partitions are created how to setup backup using rsync. I wanted to setup daily, weekly and monthly backups using rsync into /backup partition from all other partitions and automate using CRON.

I have found some useful links in arch linux wiki 
```
rsync -aAXv /* $1 --exclude={/dev/*,/proc/*,/sys/*,/tmp/*,/run/*,/mnt/*,/media/*,/lost+found,/home/*/.gvfs,/var/lib/pacman/sync/*}
```

Assuming /(root) and swap as 2 basic partitions how can I backup my complete root(/) into /backup and by default I don't want to mount /backup but during backup script should mount /backup automatically and once backup is completed it should unmount it.

I am also thinking of putting server into single user mode (init 1) during backups but not sure how to do

Here is want I am assuming
singuleuser.sh
```
#!/bin/bash
sudo init 1 # how to provide password
```

mount.sh
```
sudo mount /dev/sda2 /backup
```
backup.sh
```
#!/bin/bash
rsync -options 
```

unmount.sh
```
sudo umount  /backup
```

swithback.sh
```
#!/bin/bash
sudo init 5
```

I wanted to combine everything into one or two scripts which will fulfill my needs :)
Waiting for the response GuRu'S

---

### Post by oldfred on 2012-10-24
I have links to some examples.

Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh
Some more examples:
[http://rsync.samba.org/examples.html](http://rsync.samba.org/examples.html)

Backup to external with check of mounted & email
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)

rsync confirmation list:
[http://ubuntuforums.org/showthread.php?t=1692800](http://ubuntuforums.org/showthread.php?t=1692800)
Check for mount of backup partition
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
#[http://ubuntuforums.org/showthread.php?t=1555647&page=4](http://ubuntuforums.org/showthread.php?t=1555647&page=4)
more scripts:
[http://ubuntuforums.org/showthread.php?t=1319155](http://ubuntuforums.org/showthread.php?t=1319155)

Some files to exclude from /home:
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

You do not put sudo into scripts. If running manually you run script with sudo or run as root so sudo not needed in script.
I found using the separate excludes file reduces complexity of rsync line, but then requires another file.

rsync -aurvlP --exclude-from=mybackup_excludes.lst /home /mnt/backup

# mybackup_excludes.lst
# Note: Trailing SLASHES MATTER, copy form exactly!!!
/home/*/.cache
/home/*/.dbus
/home/*/.dropbox
/home/*/.gvfs
/home/*/.local/share/Trash
/home/*/.mozilla/firefox/*.default/Cache/**
/home/*/.qt
/home/*/.thumbnails
/home/*/Examples
/home/.ecryptfs
/home/lost+found

---

### Post by sanumala on 2012-10-24
Thanks for the quick reply. Let me check all these and once done I will share my script. 
> **oldfred said:**
> I have links to some examples.

Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh
Some more examples:
[http://rsync.samba.org/examples.html](http://rsync.samba.org/examples.html)

Backup to external with check of mounted & email
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)

rsync confirmation list:
[http://ubuntuforums.org/showthread.php?t=1692800](http://ubuntuforums.org/showthread.php?t=1692800)
Check for mount of backup partition
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
#[http://ubuntuforums.org/showthread.php?t=1555647&page=4](http://ubuntuforums.org/showthread.php?t=1555647&page=4)
more scripts:
[http://ubuntuforums.org/showthread.php?t=1319155](http://ubuntuforums.org/showthread.php?t=1319155)

Some files to exclude from /home:
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by LHammonds on 2012-10-26
The 1st thing I do is partition my server to be flexible using LVM and separation.  See my Ubuntu Server link in my sig for details.

For full-server backups, I use LVM snapshots + FSArchiver to backup the entire server (while online...no downtime).

For data backups, I use rsync and copy data files to a backup (/bak) partition.  I then archive them and copy them to a remote server.  This allows me to restore the most recent files which remain in the /bak partition and if necessary, I can go back in time to my offsite location and retrieve dated archives.

If I need to restore a partition, I reboot the server and boot to a rescue CD and use FSArchive to restore whatever partitions I need from my /bak partition or from my remote site.

LHammonds

---

