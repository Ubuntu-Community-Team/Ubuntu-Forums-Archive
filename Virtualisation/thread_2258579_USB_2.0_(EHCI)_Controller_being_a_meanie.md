---
title: "USB 2.0 (EHCI) Controller being a meanie"
date: 2014-12-28
forum: Virtualisation
---

### Post by Tom_ZeCat on 2014-12-28
I'm having trouble getting Windows 7 to run with USB ports available under VirtualBox.  This same Windows 7 Ultimate x64 worked on this Lenovo laptop before.  Previously, I was using Kubuntu 14.04.  It's a long story, but I wiped the computer and installed Kubuntu 14.10 from scratch, hence the need to reinstall VirtualBox.  

I made sure to install the Oracle VM VirtualBox extension back per the instructions on this page: 

[http://www.itzgeek.com/how-tos/mini-howtos/how-to-install-virtualbox-extension.html#axzz3NBE896O9]("http://www.itzgeek.com/how-tos/mini-howtos/how-to-install-virtualbox-extension.html#axzz3NBE896O9")

When I check my install in the terminal with this command, “sudo VBoxManage list extpacks,” I get this:  

```
tommy@tommy-Ideapad-Z570:~$ sudo VBoxManage list extpacks
[sudo] password for tommy: 
Extension Packs: 2
Pack no. 0:   Oracle VM VirtualBox Extension Pack
Version:      4.3.12
Revision:     93733
Edition:      
Description:  USB 2.0 Host Controller, Host Webcam, VirtualBox RDP, PXE ROM with E1000 support.
VRDE Module:  VBoxVRDP
Usable:       true 
Why unusable: 

Pack no. 1:   VNC
Version:      4.3.18
Revision:     96516
Edition:      
Description:  VNC plugin module
VRDE Module:  VBoxVNC
Usable:       true 
Why unusable: 
```

Looks good.  

Here's the problem I'm having.  Under Settings ==> USB, if I check "Enable USB 2.0 (EHCI) Controller," Windows 7 won't install.  It gets just passed the part where the colored lights in the splash screen come together as the Windows logo, then dies.  If I uncheck that, Windows installs.  When I go to run it, Windows boots up, but only if that box remains unchecked.  If I check it, Windows crashes.  

I'm at my wits end here.  I've googled and googled, but I'm stuck.  Does anyone know what the problem is?  Any help is appreciated.  

Btw, in case they're needed, here are my settings:  

```
General ==> Advanced
Shared Clipboard: Bidirectional
Drag'n'Drop: Bidirectional

System ==> Motherboard
Base Memory: 4096 MB
Boot Order:
Floppy, CD/DVD, Hard Disk
Pointing Device: USB Tablet

System ==> Processor
Processors: 1 CPU
Execution Cap: 100%
Extended Features: Enable PAE/NX not checked

Display ==> Video
Video Memory: 64 MB
Monitor Count: 1
Extended Features: 
Enable 3D Acceleration checked
Enable 2D Acceleration checked

Storage ==> Controller IDE:
IDE Secondary Master (and a very long file name for an iso file that I chose, which is my Windows 7 install iso)

Storage ==> Controller: SATA:
Win 7 x64 HD.vdi
Name SATA
Type AHCI
Port Count: 1

Audio
defaults

Network ==> Adapter 1
Enable Network Adapter checked
Attached to: NAT
Adapters 2, 3, & 4 not used

Serial Ports: Not enabled

USB:
Enable USB Controller checked
Enable USB 2.0 (EHCI) Controller -- if unchecked Windows 7 installs, but I have no USB access.  If checked, Windows 7 crashes before installing (right after the Windows 7 logo comes together).  If unchecked for the install and then checked before starting, Windows 7 crashes when attempting to boot up.  

Shared folders: 
/home/tommy/Shared

```

---

### Post by bashiergui on 2014-12-31
You install the guest additions into a guest. It looks like you installed it on your host. You would install win 7 as a guest, then install the guest additions in Win 7, then usb access will work.

---

