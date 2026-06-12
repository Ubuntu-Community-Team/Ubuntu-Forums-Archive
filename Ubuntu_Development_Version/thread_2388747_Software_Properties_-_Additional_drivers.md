---
title: "Software Properties - Additional drivers"
date: 2018-04-06
forum: Ubuntu Development Version
---

### Post by flocculant on 2018-04-06
Found a bug which I (as always) assumed to be just my built of allsorts of xfce4 bits and Xubuntu.

Effectively I found that installing the nvidia driver for my card from there - and then removing it - left me with 640x480px. 

Since then someone else has come up with the same issue - with the same driver (nvidia-340)

So I dig a bit more. Appears that additional drivers no longer removes any conf file(s) - a regression from 17.10.1.

Consequently there was a nvidia conf file in /etc/modprobe.d blacklisting nouveau - remove the file and resolution is then as expected.

Anyone else can confirm this? 

Particularly with a different driver?

For reference [lpbug]1761593[/lpbug]

If it is a regression - better to get that dealt with prior to release in a few weeks.

(For the record apt purge did as expected and reboot following that had expected resolution)

---

### Post by mc4man on 2018-04-06
This would be different in the case of the 390 drivers which now have a metapackage & a dozen actual packages.
In this case   additional drivers will only remove the 390 metapackage which does not remove the nvidia driver. It's only effect is to have the actual packages now eligible for autoremove.
So all in all  Additional Drivers is in sad, sad, shape.

---

