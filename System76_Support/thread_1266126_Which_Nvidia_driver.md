---
title: "Which Nvidia driver?"
date: 2009-09-14
forum: System76 Support
---

### Post by Iteria on 2009-09-14
I want to install the nvidia driver for my pangolin performance, but there's 3 listed and I don't know which to choose. I know that system76's drivers will install it for me, but I like Xubuntu and the driver program doesn't do anything if you don't have the standard Ubuntu instead of a variant.

Can someone let me know which to choose?

---

### Post by gila_monster on 2009-09-14
What three are listed for you?

---

### Post by jdb on 2009-09-14
> **Iteria said:**
> I want to install the nvidia driver for my pangolin performance, but there's 3 listed and I don't know which to choose. I know that system76's drivers will install it for me, but I like Xubuntu and the driver program doesn't do anything if you don't have the standard Ubuntu instead of a variant.

Can someone let me know which to choose?

What the system76 driver does is very varied between machines.
I may load a driver or two, it may patch a configuration file, it may do nothing.

Unless something is really tied to the gnome desktop it will get done in Xubuntu & Kubuntu also.
In Xubuntu or Kubuntu a patch might not do exactly what it does in Ubuntu.
Or a patch might be needed in Xubuntu that's not needed in Ubuntu.

You can see what is does if you look at the python files under /opt/system76,
but if your not a python progamer & I'm not,
it's liable to give you a headache.

jdb

---

### Post by Iteria on 2009-09-14
> **gila_monster said:**
> What three are listed for you?

I have Nvidia-glx-180, 173,96, and 71 ( I didn't notice the 180 one before)

[QUOTE=jdb]What the system76 driver does is very varied between machines.
I may load a driver or two, it may patch a configuration file, it may do nothing.

Unless something is really tied to the gnome desktop it will get done in Xubuntu & Kubuntu also.
In Xubuntu or Kubuntu a patch might not do exactly what it does in Ubuntu.
Or a patch might be needed in Xubuntu that's not needed in Ubuntu.

You can see what is does if you look at the python files under /opt/system76,
but if your not a python progamer & I'm not,
it's liable to give you a headache.
[/QUOTE]

I'm a programmer. That's actually interesting. I can see where it modded a few things just from a casual glance. I guess it was worth a run. Still, I know that the nvidia drivers were installed under the gnome installation, but they aren't under my xfce Xubuntu installation. 

I can't really think how a graphics driver would be gnome specific (but then, I know every little about drivers and how they interact with things), but I would really like some help knowing which to install since the driver installer didn't install the nvidia driver.

---

### Post by jdb on 2009-09-14
> **Iteria said:**
> I have Nvidia-glx-180, 173,96, and 71 ( I didn't notice the 180 one before)



I'm a programmer. That's actually interesting. I can see where it modded a few things just from a casual glance. I guess it was worth a run. Still, I know that the nvidia drivers were installed under the gnome installation, but they aren't under my xfce Xubuntu installation. 

I can't really think how a graphics driver would be gnome specific (but then, I know every little about drivers and how they interact with things), but I would really like some help knowing which to install since the driver installer didn't install the nvidia driver.

You can walk through the code & see exactly what was done for Ubuntu & then might be able to do something similar for Xubuntu.

I run Archlinux on my Daru2 & that's how I was able to figure out how to get my external mic to work.

jdb

---

### Post by Iteria on 2009-09-14
Maybe, but my knowledge of how linux works is pretty pedestrian. You would think I would know more about my own operating system, but mostly I just rely on guides. 

Basically, I'm too lazy to read the documentation. I think it would be a lot of work for me to look up the differences between gnome and xfce and then patch the code. I would probably end up doing a guess and check type of thing with the files, than any real informed kind of patching.

Maybe I'll make it a project during the winter break, but this student doesn't have time to be futzing around with non-class-related code. I'm in more of a "make it work" mode than a "I'll fix it" mode.

---

### Post by Iteria on 2009-09-17
No one answered my question. I still want to know which driver to install.

---

### Post by thomasaaron on 2009-09-17
I'd go with the one that says "recommended." I think it's the 180 driver.

---

### Post by Iteria on 2009-09-17
How do I know which on it recommended? They all have the ubuntu logo next to them and none of them say recommended anywhere?

---

### Post by marshmallow1304 on 2009-09-17
> **Iteria said:**
> How do I know which on it recommended? They all have the ubuntu logo next to them and none of them say recommended anywhere?

With Jaunty + Gnome, the recommended driver for the Pangolin is 180.  Is there a Hardware Drivers app in XFCE?

---

### Post by gila_monster on 2009-09-17
I don't have my Xubuntu box up right now, but I don't think there's a drivers app. My nVidia settings app says that I'm using 180 on the box, though, and 180 has been pretty stable. Should certainly work well with XFCE.

---

### Post by jdb on 2009-09-17
> **marshmallow1304 said:**
> With Jaunty + Gnome, the recommended driver for the Pangolin is 180.  Is there a Hardware Drivers app in XFCE?

Applications > System > Hardware Drivers

jdb

---

### Post by Iteria on 2009-09-18
Thanks, that worked.

---

### Post by gila_monster on 2009-09-18
> **jdb said:**
> Applications > System > Hardware Drivers

jdb

Ah! Thanks, jdb. Would probably help if I booted the Xubuntu box before answering next time! (Was working issues on the OTHER box at the time.)

---

### Post by jdb on 2009-09-18
> **gila_monster said:**
> Ah! Thanks, jdb. Would probably help if I booted the Xubuntu box before answering next time! (Was working issues on the OTHER box at the time.)

I was in Archlinux but I have Xubuntu about 10 seconds away  on virtualbox :)

jdb

---

