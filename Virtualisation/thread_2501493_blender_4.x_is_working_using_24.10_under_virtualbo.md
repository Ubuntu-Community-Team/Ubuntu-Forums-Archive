---
title: "blender 4.x is working using 24.10 under virtualbox not under 24.04 host"
date: 2024-10-10
forum: Virtualisation
---

### Post by Claus7 on 2024-10-10
Hello,

using ubuntu 24.10 under virtualbox, I tried to install blender found under the repos. I wasn't expecting it to work due to the fact that blender 4.x is not working under my 24.04 host due to the following errors:
> ./blender
EGL Error (0x3009): EGL_BAD_MATCH: Arguments are inconsistent (for example, a valid context requires buffers not supplied by a valid surface).
Warning: Unsupported platform as it supports max 0 SSBO binding locations
EGL Error (0x3009): EGL_BAD_MATCH: Arguments are inconsistent (for example, a valid context requires buffers not supplied by a valid surface).

Blender quit

I tried also using the command: 
```
MESA_GLSL_VERSION_OVERRIDE=460 MESA_GL_VERSION_OVERRIDE=4.6FC ./blender
```
which resulted in the following error:
> Warning: Unsupported platform as it supports max 0 SSBO binding locations

Blender quit

Under 24.10 inside vb is working fine though! 

The graphics card is an old amd evergreen.

Regards!

---

