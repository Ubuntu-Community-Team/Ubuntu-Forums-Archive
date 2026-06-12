---
title: "Using wireless card in Ubuntu 7.04 virtual machine"
date: 2007-05-02
forum: Server Platforms
---

### Post by Siph0n on 2007-05-02
I have VMWare installed on my Windows XP computer with a Dynex wireless card, and I also have a virtual machine of Ubuntu 7.04. Right now it's using a bridged connection for internet access, but I want it to see the Dynex wireless card and use that for the internet connection. Any ideas? I tried looking in the Network Manager tool, but all I saw was the Wired Connection. Also, in the VMWare program itself, I see the devices/specs of my virtual machine. Like how much memory it will have, the cdrom drive, the floppy drive, and also Ethernet. Ethernet is where I set it to use a bridged connection. Is it my wireless card that just isn't compatible with Ubuntu 7.04, or is it a VMWare problem? Any help would be appreciated, thanks! :)


Siph0n

---

### Post by Carlos Santiago on 2007-05-02
What wireless card are you using?
I use a Novatel Merlin u630 and it works fine.

The drivers were there, but I had to make some configurations on the following files: 
/etc/chatscripts/provider and 
/etc/ppp/peers/provider

and also on the udev rules:
/etc/udev/rules.d/85-pcmcia

---

### Post by Siph0n on 2007-05-02
I'm not at home right now, but it has to be either DX-WGDTC or DX-WGPDTC  , by Dynex..... I'm leaning towards the first one! :) I'll try to do some searches on that card in the forum and see what comes up. But just to clarify Carlos, you are running windows with a ubuntu virtual machine? Or are you sure its not a VMWare problem, and that it's more of a problem with my wireless card?

Siph0n

---

