---
title: "Error Decoding failed -- System halted with 20.04 on VirtualBox"
date: 2020-04-30
forum: Virtualisation
---

### Post by spammymcfilterson on 2020-04-30
I run the initial installation and the system starts. But if I restart or if it goes to sleep after a long idle period, it locks up completely, requiring a hard reset.  From that point on, all I get is this: Decoding failed  -- System halted.   I've done a lot of searching and cannot find any other reports of this exact situation with Ubuntu 20.04 and I'm guessing this may be a new issue.  This happened with Using VirtualBox Version 6.0, but continues to happen after upgrading to Version 6.1.6 r137129 (Qt5.6.2) I've created new VMs each time. The VM is configured with 4vcpus, 4gb ram, and a 60 gb disk.   My platform is WIndows 10 Pro, with an AMD Ryzen 9 3900x running stock on an Asus MB.  Any suggestions?

---

### Post by christian-pasti on 2020-06-11
> **spammymcfilterson said:**
> I run the initial installation and the system starts. But if I restart or if it goes to sleep after a long idle period, it locks up completely, requiring a hard reset.  From that point on, all I get is this: Decoding failed  -- System halted.   I've done a lot of searching and cannot find any other reports of this exact situation with Ubuntu 20.04 and I'm guessing this may be a new issue.  This happened with Using VirtualBox Version 6.0, but continues to happen after upgrading to Version 6.1.6 r137129 (Qt5.6.2) I've created new VMs each time. The VM is configured with 4vcpus, 4gb ram, and a 60 gb disk.   My platform is WIndows 10 Pro, with an AMD Ryzen 9 3900x running stock on an Asus MB.  Any suggestions?

Hi, I was wondering if you found out the problem. In my organization we are experiencing the same problem, I could solve it running the VM again (it didn't show that error the second time), then choosing a different Kernel version to boot from.

---

