---
title: "/media being mounted as /media1"
date: 2012-09-22
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by fantab on 2012-09-22
I have /DATA partition which is mounted as media... I mount it manually whenever required.

Since Quantal install...  I have noticed that it is being mounted as /DATA1 and not /DATA. In nautilus it is shown as DATA1 on the title bar but below it is shown as DATA with a Disk icon before it. 

How to fix this?

---

### Post by sgage on 2012-09-22
> **fantab said:**
> I have /DATA partition which is mounted as media... I mount it manually whenever required.

Since Quantal install...  I have noticed that it is being mounted as /DATA1 and not /DATA. In nautilus it is shown as DATA1 on the title bar but below it is shown as DATA with a Disk icon before it. 

How to fix this?

I've run into this myself. It seems to be a bug, so that if you shut down/reboot the machine while DATA is mounted, the next time you go to mount it it will be DATA1. I don't of a fix, but a workaround is to try to remember to unmount you DATA partition before shutting down.

---

### Post by mc4man on 2012-09-22
> **fantab said:**
> I have /DATA partition which is mounted as media... I mount it manually whenever required.

Since Quantal install...  I have noticed that it is being mounted as /DATA1 and not /DATA. In nautilus it is shown as DATA1 on the title bar but below it is shown as DATA with a Disk icon before it. 

How to fix this?
Do a fresh boot up & remove /media/DATA

---

### Post by fantab on 2012-09-23
> **mc4man said:**
> Do a fresh boot up & remove /media/DATA

Could you please elaborate on it mc4man? Remove /media/DATA from where?

---

### Post by sgage on 2012-09-23
> **fantab said:**
> Could you please elaborate on it mc4man? Remove /media/DATA from where?

I think he meant /media/(your account name)/DATA - they've changed the directory layout a bit. Before you mount your DATA partition, check that directory. If you see a DATA subdirectory, delete it (as root), then, when you mount, a new DATA subdirectory will be generated. If a DATA subdirectory already exists, the mounter will create DATA1. This won't be a problem if you are sure to unmount DATA before shutting down/rebooting.

---

### Post by dino99 on 2012-09-23
> **fantab said:**
> Could you please elaborate on it mc4man? Remove /media/DATA from where?

i wonder if you really understand what you do :confused:

sudo rm -rf /media/DATA

---

### Post by fantab on 2012-09-23
Alright..... Thanks.

Generally I don't unmount it before I shutdown but will try to bear that in mind.

---

