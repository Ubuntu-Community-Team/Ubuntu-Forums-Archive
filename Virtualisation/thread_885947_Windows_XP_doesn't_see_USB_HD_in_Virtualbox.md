---
title: "Windows XP doesn't see USB HD in Virtualbox"
date: 2008-08-10
forum: Virtualisation
---

### Post by Nathanp39 on 2008-08-10
I've setup Windows XP under Virtualbox 1.6.4 with Ubuntu Hardy.
The USB HD shows up in the Virtualbox USB settings OK (such as the Device\USB Devices menu for the VM), but XP doesn't see it.  When I start the XP VM, the USB drive disappears from the Ubuntu desktop.  When I look under Device Manager, XP shows the USB drivers are not installed.  I suspect the problem is more XP than VirtualBox, but I don't know for sure.

I've followed all the Virtualbox\Ubuntu\USB tutorials out there, but no luck.

Are there any USB drivers I need to install?  I've Googled this and tried everything I found, but have run out of options.  Any suggestions please?

Thanks,
Nathan

---

### Post by Nathanp39 on 2008-08-16
Figured this out. Posting in case it might help someone else.

I unchecked USB 2.0 in the Virtual Box USB settings and Windows picked up the HD after that.

Nathan

---

