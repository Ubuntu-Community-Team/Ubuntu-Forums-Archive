---
title: "Windows live moviemaker"
date: 2009-01-26
forum: Virtualisation
---

### Post by Sashin on 2009-01-26
How come this doesn't work in a virtual box of windows 7 with ubuntu as the host os?

It says that it doesn't run on my hardware.

---

### Post by Dedoimedo on 2009-01-26
Can you be more specific?
Dedoimedo

P.S. Did you dedicate enough ram, hard disk space, installed guest addons, enabled 3d in guest etc?

---

### Post by Sashin on 2009-01-26
When I try to open moviemaker live this happens;

[http://i42.tinypic.com/1zqqxhy.png](http://i42.tinypic.com/1zqqxhy.png)

I've given 2gb ram, 100GB hard disk space, I've installed guest add-ons, and I've enabled 3d. And 128 video memory.

---

### Post by Therion on 2009-01-26
VirtualBox uses it's own, generic, video driver for the VM's you create and this is probably what Windows is flapping it's arms about.

---

### Post by Sashin on 2009-01-26
I see, is there any way to change the default video drivers for the VM. Ro some way around this?

---

### Post by Sashin on 2009-01-28
Bump

---

### Post by HotShotDJ on 2009-01-28
> **Sashin said:**
> I see, is there any way to change the default video drivers for the VM. Ro some way around this?Unfortunately, no.  Current (version 2.1.*) versions of VirtualBox only support OpenGL 3D for Windows guests, not DirectX 3D.  Developers are working on DirectX 3D support.  You'll have to wait for a future version of VirtualBox.

---

### Post by Sashin on 2009-01-28
Ah, fair enough.

---

### Post by Dedoimedo on 2009-01-28
Or try VMware Server, you'll have some limited DirectX support.
[http://www.dedoimedo.com/computers/virtualization-3d-support-vmware.html](http://www.dedoimedo.com/computers/virtualization-3d-support-vmware.html)

Dedoimedo

---

