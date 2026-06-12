---
title: "Trying to install small 14.04 LTS"
date: 2015-10-21
forum: Server Platforms
---

### Post by naviathan on 2015-10-21
My intent is to setup a Xen Hypervisor using ubuntu server. Following the Wiki it says to use [COLOR=#333333][FONT=Ubuntu]"Guided - use the entire disk and setup LVM", then for "[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]Amount of volume group to use for guided partitioning:" it says to use a small amount like 10GB. When I try this it says the minimal size is 61GB? Why so large? I'd rather not use this size, but just to get started I tried it and the installer fails at selecting packages. Any ideas?[/FONT][/COLOR]

---

### Post by darkod on 2015-10-21
I am confused. Are you talking about ubuntu server as a VM on Xen? Because if you want to install Xen Server (I assume that's what you mean by Xen Hypervisor) on the physical machine then Xen has its own ISO to do that. You don't do it with ubuntu. Later on the Xen you can have linux and windows VMs but the base Xen Server is installed from their ISO.

On the other hand, if you are talking about doing virtualization with ubuntu, the most common option is KVM (which is not Xen or VMware). KVM you do install with the ubuntu ISO and the appropriate packages.

---

### Post by naviathan on 2015-10-21
According to the Wiki ([https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen)) You install server as a means to install Xen. If you know where I can find an ISO that will just install Xen Hypervisor Dom0 without going through a distro, I'd be ecstatic if you could point me in the right direction (one that's not Xen Server by Citrix).

---

### Post by darkod on 2015-10-21
I was talking about the Xen Server. I wasn't even aware about this open source Xen hypervisor.

There is no reason the installer to insist on 61GB because the basic ubuntu server installation is very small, less than 2GB. Have you tried the Manual partitioning? You can create LVM yourself and make the root LV 10GB or 5GB as per those instructions. I don't use the guided methods anyway (except for temp test VMs) because it's best to have control over the partitioning. It's one of the most important steps of installing a server.

---

### Post by naviathan on 2015-10-21
I'll try the manual method. The guided method immediately threw up the error about the minimum volume size when I was creating it. I will be surprised if the manual partitioning doesn't also.

---

### Post by TheFu on 2015-10-21
Definitely manually partition and manually configure LVM as you need.
Sorry, cannot help with xen-switched from xen to kvm in 2010. ZERO regrets.

If you don't have a specific requirement for xen, perhaps if you described the end-goal for this hypervisor, some smart folks could suggest a total-system that fits?

---

### Post by naviathan on 2015-10-21
[FONT=verdana]I'm setting up a new-to-me server to do some virtual servers in. I want to have a VM to manage my home media share, an image for workspaces to build web projects and an image for backup/rsync services. I mostly do this for fun so my funds are limited. I've managed a Thinkserver RD230 with dual Xeon X5675, 64GB DDR3 ECC memory (which only shows as 58GB in the BIOS...), 3Ware 9750-8i RAID controller, 4 5TB mechanicals in RAID5 and 4 120GB SSDs in RAID10. I plan on using the RAID10 for the Dom0 and the VM images and the RAID5 for datastore.[/FONT]

---

### Post by darkod on 2015-10-21
In your place I would investigate if this Xen project is stable for production. When we say production we also mean home servers, anything that you want to work stable. The mentioned KVM sounds like better option, and is definitely stable for production. I didn't even know about this Xen project so I can't comment on that.

Also, quick glance at the wiki you linked looked like they call Dom0 the basic OS/hypervisor. If that is the case, a raid10 of 4 disks (doesn't matter SSD or HDD) is an overkill. If by datastore you mean all the rest storage, as the term is usually used in virtualization, you need both the SSDs and HDDs in the datastore. You need only few GBs for the hypervisor.

And I see no benefit to put the hypervisor on SSD. You will probably get more performance if you have storage on the SSDs. Others can comment on this, which way is better...

---

### Post by naviathan on 2015-10-21
You've never heard of Xen? It's the basis for the Citrix XenServer, Amazon EC-2, Rackspace OpenStack, etc. It's backed by AMD and INTEL, Google, Verizon, ARM, Citrix, Oracle... It's actually pretty stable.

---

### Post by darkod on 2015-10-21
I meant the Xen open source project, not the Xen product. You said you want to avoid Xen Server (even though it has a free version). This Xen open source project is not the Xen Server and I just stated my opinion that it might not have the support as Xen Server, KVM, VMware and the likes... I haven't done comparisons so I might be wrong. That's all...

---

### Post by TheFu on 2015-10-21
Sounds like Xen isn't a bad choice, but I've heard that it is more stable on RHEL/CentOS than on Debian. When it would boot, it was very stable for us.

KVM is what Openstack is based on. That could be important for some careers.  Openstack is non-trivial to setup and really needs 10 physical systems for all the overheard to begin to be useful. I know of Openstack deployments with 2000+ physical servers and wouldn't be surprised if someone has 50K+ servers.

Proxmox sorta makes KVM and LXC easy for limited numbers of VMs - I hear that multiple Proxmox servers are grouped into a "cluster" for management reasons.

CentOS/RHEL has oVirt ... which is sorta between proxmox and openstack, if I understand it correctly. OTOH, oVirt has about 20 different languages used to create it, but I don't have any idea how much that matters for the deploying engineer.

Anyway ... doesn't seem like Xen is a bad choice either.

---

### Post by naviathan on 2015-10-21
The Xen project is the basis for XenServer. Much like KVM is the basis for many other products.

---

