---
title: "Xen 4.1 - 4.3, Ubuntu 13.10, black screen on boot."
date: 2014-04-05
forum: Virtualisation
---

### Post by nack4251 on 2014-04-05
Ubuntu-Gnome 13.10
 Xen 4.1/4.3
 Intel i5 3570K  
 8GB Ram
 AMD 7870 &#8211; Proprietary drivers, no CCC.

 Hey,

 I'm having problems booting the host OS &#8211; Ubuntu 13.10. With both Xen 4.1 and 4.3 I can select the Xen Hyper-visor from Grub, and it appears to boot but after some fast console output I get a black screen. I get the feeling it's booting but it can't load the desktop for some reason. I'm using the xm toolstack. I don't have another machine I can gain remote access from at the moment. I'm competent with Linux but not competent enough to know where to look for logs to give you. So if you need anything, ask and I'll provide it. My normal kernel boots without any problems. 

Thanks.

Edit: I'm under the impression I can run both the host and guest on the discrete card, or is this not correct? After enabling the intergrated gpu, booting xen displays the splash screen on the intergrated card and gets no further.

---

### Post by heiko_s on 2014-04-14
Not sure what you are aiming at, but your 3570K CPU doesn't support VT-d, which means no IOMMU support. If you try to pass through a graphics card, it won't work without VT-d.

---

