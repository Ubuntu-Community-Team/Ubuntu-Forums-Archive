---
title: "Removing LibreOffice."
date: 2020-04-10
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2020-04-10
I cannot remove LibreOffice sing the following command:

```
sudo apt remove --purge libreoffice*Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libreoffice*
```

I already install LibreOffice with a deb installer, and I also installed ubuntu-software, but neither store shows LibreOffice installed.

---

### Post by deadflowr on 2020-04-10
apt doesn't handle wildcards and globbing like that
it literally thinks the package is called libreoffice*.

use apt-get instead.

---

### Post by Hewjr100 on 2020-04-10
Will do right now.

Henry

---

### Post by Hewjr100 on 2020-04-10
It's a beautiful thing, when something works.  Thanks for your help.

Henry

---

### Post by zika on 2020-04-11
It is, somehow, good thing that apt does not handle wildcards as it did before, preventing us from making mistakes and such... You can always do```
:~$ apt search libreoffice-|grep install

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

libreoffice-base-core/focal,now 1:6.4.2-0ubuntu3 amd64 [installed,automatic]
libreoffice-calc/focal,now 1:6.4.2-0ubuntu3 amd64 [installed,automatic]
libreoffice-common/focal,now 1:6.4.2-0ubuntu3 all [installed,automatic]
libreoffice-core/focal,now 1:6.4.2-0ubuntu3 amd64 [installed,automatic]
libreoffice-draw/focal,now 1:6.4.2-0ubuntu3 amd64 [installed,automatic]
libreoffice-gnome/focal,now 1:6.4.2-0ubuntu3 amd64 [installed,automatic]
libreoffice-gtk3/focal,now 1:6.4.2-0ubuntu3 amd64 [installed,automatic]
libreoffice-help-common/focal,now 1:6.4.2-0ubuntu3 all [installed,automatic]
libreoffice-help-en-gb/focal,now 1:6.4.2-0ubuntu3 all [installed]
libreoffice-help-en-us/focal,now 1:6.4.2-0ubuntu3 all [installed]
libreoffice-impress/focal,now 1:6.4.2-0ubuntu3 amd64 [installed,automatic]
libreoffice-l10n-en-gb/focal,now 1:6.4.2-0ubuntu3 all [installed,automatic]
libreoffice-l10n-en-za/focal,now 1:6.4.2-0ubuntu3 all [installed]
libreoffice-math/focal,now 1:6.4.2-0ubuntu3 amd64 [installed,automatic]
libreoffice-ogltrans/focal,now 1:6.4.2-0ubuntu3 all [installed,automatic]
libreoffice-pdfimport/focal,now 1:6.4.2-0ubuntu3 all [installed,automatic]
libreoffice-style-breeze/focal,now 1:6.4.2-0ubuntu3 all [installed,automatic]
libreoffice-style-colibre/focal,now 1:6.4.2-0ubuntu3 all [installed,automatic]
libreoffice-style-elementary/focal,now 1:6.4.2-0ubuntu3 all [installed,automatic]
libreoffice-style-tango/focal,now 1:6.4.2-0ubuntu3 all [installed,automatic]
libreoffice-writer/focal,now 1:6.4.2-0ubuntu3 amd64 [installed,automatic]
```or```
:~$ apt search libreoffice|grep install

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

fonts-opensymbol/focal,now 2:102.11+LibO6.4.2-0ubuntu3 all [installed,automatic]
hunspell-en-au/focal,now 1:2018.04.16-1 all [installed]
hunspell-en-ca/focal,now 1:2018.04.16-1 all [installed]
hunspell-en-gb/focal,now 1:6.4.0~rc2-1 all [installed]
hunspell-en-us/focal,now 1:2018.04.16-1 all [installed,automatic]
hunspell-en-za/focal,now 1:6.4.0~rc2-1 all [installed]
hyphen-en-gb/focal,now 1:6.4.0~rc2-1 all [installed]
hyphen-en-us/focal,now 2.8.8-7 all [installed]
libjuh-java/focal,now 1:6.4.2-0ubuntu3 all [installed,automatic]
libjurt-java/focal,now 1:6.4.2-0ubuntu3 all [installed,automatic]
libreoffice-base-core/focal,now 1:6.4.2-0ubuntu3 amd64 [installed,automatic]
libreoffice-calc/focal,now 1:6.4.2-0ubuntu3 amd64 [installed,automatic]
libreoffice-common/focal,now 1:6.4.2-0ubuntu3 all [installed,automatic]
libreoffice-core/focal,now 1:6.4.2-0ubuntu3 amd64 [installed,automatic]
libreoffice-draw/focal,now 1:6.4.2-0ubuntu3 amd64 [installed,automatic]
libreoffice-gnome/focal,now 1:6.4.2-0ubuntu3 amd64 [installed,automatic]
libreoffice-gtk3/focal,now 1:6.4.2-0ubuntu3 amd64 [installed,automatic]
libreoffice-help-common/focal,now 1:6.4.2-0ubuntu3 all [installed,automatic]
libreoffice-help-en-gb/focal,now 1:6.4.2-0ubuntu3 all [installed]
libreoffice-help-en-us/focal,now 1:6.4.2-0ubuntu3 all [installed]
libreoffice-impress/focal,now 1:6.4.2-0ubuntu3 amd64 [installed,automatic]
libreoffice-l10n-en-gb/focal,now 1:6.4.2-0ubuntu3 all [installed,automatic]
libreoffice-l10n-en-za/focal,now 1:6.4.2-0ubuntu3 all [installed]
libreoffice-math/focal,now 1:6.4.2-0ubuntu3 amd64 [installed,automatic]
libreoffice-ogltrans/focal,now 1:6.4.2-0ubuntu3 all [installed,automatic]
libreoffice-pdfimport/focal,now 1:6.4.2-0ubuntu3 all [installed,automatic]
libreoffice-style-breeze/focal,now 1:6.4.2-0ubuntu3 all [installed,automatic]
libreoffice-style-colibre/focal,now 1:6.4.2-0ubuntu3 all [installed,automatic]
libreoffice-style-elementary/focal,now 1:6.4.2-0ubuntu3 all [installed,automatic]
libreoffice-style-tango/focal,now 1:6.4.2-0ubuntu3 all [installed,automatic]
libreoffice-writer/focal,now 1:6.4.2-0ubuntu3 amd64 [installed,automatic]
libridl-java/focal,now 1:6.4.2-0ubuntu3 all [installed,automatic]
libuno-cppu3/focal,now 1:6.4.2-0ubuntu3 amd64 [installed,automatic]
libuno-cppuhelpergcc3-3/focal,now 1:6.4.2-0ubuntu3 amd64 [installed,automatic]
libuno-purpenvhelpergcc3-3/focal,now 1:6.4.2-0ubuntu3 amd64 [installed,automatic]
libuno-sal3/focal,now 1:6.4.2-0ubuntu3 amd64 [installed,automatic]
libuno-salhelpergcc3-3/focal,now 1:6.4.2-0ubuntu3 amd64 [installed,automatic]
libunoloader-java/focal,now 1:6.4.2-0ubuntu3 all [installed,automatic]
mythes-en-us/focal,now 1:6.4.0~rc2-1 all [installed]
uno-libs-private/focal,now 1:6.4.2-0ubuntu3 amd64 [installed,automatic]
ure/focal,now 1:6.4.2-0ubuntu3 amd64 [installed,automatic]
```then, create proper apt command ...
See the difference that one &#8222;-&#8220; makes... ;)

---

### Post by corradoventu on 2020-04-13
Or better use synaptic!

---

### Post by Hewjr100 on 2020-04-13
Yep I need to install it.

Henry

---

### Post by The Cog on 2020-04-13
```
sudo apt install synaptic
```
Pretty-much the first thing I do on a new install.

---

