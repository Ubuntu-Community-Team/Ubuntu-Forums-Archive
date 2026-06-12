---
title: "VirtualBox: when exporting appliance, turns the file system READ ONLY"
date: 2014-06-12
forum: Virtualisation
---

### Post by fernandojosecabral on 2014-06-12
When exporting a guest under VirtualBox it stops when the EXPORTED.OVA file reachs 1.5 GB. Then it prints an error message AND the whole file
system becomes READ-ONLY. Even if I attach a new device, like a pendrive, it turn read-only immediately. The system becomes unusable because
no file can be created, removed or written to. I have to reboot twice before I can use the system again (first time e does an automated cleanup).

OS: Linux mint Qiana
VirtualBox: 4.3.12 r93733

Error message:
```

Failed exporting appliance
/home/fernando/exported.ova
File not accessible or errouneous file contents
Details:
Result code: VBOX_E_FIILE_ERROR (0x80BB0004)
Component:  Appliance
Interface:     Appliance {long code I supposed it not needed to understand the problem}

```

From this point on, I can not create or write any file, anywhere in the system, even as root.
Can not use piping (|) either, or else the terminal quits without notice.

1) I have exported four other guests, and it works. I can export any other guest, but this one.
2) Export crashs at 1.5 GB, but I have exported other appliances as big as 4.6 GB so size probabily is not the issue

Any hints?

---

### Post by CharlesA on 2014-06-14
Have you already run fsck on the host's OS drive?

Does virtualbox have anything to verify the integrity of a virtual hard disk file

Found this:
[http://www.deltalounge.net/wpress/2011/08/virtualbox-solved-vbox_e_file_error-0x80bb0004/](http://www.deltalounge.net/wpress/2011/08/virtualbox-solved-vbox_e_file_error-0x80bb0004/)
[http://itkbs.wordpress.com/tag/vbox_e_file_error-0x80bb0004/](http://itkbs.wordpress.com/tag/vbox_e_file_error-0x80bb0004/)

---

