---
title: "Multiple simultaneous Rsync jobs slowing system"
date: 2008-12-02
forum: Server Platforms
---

### Post by jreinhart on 2008-12-02
Hi!  Thanks in advance for any help you guys can provide me.

I've set up 2 servers to mirror each other.  They're not doing anything complex, only sharing files.  I've set up an RSync job on one of them to pull the data over and ensure that the data is the same in both locations.

The systems are not set up to load balance.  This is only for data backup and ease/speed of recovery in case of a drive or hardware failure.

I'd like to have RSync run every 5 minutes.  There are only about 7 users on the server at any given time, and there aren't any large files being edited, so theoretically this should work.

I used cron to schedule the job to run every 5 minutes.  Since there are 3 different major file shares, I set up 3 jobs.  About an hour later I received a call from the client saying that the file server access was getting slow.  I promptly disabled the cron jobs and things seemed to return to normal.

Does anyone know what might cause this?  Is it the RSync jobs running at the same time?  Could it have something to do with the cron jobs?  Is it file access?

Per my knowledge of RSync, it should know how to deal with open files, and shouldn't do any major copies after the first copy - the documentation says it only copes files that have been changed since the last rsync, and even then only the parts of the files that have been changed.

Thanks!
- Jesse

---

### Post by CrucifiedEgo on 2008-12-02
Have you checked top?  it could be that the rsyncs are overlapping each other.

Also, i don't know that this is the best way to go about what you're trying to do.  Have you considered RAID, and then tossing the disks in the backup server if needed?

---

