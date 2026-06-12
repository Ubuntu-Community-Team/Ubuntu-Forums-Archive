---
title: "How do I update my OpenGL"
date: 2014-10-22
forum: Ubuntu Application Development
---

### Post by razzvg on 2014-10-22
Hi,

I've been searching the foums but the posts kinda look outdated.
I have to write a project for class using the qtlibs and QtCreator. My freshly installed Ubuntu comes with OpenGL3 drivers. However I am getting weird display bugs as you can see below. I was told updating to OpenGL4 but I don't know how to since the newest Versions of OpenGL come with the corresponding gpu drivers. But there are no new drivers available for my system regarding the update manager.
[ATTACH=CONFIG]257439[/ATTACH]
> glxinfo | grep "OpenGL"
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Haswell Mobile 
OpenGL core profile version string: 3.3 (Core Profile) Mesa 10.1.3
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 10.1.3
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:


I am using an Intel i5-4200U CPU with Intel HD Graphics 4400. Hope you guys have a fix for me :(.

---

### Post by mörgæs on 2014-10-23
Hi, welcome to the fora.

Mesa 10.1.3 indicates that you are running Ubuntu 14.04.
Have you tried 14.10?

---

### Post by razzvg on 2014-10-23
Just upgraded to Ubuntu 14.10 Mesa Version is 10.3 now but it won't fix my Error

---

