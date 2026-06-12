---
title: "VMWare Server and Windows Vista Internet Connection Problems"
date: 2007-11-07
forum: Virtualisation
---

### Post by arbulus on 2007-11-07
I'm running Gutsy and have VMWare Server installed.  I just installed Vista as a guest OS, but I cannot get Vista to access the internet.  I've installed VMWare tools in Vista, I've gone through the "Set up an internet connection" wizard.  I've tried tinkering with the settings, but nothing seems to work.

I do have a LAN at my house. 

The Network and Sharing Center in Vista just keeps saying "Unidentified network" and "Limited Connectivity" and won't see any of the other computers on my LAN or connect to the internet.

Does anyone know how to resolve this situation?  Any help is appreciated.

---

### Post by kwlskwlguy on 2007-11-08
I'd boot the Guest OS that Vista's installed in off of your Gutsy Desktop Disk, then try to access the internet from the Live CD environment, If you can access the internet that way its a Vista Problem, and not a VMware or Ubuntu Problem.

---

### Post by arbulus on 2007-11-08
Well, I have another guest OS, Ubuntu Server, that can access the net just fine.  So I'm sure that it's specifically a Vista problem.  But I'm really at a loss as to how to get the internet connection in Vista.  I was wondering if anyone else had ever encountered this problem or might have any idea as to what to do. 

Windows really is one of the most annoying OSes I've ever used.

---

### Post by arbulus on 2007-11-08
Ok, so I changed the networking type for the guest OS to "NAT" from "Bridged" and now I can connect to the internet in Vista.  However, it's using a completely different private IP address than the one my LAN uses.  I use 192.168.1.* for addressing, but Vista is using 172.16.193.* as it's IP addressing.

I tried changing the IP to a static IP using the correct IP addressing, but then I'm right back to where I started.  It disables the connection and won't connect to the internet.  So I have to use DHCP, but I have no idea where it's getting it's address from, because I don't use 172.* addresses.

---

### Post by arbulus on 2007-11-12
Bump

---

### Post by arbulus on 2007-11-13
I have googled and googled and googled about this problem and I cannot find any solution.  I've searched the VMWare forums and I've seen numerous questions on there asking about this very same thing.  Not a one of them has been answered.

I just can't believe the lack of information I'm finding. It's really disheartening. I really need this to work, and work properly.

---

### Post by veloce on 2007-11-13
> **arbulus said:**
> Ok, so I changed the networking type for the guest OS to "NAT" from "Bridged" and now I can connect to the internet in Vista.  However, it's using a completely different private IP address than the one my LAN uses.  I use 192.168.1.* for addressing, but Vista is using 172.16.193.* as it's IP addressing.

I tried changing the IP to a static IP using the correct IP addressing, but then I'm right back to where I started.  It disables the connection and won't connect to the internet.  So I have to use DHCP, but I have no idea where it's getting it's address from, because I don't use 172.* addresses.

If you are using NAT then your vista machine **should** be on a complety different address space.  It will be set by vmware in vmware's network setup.  

To change the address range being used by vmware you need to rerun the vmware network config script.But DON't try to set it to the same 192.168.1.* space or you'll cause all kinds of network confusion.

---

### Post by arbulus on 2007-11-14
> **veloce said:**
> If you are using NAT then your vista machine **should** be on a complety different address space.  It will be set by vmware in vmware's network setup.  

To change the address range being used by vmware you need to rerun the vmware network config script.But DON't try to set it to the same 192.168.1.* space or you'll cause all kinds of network confusion.


I would rather it not be using NAT.  I want bridged.  I want my Vista VM to see the rest of my LAN and connect to a samba share that I have on my LAN. So if it's not in 192.168.* then it won't see it.

Does the vmware network script handle that or only NAT? How do I run it?

---

### Post by arbulus on 2007-11-30
Well, I just broke down and deleted the Windows VM and completely uninstalled VMWare Server.  I then reinstalled VMWare Server and then reinstalled Windows and now everything works exactly as it should.

I have no idea why this would be.  Why would this be?  Why would it not work the first time, and work perfectly after reinstalling it?

I don't know, but I'll take it.  Problem solved for now.

---

