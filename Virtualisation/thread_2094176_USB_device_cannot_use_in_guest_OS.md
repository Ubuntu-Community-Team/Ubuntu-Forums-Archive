---
title: "USB device cannot use in guest OS"
date: 2012-12-13
forum: Virtualisation
---

### Post by crecy22 on 2012-12-13
Hi all, I'm new here.

My host OS can perfectly use USB device, but it is not available in Ubuntu(guest OS).


Background
--------------------

Host computer:acer notebook aspire V3-571G
Host OS: Windows 7
Guest OS: Ubuntu 10.04.2
Virtualbox version: 4.2.4

I try all i found solution:

install Extension pack --- done, version:4.2.4r81684.
set up USB filter --- add specific USB device filter, add blank USB filter, both above filter, all useless.
plug or unplug in particular time and VBox will auto detect --- always no response.
manual install Vbox USB driver --- useless. If uninstall device from host OS and prompt Vbox USB driver, it will show blue screen.

--------------------

Use "Vboxmanage list usbhost" i found VBox can correctly detect USB device.
[IMG]http://i.imgur.com/FqCIv.jpg[/IMG]

If VBox mount USB device, USB Current State will change "Captured" from "Busy". And my Webcam is correctly verify on Ubuntu.
[IMG]http://i.imgur.com/G95nX.jpg[/IMG]

But it is all, Ubuntu still cannot detect other USB device.
[IMG]http://i.imgur.com/ZCxhz.jpg[/IMG]

How can i do for this situation? All suggests is appreciate. :'(

---

### Post by Cheesemill on 2012-12-13
For proper USB support you need to install the Guest Extensions on your guest VM.

---

### Post by haqking on 2012-12-13
> **Cheesemill said:**
> For proper USB support you need to install the Guest Extensions on your guest VM.

and also make sure the user is in the vboxusers group (ands it is the guest additions and extension pack)
```

sudo usermod -a -G vboxusers username
```

---

