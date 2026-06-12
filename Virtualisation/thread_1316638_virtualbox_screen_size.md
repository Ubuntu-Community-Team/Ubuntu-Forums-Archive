---
title: "virtualbox screen size"
date: 2009-11-06
forum: Virtualisation
---

### Post by andymorton on 2009-11-06
Hi, I'm planning to test drive a few Linux distros through Virtualbox. At the moment I'm running Linux Mint. But I can't get the screen size above 640x480. I tried to change it from within Mint but that's the maximum it will go to. Also tried full screen mode but that didn't increase it either. 
Does anyone know how to make it fit the whole screen?

Thanks 
andy

---

### Post by ^_Pepe_^ on 2009-11-06
Hi!

Try to install "Guest Additions" for VirtualBox (Devices menu). They will mount a new virtual CD on your guest system.

Inside that CD, there's a script to run a recomplile the VirtualBox kernel.

After restart, you can use more resolutions, fluid mode, full screen...so on.

Regards,
^_Pepe_^

---

### Post by TenPlus1 on 2009-11-06
When running virtualbox actually drag the window to the size you need and the Os inside will resize to that resolution, and also give you bigger resolution screens to use when changing display mode...

---

