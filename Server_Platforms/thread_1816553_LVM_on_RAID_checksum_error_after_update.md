---
title: "LVM on RAID checksum error after update"
date: 2011-08-02
forum: Server Platforms
---

### Post by zuboskal on 2011-08-02
Hello.

I have miss my LVM after do-release-update from 10.10 to 11.04.

I have root on LVM, and now VolumeGroup does not start.

```
vgscan
/dev/md0: Checksum error
```I try check & repair my RAID:
```
echo 'check'  >  /sys/block/md0/md/sync_action
echo 'repair'  >  /sys/block/md0/md/sync_action
```but without success.

What can I do next?

---

