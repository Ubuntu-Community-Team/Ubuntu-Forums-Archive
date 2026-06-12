---
title: "firefox change"
date: 2005-07-09
forum: Ubuntu Backports
---

### Post by rwabel on 2005-07-09
firefox from backport has changed from mozilla-firefox to firefox. It's now like in breezy.
But due to that change some packages got removed.
**gnome-devel** because it depends on ** devhelp**, which depends on **libdevhelp-1-0 **, which depends on mozilla-firefox and not firefox.

and what happened to **autoscan**?

Thanks

---

### Post by jcohen on 2005-07-11
Actually, the new firefox package provides mozilla-firefox. Otherwise, removing the mozilla-firefox and mozilla-firefox-gnome-support packages would have also removed ubuntu-desktop which it did not. The problem is that libdevhelp-1-0 depends on  mozilla-firefox (>= 0.10). While mozilla-firefox is provided by firefox, I don't think it has any version and therefore libdevhelp-1-0 can't be installed. 


Package: firefox
Version: 1.0.4-1ubuntu3~5.04ubp6
Priority: optional
Section: web
Maintainer: Eric Dorland <eric@debian.org>
Depends: fontconfig, psmisc, debianutils (>= 1.16), libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.9.0), libbonobo2-0 (>= 2.8.0), libbonoboui2-0 (>= 2.5.4), libc6 (>= 2.3.2.ds1-4), libcairo1 (>= 0.3.0), libfontconfig1 (>= 2.2.1), libfreetype6 (>= 2.1.5-1), libgcc1 (>= 1:4.0-0pre6ubuntu4), libgconf2-4 (>= 2.9), libglib2.0-0 (>= 2.6.0), libgnome2-0 (>= 2.8.0), libgnomecanvas2-0 (>= 2.6.0), libgnomeui-0 (>= 2.8.0), libgnomevfs2-0 (>= 2.9.90), libgtk2.0-0 (>= 2.6.0), libice6 | xlibs (>> 4.1.0), libidl0, libjpeg62, libkrb53 (>= 1.3.2), liborbit2 (>= 1:2.12.0), libpango1.0-0 (>= 1.8.1), libpixman1 (>= 0.1.3), libpng12-0 (>= 1.2.8rel), libpopt0 (>= 1.7), libsm6 | xlibs (>> 4.1.0), libstdc++6 (>= 4.0-0pre6ubuntu4), libx11-6 | xlibs (>> 4.1.0), libxft2 (>> 2.1.1), libxinerama1, libxml2 (>= 2.6.17), libxrender1, libxt6 | xlibs (>> 4.1.0), zlib1g (>= 1:1.2.1)
Suggests: firefox-gnome-support (= 1.0.4-1ubuntu3~5.04ubp6), latex-xft-fonts, xprint
Conflicts: mozilla-firefox
**Provides: www-browser, mozilla-firefox**
Replaces: mozilla-firefox
Architecture: i386
Filename: dists/hoary-backports-staging/main/binary-i386/firefox_1.0.4-1ubuntu3~5.04ubp6_i386.deb
Size: 8545518
MD5sum: d9066897ce642101926e5bfb151faf43
Description: lightweight web browser based on Mozilla
 Firefox is a redesign of the Mozilla browser component, similar to
 Galeon, K-Meleon and Camino, but written using the XUL user interface
 language and designed to be lightweight and cross-platform.
 .
 This browser was previously known as Firebird and Phoenix.
installed-size: 24300

---

### Post by rwabel on 2005-07-11
[QUOTE=jcohen]Actually, the new firefox package provides mozilla-firefox. Otherwise, removing the mozilla-firefox and mozilla-firefox-gnome-support packages would have also removed ubuntu-desktop which it did not. The problem is that libdevhelp-1-0 depends on  mozilla-firefox (>= 0.10). While mozilla-firefox is provided by firefox, I don't think it has any version and therefore libdevhelp-1-0 can't be installed. 


