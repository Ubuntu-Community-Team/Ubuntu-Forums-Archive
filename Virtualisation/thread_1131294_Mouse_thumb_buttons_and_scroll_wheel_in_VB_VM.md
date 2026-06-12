---
title: "Mouse thumb buttons and scroll wheel in VB VM?"
date: 2009-04-20
forum: Virtualisation
---

### Post by mhurtz1 on 2009-04-20
I am trying to get my mouse thumb buttons (forward and back buttons) and the scroll wheel to work inside my Windows XP Home VM. I have the scroll wheel sort of working in that it works for most programs in the VM (firefox, notepad, explorer) and all programs on the Ubuntu host. Unfortunately, it doesn't seem to work in Photoshop CS2 (in the VM), which is the main reason I'm running the VM. The thumb buttons also work on the Ubuntu host, but they don't have any functionality in the VM.

Also, I'm aware I could pass-through the external mouse as a USB device, but this is not an ideal solution as it doesn't work with my touchpad and it disables support in the host.

System Setup:
Host: Ubuntu 9.04, VirtualBox 2.2.0 (Closed Source Edition for USB), Synaptics Touchpad, Microsoft IntelliMouse Explorer
VM: Windows XP Home SP3, windows detects a "Generic Microsoft PS/2 Mouse"

Thanks in advance for any insight.

---

### Post by mhurtz1 on 2009-05-02
Anybody????

Even a way to see what events Windows is receiving when the wheel is scrolled would be a start. Is anybody aware of something like xev for windows?

Also, does anybody know if this works in VMware?

Thanks

---

