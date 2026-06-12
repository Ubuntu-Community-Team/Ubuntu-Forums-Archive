---
title: "Timing problems with cron"
date: 2006-03-04
forum: Server Platforms
---

### Post by el3ktro on 2006-03-04
I have some really strange issues with rsnapshot & cron.

I'm backing up a server with rsnapshot. Backups are being made hourly to the backup dirs "hourly.0", "hourly.1" and so forth. When rsnapshot has finished a backup, it touches the last backup dir (hourly.0) so that I can see from the directory's timestamp when the backup has been made. This has always worked perfectly - but lately there is a strange problem:

If I run rsnapshot manually, everything is fine. When I e.g. run a backup at 17:30 then the backup dir has a timestamp of 17:30, or sometimes 17:31 when the backup takes a little longer.

But when the exact same backup script is run via cron, the timestamps of the directories are totally weird.

I made a test today: I ran a manual backup at 17:20, and the timestamp was 17:20. Then I ran another backup trough cron an 17:25, but the resulting backup dir had a timestamp of 17:13!! How can that happen? The cron jobs run at the right time, and I don't have any other problems with timing, it's just this strange thing that "touch" doesn't work correctly.

Any ideas?

Tom

---

### Post by el3ktro on 2006-03-04
I made some further investigations:

I'm backing up the directory /srv/data. Let's asume this directory has a timestamp of 18:00. When I run a MANUAL backup at 18:30, then the resulting backup dir has a timestamp of 18:30 - the time where the backup is created. Thats how it should be.

Hoewever when I run a backup at 18:30 TROUGH CRON, (I'm calling the exact same backup script) then the resulting backup dir has the same timestamp as the original directory, although it should update the time by 'touching' the backup dir.

How can that be??? I've looked at the rsnapshot program, it's a perl script, and it just calls "touch %backupdir" or something. How can this command have two different results, depending on if I run it manually or trough cron? When I call the backup script manually, I do this with "sudo rsnapshot ...". In the crontab, I let the user root execute the backup script of course.

Any ideas are very welcome!!

Tom

---

### Post by LordHunter317 on 2006-03-04
Posting your crontab would be a good start.

---

