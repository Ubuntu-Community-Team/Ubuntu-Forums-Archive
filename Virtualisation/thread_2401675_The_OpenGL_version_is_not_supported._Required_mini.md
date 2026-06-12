---
title: "The OpenGL version is not supported. Required minimum OpenGL 3.3."
date: 2018-09-20
forum: Virtualisation
---

### Post by Jason_Hunter on 2018-09-20
[[IMG]https://communities.vmware.com/people/famadorian/avatar/46.png?a=4018[/IMG]]("https://communities.vmware.com/people/famadorian")[IMG]https://communities.vmware.com/8.0.4.21bdc7e/images/status/lurker-16x16.gif[/IMG]
[FONT=inherit]**[Jason Hunter]("https://communities.vmware.com/people/famadorian")** Sep 18, 2018 2:55 PM[/FONT][FONT=inherit]My host is Ubuntu 18.04[/FONT]
[FONT=inherit] [/FONT]
[FONT=inherit]I'm trying to run ArchiCAD-22 in a Windows-10 guest, but I get the message:[/FONT]
[FONT=inherit] [/FONT]
[FONT=inherit]OpenGL has been disabled: The OpenGL version is not supported. Required minimum OpenGL 3.3.[/FONT]
[FONT=inherit] [/FONT]
[FONT=inherit]However, when I start up OpenGL Extensions Viewer, I see that it reports "3.3 (Core Profile) Mesa 17" and I even am able to run the 3.3 tests, which draws an OpenGL test box on the screen.[/FONT]
[FONT=inherit] [/FONT]
[FONT=inherit]Any idea what can be wrong here?[/FONT]
[FONT=inherit] [/FONT]
[FONT=inherit]My GPU is:[/FONT]
[FONT=inherit] [/FONT]
[FONT=inherit]01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Curacao XT / Trinidad XT [Radeon R7 370 / R9 270X/370X][/FONT]
[FONT=inherit] [/FONT]
[FONT=inherit]I did a clean Windows 10 install in VMWare Workstation Player 14.1.3 build-9474260, so I've confirmed that:[/FONT]
[FONT=inherit] [/FONT]
[FONT=inherit]virtualHW.version = "14"[/FONT]
[FONT=inherit] [/FONT]
[FONT=inherit]I have no problems running ArchiCAD-21 or previous versions. [/FONT]
[FONT=inherit] [/FONT]
[FONT=inherit]Any pointers as to what I can try?[/FONT]

---

### Post by Jason_Hunter on 2018-09-30
Nobody has any clue?

I've now updated to Workstation Player 15 and updated my graphics card to Radeon RX Vega 64, but still same. I've also updated the kernel and Mesa.

---

