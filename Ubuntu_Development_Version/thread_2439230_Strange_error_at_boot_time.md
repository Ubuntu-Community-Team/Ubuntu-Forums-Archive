---
title: "Strange error at boot time"
date: 2020-03-24
forum: Ubuntu Development Version
---

### Post by sgage on 2020-03-24
Wnen I boot Ubuntu MATE 20.04 (updated as of today), the following is briefly displayed (so briefly I can hardly read it), after which boot continues as normal and nothing seems at all wrong in the session.

```
[    0.285860] Trying to unpack rootfs image as initramfs...
[    0.428563] Initramfs unpacking failed: Decoding failed
```

Anyone know what this is all about?

---

### Post by VMC on 2020-03-24
See this bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1835660](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1835660)

---

### Post by sgage on 2020-03-24
Yes, that's it VMC. I have added to the report.

Thanks for the pointer!

---

