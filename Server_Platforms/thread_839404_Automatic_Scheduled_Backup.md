---
title: "Automatic Scheduled Backup"
date: 2008-06-24
forum: Server Platforms
---

### Post by dewman0012 on 2008-06-24
Hi Guys and Girls,

We have just finished up our Ubuntu Server and it is running solid, finally! Now we need to plan out our recovery steps as needed. As of right now, we need to start doing backups of our server to an external harddrive. So my question is simple, how do I go about automatically backing up our server on a scheduled basis?

Thanks in advance!

---

### Post by firecat53 on 2008-06-24
I wrote a simple little script that mounts and backs up our main computer and the server to the extra hard drive on the server. It just uses rsync, so no fancy hard-linking for backups of older deleted files, although you could (and I may) substitute rdiff-backup for rsync pretty easily.

```
#!/bin/sh
#Backup script Documents
#Do a sort of incremental backup to the 400G harddrive, 2 partitions
#Need to check if MEDIACENTER is mounted, because it will mount more than once. The other disks won't mount if already mounted.

if [ ! -d /mnt/mediacenter/Pictures ]; then
   mount /mnt/mediacenter
   if [ $? != "0" ]; then
        echo "Could not mount share"
        exit
   fi
fi

#Mount the 200G partition for backup from MEDIACENTER (should already be mounted)
if [ `mount | grep /mnt/backup2 | wc -l` = 0 ]; then
  mount /mnt/backup2
  if [ $? != "0" ]; then
        echo "Could not mount share" 
        umount /mnt/mediacenter
        exit
  fi
fi

#Mount the second 200G parition for a second backup, one day behind
if [ `mount | grep /mnt/backup3 | wc -l` = 0 ]; then
  mount /mnt/backup3
  if [ $? != "0" ]; then
        echo "Could not mount share" 
        umount /mnt/backup2
	umount /mnt/mediacenter
        exit
  fi
fi

#Mount the 35G partition to backup the pictures
if [ `mount | grep /mnt/backup1 | wc -l` = 0 ]; then
  mount /mnt/backup1
  if [ $? != "0" ]; then
	echo "Could not mount share"
	umount /mnt/backup3
	umount /mnt/mediacenter
	exit
  fi
fi

rsync -aq --delete /mnt/backup2/ /mnt/backup3
rsync -aq --delete /etc /mnt/backup2/server
rsync -aq --delete /home /mnt/backup2/server
rsync -aq --delete /usr/local /mnt/backup2/server
rsync -aq --delete /var/www /mnt/backup2/server
rsync -aq --modify-window=10 --delete /mnt/mediacenter /mnt/backup2 &2> /dev/null
rsync -aq --delete /mnt/backup2/mediacenter/Pictures /mnt/backup1
umount /mnt/backup1
umount /mnt/backup3
umount /mnt/mediacenter


```

Probably a little confusing, since it's particular to my setup, but I think you get the general idea. I put this script in /usr/local/bin, and run a cron job every day just after midnight that executes the script. I have one other little script that additionally backs up to our webspace. Mediacenter is our vista computer, and /mnt/mediacenter is a samba share (cifs) with an fstab entry like:

```
# Mediacenter
//192.168.0.100/username	/mnt/mediacenter	cifs	credentials=/home/username/.smbpasswd,uid=1000,gid=users,users,noauto	0	0

```

The cron job (as root since you're mounting drives) looks like:
```
# m h  dom mon dow   command
05 00 * * *    /usr/local/bin/backup.sh

```

Good luck! I'm sure there's plenty of other ways to skin this proverbial cat!
Scott

---

### Post by dewman0012 on 2008-06-24
Scott,

Thanks for the reply. After doing some research and consulting a friend, I went with sbackup to get the files backed up to an External HD. However, to insure I get a backup of my database, we wrote a script to back that up as a .gz file that will be picked up by sbackup. Since those are scheduled tasks, it should solve my problem.

---

