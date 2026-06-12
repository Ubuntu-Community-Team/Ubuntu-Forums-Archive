---
title: "Disconnection of AMT (IDE-R) during installer loading"
date: 2021-08-09
forum: Server Platforms
---

### Post by jsuchecki on 2021-08-09
Hello,

I'm not sure if it is correct section. I tried to set up Ubuntu Server 20.04.2 LTS using AMT remote control. ISO image (shared by LAN) boots successful and does checking if image integrity. Problem begins before loading installer's first screen (language selection). It simply breaks connection with AMT and it cannot be restored without computer reboot. If it's some known issue? I searched for solution but without results. Installer doesn't crash, somebody looked for monitor locally. 

Best wishes

---

### Post by MAFoElffen on 2021-08-09
intel AMT allows KVM over IP... Which it sounds almost like you are having an issue with the tool you are using to connect via Intel AMT. I haven't heard any problems connecting to the Ubuntu server install iso itself, via KVM over IP, through Intel AMT, or other BCM KVM over IP connections. Even through console or serial console... that is more of a transport/connection issue of the machine, whether physical or virtual.... Not what is running on it. As what the graphics and such of the installer is right now.

What tool are you using and via what? (Mesh Commander, Radmin, Dameware, other?)

---

### Post by jsuchecki on 2021-08-10
Thank you for reply. I'm using Mesh Commander (running on Win10) as client. OnLogic Helix 500 is machine where I want to install Ubuntu.

Edit:
I see now that IP was changed. AMT works on a new but it is still some amazing that address is not constant during installation.

---

### Post by MAFoElffen on 2021-08-10
Yes. A bit strange. Do you have the Intel AMT IP set as DHCP shared or Static Shared?

---

### Post by jsuchecki on 2021-08-10
AMT IP is set to DHCP mode in MBEx. I didn't configure IP reservation based on MAC in router but anyway this IP directly after machine power-up is always the same. Maybe it's related with host name (Ubuntu's installer changes it for 'Ubuntu-Server')?

---

### Post by MAFoElffen on 2021-08-10
Could be. Have you tried it with an auto install script? (that sets everything to what you need) That would override those specifics/changes, and keep it more controlled.

Just an idea...

---

