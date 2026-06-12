---
title: "Backups"
date: 2012-03-28
forum: Server Platforms
---

### Post by michellez on 2012-03-28
Hi All

I'm looking to do a back up. My objectives are:

- Backup several Windows machines (just mount the shares?) and Linux machines
- Backup locally to specific server and and also replicate off site (I have a Linux box remotely to do this to)
- Keep the last month worth of nightly back ups
- Keep a back up once a month, say the 1st of each month for a few years

Now in the past I've just backed up a single machine to a single destination with rdiff-backup and just left it with no retention etc. I'm dealing with a lot more data with this though so I'm going to have to manage it better. Upon searching to see if this can do the 'keep nightlies for a month and keep the back up from on the 1st of each month as well for 2 years' I found rsnapshot.

rdiff-backup:
- Has the option to run --remove-older-than which is good except I want to keep the 1st of each months back up as well

rsnapshot:
- Has the retain option but the same issue as rdiff-backup basically

Am I correct in thinking that in both cases I would have to run 2 backups? A nightly and a monthly one and set the retain/remove-older-than appropriately? Annoying as surely it means a lot more data transfer and storage when the data is effectively already there?

I'm thinking the off site copy can just use rsync or something between the 2 servers to just keep a replicated copy of the backup destination.

Any tips, ideas, or something I'm missing please? :)

Thanks
Shell

---

### Post by HermanAB on 2012-03-28
> I'm thinking the off site copy can just use rsync or something between the 2 servers to just keep a replicated copy of the backup destination.
Yes.

---

### Post by koenn on 2012-03-28
> Am I correct in thinking that in both cases I would have to run 2 backups? A nightly and a monthly one and set the retain/remove-older-than appropriately? Annoying as surely it means a lot more data transfer and storage when the data is effectively already there?

If you want to *keep* monthlies, you're going to use more storage anyway so all you have to worry about is data *transfer*; in which case you could probably just have a 2nd job that just moves/copies last months backup out of the way on a montly basis. 


If it turns out you need two jobs, a nighly and a monthly, you might be able to save on transfer time by preseeding the destination dir of your monthly with data you've already backed up; that would be a local copy on your backup storage rather than a transfer over network, so possibly faster and without network load. 



I could be missing something as I haven't used rsnapshot or rdiff-backup; just rsync with --backup option and some trickery to rotate the --backup-dir.
That may be a better solution, since eg something like
```
rsync  --backup --backup-dir=/dest/$var  /src  /dest/current 
```
where $var is something that varies through a range; for daily backups it could be the day-of-month from a 'date' command, or something similar

this will gave you (nightly) increments in /dest/$var, and 1 full and up to date copy in /dest/current  (for a restore, you'd restore 'current', and optionally go back in time by copying a $var over the (restored) current)

by renaming/moving/copying 'current' on a monthly schedule, you can avoid them being overwritten; that's how you keep the monthlies then

these are all  full copies that eventually will be 1 or 2 years old; 
this means you'll need a backup location that has 12-24x the storage capacity of the volumes you're backing up.

you may want to ask yourself in what sort of circumstances a restore to a situation of 2 years ago would be a solution. I can't think of any. 
If you're thinking archiving, keep that separate from your backups, it's a different problem and requires a different approach.

If you're thinking the 2 years worth of monthlies should be incremental, rather than full, you may indeed have to run two separate jobs with separate retention periods, and you can still ask your self what sort of problem you are going to fix by restoring data from 2 years ago.

---

### Post by michellez on 2012-03-29
Thanks Koenn, lots to think about there.

Backups of a few years ago are really for things like our databases for accounts if they need to look back at something from a previous year end, for example.

It looks like I may have to go with 2 sets of data. Just seems a bit of a waste when the data is already there once. Would be nice if rdiff-backup could just use the same "base" directory to create 2 different sets of diffs - monthly/weekly. Maybe it can?

Thanks

---

