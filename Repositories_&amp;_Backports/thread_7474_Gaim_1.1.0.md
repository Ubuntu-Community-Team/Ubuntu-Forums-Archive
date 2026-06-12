---
title: "Gaim 1.1.0"
date: 2004-12-07
forum: Repositories &amp; Backports
---

### Post by s.deleeuw on 2004-12-07
Hello,

The latest version of Gaim included an important bugfix: the `Switchboard Error` (MSN). In Holland, where I live, MSN is more populair than mobile phones (according to the newspapers). Those switchboard errors make Gaim pretty unusable. So I was wondering if an update will become available in the warty-updates repository.

For now:
I compiled gaim + gaim encryption in /opt/gaim-1.1.0. For those interested:
[http://download.delete-it.nl/files/gaim-1.1.0-i386-1sl.tgz](http://download.delete-it.nl/files/gaim-1.1.0-i386-1sl.tgz) 

Just extract the tarball in the root-directory. But check the package first: I might have included a chrootkit :grin: (just kiddin', checking is a good thing to do though). Run /opt/gaim-1.1.0/bin/gaim, which should not conflict with /usr/bin/gaim. Don't forget to update your icons.

Note: It would have been better to create a .deb file, I know. But since I am new to Ubuntu/Debian, I have no idea how to do it. So I gave it the Slack' approach.


Sander

---

### Post by nigelng on 2004-12-07
if u don't want change ur icons: 

open the console, type:

sudo mv /usr/bin/gaim /usr/bin/gaim-0.9
sudo ln -s /opt/gaim-1.1.0/bin/gaim /usr/bin/gaim

:)
nigel

---

### Post by jdong on 2004-12-08
Or, use Warty Backports: [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net)

---

