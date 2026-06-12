---
title: "Creating an rsync backup how to"
date: 2007-07-10
forum: The Cafe
---

### Post by Ozor Mox on 2007-07-10
When I searched for a backup solution, what I mostly found was a load of GUI tools that people kept saying weren't working, and some threads on rsync that listed a load of different ways to use it. The rsync entry in the Ubuntu community documentation isn't very good. Now I have some experience using it, I thought it might be useful to create one of those how to guides I've seen around for a simple rsync backup to a mounted drive for a home user. Nothing fancy, just the useful options for a standard backup.

Would this be helpful? Is there a special format or any other rules to creating these guides?

---

### Post by qpieus on 2007-07-10
Well, this is the first sticky in the Tutorials & Tips subforum. It has some guidance on making a how-to:

[http://ubuntuforums.org/showthread.php?t=316820]("http://ubuntuforums.org/showthread.php?t=316820")

As far as will it be useful? I think if you can make a nice clear guide that people can use to perform a similar backup task, then it would be useful.

---

### Post by jynyl on 2007-07-22
Any progress on this?  Sounds just what I am searching for right now.

---

### Post by vanadium on 2007-07-22
```

rsync -av --del <source> <destination>

```

is really all you need to mirror one directory tree to another place. Experiment first without the --del switch. --dell will delete files in destination that do not exist (anymore) in the source. If you swapped source and destination ...

---

### Post by Ozor Mox on 2007-07-25
Vanadium, I know that command now, thanks for telling me in the other thread where I was asking about rsync!

I just thought it might be helpful to have that documented somewhere, plus I've learnt some other useful commands and some things about filesystems that might be helpful for others trying to create a simple backup on a mounted external hard drive.

---

### Post by John.Michael.Kane on 2007-07-25
These may give you some more ideas for your howto.

[Easy Automated Snapshot-Style Backups with Linux and Rsync]("http://www.mikerubel.org/computers/rsync_snapshots/")

[Backups using rsync]("http://www.sanitarium.net/golug/rsync_backups.html")

[Rsync mirroring howto and FAQ]("http://sunsite.dk/info/guides/rsync/rsync-mirroring.html")

[basic rsync]("http://transamrit.net/docs/rsync/")

[Using-rsync]("http://everythinglinux.org/rsync/")

[Rsync tutorial]("http://www.fredshack.com/docs/rsync.html")

---

