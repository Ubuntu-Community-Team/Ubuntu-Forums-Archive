---
title: "Lost conky transparency on upgraded netbook. Saucy running fine otherwise"
date: 2013-07-02
forum: Ubuntu Development Version
---

### Post by philinux on 2013-07-02
Conky background is now black instead of transparent.

Any help appreciated. I'm a conky novice.

---

### Post by philinux on 2013-07-02
Just spotted this conky gui. Will try this later. 

[http://m.webupd8.org/2013/07/conky-manager-gui-for-managing-conky.html?m=1](http://m.webupd8.org/2013/07/conky-manager-gui-for-managing-conky.html?m=1)

---

### Post by VinDSL on 2013-07-02
Might play around with this (or combinations thereof) in the pre-TEXT area of your .conkyrc file...

```
####
## Create 'own_window' type. Makes Conky behave like other panels.
#
own_window yes
own_window_transparent yes
own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
####
## Some distros require the following lines for TRUE transparency.
## BOTH of these lines need to be Commented/Uncommented in tandem.
#
own_window_argb_visual yes
own_window_argb_value 255
####
## Don't want TRUE transparency? (icons look janky on certain walls)
## Comment both of the lines above and Uncomment the line below.
#
# own_window_argb_visual no
```

If you copy n' paste this code into your .conkyrc file, make sure it isn't duplicated elsewhere in the file.

---

### Post by VinDSL on 2013-07-02
Er...

Are you running nouveau drivers in llvmpipe mode, by any chance?

---

### Post by philinux on 2013-07-03
> **VinDSL said:**
> Er...

Are you running nouveau drivers in llvmpipe mode, by any chance?

Thanks for help VinDSL. Just booted up again to check forum.

Well I'll be. 4 reboots and black conky background. This morning UK time I booted up and conky fine again.

This is an acer 1410 with intel graphics.

---

### Post by VinDSL on 2013-07-03
> **philinux said:**
> Thanks [...]
Welcome

---

### Post by philinux on 2013-09-16
Conky at it again.
Bit different corruption this time.
Gonna reboot a couple of times. That fixed it before.

---

