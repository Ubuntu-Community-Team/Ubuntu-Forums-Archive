---
title: "Did a upgrade of the kernel."
date: 2012-03-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Ryssen on 2012-03-20
From 11.10 to 12.04 and now when trying to update the system I get a message that the boot folder is full. and the command "sudo apt-get clean" aint working.
So what to do,Is there a way of manualy cleaning the folder?

---

### Post by wojox on 2012-03-20
Probably need to remove some old kernels. Which one's ?

```
ls -lah /boot
```

---

### Post by ajgreeny on 2012-03-20
Do you have a separate /boot partition, and if so why do you bother?  It generally causes more problems than it solves.

The command ```
grep menuentry /boot/grub/grub.cfg
``` will show you exactly what kernels are listed in your grub menu, and how many kernels you have.  You can then remove the unwanted ones (all except the last two) with *software-centre*, *synaptic* or *apt-get remove*

---

### Post by Elfy on 2012-03-21
*Thread moved to **Ubuntu +1 (Precise Pangolin)**.*

---

### Post by Ryssen on 2012-03-22
Hmm,I had to reinstall ubuntu so that sorted the problem..
Thanks anyway!

---

