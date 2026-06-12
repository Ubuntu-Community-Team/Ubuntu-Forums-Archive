---
title: "OpenGL with OS X 10.9 + VirtualBox 4.3.4 + Ubuntu 13.10"
date: 2013-12-08
forum: Virtualisation
---

### Post by fogleman on 2013-12-08
Hello. I am running Ubuntu in VirtualBox with an OS X host. I am trying to test an OpenGL application that needs GL shader language 3.3 or higher, but glxinfo is reporting 1.20.

glxinfo | grep OpenGL shows:

OpenGL vendor string: Humper
OpenGL renderer string: Chromium
OpenGL version string: 2.1 Chromium 1.9
OpenGL shading language version string: 1.20
OpenGL extensions:

I have installed the VirtualBox guest additions and I have tried increasing the video memory to 128 MB and I have tried enabling and disabling 3D acceleration in VirtualBox.

What can I do to get a newer shading language version? I've seen much higher versions searching Google with the same Chromium version.

Thanks!

---

