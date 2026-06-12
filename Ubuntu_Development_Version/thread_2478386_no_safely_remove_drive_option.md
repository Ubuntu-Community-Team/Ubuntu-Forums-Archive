---
title: "no safely remove drive option"
date: 2022-08-25
forum: Ubuntu Development Version
---

### Post by Claus7 on 2022-08-25
Hello,

either using ubuntu flashback, xorg or wayland there is no option to safely remove a usb hdd. There is the option to umount it or even eject it by right clicking on the icon of the drive on desktop, yet this doesn't switch off the light the drive has. Also, choosing these options doesn't display the message that was displayed when someone was successful in removing the drive from ubuntu.

The new nautilus (Files) version 43 has discontinued to offer this option, which I think was the safest way to remove a drive from ubuntu (till jammy).

Ubuntu jammy: it offers the option from Files, which means that you cannot right click and remove the drive from desktop safely.
Ubuntu kudu: no option at all (for safely removing the drive).
Using nemo instead: it works in every desktop, yet it is not the default.

Regards!

---

### Post by jbicha on 2022-08-26
In the Disks app that comes pre-installed, I can click an external disk and there is a power symbol button I can click to power off the device.

Here's a nautilus bug I found: [https://gitlab.gnome.org/GNOME/nautilus/-/issues/2154](https://gitlab.gnome.org/GNOME/nautilus/-/issues/2154)

---

### Post by Claus7 on 2022-08-26
Hello,

> **jbicha said:**
> In the Disks app that comes pre-installed, I can click an external disk and there is a power symbol button I can click to power off the device.

Here's a nautilus bug I found: [https://gitlab.gnome.org/GNOME/nautilus/-/issues/2154](https://gitlab.gnome.org/GNOME/nautilus/-/issues/2154)

thank you for the alternative proposal. I didn't know that. I was avoiding Disks utility, unless I had to see something more important, since there also lies the central disk of anyone's system. 

I tested it in 22.04. Lights went off, yet I didn't have the information displayed, that the drive was safely removed. 

Hope the bug gets fixed soon, since it has to do with very frequent usage of one's computer. I think I will stick with nemo handling the desktop: if only it didn't expand the labels of desktop icons upon hovering.

Regards!

---

### Post by mIk3_08 on 2022-08-27
> **Claus7 said:**
> Hello,
either using ubuntu flashback, xorg or wayland there is no option to safely remove a usb hdd. 
Disks app can stop or even turn off your extended external storage. I' have been using this app and it helps me a lot. Here is the image below. Regards and cheers.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290933&stc=1[/IMG]

---

### Post by Claus7 on 2022-08-27
Hello,

thank you. It is just that I was removing every external usb drive by right clicking on its desktop icon and choosing safely remove drive. Every time the drive wasn't busy, it was informing me that it was safely removed.

Regards!

---

### Post by zebra2 on 2022-08-27
On my 22.4 I'm getting a Unmount, Eject, New Window options. On my 22.10 I'm getting an Eject with an Eject arrow to the right .
Either way, unmount or eject the results are the same.

---

### Post by mIk3_08 on 2022-08-28
On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

### Post by Claus7 on 2022-08-30
Hello,

testing again, nautilus has this feature and informs about safely removing a drive. It doesn't do it when a usb stick is used though.[Edit: it does even on sticks, yet the light is still on.] I consider the option disks to be an alternative. There is no desktop option that does the same though, as it used to. It's good that nautilus has this feature back. 

Regards!

---

