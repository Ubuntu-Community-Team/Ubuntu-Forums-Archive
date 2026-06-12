---
title: "requesting Clearlooks 0.6.1"
date: 2005-06-22
forum: Ubuntu Backports
---

### Post by Confuse on 2005-06-22
I know this is currently in breezy, but there is nothing unstable about this program at all. It has many noticible changes and would be a great addition to the backports. It compiles right out of the box too, so no compilications. If you could find the time to backport this updated version, it'd be highly appreciated.

---

### Post by Slo Mo Snail on 2005-06-22
I'll add it later to the backports repository

---

### Post by Technoviking on 2005-06-22
I'm unsure of this package, I have made it but it does not look nearly as nice at the version in Hoary (0.50). Please check out the screenshot, especially the systray, and let me know what you think.

Mike

---

### Post by sjmorgan on 2005-06-22
[QUOTE=Mike Basinger]I'm unsure of this package, I have made it but it does not look nearly as nice at the version in Hoary (0.50). Please check out the screenshot, especially the systray, and let me know what you think.[/QUOTE]Looks like it isn't working properly. The panels seem to be using the default GNOME controls as opposed to the Clearlooks ones.

---

### Post by jdong on 2005-06-22
[QUOTE=Mike Basinger]I'm unsure of this package, I have made it but it does not look nearly as nice at the version in Hoary (0.50). Please check out the screenshot, especially the systray, and let me know what you think.

Mike[/QUOTE]
yuck, looks like that on the Clearlooks I built, too...

---

### Post by Slo Mo Snail on 2005-06-22
I had the same problem after playing with gnome-theme-manager... just restart gnome and everything works fine again...

I really like some of the new stuff ;) and it normally doesn't look as on your screenshot... so please just restart gnome... that shouldn't be needed but somehow...

---

### Post by jdong on 2005-06-22
oh, cool. will try.

---

### Post by jdong on 2005-06-22
One of you two, upload it.

---

### Post by Slo Mo Snail on 2005-06-22
I already uploaded it an hour ago ;)

---

### Post by Confuse on 2005-06-22
[QUOTE=Slo Mo Snail]I already uploaded it an hour ago ;)[/QUOTE]

Does it need to be tested or approved? Do you mind posting the .deb, I don't have it listed as upgradable in synaptic. Thanks.

---

### Post by Majlo on 2005-06-22
[QUOTE=Confuse]Does it need to be tested or approved? Do you mind posting the .deb, I don't have it listed as upgradable in synaptic. Thanks.[/QUOTE]

Is in staging (repo for testing)

Add this into /etc/apt/sources.list 

## Backports Staging
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted

---

### Post by McQuaid on 2005-06-23
Just for people who don't know, there is a great theme pack for clearlooks that was just updated for .6 of clearlooks.

[http://gnome-look.org/content/show.php?content=25557](http://gnome-look.org/content/show.php?content=25557) 

His homepage is [here](http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/index.html) but better grab them from gnome-look for now as I don't think his page has been updated yet.

Btw, I wish more themes, icons pointers etc were packaged,  I personally don't install themes in my home as I want therm system wide and it would be nice if there was a gui way to install themes for all users.

---

