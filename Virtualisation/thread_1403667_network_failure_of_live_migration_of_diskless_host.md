---
title: "network failure of live migration of diskless hosts on KVM"
date: 2010-02-10
forum: Virtualisation
---

### Post by agshekeloh on 2010-02-10
Hi,

I have a group of diskless Ubuntu 9.10 x86-64 hosts running KVM and OpenNebula 1.4.  Virtual machines are also running diskless.  Each server has a NIC for management and a separate NIC for diskless VMs, set up as a bridge.  The NFS server is an OpenSolaris 2009.06 machine.

I can run virtual machines either through KVM directly or through OpenNebula, and they work fine.  When I do a live migration to another server through either virsh or onevm, the virtual machine becomes nonresponsive.  I cannot ping the virtual machine.  VNCing to the console works, and I see the VM's text console, but the VM doesn't answer the keyboard.

On the network side, other machines lose arp to the VM IP address.  Using TCPdump on the bridge's underlying interface, I can see arp who-has requests for the VM IP, but the host running the VM does not respond.  This occurs with both Ubuntu and FreeBSD VMs.  To my untutored eye, it appears that the VMs don't connect to the bridge after a live migration.

Any suggestions, folks?

Thanks,
==ml

---

### Post by ortayus on 2010-05-14
Its too bad there is no reply because I have the same issue with migrating Ubuntu.

---

### Post by RootsDog on 2010-07-22
Same problem here ...
After trying 'zillions of tips from the net (to no avail),
I wonder if *anybody* actually succeded in setting
up a working and reliable configuration with brigded
networking which supports live migration via virsh.

Anybody ? 

Regards,

---

