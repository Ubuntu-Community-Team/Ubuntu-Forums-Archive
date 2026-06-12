---
title: "Firefox is ditching XUL?"
date: 2011-10-15
forum: The Cafe
---

### Post by Lucradia on 2011-10-15
See this: [http://news.cnet.com/8301-30685_3-20120877-264/new-firefox-interface-to-speed-up-firefox-on-android/](http://news.cnet.com/8301-30685_3-20120877-264/new-firefox-interface-to-speed-up-firefox-on-android/)

Though for now, it seems like it's only an android problem? But, it also seems Desktop users might have to deal with it too soon.

Firefox will still use gecko however. I for one, welcome this change actually, as it would allow that global menu to be better integrated, and it would no longer need its own add-on to global menu. Of course, this is assuming Firefox will use GTK instead.

---

### Post by lovinglinux on 2011-10-15
> **Lucradia said:**
> Though for now, it seems like it's only an android problem? But, it also seems Desktop users might have to deal with it too soon.

I doubt it. This would mean killing almost the entire add-on base for Desktop.

---

### Post by Lucradia on 2011-10-15
> **lovinglinux said:**
> I doubt it. This would mean killing almost the entire add-on base for Desktop.

Still can use GTK for add-on development if they removed it from desktops.

---

### Post by Penguinnerd on 2011-10-15
Yeah, I seriously doubt they would do that.

At least not anytime soon.

---

### Post by lovinglinux on 2011-10-15
> **Lucradia said:**
> Still can use GTK for add-on development if they removed it from desktops.

Most likely, if they decide to ditch XUL in the future, to promote migration from XUL add-ons to Restartless add-ons. Anyway, in my opinion, this is not going to happen any time soon.

---

### Post by 3Miro on 2011-10-15
In Gentoo repository Firefox 7 no longer depends on XULRunner. I don't know if they just copy-pasted the part of XUL that they use or what, but I currently don't have XULRunner installed and I am using Firefox 7.

---

### Post by lovinglinux on 2011-10-15
> **3Miro said:**
> In Gentoo repository Firefox 7 no longer depends on XULRunner. I don't know if they just copy-pasted the part of XUL that they use or what, but I currently don't have XULRunner installed and I am using Firefox 7.

Firefox doesn't require xulrunner on Ubuntu since version 3.6 I guess, but the necessary libraries are shipped with Firefox. It still uses XUL, but do not depend on external packages.

---

### Post by 3Miro on 2011-10-15
> **lovinglinux said:**
> Firefox doesn't require xulrunner on Ubuntu since version 3.6 I guess, but the necessary libraries are shipped with Firefox. It still uses XUL, but do not depend on external packages.

This is interesting. 

On Ubuntu 10.04, Ubuntu-desktop and some Gnome and Evolution packages depend on Xulrunner. However, Firefox itself doesn't.

On Gentoo, Firefox 6 and earlier depend on Xulrunner. You get Xulrunner wither with building Gnome 2 or with installation of Firefox (if you are using Xfce or KDE). I just noticed the other day that I can safely remove Xulrunner form my install and keep Firefox 7.

---

### Post by Lucradia on 2011-10-16
> **3Miro said:**
> This is interesting. 

On Ubuntu 10.04, Ubuntu-desktop and some Gnome and Evolution packages depend on Xulrunner. However, Firefox itself doesn't.

On Gentoo, Firefox 6 and earlier depend on Xulrunner. You get Xulrunner wither with building Gnome 2 or with installation of Firefox (if you are using Xfce or KDE). I just noticed the other day that I can safely remove Xulrunner form my install and keep Firefox 7.

As lovinglinux said, Firefox ships with XUL within its own package.

---

