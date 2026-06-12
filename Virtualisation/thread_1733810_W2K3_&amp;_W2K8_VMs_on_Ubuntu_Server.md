---
title: "W2K3 &amp; W2K8 VMs on Ubuntu Server"
date: 2011-04-19
forum: Virtualisation
---

### Post by bgreenaway on 2011-04-19
Investigating using VMs on Ubuntu Server to run Windows 2003 Server running file and print services with a few small applications and Windows 2008 Server running SQL Server 2008. 

Anyone got any recommendations for best choice of VM?

---

### Post by joberly on 2011-04-19
People swear by KVM. I myself use VirtualBox. Does your hardware support VTx or AMD-V ?

---

### Post by bgreenaway on 2011-04-19
Thanks Joberly. Yet to get the hardware, but it will support both. 

I use VirtualBox a lot, but just for Windows XP and Win 7 VMs. Is it robust and reliable enough to run the OSes?

---

### Post by robots.jpg on 2011-04-20
Will the Ubuntu server be doing anything other than hosting the VMs?  If  not, it would probably make sense go with a hypervisor like VMware ESXi  or KVM instead.  Not to steer you away from using Ubuntu or anything --  they will just make much better use of the resources available to them,  and there's no reason you couldn't throw an Ubuntu Server VM on there  as well.

I haven't tried KVM personally, but I've found ESXi to be extremely reliable.

---

### Post by bgreenaway on 2011-04-20
No, the Ubuntu host server will not be doing anything else other than hosting the VMs.

---

### Post by TheR on 2011-04-20
I am running 3 windows 2k3 and one 2k8 server on 10.04 KVM and they run like charm. DC and file server, web server, avir management and sql 2k8  server, fax and time register server. Sitting on 4Core i7 3gHz. Mostly still doing nothing ;-)

Disks are on iSCSI 10g Ethernet switch. 4 raptors raid 10. hdtach shows speed between 120&150GB. If you use local disk I would suggest using lvm or raw partitions for disk intensive machines. Other can easly live inside qcow file.

by
TheR

---

