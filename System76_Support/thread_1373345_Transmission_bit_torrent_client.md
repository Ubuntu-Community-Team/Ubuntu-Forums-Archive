---
title: "Transmission bit torrent client"
date: 2010-01-05
forum: System76 Support
---

### Post by porlaizquierda on 2010-01-05
i did a partial upgrade to 9.04 a few days ago and today i realized that it took away transmission, which worked beautifully. when i try to download it from add/remove software i get this:

Cannot install 'transmission-gtk'

This application conflicts with other installed software. To install 'transmission-gtk' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

so when i get to synaptic package manager transmission-common shows that it is installed. but transmission itself is not installed. when i try to install that it says:

Could not mark all packages for installation or upgrade.
The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.

transmission:
 Depends: transmission-cli but it is not going to be installed
 Depends: transmission-gtk but it is not going to be installed


when i try to install transmission-gtk or transmission-cli, i get this:

Could not mark all packages for installation or upgrade.
The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.


transmission-cli:
 Depends: libevent-1.4-2 (>=1.4.11-stable) but it is not installable


or this:


Could not mark all packages for installation or upgrade.
The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.

transmission-gtk:
 Depends: libevent-1.4-2 (>=1.4.11-stable) but it is not installable



what's going on with that? can anyone help?

---

### Post by thomasaaron on 2010-01-05
There are a couple of ways to install it. You can get it from the ppa repos. See...

[http://ubuntuforums.org/showthread.php?t=1175583](http://ubuntuforums.org/showthread.php?t=1175583)

...or you can maybe just install the .deb here. You can get the one for 9.10 here...

[http://packages.ubuntu.com/search?keywords=transmission&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=transmission&searchon=names&suite=all&section=all)

---

### Post by porlaizquierda on 2010-01-05
i'm using ubuntu 9.04 on a starling netbook.

---

### Post by porlaizquierda on 2010-01-06
i went to this site

[http://packages.ubuntu.com/ko/karmic/i386/libevent-1.4-2/download](http://packages.ubuntu.com/ko/karmic/i386/libevent-1.4-2/download)

and downloaded and installed libevent-1.4-2 and was then able to download transmission and it's downloading. hopefully this helps anyone with a similar problem.

---

### Post by HuaiDan on 2010-10-13
I was having a similar issue trying to install Wine 1.2, with the same error message about dependencies and a a stubborn refusal to install needed packages. As it turns out, while I'm using Lucid, there was a repo added for the Maverick Meercat CD. When I removed that and reloaded, everything went swimmingly.

---

### Post by thomasaaron on 2010-10-14
"swimmingly"... I love the English language. :)

---

