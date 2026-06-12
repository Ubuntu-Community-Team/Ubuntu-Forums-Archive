---
title: "ESXi Ubuntu 16.04 guests hang intermittently"
date: 2017-05-04
forum: Virtualisation
---

### Post by cmbuck on 2017-05-04
Hi all, I am requesting assistance troubleshooting/debugging unresponsive 16.04 guests on an ESXi host.

**The problem**:
I have an Ubuntu 16.04 Server and an Ubuntu 16.04 Desktop guest on an ESXi 6.5 server.  I was able to successfully install each of them, however they now hang and go completely unresponsive when I try to use them.  For the Desktop guest, it freezes within a minute or two of booting and displaying the login screen.  For the Server, it now appears to last 12-24 hours before it hangs.  Clearly, the issue appears to affect both guests, but at different speeds.  When the VMs freeze, they are completely unresponsive to the ESXi console, SSH, or any other program as far as I can tell.  Additionally, according to ESXi, it appears the Server guest (which is frozen and unresponsive right now) is utilizing one full processor core at 100%, and says 100% of the RAM I have allocated is "consumed", yet 0% of the RAM is "active".

**What have I tried**:
[LIST]
[*]Virtualizing other Operating Systems on the host -The ESXi host is also successfully running two FreeBSD guests which are operating without issue, so it is not the case that the host cannot virtualize anything.
[*]Memory test on the Host RAM - I've ran memtest on the bare metal host for 3 passes with no memory errors.
[*]REISUB as explained [here]("https://askubuntu.com/questions/4408/what-should-i-do-when-ubuntu-freezes/36717#36717") - This does not do anything unfortunately
[*]Adding [FONT=courier new]intel_idle.max_cstate=1[/FONT] into my grub file as explained [here]("https://askubuntu.com/a/803649").  This also doesn't fix the hanging
[/LIST]

**Specifications**:
[LIST]
[*]Host: Xeon E-1230 quad core
[*]Host: 32 GB ECC RAM
[*]Host: SSD for the ESXi datastore used for the Ubuntu guest OS disks
[*]Host: Supermicro Motherboard
[*]Guest Server: 4 GB RAM, 4 cores, 32 GB storage.
[*]Guest Desktop: 4 GB RAM, 4 cores, 16 GB storage.
[/LIST]


Would anyone be willing to share some guidance on debugging or resolving this issue?  Thanks!

---

