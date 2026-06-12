---
title: "Gstreamer-bad Plug-ins Broken"
date: 2017-07-12
forum: Ubuntu Development Version
---

### Post by Frogs Hair on 2017-07-12
Is anyone else having this problem? Pithos Pandora client was removed during updates due to held packages for these plug-ins. Attempting to reinstall restricted extras gives held/broken package message.

---

### Post by rrnbtter on 2017-07-12
Greetings,
I don't know about the Pandora but I installed Ubuntu-restricted-extras on two fully updated laptops today July 12th with no problems. I installed it to get streaming working in my Opera browser. Off topic but I will add that my Wayland login is broken after yesterday's updates. Gnome x11 is still working fine.

---

### Post by dino99 on 2017-07-13
There is a gdal api change , which disturb some packages upgrade   Bug #1703631

---

### Post by Frogs Hair on 2017-07-13
Successfully reinstalled ubuntu-restricted-extras, so looks more like a Pithos problem at present.

---

### Post by jbicha on 2017-07-13
Did you install pithos from the Ubuntu archives or from some other source?

Please don't use [-proposed updates]("https://askubuntu.com/questions/785414/is-it-ok-to-enable-proposed-updates-during-ubuntus-development-cycle") during the development cycle. And if you ignore that advice, please at least pay attention when you dist-upgrade.

---

### Post by Frogs Hair on 2017-07-13
From Ubuntu archives.

---

### Post by jbicha on 2017-07-13
Ok, then the second paragraph is for you. ;)

---

### Post by jbicha on 2017-07-13
At least I think that's the problem. There's not enough information here to know why apt isn't working for you. Try reading through the logs in /var/log/apt/

---

### Post by Frogs Hair on 2017-07-13
Looking at history and and other sources to find out what happened .

---

### Post by Frogs Hair on 2017-07-14
Able to reinstall after updates.

---

### Post by #&amp;thj^% on 2017-07-14
> **jbicha said:**
> Did you install pithos from the Ubuntu archives or from some other source?

Please don't use [-proposed updates]("https://askubuntu.com/questions/785414/is-it-ok-to-enable-proposed-updates-during-ubuntus-development-cycle") during the development cycle. And if you ignore that advice, please at least pay attention when you dist-upgrade.

Just politely asking, Dose this mean you are uninterested in early reporting proposed bugs?

---

### Post by dino99 on 2017-07-14
Has been  solved by that upgrade:

opencv (3.1.0+dfsg1-1~exp1ubuntu2) artful; urgency=medium

  * Rebuild against new gdal ABI.

 -- Gianfranco Costamagna <locutusofborg@debian.org>  Fri, 14 Jul 2017 11:48:48 +0200

---

### Post by Frogs Hair on 2017-07-14
> **dino99 said:**
> Has been  solved by that upgrade:

opencv (3.1.0+dfsg1-1~exp1ubuntu2) artful; urgency=medium

  * Rebuild against new gdal ABI.

 -- Gianfranco Costamagna <locutusofborg@debian.org>  Fri, 14 Jul 2017 11:48:48 +0200

Suspected opencv  was the package, and it is in today's update history.

---

