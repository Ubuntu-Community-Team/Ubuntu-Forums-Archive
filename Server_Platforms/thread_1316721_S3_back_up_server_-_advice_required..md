---
title: "S3 back up server - advice required."
date: 2009-11-06
forum: Server Platforms
---

### Post by Wildscot on 2009-11-06
Hi folks,

I've built a server for a small office from an old P3 junker running 9.10 headless and administered by SSH. It's intended to host an intranet/wiki and also to work as a backup server.
The plan is that it will run unattended and back up a handful of windows shares locally to disk (Raid 1), daily and then copy this over to an Amazon S3 bucket weekly.

So far I am quite happy with the server set up, RAID is fine, I have my windows shares mounted and my Amazon S3 bucket mounted etc. I still have to set up my rsync and cron jobs etc, but I'm happy to research that, it's more a question of method.

I have 3 mounts/directories in play:
/mnt/shares => where I have the Windows shares mounted.
/documents => the local mirror of the windows shares.
/mnt/s3bucket => my mounted Amazon S3 bucket

What I had planned was a regular cron job to rsync /mnt/shares to /documents then another less regular to rsync to /mnt/s3bucket.

However as I was about to set this up I realised that if I had a problem with the network or one of the Windows machines was down it would find nothing on /mnt/shares/machine1 and would copy this across to /documents/machine1 wiping out the existing backup - correct?

How could I have it check that the share was mounted before carrying out the rsync job?

[SIZE="1"]NB: I realise I can set up 'push' backups from the windows machines with SyncBack or similar but I'd rather it was self contained. I'd also like to learn.[/SIZE]

Cheers,

Wildscot

---

### Post by awclemen on 2009-11-06
The mount command with no arguments will show all filesystems that are mounted. So, you could issue mount on its own, grep the output for say, "/mnt/shares/machine1 ", and then count the number of lines in the output. 0 means it's not mounted, 1 means it is.

---

### Post by Wildscot on 2009-11-06
Ah, interesting. Thanks.
Any thoughts how would I integrate that into a script so it would check the share was mounted and if not it would exit the script? I'm hoping that this machine can be left largely to it's own devices once it's been set up.
I'm on a pretty steep learning curve here!

---

### Post by awclemen on 2009-11-06
```

#!/bin/bash
lineCount=`mount | grep '/mnt/shares/machine1 ' | wc -l`
if [ $lineCount == 1 ]
then echo "it's there"
else echo "it's not there"
fi


```

---

### Post by Thirtysixway on 2009-11-06
Is there a way to rename folders or organize it?  This way you could have /2009/11/01/machine1 etc in both your local and amazon backups.

The positive is that you have to-the-day backups, and the ability to restore old files.

The negative is that (unless you did some fancy scripting..) you may end up with hundreds of copies of files that never change from day to day or month to month wasting space on your S3 service.

---

