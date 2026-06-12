---
title: "Virtual Machine Migration"
date: 2011-09-23
forum: Security
---

### Post by Archers on 2011-09-23
Hi,

I want to migrate a Virtual Box software to another computer which  running on Ubuntu or Windows. Is that possible to do that migration when virtual machine is running. ...I meant without shutting down the virtual machine.

I am searching for solution to this problem. Please any of them help me out 

Thanks in advance

---

### Post by e79 on 2011-09-23
> **Archers said:**
> Hi,

I want to migrate a Virtual Box software to another computer which  running on Ubuntu or Windows. Is that possible to do that migration when virtual machine is running. ...I meant without shutting down the virtual machine.

I am searching for solution to this problem. Please any of them help me out 

Thanks in advance

As far as I know you cannot, unless you are running a VMware product called [VSphere]("http://www.vmware.com/products/vmotion/overview.html") (which is a barebone Hypervisor to run multiple virtual machines). Live migration of virtual machines are not part of home use virtualization products.

Hope this answer your question

---

### Post by Archers on 2011-09-23
okay if I use Vsphere it is possible to migrate lively from one host to another host

---

### Post by CharlesA on 2011-09-24
Try this:

save VM, > copy VirtualBox VMs folder to other host, start VMs.

---

