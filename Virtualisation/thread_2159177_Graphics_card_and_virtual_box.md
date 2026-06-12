---
title: "Graphics card and virtual box"
date: 2013-07-02
forum: Virtualisation
---

### Post by achu91 on 2013-07-02
;i am having ubuntu 13.04 as Host and windows XP in virtual box(VB).I would like to know whether if i install a graphics card ,whether VB will detect automatically or rather  whether my graphics card will work in VB while playing games etc..Please reply ;

---

### Post by heiko_s on 2013-07-02
Hope I got your question right.

Windows XP running inside Virtualbox will use a "virtual graphics device" without direct access to the graphics hardware. Virtualbox will broker (or translate) the graphics instructions to be executed by the Ubuntu-based driver (whatever driver you installed).

You can install the Guest Additions in Windows and improve graphics performance - see also here: [http://askubuntu.com/questions/139320/enable-graphics-card-in-virtual-box]("http://askubuntu.com/questions/139320/enable-graphics-card-in-virtual-box") and here: [http://www.virtualbox.org/manual/ch04.html#guestadd-3d]("http://www.virtualbox.org/manual/ch04.html#guestadd-3d").

The best performance can be achieved using a separate graphics card for your guest (is that what you asked?) together with VGA passthrough (sometimes also referred to as PCI passthrough). This solution requires very specific hardware features and only a limited range of graphics cards will work. Given the hardware restrictions, VGA passthrough is known to work well with Xen (an "alternative" to Virtualbox) and KVM using the latest kernels and perhaps some patches.

There is talk about Virtualbox supporting VGA passthrough for some graphics cards, but I haven't seen it yet. I'm using Xen. Whatever virtualization solution you choose (Virtualbox, Xen, KVM, or the commercial VMware), VGA passthrough can be challenging but also very rewarding.

Try with the suggestions in the link above and see if that works for you.

---

### Post by achu91 on 2013-07-02
Thanks you very much  for the detailed and excellent reply,it has helped to understand more about VB .But  in the manual for VB it is written  that it supports directx;So when we are installing a game ,and it asks to install directX ,shall i proceed with installation of directx or the guest addition has directx by default.Kindly reply.

---

