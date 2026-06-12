---
title: "Questions about Xubuntu 23.10"
date: 2023-09-19
forum: Ubuntu Development Version
---

### Post by jacatone on 2023-09-19
I removed some software like Libre Office from my install and now think I'm missing some dependencies.  Is there a cli imputs or program to check this?

---

### Post by #&amp;thj^% on 2023-09-19
23.10 has not been released yet this belongs in Development sub Forum
All I can show you is:
```
 apt depends libreoffice
libreoffice
  Depends: libreoffice-base
  Depends: libreoffice-calc
  Depends: libreoffice-core (= 4:7.6.1~rc2-0ubuntu2)
  Depends: libreoffice-draw
  Depends: libreoffice-impress
  Depends: libreoffice-math
  Depends: libreoffice-report-builder-bin
  Depends: libreoffice-writer
  Depends: python3-uno
  Conflicts: libreoffice-dev (<= 1:5.0.3~rc1-2)
  Conflicts: libreoffice-dev-doc (<= 1:5.0.3~rc1-2)
  Recommends: fonts-crosextra-caladea
  Recommends: fonts-crosextra-carlito
  Recommends: fonts-dejavu
  Recommends: fonts-linuxlibertine
  Recommends: fonts-noto-core
  Recommends: fonts-noto-extra
  Recommends: fonts-noto-mono
  Recommends: fonts-noto-ui-core
  Recommends: fonts-sil-gentium-basic
 |Recommends: libreoffice-gnome
  Recommends: libreoffice-plasma
  Recommends: libreoffice-nlpsolver
  Recommends: libreoffice-report-builder
  Recommends: libreoffice-script-provider-bsh
  Recommends: libreoffice-script-provider-js
  Recommends: libreoffice-script-provider-python
  Recommends: libreoffice-sdbc-mysql
  Recommends: libreoffice-sdbc-postgresql
  Recommends: libreoffice-wiki-publisher
  Recommends: libreoffice-java-common (>= 4:7.6.1~rc2~)
  Recommends: fonts-liberation (>= 1:2)
  Recommends: fonts-liberation-sans-narrow
  Suggests: cups-bsd
    cups-bsd:i386
 |Suggests: firefox
 |Suggests: firefox-esr
  Suggests: thunderbird
  Suggests: ghostscript
    ghostscript:i386
  Suggests: gnupg
  Suggests: gpa
  Suggests: <hunspell-dictionary>
    hunspell-af
    hunspell-an
    hunspell-ar
    hunspell-be
    hunspell-bg
    hunspell-bn
    hunspell-bo
    hunspell-br
    hunspell-bs
    hunspell-ca
    hunspell-cs
    hunspell-da
    hunspell-de-at
    hunspell-de-at-frami
    hunspell-de-ch
    hunspell-de-ch-frami
    hunspell-de-de
    hunspell-de-de-frami
    hunspell-dz
    hunspell-el
    hunspell-en-au
    hunspell-en-ca
    hunspell-en-gb
    hunspell-en-us
    hunspell-en-za
    hunspell-es
    hunspell-eu
    hunspell-fr-classical
    hunspell-fr-comprehensive
    hunspell-fr-revised
    hunspell-gd
    hunspell-gl
    hunspell-gu
    hunspell-gug
    hunspell-he
    hunspell-hi
    hunspell-hr
    hunspell-hu
    hunspell-id
    hunspell-is
    hunspell-it
    hunspell-kk
    hunspell-kmr
    hunspell-ko
    hunspell-lo
    hunspell-lt
    hunspell-lv
    hunspell-mn
    hunspell-ne
    hunspell-nl
    hunspell-no
    hunspell-oc
    hunspell-pl
    hunspell-pt-br
    hunspell-pt-pt
    hunspell-ro
    hunspell-ru
    hunspell-si
    hunspell-sk
    hunspell-sl
    hunspell-sr
    hunspell-sv
    hunspell-sw
    hunspell-te
    hunspell-th
    hunspell-tr
    hunspell-uk
    hunspell-uz
    hunspell-vi
    myspell-eo
    myspell-es
    myspell-et
    myspell-fo
    myspell-fr
    myspell-tl
  Suggests: <hyphen-hyphenation-patterns>
    hyphen-af
    hyphen-be
    hyphen-bg
    hyphen-ca
    hyphen-cs
    hyphen-da
    hyphen-de
    hyphen-el
    hyphen-en-gb
    hyphen-en-us
    hyphen-es
    hyphen-fr
    hyphen-gl
    hyphen-hr
    hyphen-hu
    hyphen-id
    hyphen-is
    hyphen-it
    hyphen-lt
    hyphen-lv
    hyphen-mn
    hyphen-nl
    hyphen-no
    hyphen-pl
    hyphen-pt-br
    hyphen-pt-pt
    hyphen-ro
    hyphen-ru
    hyphen-sk
    hyphen-sl
    hyphen-sr
    hyphen-sv
    hyphen-th
    hyphen-uk
    hyphen-zu
    myspell-et
 |Suggests: imagemagick
    graphicsmagick-imagemagick-compat
    imagemagick:i386
    imagemagick-6.q16:i386
    imagemagick-6.q16
  Suggests: graphicsmagick-imagemagick-compat
  Suggests: libgl1
  Suggests: <libreoffice-grammarcheck>
    libreoffice-lightproof-en
    libreoffice-lightproof-hu
    libreoffice-lightproof-pt-br
    libreoffice-lightproof-ru-ru
  Suggests: <libreoffice-help> (= 7.6)
    libreoffice-help-ca
    libreoffice-help-cs
    libreoffice-help-da
    libreoffice-help-de
    libreoffice-help-dz
    libreoffice-help-el
    libreoffice-help-en-gb
    libreoffice-help-en-us
    libreoffice-help-es
    libreoffice-help-et
    libreoffice-help-eu
    libreoffice-help-fi
    libreoffice-help-fr
    libreoffice-help-gl
    libreoffice-help-hi
    libreoffice-help-hu
    libreoffice-help-id
    libreoffice-help-it
    libreoffice-help-ja
    libreoffice-help-km
    libreoffice-help-ko
    libreoffice-help-nl
    libreoffice-help-om
    libreoffice-help-pl
    libreoffice-help-pt
    libreoffice-help-pt-br
    libreoffice-help-ru
    libreoffice-help-sk
    libreoffice-help-sl
    libreoffice-help-sv
    libreoffice-help-tr
    libreoffice-help-vi
    libreoffice-help-zh-cn
    libreoffice-help-zh-tw
  Suggests: <libreoffice-l10n> (= 7.6)
    libreoffice-l10n-af
    libreoffice-l10n-am
    libreoffice-l10n-ar
    libreoffice-l10n-as
    libreoffice-l10n-ast
    libreoffice-l10n-be
    libreoffice-l10n-bg
    libreoffice-l10n-bn
    libreoffice-l10n-br
    libreoffice-l10n-bs
    libreoffice-l10n-ca
    libreoffice-l10n-cs
    libreoffice-l10n-cy
    libreoffice-l10n-da
    libreoffice-l10n-de
    libreoffice-l10n-dz
    libreoffice-l10n-el
    libreoffice-l10n-en-gb
    libreoffice-l10n-en-za
    libreoffice-l10n-eo
    libreoffice-l10n-es
    libreoffice-l10n-et
    libreoffice-l10n-eu
    libreoffice-l10n-fa
    libreoffice-l10n-fi
    libreoffice-l10n-fr
    libreoffice-l10n-ga
    libreoffice-l10n-gd
    libreoffice-l10n-gl
    libreoffice-l10n-gu
    libreoffice-l10n-gug
    libreoffice-l10n-he
    libreoffice-l10n-hi
    libreoffice-l10n-hr
    libreoffice-l10n-hu
    libreoffice-l10n-id
    libreoffice-l10n-is
    libreoffice-l10n-it
    libreoffice-l10n-ja
    libreoffice-l10n-ka
    libreoffice-l10n-kk
    libreoffice-l10n-km
    libreoffice-l10n-kmr
    libreoffice-l10n-kn
    libreoffice-l10n-ko
    libreoffice-l10n-lt
    libreoffice-l10n-lv
    libreoffice-l10n-mk
    libreoffice-l10n-ml
    libreoffice-l10n-mn
    libreoffice-l10n-mr
    libreoffice-l10n-nb
    libreoffice-l10n-ne
    libreoffice-l10n-nl
    libreoffice-l10n-nn
    libreoffice-l10n-nr
    libreoffice-l10n-nso
    libreoffice-l10n-oc
    libreoffice-l10n-om
    libreoffice-l10n-or
    libreoffice-l10n-pa-in
    libreoffice-l10n-pl
    libreoffice-l10n-pt
    libreoffice-l10n-pt-br
    libreoffice-l10n-ro
    libreoffice-l10n-ru
    libreoffice-l10n-rw
    libreoffice-l10n-si
    libreoffice-l10n-sk
    libreoffice-l10n-sl
    libreoffice-l10n-sr
    libreoffice-l10n-ss
    libreoffice-l10n-st
    libreoffice-l10n-sv
    libreoffice-l10n-szl
    libreoffice-l10n-ta
    libreoffice-l10n-te
    libreoffice-l10n-tg
    libreoffice-l10n-th
    libreoffice-l10n-tn
    libreoffice-l10n-tr
    libreoffice-l10n-ts
    libreoffice-l10n-ug
    libreoffice-l10n-uk
    libreoffice-l10n-uz
    libreoffice-l10n-ve
    libreoffice-l10n-vi
    libreoffice-l10n-xh
    libreoffice-l10n-zh-cn
    libreoffice-l10n-zh-tw
    libreoffice-l10n-zu
  Suggests: libreoffice-librelogo
  Suggests: libxrender1
  Suggests: <myspell-dictionary>
    myspell-de-de-1901
    myspell-fr-gut
    myspell-he
    hunspell-kk
    myspell-cs
    myspell-da
    myspell-en-au
    myspell-eo
    myspell-es
    myspell-et
    myspell-fa
    myspell-fo
    myspell-fr
    myspell-ga
    myspell-gd
    myspell-gv
    myspell-hu
    myspell-hy
    myspell-nb
    myspell-nn
    myspell-sk
    myspell-sq
    myspell-tl
    myspell-uk
  Suggests: <mythes-thesaurus>
    mythes-ar
    mythes-bg
    mythes-ca
    mythes-cs
    mythes-da
    mythes-de
    mythes-de-ch
    mythes-en-us
    mythes-es
    mythes-fr
    mythes-gl
    mythes-gug
    mythes-hu
    mythes-id
    mythes-is
    mythes-it
    mythes-lv
    mythes-ne
    mythes-no
    mythes-pl
    mythes-pt-br
    mythes-pt-pt
    mythes-ro
    mythes-ru
    mythes-sk
    mythes-sl
    mythes-sv
    mythes-uk
  Suggests: openclipart-libreoffice
  Suggests: pstoedit
  Suggests: unixodbc
    unixodbc:i386
  Suggests: gstreamer1.0-plugins-base
  Suggests: gstreamer1.0-plugins-good
  Suggests: gstreamer1.0-plugins-ugly
  Suggests: gstreamer1.0-plugins-bad
  Suggests: gstreamer1.0-libav
 |Suggests: default-jre (>= 2:1.8)
 |Suggests: <java-runtime> (>= 8)
    default-jre
    openjdk-11-jre
    openjdk-17-jre
    openjdk-21-jre
    openjdk-22-jre
 |Suggests: <java8-runtime>
    default-jre
    openjdk-11-jre
    openjdk-17-jre
    openjdk-19-jre
    openjdk-20-jre
    openjdk-21-jre
    openjdk-22-jre
    openjdk-8-jre
  Suggests: <jre>
  Suggests: libsane1
  Suggests: libofficebean-java

```
you won't get bored reading all:
```
 apt show libreoffice
Package: libreoffice
Version: 4:7.6.1~rc2-0ubuntu2
Priority: optional
Section: universe/editors
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian LibreOffice Maintainers <debian-openoffice@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 73.7 kB
Depends: libreoffice-base, libreoffice-calc, libreoffice-core (= 4:7.6.1~rc2-0ubuntu2), libreoffice-draw, libreoffice-impress, libreoffice-math, libreoffice-report-builder-bin, libreoffice-writer, python3-uno
Recommends: fonts-crosextra-caladea, fonts-crosextra-carlito, fonts-dejavu, fonts-linuxlibertine, fonts-noto-core, fonts-noto-extra, fonts-noto-mono, fonts-noto-ui-core, fonts-sil-gentium-basic, libreoffice-gnome | libreoffice-plasma, libreoffice-nlpsolver, libreoffice-report-builder, libreoffice-script-provider-bsh, libreoffice-script-provider-js, libreoffice-script-provider-python, libreoffice-sdbc-mysql, libreoffice-sdbc-postgresql, libreoffice-wiki-publisher, libreoffice-java-common (>= 4:7.6.1~rc2~), fonts-liberation (>= 1:2), fonts-liberation-sans-narrow
Suggests: cups-bsd, firefox | firefox-esr | thunderbird, ghostscript, gnupg, gpa, hunspell-dictionary, hyphen-hyphenation-patterns, imagemagick | graphicsmagick-imagemagick-compat, libgl1, libreoffice-grammarcheck, libreoffice-help (= 7.6), libreoffice-l10n (= 7.6), libreoffice-librelogo, libxrender1, myspell-dictionary, mythes-thesaurus, openclipart-libreoffice, pstoedit, unixodbc, gstreamer1.0-plugins-base, gstreamer1.0-plugins-good, gstreamer1.0-plugins-ugly, gstreamer1.0-plugins-bad, gstreamer1.0-libav, default-jre (>= 2:1.8) | java-runtime (>= 8) | java8-runtime | jre, libsane1, libofficebean-java
Conflicts: libreoffice-dev (<= 1:5.0.3~rc1-2), libreoffice-dev-doc (<= 1:5.0.3~rc1-2)
Homepage: http://www.libreoffice.org
Task: edubuntu-desktop-gnome
Download-Size: 14.9 kB
APT-Sources: http://us.archive.ubuntu.com/ubuntu mantic/universe amd64 Packages
Description: office productivity suite (metapackage)
 LibreOffice is a full-featured office productivity suite that provides
 a near drop-in replacement for Microsoft(R) Office.
 .
 This metapackage installs all components of libreoffice:
  * libreoffice-writer: Word processor
  * libreoffice-calc: Spreadsheet
  * libreoffice-impress: Presentation
  * libreoffice-draw: Drawing
  * libreoffice-base: Database
  * libreoffice-math: Equation editor
 It also recommends additional packages (e.g. fonts) in order to match an
 upstream LibreOffice install as closely as possible.
 .
 You can extend the functionality of LibreOffice by installing these
 packages:
  * hunspell-*/myspell-*: Hunspell/Myspell dictionaries
    for use with LibreOffice
  * libreoffice-l10n-*: UI interface translation
  * libreoffice-help-*: User help
  * mythes-*: Thesauri for the use with LibreOffice
  * hyphen-*: Hyphenation patterns for LibreOffice
  * libreoffice-gtk(2|3): Gtk UI Plugin, GNOME File Picker support
  * libreoffice-gnome: GIO backend
  * unixodbc: ODBC database support
  * cups-bsd: Allows LibreOffice to detect your CUPS printer queues
    automatically
  * libsane: Use your sane-supported scanner with LibreOffice
  * libxrender1: Speed up display by using Xrender library
  * libgl1: OpenGL support
  * openclipart-libreoffice: Open Clip Art Gallery with LibreOffice index
    files
  * firefox-esr | thunderbird | firefox:
    Mozilla profile with Certificates needed for XML Security...
  * openjdk-11-jre | openjdk-8-jre | java8-runtime:
    Java Runtime Environment for use with LibreOffice
  * pstoedit / imagemagick / ghostscript: helper tools for EPS
  * gstreamer0.10-plugins-*: GStreamer plugins for use with LibreOffices
    media backend
  * libpaper-utils: papersize detection support via paperconf
  * bluez: Bluetooth support for Impress (slideshow remote control)

```
You think your missing some Deps? or you know your missing Deps

