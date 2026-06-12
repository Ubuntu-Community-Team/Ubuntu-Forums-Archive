---
title: "I cannot access at the 3D desktop"
date: 2016-02-04
forum: Ubuntu Studio
---

### Post by septicalmind on 2016-02-04
Hello,
Sorry, for my bad english, I'm french...
I have ubuntu studio 15.10 32 bits. All is running without problems.

My graphic card with the drivers from nvidia with open gl turns perfectly.

I have installed compiz. And I access to it and I can parameter it.

But, nothing happen in my desktop. All is in 2D mode.
In console with root :
glxinfo | grep "direct rendering"
direct rendering : yes

when I type : config --replace, there is no effect.

Thank for your help

---

### Post by monkeybrain20122 on 2016-02-04
What is the output of

```
glxinfo | grep OpenGL 
```?

Did you run

```
sudo nvidia-xconfig
``` after you install the Nvidia driver and before you reboot?

---

### Post by septicalmind on 2016-02-07
Thanks to you, I will try it. And i will post the result.
 But my install is ubuntu studio with Xcfe 4.

---

### Post by deadflowr on 2016-02-07
config --replace?
Did you mean 
compiz --replace?

---

### Post by septicalmind on 2016-02-08
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce GT 440/PCIe/SSE2
OpenGL core profile version string: 4.4.0 NVIDIA 352.63
OpenGL core profile shading language version string: 4.40 NVIDIA via Cg compiler
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 4.5.0 NVIDIA 352.63
OpenGL shading language version string: 4.50 NVIDIA
OpenGL context flags: (none)
OpenGL profile mask: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.1 NVIDIA 352.63
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.10
OpenGL ES profile extensions:

I have installed the original drivers from the constructor

---

### Post by septicalmind on 2016-02-11
Thanks to you all, I was resolve the problems.

---

