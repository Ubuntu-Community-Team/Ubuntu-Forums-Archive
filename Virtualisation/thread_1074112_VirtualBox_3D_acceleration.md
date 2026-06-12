---
title: "VirtualBox 3D acceleration"
date: 2009-02-18
forum: Virtualisation
---

### Post by ov3rcl0ck on 2009-02-18
Most people think that 3D support isn't offered in VirtualBox. But as of version 2.1.0 it supports OpenGL only, take a look at this link [http://jeremy.visser.name/2008/12/18/virtualbox-210-does-opengl-3d-acceleration/]("http://jeremy.visser.name/2008/12/18/virtualbox-210-does-opengl-3d-acceleration/"). Your probably thinking "Hey OpenGL, I can probably run it in wine, or it is probably already available for linux.", but what most people don't know is that there is a DirectX OpenGL wrapper that allows you to emulate DirectX using OpenGL, however the project is still in alpha-3 stage you can still get it from sourceforge, [http://sourceforge.net/projects/dxglwrap]("http://sourceforge.net/projects/dxglwrap"). So you could install Vbox, setup windows, install the wrapper, and play a DirectX game using 3D acceleration(if you have 3D acceleration on your host box). I still have yet to try this and I will later post more about it. Feel free to post about how you did it and how to get it working.

---

### Post by yther on 2009-02-18
Well, I'm interested in this.  I like VirtualBox' interface more than VMware Player's, and I somehow doubt that direct graphical acceleration would work using VMware Server, although I haven't tried it.

When I last looked at this, it seemed very "blue sky" priority, so I thought, "Hm, maybe in a year or so..."  Please let us know what sort of results you get!

---

### Post by iheartubuntu on 2009-02-19
I had a couple games I tried in my VB XP and the games wouldnt play. They both use 3D acceleration and my video card is an nVidia with 512mb of memory on board. Would be cool to get it working!

---

### Post by iheartubuntu on 2009-02-19
Hmmm. So I wonder what the purpose of 3D virtualization is? Will it allow me to play my FIFA 2008?

---

### Post by Vadi on 2009-02-19
There isn't much point in using Virtualbox for 3d since from what I understand, it makes use of Wine to accomplish this.

---

### Post by ov3rcl0ck on 2009-11-08
Well right now Vbox released i think its version 3 which has support for DirectX 3D acceleration. I know this thread was started awhile ago, but the wrapper did work for a few games, just horrible performance since you're emulating in an emulator. I would never recommend it, the performance is just way way too horrible, and Vbox's DX support is much better.

---

### Post by kio_http on 2009-11-09
Virtualbox 3.0 uses Wined3d! So it actually converts DirectX signals to OpenGl for its virtual graphics adapter.

---

### Post by ov3rcl0ck on 2009-11-09
It is pretty slow, but it will run games at decent speeds if you have good specs.

---

### Post by blur xc on 2009-11-09
I tried Lego Digital Designer on Vista running in VBox and it still doesn't work.  It hangs on the "searching for hardware" part of the installation.  Maybe it'd work better w/ xp or something, but that I don't have.  I have hope though, the VBox guys crank out fixes and updates pretty quickly, so maybe sometime soon in the future it'll work.

BM

---

