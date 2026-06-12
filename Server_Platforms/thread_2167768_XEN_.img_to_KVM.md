---
title: "XEN .img to KVM"
date: 2013-08-14
forum: Server Platforms
---

### Post by nerdtron on 2013-08-14
I have some .img files previously used as XEN images in CentOS which I would like to use now with KVM in Ubuntu server. Do you have any success on converting xen images to kvm compatible images? How did you do it? Any tutorial?

I would very much appreciate your responses as I really need those xen images to run again.
Thanks a lot.

---

### Post by sandyd on 2013-08-15
Easiest way is to use virt-v2v, see process described at [https://access.redhat.com/site/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/V2V_Guide/chap-V2V_Guide-Converting_Virtual_Machines_to_Run_on_KVM_Managed_by_libvirt.html](https://access.redhat.com/site/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/V2V_Guide/chap-V2V_Guide-Converting_Virtual_Machines_to_Run_on_KVM_Managed_by_libvirt.html)

might need access to a fedora vm if you dont find virt-v2v on ubuntu

---

### Post by TheFu on 2013-08-16
I've migrated all our Xen VMs to KVM over the last year.  It was fairly simple process.
* Make a backup of the Xen VMs using normal backup tools. Don't necessarily backup everything - settings, data and non-packaged programs.  Use **dpkg --get-selections> package-list.txt** to store all the installed packages.
* Create a new KVM VM iwth the settings you desire running the exact same OS release.
* Restore the Xen backup into the new VM - settings and data
* Install the packages using **dpkg --set-selections< package-list.txt** and** apt-get -f install** to get them all reinstalled.
* Profit.

There are a few details like NIC MAC addresses that you'll want to watch carefully, but besides that it was really easy.

---

