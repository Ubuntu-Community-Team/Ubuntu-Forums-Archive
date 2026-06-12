---
title: "Sidux questions: Is it a good bleeding edge distro? How do I install MP3 codecs?"
date: 2009-09-10
forum: The Cafe
---

### Post by gymophett on 2009-09-10
I don't understand. It is based on Debian sid. It uses the latest packages. How do I install MP3 codecs? I usually follow guides. Thanks guys.

---

### Post by linuxwizard on 2009-09-10
[http://www.debian-multimedia.org/](http://www.debian-multimedia.org/)

The first package to install is debian-multimedia-keyring. Than make sure you use sources.list > For sid (unstable)




SIDUX ROCKS

---

### Post by mdmarmer on 2009-09-10
exoodles debian multimedia installer script
[http://ex.505.ru/](http://ex.505.ru/)
To install, do, as root: cd /usr/local/bin; wget -Nc ex.505.ru; chmod +x exoodles; exoodles

smxi script is documented at [http://smxi.org/](http://smxi.org/)

Note: sidux forums and irc do not support these scripts.
For support, go to [http://www.sidux-underground.net](http://www.sidux-underground.net) or [http://techpatterns.com](http://techpatterns.com)

Mike

---

### Post by MarcusW on 2009-09-10
What's the difference between sidux and Debian Sid? I went to the "why sidux" page and it had some pros of using Sidux/Debian Sid compared to other Debian dists which didn't exactly explain much. ^^

---

### Post by mdmarmer on 2009-09-11
They have a sidux control center app and they build their own kernels.  Also, you need support or a lot of expertise to run sid -- without a community and advice on when a dist-upgrade is safe, you are likely to break your system sooner or later ...

Mike

---

