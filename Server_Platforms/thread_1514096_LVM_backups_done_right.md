---
title: "LVM backups done right"
date: 2010-06-20
forum: Server Platforms
---

### Post by denarced on 2010-06-20
I have 4 HDDs, 2x2TB and 2x1TB. The setup at the moment is:
/boot
LVM
[INDENT]LVM Volume group lvmvolume[/INDENT]
[INDENT][INDENT]LVM logical volume /home[/INDENT][/INDENT]
[INDENT][INDENT]LVM logical volume /swap[/INDENT][/INDENT]
[INDENT][INDENT]LVM logical volume /[/INDENT][/INDENT]
This resides on a one 2TB HDD and on one 1TB HDD.
So the backup disks will be identical, 1x2TB+1x1TB.
Now I'll be using snapshots for making the backups,
but the question then becomes, how do I format the
backup disks and how do I execute the backup? The
endgame is to have a backup from which it is quite
simple to get a system up and running. In other
words, I'd like to get close to a situation which
would result if I just make a binary copy of the 
two disks to the other two disks (the backup disks).
That could be achieved by using something like:
```

dd if=/dev/sda1 of=/dev/sdc1
dd if=/dev/sdb1 of=/dev/sdd1

```
I'm not using that since it's not a very slow and 
inconvenient way to go.

Help appreciated

---

### Post by weirdtalk on 2010-06-20
You might be interested in this:
[http://backintime.le-web.org/](http://backintime.le-web.org/)

I was not satisfied with backup tools like timevault and flyback so had been using rsync to make hard-linked snapshots. I was actually in the process of writing a program to automate smart snapshot removal when I found this. It's very easy to setup. It uses cron to do snapshots so it is "set and forget" easy. It also is "copy & paste" restoreable in an emergency. (Really I thing easy restore is the MOST important part of any backup solution)

---

### Post by denarced on 2010-06-20
> **weirdtalk said:**
> You might be interested in this:
[http://backintime.le-web.org/](http://backintime.le-web.org/)

I was not satisfied with backup tools like timevault and flyback so had been using rsync to make hard-linked snapshots. I was actually in the process of writing a program to automate smart snapshot removal when I found this. It's very easy to setup. It uses cron to do snapshots so it is "set and forget" easy. It also is "copy & paste" restoreable in an emergency. (Really I thing easy restore is the MOST important part of any backup solution)

back in time seems like a nice tool but I'm thinking I wanna go manual with this one, for now. This is one of those operations that 'cause the control freak in my head to really take charge :).

I've been using rsync too but never for scenarios like this. What, I just take the information on partition sizes and LVM-info and re-create a duplicate structure on the other disks and that's it. No problems ?

---

### Post by weirdtalk on 2010-06-20
Well if you want you could use dd to make your backup the first time (slow, like all first time backups) then use rsync to update it quickly. This doesn't do the snapshot part but it's still a good system.

---

### Post by psusi on 2010-06-20
If you are going to use rsync there is no reason to dd the first time.  If you have a complete set of duplicate disks, then yes, you can use rsync to keep two full copies of your data that you can use to quickly replace the first set of disks with the second.  Just make a snapshot, mount it, then use rsync to copy it to the backup volume.

---

