---
title: "[Xubuntu / Lubuntu]  Skippy-xd / Exposé"
date: 2021-04-05
forum: Ubuntu, Linux and OS Chat
---

### Post by batra3 on 2021-04-05
Skippy-xd is an X11 software that brings an 'exposé' mode to Xubuntu or Lubuntu (like mission control on MacOS, or gnome-shell).

It is no longer maintained and has not worked for a while on Ubuntu (and its variants).

MXlinux has remade a version that works.
I got the 2 necessary .deb files from the MX directory: [http://la.mxrepo.com/mx/testrepo/pool/test/s/skippy-xd/](http://la.mxrepo.com/mx/testrepo/pool/test/s/skippy-xd/)

I integrated a fix developed by B. Murphy, and added its xdotool dependency in the .deb, to fix the bug not displaying reduced windows.

I modified then regenerated one of the .deb, to change the name of one of the dependencies: libjpeg62 (ubuntu version) instead of libjpeg62-turbo (mx version). Otherwise the MXLinux version does not work on Ubuntu. 

Tested and working on Ubuntu 21.04. Should work fine on Ubuntu 18.04 and higher. On Debian too, I suppose, but not tested.

Install skippy-xd :
```

sudo add-apt-repository ppa:batra3/ytool
sudo apt-get update
sudo apt install skippy-xd
```

Il you don't want a PPA, you can manually install the .deb via that link : [https://launchpad.net/~batra3/+archive/ubuntu/ytools/+files/skippy-xd_0.5.2-1~focal_all.deb](https://launchpad.net/~batra3/+archive/ubuntu/ytools/+files/skippy-xd_0.5.2-1~focal_all.deb)

To enable exposé mode, position the **Expose.desktop** launcher that comes with the .deb onto the desktop, into a dock, or onto a panel. Then click on it :)
You can also run the **skippy-xd-fix** command by binding it to a key or key combination (see in settings > keyboard).
**skippy-xd **(without the suffix '-fix') run the classical version of skippy-xd, without the fix.

To modify the config file skippy-xd.rc (wich manages the appearance) : 
  mkdir ~/.config/skippy-xd/ && cp /etc/xdg/skippy-xd.rc ~/.config/skippy-xd/
then modify the config file

---

### Post by coffeecat on 2021-04-05
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

