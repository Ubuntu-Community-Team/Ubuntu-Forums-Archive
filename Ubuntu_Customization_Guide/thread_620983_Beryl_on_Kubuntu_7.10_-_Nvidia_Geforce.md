---
title: "Beryl on Kubuntu 7.10 - Nvidia Geforce"
date: 2007-11-23
forum: Ubuntu Customization Guide
---

### Post by guatifa on 2007-11-23
Hello everybody,

I installed Kubuntu 7.10 on my new ACER ASPIRE 5720G with GeFORCE 8400 GS.
When I try to launch Beryl I just get a White screen. When I try to play with the effects it works but still behind that screen.

I installed the nvidia drivers, compiz, and GLX from the repositories (synaptic) and evrything seems to be done. But still the problem remains.

Doses anyone had the same problem with this distro and the same graphical card?
I wonder if you, guys, can help!

Thanks

---

### Post by tossman on 2008-03-06
Sorry,can you tell me where can I get Beryl firstly?

---

### Post by tyster on 2008-04-10
I just got it from the Adept Package manager.  Did a search for "compiz".  I installed it, but when I ran it, the top bar of all the windows went away (that have the close/restore/minimize buttons).  Could the problem have something to do with the Kubuntu transparency effects?

Compaq F750US laptop
AMD 64 X2 CPU
nVidia GeForce 7000M

---

### Post by veganrailpunk on 2008-04-22
> **tyster said:**
> I just got it from the Adept Package manager.  Did a search for "compiz".  I installed it, but when I ran it, the top bar of all the windows went away (that have the close/restore/minimize buttons).  Could the problem have something to do with the Kubuntu transparency effects?

Compaq F750US laptop
AMD 64 X2 CPU
nVidia GeForce 7000M

you need to turn on "window decoration" in "advanced desktop effects settings" under "settings" in the k-menu. if you don't have that then make sure you have all these instaled:

compiz 
compizconfig-settings-manager  
compiz-kde 
compiz-fusion-plugins-main 
compiz-fusion-plugins-extra  
emerald 
librsvg2-common 

easiest way is
```
sudo aptitude install compiz compizconfig-settings-manager compiz-kde compiz-fusion-plugins-main compiz-fusion-plugins-extra emerald librsvg2-common
```

---

