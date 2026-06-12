---
title: "How do you do your rsync backups?"
date: 2009-06-27
forum: The Cafe
---

### Post by learningcurb on 2009-06-27
I ran across a very interesting link that provided some interesting tips on rsync backups:

[http://www.halfgaar.net/backing-up-unix](http://www.halfgaar.net/backing-up-unix)

Among the more interesting switches are:

--archive --sparse --numeric-ids --hard-links --delete --delete-excluded --delete-after

---

### Post by beercz on 2009-06-27
[http://rsnapshot.org](http://rsnapshot.org)

I run rsnaphot from a cron job on my server daily to back up my laptop.  Uses rsync over ssh (with keys).

Been doing this for ages now - runs beautifully - never lets me down.

---

### Post by drumsticks on 2009-06-28
> **beercz said:**
> [http://rsnapshot.org](http://rsnapshot.org)

I run rsnaphot from a cron job on my server daily to back up my laptop.  Uses rsync over ssh (with keys).

Been doing this for ages now - runs beautifully - never lets me down.

+1.

I rsnapshot daily (hourly is overkill for me) to another partition on the same hard drive (laptop), then occasionally (every week or two), I rsync the entire rsnapshot backups to an external hard drive.

---

### Post by ghindo on 2009-06-28
I use rsync to back up files from my laptop to my server with Grsync.

---

