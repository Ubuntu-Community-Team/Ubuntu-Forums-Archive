---
title: "Yikes! 8.04LTS can't connect to virsh or start VMs"
date: 2009-09-18
forum: Virtualisation
---

### Post by cleentrax on 2009-09-18
I rebooted my 8.04LTS server for a kernel update, and when it restarted, two of my VMs failed to autostart.

I cannot connect to virsh, and restarting the libvirtd times out connecting to console.

Strangely, two of my four VMs are still live.

All four of the VMs are production web servers. The two that won't start have 8.04server installed. The two that will start have 9.04server installed. Coincidence? I don't know.

Any ideas? Which logs should I look at? 

I'm trying a Distribution Upgrade to 8.10 for the host right now, but it's taking hours.

---

### Post by cleentrax on 2009-09-18
Updated to 8.10. Rebooted and now I can connect to virsh but I cannot start the two machines: "libvir: QEMU error : internal error Timed out while reading console startup output"

---

### Post by cleentrax on 2009-09-18
Problem Solved. Launchpad bug #344400.
[https://bugs.launchpad.net/bugs/344400](https://bugs.launchpad.net/bugs/344400)

workaround is to launch the VMs manually: in descending order from largest to smallest.

---

