---
title: "rsync errors: link_stat &quot;/no&quot; failed"
date: 2008-10-21
forum: Server Platforms
---

### Post by botfish on 2008-10-21
I've got a bash backup script that pulls my home directory off a remote machine. Occasionally it spits out the following or similar error:

rsync: link_stat "/no" failed: No such file or directory (2)
rsync: link_stat "/user@machine:/home/user" failed: No such file or directory (2)
rsync error: some files could not be transferred (code 23) at main.c(977) [sender=2.6.9]

Unless someone asks I wont post the whole script (200 lines) but below is the rsync command. 

/usr/bin/rsync $VERBOSE $EXCLUDE -a --delete -e "ssh -i $RKEY" $REMOTE_USER@$REMOTE_MACHINE:$REMOTE_SOURCE $LOCAL_TARGET/$BACKUP_TIME

I based the script on [http://www.linux.com/feature/113847?page=2](http://www.linux.com/feature/113847?page=2) but modified it to "pull" rather than "push". It uses the same idea of hard link rotation.

Thanks for any help!

---

### Post by MJN on 2008-10-21
A long shot off the top of my head... try wrapping the source in quotes i.e. $REMOTE_USER@$REMOTE_MACHINE:$REMOTE_SOURCE" as it may be that you have some non-escaped characters (spaces in particular) that are causing the part of the file matching to fail.
 
That said, does it fail at the same point each time? If not, then I suppose it is fair to rule out file naming issues.
 
Is there anything perculiar about the source end? Slow HDD, external USB drive, non-Linux filesystem etc?
 
Mathew

---

### Post by botfish on 2008-10-22
Thanks.

I found one of the file names in my source directory contained a space so I fixed that and also surrounded the source in quotes as you suggested. The problem has not reoccurred after a couple of trials.

Strange thing is that the offending file that I renamed was not mentioned in the rsync error I'm not sure where the "/no" came from.

Both computer are very new and have plenty of capacity so I cant see it being a hardware problem.

---

### Post by MJN on 2008-10-22
There is nothing wrong with having a space in a filename, hence removing them is not really the right solution to your problem! (it merely avoids the symptoms on this occasion, but you can't really on it for good)
 
Try just wrapping the source in quotes - that should then accomodate spaces (and other escapable characters) without you having to manually restrict the allowable character set in your filenames.
 
Mathew

---

