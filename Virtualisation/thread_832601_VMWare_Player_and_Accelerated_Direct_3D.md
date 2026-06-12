---
title: "VMWare Player and Accelerated Direct 3D"
date: 2008-06-17
forum: Virtualisation
---

### Post by Zaiden on 2008-06-17
I've been trying to get Ragnarok online to run in WINE, but every attempt is just a large failure. So after doing some looking around, I came across [a video of Ragnarok Online running in VMWare Player]("http://www.youtube.com/watch?v=KqccoZzO1CU").

Without much knowledge of the virtual machines, I installed Server first, and managed to have direct3d acceleration working, but anything in 3D brought up a white screen. Then I found it it only works in Workstation and Player.

So I installed player, made an image through [EasyVMX]("http://www.easyvmx.com/"), and got everything to run including VMWare Tools and, after that, DirectX 9.

Problem starts when I run dxdiag. For some reason, Direct3D isn't enabled. I did check the .mpx file for the three lines (mks.enable3d = TRUE, svga.vramSize = 67108864, and vmmouse.present = FALSE), but with it, it still doesn't work. Before I installed the Player image, I tried running the old Server XP installation, and direct3D was detected, but I recieved an error when trying to run something 3D (AKA: RO).

Would anyone have any possible idea what I should do/change/etc? I'm trying to avoid a Dual Boot into XP, because I know I'll probably load XP up more often than Ubuntu, and I don't want that to happen...

My System specs are:

Ubuntu 8.04 Hardy Heron AMD64
AMD 64X 5400 Dual Core
2GB RAM
Nvidia 8800GTS 320MB

---

### Post by deconstruct on 2008-06-18
Do you use the binary NVidia driver and does your 3d acceleration and opengl work in ubuntu?
What happens if you run "glxgears" in a terminal?
What output do you get when you run "glxinfo"

If you use the driver and opengl works, you could check the log-file that vmware player creates, when you run the virtual machine. Its in the same directory like the vmx file and has the same name with a .log extension. 

In the log file search for lines containing "mks". You should at least see lines like:

[FONT="courier"]Jun 17 11:53:38.607: vmx| DICT   mks.enable3d = TRUE
Jun 17 11:53:39.084: mks| Async MKS thread is alive
Jun 17 11:53:55.122: mks| Connecting to window system.
Jun 17 11:53:55.122: mks| XINFO X fd is 53
....
Jun 17 11:53:55.133: mks| GLPrimaryInit3D, thread mks
Jun 17 11:53:55.136: mks| GLPrimaryHostConnect thread mks
....
Jun 17 11:53:55.293: mks| Current OpenGL Version: 2.1.7412 Release major: 2, minor: 1, release: 7412

[/FONT]
Look out, if you see error messages. At my pc vmware 3d accereration does not work either, i get the following error messages.

[FONT="courier"]Jun 17 11:53:55.293: mks| GLUtil_InstallExtensionLists: Missing extension GL_ARB_imaging
Jun 17 11:53:55.293: mks| GLUtil_InstallExtensionLists: Missing extension GL_NV_texture_shader
Jun 17 11:53:55.293: mks| Using FBO
Jun 17 11:53:55.335: mks| glXMakeCurrent failed!! (0:no error).
Jun 17 11:53:55.335: mks| Panic: dropping lock (was bug 49968)
Jun 17 11:53:55.335: mks| NOT_REACHED /build/mts/release/bora-93057/bora/mks/hostops/GL/backend/GLHostX.c:410[/FONT]

If somebody has a clue what causes this or has the same problem, I would be glad if he could answer in [my thread]("http://ubuntuforums.org/showthread.php?t=831788"). I assume, it could be a problem with the ATI drivers?

---

### Post by Zaiden on 2008-06-18
Not sure how, but the problem seemed to have fixed itself. I ran the vmx file that was created in Workstation (That I installed today to test out) in Player as a test, and oddly direct3d was enabled. I could even play RO finally, though with some performance issues.

My guess is that either having Workstation installed along side player fixed it, or the vmx file Workstation created was better than the one I made from the EasyVMX website.

---

