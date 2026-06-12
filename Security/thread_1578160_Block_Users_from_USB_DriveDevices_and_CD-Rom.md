---
title: "Block Users from USB Drive/Devices and CD-Rom"
date: 2010-09-20
forum: Security
---

### Post by sathisindia on 2010-09-20
**Block Users from USB Drive/Devices and CD-Rom**             
                                                                I am using **[COLOR=Red]Ubuntu 9.10- the Karmic Koala(64 bit)[/COLOR]** in my company. I would like to block [COLOR=Navy]the users[/COLOR]([COLOR=Red]**except Super user**[/COLOR]) from  using [COLOR=Red]USB Drive/Devices and CD-Rom[/COLOR] for security resons and to prevent  my employees from copying data.

In Users Settings, I tried unchecking some items in User Privileges tab but it didn't work.

Thank you!

---

### Post by HermanAB on 2010-09-20
There is a Gnome wizard in the system menu for managing user permissions, but for the life of me I cannot remember the name and I'm not running Gnome now.  Changing the USB mount permission is trivial with that one.

---

### Post by sathisindia on 2010-09-20
> **HermanAB said:**
> There is a Gnome wizard in the system menu for managing user permissions, but for the life of me I cannot remember the name and I'm not running Gnome now.  Changing the USB mount permission is trivial with that one.




In Ubuntu 9.10 there is no Gnome wizard in system menu....

---

### Post by BkkBonanza on 2010-09-20
You can use a udev rule. I worked this one out some months ago for another user asking about it and posted it on this forum. If I can find it I'll check back and post it. Maybe someone else remembers that rule...

Edit: Yes, did a search here and found it. Here's a link to what I did before and it does work. If you can find a simple "gnome setting" to do this reliably so it can't be circumvented then do that, but otherwise this method described worked well in my testing.

[http://ubuntuforums.org/showthread.php?p=8549547&highlight=udev+rule+usb#post8549547](http://ubuntuforums.org/showthread.php?p=8549547&highlight=udev+rule+usb#post8549547)

---

### Post by cariboo on 2010-09-20
You coulsd also remove the user from the cdrom and plugdev groups:

```
sudo gpasswd -d USER cdrom,plugdev
```

---

### Post by FuturePilot on 2010-09-20
Use Policykit [http://ubuntuforums.org/showpost.php?p=9816231&postcount=2]("http://ubuntuforums.org/showpost.php?p=9816231&postcount=2")

---

### Post by HermanAB on 2010-09-20
Yes, that is it.  There is a gnome policykit wizard.  Just run it and futz around a bit and you'll eventually figure out how to restrict USB mounting.

[http://packages.ubuntu.com/hardy/policykit-gnome](http://packages.ubuntu.com/hardy/policykit-gnome)
[http://hal.freedesktop.org/docs/PolicyKit-gnome/](http://hal.freedesktop.org/docs/PolicyKit-gnome/)

---

