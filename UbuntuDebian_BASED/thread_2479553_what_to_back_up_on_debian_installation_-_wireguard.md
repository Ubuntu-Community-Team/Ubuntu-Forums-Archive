---
title: "what to back up on debian installation - wireguard and redmine (from turnkey linux)"
date: 2022-09-28
forum: Ubuntu/Debian BASED
---

### Post by primuspaul on 2022-09-28
I run two computers as servers - one with wireguard and one with redmine. Nothing much really changes on these computers with the exception of the redmine server which obviously has changes applied to the mariadb database daily, but this specific component is already backed up daily via a database dump daily (via cron).

However, there are occasional changes that are made to the system. Certificates are sometimes added to wireguard for extra computers, cron items and webpages are sometimes changed on the redmine server, etc... So my question is: how do I back these up to allow me to recover the system in the event of catastrophic failure? What directories do I need to back up and what is the recommended way of doing it?

Presently the system is accessible via SSH (PuTTY), so something that works over PuTTY is recommended. These major backups are only going to be run once a month or something like that since, once again, besides MariaDB changes (which are backed up separately), no real changes are commonly made to these systems.

---

### Post by deadflowr on 2022-09-29
*Thread moved to **Ubuntu/Debian BASED***

---

### Post by TheFu on 2022-09-29
Proper backups of Unix systems cannot be performed to Windows, unless the backup tool encapsulates the data and file system attributes completely.  Duplicity (and that family of tools) does that, but most others do not.  Many people use rsync and librsync, but MS-Windows storage would drop 50% of the metadata making the backup data next to useless.

So, you either need to use a proper OS and file system to store the backups
or you need to suffer through using duplicity.  I do not use duplicity.

As for what you need to save, there are many, many, opinions about that.  I've posted hundreds of times what my backup and restore processes are in these forums. Those posts often have specific directories to be included, but you'll have specific directories too.  

BTW, I ran a redmine server for a few years. Nothing really special about it that I recall.  Typical RoR webapp.  A little slow, but not THAT bad.  We use LVM snapshots to quiesce the file system before doing backups. This prevents file corruption in the backups.  BTRFS and ZFS support proper snapshots too.  The trick is to not keep too many, since any storage blocks in a snapshot cannot be modified - effectively they are read-only.  That's good and bad, depending on the amount of excess storage inside the system.  I prefer to let my backups handle the versioning where it is more efficient and differences can be stored as compressed diffs. That's how rdiff-backup works. Alas, the Windows implementation sucks and without a proper Unix file system that supports owner, group, permissions, ACLs and xattrs, Windows is useless for backups, IMHO.

Of course, you could run a small virtual machine on your Windows system and use that to "pull" the backups from the server.  "pulled" backups are excellent at combating malware, though I wouldn't want Windows close to the backups - MS-Windows getting hacked is a way of life, it seems. Big target. Bet they'd love access to the backups. If you go this route, I'd definitely enable Linux-based LUKS encryption on the storage where the backup data is stored.

---

### Post by primuspaul on 2022-09-29
> **TheFu said:**
> Proper backups of Unix systems cannot be performed to Windows, unless the backup tool encapsulates the data and file system attributes completely.  Duplicity (and that family of tools) does that, but most others do not.  Many people use rsync and librsync, but MS-Windows storage would drop 50% of the metadata making the backup data next to useless.

So, you either need to use a proper OS and file system to store the backups
or you need to suffer through using duplicity.  I do not use duplicity.

As for what you need to save, there are many, many, opinions about that.  I've posted hundreds of times what my backup and restore processes are in these forums. Those posts often have specific directories to be included, but you'll have specific directories too.  

BTW, I ran a redmine server for a few years. Nothing really special about it that I recall.  Typical RoR webapp.  A little slow, but not THAT bad.  We use LVM snapshots to quiesce the file system before doing backups. This prevents file corruption in the backups.  BTRFS and ZFS support proper snapshots too.  The trick is to not keep too many, since any storage blocks in a snapshot cannot be modified - effectively they are read-only.  That's good and bad, depending on the amount of excess storage inside the system.  I prefer to let my backups handle the versioning where it is more efficient and differences can be stored as compressed diffs. That's how rdiff-backup works. Alas, the Windows implementation sucks and without a proper Unix file system that supports owner, group, permissions, ACLs and xattrs, Windows is useless for backups, IMHO.

Of course, you could run a small virtual machine on your Windows system and use that to "pull" the backups from the server.  "pulled" backups are excellent at combating malware, though I wouldn't want Windows close to the backups - MS-Windows getting hacked is a way of life, it seems. Big target. Bet they'd love access to the backups. If you go this route, I'd definitely enable Linux-based LUKS encryption on the storage where the backup data is stored.

Perhaps it makes more sense to install a virtual machine program on another linux machine and run these as virtual machines on that linux machine? That way I can just back up snapshots of the VMs.

If I want to back up only the really important things (besides the database) like the wireguard certificates and CRON records, do I just need to back up [COLOR=#232629][FONT=ui-monospace]/var/spool/cron[/FONT][/COLOR] & [COLOR=#232629][FONT=ui-monospace]/etc/[/FONT][/COLOR]? Then I'll just reinstall on VMs.

---

### Post by TheFu on 2022-09-29
VM snapshots aren't the same as backups.  Backing up a VM snapshot might as well be like using dd, which is an extremely inefficient way to backup anything.

Whatever you choose to backup, you'll need to test the restore process to ensure you don't create a chicken/egg problem.  Usually takes me 5 attempts to get it correct, modify the backups to get the missing information, then repeat.  Until you actually test a restore (or 5), you really don't know if you have backups at all.

I'm a huge fan of daily, automatic, versioned backups.  With the right tool, these can complete in seconds, effectively having zero downtime and if volume manager snapshots are used (don't confuse snapshots that aren't created using a volume manager with anything else), then there won't be any file corruption.

Getting /etc/ is certainly useful, but you cannot blindly restore /etc/ onto a new system.  That would be bad.  Some files can be selective restored. Others need to be carefully merged and others shouldn't be touched at all on the new system.  That's left for you to figure out which is which.  I put a comment tag in any files I modify in /etc/ so I know which I've modified.  /etc/ is small enough that getting everything isn't a huge problem, especially with efficient versioned backups.

---

