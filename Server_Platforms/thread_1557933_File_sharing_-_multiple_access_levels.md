---
title: "File sharing - multiple access levels"
date: 2010-08-21
forum: Server Platforms
---

### Post by TNHarleyRider on 2010-08-21
Hi all.
 
I am running Ubuntu server v. 10.04 on a small home server (ATOM CPU, SuperMicro motherboard and software RAID 1 SATA HDDs) with SAMBA. The one user in Samba is the same as the the Ubuntu server user as well as the Windows Vista user IDs on my desktop and notebook PCs. The passwords between the listed accounts are manually synchronized. I have a couple of shares setup in Samba to allow centralized file storage on the server. No problems with this everything works well.
 
The problem is that there are some documents that are more private (i.e. 401K and other investment history, banking records, etc.) than what I would like casual users of my computer to discover. I could create multiple user IDs on the Vista system and in Samba, but my wife and I typically leave the computers on. That said, I want to isolate some files from people like our son-in-law and friends who may jump on the computer to look things up while they're here. Saying "I need to reboot first" is akward and begs for the question of why to which the answer is I don't trust you THAT much. 
 
I would like a way to setup a different share (?) that would require a separate authentication before access is granted. That way my wife and I can keep some things protected without the hassle of rebooting or logging out/logging back in the PC first. I know that there's different document management software packages out there, but that seems like overkill. I could setup a virtualization software and run something like FreeNAS in a VM, but the ATOM motherboard doesn't support the virtualization extensions that seem to be required for KVM. I could also run VMware Server (the free one) with FreeNAS in a VM, but that doesn't seem to be friendly install and breaks if the kernel is updated.
 
Does anyone have any constructive suggestions?
 
Thanks

---

### Post by earthpigg on 2010-08-22
Something like TrueCrypt would be a simple solution. Put the sensitive stuff in a folder, and encrypt it.

---

### Post by TNHarleyRider on 2010-08-22
Thanks, Earthpigg. That's actually a rather obvious solution.  :redface:

---

