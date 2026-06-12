---
title: "Unable to install Ubuntu Impish"
date: 2021-09-12
forum: Ubuntu Development Version
---

### Post by lanfust on 2021-09-12
Hello
trying to install Impish Ubuntu
I've made a boot key like this

```
dd if=source of=target bs=4M status=progress && sync
```

When i am on the screen where you can set option between full install or minimal i choose minimal click next but stays on this screen.

Is it a bug install or can i do something to go next screen ?

Same issue with kubuntu impish

---

### Post by grahammechanical on 2021-09-12
Ubuntu 21.10 (Impish Indri) is still under development. It will not be released until 14 October 2021. The developers are also experimenting with a new installer application which may or may not be ready in time for the release of 21.10. If this new installer is not fully functional by 14th October it will not be included.

So, expect bugs!

This forum has a section for discussion of the development version. You might be interested in this thread from the Ubuntu Development Version section of this forum.

[https://ubuntuforums.org/showthread.php?t=2463829](https://ubuntuforums.org/showthread.php?t=2463829)

Regards

---

### Post by coffeecat on 2021-09-12
*Thread moved to **Ubuntu Development Version** sub-forum.*

---

### Post by lanfust on 2021-09-12
ok thanks
i don't know they tested a new installer

---

### Post by corradoventu on 2021-09-16
The NEW installer (ubuntu-desktop-installer) is used only in the ISO you can download from [http://cdimages.ubuntu.com/daily-canary/pending/](http://cdimages.ubuntu.com/daily-canary/pending/) but non in the standard ISO from [http://cdimages.ubuntu.com/daily-live/pending/](http://cdimages.ubuntu.com/daily-live/pending/)
see [https://discourse.ubuntu.com/t/refreshing-the-ubuntu-desktop-installer/20659](https://discourse.ubuntu.com/t/refreshing-the-ubuntu-desktop-installer/20659)
Using the standard image you should not have problem installing Ubuntu Impish.

---

