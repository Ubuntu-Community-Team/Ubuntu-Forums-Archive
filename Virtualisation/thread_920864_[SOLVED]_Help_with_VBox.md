---
title: "[SOLVED] Help with VBox"
date: 2008-09-15
forum: Virtualisation
---

### Post by Virtua-Touch on 2008-09-15
I was trying to install VBox on Ubuntu, and it failed, but now everytime I try to do it from Synaptic (I added VBox'x repositories after the installation failed) it says that VBox is installed already, when it isn't.

---

### Post by tuxxy on 2008-09-15
I would recommend you go download [VirtualBox 2.0 ]("http://www.virtualbox.org/wiki/Downloads")from their website, this is an updated version to the one you are trying to isntall, also make sure you select the PUEL licensed version not the OSE.

This new version provides support for 64-bit guest OS's amongst other thingss :)

---

### Post by Virtua-Touch on 2008-09-15
I've downloaded the .deb from the website for 2.0.2. This morning, it said I had to install two pacakges that started with 'lib' I'll check that out now.

---

### Post by tuxxy on 2008-09-15
You may just need some dependant files then before you install, try to install the lib packages it lists.

---

### Post by Virtua-Touch on 2008-09-15
Well, it installed perfectly with no erros. Yet, it doesn't show up in Applications.
(Main Menu)

---

### Post by Ptero-4 on 2008-09-15
Something to note about vbox 2 x64 guest support. It only works if your host CPU supports hardware virtualisation (Pentium DualCore and AMD Sempron are x64 CPU´s but lack VTx/AMDv hardware virtualisation) if your host CPU doesn´t, vbox silently emulates x86.
P.D: I know this b/c I got a laptop with a Pentium DualCore CPU and it can´t run x64 guests on vbox 2.

---

### Post by Virtua-Touch on 2008-09-15
I have 32-Bit/x86. I've just tried to install VBox from Terminal using sudo apt-get install virtualbox and it installed but no icon.

---

### Post by drs305 on 2008-09-15
You can make a shortcut for it. The terminal command is "VirtualBox" and the icon is "/usr/share/pixmaps/Vbox.png"

---

### Post by Virtua-Touch on 2008-09-16
It just decided to show up and it works great. Do I have to add myself to a group or do anything else beyond installation?

---

### Post by drs305 on 2008-09-16
> **Virtua-Touch said:**
> It just decided to show up and it works great. Do I have to add myself to a group or do anything else beyond installation?

It automatically added me to the group 'vboxusers'. You can check with "groups" in terminal. All you might want to do is check where it put your default folders and move them somewhere else if you wish. There wasn't much to do other than start creating your machines. ;-)

---

