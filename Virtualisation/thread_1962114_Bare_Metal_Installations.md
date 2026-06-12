---
title: "Bare Metal Installations"
date: 2012-04-20
forum: Virtualisation
---

### Post by ptmuldoon on 2012-04-20
I'm looking for the best, easiest solution in getting started with virtualization and to help in performing the following.

I currently have a working machine at home running Ubuntu Server being used primarily as a NAS to store media.  It has a Raid5 setup on it with mdadm.

I'm considering either 
1. XEN XCP - [http://www.xen.org/products/cloudxen.html](http://www.xen.org/products/cloudxen.html)
2. Citrix XenServer - [http://www.citrix.com/English/ps2/products/product.asp?contentID=683148](http://www.citrix.com/English/ps2/products/product.asp?contentID=683148)
3.  VmWare Hypervisor - [https://my.vmware.com/web/vmware/evalcenter?p=free-esxi5&lp=default](https://my.vmware.com/web/vmware/evalcenter?p=free-esxi5&lp=default)


First.  Any recommendation of one over the other, and reasons for choosing it over the others?  

And with any the above 3 options, can I do the following?

1.  Install the Bare Metal System
2.  Create a VM for Ubuntu Server, and rebuild the array?
3.  Than also install Windows, and some other OS
4.  Can you remote manage into the host to manage the VM's.
5.  Can you remote manage/connect into each VM on its own as well?

I was reading that VMWare Hypervisor does not support software raid.  So that does mean the Virtual Machines with VMware can also not use software raid?

I also think I should be able to use clonezilla to copy my existing Ubuntu Server setup to move onto a VM?  This OS is currently on a separate drive from my media.

Again, I'm a newbie to virtualization.  I have most of my parts now ready for the build, and hope to start next week.

---

### Post by CharlesA on 2012-04-20
I'd go for Xen myself, but ESXi works wonders too.

XenServer is around a grand to buy after the trial is over, so unless you want to spend a ton of money on a virtualization solution, that might not be the best way to go.

The host software doesn't care how the guests are configured, you can use Software RAID on the guest and it would run fine.

EDIT: Those three hypervisors are enterprise grade, so the learning curve may be a bit high.

Sidenote: I am running Ubuntu server as my NAS and VM host using VirtualBox.

If you don't want to reinstall the whole thing, you might want to look into KVM as well.

---

### Post by ptmuldoon on 2012-04-20
Thanks for the fast response.  It was my understanding that Citrix XenServer offered both a free and paid version.  This is for home use only, so I'm not going to shell out a ton of money just to learn. This is from the Citrix Website:

> The free edition of XenServer starts with a 64-bit hypervisor and centralized management, live migration, and conversion tools to create a virtual platform that maximizes guest density and performance. The premium editions of XenServer extend the platform to enable organizations of any size to integrate and automate management processes, delivering a virtual datacenter solution.  

I don't mind the learn curve though. I may start out by giving Xen a try first, but I think ESXi may be the easier to get an up running faster.

---

### Post by dcstar on 2012-04-24
> **ptmuldoon said:**
> 
..........
I don't mind the learn curve though. I may start out by giving Xen a try first, but I think ESXi may be the easier to get an up running faster.

I use ESXi professionally and its major handicap in the Linux world is that it **only** has a Windows management tool.

If you can live with this, the VMs you run after setting them up will work quite efficiently.

---

