---
title: "Pleae help. sun blade 100."
date: 2008-01-07
forum: Sun Sparc Users
---

### Post by maxbg on 2008-01-07
i've insatlled ubuntu desktop 7.1o without problems (install video=atyfb:1024x768@60 ide=nodma).

at OK prompt i'm not able to get SILO prompt (boot disk0:a or disk0:c o disk0:1 or disk0:3): i always get "The file just loaded doen not appear ti be executable").

Output of devalias:
  disk0 /pci@1f,0/ide@d/disk0,0

Output of probe-ide

  device 0 (primary master)
  ata model: maxtor6E040L0

  device 1
  removable atapi

  device 2
  ata model: maxtor 6L040J2

---

### Post by zanderred on 2008-01-13
Hi maxbg, have a look at  [http://dlc.sun.com/pdf/806-6637-12/806-6637-12.pdf](http://dlc.sun.com/pdf/806-6637-12/806-6637-12.pdf)  - Jan 8, 2002
 hope this helps.

---

### Post by maxbg on 2008-01-14
Problem solved.

The error was in disk geometry.

---

