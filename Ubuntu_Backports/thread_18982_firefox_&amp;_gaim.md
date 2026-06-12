---
title: "firefox &amp; gaim"
date: 2005-03-09
forum: Ubuntu Backports
---

### Post by techn9ne on 2005-03-09
I added staging and tried to update firefox and gaim and got this :

Setting up gaim (1.1.2-3ubuntu1-4.10ubp1) ...
rmdir: `/usr/share/doc/gaim': No such file or directory
dpkg: error processing gaim (--configure):
 subprocess post-installation script returned error exit status 1
Setting up mozilla-firefox (1.0.0+dfsg.1-6ubuntu1~4.10ubp1) ...
Updating mozilla-firefox chrome registry...E: /usr/lib/mozilla-firefox/extension s/installed-extensions.txt still present. Registration might have gone wrong.
mv: cannot stat `/usr/lib/mozilla-firefox/defaults.ini': No such file or directo ry
dpkg: error processing mozilla-firefox (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mozilla-firefox-gnome-support :
 mozilla-firefox-gnome-support depends on mozilla-firefox (= 1.0.0+dfsg.1-6ubunt u1~4.10ubp1); however:
  Package mozilla-firefox is not configured yet.
dpkg: error processing mozilla-firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gaim
 mozilla-firefox
 mozilla-firefox-gnome-support
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by dcstar on 2005-03-10
[QUOTE=techn9ne]I added staging and tried to update firefox and gaim and got this :
........
Setting up mozilla-firefox (1.0.0+dfsg.1-6ubuntu1~4.10ubp1) ...
Updating mozilla-firefox chrome registry...E: /usr/lib/mozilla-firefox/extension s/installed-extensions.txt still present. Registration might have gone wrong.
mv: cannot stat `/usr/lib/mozilla-firefox/defaults.ini': No such file or directo ry
dpkg: error processing mozilla-firefox (--configure):
 subprocess post-installation script returned error exit status 1
........[/QUOTE]
As far as Firefox goes:

[http://ubuntuforums.org/showthread.php?t=17142&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=17142&page=1&pp=10)

---

