---
title: "[SOLVED] Is this possible?"
date: 2008-12-08
forum: The Cafe
---

### Post by Newuser1111 on 2008-12-08
A laptop I have(Acer Aspire 3003lci) is having problems reading most CDs and cannot boot to USB.]

So can I do this?(If so, How?)
[LIST=1]
[*]Install DamnSmallLinux from a "Pocket CD-RW"
[*]Add another option to GRUB to make it load a 2GB Flash Drive
[*]Install Ubuntu from the Flash Drive
[/LIST]

The first one is already done.

---

### Post by Catalyst2Death on 2008-12-08
booting to the USB disk is BIOS dependent, so if you can't do it from bios you can't do it at all.  

I would suggest going over the network:
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
(server and network installation)
[http://ubuntuforums.org/showpost.php?p=2493&postcount=2](http://ubuntuforums.org/showpost.php?p=2493&postcount=2)

---

### Post by Newuser1111 on 2008-12-08
> **Catalyst2Death said:**
> booting to the USB disk is BIOS dependent, so if you can't do it from bios you can't do it at all.  

I would suggest going over the network:
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
(server and network installation)
[http://ubuntuforums.org/showpost.php?p=2493&postcount=2](http://ubuntuforums.org/showpost.php?p=2493&postcount=2)Already tried Network install, and it didn't work.

---

### Post by FuturePilot on 2008-12-08
> **Catalyst2Death said:**
> booting to the USB disk is BIOS dependent, so if you can't do it from bios you can't do it at all.  


Not really. If it's any somewhat recent (within the last 5 years or so) computer and you can access Grub, you can boot from USB even if your BIOS doesn't support it.

[https://help.ubuntu.com/community/BootFromUSB]("https://help.ubuntu.com/community/BootFromUSB")

---

### Post by Newuser1111 on 2008-12-08
> **FuturePilot said:**
> Not really. If it's any somewhat recent (within the last 5 years or so) computer and you can access Grub, you can boot from USB even if your BIOS doesn't support it.

[https://help.ubuntu.com/community/BootFromUSB]("https://help.ubuntu.com/community/BootFromUSB")```
grub> root (hd0,0)
Filesystem type is ext2fs, partition type 0x83

grub> root (hd1,0)
Filesystem type unknown, partition type 0x7

grub> root (hd2,0)

Error 21: Selected disk does not exist.
```
So is it hd1,0?

EDIT:
Yes, and it is able to boot an existing OS from it.
But I want to install Ubuntu.

---

### Post by FuturePilot on 2008-12-08
> **Newuser1111 said:**
> ```
grub> root (hd0,0)
Filesystem type is ext2fs, partition type 0x83

grub> root (hd1,0)
Filesystem type unknown, partition type 0x7

grub> root (hd2,0)

Error 21: Selected disk does not exist.
```
So is it hd1,0?

EDIT:
Yes, and it is able to boot an existing OS from it.
But I want to install Ubuntu.
Here's what I would do, but it would depend on you having access to a computer that can boot the live CD.
Boot the live CD and use the USB creator to create a bootable USB drive. Then on your laptop boot from the USB and then install the system from that.

---

### Post by Newuser1111 on 2008-12-08
> Here's what I would do, but it would depend on you having access to a computer that can boot the live CD.
Boot the live CD and use the USB creator to create a bootable USB drive. Then on your laptop boot from the USB and then install the system from that.OK, I'll try that.

EDIT:
Seems to be working so far.

EDIT:
It worked.

---

