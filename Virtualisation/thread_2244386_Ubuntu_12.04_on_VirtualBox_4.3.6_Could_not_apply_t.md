---
title: "Ubuntu 12.04 on VirtualBox 4.3.6 Could not apply the stored configuration for monitor"
date: 2014-09-16
forum: Virtualisation
---

### Post by calleywang on 2014-09-16
Hi all,

I tried changing the video settings for this virtual machine to enable 3D acceleration. When I booted up the virtual machine, the screen was stuck at 640x480 resolution (my computer has a 1600x900 resolution) and it showed the error message

Could not apply the stored configuration for monitors

none of the selected modes were compatible with the possible modes:
Trying modes for CRTC 380
CRTC 380: trying mode 640x480@73Hz with output at 1024x768@61Hz (pass 0)
CRTC 380: trying mode 640x480@73Hz with output at 1024x768@61Hz (pass 1)

I tried to open display settings in Ubuntu, but the only possible choice for resolution was 640x480. I closed the VM and tried changing the video settings back, but nothing changed. I have googled this error message, but they all seem to be from users who only got the message, with no changes to their screen resolution.

My host machine is Windows 7, with both Intel HD graphics and NVIDIA graphics.

---

### Post by bashiergui on 2014-09-16
If the VBox Extension Pack isn't installed in the guest, install it. That's how you gain control over graphics displays of guests.

---

