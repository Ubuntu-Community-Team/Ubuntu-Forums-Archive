---
title: "Kubuntu Dapper"
date: 2006-09-11
forum: Testimonials &amp; Experiences
---

### Post by DigitalDuality on 2006-09-11
d

---

### Post by jdong on 2006-09-11
> **DigitalDuality said:**
> 
My 2 complaints is i can't seem to find anything equal to Gdebi to install debs graphically.  I have an option to right click on debs to install them, but it hasn't worked once when sudo dpkg -i would.

Well, for that, gdebi is still my favorite tool. Even as a kubuntu user (at times), i'll still use gdebi. There's nothing wrong with using a GTK app inside KDE -- in fact the qt GTK engine makes the GTK app (kind of) take on your KDE theme, so arguably GTK runs better inside KDE than vice-versa.

You can associate debs with gdebi, so that they'd always use gdebi.

In the development world, adept will {eventually} get the ability to function like gdebi.

> 
The 2nd is it's incredibly annoying that the volume buttons on my keyboard aren't supported.  But i was expecting that to happen.


Edgy's Kubuntu fixes this for good by introducing laptop keys support, but in Dapper you can work around it by going into KMix's Settings menu and choosing Set Global Shortcuts. You can configure your volume buttons as hotkeys for increasing/decreasing volume. You can configure Amarok in the sme way to use your play/stop buttons, if you have them. Again, Edgy won't need these tweaks.

---

### Post by DigitalDuality on 2006-09-11
d

---

### Post by jdong on 2006-09-11
Right click the deb file, then under the Actions menu, find the Open With... option.

In the subsequent application picker, type "gdebi %f" in the textbox at the top, then at the bottom check Remember Association (roughly).

---

### Post by DigitalDuality on 2006-09-11
d

---

