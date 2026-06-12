---
title: "Hardy + VBox1.6.2 + USB Harddrive = Problem?"
date: 2008-07-04
forum: Virtualisation
---

### Post by Kamilion on 2008-07-04
Howdy all, I'm running the latest VirtualBox 1.6.2 binary from the vbox site on my Hardy 8.04 GNOME desktop.
I've got all the USB stuff set up, and I can see and use my Canon Canoscan 3000F just fine.

Now, here's my problem: I work in IT and there's many times where I need to access data on a hard drive, so a couple months ago I picked up a [Kingwin IDE/SATA to USB Dongle]("http://www.yesbuy.net/kingwin-usb-2-0-to-sata-ide-adapter-usi-2535.html").
I've set up a device filter in Vbox, with the following data:

JMicron USB to ATA/ATAPI Bridge [0100]
Manufacturer: JMicron
Product: USB to ATA/ATAPI Bridge
Vendor ID: 152D
Product ID: 2338
Revision: 0100
Serial No.: 9243D39E2222

by clicking the "Add Filter From Device" button.

Now, here is where the problem comes into play...
I start up my Win2k virtual machine, and I can see from the Devices -> USB Devices menu that it has found and checkmarked the Canon scanner, but the IDE adapter is greyed out.

See Attached Screenshot.

So I unplugged the adapter from the usb port, started the virtual machine up first, and plugged in the adapter.

Ubuntu has decided it wants the device instead, and mounts the drive and opens nautilus for the mount.

This is a NTFS disk, and the problem is, it needs a checkdisk and a defrag, and since there is still no ntfsck or ntfsdefrag, my only recourse is to use the virtual machine to do it.

Yes, I know about the shared folders. 
Honestly, I'd use that if I just needed access to the files on the volume.
Please don't suggest it as a viable course of action, as I have explained the exact reasoning behind my query, and it was the logical answer to all of the other threads with this type of question.

The tooltip over the Device shows it's state as "Unavailable".

How can I knock either the kernel, dbus, or the automounter into leaving the adapter alone once it's been plugged in and leave it in an available state for VirtualBox 1.6.2 non-OSE to access and abuse in it's own right?

Thanks for reading, I hope someone has an answer.

-- Kamilion

---

### Post by xaris106 on 2008-07-12
might be late for an answer but have you tried without the filter?

---

### Post by dark_phantom on 2008-07-13
I agree, try it without the filter.  All I do is setup the usb controller and not set any type of filter and I can mount any usb device that I have connected.

---

### Post by Kamilion on 2008-07-13
Thanks, I'll give that a shot later when I get back to that PC.
Appreciate the help!

---

