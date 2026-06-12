---
title: "Unable to access LUKS-encrypted external hard drive"
date: 2022-01-07
forum: Security
---

### Post by arche11 on 2022-01-07
Hi,  I have an problem with an external hard drive. It is fully Luks-encrypted and normally unlocks automatically on boot-up. Maybe it got ejected without safely disconnecting it.  When I connect the drive two partitions show up in Nautilus: 'Boot' and 'Rootfs' and the rest is free disk space.  I don't really know what to do. Can someone help me restoring my data?  Thanks. If you need extra info, terminal-outputs, etc. let me know.

---

### Post by TheFu on 2022-01-07
Need some information. Run this and post the results wrapped in forum 'code tags'
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```

It is very likely that LVM is used, so we need to see how the LUKS container is organized/layered.

I've used 'code tags' in this post. If yours doesn't look the same, fix it. Please.  Especially for this command output, it is too easy to make a mistake if the columns don't align.

---

