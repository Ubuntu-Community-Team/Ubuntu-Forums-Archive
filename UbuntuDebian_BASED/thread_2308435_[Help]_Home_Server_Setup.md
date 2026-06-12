---
title: "[Help] Home Server Setup"
date: 2016-01-03
forum: Ubuntu/Debian BASED
---

### Post by phoanglong-ciao on 2016-01-03
hi guys,

merry xmas and happy new year,

I'm in the process of rebuilding my home server and would great appreciated any help, here is a bit overview of my current setup:

1. My old PC Server is running Zentyal Server Community Edition 4.2.1 (low specs, running nicely for the past 3 years, intel g620, ram 4gb ddr3)
2. My new setup will be running on Supermicro Server Rack 1U with Vmware Vsphere base running Zentyal Server and Elastix.

I have a few setback with my setup and it would be greatly appreciated if someone can help me out.

1. On my old Zentyal Server, I have setup and configured quite a lot of thing and it would be a pain to do them one by one, all over again :(
- Is there any software to do a back up and restore for Ubuntu Server? Will it backup every setting on my old server and transfer it a new one?
- Can I use CloneZilla to clone the current server hdd and restore on new hardware? Will there be any misconfiguration (a.k.a different hardware, device, ethernet, pci etc..))

2. On my old system I have two hdd, 1 is 80gb (for OS) and the other is 4TB (for data storage)
- My supermicro is currently running a adaptec raid (RAID 1) for 2 WD SAS 250 gb. I have manage to successfully install VMWare vSphere for virtualisation and finished installing the Zentyal server and Elastix.
- I don't have any experience with supermicro and hardware raid so this might sound a like a complete idiot but how can I configure the supermicro to run RAID on the WD SAS only, leaving me more space with 4TB and the 80gb.

3. in my old computer, Zentyal is being setup as DHCP and DNS server and as I move to virtualisation technology, the Zentyal won't be the first one to boot, if it is not the first one to boot up how could it lease the IP to client? as VMware also need IP to be configured. Should I set Static IP address for VMware and let's the Zentyal does it thing?

Many thanks,

Long

---

### Post by ian-weisser on 2016-01-03
> **phoanglong-ciao said:**
> 
1. On my old Zentyal Server, I have setup and configured quite a lot of thing and it would be a pain to do them one by one, all over again :(
- Is there any software to do a back up and restore for Ubuntu Server? Will it backup every setting on my old server and transfer it a new one?
- Can I use CloneZilla to clone the current server hdd and restore on new hardware? Will there be any misconfiguration (a.k.a different hardware, device, ethernet, pci etc..))

There are many applications for backing up and restoring.
None of them tries to figure out or debug changed hardware or upgraded OS during a restore. That's still a human admin task. Restoring settings and customizations to a new system may work, may not.
Bootable-backups (like clonezilla produces) may work on new hardware, may not...precisely due to those possible misconfigurations.

Installing, tracking, debugging, and uninstalling various customizations, settings, and packages is simply part of Intermediate Linux.
Best to use an organized way of tracking them, to make it easier for you to maintain.

---

