---
title: "Ubuntu PXE Boot Solution"
date: 2014-03-02
forum: Ubuntu, Linux and OS Chat
---

### Post by xicarusx on 2014-03-02
Using Ubuntu Server 12.04LTS I have a home server with many bootable tools available via PXE. Including Ubuntu Live 12.04-13.10 32 and 64bit which i can install Ubuntu Desktop from. I also have Antivirus tools, Cloning Tools, Recovery Tools, Diagnostic Tools and other OS installers. I used this site as a base guide and added a lot of my own stuff [http://pxedust.icarey.net](http://pxedust.icarey.net). Does anyone else PXE boot their repair tools?

---

### Post by lykwydchykyn on 2014-03-03
Yeah, I set up a "magic PXE" network several years back at work to boot all kinds of tools and installers.  It doesn't get used as much any more since the other guys want to use winPE and I can't be bothered to go through what it takes to make that work with PXE.

---

### Post by xicarusx on 2014-03-03
The reason I am drawn to this one is that you can boot WinPE. I have been booting .wim images from a multitude of programs. Avast! AV, and a few others along with custom PE. 

I even made my own custom Windows 8.1 PE disk for doing diagnostics and removing malware, and it was extremely easy.

Installation was as easy as installing Ubuntu Server, running a script and configuring DHCP. Then to add a PE disk I used the Windows Deployment plugin provided and edited the menu file for my other PE images. 

It seems in the future other PE disks will be added to this project though.

---

