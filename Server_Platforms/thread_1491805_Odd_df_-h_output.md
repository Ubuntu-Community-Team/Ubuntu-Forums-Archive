---
title: "Odd df -h output"
date: 2010-05-24
forum: Server Platforms
---

### Post by Loki57701 on 2010-05-24
When I run the command *df -h *I get a weird output:

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             109G  1.1G  103G   2% /
none                  238M  248K  238M   1% /dev
none                  242M     0  242M   0% /dev/shm
none                  242M  240K  242M   1% /var/run
none                  242M     0  242M   0% /var/lock
none                  242M     0  242M   0% /lib/init/rw
/dev/sdb              459G   82G  354G  19% /share
/dev/sdc1             1.9T  304G  1.6T  17% /usb




```I've never seen this before. I'm thinking maybe I should run a disk erasing program like DBAN and re-install.

Any Advice?

---

### Post by Ryan Dwyer on 2010-05-24
What's weird about it? I get similar results.

---

### Post by sylvester_0 on 2010-05-24
Looks fine to me...

```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda4              19G   15G  2.7G  85% /
none                  998M  276K  997M   1% /dev
none                 1002M  3.4M  999M   1% /dev/shm
none                 1002M  228K 1002M   1% /var/run
none                 1002M     0 1002M   0% /var/lock
none                 1002M     0 1002M   0% /lib/init/rw
/dev/sda3             179M  131M   39M  78% /boot
/dev/sda6             223G   58G  165G  26% /media/FBF2-BA92

```

---

### Post by nmaster on 2010-05-24
> **Ryan Dwyer said:**
> What's weird about it? I get similar results.
perhaps the "none" entries. i don't know what those are.

```
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             133G   51G   76G  41% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  216K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  168K  1.5G   1% /dev
tmpfs                 1.5G     0  1.5G   0% /dev/shm
lrm                   1.5G  2.5M  1.5G   1% /lib/modules/2.6.28-18-generic/volatile

```

---

### Post by Loki57701 on 2010-05-24
Yes, I was referring to the 'none' entries. On other systems I get something closer to what neil.m.master shows. If other people have the same results and are having no problems, than I suppose it's nothing. I was just curious, thanks for the replies everyone.

---

### Post by .nedberg on 2010-05-24
Well, I have similar resulta. But I would still want to know what it is…

---

### Post by ian dobson on 2010-05-24
Hi,

The none entries are nothing to worry about. They are pseudo  file systems (device file system mounted on /dev).

Regards
Ian Dobson

---

