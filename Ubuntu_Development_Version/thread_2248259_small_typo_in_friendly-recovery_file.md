---
title: "small typo in friendly-recovery file"
date: 2014-10-13
forum: Ubuntu Development Version
---

### Post by zika on 2014-10-13
/lib/systemd/system/friendly-recovery.service
line 14
```
ExecStartPre=-dmesg --console-off
```change to```
ExecStartPre=-/bin/dmesg --console-off
```preventing warning in boot process.

---

### Post by sammiev on 2014-10-13
Thanks zika,

Took care of a boot warning saving a few seconds on boot time.

---

### Post by tomh0665 on 2014-10-15
[https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/1354937](https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/1354937)

---

### Post by rrnbtter on 2014-10-15
Greetings,
@zika
Thank you!

---

### Post by zika on 2014-10-15
> **tomh0665 said:**
> [https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/1354937](https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/1354937)It'll be a nice way of testing if any of dev-guys read forum(s)... ;)

---

