---
title: "No network after install on VMware ESXi"
date: 2012-08-23
forum: Virtualisation
---

### Post by rblumenthal on 2012-08-23
I have a VMware ESXi host where I created a new virtual machine to install the latest version of Ubuntu. Install went through fine, but I have no network connection at all. I tried the 3 options for network adapter that I had (E1000, VMXNET 3, and Flexible). I am at a loss at the moment. Any insight on where to look would be appreciated.

Thanks

---

### Post by dcstar on 2012-08-30
> **rblumenthal said:**
> I have a VMware ESXi host where I created a new virtual machine to install the latest version of Ubuntu. Install went through fine, but I have no network connection at all. I tried the 3 options for network adapter that I had (E1000, VMXNET 3, and Flexible). I am at a loss at the moment. Any insight on where to look would be appreciated.


You first verify the networking on the ESXi host by setting up the host NTP server and making sure it works. You then ensure that the VM networking is actually using the host ESXi networking resources.

---

