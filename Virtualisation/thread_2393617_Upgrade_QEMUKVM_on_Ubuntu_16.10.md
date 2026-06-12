---
title: "Upgrade QEMU/KVM on Ubuntu 16.10"
date: 2018-06-05
forum: Virtualisation
---

### Post by khap on 2018-06-05
Hi Folks,


I am hoping this is the correct forum on which to introduce my question as I am new to Ubuntu/linux world... and KVM Hypervisor.


I am looking at upgrading the current version of KVM virtualisation tool which we use to create a small number of VMs including our Vsphere 6.0 server so as it is independent of our ESX farm. 


The upgrade is necessary to mitigate some recent security vulnerabilities.


I am wondering what companion apps I have to upgrade at the same time as I upgrade KVM? I'm thinking about the virt tools (virt-manager etc), virsh. 
Does QEMU need to be upgraded independently as well? Or does it get updated when KVM is installed. 


Does anyone have a plan of what they did when they have recently upgraded KVM that they could forward to me?


The underlying Server hardware is Cisco UCS C220m4 (Standalone) - Ubuntu 16.10 (see attachment)


Thanks in advance

---

### Post by QIII on 2018-06-05
If you are concerned about security, your first step should be to stop using 16.10 and move to a supported release.  16.10 is past its End Of Life and is no longer supported nor secure.  It no longer receives updates -- not even security updates.

---

### Post by #&amp;thj^% on 2018-06-05
Respectfully you are aware that yakkety 16.10 is past EOL right?
Maybe better to go with an LTS version like 16.04 or newly added to the LTS 18.04 with 5 years of support.
Ninja'd  by QIII BTW 16.04 is still in support 16.10 is not though. :p

---

### Post by QIII on 2018-06-05
I edited my typo.

Derp!  Time for me to take a nap?

---

### Post by khap on 2018-06-05
Thnx for swift replies. 

No I was not aware that 16.10 was EOL as I said am new to this. I will investigate upgrading 16.10 to a supported version of Ubuntu. And then upgrading KVM tool. 

Thnx again.

---

### Post by #&amp;thj^% on 2018-06-05
Welcome here is a guide to view for your choice making: [https://www.ubuntu.com/info/release-end-of-life](https://www.ubuntu.com/info/release-end-of-life)

---

