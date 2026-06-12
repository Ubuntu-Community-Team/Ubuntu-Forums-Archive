---
title: "Use Virtualbox to Print with a non Linux Supported Printer"
date: 2012-02-08
forum: Virtualisation
---

### Post by gr8 on 2012-02-08
I have a printer that I'd like to use on my Ubuntu system. Unfortunately there aren't proper Linux drivers for the printer. Can I print with this unsupported Linux printer through VirtualBox and Windows 7? Or does the printer also need to function in my host system (Ubuntu 11.10)?

---

### Post by japzone on 2012-02-08
If you set the Network Adapter type in the VM to "Bridged" you're GuestOS will apear on your Home Network just like a normal PC so it'll have normal access to any Network Printer, no setup on your Host neccessary. If you want to use a Non-Network printer, it must be USB and then you simply plug it into the Host and once the GuestOS has booted to the Desktop just go to "Devices-->USB" and select your printer to attach it.

---

