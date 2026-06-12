---
title: "Quick Question"
date: 2007-03-10
forum: The Cafe
---

### Post by penguinchrissy on 2007-03-10
I was wondering if anyone knows if its possible to access my harddrive files through a VM. I have a VM running windows and I want to edit some song files using a windows only program that doesn't run in wine.

---

### Post by SeanTater on 2007-03-10
VM as in VMware -- never used it, sorry. However, if you mean qemu, look at the qemu man page. I think you might want --> qemu -hda / <-- But I have not used it in a while..

---

### Post by SishGupta on 2007-03-10
If you are using vmware server you can add devices and I think this way you can add hard drives.

In vmware player adding devices is harder.

For sure I know that you can access network shares through vmware and that would be just as effective. It is how I would access hard drives in vmware back when I used vmware.

---

### Post by runningwithscissors on 2007-03-10
Qemu supports SMB. You can set up an Samba server on your machine that can make any number of shares available to the VM. The default network address of the host machine inside of QEMU is 10.0.2.2

VMWare must have something similar or support for NFS. I haven't used it.

---

