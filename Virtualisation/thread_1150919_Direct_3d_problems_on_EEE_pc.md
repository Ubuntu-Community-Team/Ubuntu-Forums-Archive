---
title: "Direct 3d problems on EEE pc"
date: 2009-05-06
forum: Virtualisation
---

### Post by Vaati on 2009-05-06
Ok so after recently picking up an EEE pc 1000HA I decided to installl Ubuntu, not a hitch there, vutting to the chase I've installed the latest version of vmware workstation (6.5.2) and after installing windows xp and vmware tools I cannot get Direct 3d working any help would be greatly appreciated

---

### Post by Vaati on 2009-05-10
bump...

---

### Post by juancarlospaco on 2009-05-10
Use Virtualbox,
*eee have Intel Graphics, Drivers Sucks...*

---

### Post by lukeiamyourfather on 2009-05-11
Virtual machines don't have any 3D acceleration with the exception of VirtualBox which has very limited 3D acceleration for OpenGL only that uses the host's graphics processor. So at best it'll be only OpenGL support that's slower than native speeds.

If you really need 3D acceleration for something then just dual boot, assuming the Intel graphics processor can handle it in the first place. Cheers!

---

### Post by dcstar on 2009-05-17
> **lukeiamyourfather said:**
> **Virtual machines don't have any 3D acceleration with the exception of VirtualBox** which has very limited 3D acceleration for OpenGL only that uses the host's graphics processor. So at best it'll be only OpenGL support that's slower than native speeds.
.......

Rubbish, add the following to the VMWare guest's .vmx file:

```
mks.enable3d = "TRUE"
svga.vramSize = 67108864
```

If you have Direct Rendering working on your host you will now have it available in your VMWare guest.

---

