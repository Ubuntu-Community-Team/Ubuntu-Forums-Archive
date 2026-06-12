---
title: "Cron Job: How to copy to a windows share?"
date: 2009-05-04
forum: Server Platforms
---

### Post by xanimal on 2009-05-04
I am working on fine tuning my backup script so that it copies the backup files to two different locations as a cron job. 

Location #1 - External USB 1 TB Backup Drive (/dev/sdb1)
Location #2 - Windows Shared Folder

Here is the script that I have created. I can tell that the scrip it running, the backup file is created, however it is not copying over to either one of the locations. Can someone point me in the right direction? Running Ubuntu Server 8.04LTS

> #!/bin/bash

echo "Mount External 1TB Drive"
ntfs-3g /dev/sdb1 /mnt/1tb

#Set Variables
backupdir=/home/
filename="Homes-$(date '+%F-%H%M').tar.gz"

echo "Creating a backup file"
#Make a tar file
cd /tmp/
tar -cvzf "$filename" "$backupdir"

echo "Move backup file to 1TB"
cp "$filename" /mnt/1tb/Homes/

echo "Mount Temp Folder on Server2"
mount -t cifs -o user=user%passwd //192.168.1.221/Temp /mnt/temp

echo "Copy Backup to Server2 for Secondary Backup"
cp "$filename" /mnt/temp/

echo "Unmount Server2 - Temp"
umount /mnt/temp

echo "Unmount QB Share"
umount /mnt/1tb

echo "All Done."

---

### Post by smileypaul on 2009-05-07
Could be a permissions problem?

What happens when you run the script manually?

---

### Post by xanimal on 2009-05-07
If I run it as a regular user it stops at the mounting part. If I run it as root, it runs just fine and copies the harddrives like it supposed to.

---

### Post by SciFi-Bob on 2009-05-07
I would suggest that you target the "echo" lines to a log file in the /tmp directory while testing.
That way it is easy to see where the script is failing.

Instead of 

  echo "Mount Temp Folder on Server2"

you could use 

  echo "Mount Temp Folder on Server2" >> /tmp/backup.log

Any user has write access to /tmp, so that should not be any problem.

Also, since the script works running as root, are you sure it runs as root in cron?
If you have added a line to crontab, remember to include a username before the script path. And if the script need to run as root, then this username needs to be "root" (without quotes).

If you need to run mount as user, then you need the "user" keyword in the options column in fstab.

For example, instead of "default", you would write "user".
That means that users are allowed to mount, but, of course, the user that is mounting must also have access to the mounted folder

---

### Post by mojorising on 2009-05-07
xanimal, silly question: Why not just put this script in root's crontab? 

Another simple option is to only have the mounting of the drives in root's crontab and then have the unprivileged user run it's back-up scripts. 

You can have the user perform actions as another user (root performing the mount/umount, in this case) but I can't remember off the top of my head how to do that right know. There's quite a few articles on that though found via Google. 


Mike

---

### Post by xanimal on 2009-05-07
Hmm. I'll have to do some reading up on Crontab. Thanks for the help guys. I'll post back and let you know what I find out.

---

### Post by xanimal on 2009-05-08
> **mojorising said:**
> xanimal, silly question: Why not just put this script in root's crontab? 

Another simple option is to only have the mounting of the drives in root's crontab and then have the unprivileged user run it's back-up scripts. 

You can have the user perform actions as another user (root performing the mount/umount, in this case) but I can't remember off the top of my head how to do that right know. There's quite a few articles on that though found via Google. 


Mike

Mike,
By adding it to root's crontab you are meaning editing /etc/crontab?

For my nightly backups it would be:
0 0 * * * root /home/user/homebackupscript

For Weekly:
0 0 * * 0 root /home/user/homebackupscript

That look right?

---

### Post by xanimal on 2009-05-13
Ok added the job to the Crontab. Still doesnt copy to the external. Do I need to add something to the FSTAB for the external? what about the network map?

---

### Post by diablo2nd on 2010-07-19
Did this ever get solved? i have an identical issue except using platform ubuntu 10.04 desktop backup script executes tar command that fails partway through, also my smbclient line that copys from windows machines is failing.

The script runs fine when executed. Is there a time limit on executing cron jobs

---

### Post by kgatan on 2010-07-20
The problem of the original post is mounting as a non-superuser.
Non superusers can only mount filesystems that have been defined in fstab with the "user" option.

So if i understood the man for mount you should in your case define the mount in fstab with the user option and then u can mount and umount the mount point with any user.

But im a rookie so beware :)

> The non-superuser mounts.
                     Normally,  only  the  superuser  can  mount file systems.
                     However, when fstab contains the user option on  a  line,
                     anybody can mount the corresponding system.

                     Thus, given a line

                            /dev/cdrom  /cd  iso9660  ro,user,noauto,unhide

                     any  user  can mount the iso9660 file system found on his
                     CDROM using the command

                            mount /dev/cdrom

                     or

                            mount /cd

                     For more details,  see  fstab(5).   Only  the  user  that
                     mounted  a  filesystem can unmount it again.  If any user
                     should be able to unmount, then use users instead of user
                     in  the  fstab  line.  The owner option is similar to the
                     user option, with the restriction that the user  must  be
                     the  owner  of  the special file. This may be useful e.g.
                     for /dev/fd if a login  script  makes  the  console  user
                     owner  of this device.  The group option is similar, with
                     the restriction that the user must be member of the group
                     of the special file.

---

