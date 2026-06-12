---
title: "VirtualBox, 2 Core/CPU support?"
date: 2007-10-29
forum: Virtualisation
---

### Post by netegalkaka on 2007-10-29
Hi all,

I'd like to know if future relesase of VirtualBox would support 2core or 2 cpu in virtual machines.

Currently when i look at the task manager of my virtual Vista, it only shows me 1cpu instead of 2.

Many thanks.

---

### Post by Delvien on 2007-11-07
> **netegalkaka said:**
> Hi all,

I'd like to know if future relesase of VirtualBox would support 2core or 2 cpu in virtual machines.

Currently when i look at the task manager of my virtual Vista, it only shows me 1cpu instead of 2.

Many thanks.

It doesnt need it, It pulls processing from both cores as it should, your VM will only show 1 CPU, but its better this way. (one app) 

If you are comparing it to VMware, the 2 processor option actually slows down the VM.

---

### Post by nutz on 2007-11-07
He is right; vbox acts like it is a single threaded process. Even under maximum usage in the VM it never uses more than 1 cpu core on the host system. Same setup, Ubuntu host and Media Center client...

---

