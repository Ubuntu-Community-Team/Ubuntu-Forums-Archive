---
title: "VirtualBox native client vs rdekstop"
date: 2009-10-30
forum: Virtualisation
---

### Post by corsakh on 2009-10-30
Hello,

I am running Windows XP SP3 under VirtualBox 3.0.8 on Ubuntu 9.10.

When I run VB native client Windows desktop seems to render quicker and use less CPU than when I connect to the virtual machine running in headless mode using rdesktop.

For example, when I use native VB client I can drag a window across the screen and CPU would only take about 30-40%. But when I do the same thing in rdekstop it goes all the way to 100%. It becomes slower depending on how complicated the desktop wallpaper is - its faster for a single color and really slow for large landscape pictures.

Is there any way to fix this? Am I missing something simple and maybe there are some flags with rdesktop or something like that?

Computer is Athlon 64 x2 4800+, 3Gb RAM, 512Mb Nvidea 9600GT.

---

### Post by mishkind on 2009-11-11
you can try playing around with the -x option. I usually use something like:

```
rdesktop -z -5 -xl -N
```

---

