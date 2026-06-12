---
title: "Warcraft III, First run ok, second run crashed"
date: 2010-08-21
forum: Wine
---

### Post by ALF102 on 2010-08-21
Ok, I try to run Warcraft II: Frozen Throne for the frst time using wine 1.2. I use the following commands:

alfy102@alfy102-laptop:~$ env WINEPREFIX="/home/alfy102/.wine" wine "/home/alfy102/War3/w3/Frozen Throne.exe" -opengl
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x33f108,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5d4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f60c,0x00000000), stub!
alfy102@alfy102-laptop:~$ fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub

after I played for a while I exit it. Then when I want to run the game again it crashed. This is what I got from the terminal:

alfy102@alfy102-laptop:~$ env WINEPREFIX="/home/alfy102/.wine" wine "/home/alfy102/w3/Frozen Throne.exe" -opengl
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x33f108,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5d4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f60c,0x00000000), stub!


and this is the error message from the game:

This application has encountered a critical error:

FATAL ERROR!

Program:        Z:\home\alfy102\w3\war3.exe
Exception:      0xC0000005 (ACCESS_VIOLATION) at 0073:67AF4821

The instruction at '0x67Af4821' reference memory at '0xC0000002C'
The memory could not be 'read'



Then when I press ok, it asked me to enter the Frozen Throne CD

---

### Post by ALF102 on 2010-08-22
does this have anything to do with my graphic? If so, how do I check my graphic driver?

---

### Post by ALF102 on 2010-08-31
ok its been a week and there's no reply.

Recently I try to get Wine 1.3 and guess what the same problem occurs, I can run it for the first time after installing wine but I can't run it again after I close the game. What really makes me ticks off is that my friend got the same graphic driver as me, same wine version, and same settings as me but he can run the game smoothly using the -opengl command.

Here's an extra info:


00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
02:00.0 Ethernet controller: Atheros Communications Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

and even our terminal output is the same but I'm the one who can't run the game.

---

### Post by Rasa1111 on 2010-08-31
might want to consider it as a blessing. lol

---

### Post by ALF102 on 2010-08-31
Why's that?

---

### Post by ALF102 on 2010-09-01
Solved it. I've downgrade my wine version from 1.2 to 1.0.1. Now I can run it flawlessly

---

