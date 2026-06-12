---
title: "VM slowness, locking"
date: 2012-09-19
forum: Virtualisation
---

### Post by deesto on 2012-09-19
Despite having Natty installed on a decent system (8 GB RAM, Core 2 Duo 3.33GHz w/vmx), I have trouble running *any* guest OS inside a VM.  When installing an OS (like Precise). I give the VM a CPU and 1 or 2 GBs of memory, use unallocated qcow2 disk, and I've tried different disk cache settings. Installation starts ok and goes slowly, until the system starts doing something, like writing to disk, and then the VM will lock up for a few seconds, sometimes tens of seconds.  This happens almost every time I do anything within the VM, such as running an update.  I sometimes lose the mouse pointer too, which comes back eventually after the lockup.  On the host OS, memory never moves, and CPU usage rarely goes over 50% (or 100% of the assigned CPU).  In the guest, memory stays just over 50%, CPU reportedly stays around 10% but spikes during activity.  I can tell something strange is going on by watching the virt-manager host details overview (Edit -> Connection Details -> Overview), where the CPU Usage graph also seems to lock up and jump between readouts, along with the VM.  I wouldn't expect this to happen on the host OS, since I don't see slowness within the host otherwise, but it does.  Maybe this indicates a disk I/O problem?

---

