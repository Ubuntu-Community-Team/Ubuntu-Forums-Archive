---
title: "Restrict Acces to a partition from a live CD"
date: 2009-06-09
forum: Security
---

### Post by pyrocloud on 2009-06-09
I'm currently shoring up the security of our system, and a thought crossed my mind.

What if someone came into the server room and wanted to clean out a partition or do some other nasty stuff when no one was looking?

Like using a bootable cd distro to access files and stuff they shouldn't.

Is there a way to stop or restrict this type of situation?

---

### Post by rookcifer on 2009-06-09
The only way to stop it would be to set a BIOS password so that they can't boot the machine with a live cd.  However, this wont stop them from messing with the machine while it's running (but if they don't have a root account or sudo access, the damage they can do is limited).

If the machine wont be running, then whole disk encryption will stop them from being able to boot the OS from the hard disk or see any information on it from a livecd.  However, encryption will not stop them from destroying the partitions from a livecd.  In essence, they can't read the partitions, but they can format them.  However, since you are running a server, I doubt encryption will do you much good since the machine needs to be on 24/7.

The only way to be sure is to put the machine in a locked room where only you and people you trust have the key.  Then set a BIOS password so the machine can't be rebooted (even a BIOS password will not help if they have access to the machine and can steal the hard disks and boot it from another machine.  That is where encryption comes in handy).

---

### Post by bodhi.zazen on 2009-06-10
The only way to secure your data is with encryption.

The only way to prevent access to a partition from a live CD is to restrict physical access to the server. If the partition is encrypted, it can not be accessed without a password. It can, however, be deleted.

A bios password is of little use as it is easily defeated either by resetting the bios password or pouring a cup of coffee into the cooling fan.

Physical access == bad news.

---

### Post by Cheesemill on 2009-06-10
Anyone with physical access to your machines can do whatever they wish. The only way to secure your data is with full-disk encryption.

This only stops them accessing your data though, there would be nothing to stop them deleting it.

Cheesemill

---

### Post by statistic on 2009-06-12
Full disk encryption via truecrypt Is actually surprisingly easy to use, and I recommend it highly. The downside however is you would need to be physically present for a reboot, and forgetting the password would mean unrecoverable data loss.

As for trying to prevent vandalism, regular off-site backups would be the system for that. You could truecrypt those as well, but I suggest just locking them in a safe somewhere, that way if you DO forget your truecrypt password, you still have the backups.

---

### Post by Jekshadow on 2009-06-13
Encrypt the drive, and prevent physical access to the room. I recommend a good lock and then use full drive encryption.

---

