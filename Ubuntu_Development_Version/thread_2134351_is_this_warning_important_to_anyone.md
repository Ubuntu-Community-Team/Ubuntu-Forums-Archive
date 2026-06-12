---
title: "is this warning important to anyone?"
date: 2013-04-10
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2013-04-10
got this in my terminal during a upgrade today
```
Setting up linux-generic (3.8.0.17.33) ...
Setting up software-center (5.6.0-0ubuntu2) ...
Updating software catalog...this may take a moment.
INFO:softwarecenter.db.pkginfo_impl.aptcache:aptcache.open()
WARNING:softwarecenter.db.update:The file: '/usr/share/app-install/desktop/workrave:workrave.desktop' could not be read correctly. The application associated with this file will not be included in the software catalog. Please consider raising a bug report for this issue with the maintainer of that application
WARNING:softwarecenter.db.update:The file: '/usr/share/app-install/desktop/sonic-visualiser:x-sonicvisualiser-layer.desktop' could not be read correctly. The application associated with this file will not be included in the software catalog. Please consider raising a bug report for this issue with the maintainer of that application
WARNING:softwarecenter.db.update:The file: '/usr/share/app-install/desktop/sonic-visualiser:x-sonicvisualiser.desktop' could not be read correctly. The application associated with this file will not be included in the software catalog. Please consider raising a bug report for this issue with the maintainer of that application
Software catalog update was successful.
Setting up xfce4-settings (4.11.0-0ubuntu1~ppa0.13.04.1) ...
Installing new version of config file /etc/xdg/xfce4/xfconf/xfce-perchannel-xml/xsettings.xml ...
Installing new version of config file /etc/xdg/autostart/xfsettingsd.desktop ...
Setting up xserver-xorg-video-intel (2:2.21.6-0ubuntu1) ...

```

---

### Post by Toz on 2013-04-10
I've noticed this as well. Found [this]("https://bugs.launchpad.net/ubuntu/+source/workrave/+bug/1159023") bug report. Doesn't seem to affect system operation.

---

### Post by VinDSL on 2013-04-10
For the most part, I disregard warnings.

Errors, however, do concern me... sometimes.

---

### Post by grahammechanical on 2013-04-11
I have seen those two warnings but what can we do about it? I do not have those applications installed. My ability to use the system and update it is not affected. There has to be a way for software centre to make sure it is not installing software that has not been updated to run on the next Ubuntu release. May be this is what we are seeing. Applications that are not maintained by the developer get dropped from the catalogue. May be.

---

### Post by philinux on 2013-04-11
This bug too. [https://bugs.launchpad.net/ubuntu/+source/app-install-data-ubuntu/+bug/1162327](https://bugs.launchpad.net/ubuntu/+source/app-install-data-ubuntu/+bug/1162327)

I tend to ignore these warnings if system works ok. I dont use software centre anyway. Synaptic is my preferred choice.

---

### Post by dino99 on 2013-04-11
+1 for synaptic
sadly the other package choices are too buggy (update-manager/software-center)

---

### Post by pfeiffep on 2013-04-11
I tend not to ignore warnings when testing software ... imho if you're going to test ignorance certainly is NOT bliss

---

### Post by ventrical on 2013-04-11
> **pfeiffep said:**
> I tend not to ignore warnings when testing software ... imho if you're going to test ignorance certainly is NOT bliss

The direction to what to do is very clear:


```

Please consider raising a bug report for this issue with the maintainer of that application

```

 Now , whether the maintainer actually DOES anything is another story. So, as far as I am concerned, it is an f/p.

regards, ventrical

---

### Post by ventrical on 2013-04-11
...as suspected .. it is an f/p and one of the programs (workrave) was deleted from repos.


[http://www.ubuntuupdates.org/package/core/raring/universe/proposed/workrave](http://www.ubuntuupdates.org/package/core/raring/universe/proposed/workrave)

---

### Post by rrnbtter on 2013-04-11
Greetings,
This problem is ancient history. It has been around since the end of March.  It should be fixed shortly. It's not clear to me why it has persisted this long.

---

