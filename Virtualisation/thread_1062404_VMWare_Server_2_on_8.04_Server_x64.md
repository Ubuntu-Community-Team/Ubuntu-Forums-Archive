---
title: "VMWare Server 2 on 8.04 Server x64"
date: 2009-02-06
forum: Virtualisation
---

### Post by ihavenoideax2 on 2009-02-06
Hello to all again.

I have been rummaging the interweb for an answer to fix my problem with no avail. Currently I am running Ubuntu Server 8.04.2 x64 with all updates on a AMD 64 3500, 4Gib Ram, and a bunch of drives running VMWare Server. 

Anyway, what I am trying to do is get my LaserJet 6P parallel port printer to forward to my virtual server I use for my file server which is also Ubuntu Server 8.04.2 x64. I have changed the modules that load on the host server to not load lp and load parport_pc and ppdev with no avail. Anyone have any ideas what I should do since my whole house uses this printer and I would like to get it back up and running very soon.

Also on this file server I have cupsys and samba installed and all permissions setup and vmware tools installed. Thank you in advance.

---

### Post by dcstar on 2009-02-07
> **ihavenoideax2 said:**
> Hello to all again.

I have been rummaging the interweb for an answer to fix my problem with no avail. Currently I am running Ubuntu Server 8.04.2 x64 with all updates on a AMD 64 3500, 4Gib Ram, and a bunch of drives running VMWare Server. 

Anyway, what I am trying to do is get my LaserJet 6P parallel port printer to forward to my virtual server I use for my file server which is also Ubuntu Server 8.04.2 x64. I have changed the modules that load on the host server to not load lp and load parport_pc and ppdev with no avail. Anyone have any ideas what I should do since my whole house uses this printer and I would like to get it back up and running very soon.

Also on this file server I have cupsys and samba installed and all permissions setup and vmware tools installed. Thank you in advance.

Configuring the VM to have a parallel port should do this, and you cannot stop the host from detecting the hardware because then the VM cannot use it.

---

### Post by ihavenoideax2 on 2009-02-07
So what do you think I should do than? I know I can do it but how?

---

### Post by dcstar on 2009-02-09
> **ihavenoideax2 said:**
> So what do you think I should do than? I know I can do it but how?

The parallel port stuff is in the same configuration area as all the other VM options, use whatever you use for them.

---

### Post by ihavenoideax2 on 2009-02-09
See I know that and it is added on the VM but it doesn't do anything when I try to add it to cups. It has an LPT port in the add options in cups on the VM but when you try to add it, it doesn't detect the printer.

---

