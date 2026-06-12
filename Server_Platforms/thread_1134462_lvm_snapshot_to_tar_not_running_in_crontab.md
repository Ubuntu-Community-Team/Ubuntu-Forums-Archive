---
title: "lvm snapshot to tar not running in crontab"
date: 2009-04-23
forum: Server Platforms
---

### Post by senor_smile on 2009-04-23
I have a 8.04 LTS server being used as a file server.  I have an LVM volume which takes up half of the available storage on the secondary disk(actually 4 disks put into one via LVM).  My goal is to take a snapshot once per day, tar the contents of the disk's snapshot, and then remove the snapshot.  This all works when I run the commands manually.  However, I have entered them into a script to run, and entered the script in crontab.  Here's the script: 

```
umount /media/datasnapshot
lvremove -f /dev/fileserver/datasnapshot

lvcreate -L69G -s -n datasnapshot /dev/fileserver/data
mount /dev/fileserver/datasnapshot /media/datasnapshot

tar -pczf /media/WDC/backups/data$(date +%y.%m.%d).tar.gz /media/datasnapshot

umount /media/datasnapshot
lvremove -f /dev/fileserver/datasnapshot
```

I first unmount and remove the snapshot in case there was an existing snapshot in use by the admin on site.  When I run these commands from the cli all goes well.  When this script ran at 15:00 today, as scheduled, it only produced a tiny 121 byte file.  The files being produced when I run the script manually are 2.8 GB.  In the syslog, the only mention of the script running is: 

```
Apr 23 15:00:01 FileServer /USR/SBIN/CRON[16408]: (root) CMD (/home/allyn/backupscript.sh)
Apr 23 15:15:08 FileServer crontab[16501]: (root) BEGIN EDIT (root)
Apr 23 15:15:10 FileServer crontab[16501]: (root) END EDIT (root)
```

Thanks in advance!
--shaun

---

### Post by doogy2004 on 2009-04-23
what does your crontab entry look like?

---

### Post by senor_smile on 2009-04-24
my crontab contains the following: 

# m h  dom mon dow   command
0 15 * * * /home/allyn/backupscript.sh


the backupscript.sh is the script that contains the entire code for creating the snapshot, tar-ing the contents of the data drive, and removing the snapshot.

---

### Post by senor_smile on 2009-04-27
I have further determined that only parts of my shell script are running.  The snapshot is not being created, but it's going ahead with the tar creation, which explains the tiny tar files with nothing in them.  

So, I have made a simpler shell script to just create a snapshot, and it doesn't work.  

I have the following in a file called snapshot.sh:

```
lvcreate -L69G -s -n datasnapshot /dev/fileserver/data
mount /dev/fileserver/datasnapshot /media/datasnapshot

```

the file has rxwrxwrxw(777) privileges.  The script runs fine, i.e. creates the snapshot correctly, when I run it manually from the command line.  Any ideas what I need to change to get that to run correctly?

---

### Post by senor_smile on 2009-04-27
I have finally solved the problem!!!

After reading ubuntu's wiki on crontab, I found a reference to setting the path.  I added: 

```
PATH=/usr/sbin:/usr/bin:/sbin:/bin
```

and all works as expected now.

---

