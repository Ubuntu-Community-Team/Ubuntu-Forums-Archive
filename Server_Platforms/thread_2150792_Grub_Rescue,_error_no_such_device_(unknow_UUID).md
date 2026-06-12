---
title: "Grub Rescue, error: no such device: (unknow UUID)"
date: 2013-06-02
forum: Server Platforms
---

### Post by jpaytoncfd on 2013-06-02
I installed a new motherboard last night and can not boot. 

Grub comes up with no such device. The UUID it lists does not match any drives or partitions I have or have had. The grub.cfg lists all the proper UUIDs and does not list the one it states is missing. I have tried grub-update, grub-install --recheck, etc. Nothing seems to be working. and I can not find this UUID listed anywhere so I do not know where GRUB is getting it. Fstab only has one UUID and it is correct. 

Any ideas would be greatly appreciated.

---

### Post by jpaytoncfd on 2013-06-02
I have now tried reinstalling from scratch and still have the same error.

---

### Post by jpaytoncfd on 2013-06-02
Problem solved, The BIOS was set to emulate the sata drives as IDE. Grub saw sata drives and got confused when the emulated IDE was different

---

### Post by Stuart_Conner on 2013-10-05
> **jpaytoncfd said:**
> Problem solved, The BIOS was set to emulate the sata drives as IDE. Grub saw sata drives and got confused when the emulated IDE was different

So all you did to fix this was change a bios setting dealing with sata/ide drives?
Please elaborate.

---

