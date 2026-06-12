---
title: "Intel Graphics Bug"
date: 2013-05-29
forum: Ubuntu Development Version
---

### Post by roly33 on 2013-05-29
13.10 is reporting that my Toshiba Satellite C660-15R has got a VESA: intel Cantiga Graphics Card instead of a Mobile intel 4 Graphics Card and my resolution is locked at 1024x768 4:3 instead of 1366x768 16:9.

Is there an easy way to fix it without having to do a re-install?

Roland

---

### Post by dino99 on 2013-05-29
is xserver-xorg-video-intel installed ?
what shows "additional drivers" tab ?

---

### Post by grahammechanical on 2013-05-29
Are you sure that there is a difference between the two?

[http://ark.intel.com/products/codename/26552/Cantiga](http://ark.intel.com/products/codename/26552/Cantiga)

Before you call this a bug make sure that Details is not reading an ID from the graphic card that has only been changed on paper by Intel

Regards.

---

### Post by roly33 on 2013-05-29
> **grahammechanical said:**
> Are you sure that there is a difference between the two?

[http://ark.intel.com/products/codename/26552/Cantiga](http://ark.intel.com/products/codename/26552/Cantiga)

Before you call this a bug make sure that Details is not reading an ID from the graphic card that has only been changed on paper by Intel

Regards.

It used to show up as Mobile intel 4 Express Graphics and let me set the resolution to 1366x768 16:9 Widescreen I'm now forced to only use 1024x768 4:3 which has stretched everything to Widescreen which looks horrendous on a 1366x768 16:9 Widescreen display & my graphics card isn't listed on the link you provided.
 
Roland

---

### Post by roly33 on 2013-05-29
> **dino99 said:**
> is xserver-xorg-video-intel installed ?
what shows "additional drivers" tab ?

xserver-xorg-video-intel is installed.

I can't seem to find and additional drivers tab.

Roland

---

### Post by cariboo on 2013-05-29
> **roly33 said:**
> xserver-xorg-video-intel is installed.

I can't seem to find and additional drivers tab.

Roland

Additional drivers is now located in System Settings->Software & Updates

---

### Post by roly33 on 2013-05-30
> **cariboo907 said:**
> Additional drivers is now located in System Settings->Software & Updates

Thank's

> **dino99 said:**
> what shows "additional drivers" tab ?

No additional drivers available shows in additional drivers.

Roland

---

### Post by craig10x on 2013-05-30
He won't find any optional drivers for intel because the proprietary and open source intel drivers are identical...that is why ubuntu doesn't offer any options (i have intel also so that is why i was aware of that)...

---

### Post by philinux on 2013-05-30
Doubt if this will help the OP but at least Intel are making progress.

[http://www.webupd8.org/2013/05/intel-linux-graphics-installer.html](http://www.webupd8.org/2013/05/intel-linux-graphics-installer.html)

---

### Post by roly33 on 2013-05-31
> **philinux said:**
> Doubt if this will help the OP but at least Intel are making progress.

[http://www.webupd8.org/2013/05/intel-linux-graphics-installer.html](http://www.webupd8.org/2013/05/intel-linux-graphics-installer.html)

Thanks for that.  i found it on the intel Linux driver website yesterday and I'm now running 13.04 with the intel Driver.

Roland

---

### Post by craig10x on 2013-05-31
> **roly33 said:**
> Thanks for that.  i found it on the intel Linux driver website yesterday and I'm now running 13.04 with the intel Driver.

Roland

Just curious, but where did you find the updated linux driver on the Intel website?  Could you post a link here....thanks
And how do you use it?...does it scan your ubuntu system and give a selection to install?

---

### Post by dino99 on 2013-05-31
[http://www.webupd8.org/2013/04/how-to-use-intel-linux-graphics-drivers.html](http://www.webupd8.org/2013/04/how-to-use-intel-linux-graphics-drivers.html)

---

### Post by craig10x on 2013-05-31
Cool...thanks...anyone know if ubuntu updates eventually supply these quarterly stack updates as described on the intel web page?
If so, how long after the quarterly release do we usually get them from ubuntu repos?

---

