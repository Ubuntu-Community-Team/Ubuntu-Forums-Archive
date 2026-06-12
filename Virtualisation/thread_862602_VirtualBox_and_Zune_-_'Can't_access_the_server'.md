---
title: "VirtualBox and Zune - 'Can't access the server'"
date: 2008-07-17
forum: Virtualisation
---

### Post by Mr_Chapendi on 2008-07-17
I've installed VirtualBox 1.6.2 on Hardy Heron in order to use sync to my Zune - something I have done successfully on a previous Ubuntu install (7.10).  I've enabled the USB support, added the USB filesystem to fstab, and that seems to be working, as I've successfully played around with a thumb drive in my Windows XP host.

I set the Zune software up, and it actually picked up my Zune.  It shows the correct contents, and name, etc.  

From here, I get problems.  I can't sync anything to my Zune from the shared 'Music' folder without getting the 'Cannot access the server' error.  (Code C00D11B2.)  I can, however, sync items that I drop to the Windows desktop and sync from there.

I know that you can sync from the shared folders to a Zune - unless my memory fails me I've done it before.  I just don't remember these errors.  Has anyone else experienced similar problems?

---

### Post by tgerbert on 2008-08-02
Is the Windows Firewall service turned on in your VirtualBox's Windows XP, and the Zune exceptions set?

For some stupid reason the Zune software doesn't seem to play nice without it.

---

### Post by kbsona on 2008-11-01
Try syncing from a Samba share instead of a vbox share..

---

### Post by tgerbert on 2008-11-05
> **kbsona said:**
> Try syncing from a Samba share instead of a vbox share..

Well, that works, thanks.

But why, out of curiosity?

---

