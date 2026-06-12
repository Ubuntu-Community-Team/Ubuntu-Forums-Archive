---
title: "VMware Server host network works by not guest"
date: 2007-12-01
forum: Virtualisation
---

### Post by dborko on 2007-12-01
Am using a laptop have Gusty installed with VMWARE Server.  Trying to install XP Guest.  The Newtorking both wirless and wired do work on the host side, but the guest side will not work.  Show uo as eth0 and eth1.  Guest balks says dev/v????0 not working.

Any ideas

---

### Post by Delvien on 2007-12-02
> **dborko said:**
> Am using a laptop have Gusty installed with VMWARE Server.  Trying to install XP Guest.  The Newtorking both wirless and wired do work on the host side, but the guest side will not work.  Show uo as eth0 and eth1.  Guest balks says dev/v????0 not working.

Any ideas

what vmnet was chosen when you were configuring? 

Mine is vmnet2, the automatic bridged for some reason doesnt pick up all the time. So chose the right subnet and should be right as rain afterwards.

---

