---
title: "Automate daily backups to two alternating external USB hard disks"
date: 2014-03-03
forum: Server Platforms
---

### Post by lepukowsky on 2014-03-03
I setup a Samba server for a small family business. The owner would like to have automatic backups to 2 usb drives such that she can take one home each night while cron runs a backup on the other, then swap them when she gets back the next morning. 

My script to do automatic backups was simply making sure /dev/sdb1 was mounted to /mnt/backups and then doing a recursive copy. However sometimes the drives get mapped to other letters such as sdc1 or sdd1, so the copy never happens.

What would be the appropriate way to script a backup procedure for this setup since I can't guarantee usb drives are always going to be mapped to the same letters? Would using UUID's on the devices help?  What commands can I use to check if a device is mounted correctly, and if not, attempt to remount the other drive before attempting a backup?

Any help would be greatly appreciated!

---

### Post by TheFu on 2014-03-03
You should use either UUIDs or LABELS to mount the devices.  That will put them into the same location at every mount.
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions) - use the system-wide method and please use EXT4 as the target file system format. None Linux file systems don't retain critical meta-information.  Definitely do not use NTFS to backup Linux.

A recursive copy is not very efficient. There are many better ways to do backups - have been for years.  If the backup moves, it MUST BE ENCRYPTED. That means **duplicity** is probably the best answer.  I don't use it, choosing **rdiff-backup** for our needs.  rsync can be made to backup to differential backup storage too.  Highly efficient - having 120 days of backups available feels good and hardly requires any extra storage for most situations - 20% more than a mirror does (copy) for all those extra backups. Seems like a no-brainer to me.

I've written about using rdiff-backup here numerous times. Even posted a relatively simple script and helped another poster get it working. Backups are a well-covered topic on these forums.

---

### Post by lepukowsky on 2014-03-03
Thank you for the response. Reading the link now.

Just curious, why is it bad to backup to NTFS? The owner purchaed 2 usb drives that are already NTFS formatted, and although I could reformat them to ext4,she wouldn't be able to view the files on a Windows PC when she takes the drives home.

---

### Post by oldfred on 2014-03-03
If just data or just /home, NTFS probably is ok.

It just is that you lose all ownership & permissions and will have to reset them if you restore data to a Linux file system. Resetting only data's ownership & permissions is relatively easy, but you cannot reset system files.

---

### Post by TheFu on 2014-03-03
> **oldfred said:**
> If just data or just /home, NTFS probably is ok.

It just is that you lose all ownership & permissions and will have to reset them if you restore data to a Linux file system. Resetting only data's ownership & permissions is relatively easy, but you cannot reset system files.

This is part of it, but it is also about doing backups better - not just a "copy". A mirror/copy has all sorts of failure modes even for data-only backups that make it less desireable. Modern backup tools support file versioning, so a corrupted file that is not noticed for a week can still be recovered.

---

### Post by lepukowsky on 2014-03-03
That's a good point about the file permissions from ext4 to ntfs. Unfortunately the customer gets what the customer wants! I will just cross my fingers and hope the backups are merely for home use instead of restore points for the time being. I could probably set up an rsync script to copy the files to my personal server in case we need to do an actual backup that preserves permissions. [http://stackoverflow.com/questions/3450250/is-it-possible-to-create-a-script-to-save-and-restore-permissions]("http://stackoverflow.com/questions/3450250/is-it-possible-to-create-a-script-to-save-and-restore-permissions") offers some other methods I could try as well.

One last question-- it seems like using UUID's is the way to go, but since these drives are going to plugged in/out every other day, what would be the proper way to test if they are mounted? Thanks!

---

### Post by oldfred on 2014-03-03
Some examples:
 Backup to external with check of mounted & email
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
rsync confirmation list:
[http://ubuntuforums.org/showthread.php?t=1692800](http://ubuntuforums.org/showthread.php?t=1692800)
[http://ubuntuforums.org/showthread.php?t=1555647&page=4](http://ubuntuforums.org/showthread.php?t=1555647&page=4)
more scripts:
[http://ubuntuforums.org/showthread.php?t=1319155](http://ubuntuforums.org/showthread.php?t=1319155)

I also have link to the on TheFu did:
      Sample rsync file by TheFu
[http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880](http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880)

---

### Post by TheFu on 2014-03-03
Clearly, you aren't doing system backups then - I'd get the client to sign a risk acceptance letter, so there isn't any confusion.  I've had to do this at a Fortune 50 company.  It makes clear that you are serious and usually they will reconsider their prior choice.  It is also a nice "I warned you" when data loss happens.

I'd use **autofs** and look for a file that I know exists only in the mounted area 1st, then run 'df' looking for the expected mount point 2nd. Don't know if this is the "correct way" - just that it works and doesn't have the "backup" mount point showing up all day long if nobody is using it.

Simple rsync makes a mirror. Please use the rsync methods that leverage hardlinks for versioning ... or use another modern backup tool like duplicity or rdiff-backup. All of these work over ssh for network backups.

Most small businesses don't really have all that much change data daily.  Pulling remote backups over the internet is usually easy and completely secure over rsync+ssh (or 20 other backup tools that use librsync+ssh).  It is just the first backup that takes time.

My email server network backups take just 3 minutes. The other 30 servers here take 1-2 minutes each thanks to the efficiency of rdiff-backup.  Just sayin'.


[http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880](http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880) is not an rsync backup script. It is for rdiff-backup. I don't use rsync for backups - just mirrors.

---

