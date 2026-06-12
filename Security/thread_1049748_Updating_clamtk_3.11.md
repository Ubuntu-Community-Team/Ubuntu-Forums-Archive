---
title: "Updating clamtk 3.11"
date: 2009-01-24
forum: Security
---

### Post by wangsuda on 2009-01-24
I installed clamtk 3.11 on Ubuntu 8.10. I did this because I run a dual boot system (windows XP pro SP3). I tried updating clamtk 3.11, but the response I received is "you must be root to install updates." OK, how do I get to root to install updates? In advance, thank you.

---

### Post by fotno on 2009-01-24
sudo clamtk

---

### Post by cariboo on 2009-01-25
The correct command is:

```
sudo freshclam
```

When you installed clamtk  there should have been a cron job created, that goes out and checks for updates every night.

Jim

---

### Post by wangsuda on 2009-01-25
> **cariboo907 said:**
> The correct command is:

```
sudo freshclam
```

When you installed clamtk  there should have been a cron job created, that goes out and checks for updates every night.

Jim
Thanks Jim, appreciate the help!

---

