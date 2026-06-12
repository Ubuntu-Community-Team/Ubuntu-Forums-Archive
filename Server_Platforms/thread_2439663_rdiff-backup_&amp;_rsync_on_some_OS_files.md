---
title: "rdiff-backup &amp; rsync on some OS files"
date: 2020-03-30
forum: Server Platforms
---

### Post by aljames2 on 2020-03-30
I feel I should know this and may kick myself for not seeing it already.

Internals look like this:  
```
Sata SSD (Ubuntu OS) ----> HDD-1 (rdiff-backup of SSD /home, /etc, etc.) ----> HDD-2 (rsync backup of HDD-1)
```

Ubuntu server runs on the SSD.  I use LVM snapshots & rdiff-backup to backup daily /home, /etc, /usr/local to my HDD-1.  Then I make a rsync backup of HDD-1 on HDD-2.

Question: I understand rdiff-backup is better at backing up OS files & versioning.  I have read that rsync is not good for this because of the linking & metadata.  Should I instead be using dd to make a mirror of HDD-1 on HDD-2 to better capture the permissions & other metadata?  I do use rsync for data backups but not sure if I am messing up by using it to backup /home, /etc, usr/local on this 2nd (redundant) HDD-2.

---

### Post by TheFu on 2020-03-30
Nope.  The rsync of the rdiff-backup area(s) will capture all the data, versions, and metadata you need ... assuming you use something like:
```
sudo ionice rsync -avz  $EXCLUDES    --delete     /1st-HDD/$HOSTNAME/      /2nd-HDD/$HOSTNAME/
```
Running as root matters, but only slightly.  Doesn't really matter which variant of --delete you use.  There are a few options.  --delete-after would be the safest, but uses the most storage.  --delete-before is the least safe, but uses the least storage for when the target is tight.

But perhaps you want to enable LUKS encryption for the disks or perhaps use a backup server over the network?  

rsync behaves differently when it is locally attached compared to going over a network.  Over a network, the librsync magic happens, unlike when it is used locally. There are rsync options which can force the network block comparisons to be used for local rsync tasks. I always have to hunt those down.  rdiff-backup uses librsync with that comparison option always AND it retains the block checksum between runs, so it is much faster than straight rsync during comparisons.

The rsync manpage is a beast.  Bet you learn something new.  I always do, every time I open it up.

---

### Post by aljames2 on 2020-03-31
Great thanks!!  No joke, the manpage is a college course :)

---

### Post by aljames2 on 2020-04-06
A few rsync options are confusing me -AX.  -AX preserves ACLs, permissions, and extended attributes.

-avz works when pulling or pushing from the client machine:
```
rsync -avz --delete user@server:/home/ /home/ --dry-run
rsync -avz --delete /home/ user@server:/home/ -dry-run
```

But if I try to use the -AX options to preserve permissions, I run in to permission denied issues when I try to push to the server.  I know I shouldn't push and better to pull but I haven't set up the ssh keys in the other direction yet.
```
rsync -aAXvz --delete /home/ user@server:/home/ --dry-run
```

Is -AX necessary as I don't see it being used in many examples?

In my examples here I use /home/ and would always pull when backing up, probably a bad example for what I'm actually doing.  I am working on editing some scripts and document files saved in a small working directory and I am trying to push changes back to the server to keep the most current version on the server.  It's sometimes easier to push these small changes but I should do it better.  I digress

---

