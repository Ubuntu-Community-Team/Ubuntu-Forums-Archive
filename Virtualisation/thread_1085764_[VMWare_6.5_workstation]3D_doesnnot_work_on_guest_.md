---
title: "[VMWare 6.5 workstation]3D doesnnot work on guest OS"
date: 2009-03-03
forum: Virtualisation
---

### Post by maximmak on 2009-03-03
I am running vmware workstation 6.5 on Ubuntu 8.10, and having windows xp sp3 as my guest os; however, the vmware says "This computer does not have a 3D graphics system supported by VMware Workstation."

anyone know how to fix it?
thanks!

here is my computer info:


Edit bodhi.zazen : Deleted the long output from lshw. Please use text attachments if you wish to post such long output in the future and as cwsnyder indicated, with virtualization your actual physical hardware is irrelevant anyways.

---

### Post by cwsnyder on 2009-03-03
That is correct.  If you read the documentation for VMware, they state plainly that the client operating system does not have direct access to the video card and thus does not have 3D graphics or acceleration.  If you need full 3D graphics acceleration, you need to dual-boot, rather than run a virtual client.  (For example if you want to run Windows games.)  This is to prevent problems with the client and host both controlling the graphics hardware.  The client has access only to the VESA emulation.

---

### Post by bodhi.zazen on 2009-03-03
improving graphics / 3d acceleration in guests in in development with all platforms (VMWare, VBox, and KVM at least), but alas IMO it is still in Beta and does not work "as advertised".

If you need 3d acceleration you are best off dual booting at the moment.

---

### Post by davbran on 2009-03-03
There is a little more to it than just that though, right now there is DX9.x support for 3D in VMware 6.5 there is no OpenGL support for it.

---

