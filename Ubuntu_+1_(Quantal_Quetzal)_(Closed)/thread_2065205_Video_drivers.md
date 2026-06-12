---
title: "Video drivers"
date: 2012-10-01
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by northwestern on 2012-10-01
Please help

I do I load my AMD 3400 video drivers in 12.10, when I download the additional driver application and run it, it says "no drivers available".

Regards 
Northwestern

---

### Post by kaldor on 2012-10-01
I believe the proprietary driver no longer supports the 3000 series. The default open source driver should support your 34xx-series card pretty well, though.

You can try installing the fglrx package. But overall, I'd just stick with the default one if you aren't into gaming.

---

### Post by 2F4U on 2012-10-01
I would also assume that the proprietary ATI drivers don't support your graphics card. From the Arch Wiki([https://wiki.archlinux.org/index.php/ATI_Catalyst](https://wiki.archlinux.org/index.php/ATI_Catalyst)):

> **Catalyst 12.6 stable news**: 
- **supports Radeon HD >= 5xxx**. 


---

### Post by northwestern on 2012-10-01
Thanks for your quick replies. The default open source package seems to work OK, the problem is I use two screens (laptop plus one other), every time I shut down and restart I have to reset the screen options again. I seem to be doing everything alrighty but it always needs resetting.

Regards
northwestern

---

### Post by kaldor on 2012-10-01
I've heard about that issue before. You shouldn't need the proprietary driver in order to keep your settings.

Google around about preserving settings with the Radeon (open source) driver. I had the same issue when I was using the open source NVIDIA (Nouveau) driver. You should be able to find something.

---

