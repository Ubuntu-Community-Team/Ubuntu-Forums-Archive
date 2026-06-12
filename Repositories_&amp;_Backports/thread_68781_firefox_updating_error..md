---
title: "firefox updating error."
date: 2005-09-24
forum: Repositories &amp; Backports
---

### Post by fahad on 2005-09-24
Hi,

i tried to update my firefox , but i got this error "

E: /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox

--
right now i cant use firefox :(
after having this problem


,
any suggestion ?

---

### Post by judabuddhist on 2005-09-24
I have the exact same problem, and am now posting from konqueror. Any help would be appreciated

---

### Post by evilghost on 2005-09-24
[http://ubuntuforums.org/showthread.php?t=68864](http://ubuntuforums.org/showthread.php?t=68864)

---

### Post by fahad on 2005-09-24
Thanks  :-)

---

### Post by kwn12 on 2005-09-26
Great, that fixed my problem. I did, however, have to follow Grafter's advice in the other thread and use:
cd /var/cache/apt/archives
sudo dpkg -i --force-all mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb
sudo dpkg -i --force-all mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb

---

### Post by evilmrt on 2005-09-26
sudo apt-get -f install

worked fine for me!

---

### Post by Ozitraveller on 2005-09-26
I've just upgraded to breezy, and firefox broke me there too! But it wasn't the only problem, so maybe in a couple of days I'll try again. Sure hope the firefox upgrading issue gets resolved it's been around for a while now.

---

### Post by oxalá on 2005-09-27
[QUOTE=kwn12]Great, that fixed my problem. I did, however, have to follow Grafter's advice in the other thread and use:
cd /var/cache/apt/archives
sudo dpkg -i --force-all mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb
sudo dpkg -i --force-all mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb[/QUOTE]


worked for me as well.

---

