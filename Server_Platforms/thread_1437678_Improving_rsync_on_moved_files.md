---
title: "Improving rsync on moved files"
date: 2010-03-24
forum: Server Platforms
---

### Post by dargaud on 2010-03-24
Hello all,
ok, this is not a question relevant to ubuntu, if only to backups.
I've long been using *rsync -av --delete /home /backup* to make my backups and it works great. But I was wondering if there are options that allow rsync to work better on moved files.

Let me explain: if I move or rename large files in /home, then the command will delete their previous backups and copy them again to their new location. That's time consuming. There are other backup tools that can guess that they are the same files based on various info (date+size or, more securely but slower, hash number). Are there options in rsync that can do that ?

Note: I'm not really looking for other backup tool suggestions. I use rsync on Linux and robocopy on Windows so that I can script things.

---

### Post by jrssystemsnet on 2010-03-24
Nope.

You can always do a preliminary move command yourself, if you've done something REALLY giant and obnoxious on the other end.  For example, if you renamed /client/machine/reallybigdir to /client/machine/20GBofCrap one day, you might want to go the backups and **mv /backups/reallybigdir /backups/20GBofCrap** before your rsync process runs.

I've considered using **inotify** to set up a process to "replay" rename operations from a client onto the backup before doing scheduled rsync operations, for exactly this reason... but that's only an option if **inotify** is available on the client - ie, if you're backing up a Linux machine, not a Windows machine.

---

### Post by KB1JWQ on 2010-03-24
Doing a replay is time consuming enough that I'd probably just replicate a filesystem in near-realtime. :-)

---

### Post by jrssystemsnet on 2010-03-24
> **KB1JWQ said:**
> Doing a replay is time consuming enough that I'd probably just replicate a filesystem in near-realtime. :-)Uh?  Replaying move operations isn't time-consuming at all.  That's the whole point.

Whereas if you DON'T replay a move operation on the client on the backup, you can end up with a single directory rename (which a replay would accomplish instantaneously and with only a few bytes of traffic moved over any network inbetween client and backup) requiring tens or hundreds of gigabytes of disk writes and traffic.

---

### Post by KB1JWQ on 2010-03-24
I misspoke, my apologies.  Trying to do too many things at once today.

Doing a replay is COMPLEX enough that I'd rather find an alternate solution.  Coming from a Mac world, my solution was this: [http://blog.interlinked.org/tutorials/rsync_time_machine.html](http://blog.interlinked.org/tutorials/rsync_time_machine.html)

Doesn't solve the "I renamed 20 gigs of stuff to another folder" style problems, but my environment rarely sees such things happen.  

I'm from the school of "backups should be fire and forget." :-)

---

### Post by dargaud on 2010-05-10
> I'm from the school of "backups should be fire and forget.
When your computer goes on fire, you figure out that you forgot to do your backup ?

---

