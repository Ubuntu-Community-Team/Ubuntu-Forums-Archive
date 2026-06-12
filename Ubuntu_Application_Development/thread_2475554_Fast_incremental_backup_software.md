---
title: "Fast incremental backup software"
date: 2022-05-31
forum: Ubuntu Application Development
---

### Post by baltic on 2022-05-31
One day (That was when i could not restore my backup to another drive while booted from an USB stick) I got tired of duplicity quirks and decided that I can do better.

So [here is Archivarius]("https://github.com/dsvi/archivarius"). It's more like a wayback machine. It can save versions (snapshots) of a target dir, so you can restore this version later.

It's fast:


[LIST]
[*]To restore the latest saved version, it does not have to first restore the oldest one, and then incrementally refine it. It goes right to the latest, despite being incremental. So depth of your archive does not affect restoration performance.
[*]Uses modern encryption (ChaCha20+Poly1305) and compression (zstd).
[*]It does not require a few gigs of local cache to work efficiently over network. Neither does it require periodic full-backups. So it's much easier on the network bandwidth.
[/LIST]

It's reliable:


It never overwrites files. It only adds new ones, and deletes the obsolete ones. So even in case of power outage while archiving, your archive is safe.

---

### Post by TheFu on 2022-05-31
What is the authentication method for "pulled" backups over the network?

People use the term "snapshot" incorrectly all the time, especially when it comes to backups.  Snapshots are a file system capability and takes far less than a second to freeze the blocks involved.  Most backup tools that support versioning don't tie into the file system or volume management capabilities, so their versions or revisions shouldn't be called "snapshots".  IMHO.
LVM, ZFS, BTRFS support snapshots.

Every backup tool has quirks. Just depends on understanding what the dev was thinking.

OTOH, anything that gets more people from abusing tar is always a huge bonus in my mind.

---

### Post by baltic on 2022-06-01
Yeah, it's essentially "versions". Kinda like in git.
It works only with local filesystems, so if you need network of whatever kind, you have to mount it first, like i do ;)
That helped to keep the code extremely simple. Less then 5k lines of C++ code.

---

### Post by TheFu on 2022-06-01
There is something to be said for K.I.S.S. and for people not doing backups at all, anything is better than nothing, especially when versioned backups are really easy.

In this day of malware, we can't use any backup solution that isn't "pull"ed by the backup server and storage mounts are no-go as well, since a virus can spread in that way.  Of course, any client/server architecture introduces a bit of complexity and possible incompatibility.  rdiff-backup has run into that a few times, by changes in the way python serializes streams between v2 and v3, most recently.  But besides that, the versioned storage is very similar to what I understand Archivarius uses, i.e. reverse-incremental diffs.  There are some liabilities in doing that.  Only the oldest backups can be trimmed. 

If "A" is the most recent version and "Z" is the oldest, then removing "P" will break all the versions from "Q" - "Z".  "A" moves forward with every new backup version.  After a backup completes, my script removes "Z" and older backup versions.  Sometimes I'll take a fresh backup in the middle of the day because they usually only need a few minutes to complete before attempting something too dangerous. Plus, not all of my systems use snapshot-capable volume management, which I'm slowly correcting.  True snapshots seem to confuse normal users, sadly.  Timeshift will use them, if it is available, but otherwise, it does rsync stuff with hardlinks. Meh. That doesn't provide versioned metadata about the ACLs, owner, group, permissions xattrs which are mandatory at restore time.

BTW, if you don't handle sparse files correctly, you'll want to add that.  Sort sucks when an LDAP DB says it is 20MB (on disk), but explodes to 50G during a backup. I've had that happen. rdiff-backup and rsync have options to handle sparse files.  Since lots of people use sparse files for VMs, that would be a more likely place to see it, I suspect.

---

