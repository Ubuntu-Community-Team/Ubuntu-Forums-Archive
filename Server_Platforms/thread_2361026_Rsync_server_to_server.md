---
title: "Rsync server to server"
date: 2017-05-11
forum: Server Platforms
---

### Post by OiPenguin on 2017-05-11
I'm trying to mirror two servers by rsyncing what's on server A (*.31) to server B (*.32). Server B contains alot of what's on A, but not everything. It's important that I avoid a full total copy (1.6 GB) as that will result in me running out of space. Hence, I've tried the command below as a dry run to estimate the size being copied. I was expecting the output to give me the total size of **new files added to server B**, not the entire sum of files and directories in server A, which is my impression of the output. Being a novice at rsync I see to explanations: a) my script is incorrect and I'm rsyncing to the wrong location and hence, will run out of space. b) the output gives the entire size of the sum of files and directories which are subject to my script, but the destination is correct. If explanation b) is correct that is great, as I will have enough space for the intended backup. 

To repeat the essential question: Will the output of the script below be the total sum of files and folders subject to the script, regardless of what is actually transferred?

```
#!/bin/bash
# rsync backup-script
# single transfer of backup-script
# stored in /root at 192.168.0.31
# add --dry-run after -av to test

rsync -av --dry-run --progress --log-file=/root/rsync-single.log -e ssh /media/b0849d4b-e820-45d8-9736-d140bbd2e225/backup/rsync-backup-larslaptop-old root@192.168.0.32:/media/4b275ead-ee9d-4118-9b83-50d361f982dc/backup
```

Output:
```
sent 23,389,987 bytes  received 1,651,368 bytes  15,471.95 bytes/sec
total size is 1,666,577,686,608  speedup is 66,553.02 (DRY RUN)

```

---

### Post by howefield on 2017-05-11
Thread moved to the "*Server Platforms*" forum for a better fit.

---

### Post by TheFu on 2017-05-11
No need to specify -e ssh for the last 10 yrs. ssh is assumed for remote rsync.
```
$ rsync -av --dry-run --progress --stats /media/b0849d4b-e820-45d8-9736-d140bbd2e225/backup/rsync-backup-larslaptop-old  \
root@192.168.0.32:/media/4b275ead-ee9d-4118-9b83-50d361f982dc/backup/
```

Remote root is dangerous. I'd avoid it and actually have remote root prevented by the ssh settings. That doesn't mean this won't work, just that it won't work on a default Ubuntu system or on any that I've setup.

Also, I'd mount the storage using labels, to different non-/media locations.  UUIDs are for computers, not mounts. ;)

I'd use trailing slashes on the target. This is a subtle, but important, "rsync thing."  Trailing slashes have specific meaning. You can read the explanation at rsync.org. I'm assuming you want the "backups" directories to be identical. If this isn't true, then the command needs to change.

Make sense?

---

### Post by OiPenguin on 2017-05-11
> **TheFu said:**
> No need to specify -e ssh for the last 10 yrs. ssh is assumed for remote rsync.
```
$ rsync -av --dry-run --progress --stats /media/b0849d4b-e820-45d8-9736-d140bbd2e225/backup/rsync-backup-larslaptop-old  \
root@192.168.0.32:/media/4b275ead-ee9d-4118-9b83-50d361f982dc/backup/
```

Remote root is dangerous. I'd avoid it and actually have remote root prevented by the ssh settings. That doesn't mean this won't work, just that it won't work on a default Ubuntu system or on any that I've setup.


Both systems are actually Open Media Vault and I've only got ssh access with root. Hence rsync as root. (I choose to post here due to the high activity of this forum and the fact that Debian is the basis of OMV.) 

> **TheFu said:**
> 
Also, I'd mount the storage using labels, to different non-/media locations.  UUIDs are for computers, not mounts. ;)


Again, this is due to OMV using mdadm. I doubt that I can change this.

> **TheFu said:**
> 
I'd use trailing slashes on the target. This is a subtle, but important, "rsync thing."  Trailing slashes have specific meaning. You can read the explanation at rsync.org. I'm assuming you want the "backups" directories to be identical. If this isn't true, then the command needs to change.
Make sense?

I'll read up on trailing slashes. I definitely want the backup directory to be identical. rsync.org is not live though, but I'll find another source.

---

### Post by TheFu on 2017-05-11
Thought rsync had a dedicated site. .net?  somewhere else?    
I bet OVM has a different way to accomplish this. Not providing that important piece of information probably won't get the best answer.

---

### Post by SeijiSensei on 2017-05-11
If you know which directories you want to transfer, then I'd just use "--files-from" and a text file containing the matching globs.  Like this:
```

cd /
rsync -avr . server:/backup --files-from=/home/username/xfer-file-list
```
with entries in xfer-file-list like this:
```

home/
var/
data/

```
The entries do not have leading slashes since they are rooted at / already.  Use "rsync -avrn" to get the dry-run results.

---

### Post by OiPenguin on 2017-05-12
> **SeijiSensei said:**
> If you know which directories you want to transfer, then I'd just use "--files-from" and a text file containing the matching globs.  Like this:
```

cd /
rsync -avr . server:/backup --files-from=/home/username/xfer-file-list
```
with entries in xfer-file-list like this:
```

home/
var/
data/

```
The entries do not have leading slashes since they are rooted at / already.  Use "rsync -avrn" to get the dry-run results.

Thank you, however this approach makes me slightly uncertain. Will this make a *replicate* of server A in server B or copy the selected files and folders from server A to a different location in server B? 

Based on the file structure of my server as displayed in #1 is the syntax below correct?

```

rsync -avrn . root@ip-of-target-server:/media/4b275ead-ee9d-4118-9b83-50d361f982dc --files-from=/media/b0849d4b-e820-45d8-9736-d140bbd2e225/xfer-file-list

xfer-file-list.txt
home/
m/
var/

```

---

### Post by SeijiSensei on 2017-05-13
That syntax will create subdirectories under /media/4b275ead-ee9d-4118-9b83-50d361f982dc matching the ones in xfer-list like /media/4b275ead-ee9d-4118-9b83-50d361f982dc/home.

Make sure you start the transfer from the root of the file system by using "cd /" before running rsync.

---

