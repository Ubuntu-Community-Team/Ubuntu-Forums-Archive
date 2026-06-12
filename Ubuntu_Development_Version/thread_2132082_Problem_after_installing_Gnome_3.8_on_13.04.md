---
title: "Problem after installing Gnome 3.8 on 13.04"
date: 2013-04-03
forum: Ubuntu Development Version
---

### Post by geovino on 2013-04-03
I followed these instructions: [http://www.ubuntukiller.com/2013/03/how-to-installupgrade-gnome-38-in.html?showComment=1364557968504](http://www.ubuntukiller.com/2013/03/how-to-installupgrade-gnome-38-in.html?showComment=1364557968504)
to install Gnome 3.8. I add the first two PPAs and then installed gnome. It came up OK and I did an upgrade that added more new components, but after rebooting and going to Unity and then rebooted back to gnome, gnome wouldn't open any of the controls, only a wallpaper and nothing else. How would I get gnome to boot up properly? Or is this still too new and buggy to fix?

---

### Post by Frogs Hair on 2013-04-03
Some have been successful , I on the other hand, spent the last hour or so getting back 3.6 which I am typing from. I plan to try again after the final release of 13.04. I still have quite a few updates rolling in . Removing the 3.8 dependencies was a bear because I had a conflicting program (sushi) which took a while to track down.

---

### Post by geovino on 2013-04-03
It would be too confusing for me to fix this. I'll wait until the final comes out and do a fresh install.

---

### Post by jbicha on 2013-04-03
After adding the GNOME3 PPA, you need to use ```
sudo apt-get dist-upgrade
```

Otherwise, you'll have problems.

---

