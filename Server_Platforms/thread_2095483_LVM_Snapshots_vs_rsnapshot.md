---
title: "LVM Snapshots vs rsnapshot"
date: 2012-12-17
forum: Server Platforms
---

### Post by gyzer on 2012-12-17
I am just starting to play around with LVM and I was curious about best practice for backups. 

I have been using rsnapshot for years and it has never failed me. Now with using LVM, should I still be using rsnapshot or should I just be using LVM snapshots? I will be backing up to an external USB drive.

---

### Post by gyzer on 2012-12-22
Any ideas? I'm just really curious what the best practice would be.

---

### Post by sandyd on 2012-12-23
Generally, I find LVM snapshots much faster than rsnapshot, but thats just me.

---

### Post by gyzer on 2012-12-23
I don't care about speed. This is done late at night on my home server.

---

### Post by LHammonds on 2012-12-24
I setup my servers with LVM and use snapshots along with fsarchiver to create full, 100% backups that do not require any downtime.

Check my sig for details.

---

### Post by craigp84 on 2012-12-24
rsnapshot and lvm snapshots tend to be used as solutions for slightly different problems.

E.g. backing up a database - i'd choose LVM snapshots to ensure i had a consistent backup (rsnapshot would grab the commitlog and the data file(s) at different times potentially leading to data loss).

Alternatively if i was backing up home directories or a shared folder on the network, i'd choose rsnapshot - it's useful for users to be able to self service the restore operation, and i don't need to worry about inconsistencies between files backed up in random order.

Hope this helps

---

### Post by gyzer on 2012-12-26
That does. I'm not running any databases on the server so then I really don't need to use LVM snapshots. I guess the only time I would do one is before I make massive changes to the system or before I run updates.

---

