---
title: "DF Output Odd"
date: 2009-07-01
forum: Server Platforms
---

### Post by terazen on 2009-07-01
I was looking at this a second ago and for /dev/sda1 it is saying 211G available and 60G used which adds up to 271G and not 285G that df reports.  How does this math work?

df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             285G   60G  211G  23% /
varrun                2.0G   52K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G   44K  2.0G   1% /dev
devshm                2.0G     0  2.0G   0% /dev/shm

---

### Post by TwiceOver on 2009-07-01
You lose 5% by default so that the disk can never truely become completely full.  Some sort of administrative buffer.

You can change that setting using tune2fs...  I can't remember the exact command.

---

### Post by ian dobson on 2009-07-01
Hi,

mkfs reserves 5% for user root, so that when the fs is full for normal users root can still login and tidy things up.

Regards
Ian Dobson

---

