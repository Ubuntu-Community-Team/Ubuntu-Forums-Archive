---
title: "incremental or differential changes"
date: 2011-10-19
forum: Server Platforms
---

### Post by albertramsbottom on 2011-10-19
Hi

Bit of a newbie with a rather difficult task to sort out.

I have a multi-server environment running a well know web app thats recently has become a little shaky.  Because of this I have been asked to create a backup mirror of it in our newly purchased Sans blade using VM.

Everything is fine and its up and running.  The only issue I have is keeping the mirror up to date.  It doesn't have to be an exact copy of the live system only maybe a few hours difference.

Now the data folder associated with this app is 270GB and therefore cannot be moved quickly from one NFS share to another (its the NFS share that's the issue)

So I was wondering if there is a Ubuntu method of checking differences between folders on different servers and copying the changes?

Rdiff seems to ring a bell

So any help would be great
Albert:popcorn:

---

### Post by vasile002 on 2011-10-19
you can use lsyncd, it will automatically detect the changes and transfer using rsync only those

---

### Post by Jonathan L on 2011-10-19
> **vasile002 said:**
> you can use lsyncd, it will automatically detect the changes and transfer using rsync only those

Hi

Regardless of how you sync your data, I'd recommend you make snapshots and sync from there.  Then you know that you have a consistent state to be syncing from, which can avoid a lot of problems.  You don't say what applications you're running: you might consider doing databases differently from other files.  And even when you get it all working to your satisfaction, I'd recommend you don't forget those occasional full backups !

[http://manpages.ubuntu.com/manpages/lucid/man8/xfs_freeze.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/xfs_freeze.8.html)

I've had good results syncing with rsync.

Hope that's of some use.

Kind regards,
Jonathan.

---

### Post by albertramsbottom on 2011-10-19
Thanks a lot folks

It is Moodle and uses Mysql.  This is only for dire issues when i am on holiday so it isnt to much of a problem that the data might might be a few hours older than the live servers

Albert

---

