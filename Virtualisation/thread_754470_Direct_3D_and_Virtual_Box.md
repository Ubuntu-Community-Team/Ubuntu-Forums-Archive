---
title: "Direct 3D and Virtual Box"
date: 2008-04-13
forum: Virtualisation
---

### Post by hitspace on 2008-04-13
i installed virtual box and after that a game , rise of nations, i was getting video related problems. i realized that direct 3d was not enabled and that i couldnt do it with the direct x diagnostic. i was wondering if its possible to install other video drivers on virtual box other then then the virtual box graphics drivers.

---

### Post by Griffin3 on 2008-10-24
In a word, no.  The virtual 'hardware' in virtualbox is entirely a software construct, it is virtual (as of version 2.0.3).  Wouldn't make sense to translate the 3D hardware instructions into software that would render in 2D, in another layer, that then runs on the 'real' video card though yet another layer of emulation.

That being said, it should be possible to adapt the video driver in virtualbox to pass through a limited set of 3D commands to the hardware (if supported) and then expand that subset until you had something useful.  It's open source ...  so learn C and take some stimulants and get cracking!

[Heh.  Or, like the rest of us, wait in quiet hope, and help the alpha testers out whenever you see a project doing this.]

---

### Post by falkTX on 2008-10-24
Have you tried VMware?

It's like VirtualBox and has Basic Direct3D Support (using VMware's SVGAII driver).
The only "problem"... It's shareware

---

### Post by Thelasko on 2008-10-24
> **falkTX said:**
> Have you tried VMware?

It's like VirtualBox and has Basic Direct3D Support (using VMware's SVGAII driver).
The only "problem"... It's shareware

Only in the newest version IIRC.

---

### Post by RobertMillan on 2009-02-04
> **hitspace said:**
> i installed virtual box and after that a game , rise of nations, i was getting video related problems. i realized that direct 3d was not enabled and that i couldnt do it with the direct x diagnostic. i was wondering if its possible to install other video drivers on virtual box other then then the virtual box graphics drivers.

This is still very experimental, but you can get Direct3D support on VirtualBox now, using WineD3D.  See:

[http://aybabtu.com/rmh/wined3d/](http://aybabtu.com/rmh/wined3d/)

[http://www.virtualbox.org/ticket/2940](http://www.virtualbox.org/ticket/2940)

However it's only known to work for testcases and simple apps so far.

---

