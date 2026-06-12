---
title: "USB not connecting to Ubuntu VM"
date: 2024-08-27
forum: Virtualisation
---

### Post by victorylap26748 on 2024-08-27
I am running a Ubuntu virtual Machine on a Manjaro OS host system.

I cannot connect a USB device to my virtual machine. I have already downloaded the extension pack for Virtualbox. The preference section does not show 'extensions' option. I can detect my camera / microphone from the 'devices' menu BUT states 'no USB connected'.

---

### Post by &amp;KyT$0P# on 2024-08-27
On your Manjaro host, does running
```
id
```
in Terminal show your user is a member of the [FONT=monospace]vboxusers[/FONT] group?  If not, try adding your user to that group, then log out & log back in for the change to take effect.

---

### Post by victorylap26748 on 2024-08-29
I have joined vboxusers group.

I have a list of USBs listed on the ‘devices’  pull down menu including ‘Chicony Electronics HD user facing’ which I  have selected in the menu.

 However, the camera does not function using Cheese and Camera apps. The device is recognized in shaded text.

---

### Post by &amp;KyT$0P# on 2024-08-29
Does your webcam work in guvcview or VLC media player in the guest?

How are you attaching the webcam to the guest?  Are you using "Devices > USB" submenu, or "Devices > Webcams" submenu?  Does trying the other one instead help?

From another thread, you have VirtualBox 7.0.20.  If you have the Extension Pack installed, is it also version 7.0.20?

---

