---
title: "security for tmpfs and ramdisk in /etc/fstab"
date: 2011-02-27
forum: Security
---

### Post by MountainX on 2011-02-27
The found the following two lines recommended in a few online articles about security:

/etc/fstab:
```

tmpfs /dev/shm tmpfs defaults,nosuid,noexec,rw 0 0
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0

```

Anyone here want to comment on whether they are indeed recommended and whether they are correct (Ubuntu 10.10 64 bit)?

I've been using them since I built my system 6 months ago. I've observed a strange thing when I insert USB flash drives. They either open a root Nautilus or give an error (or both). The fact that simply inserting any USB flash drive in my system opens a root Nautilus without a password prompt freaks me out!

---

