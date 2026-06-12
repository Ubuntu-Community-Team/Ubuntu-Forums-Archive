---
title: "you need at least 8.6 gb to install ubuntu. this computer has only 0.0b"
date: 2017-03-20
forum: Virtualisation
---

### Post by Vinayaka_Negalur on 2017-03-20
Hi all,

Maybe this is already resolved, But i was not able to find the right info for this issue.

I am running windows 7 with 16GB memory and 2 TB HDD.
I have installed VirtualBox-5.1.18-114002-Win version.

When I try to install "ubuntu-16.04.2-desktop-amd64", I get the error as 

"you need at least 8.6 gb to install ubuntu. this computer has only 0.0b"

When I click on Try ubuntu, it works like a charm..

I searched for some details for the same in internet and found a link which tells that this is a bug in ubuntu (not sure though??:roll:)
[https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1614810](https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1614810)

Can you please guide me if you have faced a similar issue or if the solution is known..

---

### Post by SeijiSensei on 2017-03-20
Are you trying to install to the virtual machine, or to the physical machine in a dual-boot setting?  If the latter, your hard drive is probably entirely dedicated to Windows leaving no space for Ubuntu.  If you're installing to the VM, how much space did you allocate for the virtual disk when creating the virtual machine?

---

### Post by Vinayaka_Negalur on 2017-03-20
I am trying to install ubuntu on VM.
I allocated 80GB while creating the Virtual disk, I see that 83GB vdi file is created in HDD. 

> **SeijiSensei said:**
> Are you trying to install to the virtual machine, or to the physical machine in a dual-boot setting?  If the latter, your hard drive is probably entirely dedicated to Windows leaving no space for Ubuntu.  If you're installing to the VM, how much space did you allocate for the virtual disk when creating the virtual machine?

---

### Post by howefield on 2017-03-20
Thread moved to the "*Virtualisation*" forum for a better fit.

---

### Post by SeijiSensei on 2017-03-21
I've installed 16.04 in VirtualBox VMs running on top of both Windows and Linux without a hitch so your situation is unusual to say the least. I usually download the ISO image onto the host's disk and point to it during the VM creation process.  When asked about partitioning, I tell the installer to use the whole disk, since it only sees the VM container.

---

### Post by Vinayaka_Negalur on 2017-03-21
The harddisk (vdi file) allocated was removed somehow and hence the iso file was not finding the HDD space to install.
After creating a new virtual machine, the issue is resolved. 

> **SeijiSensei said:**
> I've installed 16.04 in VirtualBox VMs running on top of both Windows and Linux without a hitch so your situation is unusual to say the least. I usually download the ISO image onto the host's disk and point to it during the VM creation process.  When asked about partitioning, I tell the installer to use the whole disk, since it only sees the VM container.

---

### Post by Tadaen_Sylvermane on 2017-03-29
Just as a note for future reference. Linux is not like Windows. In Windows you need 20+ gigs for an installation + software. Anecdotally in my usage I always create a 15 gig partition for root, and never use more than half of it for all of my os + software. For testing in a vm unless you plan on using it for storage keep em small. can create more vms that way :p

---

