---
title: "No 3D Unity with Geforce4 MX440?"
date: 2012-04-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Diskdoc on 2012-04-04
Trying out Precise and I can see there's no longer a proprietary Nvidia driver available! Why?

Booting up the system with Noveau as my only option leave me with a needlessly sluggish Unity 2D desktop. Checking

> /usr/lib/nux/unity_support_test -p

gives

> OpenGL vendor string:   Nouveau
OpenGL renderer string: Mesa DRI nv18 x86/MMX+/3DNow!+/SSE
OpenGL version string:  1.2 Mesa 8.0.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        no
GL fragment program:      no
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       no

Unity 3D supported:       no


Is this like it's supposed to be or did something go wrong updating from Lucid? I'm fairly sure I'd have better 3D support with NVidias proprietary driver.

---

### Post by ronacc on 2012-04-04
nvidia-96 should be available in synaptic .

---

