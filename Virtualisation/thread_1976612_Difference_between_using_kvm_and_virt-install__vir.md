---
title: "Difference between using kvm and virt-install / virt-manager"
date: 2012-05-09
forum: Virtualisation
---

### Post by lostinspace2011 on 2012-05-09
I am trying to get windows running as a guest OS. So far I have managed to use

```
kvm -m 512 -cdrom windows-vista.iso -boot d vista.img
``` 

successfully. However from what I gather online it is better to use the virt-install tool set. If I understand this correctly using virt-install / virt-manager will make use of hardware features while running the command above will use emulation.

Is this correct ? What other differences are there ?

---

