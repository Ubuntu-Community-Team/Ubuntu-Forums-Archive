---
title: "Can someone explain what gallium3d is?"
date: 2009-05-18
forum: The Cafe
---

### Post by nolliecrooked on 2009-05-18
Ive seen loads about it, but never much detail to what it actually does.

---

### Post by starcannon on 2009-05-18
gallum3d is my precious.

Gallium3d however is:
> 
**Gallium3D** is a [software library]("http://en.wikipedia.org/wiki/Software_library") for [3D graphics]("http://en.wikipedia.org/wiki/3D_computer_graphics") [acceleration]("http://en.wikipedia.org/wiki/Hardware_acceleration") being developed by [Tungsten Graphics]("http://en.wikipedia.org/w/index.php?title=Tungsten_Graphics&action=edit&redlink=1"), an engineering company with expertise in Linux and open-source graphics technologies. Gallium3D operates as a layer between the graphics [API]("http://en.wikipedia.org/wiki/Application_programming_interface") and the [operating system]("http://en.wikipedia.org/wiki/Operating_system") with the primary goal of making [driver]("http://en.wikipedia.org/wiki/Device_driver") development easier, bundling otherwise duplicated code of several different drivers at a single point. This is done by providing a better division of labour (for example, leaving memory management to the kernel [DRI]("http://en.wikipedia.org/wiki/Direct_Rendering_Infrastructure") driver) and to support modern hardware architectures.
 Gallium3D provides a unified [API]("http://en.wikipedia.org/wiki/Application_programming_interface") exposing standard hardware functions such as shader units found on modern hardware. Thus, 3D APIs such as [OpenGL 1.x/2.x]("http://en.wikipedia.org/wiki/OpenGL"), [OpenGL 3.x]("http://en.wikipedia.org/wiki/OpenGL#OpenGL_3.0"), [OpenVG]("http://en.wikipedia.org/wiki/OpenVG"), [GPGPU]("http://en.wikipedia.org/wiki/GPGPU") infrastructure or even [Direct3D]("http://en.wikipedia.org/wiki/Direct3D") (as found in the [Wine]("http://en.wikipedia.org/wiki/Wine_%28software%29") compatibility layer) will need only a single back-end, called state tracker, targeting Gallium3D API. By contrast [Mesa 3D]("http://en.wikipedia.org/wiki/Mesa_3D") requires a different backend for each hardware platform, and several other APIs need translation to OpenGL at the expense of further overhead.[[1]]("http://en.wikipedia.org/wiki/Gallium3D#cite_note-0")[[2]]("http://en.wikipedia.org/wiki/Gallium3D#cite_note-1")[[3]]("http://en.wikipedia.org/wiki/Gallium3D#cite_note-2") In addition, using the modular structure of Gallium3D, there are works underway to leverage the [LLVM]("http://en.wikipedia.org/wiki/Low_Level_Virtual_Machine") compiler suite and create a module to optimize shader code on the fly.[[4]]("http://en.wikipedia.org/wiki/Gallium3D#cite_note-3")
 Under Gallium3D, DRM ([Direct Rendering Manager]("http://en.wikipedia.org/wiki/Direct_Rendering_Manager")) kernel drivers will manage the memory, and DRI ([Direct Rendering Interface]("http://en.wikipedia.org/wiki/Direct_Rendering_Infrastructure")) driver (now called DRI2) will be more GPU processing oriented. This will resolve memory management problems whose solutions are considered infeasible under Mesa 3D.[[5]]("http://en.wikipedia.org/wiki/Gallium3D#cite_note-4")
 Gallium3D represents each shader program using an extensible binary intermediate representation called Tungsten Graphics Shader Infrastructure (TGSI). When Gallium targets LLVM the TGSI code is converted to the LLVM [instruction set]("http://en.wikipedia.org/wiki/Low_Level_Virtual_Machine#Code_representation").
