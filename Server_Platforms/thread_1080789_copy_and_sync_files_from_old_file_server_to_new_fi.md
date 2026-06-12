---
title: "copy and sync files from old file server to new file server"
date: 2009-02-25
forum: Server Platforms
---

### Post by StrangeBrew on 2009-02-25
Here's my situation. I have old file server (server A, Win2k) that is in domainA. Then the new file server (server B, Win2k3) that is in domainB. I'm looking for a way to copy files modified after a certain date from server A to server B. I don't want everything from server A because there are a lot of old files that no one uses anymore. Then I need incremental copies done unitl can get all of the users moved from domainA to domainB. I was thinking an ubuntu box in the middle would best handle the job, I just need some help getting there.

thanks

---

### Post by ghoster on 2009-03-02
rsync? [http://samba.anu.edu.au/rsync/](http://samba.anu.edu.au/rsync/)

---

### Post by hictio on 2009-03-02
[Rsnapshot](http://rsnapshot.org/) its another option as well.

But, since you are dealing with Windows boxes, then take a look at [BackupPC](http://backuppc.sourceforge.net/).

[BackupPC Setup Manual](http://taksuyama.com/?page_id=5)

---

