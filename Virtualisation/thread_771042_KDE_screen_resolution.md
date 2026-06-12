---
title: "KDE screen resolution"
date: 2008-04-27
forum: Virtualisation
---

### Post by zorkerz on 2008-04-27
Im running ubuntu 8.04 with virtualbox OSE installed. Ive installed a kubuntu 8.04 virtual machine which i do not know how to set at a higher resolution than 800x600. This is fine when i want kubuntu as window on my ubuntu desktop but when I want it full screen I would like to make the resolution 1024x768 (my monitors max).

I am also having this problem with edubuntu making me think its not a problem with the specific virtual machine but virtualbox OSE.

any sugestions?

---

### Post by tollboy on 2008-04-27
i am having the same problem when doing the same as
i also tried ```
dpkg-reconfigure xserver-xorg
```
bt in 8.04 it works till the setting of keyboard only.......





help please i too want run kubuntu on virtual machine on full screen 
thanx in advance

---

### Post by zorkerz on 2008-04-28
Ok I fixed my problem. Under Monitory & Display in the system settings I went to the hardware tab and changed the #1 monitor from plug n play to LCD panel 1024x768. I had tried this before but also changed my graphics card which was breaking x.

tollboy: are you not able to reconfigure xorg? I use 'dpkg-reconfigure xserver-xorg -phigh' to reset xorg.conf to the defaults. I don't know what to do if you are unable to reconfigure xorg.conf at all. You could try manually setting the monitor by editing /etc/X11/xorg.conf but that can be risky make sure you backup.

good luck

---

### Post by zorkerz on 2008-04-28
Now its back again I installed the guest additions on my kubuntu guest. The resolution now only works at 640x480 which is barely usable no matter what I set the monitor as (plug n play or LCD 124x768). This really stinks.

Is there anything else I can try?
Why would the guest additions change this? (it seems to have changed the graphics card driver)

---

### Post by zorkerz on 2008-04-29
its now working for me but unfortunately im not sure what did the trick. If I can figure out in edubuntu ill report back.

---

### Post by tollboy on 2008-05-01
> tollboy: are you not able to reconfigure xorg? I use 'dpkg-reconfigure xserver-xorg -phigh' to reset xorg.conf to the defaults. I don't know what to do if you are unable to reconfigure xorg.conf at all. You could try manually setting the monitor by editing /etc/X11/xorg.conf but that can be risky make sure you backup.

good luck
i am  comparing the two distro here when
i am just saying that wen this command ```
dpkg-reconfigure xserver-xorg
```is used in 7.10 
rsolution can be changed from same screen 
bt now in 8.10 the screen ends at keyboard setting onlly

---

### Post by zorkerz on 2008-05-01
ah

Ive been messing around with this and keep running into problems. Ive been trying out different xorg.conf settings, then loging out, restarting x, and loging back in. Occasionally I am then able to change between 640x480, 800x600, and my screens max 1024x768. This never lasts when I restart the computer. In fact every time I restart the computer my edits to xorg.conf are deleted and the same broken xorg.conf gets put in place.

Thats where I stand know, I don't know what else to try or do.

---

### Post by seamuso on 2008-05-01
Try this xorg.conf

[http://ubuntuforums.org/showpost.php?p=4838886&postcount=6](http://ubuntuforums.org/showpost.php?p=4838886&postcount=6)

---

### Post by tollboy on 2008-05-03
my problem is not solved 
wat u said 
it is for kde 3 version 
bt i am using kubuntu with kde 4 
and not founding any option there like that

---

