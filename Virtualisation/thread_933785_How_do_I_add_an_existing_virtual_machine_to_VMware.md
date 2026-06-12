---
title: "How do I add an existing virtual machine to VMware?"
date: 2008-09-29
forum: Virtualisation
---

### Post by pagemaster on 2008-09-29
When I click "Add Virtual Machine to Inventory," it opens a new window with only "My Computer" and inside an empty directory labeled "Standard." How am I meant to add my precreated VMware, if I can't navigate to it, like VMware on Windows?

Thanks
Mike

---

### Post by lazyart on 2008-09-30
File>Open>Browse...

---

### Post by pagemaster on 2008-09-30
I don't see File anywhere.

I am using the linux VMware, with firefox as my interface. The only option I have that is even remotely like File is "Virtual Machine" which then goes onto "Add Virtual Machine to Inventory" and then gives me the same UI with just My Computer and inside is Standard.

---

### Post by MystaMax on 2008-09-30
Hi pagemaster-

VMware Server 2 uses datastores to manage VM locations. 

If your VMs are not in the deafult VMware Server location (/var/lib/vmware/Virtual Machines), then you will have to add another datastore, or move your VMs to the known datastore location. I suggest reading over the [VMware Server 2 manual]("http://www.vmware.com/pdf/vmserver2.pdf"). Page 110 talks about adding Datastores.

The WebUI tells you where your datastore is (see screenshot).

You can also change your default datastore location, by editing the /etc/vmware/config file

```
sudo vi /etc/vmware/config
```Look for vmdir = "/var/lib/vmware/Virtual Machines"

Or you can add another datastore, see the linked manual for that.

---

