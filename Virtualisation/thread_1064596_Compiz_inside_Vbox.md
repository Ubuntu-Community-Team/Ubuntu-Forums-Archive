---
title: "Compiz inside Vbox?"
date: 2009-02-09
forum: Virtualisation
---

### Post by nowhere@cox.net on 2009-02-09
Hey all, I've seen a youtube video of vbox running in vista with Ubuntu Intrepid installed WITH compiz desktop cube etc. Unfortunately I can't get it working in mine vbox. I try this:
```
nowhere99@nowhere:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

```

I added vboxvideo to the whitelist in /usr/bin/compiz
```
nowhere99@nowhere:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1168x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: usr/bin/metacity 

```

Anyone know how to get this working? glxgears works fine in the vbox...

Thanks!

---

### Post by Ng Oon-Ee on 2009-02-09
You will probably need to modify the xorg.conf within your guest OS to enable compositing and other stuff you'll need. Unfortunately, since 3D acceleration (OpenGL) in VBox is so new, it may be a bit hard to find exactly what you need to modify. The Vbox 'virtualized video card' is certainly not the same in terms of its xorg.conf settings as compared to nvidia or ati cards which everybody uses.

---

### Post by nowhere@cox.net on 2009-02-09
yeah. I was hoping someone had figured it out. I may get around to it. It's dropped down the priority list a bit. Other things that don't work need fixing in the meantime...

If anyone comes up with some new info please post!

Thanks!

---

