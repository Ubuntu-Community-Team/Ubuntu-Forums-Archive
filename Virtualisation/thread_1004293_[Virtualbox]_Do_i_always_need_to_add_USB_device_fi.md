---
title: "[Virtualbox] Do i always need to add USB device filter to make Guest OS see USB?"
date: 2008-12-07
forum: Virtualisation
---

### Post by asaren on 2008-12-07
Hi,

Do i always need to add USB device filter in Virtualbox to make Guest OS see USB? 

If it does, i need to add it everytime when i connect new usb device.

Is there a way to auto detect new usb device in XP Guest OS.

Thank you

---

### Post by AClark on 2008-12-07
If you add a usb filter and don't fill in any of the criteria then it will be a generic usb filter and any usb device you plug in will be available to the VM.  

In other words just click on the + sign in the usb settings dialogue and save it with out making any changes.

If you fill in the manufacturer criteria for example then only devices from that manufacturer will be visible to the VM.

You still have to go to the Devices menu in the VM and under usb check the device you want to mount before it will be accessible.

Hope this is clear.

---

