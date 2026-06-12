---
title: "Ubuntu desktop on Ubuntu server 19.04 crash on virtual machine over hyper-V"
date: 2019-05-09
forum: Virtualisation
---

### Post by plhmk on 2019-05-09
Hello,
I tried to install Ubuntu 19.04 server on Windows 2016 server with Hyper-V .
The installation works well without problems with the character interface.
If I try to install the Ubuntu desktop with the command
sudo apt-get install ubuntu-desktop
the installation proceeds correctly until the reboot but then everything stops with a black screen and a flashing cursor, the only possibility is to turn off the virtual machine.:(
The same operation done instead with Ubuntu 18.04 works correctly and I have the desktop running on the virtual machine.:D
The same operation with 19.04 done on VMWare ESXi leads to a working system but with a generic "system error" that is repeated every time the machine is started, but without apparent consequences.:o
Any suggestions for Hyper-v?
Thank you
Regards

---

### Post by TheFu on 2019-05-09
Servers should always be LTS releases. Non-LTS versions should only be installed if bleeding edge hardware demands - - DEMANDS - it.

As for loading any GUI onto a server, it isn't a best practice. People do it, but that doesn't mean it is a good idea.

When you check the log files, anything inside? Reads like it is a video driver issue. Perhaps try using a different video driver?  I know that SPICE and QXL work great since 16.04 inside VMs, but I don't know anything about non-LTS releases nor using those drivers with non-Linux-based hypervisors.  We don't touch either.

Can't say anything about Hyper-v - never use it and we dropped VMware-everything in 2011.

---

### Post by plhmk on 2019-05-16
Hello, thanks.
Can be a video driver issue, i use in the server an nVidia GPU (GTX 970), but i will use LTS for now.
For me is better use GUI on server, is easy and is a test server, no problem.
Why is Hyper-V not recommended and VMWare abandoned since 2011?
They should be compatible, otherwise how do I virtualize?
Regards

---

### Post by TheFu on 2019-05-16
> **plhmk said:**
>  
Why is Hyper-V not recommended and VMWare abandoned since 2011?
They should be compatible, otherwise how do I virtualize?
Regards

Who said "not recommended?"  No me.
I said we have never touched Hyper-V and stopped using VMWare in 2011.  The reasons are fairly well understood by former customers at the time.  VMware decided to fire many of their customers by altering the pricing to levels that just weren't reasonable.

We use KVM for all virtualization. Started using it in 2010 and VMware forced us to move faster than expected, but we've never regretted it.  KVM is the fastest of the HVM hypervisors, while still being the most flexible and most stable.
Prior to switching to KVM, we used Xen and ESXi on our production systems.  Before that we used virtualbox for toy systems and VMware Workstation and VMware Server going back into the 1990s.  On other Unix platforms, we used the native hypervisors - LPARS on AIX, nPars on HP-UX, "Containers" and Domains on Solaris using both hardware partitioning and just the software stuff.

Unless you have a very strong, specific, need, I'd push for a new setup to use KVM as the hypervisor.

---

