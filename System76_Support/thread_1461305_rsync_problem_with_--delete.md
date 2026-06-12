---
title: "rsync: problem with --delete"
date: 2010-04-24
forum: System76 Support
---

### Post by WDYSUN on 2010-04-24
Hello dears,

I am trying to use rsync as a backup tool I am using this command

```

rsync -a -v --progress --delete   home   external_hd

```

the problem is that while the command changes update files on the destination, it doesn't delete the files removed from source, so everything removed from destination still appears on the destination.

I thought the option --delete should have done the job. Could somebody  help me?

Best Wishes
Pietro

---

### Post by phyzome on 2010-04-24
Does rsync complain about "not being able to stat all files" or something like that? If so, it will not go into the delete phase. Try piping the output to a log file, like so:

rsync blah blah blah 2>&1 | tee /tmp/backup.log

The most likely culprit is .gvfs in your home directory. Add the option --exclude=.gvfs, and you should be good. (This is a known problem with .gvfs -- even root can't stat it.)

(I should also mention that this is probably not the correct forum for your question, since it isn't System76-specific.)

---

### Post by WDYSUN on 2010-04-24
Hello,

> **phyzome said:**
> 
...
The most likely culprit is .gvfs in your home directory. Add the option --exclude=.gvfs, and you should be good. (This is a known problem with .gvfs -- even root can't stat it.)



I tried --exclude=.gvfs but the problem is still there, I also put the option 

 --log-file=/media/BKDISK/rsync_log

but I don't get any log file at the end. Anyway that's the output when there no changes on the source directory:

```

rsync: opendir "/home/pietro/.local/share/Trash/expunged/45063646/cdrtools-2.01.01/libvms" failed: Permission denied (13)
rsync: opendir "/media/EHD1/tribeca-home-pietro/.local/share/Trash/expunged/45063646/cdrtools-2.01.01/libvms" failed: Permission denied (13)
IO error encountered -- skipping file deletion
sent 2177604 bytes  received 4874 bytes  4364956.00 bytes/sec
total size is 203335370473  speedup is 93167.20
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1057) [sender=3.0.6]

```

I hope this can be solved

Pietro

---

### Post by phyzome on 2010-04-24
> **WDYSUN said:**
> ```
IO error encountered -- skipping file deletion
```

Well, there's your problem. Look around in the output more:

> **WDYSUN said:**
> ```
rsync: opendir "/home/pietro/.local/share/Trash/expunged/45063646/cdrtools-2.01.01/libvms" failed: Permission denied (13)
```

Well, try accessing that file! Can you open it? Try reading it as root instead.

I generally do my backups as root, because I occasionally end up with files in my home dir that were written by root.

---

### Post by WDYSUN on 2010-04-24
Ok now it works! Thanks a lot! I didn't know that the home dir could contain root owned file/dir.

By the way it does not save the log file.

Best Wishes
Pietro

---

### Post by Jamal88 on 2012-10-11
What I understand after lot of debugging for this issue...If rsync has a read error at source(e.g due to permission) it cannot determine whether to delete the file in destination or not...and it skip the -delete action for all other files for saftey reason.

Make sure all files has read permission at source.

---

