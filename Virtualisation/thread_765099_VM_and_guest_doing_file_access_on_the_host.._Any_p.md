---
title: "VM and guest doing file access on the host.. Any problems with this scenario?"
date: 2008-04-24
forum: Virtualisation
---

### Post by Saneless on 2008-04-24
Here's my scenario:

I'm going to partition my machine about 35GB for Vista and then the remainder (280GB or so) for linux.  maybe 15GB for / and the rest for /home

I'm going to install VBox probably, but I'm not against VMWare server.  This is in LInux, which I intend to use as much as possible (meaning never use vista if I don't have to)

On the virtual machine I'll be running XP and I plan on having itunes on it so I can do my ipod a good way (sorry linux peeps, I think the alternatives are poo).  I plan on having the files sit in a linux folder under home and having the XP VM access/edit them.

Is this going to work?  Will the XPVM treat the /home drive like a network shared drive and have no issues?  Will it freak out since it's technically a partition in Linux?  Will linux freak out because a different OS is accessing the file system?

Just things like that I don't know about.. I'd rather not copy all the files to the XP VM because if I wipe it out I don't want all my things stored inside a VM image, I'd rather they be in a regular filesystem.

Thanks in advance

---

### Post by dcstar on 2008-04-25
> **Saneless said:**
> Here's my scenario:

I'm going to partition my machine about 35GB for Vista and then the remainder (280GB or so) for linux.  maybe 15GB for / and the rest for /home

I'm going to install VBox probably, but I'm not against VMWare server.  This is in LInux, which I intend to use as much as possible (meaning never use vista if I don't have to)

On the virtual machine I'll be running XP and I plan on having itunes on it so I can do my ipod a good way (sorry linux peeps, I think the alternatives are poo).  I plan on having the files sit in a linux folder under home and having the XP VM access/edit them.
........

As with all VM file sharing, using a Samba share on the host is usually the easiest way of doing it.

You CANNOT (and should not) directly access host file systems from a VM - the risks of corruption are too great.

The are numerous HOWTOs on the Samba sharing.

---

