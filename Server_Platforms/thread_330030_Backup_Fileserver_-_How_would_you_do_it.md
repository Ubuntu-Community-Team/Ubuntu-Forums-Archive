---
title: "Backup Fileserver - How would you do it?"
date: 2007-01-02
forum: Server Platforms
---

### Post by Transition on 2007-01-02
So i put together a server with intent to be used as a fileserver / backup machine.  Below is the relevent information.

Ubuntu 6.10 Server
1 x WD 250gb OS / File Drive
2 x WD 250 gb Backup Drives
.. and a hot swappable SATA rack for the 2 backup drives.

My objective is to do daily backups of the OS drive by use of rsnapshot.  I plan on removing 1 of the backup drives every Friday and taking it home so we always have a safe off-site copy.   This means there will always be one system drive in, and one backup drive.

Can anyone forsee any problems by doing it like this?  I'm trying to think of the easiest way to accomplish this.

---

### Post by Transition on 2007-01-03
No one?

---

### Post by MJN on 2007-01-03
There's probably not all that much to say to be honest..

Have you thought about a more automated backup process? Off-site backups are all well and good but if they rely on you physically being present at the end of the week to manually remove the drive you may find it's the week when you're not in that the computer room burns down... (sods law and all that).

I'd be inclined to look at an 'online' offsite solution i.e. backing up weekly (or daily) over the 'net but given the obvious bandwidth issues this may benefit from being incremental.

Another concern with physically removing a backup drive is what do you do with it? Is there any danger of it being compromised? (e.g. stolen from you, your car etc). An online solution at least always keeps the data in controllable environments (I am assuming the link between the two is encrypted) and hence far less prone to potential compromise.

Mathew

---

