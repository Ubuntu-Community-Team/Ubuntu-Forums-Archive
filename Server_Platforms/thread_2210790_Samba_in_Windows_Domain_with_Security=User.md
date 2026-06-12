---
title: "Samba in Windows Domain with Security=User"
date: 2014-03-12
forum: Server Platforms
---

### Post by Beeeerock on 2014-03-12
This is an issue that I find all over Google, but without any clear resolution that I can find.  Simply, why does it take so long to open a folder on my Ubuntu 12.04 Samba server from a Windows 7 workstation?  The workstation is on the domain but I haven't wanted to add Samba to the domain (hope is to retire Windows Server once the trial period is completed successfully).  So Security=User is the way smb.conf is set at the moment.  Workgroup = the domain name.

My feeling is that the problem exists on the Windows side of things.  Can't explain why though.

I'm wondering... are there any known issues with running Samba in a LAN where everything else is part of a domain, *without* making the Samba server a part of the domain?

---

### Post by thufirhawat2 on 2014-03-12
I have 3 Ubuntu 12.04 samba NASs configured as security=user on my office 2008 windows domain at work, and do not have any issues connecting with windows 7, server 2008, or server 2012 machines. Have you tried mapping the samba shares as network drives on the clients you are connecting from? Is the problem just that it is slow to load a folder's contents, or slow transfer rate as well?

---

