---
title: "DVD not working"
date: 2010-12-06
forum: System76 Support
---

### Post by oconnor on 2010-12-06
I tried to follow the instructions at:
[www.knowledge76.com/index.php/Installing_Restricted_Formats](www.knowledge76.com/index.php/Installing_Restricted_Formats)
When I try the first commad (sudo apt-get install ubuntu-restricted-extras) the process takes about 20 minutes and my terminal ends up with this blue and grey box that says "Package Configuration... Configuring ttf-mscorefonts-installer..." and at the end it has an <Ok>.  But I can't use any of the keys.  I can't move on.  

And when I open a new terminal and try the next command:
sudo /usr/share/doc/libdvdread4/install-css.sh
it says dpkg: status database area is locked by another process


suggestions?

---

### Post by tlroche on 2010-12-07
> **oconnor said:**
> when I open a new terminal and try the next command:
sudo /usr/share/doc/libdvdread4/install-css.sh
it says dpkg: status database area is locked by another process

Try removing the lock:

[LIST=1]
[*]Either restart, or do (== type in terminal) ```
sudo rm /var/lib/dpkg/lock
```
[*]Let `dpkg` repair itself: ```
sudo dpkg --configure -a
```
[/LIST]

Then try installing ubuntu-restricted-extras again.

---

