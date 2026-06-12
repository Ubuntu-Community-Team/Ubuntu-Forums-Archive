---
title: "the new NVIDIA  driver allows direct use of compiz and beryl"
date: 2006-11-17
forum: The Cafe
---

### Post by darkhatter on 2006-11-17
[quote=http://forum.club.mandriva.com/viewtopic.php?t=56729&sid=7843eb888d7c10665d9aab0ddbb8656f]

This is not accurate. drak3d does not test for the chip on your graphics card, it checks dynamically for the GL capabilities of whatever card is in use. 

You cannot use AIGLX with the NVIDIA proprietary driver. The entire concept does not make sense. AIGLX is a framework which allows drivers that use the X.org DRI infrastructure to provide the GLX_EXT_TEXTURE_FROM_PIXMAP extension that compiz / beryl (and compositing in general) requires. The NVIDIA proprietary driver does not use the X.org DRI infrastructure and thus couldn't possibly make use of AIGLX. 

What the new NVIDIA driver in fact allows is direct use of compiz or beryl on the NVIDIA driver itself. The driver directly provides the GLX_EXT_TEXTURE_FROM_PIXMAP extension, meaning you don't need the whole Xgl hack to make it available. When you run compiz or beryl on the new NVIDIA driver without Xgl, you're not using AIGLX, compiz is running directly on top of the NVIDIA driver. 

This doesn't work in stock 2007, not really because of any issue with drak3d, but because the compiz and compiz-quinnstorm shipped in 2007 were not new enough to handle it. The best way to use it is to install a recent version of beryl, and drak3d doesn't work with beryl, since it didn't exist when drak3d was written. 

The page you linked to is the one I would advise for anyone wanting to use beryl directly on the new NVIDIA driver with MDV 2007, for now. I'm hoping we'll be able to get the relevant stuff (the new NVIDIA driver, and beryl) into 2007 backports media.
_________________
Adam Williamson | Editor, Mandriva Community Newsletter; Mandriva Club Monkey | awilliamson A T mandriva D 0 T com 
All opinions posted here are my own and do not represent official Mandriva policy.
[/quote]

I know what everyone is thinking, but this keeps popping up all over the forum, and its driving me crazy ](*,)

---

