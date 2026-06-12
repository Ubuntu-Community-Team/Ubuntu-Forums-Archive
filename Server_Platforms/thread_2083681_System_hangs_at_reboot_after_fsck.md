---
title: "System hangs at reboot *after* fsck"
date: 2012-11-13
forum: Server Platforms
---

### Post by martijntje on 2012-11-13
I am having an annoying problem where a server sometimes hangs for a long, long time during a reboot. This usually happens when the server has not been rebooted for a while.

After the fsck, there is no output for a long time. The screen looks like this:

```
fsck from util-linux 2.20.1
/dev/sda1: clean, 928681/8921088 files, 4273469/24683840 blocks
```It's hard to see what exactly is wrong, because no indication is given as to what the server is doing. After it has finally booted (which can take a few hours), rebooting it works just fine.

---

### Post by rubylaser on 2012-11-14
Have you looked at dmesg to view the whole boot process after it's done booting?

---

