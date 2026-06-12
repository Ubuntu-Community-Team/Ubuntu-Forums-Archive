---
title: "How Easy is it to: Corrupt Luks Container w/ Improper Dismount"
date: 2016-12-07
forum: Security
---

### Post by mikey93898 on 2016-12-07
Hey all,

Suppose I mount a remote file to my desktop (ie: sshfs). The file is a luks container. Then I "open" the locally-mounted luks container file. Then I lose my internet connection in the middle of a file operation.

Is the luks container corrupted at this point? Would a certain filesystem be better at preventing corruption? Certain settings maybe (ie: somehow disable write cache)?

I ask because I'd like to place a hard drive at a friend's house, and use luks to allow me to use that hard drive as a remote backup destination, fully encrypted even to my friend. I'm trying to figure out the best way to go about this. I think I realize eCryptfs would be more safe, but I've had issues mounting eCryptfs off an sshfs mount (certain read/write permission lockup problems).

Any ideas?

---

### Post by TheFu on 2016-12-07
ZFS is the only file system I know that validates data on disk is what was supposed to written. BTRFS might have similar protections, but I consider it too new to trust with my data.

LUKS is a whole partition encryption method, correct?  That means anyone with root or open permissions to the mounted location will have access. This same issue happens with ecryptfs that is automatically mounted at login.

I cannot image that any remote access file system would be able to corrupt LUKS. They just don't work at that level.  The only risk would be if a file where opened and being written, then there could be corruption, but any journal'ed file system should handle that sufficiently.

BTW, sshfs is a handy tool, but for remote backups, there are other tools which use ssh and are more efficient for that sort of work.  rsnapshot, rsync, rdiff-backup, rbackup, and probably 30 others.  If you really want a secured backup, the data needs to be encrypted before leaving your machine.  duplicity and a few others do this. 

I backed up Mom's (RIP) Lubuntu system from 500+ miles away every week using rdiff-backup (it uses ssh tunnels by default).  Local backups, she used Back-In-Time, it was easier for her to understand. In 3 yrs of doing that, I don't remember **any** times when we were disconnected.  She had $15/month DSL, the lowest tier sold.  rdiff-backup knows when a backup is corrupt and rolls back the failed files next attempt.  I pre-seeded the first backup during a visit, but after that the amount of time needed was just minutes a week. She didn't have any media, just journals and emails and quicken data (she used Quicken under WINE).

Anyway, i think you'd be happier with a different backup solution. Sadly, I don't think my favorite tool, rdiff-backup, is the best for your encryption needs.  Take a look at [http://zbackup.org/](http://zbackup.org/) . I haven't used it, but seems to meet the requirements.

---

### Post by untrustytahr on 2016-12-07
I can't speak to the fs corruption aspect, but duplicity would be a good choice for this IMHO.  It allows you to encrypt either symmetrically or asymmetrically using gpg.  All anyone that had physical access to the files would see are encrypted tarballs.  Without your private key and/or password it would be useless to them.  The ssh transport is an additional layer of security from interception, but the end-to-end encryption would be secure even if transport was compromised.

It has too many options to cover but the man page does a fairly decent job with them (yeah, i know... but it really does cover most situations).

As always with backups, check them and periodically do a file restore to make sure things are working as expected.

---

