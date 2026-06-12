---
title: "Shutdown/Reboot Problem after Upgrading Kernel (10.04 LTS within Xen domU)"
date: 2010-12-28
forum: Virtualisation
---

### Post by hansbickhofe on 2010-12-28
Hi all.
After upgrading our domU Ubuntu 10.04.1-LTS Install's from kernel-2.6.32-24-server to kernel-2.6.32-27-server
there's a Problem shuting down or rebooting these VM's. 
The VM shut's down and at the end I can see:

* Will now restart
[ 43.112639] Restarting system. 

But thats all.
Only a forced shutdown or reboot will help.
When we change the Kernel to the previous Version, everythings fine.
Any hints?

Xen dom0:
A Pool of two XenServer 5.6.0 with Hotfix 1/2/4 applied.
The SR for the VM Images is a DRBD Device.
Thanks for your time and help!

Regards, Hans Bickhofe

---

### Post by LagoniX on 2010-12-28
Hi Hans,

You are not alone with this issue. 
I having the same problem but I don't have the time to run though all the changes made in the new kernel.

FYI, I have created a bug on this in launchpad, so if you have anything to add, feel free to do it. [Link]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/695012")

BR.
Brian

---

### Post by hansbickhofe on 2010-12-29
Hi Brian.
Thanks for your answer. If I find something new to this I'll add it.

Regards, Hans

---

### Post by pepoluan on 2011-01-22
I have the same problem, too. I thought I made a mistake during paravirtualization, but it appears I didn't.

---