---

### Post by guiverc on 2023-09-19
This may not be helpful (see 1fallen's response), but just in case I'll provide it.

To see what packages are installed, you can view the manifest for the ISO you used. There are two Xubuntu ISOs, the full ISO manifest being [https://cdimage.ubuntu.com/xubuntu/daily-live/current/mantic-desktop-amd64.manifest](https://cdimage.ubuntu.com/xubuntu/daily-live/current/mantic-desktop-amd64.manifest)

I often find that helpful to see if something was removed that was original media; beyond the obvious viewing your *apt* log history 

```
/var/log/apt/history.log
```

as viewing the log lets me see what I removed, and the manifest helps me determine if it was an original installed package, or something I added myself (*roughly*).

Not all packages on the ISO/manifest will be installed; you can select options during install that cause a *minimal* type of install, causing the packages to actually install then get removed (*minimal install installs everything, then removes packages according to a droplist as this is faster*), which includes the installer itself (`ubiquity`) which you'll note on the ISO as used to install, but it won't exist on your installed system (*there is no need** for it*).

I was tempted to include a `dpkg -l |grep libreoffice` from my system, alas my system may no longer unaltered, and you can get details from the manifest itself.

Please note:  Ubuntu *mantic* is still in *development* and actually still *alpha* (but *beta* is less than a day away now) so changes can occur from one ISO to another, even if at a slower pace given we've passed [*beta freeze*]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2023-September/001339.html")*, *and also note there can be multiple *dailies* in a single day, thus *manifest* files are specific to the ISO they relate to.  I use the *current* one in my URL, but it's not the only one.

Edit:   I just checked and the ISO/QA tracker now lists BETA ([http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)) ... though it was actually *build* notices that made be check.

20230919.1 is the first marked *beta* for Xubuntu Desktop
20230919.3 is the first marked *beta* for Xubuntu Minimal

alas I note some uploads didn't make it prior to *beta freeze* for Xubuntu :(

---

