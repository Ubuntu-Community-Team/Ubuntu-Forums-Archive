---
title: "Problems with Samba and FAT32 Permissions"
date: 2009-01-06
forum: Server Platforms
---

### Post by RobertSOakes on 2009-01-06
Dear Community Members,

While I've lurked a bit and tried to learn as much as I can about Linux and Ubuntu, I've come up against a problem which I don't know how to solve.  If anyone has any ideas on what to do I would be extremely appreciative.

For the past year or so, I have used an old computer running Ubuntu 7.10 (and then 8.04) as a file server.  There are two, one terabyte USB drives attached, one which is used for a network file share and the other as a backup.  I am having trouble with the backup drive.

The other computers in the house run Windows Vista and I have had no difficulties in accessing the drive or using the built-in Windows Vista backup.  That is, until about a month ago.

One of the drives was starting to act odd, I therefore bought a new drive and transferred the data.  I also took the time to upgrade to Ubuntu server 8.10.  Since then, while the drive which serves as a store (accessed over samba) works great, I am getting very odd behavior from the backup drive.  Specifically:
[LIST=1]
[*]I can access the drive and copy files from any computer without difficulty.
[*]I am not however, able to back up the computers to the drive.  It quits with Windows Error 0x80070003.
[/LIST]

I finally sat down and spent some time tracking things through to determine what the problem is.  It looks like a permissions issue.  The backup will begin correctly and load the first .zip file in the proper directory, it then quits because it does not have appropriate read/write permissions to the path.

If I go to the backup directory and run ls -l, this is what the output shows:

drwx------  4 roakes roakes 16384

In contrast, the previously created backups have the following permissions and owners:

drwxrwxrwx  4 roakes roakes 16384

I do not understand why there is a difference.  The drive is formatted as FAT32 and has been mounted so that all files and folders are public.  The fstab entry looks like this:

/dev/sdc1 /media/backup vfat users,defaults,umask=000 0 0

Further, I have tried to set the samaba permissions so that all files and folders are public as well.  Here is the /etc/samba/smb.conf entry:

[PC-Backup]
comment = Public Backup Folder
path = media/backup/PC-Backup
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force directroy mode = 0777
force create mode = 0777

Since all of the permissions are set to public rwx on both the drive as well as in samba, I am not sure how the Windows Vista Backup is creating files and folders with limited permissions.  This particularly confounds me since the drive is formatted as FAT32 and I didn't think it was possible to create permissions different from the mount permissions.

If anyone has any insight about how I might fix this problem and can resume backing up my computers, I would be extremely grateful.

Best Regards,

Rob Oakes
[http://www.oak-tree.us/blog](http://www.oak-tree.us/blog)

---

### Post by jms1989 on 2009-02-01
your path varible seems odd for your samba entry. You forgot the leading forward slash /

other than that, it looks like it should work.

---

