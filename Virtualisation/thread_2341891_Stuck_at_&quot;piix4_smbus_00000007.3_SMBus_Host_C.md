---
title: "Stuck at &quot;piix4_smbus 0000:00:07.3: SMBus Host Controller not enabled!&quot; message on vm"
date: 2016-11-01
forum: Virtualisation
---

### Post by tech-gamer on 2016-11-01
I am using VMware workstation 12 to run ubuntu 16.10 with 1 processors and 2GB of ram. When I boot I always stuck with black screen
with

```
[    1.934876] sd 2:0:0:0: [sda] Assuming drive cache: write through
/dev/sda1: recovering journal
/dev/sda1: clean. 186347/1179648 files, 1246549/471592 blocks
piix4_smbus 0000:00:07.3: SMBus Host Controller not enabled!
```


solved!!
removing "quiet splash" from grub fix!

---

### Post by QIII on 2016-11-01
Moved to Virtualisation.

---

### Post by tech-gamer on 2016-11-02
this error is driving me CRAZY!!

---

### Post by tech-gamer on 2016-11-02
solved! removing "quiet splash"on grub fix it!

---

