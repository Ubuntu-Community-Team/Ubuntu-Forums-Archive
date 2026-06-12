---
title: "Access Ubuntu server guest vm from Ubuntu server host"
date: 2010-07-01
forum: Virtualisation
---

### Post by ryanrad on 2010-07-01
I need a little help and feel like I'm missing something completely trivial.  I just finished installation of an Ubuntu guest server on an Ubuntu host vm using kvm.  I know the guest is running...
```
virsh # list --all
Id Name                 State
----------------------------------
  1 cloop-staging        running
```
Now how do access it?

---

### Post by ryanrad on 2010-07-02
Installed virt-manager and virt-viewer on local machine.  Used remote connection to host and was able to connect to guest.

---

