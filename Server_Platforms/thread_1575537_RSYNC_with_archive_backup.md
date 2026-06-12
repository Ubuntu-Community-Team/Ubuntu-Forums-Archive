---
title: "RSYNC with archive backup"
date: 2010-09-15
forum: Server Platforms
---

### Post by tlsarles on 2010-09-15
I think rsync is the tool for the job, but I'll let the experts decide....

Say I have a Linux host acting as an ISCSI server for a Windows box. I want to keep an off site backup, so I figure rsync will keep the ISCSI server synced with an offsite Linux host. I understand that Rsync does block level incremental transfer to conserve bandwidth.... ok, awesome.

The trick is, that I also want an archival copy kept. Say I want to go back to a revision of a file from 10 days ago, I need to be able to do that.

I was planning on using Backup Exec, since we currently have a licensed copy. Throw the archives from Backup Exec onto the ISCSI server as well, and have it keep a rotating 30 day backup, or something like that. The issue I see here is that this will be creating a deleting files as it does its daily backup rotation. I'm guessing RSYNC will see these as new files, and likely retransmit everything on a daily basis. The question then becomes, is this assumption correct, or will it still know to do a block level incremental transfer even when file names and such are changing?

or........ is there a better way to do this?

Appreciate it

---

### Post by CharlesA on 2010-09-15
It really depends on what you want to do. Rsync won't create incremental backups on it's own. 

Check this out here: [http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)

---

### Post by BkkBonanza on 2010-09-16
That's a great page on getting more out of rsync for backup rotation.

Regarding rsync block-level file copying... it will re-copy the whole file if it has a new name. Rsync starts by looking at file timestamp info and if it has changed then it will find differences and copy changed blocks. But if the filename is different then it considers it a new file and copies the whole thing.

Note that in the page mentioned above he talks about using hard links and rsync auto unlinking before copying (with --link-dest option). This is a file level incremental backup (not block level). When the backup file is unlinked a copy must be made to provide the unlinked version but that copy should only happen on the same device, so if rsyncing across the LAN or internet then that should be much faster than a full source file copy. The cross LAN/net copying would be incremental once the destination local file is unlinked.

------
To get "true block level" incremental backups you would need to use a versioning file system. This would store versions of files as they change on a block level. None of the "normal" Linux file systems do this but there are some available. I haven't worked with them ([see here]("http://en.wikipedia.org/wiki/Versioning_file_system")). You may not really need that level anyway as it seems like an rsync + hard link style backup is a decent compromise storing at least periodic file versions.

Using rsync along with something like CopyFS (or brtfs,ext3cow) seems like an interesting variation that should provide file copy efficiency with auto-versioning of the backups. I haven't tried it, though I may experiment myself. Potentially you could do differential backups more often for a finer grained trail with very little extra xfer overhead.

(CopyFS is actually in the repos and doesn't require a special formatted partition since it uses Fuse. It's not clear if it's block level though.)

---

### Post by BkkBonanza on 2010-09-16
I'm just testing a small [NILFS]("http://www.nilfs.org/en/about_nilfs.html") partition on my iSCSI drive. After looking at some different options this seems like the most readily usable option for Ubuntu 10.4.

I'm resizing my ext3 partition to leave 2 GB for a dedicated backup NILFS partition. I'll mount that and rsync my backups onto it across the LAN. This should allow for rsync to do efficient differential backups and also keep checkpoints each time so that accessing historic versions of the backups is easy. 

I'll post back when I see how it works.
...
Reporting back.
NILFS worked fine for me on iSCSI across the LAN. I used rsync to do some test backups. That's when I realized what I should have known all along. Rsync does "atomic" copies, it copies the file, updates it, and removes the original and links the new one in. Hence, it doesn't benefit from versioning at all. You just end up with more deleted data in remnant version checkpoints. I guess I should have expected that. The result is that you won't get as good efficiency as the method suggested in the article above (using the --link-dest option). Rsync will always be making an temporary copy anyway.

---

### Post by tlsarles on 2010-09-20
Great answers, thanks. Looks like I've got some reading to do

---

### Post by LightningCrash on 2010-09-20
It sounds like the feature set you're looking for really closely matches that of ZFS.

ZFS supports snapshots, you can transmit incremental filesystem changes to your backup pool, etc.

---

