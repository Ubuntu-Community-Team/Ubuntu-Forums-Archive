---
title: "hybrid data storage (SATA + SSD)"
date: 2007-12-13
forum: The Cafe
---

### Post by tehet on 2007-12-13
Hi, here's just a silly idea.
SSD is said to be much faster than traditional hard drives. You can get a 8GB SSD express card for ~50 EUR, which isn't exactly cheap but affordable. However, SSD can sustain unlimited reads, but a limited number of writes before it wears out. So, suppose you'd get a 8GB SSD express card for the OS and a nice big SATAII disk for the rest partitioned as follows

SATA or whatever traditional drive:
/var
/proc
/swap
/home
edit: /dev as well perhaps because device nodes are created at boot (right?).

SSD:
the rest, mounted with noatime, nodiratime, so there is hardly ever written to the SSD. (Or are there more services that write to / ?)

Would that do anything for performance? I've heard about a file system especially designed for flash memory in embedded devices. Would that be better that ext3 for instance?

---

