---
title: "OpenGL issues with VMware"
date: 2013-06-26
forum: Server Platforms
---

### Post by Scrumps on 2013-06-26
I have my ubuntu server 13.04 x64 server setup so that I connect to a virtual daemon, that then forwards the logins to newly created X sessions. So, I will connect my VNC Server to port 5999, and then after a successful authentication, it will setup session :5901/:1 and log me in to a new desktop. Same goes if another user logs in, it creates :5902/:2, and so on and so forth (the manual for this is [here]("http://www.realvnc.com/products/vnc/documentation/5.0/misc/reference/vncserver-virtuald.html")).

Anyways, this causes a problem for me (at least I think this is the cause of the problem), when I go to run things like glxgears or vmware I get the following error message:
Xlib:  extension "NV-GLX" missing on display ":1".

If I am running VMware workstation, and I try to use any form of 3D acceleration, I get an error stating that I am not running an appropriate driver, even though I am running:
lspci
06:00.0 VGA compatible controller: NVIDIA Corporation GF119 [GeForce GT 520] (rev a1)

dpkg --list
ii  libkwinnvidiahack4                                          4:4.10.3-0ubuntu0.1~ubuntu13.04      amd64        library used by nvidia cards for the KDE window manager
ii  nvidia-304                                                  304.88-0ubuntu1                      amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-current                                              304.88-0ubuntu1                      amd64        Transitional package for nvidia-current
ii  nvidia-settings-304                                         304.88-0ubuntu1                      amd64        Tool for configuring the NVIDIA graphics driver


Now, I am not sure how to go about resolving this, so that I can use 3D acceleration in Vmware or any other program over VNC. But it seems like I would need to setup something in Xorg (or relevant file), or setup something in a vncserver config file that allows me to do pass throughs for driver extensions.

I was wondering if anyone knew how to do this, or if someone could point me in the right direction.

EDIT:

I just upgraded the RAM in the machine, so I had the chance to physically login, the same issue occurs. I am unable to get 3D Acceleration to work with VMware. So, I guess how am I supposed to enable 3D Acceleration on VMware?

---

