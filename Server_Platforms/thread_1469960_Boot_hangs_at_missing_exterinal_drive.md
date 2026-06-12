---
title: "Boot hangs at missing exterinal drive"
date: 2010-05-02
forum: Server Platforms
---

### Post by MrWES on 2010-05-02
I just finished successfully upgrading my Hardy server to Lucid, 10.04, now when I boot the server it pauses for a "missing" drive and I have to hit the "S" key to skip or continue to wait. The drive is a 30gb 2.5" drive in an enclosure and is at times connected via USB. Here's the entry from /etc/fstab:
```
/dev/sdg1 /media/30gb auto users,gid=users,umask=0000,defaults

```

Will changing it to noauto prevent the system waiting for the drive to become available?

Thanks,
Bill

---

### Post by MrWES on 2010-05-04
Kakakabump!

---

