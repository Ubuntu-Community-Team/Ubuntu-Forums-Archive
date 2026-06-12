---
title: "PXE How-To for Ubuntu Server 7.1 Gutsy ?"
date: 2007-11-25
forum: Server Platforms
---

### Post by ToyotaDiesel on 2007-11-25
I've found a plethora of How-Tos for building a PXE server for almost every build of Ubuntu except Gutsy.

I'm running into path differences, specifically in the package netkit-inetd which doesnt even seem to be available any longer, and also in the dhcp package.  

I've also found several that utilize a Windows PXE server for Linux distros, but what I'm looking for is an Ubuntu box to serve out Ubuntu distros.  

Does anyone know of a current how-to that can be used to build up PXE server in Gutsy? 

Thanks in advance.

---

### Post by copilot on 2007-11-26
I'm working on getting mine working right now, when I do I'll post the how-to here. I got it working last week but realized that I had made so many changes and tweaks that I didn't know _how_ I got it working. This week I'm starting from scratch and documenting every command and config file change.

---

### Post by Indigo258 on 2007-11-26
I posted a how-to for this on my blog ([http://outsidaz.org/blog1/2007/08/09/setting-up-a-pxe-linux-recovery-deployment-server-using-debian-lennyetch/](http://outsidaz.org/blog1/2007/08/09/setting-up-a-pxe-linux-recovery-deployment-server-using-debian-lennyetch/)) not too long ago. It was written for Debian Etch, but should be very easily adapted to Gutsy.

---

### Post by ToyotaDiesel on 2007-11-26
Thanks to the both of you.  

copilot, I look forward to your how-to.  I've shelved the server until I can get some more info on how to do this.

Indigo.  Thanks.  Can you tell me if this line is verbatim the way it should be in dhcp?

filename "pxelinux.0";

I ask because dhcp3 was choking on this line, saying something about it expected a semicolon.  I'll post the error when I can.  I'm sure i'll run into it again, since every how-to I read had that line common to them.

---

