---
title: "How to install Ubuntu Server on USB stick for UEFI?"
date: 2013-07-07
forum: Server Platforms
---

### Post by Kdar on 2013-07-07
How should I go about installing Ubuntu Server 13.04 on USB drive/stick for NAS with UEFI bios?

Can I do it from VirtualBox? or what are my options? (I don't have external CD-drive)

---

### Post by papibe on 2013-07-07
Hi Kdar.

Check post #4 in this [thread]("http://ubuntuforums.org/showthread.php?t=2153157&highlight=server+usb"). I haven't tried it yet, but it looks promising.

Regards.

---

### Post by Kdar on 2013-07-08
Thanks.. I got it. I basically used two USBs.. once was "CD" and other as storage.

I do see a weird thing now... when I connected my HDDs (by SATA), they show up as sda and sdb... and the root file system becomes sdc (which is that USB stick).

Is it normal? and if not.. how could I fix it or force the file system to be on sda?

---

