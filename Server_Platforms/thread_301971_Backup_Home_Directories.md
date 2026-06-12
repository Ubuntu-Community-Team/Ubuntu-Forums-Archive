---
title: "Backup Home Directories"
date: 2006-11-17
forum: Server Platforms
---

### Post by scott_ttocs46 on 2006-11-17
Hi all,
   Does anyone know of/how to create a script/application that will do something to this affect:

For each home directory on mainserver, make a backup at a set time on backupserver in /backup/mainserver/homes.

Thanks,
Scott

---

### Post by breezyfox on 2006-11-18
> **scott_ttocs46 said:**
> Hi all,
   Does anyone know of/how to create a script/application that will do something to this affect:

For each home directory on mainserver, make a backup at a set time on backupserver in /backup/mainserver/homes.

Thanks,
Scott
Hi
following link may help you. Just try
[http://www.desktoplinux.com/articles/AT2280165098.html](http://www.desktoplinux.com/articles/AT2280165098.html)


bz

---

### Post by scott_ttocs46 on 2006-11-18
thanks. very useful.

---

### Post by scott_ttocs46 on 2006-11-18
So, a script something like this?

mount -t samba backupserver.lan/mainserver /mnt/backupserver
tar tzf Mainserver.Homes.Backup.tar.gz /home/*
mv Mainserver.Homes.Backup.tar.gz /mnt/backupserver


( I am not sure about how to mount a samba share. Particularly, the -t tag. Also I am not certain if the wildcard will work in this.)

How do you shedule something like this? With Cron?

---

### Post by MJN on 2006-11-19
Mount the Samba share with:

[B]mount -t smbfs -o username=<username>,password=<password> //<IP of server>/<share name> <local mount point>

[/B](Hint for the <share name>: run **smbclient -L <IP of server> -N**)

I personally would (and do) use **rsync**[1] - the home directories here are regularly each in excess of 10GB (photos etc) yet on a day-to-day basis they change relatively little (matter of MB's) - rsync only transmits the changed files and not the whole lot so easy on the bandwidth (crucial given I also back them up offsite so only the first time I ran it did it have to trawl through the multi-GB upload).

Mathew

[1] Something like **rsync -avi --delete --stats /home/ /mnt/backupserver/ > BACKUP-log** (-a: archive (preserves permissions, recurse etc), -v: verbose output (good for the log), -i: itemise changes (good for the log), --delete: delete files on the destination that don't exist on the source (i.e. files you're removed), --stats: give file transfer stats (good for the log), > BACKUP-log: store all output (log of backup))

---

### Post by scott_ttocs46 on 2006-11-27
> **MJN said:**
> Mount the Samba share with:

[B]mount -t smbfs -o username=<username>,password=<password> //<IP of server>/<share name> <local mount point>

[/B](Hint for the <share name>: run **smbclient -L <IP of server> -N**)

I personally would (and do) use **rsync**[1] - the home directories here are regularly each in excess of 10GB (photos etc) yet on a day-to-day basis they change relatively little (matter of MB's) - rsync only transmits the changed files and not the whole lot so easy on the bandwidth (crucial given I also back them up offsite so only the first time I ran it did it have to trawl through the multi-GB upload).

Mathew

[1] Something like **rsync -avi --delete --stats /home/ /mnt/backupserver/ > BACKUP-log** (-a: archive (preserves permissions, recurse etc), -v: verbose output (good for the log), -i: itemise changes (good for the log), --delete: delete files on the destination that don't exist on the source (i.e. files you're removed), --stats: give file transfer stats (good for the log), > BACKUP-log: store all output (log of backup))
This mount command doesn't work:


administrator@solar:~$ sudo mount -t smbfs -o username=solar,password=***** //192.168.0.15/solar /mnt/mfs
mount: wrong fs type, bad option, bad superblock on 192.168.0.15/solar,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


dmesg | tail yields:

...
[43797867.560000] smb_fill_super: missing data argument
[43797933.680000] smbfs: mount_data version 1919251317 is not supported

---

### Post by scott_ttocs46 on 2006-11-27
"
If the output includes the following text then you're missing the smbfs package:

smbfs: mount_data version 1919251317 is not supported
"

[http://www.debian-administration.org/articles/165](http://www.debian-administration.org/articles/165)

Did:

sudo apt-get install smbfs

It seems to work.

---

### Post by scott_ttocs46 on 2006-11-27
So far, this is my script:

sudo mount -t smbfs -o username=solar,password=***** //192.168.0.15/solar /mnt/mfs
tar -c -f /mnt/mfs/backup__home_administrator.tar -v /home/administrator/
sudo umount /mnt/mfs

I need to be able to cron it for every twelve hours.

But it needs to backup each users home directory.

It also needs to change the tar file name to include the home directory name and timestamp of tarring so I can sort them out.

Any ideas?

---

