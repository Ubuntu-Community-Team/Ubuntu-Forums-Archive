---
title: "Gnome 46: HTML codes in notifications"
date: 2024-06-01
forum: Ubuntu Development Version
---

### Post by hectorsales on 2024-06-01
In notifications the message is displayed with html tags:

[https://gitlab.gnome.org/GNOME/gnome-shell/-/issues/7495](https://gitlab.gnome.org/GNOME/gnome-shell/-/issues/7495)

There's a fix:

[https://gitlab.gnome.org/GNOME/gnome-shell/-/commit/7f476e051cce72ec92c8c041eef485f82108eb0f](https://gitlab.gnome.org/GNOME/gnome-shell/-/commit/7f476e051cce72ec92c8c041eef485f82108eb0f)

My question where is the file/path "notificationDaemon.js"

Thanks in advance!!

---

### Post by Claus7 on 2024-07-06
Hello,

searching my system didn't provide any result. I think that this kind of file is a source file that is converted to something else when it comes to the end user. I might be wrong though. Do any of the following help? I discovered them under synaptic:
```
/.
/usr
/usr/lib
/usr/lib/notification-daemon
/usr/lib/notification-daemon/notification-daemon
/usr/share
/usr/share/applications
/usr/share/applications/notification-daemon.desktop
/usr/share/doc
/usr/share/doc/notification-daemon
/usr/share/doc/notification-daemon/NEWS.gz
/usr/share/doc/notification-daemon/changelog.Debian.gz
/usr/share/doc/notification-daemon/copyright
/usr/share/locale
/usr/share/locale/af
/usr/share/locale/af/LC_MESSAGES
/usr/share/locale/af/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/an
/usr/share/locale/an/LC_MESSAGES
/usr/share/locale/an/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/ar
/usr/share/locale/ar/LC_MESSAGES
/usr/share/locale/ar/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/as
/usr/share/locale/as/LC_MESSAGES
/usr/share/locale/as/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/ast
/usr/share/locale/ast/LC_MESSAGES
/usr/share/locale/ast/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/be
/usr/share/locale/be/LC_MESSAGES
/usr/share/locale/be/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/bg
/usr/share/locale/bg/LC_MESSAGES
/usr/share/locale/bg/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/bn
/usr/share/locale/bn/LC_MESSAGES
/usr/share/locale/bn/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/bn_IN
/usr/share/locale/bn_IN/LC_MESSAGES
/usr/share/locale/bn_IN/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/bs
/usr/share/locale/bs/LC_MESSAGES
/usr/share/locale/bs/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/ca
/usr/share/locale/ca/LC_MESSAGES
/usr/share/locale/ca/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/ca@valencia
/usr/share/locale/ca@valencia/LC_MESSAGES
/usr/share/locale/ca@valencia/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/cs
/usr/share/locale/cs/LC_MESSAGES
/usr/share/locale/cs/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/da
/usr/share/locale/da/LC_MESSAGES
/usr/share/locale/da/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/de
/usr/share/locale/de/LC_MESSAGES
/usr/share/locale/de/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/el
/usr/share/locale/el/LC_MESSAGES
/usr/share/locale/el/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/en_GB
/usr/share/locale/en_GB/LC_MESSAGES
/usr/share/locale/en_GB/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/eo
/usr/share/locale/eo/LC_MESSAGES
/usr/share/locale/eo/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/es
/usr/share/locale/es/LC_MESSAGES
/usr/share/locale/es/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/et
/usr/share/locale/et/LC_MESSAGES
/usr/share/locale/et/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/eu
/usr/share/locale/eu/LC_MESSAGES
/usr/share/locale/eu/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/fa
/usr/share/locale/fa/LC_MESSAGES
/usr/share/locale/fa/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/fi
/usr/share/locale/fi/LC_MESSAGES
/usr/share/locale/fi/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/fr
/usr/share/locale/fr/LC_MESSAGES
/usr/share/locale/fr/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/fur
/usr/share/locale/fur/LC_MESSAGES
/usr/share/locale/fur/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/gl
/usr/share/locale/gl/LC_MESSAGES
/usr/share/locale/gl/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/gu
/usr/share/locale/gu/LC_MESSAGES
/usr/share/locale/gu/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/he
/usr/share/locale/he/LC_MESSAGES
/usr/share/locale/he/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/hi
/usr/share/locale/hi/LC_MESSAGES
/usr/share/locale/hi/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/hu
/usr/share/locale/hu/LC_MESSAGES
/usr/share/locale/hu/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/id
/usr/share/locale/id/LC_MESSAGES
/usr/share/locale/id/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/it
/usr/share/locale/it/LC_MESSAGES
/usr/share/locale/it/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/ja
/usr/share/locale/ja/LC_MESSAGES
/usr/share/locale/ja/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/km
/usr/share/locale/km/LC_MESSAGES
/usr/share/locale/km/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/kn
/usr/share/locale/kn/LC_MESSAGES
/usr/share/locale/kn/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/ko
/usr/share/locale/ko/LC_MESSAGES
/usr/share/locale/ko/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/lt
/usr/share/locale/lt/LC_MESSAGES
/usr/share/locale/lt/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/lv
/usr/share/locale/lv/LC_MESSAGES
/usr/share/locale/lv/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/ml
/usr/share/locale/ml/LC_MESSAGES
/usr/share/locale/ml/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/mr
/usr/share/locale/mr/LC_MESSAGES
/usr/share/locale/mr/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/ms
/usr/share/locale/ms/LC_MESSAGES
/usr/share/locale/ms/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/nb
/usr/share/locale/nb/LC_MESSAGES
/usr/share/locale/nb/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/nl
/usr/share/locale/nl/LC_MESSAGES
/usr/share/locale/nl/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/nn
/usr/share/locale/nn/LC_MESSAGES
/usr/share/locale/nn/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/oc
/usr/share/locale/oc/LC_MESSAGES
/usr/share/locale/oc/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/or
/usr/share/locale/or/LC_MESSAGES
/usr/share/locale/or/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/pa
/usr/share/locale/pa/LC_MESSAGES
/usr/share/locale/pa/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/pl
/usr/share/locale/pl/LC_MESSAGES
/usr/share/locale/pl/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/pt
/usr/share/locale/pt/LC_MESSAGES
/usr/share/locale/pt/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/pt_BR
/usr/share/locale/pt_BR/LC_MESSAGES
/usr/share/locale/pt_BR/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/quz
/usr/share/locale/quz/LC_MESSAGES
/usr/share/locale/quz/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/ro
/usr/share/locale/ro/LC_MESSAGES
/usr/share/locale/ro/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/ru
/usr/share/locale/ru/LC_MESSAGES
/usr/share/locale/ru/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/sk
/usr/share/locale/sk/LC_MESSAGES
/usr/share/locale/sk/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/sl
/usr/share/locale/sl/LC_MESSAGES
/usr/share/locale/sl/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/sr
/usr/share/locale/sr/LC_MESSAGES
/usr/share/locale/sr/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/sr@latin
/usr/share/locale/sr@latin/LC_MESSAGES
/usr/share/locale/sr@latin/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/sv
/usr/share/locale/sv/LC_MESSAGES
/usr/share/locale/sv/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/ta
/usr/share/locale/ta/LC_MESSAGES
/usr/share/locale/ta/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/te
/usr/share/locale/te/LC_MESSAGES
/usr/share/locale/te/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/th
/usr/share/locale/th/LC_MESSAGES
/usr/share/locale/th/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/tr
/usr/share/locale/tr/LC_MESSAGES
/usr/share/locale/tr/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/ug
/usr/share/locale/ug/LC_MESSAGES
/usr/share/locale/ug/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/uk
/usr/share/locale/uk/LC_MESSAGES
/usr/share/locale/uk/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/uz@cyrillic
/usr/share/locale/uz@cyrillic/LC_MESSAGES
/usr/share/locale/uz@cyrillic/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/vi
/usr/share/locale/vi/LC_MESSAGES
/usr/share/locale/vi/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/zh_CN
/usr/share/locale/zh_CN/LC_MESSAGES
/usr/share/locale/zh_CN/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/zh_HK
/usr/share/locale/zh_HK/LC_MESSAGES
/usr/share/locale/zh_HK/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/zh_TW
/usr/share/locale/zh_TW/LC_MESSAGES
/usr/share/locale/zh_TW/LC_MESSAGES/notification-daemon.mo
/usr/share/locale/zu
/usr/share/locale/zu/LC_MESSAGES
/usr/share/locale/zu/LC_MESSAGES/notification-daemon.mo
```

Regards!

---

### Post by #&amp;thj^% on 2024-07-06
This seems to be in Gnome-Shell, and that counts me out.

But you could try to find it with:
Run this in one terminal:
```
dbus-monitor

```
Then in another window run a test:
```
notify-send Test 'a\nb'

```
Look in the window with dbus working.

Since I'm not a Gnome user this is just a guess.

---

### Post by jbicha on 2024-07-08
If you are using Ubuntu 24.04 LTS, we are trying to get a [different SRU]("https://launchpad.net/ubuntu/+source/gnome-shell") fixed before updating to 46.2 or 46.3. Bundling too many attempted fixed into a single SRU doesn't work well.

If you are using Ubuntu 24.10 (still in development), you would already have gnome-shell 46.2 with this fix.

It's not possible to apply the fix directly without building gnome-shell. That file is compiled, not left as plain text on the computer.

---

### Post by #&amp;thj^% on 2024-07-08
> **jbicha said:**
> 
If you are using Ubuntu 24.10 (still in development), you would already have gnome-shell 46.2 with this fix.

It's not possible to apply the fix directly without building gnome-shell. That file is compiled, not left as plain text on the computer.
Thanks jbicha, that explains a lot. (My Guess for Gnome-Shell)
```
apt policy gnome-shell
gnome-shell:
  Installed: (none)
  Candidate: 46.2-1ubuntu4
  Version table:
     46.2-1ubuntu4 500
        500 http://archive.ubuntu.com/ubuntu oracular/main amd64 Packages

```

---

