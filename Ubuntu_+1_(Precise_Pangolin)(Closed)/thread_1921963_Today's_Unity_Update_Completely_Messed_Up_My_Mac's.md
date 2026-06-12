---
title: "Today's Unity Update Completely Messed Up My Mac's Display!"
date: 2012-02-07
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kevpan815 on 2012-02-07
It's a Mid Year 2010 Mac Mini with a: Vesa Nvidia GeForce 320M Graphics Gard Device Driver installed.

---

### Post by cariboo on 2012-02-07
So what driver are you using? Vesafb, nouveau or the Nvidia closed source driver>

---

### Post by kevpan815 on 2012-02-08
> **cariboo907 said:**
> So what driver are you using? Vesafb, nouveau or the Nvidia closed source driver>

I am using the default in the box device driver that comes with 12.04. I don't know how to install anything else. The monitor that I am using is a 19 inch LED LCD Vizeo HDTV using a HDMI cable.

---

### Post by cariboo on 2012-02-08
If you have an /etc/X11/xorg.conf could post it, you can also use:

```
lsmod 
```

to see if vesafb, nouveau or nvidia is present.

---

### Post by dino99 on 2012-02-08
sudo jockey-gtk

let you know which driver is activated. If you want/need to try something else, then open synaptic and makes the change.

---