Package: firefox
Version: 1.0.4-1ubuntu3~5.04ubp6
Priority: optional
Section: web
Maintainer: Eric Dorland <eric@debian.org>
Depends: fontconfig, psmisc, debianutils (>= 1.16), libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.9.0), libbonobo2-0 (>= 2.8.0), libbonoboui2-0 (>= 2.5.4), libc6 (>= 2.3.2.ds1-4), libcairo1 (>= 0.3.0), libfontconfig1 (>= 2.2.1), libfreetype6 (>= 2.1.5-1), libgcc1 (>= 1:4.0-0pre6ubuntu4), libgconf2-4 (>= 2.9), libglib2.0-0 (>= 2.6.0), libgnome2-0 (>= 2.8.0), libgnomecanvas2-0 (>= 2.6.0), libgnomeui-0 (>= 2.8.0), libgnomevfs2-0 (>= 2.9.90), libgtk2.0-0 (>= 2.6.0), libice6 | xlibs (>> 4.1.0), libidl0, libjpeg62, libkrb53 (>= 1.3.2), liborbit2 (>= 1:2.12.0), libpango1.0-0 (>= 1.8.1), libpixman1 (>= 0.1.3), libpng12-0 (>= 1.2.8rel), libpopt0 (>= 1.7), libsm6 | xlibs (>> 4.1.0), libstdc++6 (>= 4.0-0pre6ubuntu4), libx11-6 | xlibs (>> 4.1.0), libxft2 (>> 2.1.1), libxinerama1, libxml2 (>= 2.6.17), libxrender1, libxt6 | xlibs (>> 4.1.0), zlib1g (>= 1:1.2.1)
Suggests: firefox-gnome-support (= 1.0.4-1ubuntu3~5.04ubp6), latex-xft-fonts, xprint
Conflicts: mozilla-firefox
**Provides: www-browser, mozilla-firefox**
Replaces: mozilla-firefox
Architecture: i386
Filename: dists/hoary-backports-staging/main/binary-i386/firefox_1.0.4-1ubuntu3~5.04ubp6_i386.deb
Size: 8545518
MD5sum: d9066897ce642101926e5bfb151faf43
Description: lightweight web browser based on Mozilla
 Firefox is a redesign of the Mozilla browser component, similar to
 Galeon, K-Meleon and Camino, but written using the XUL user interface
 language and designed to be lightweight and cross-platform.
 .
 This browser was previously known as Firebird and Phoenix.
installed-size: 24300[/QUOTE]
 I see!
in breezy libdevhelp-1-0 depends on mozilla-browser and not mozilla-firefox. kinda funny :-)

I hope they will change that once, but at the moment I don't need it

---

### Post by jdong on 2005-07-11
Alright, I've rolled Firefox back to 5.04ubp5, which doesn't have this issue... Downgrade, please.

---

### Post by rwabel on 2005-07-11
[QUOTE=jdong]Alright, I've rolled Firefox back to 5.04ubp5, which doesn't have this issue... Downgrade, please.[/QUOTE]
 thanks, but now can't install mozilla-firefox-gnome-support neither firefox-gnome-support.

I've now mozilla-firefox and firefox installed. Firefox I cannot remove, because yelp, epiphany and other depend on it.

Now apt wants to upgrade my firefox (because it's older) if I do that he wants to remove mozilla-firefox.

Kinda complilcated now :-)

---

### Post by Mez on 2005-07-11
ubp5 has dependencies on other libs and causes problems, which is exactly the reason why it was made up to version 6.

The problem is that the pseudo - package was made up wrong.... and with version 5, it causes lot's of dependency problems.

---

### Post by rwabel on 2005-07-11
[QUOTE=Mez]ubp5 has dependencies on other libs and causes problems, which is exactly the reason why it was made up to version 6.

The problem is that the pseudo - package was made up wrong.... and with version 5, it causes lot's of dependency problems.[/QUOTE]
 I see, thanks. Then the pseudo package will get fixed sooner or later?

---

