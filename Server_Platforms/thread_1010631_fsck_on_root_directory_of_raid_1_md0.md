---
title: "fsck on root directory of raid 1 md0"
date: 2008-12-14
forum: Server Platforms
---

### Post by sam702 on 2008-12-14
Hi.

I'm using 8.04 as a headless fileserver.

What is the correct procedure to check the file system on a RAID 1 setup for the root directory?

Please help.  Thanks.

---

### Post by dantrevino on 2008-12-14
The root filesystem actually resides on "md0".  You wouldnt want/need to do anything to the individual devices.  If one of the devices fail and you need to rebuild/recover, thats a completely separate process.

---

