---
title: "virtual machine"
date: 2008-01-14
forum: Virtualisation
---

### Post by rockinlinux on 2008-01-14
I have needs of windows. I am needing to run photshop cs2 or3 for my school but i want to install something like vmware or vitualbox. I need usb support for a device (tablet) that i can not get running in ubuntu. I would also like it to be free...what can i do?

thanks in advance :)

---

### Post by thisismalhotra on 2008-01-14
Hi,

You can download vmware player for free from vmware website and also download a pre built windows image by googling it. Very few things to configure should work like actual windows !!

:)

---

### Post by rockinlinux on 2008-01-14
and that has usb support? and i can install drivers?

---

### Post by rockinlinux on 2008-01-14
anyones else?

---

### Post by The Cog on 2008-01-14
I would presume that vmware has USB support. I would be veeeery surprised it it didn't.

Another possibility is VirtualBox. The VirtualBox that's in the repositories does not have USB support, but the one you can download from the VirtualBox web site does. The web-site version is restricted - you cannot use it for a commercial server application without  buying a license from them, but it's fine for personal use.

---

### Post by bodhi.zazen on 2008-01-14
> **thisismalhotra said:**
> Hi,

You can download vmware player for free from vmware website and also download a pre built windows image by googling it. Very few things to configure should work like actual windows !!

:)

VMWare Server is superior to player and freely available.

Both Virtualbox and VMWare allow sharing, either via usb driver or any number of network protocols (nfs, samba, ssh (scp), http, ftp).

---

### Post by fiddledd on 2008-01-14
Sorry if you already know this:
The OSE version of VirtualBox in the repositories doesn't support USB, the non-free version does. You'll also probaly need to install VirtualBox additions on the Guest for Folder Sharing etc.

---

### Post by rockinlinux on 2008-01-14
so will i be able to run photoshop cs2 and dreamweaver, flash and fireworks in this? and also will i be able to install the drivers for my genius gpen tablet?

---

### Post by rockinlinux on 2008-01-15
so i installed virtualbox with windows xp and it wroks better than i thought, I installed photoshop and it runs just like a normal windows install. The only question i have is there a way to mke the windows like full screen? I went to the machine menu and clicked the ful screen but it was just a small box surrounded by black.

thanks for everything!!

---

### Post by rockinlinux on 2008-01-15
i also just tryied to plug my camera in and it was not detected by windows. This is strange but i dont realy know anything about windows because i only use linux....how do i get the usb to work?

---

### Post by fiddledd on 2008-01-15
I'm going to assume you've done all this, but just in case:
In VirtualBox Setting for the VM you have to manually add the USB adapter and also each USB device, it should all show up in the add device. Tehn while running the guest you have to select the USB device from the Machine menu (it's a checkbox). I'm typing this from memeory as I've not used VirtualBox for a while (or even Ubuntu actually :) ), so it may not exactly match the menus etc.

EDIT:
Almost forgot, and you must have Virtualbox Additions installed on the XP guest.

---

### Post by rockinlinux on 2008-01-15
Ok i got it working, i had to edit my fstab and do someother thing...i found a how to at the virtualbox forums. Now my question (i might jst strat another topic) is if i can add a device that does not work in ubuntu.

---

### Post by fiddledd on 2008-01-15
I tried it with a USB Framegrabber, didn't work. However, take a look here:

[http://ubuntuforums.org/archive/index.php/t-541195.html](http://ubuntuforums.org/archive/index.php/t-541195.html)

it might help.

---

