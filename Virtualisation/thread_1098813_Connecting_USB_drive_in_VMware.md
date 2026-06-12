---
title: "Connecting USB drive in VMware"
date: 2009-03-17
forum: Virtualisation
---

### Post by Warner White on 2009-03-17
I am running VMware Server 2 on Ubuntu intrepid ibex. I have created an XP Professional virtual machine, but am unable to connect my USB drive. I have installed VMware tools, and have installed the USB controller, and it appears in the hardware panel of the Summary tab, which says, "Autoconnect enabled." On the status bar of the vm the drive appears when I insert a flash drive, and so do the various usb devices (printer, external hard drive, etc.), all marked witha big red X. When I right click and say Connect, the red X disappears temporarily, but then it reappears and up pops a message that says, "Remote USB device error: Remote device disconnected: an error occured while sending data." I also am unable to connect to the internet, but the connection to my local network is operational. I tried disabling Network adapter 1, but all that did was to disconnect me from my local network.

Any ideas about what to do?

---

### Post by dcstar on 2009-03-18
> **Warner White said:**
> I am running VMware Server 2 on Ubuntu intrepid ibex. I have created an XP Professional virtual machine, but am unable to connect my USB drive. I have installed VMware tools, and have installed the USB controller, and it appears in the hardware panel of the Summary tab, which says, "Autoconnect enabled." On the status bar of the vm the drive appears when I insert a flash drive, and so do the various usb devices (printer, external hard drive, etc.), all marked witha big red X. When I right click and say Connect, the red X disappears temporarily, but then it reappears and up pops a message that says, "Remote USB device error: Remote device disconnected: an error occured while sending data." I also am unable to connect to the internet, but the connection to my local network is operational. I tried disabling Network adapter 1, but all that did was to disconnect me from my local network.

Any ideas about what to do?

Have you read the FAQ at the top of this forum?

---

### Post by Ardbob on 2009-05-10
I am having the same issue with my external WD Hard drive. I looked at the thread/FAQ about the issue and followed the instructions. All it said to do was insert a line of code into /etc/fstab, so I did. Now it doesn't pop up with the error and it seemed to recognize the drive in windows xp, but instead of showing up in the explorer as an external hard drive it showed up as a CD Drive... does anyone know why it's doing that or how to fix it?

---

