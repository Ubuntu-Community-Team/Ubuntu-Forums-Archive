---
title: "3D acceleration does not work in VMware Player"
date: 2008-06-17
forum: Virtualisation
---

### Post by deconstruct on 2008-06-17
Hello,

I can't get 3d acceleration to work in VMware Player 2.04 64bit running on Ubuntu Linux 8.04 64bit. 
The vmplayer is installed correctly and works, as I can boot without any problems into my 
Windows XP vmware image (SP2, VMware tools installed) and everything works (network, sound, etc)

But if I activate 3d-acceleration in the VMX-file like this...

mks.enable3d = "TRUE"
vmmouse.present = "FALSE"

... then vmware player crashes at startup with an unrecoverable error.
Here is the part of the LOG-file with the information about the crash:

Jun 17 11:51:54.349: mks| Current OpenGL Version: 2.1.7412 Release major: 2, minor: 1, release: 7412 
Jun 17 11:51:54.349: mks| GLUtil_InstallExtensionLists: Missing extension GL_ARB_imaging
Jun 17 11:51:54.349: mks| GLUtil_InstallExtensionLists: Missing extension GL_NV_texture_shader
Jun 17 11:51:54.350: mks| Using FBO
Jun 17 11:51:54.390: mks| glXMakeCurrent failed!! (0:no error).
Jun 17 11:51:54.390: mks| Panic: dropping lock (was bug 49968)
Jun 17 11:51:54.390: mks| NOT_REACHED /build/mts/release/bora-93057/bora/mks/hostops/GL/backend/GLHostX.c:410
....
Jun 17 11:51:54.399: mks| Msg_Post: Error
Jun 17 11:51:54.399: mks| [msg.log.error.unrecoverable] VMware Player unrecoverable error: (mks)
Jun 17 11:51:54.399: mks| NOT_REACHED /build/mts/release/bora-93057/bora/mks/hostops/GL/backend/GLHostX.c:410


I have an ATI HD3200 graphics card and I use the ATI Catalyst 8.5 driver (fglrx) on a
linux kernel 2.6.24-18. In my linux host OS the 3D acceleration works great, as
I can run 3d games like quake3 or apps like google earth.

fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3200 Graphics
OpenGL version string: 2.1.7412 Release

$ glxinfo 
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2


Does anyone have an idea what causes this crash and how i can get 3d-acceleration
in VMware Player to work? I would be glad, if someone could help here.

---

### Post by LordMoonstone on 2008-06-29
Just a helpful bump. 

I'm having the same problem, and searching for the error message (VMware Workstation unrecoverable error: (mks)
NOT_REACHED /build/mts/release/bora-93057/bora/mks/hostops/GL/backend/GLHostX.c:410) yields nothing. 

I want to say it's something with OpenGL, but I have no clue what I'm talking about. As deconstruct points out, *is* it a problem with the ATI drivers? 
I'm running a HD2400 however; but still on the same kernel (as far as I know..).

3D acceleration works fine from what I can tell and direct rendering is set and glxgears runs quite smoothly. 

Anyone got anything?

---

### Post by MyFreakinUserName on 2008-07-24
I have ATI Radeon HD 3650, and VMware Workstation 6.0.4 gives me the same when I try to enable 3D:
NOT_REACHED /build/mts/release/bora-93057/bora/mks/hostops/GL/backend/GLHostX.c:410

I use fglrx version 8.6, no compiz/beryl.
fgl_glxgears and glxgears work fine.

Just wondering what do you have in your /etc/X11/xorg.conf section Device,
do you have **UseFastTLS** enabled?

aticonfig manual says that you should disable it if you have problems with virtual machines or wine.

Thus, maybe the following could help:
**aticonfig --initial --tls=off**

Another thought would be to try the very latest fglrx drivers (8.7) from AMD site.:confused:

I have not tried it myself yet, will play with it on weekend...

---

