---
title: "Need to get Dedicated Graphics working with OpenGL on Windows Subsystem for Linux"
date: 2017-03-18
forum: Windows
---

### Post by yodawgitsodawg on 2017-03-18
Hi all, I'm pretty new at this (a few months experience) so please forgive anything that might seem obvious to you.

I've spent the last day or so setting up Windows Subsystem for Linux on my laptop. I've got it mostly working on the integrated graphics chip (Intel HD 520).
See results below;

```

glxinfo | grep OpenGL
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.4, 256 bits)
OpenGL version string: 2.1 Mesa 10.1.3
OpenGL shading language version string: 1.30
```

glxgears runs smoothly, I can boot up quake from the bash terminal and its all pretty good.

However, this semesters project requires us to write programs for OpenGL 3.2, and as you can see, my laptop won't support it right now, it's only running OpenGL 2.1. I'm fairly sure that I've reached the point that I can't run a newer version of OpenGL unless it's supported by the Nvidia 940MX GPU.

If I install the nvidia-378 drivers, glxinfo returns:

```

name of display: :0
Error: couldn't find RGB GLX visual or fbconfig
Error: couldn't find RGB GLX visual or fbconfig

```

If I uninstall them again, I can then use OpenGL.

I've spent a while trying to get past this wall, I feel so close but I'm not sure what the next step is.

---

### Post by QIII on 2017-03-18
Hello!

Forgive my ignorance, but what is "Windows Subsystem for Linux"?

---

### Post by yodawgitsodawg on 2017-03-18
Hey, no worries.

Windows 10 supports a compatability layer for running Linux executables, and it's not a VM. Not really sure how else to describe it.

[https://msdn.microsoft.com/en-au/commandline/wsl/install_guide](https://msdn.microsoft.com/en-au/commandline/wsl/install_guide)

It's super neat, let's me use the majority of Linux features in Windows, even browse my windows files in the bash terminal. It runs Ubuntu 14.04.

Have a google, it's pretty neat.

---

### Post by QIII on 2017-03-18
OK.  Yes, I've read about that.

Since it is a Windows thing, however, I've moved this to the Windows subforum for a better fit.  This is more likely where folks who have experience will hang out.

---

### Post by yodawgitsodawg on 2017-03-18
Thanks for that.

---