[http://en.wikipedia.org/wiki/Gallium3D](http://en.wikipedia.org/wiki/Gallium3D)

---

### Post by nolliecrooked on 2009-05-18
> **starcannon said:**
> gallum3d is my precious.

Gallium3d however is:

[http://en.wikipedia.org/wiki/Gallium3D](http://en.wikipedia.org/wiki/Gallium3D)

  cheers (y)

---

### Post by nolliecrooked on 2009-05-18
BTW is the code for this gonna be open-sourced?

---

### Post by GeneralZod on 2009-05-18
> **nolliecrooked said:**
> BTW is the code for this gonna be open-sourced?

It's available under the MIT license (again, from the Wiki article ;))

---

### Post by gnomeuser on 2009-05-18
> **nolliecrooked said:**
> BTW is the code for this gonna be open-sourced?

Please for the sake of your own and our collective sanity, can you please do just the tiniest bit of research before asking questions. 

Remember most questions have been answered before, you don't need a developer to help you install the nvidia driver on Fedora e.g. like you asked me to help with last night. 

This one was even answered in the wikipedia article you got linked earlier. 

It doesn't hurt to try on your own, then if you fail I am perfectly sure someone will help you.

---

### Post by nolliecrooked on 2009-05-18
> **gnomeuser said:**
> Please for the sake of your own and our collective sanity, can you please do just the tiniest bit of research before asking questions. 

Remember most questions have been answered before, you don't need a developer to help you install the nvidia driver on Fedora e.g. like you asked me to help with last night. 

This one was even answered in the wikipedia article you got linked earlier. 

It doesn't hurt to try on your own, then if you fail I am perfectly sure someone will help you.

I did try on my own, 4 times, by following the instructions from the Fedora Forum F11 nVidia how-to sticky. I did everything it said, but alway got a black screen of death. And like I said to you in the PM's, Fedora really needs to learn to be more user friendly. 

BTW I do try to do as much research as I can, but not everything is always clearly documentated.

---

### Post by starcannon on 2009-05-18
> **nolliecrooked said:**
> I did try on my own, 4 times, by following the instructions from the Fedora Forum F11 nVidia how-to sticky. I did everything it said, but alway got a black screen of death. And like I said to you in the PM's, Fedora really needs to learn to be more user friendly. 

BTW I do try to do as much research as I can, but not everything is always clearly documentated.

When first learning, I generally recommend staying off the bleeding edge. Go with a nice Long Term Support release if your using Ubuntu; generally most of the snags are worked out, or simple to deal with. Ubuntu 8.04 is a great release, the Hardware Driver manager gets along famously with Nvidia and ATi, and you should be in a situation to learn your way around the OS in bite size pieces that way. Anyway just my .02, and its probably only worth .01.

GL

---

### Post by nolliecrooked on 2009-05-18
> **starcannon said:**
> When first learning, I generally recommend staying off the bleeding edge. Go with a nice Long Term Support release if your using Ubuntu; generally most of the snags are worked out, or simple to deal with. Ubuntu 8.04 is a great release, the Hardware Driver manager gets along famously with Nvidia and ATi, and you should be in a situation to learn your way around the OS in bite size pieces that way. Anyway just my .02, and its probably only worth .01.

GL

8.04 is great if you have an ATi card, but theres a major bug with it which means any nVidia driver beyond some obscure beta version of 177 will not work.

---

### Post by starcannon on 2009-05-18
I'm using 180's right now on twin sli 7950gt's under 8.04 no problems.

---

### Post by nolliecrooked on 2009-05-18
> **starcannon said:**
> I'm using 180's right now on twin sli 7950gt's under 8.04 no problems.

Seriously??????????

HOW did you install them? :D

Theres loads of bug reports on Launchpad for this issue.

---

### Post by sim-value on 2009-05-18
> **nolliecrooked said:**
> I did try on my own, 4 times, by following the instructions from the Fedora Forum F11 nVidia how-to sticky. I did everything it said, but alway got a black screen of death. And like I said to you in the PM's, Fedora really needs to learn to be more user friendly. 

BTW I do try to do as much research as I can, but not everything is always clearly documentated.

> **starcannon said:**
> When first learning, I generally recommend staying off the bleeding edge. Go with a nice Long Term Support release if your using Ubuntu; generally most of the snags are worked out, or simple to deal with. Ubuntu 8.04 is a great release, the Hardware Driver manager gets along famously with Nvidia and ATi, and you should be in a situation to learn your way around the OS in bite size pieces that way. Anyway just my .02, and its probably only worth .01.

GL

> **nolliecrooked said:**
> 8.04 is great if you have an ATi card, but theres a major bug with it which means any nVidia driver beyond some obscure beta version of 177 will not work.

> **starcannon said:**
> I'm using 180's right now on twin sli 7950gt's under 8.04 no problems.

> **nolliecrooked said:**
> Seriously??????????

HOW did you install them? :D

Theres loads of bug reports on Launchpad for this issue.
Offtopic at its finest ...

OT: looks awesome ...
Though i dont care how it works as long i get my HDR :D

---

