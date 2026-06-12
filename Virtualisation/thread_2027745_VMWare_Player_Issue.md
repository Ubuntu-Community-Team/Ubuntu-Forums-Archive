---
title: "VMWare Player Issue"
date: 2012-07-16
forum: Virtualisation
---

### Post by beats4u on 2012-07-16
I have a simple network setup with three win 7 machines and one mint 12 desktop all sharing files fine.  I just set up a precise 64 bit vm on one of the win 7 machines with vmware player 4.  I can access shares on the new precise vm from my mint 12 machine and fom the win 7 host but I get prompted for a username and password from the other win 7 machines and no credentials work.  Shares are set for guest access.  Precise was originally installed with nat enabled on the vm nic but I changed it to bridged and am pulling an ip from the proper subnet range. I can ping the vm from the two machines and can access it via rdp.  Help.

---

### Post by dcstar on 2012-07-24
> **beats4u said:**
> I have a simple network setup with three win 7 machines and one mint 12 desktop all sharing files fine.  I just set up a precise 64 bit vm on one of the win 7 machines with vmware player 4.  I can access shares on the new precise vm from my mint 12 machine and from the win 7 host but I get prompted for a username and password from the other win 7 machines and no credentials work.  Shares are set for guest access.  Precise was originally installed with nat enabled on the vm nic but I changed it to bridged and am pulling an ip from the proper subnet range. I can ping the vm from the two machines and can access it via rdp.  Help.

This will have nothing to do with the VM environment if the basic bridged networking is functional.

Check the Network or General forums for similar access issues, or more likely look in a Windows forum and find out how to fix the Firewall on the Win 7 host.

---

