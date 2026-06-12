---
title: "New UBUNTU Server"
date: 2018-02-19
forum: Server Platforms
---

### Post by glassonion on 2018-02-19
I have a vps with ubuntu installed. 

I have performed the following to install the desktop UI:> [COLOR=#333333][FONT=&amp]Sudo apt-get update[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Sudo apt-get upgrade[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Sudo apt-get install ubuntu-desktop[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Sudo apt-get install dkms[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Sudo reboot?[/FONT][/COLOR]
My goal is to access the desktop rather than the command line. How can I, or what do I need to connect between my windows box and ubuntu server so I can enjoy the desktop.

---

### Post by wildmanne39 on 2018-02-19
*Thread moved to **Server Platforms, a more appropriate forum**.*

---

### Post by QIII on 2018-02-20
Somebody may be along shortly to answer your question directly. But before that, let me say something about the accepted standard practice with Linux servers:  They are not run with GUIs, especially when exposed to the web.  Servers should be run with the barest minimum of services necessary to perform their intended purposes.  

A GUI adds a plethora of services that form dangerous attack surfaces.  You may "enjoy" your GUI by being compromised.

Just my two cents before you find yourself having a significant emotional event.

---

### Post by wyliecoyoteuk on 2018-02-20
If you want to connect via remote desktop, you will need VNC server (and vnc client on the windows Pc)

---

### Post by mastablasta on 2018-02-21
if however you want a GUI to administer the server on server, then using a webgui is an option. 

investigate Zentyal, Ajenti, Openmediavault (Debian)...

there is a bunch of hosting or control panels available. many are free, some are free only for home use. some are tied to specific distro, others work on various platforms.

---

