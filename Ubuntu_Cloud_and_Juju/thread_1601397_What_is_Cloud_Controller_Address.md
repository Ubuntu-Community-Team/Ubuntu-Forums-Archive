---
title: "What is Cloud Controller Address"
date: 2010-10-20
forum: Ubuntu Cloud and Juju
---

### Post by satimis on 2010-10-20
Hi folks,

Ubuntu 1010-1 server edition, 64-bits

I follow;
Private cloud  Deploy 
[http://www.ubuntu.com/cloud/private/deploy](http://www.ubuntu.com/cloud/private/deploy)

installing Private Enterprise Cloud.

Coming to;```

Cloud Controller Address

```

whether it is the IP address of this "cloud"(box)?  Public IP address OR router IP address?  TIA

B.R.
satimis

---

### Post by kim0 on 2010-10-20
Hey :) You're probably better off following this more detailed guide
[https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall)

---

### Post by Rusty au Lait on 2010-10-20
If you configuration requirements demand that you put your CC (Cluster Controller) on a different machine that the CLC (Cloud controller) you will have a different IP address than the CLC. It is asking for your 'machines' IP address, not an instance IP address.

---

### Post by satimis on 2010-10-21
> **kim0 said:**
> Hey :) You're probably better off following this more detailed guide
[https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall)

Hi,

Thanks for you URL.

This is my first attempt installing Ubuntu Private Enterprise Cloud.  I don't have any previous experience.  Also I don't have several physical machines (PCs).  Therefore I'm prepared to perform this test on the VMs of a Oracle VirtualBox.  The setup planned by me is as follows;


VirtualBox (PC)
AMD Phenon X4
RAM 8G
HD 1T (WD Black series, 64M buffer)

host - Ubuntu 1010 desktop 64-bit
virtualizer - Oracle VBox version 3.2.10 r66523

CD - Ubuntu 1010 server 64-bit


1)
Install a front end on a VM, say VM-1.  Size=200G


2)
Clone a VM, say VM-2, on VM-1, to be run as node

(remark: I'll try to reduce the image size to 100G on cloning.  If failure I'll install VM-2 from the CD)


I don't know whether my plan can work OR not.  Please shed me some light.  TIA


B.R.
satimis

---

### Post by satimis on 2010-10-21
> **Rusty au Lait said:**
> If you configuration requirements demand that you put your CC (Cluster Controller) on a different machine that the CLC (Cloud controller) you will have a different IP address that the CLC. It is asking for your 'machines' IP address, not an instance IP address.

Hi

Advice noted.  Thanks

B.R.
satimis

---

### Post by kim0 on 2010-10-22
You may be interested in my post on how to run UEC on an EC2 instance (which is already a VM, just like running on VirtualBox)

[http://foss-boss.blogspot.com/2010/10/cloud-on-cloud-uec-on-ec2.html](http://foss-boss.blogspot.com/2010/10/cloud-on-cloud-uec-on-ec2.html)

---

