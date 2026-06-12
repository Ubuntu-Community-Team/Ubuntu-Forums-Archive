---
title: "Changing the Bootscreen for LTSP clients to XUbuntu"
date: 2009-07-20
forum: Server Platforms
---

### Post by Avinash.Rao on 2009-07-20
Dear all,

I have installed XUbuntu Desktop on Ubuntu Server 8.04 for LTSP.

ii ltsp-manager 0.0.2-0ubuntu3 Ubuntu LTSP server management GUI
ii ltsp-server 5.0.40~bzr20080212-0ubuntu7 Basic LTSP server environment
ii ltsp-server-standalone 5.0.40~bzr20080212-0ubuntu7 Complete LTSP server environment
ii ltspfs 0.5.0~bzr20080109-3ubuntu3 Fuse based remote filesystem for LTSP thin clients
ii python-ltsp 0.2-0ubuntu2 Provides ltsp related functions

LTSP is working, but when the LTSP client boots, the boot screen is
the one that Ubuntu Desktop Edition uses, the orange one! How do i get
the Blue XUbuntu Boot screen for LTSP clients? The login screen is XUbuntu only, the background image and theme in XUbuntu. But the boot screen in the beginning that is when the LTSP Client boots it is the Hardy Boot screen and not the standard XUbuntu and this is not the case on the server or a machine installed with XUbuntu, the initial screen is what i want to change?

Thanks
Avinash

---

### Post by Avinash.Rao on 2009-07-20
1) install the xubuntu usplash theme in your chroot
2) run update-initramfs -u in your chroot
3) run ltsp-update-kernels on your server

---

### Post by komputes on 2009-07-20
Can you expand on the command line way of  			 		   		 		 installing the xubuntu usplash theme in the LTSP chroot?

---

### Post by Avinash.Rao on 2009-07-26
I read this documentation given by asmo.. 

[http://www.ltsp.org/~sbalneav/LTSPManual.html#updating-chroot](http://www.ltsp.org/~sbalneav/LTSPManual.html#updating-chroot)

Its a beautiful doc to learn all about LTSP.



> **komputes said:**
> Can you expand on the command line way of  			 		   		 		 installing the xubuntu usplash theme in the LTSP chroot?

---

