---
title: "[SOLVED] VMWare Internet Connection"
date: 2008-05-24
forum: Virtualisation
---

### Post by M4rotku on 2008-05-24
Hello all,

In the past, I have used VirtualBox for my virtualization needs.  However, I am trying to switch to VMWare because I was having problems mounting my webcam.  When I was using VirtualBox, the guest would atomatically be connected to the internet through my host's connection.  However, with VMWare, it tells me that I am not connected when I open my browser.  Is there any way to achieve the same sort of connection on the guest as I did with VirtualBox?  If so, then can someone guide me through it in idiot-proof steps?

Much thanks,
M4rotku

---

### Post by fjgaude on 2008-05-24
From my experience you simply make sure you are using the NAT option in VMware, and that does it automatically.

Most options are greyed out when you have the VM loaded, so load it, then power off and then you can get to all the options, including adding hardware, etc.

---

### Post by M4rotku on 2008-05-24
That worked, thanks

---

### Post by Shazaam on 2008-05-24
Just a little tip...
You can edit the settings in the .vmx file of any vm. Find the .vmx file, right-click it and choose open with a text editor.

---

