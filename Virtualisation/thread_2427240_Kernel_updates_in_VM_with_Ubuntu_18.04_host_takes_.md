---
title: "Kernel updates in VM with Ubuntu 18.04 host takes very very long time"
date: 2019-09-19
forum: Virtualisation
---

### Post by antarex882 on 2019-09-19
I noticed that updating the kernel with the Software Updater takes very long time.
The situation is the following.
I am running three different VMs in VirtualBox: Ubuntu 16.04, Ubuntu Budgie 18.04 and Ubuntu 19.04.
The host machine has been running Ubuntu Budgie 18.04 with the original kernel 4.15 for more than a year without issues.
I recently had to reinstall the host machine due to HW failure. I reinstalled using Ubuntu Budgie 18.04.3 and noticed that the kernel is now 5.0.0.x (with HWE).
Now it takes extremely amount of time to update the kernels in the guest VMs.
Obviously this has something to do with the host running 5.0.0.x but how can this be? How can it affect the time it takes to update the kernels in the Virtual machines?

The guest - Ubuntu Budgie 18.04 - updated from 5.0.0.27 to 5.0.0.29 in 2 minutes on a Windows 10 host.
On my Ubuntu Budgie 18.04 host (Intel i5-3570K) the same update took 32 minutes!
I have noticed the same problem with all VMs (guest systems Ubuntu 16.04, Ubuntu Budgie 18.04 and Ubuntu 19.04).
Ubuntu 16.04 is running kernel 4.15.
Would appreciate any suggestion how to solve this issue. If I can't solve it I have to use the Windows host for instead which I do not like :-).

VirtualBox version is 6.0.10.

---

### Post by deadflowr on 2019-09-19
*Thread moved to **Virtualization** *

---

### Post by lammert-nijhof on 2019-09-21
Strange! I use the same Linux version 5.0.0-29 on my hosts (Ryzen 3 2200G and an i5-2520m) and have no problems with my VMs Ubuntu 16.04; 19.04, Ubuntu Mate, Xubuntu, Windows 7 and 10 and some others. 
I use Virtualbox 6.0.12, but also with 6.0.10 everything was fine.  
I assume you installed Virtualbox Extension Pack again and it is 6.0.10 too.
Did you try re-installing Virtualbox Guest Additions in a Guest? And do  it on the Linux Host to avoid any Windows interference, however unlikely

---

### Post by antarex882 on 2019-09-30
Yes I have tried reinstalling the Virtualbox Guest Additions but it did not solve the issue.
However, I have found a possible solution.

The suggested solution as suggested by "S. Christian Collins" in this thread (refer to comment #34) would be to turn "Use Host I/O Cache" on for the SATA controller.:
[https://bugs.launchpad.net/dpkg/+bug/947664](https://bugs.launchpad.net/dpkg/+bug/947664)

I  also found the following blog post on this subject why activating this  option might be a good idea (and also why it is not by default):
[https://www.electricmonk.nl/log/2016/03/14/terrible-virtualbox-disk-performance]("https://www.electricmonk.nl/log/2016/03/14/terrible-virtualbox-disk-performance")

*Note: The computer is a pure Ubuntu Budgie installation. I don't run Windows or anything else on this computer (except Linux).*

---

