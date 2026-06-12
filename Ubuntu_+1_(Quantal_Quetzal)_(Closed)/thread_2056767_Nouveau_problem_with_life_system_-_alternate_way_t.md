---
title: "Nouveau problem with life system - alternate way to install?"
date: 2012-09-12
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by JerryPreissler on 2012-09-12
I'm running into a problem with the nouveau driver in Quantal that prevents me from running the installer (see [https://bugs.launchpad.net/ubuntu/+bug/1049497](https://bugs.launchpad.net/ubuntu/+bug/1049497) ). Is there any way to install the system from the command line or work around the problem otherwise?

---

### Post by mips on 2012-09-12
There's always the alternate cd image or the netinstall cd image.

---

### Post by JerryPreissler on 2012-09-12
> **mips said:**
> There's always the alternate cd image or the netinstall cd image.

I can't find the alternate cd among the images offered at [https://wiki.ubuntu.com/QuantalQuetzal/TechnicalOverview/Beta1#Download_the_Beta_1](https://wiki.ubuntu.com/QuantalQuetzal/TechnicalOverview/Beta1#Download_the_Beta_1) and AFAIR the alternate CD was dropped from the Quantal release to reduce the number of iso images to handle.

I had not thought about the netboot image and will give it a try, thanks for the hint. Not sure if this will help, though - if the netboot also uses the graphical installer I don't think this will work.

Is there a way to fall back to standard VGA or something curses-based for the installation?

---

### Post by mips on 2012-09-12
> **JerryPreissler said:**
> I can't find the alternate cd among the images offered at [https://wiki.ubuntu.com/QuantalQuetzal/TechnicalOverview/Beta1#Download_the_Beta_1](https://wiki.ubuntu.com/QuantalQuetzal/TechnicalOverview/Beta1#Download_the_Beta_1) and AFAIR the alternate CD was dropped from the Quantal release to reduce the number of iso images to handle.

I had not thought about the netboot image and will give it a try, thanks for the hint. Not sure if this will help, though - if the netboot also uses the graphical installer I don't think this will work.


Ah ok the other variants of Ubuntu (Xubuntu etc still have alternate images).

The netinstall/alternate images do not have gui installers, it's cli based but still easy to use.

You can grab the mini/netinstall iso from here if you want,
i386--- [http://archive.ubuntu.com/ubuntu/dists/quantal/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/quantal/main/installer-i386/current/images/netboot/)
amd64--- [http://archive.ubuntu.com/ubuntu/dists/quantal/main/installer-amd64/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/quantal/main/installer-amd64/current/images/netboot/)

---

### Post by JerryPreissler on 2012-09-12
> **mips said:**
> 

The netinstall/alternate images do not have gui installers, it's cli based but still easy to use.

You can grab the mini/netinstall iso from here if you want,
i386--- [http://archive.ubuntu.com/ubuntu/dists/quantal/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/quantal/main/installer-i386/current/images/netboot/)
amd64--- [http://archive.ubuntu.com/ubuntu/dists/quantal/main/installer-amd64/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/quantal/main/installer-amd64/current/images/netboot/)

Great, thanks for the info.  I'll give it a try and update the thread title if it works.

---

