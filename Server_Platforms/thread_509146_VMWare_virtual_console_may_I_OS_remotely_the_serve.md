---
title: "VMWare virtual console may I OS remotely the server?"
date: 2007-07-25
forum: Server Platforms
---

### Post by erasmo.da.rotterdam on 2007-07-25
Hello everybody,
I installed VMWare server on a 64 bit UbuntuDapper LTS server.
On a remote PC I installed the Virtual Console.
Is it possible to install an OS on a Virtual Machine created on the server without introducing a bootable CD on the server? 
It would be great if I could simply use an Ubuntu CD on the remote PC with the virtual console without having to go to the server farm...

---

### Post by veloce on 2007-07-25
Yes it is possible.

There are two ways to do this.  The easiest (but slower) way is to go into the cd rom settings for the virtual machine and set it to use the "physical drive - client".  This is slow because the cd information has to travel from the host across the network. 

The other way is to create an iso from the disk and mount that. Preferably locate it on the host.

---

### Post by erasmo.da.rotterdam on 2007-07-25
Thank you very very much!!!

:guitar:

I downloaded an ISO on the remote server.
on the Virtual Console it is possible to tell the CDROM to use it

After that everything was a piece of cake!!

---

