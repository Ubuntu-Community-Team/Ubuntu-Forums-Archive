---
title: "Backing up: worth its own Desktop icon?"
date: 2014-01-25
forum: Ubuntu, Linux and OS Chat
---

### Post by EnglishElectricAndy on 2014-01-25
I never cease to be amazed at the number of people I come across who don't consider the idea of making backups until AFTER a major computerized catastrophe. A case study is a beer buddy of mine who complained about a hardware failure that meant he couldn't access his 55GB of music files. When I said "Didn't you back them up?" there was a poignant silence.

Pondering this, the thought occurred that I haven't come across a mainstream OS or distro that has an icon for 'Backing up' or 'Make backups' on the default Desktop/start page. Clicking on such an icon wouldn't have to do very much, maybe open a dialog with options to backup to a local external device, backup to an online host or (perhaps with a 'not recommended' caveat) backup to partition on this disk.

Of course the user is free to disregard such an icon, but if it was on the Desktop by default it might prompt some people to have a :idea: moment and save themselves from potential future head-and-heart aches.

Interested to hear other views on the pros and cons of this approach.

---

### Post by TheFu on 2014-01-25
Perhaps a "Setup Backups" icon ... doing manual backups is already a failure in my book.  I know.  I didn't get backup religion until 1 disk failed that was part of a 3 disk LVM LV partition. My LVM-fu was weak then and I lost all the data on all 3 disks, not just the 1 that failed.  I had tape drive and plenty of tapes, but it was slow.  I was backing up before that problem happened.  Switched to disk-based backups and did manual backups with rsync every week. That turned into every few weeks, every few months, then I lapsed over a year between backups. With all the anti-reinforcement (nothing bad happened), I let the system get to a point where doing a backup wasn't possible anymore.

Since around 2002, I've had backup religion. If I can't afford the backup storage, then I don't by the main storage either.  I'm willing to use cheaper "green" drives for backups, but not main storage.  Everything is autmatic, daily with either 60 days of 90 days of backups. Any date in the backup range can be restored.  Takes about 1-3 minutes a day to backup each machine (or VM).  The backups are really efficient - usually 12% larger than the original storage - so if the server has 10G of storage used, then the backup for 60 days is about 12G. It depends on how much changes over that time, but 12% is a good average. This is for OS/Apps and personal files.

For media - audio and video files, I use rsync with a simple mirror. No need to capture changed data for that sort of files.

Then there are the people who confuse RAID with a backup.  **RAID cannot replace backups**. It is for HA - High Availability. Most of the time, RAID ends up being a faster way to get corrupt data replicated to more places.  With versioned backups, can file corruption can be resolved. Any virus that modifies files can be caught and those files restored. RAID doesn't help at all with that.

---

### Post by CharlesA on 2014-01-25
I think I also got the "backup religion" that TheFu talks about because I keep multiple backups of everything and stress that to anyone - if you value your data, you will keep backups of it.

Manual backups = I will forget to run them. Automatic = win.

---

### Post by Old_Grey_Wolf on 2014-01-25
I have encountered people that make backups; however, they never checked to see if the backup solution they chose was doing what they thought it was doing.

---

