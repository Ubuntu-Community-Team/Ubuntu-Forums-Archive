---
title: "Request: Skype dependencies (dbus-1 &gt;= 0.23, libqt3c102-mt &gt;= 3:3.3.3)"
date: 2005-05-13
forum: Ubuntu Backports
---

### Post by pfp on 2005-05-13
Skype provides a .deb package, but it depends on more recent libs than what Ubuntu provides. Namely dbus-1 >= 0.23 and libqt3c102-mt >= 3:3.3.3 (and their dependencies).

[http://www.skype.com/products/skype/linux/](http://www.skype.com/products/skype/linux/)

Debian testing has these libs, but using it would bring in Debian's libc6 and lots of other libs too..

BTW, could it be possible to include Skype itself? Altough I doubt their license permits redistribution...

/ peter

---

### Post by ggozad on 2005-05-13
I installed succesfully skype with not problems. You don't need the libs from Debian they exist for Ubuntu.
If you don't want the libraries you can always download the static binary provided in the Skype download page.

---

### Post by jdong on 2005-05-13
Bringing in new versions of these libraries would also cause incompatibility with the packages compiled against the official versions of these libraries. So, it seems like I can't do so.

---

### Post by ZeroA4 on 2005-05-23
[QUOTE=pfp]Skype provides a .deb package, but it depends on more recent libs than what Ubuntu provides. Namely dbus-1 >= 0.23 and libqt3c102-mt >= 3:3.3.3 (and their dependencies).

[http://www.skype.com/products/skype/linux/](http://www.skype.com/products/skype/linux/)

Debian testing has these libs, but using it would bring in Debian's libc6 and lots of other libs too..

BTW, could it be possible to include Skype itself? Altough I doubt their license permits redistribution...

/ peter[/QUOTE]
You can follow this [http://ubuntuguide.org/#skype](http://ubuntuguide.org/#skype), they have a link to a modified .deb that refers to the libs in Ubuntu repos.

Or you can install the libs and force install the official .deb

---

### Post by pfp on 2005-05-23
[QUOTE=ZeroA4]You can follow this [http://ubuntuguide.org/#skype](http://ubuntuguide.org/#skype), they have a link to a modified .deb that refers to the libs in Ubuntu repos.

Or you can install the libs and force install the official .deb[/QUOTE]

Hmm, seems I was asleep when hoary was released; I wrote my original post while still on warty. It seems the .deb from skype.com installs cleanly on Hoary. 

Anyway, thanks for the info :)

---

