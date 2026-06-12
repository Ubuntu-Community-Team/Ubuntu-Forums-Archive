---
title: "[SOLVED] Switching to Non-Free VirtualBox"
date: 2008-07-09
forum: Virtualisation
---

### Post by twoseids on 2008-07-09
I have heard that I need to use the non-free VirtualBox in order for USB to work. Is this true? And if so, will I have to reinstall Windows XP, or can I just open that VM within the new copy of VirtualBox?

---

### Post by HotShotDJ on 2008-07-09
> **twoseids said:**
> I have heard that I need to use the non-free VirtualBox in order for USB to work. Is this true? And if so, will I have to reinstall Windows XP, or can I just open that VM within the new copy of VirtualBox?Yes... this is true... you need the PUEL version that you download directly from SUN in order to get USB support in VirtualBox.  You will NOT have to reinstall Windows XP.  Simply uninstall the version of VirtualBox you have installed now (don't forget to uninstall virtualbox-ose-modules-* as well!) and then install the PUEL version that you downloaded. When you boot up your Windows XP VM, you'll need to install the new Guest Additions and then reboot your VM.  That should do it for you.

---

### Post by twoseids on 2008-07-09
> **HotShotDJ said:**
> Yes... this is true... you need the PUEL version that you download directly from SUN in order to get USB support in VirtualBox.  You will NOT have to reinstall Windows XP.  Simply uninstall the version of VirtualBox you have installed now (don't forget to uninstall virtualbox-ose-modules-* as well!) and then install the PUEL version that you downloaded. When you boot up your Windows XP VM, you'll need to install the new Guest Additions and then reboot your VM.  That should do it for you.
Excellent. Appreciate your help.

---

