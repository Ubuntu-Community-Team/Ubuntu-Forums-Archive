---
title: "Gnome-shell 3.16.2"
date: 2015-06-05
forum: Ubuntu Development Version
---

### Post by harry332 on 2015-06-05
New Gnome-shell 3.16.2 has arrived into Wily official repos.
ATM on proposed.
Working very well.

---

### Post by dino99 on 2015-06-05
****** has arrived ******
only a small packages list by now; still getting some upgrades each day :p

---

### Post by zika on 2015-06-05
Still longing for HideTopBar that works in 3.16 ... ;)

---

### Post by QDR06VV9 on 2015-06-05
> **zika said:**
> Still longing for HideTopBar that works in 3.16 ... ;)
+1 And That Stawberry of yours is making me Hungary!;)
Good things come for Us that wait.

---

### Post by kansasnoob on 2015-06-05
> **zika said:**
> Still longing for HideTopBar that works in 3.16 ... ;)

Does that require an extension? Or is it something that can just be GNOME Tweaked?

An auto-hiding top bar would be great!!!!!!!!!

---

### Post by Chanath on 2015-06-06
> **zika said:**
> Still longing for HideTopBar that works in 3.16 ... ;)

Hide top bar works in 3.16.2, so try again.
EDIT: I used the staging ppa to install 3.16.2

---

### Post by harry332 on 2015-06-06
Surely not as impressive as in Gnome3 Staging PPA.
I did mean gnome-shell (packages gnome-shell, mutter and GTK+3), not the whole Gnome 3.16.2, though.

---

### Post by zika on 2015-06-06
> **Chanath said:**
> Hide top bar works in 3.16.2, so try again.
EDIT: I used the staging ppa to install 3.16.2```
:~$ dpkg -l|grep gnome-shell
ii  gnome-shell                                           3.16.2-1ubuntu1                                    amd64        graphical shell for the GNOME desktop
ii  gnome-shell-common                                    3.16.2-1ubuntu1                                    all          common files for the GNOME graphical shell
ii  gnome-shell-extensions                                3.16.1-0ubuntu1                                    all          Extensions to extend functionality of GNOME Shell
```It works after some persuasion. Thank You for encouragement. Depreciation of NPAPI in modern browsers does not help, but, on the other hand, makes it more intuitive once I turned my weekend brain on... ;)
```
:~$ cat /var/lib/apt/lists/ppa.launchpad.net_gnome3-team_gnome3-staging_ubuntu_dists_wily_main_binary-amd64_Packages |grep Package
Package: gtk-doc-tools
Package: libglib2.0-0
Package: libglib2.0-0-dbg
Package: libglib2.0-data
Package: libglib2.0-dev
Package: libglib2.0-doc
Package: gnome-cards-data
Package: valac
Package: libwebkitgtk-dev
Package: libwebkit-dev
Package: gobject-introspection
Package: libglib2.0-0-refdbg
Package: libgirepository1.0-dev
Package: libclutter-1.0-0
Package: libclutter-1.0-dev
Package: libclutter-1.0-dbg
Package: libclutter-1.0-doc
Package: aisleriot
Package: libglib2.0-bin
Package: clutter-1.0-tests
Package: libgirepository1.0-doc
Package: libwebkitgtk-3.0-0
Package: libwebkitgtk-3.0-dev
Package: libwebkitgtk-3.0-common
Package: libgirepository-1.0-1
Package: gir1.2-glib-2.0
Package: gir1.2-freedesktop
Package: gir1.2-clutter-1.0
Package: gir1.2-gtk-3.0
Package: libwebkitgtk-1.0-0
Package: libwebkitgtk-1.0-0-dbg
Package: libwebkitgtk-1.0-common
Package: libclutter-1.0-common
Package: libwebkitgtk-3.0-0-dbg
Package: gir1.2-webkit-3.0
Package: libgtk-3-0
Package: libgtk-3-dev
Package: libgtk-3-0-dbg
Package: gtk-3-examples
Package: libgail-3-0
Package: libgail-3-dev
Package: libgail-3-0-dbg
Package: libgtk-3-common
Package: libgtk-3-bin
Package: libgtk-3-doc
Package: libgail-3-doc
Package: valadoc
Package: libjavascriptcoregtk-1.0-0
Package: libjavascriptcoregtk-1.0-dev
Package: libjavascriptcoregtk-1.0-0-dbg
Package: libjavascriptcoregtk-3.0-0
Package: libjavascriptcoregtk-3.0-dev
Package: libjavascriptcoregtk-3.0-0-dbg
Package: gir1.2-javascriptcoregtk-3.0
Package: libvaladoc-dev
Package: libwebkit2gtk-3.0-dev
Package: gir1.2-webkit2-3.0
Package: libwebkit2gtk-3.0-25
Package: libwebkit2gtk-3.0-25-dbg
Package: libglib2.0-tests
Package: libvaladoc-data
Package: libwebkitgtk-common-dev
Package: libjavascriptcoregtk-3.0-bin
Package: libinput-dev
Package: valac-0.28
Package: libvala-0.28-0
Package: libvala-0.28-dev
Package: valac-0.28-dbg
Package: libvala-0.28-0-dbg
Package: valac-0.28-vapi
Package: vala-0.28-doc
Package: libvaladoc3
Package: libinput10
Package: libinput10-dbg
Package: valac-0.30-vapi
Package: vala-0.30-doc
Package: valac-0.30
Package: libvala-0.30-0
Package: libvala-0.30-dev
Package: valac-0.30-dbg
Package: libvala-0.30-0-dbg
``````
:~$ cat /var/lib/apt/lists/ppa.launchpad.net_ricotz_testing_ubuntu_dists_wily_main_binary-amd64_Packages |grep Package
Package: gtk-doc-tools
Package: libglib2.0-0
Package: libglib2.0-0-dbg
Package: libglib2.0-data
Package: libglib2.0-dev
Package: libglib2.0-doc
Package: valac
Package: gobject-introspection
Package: libglib2.0-0-refdbg
Package: libgirepository1.0-dev
Package: libglib2.0-bin
Package: libgirepository1.0-doc
Package: libgirepository-1.0-1
Package: gir1.2-glib-2.0
Package: gir1.2-freedesktop
Package: gir1.2-gtk-3.0
Package: libgtk-3-0
Package: libgtk-3-dev
Package: libgtk-3-0-dbg
Package: gtk-3-examples
Package: libgail-3-0
Package: libgail-3-dev
Package: libgail-3-0-dbg
Package: libgtk-3-common
Package: libgtk-3-bin
Package: libgtk-3-doc
Package: libgail-3-doc
Package: libglib2.0-tests
Package: valac-0.28
Package: libvala-0.28-0
Package: libvala-0.28-dev
Package: valac-0.28-dbg
Package: libvala-0.28-0-dbg
Package: valac-0.28-vapi
Package: vala-0.28-doc
Package: libmozjs-31-0
Package: libmozjs-31-0-dbg
Package: libmozjs-31-dev
Package: libmozjs-31-bin
Package: libmozjs-31-bin-dbg
Package: valac-0.30-vapi
Package: vala-0.30-doc
Package: valac-0.30
Package: libvala-0.30-0
Package: libvala-0.30-dev
Package: valac-0.30-dbg
Package: libvala-0.30-0-dbg
Package: libmozjs-38-0
Package: libmozjs-38-0-dbg
Package: libmozjs-38-dev
Package: libmozjs-38-bin
Package: libmozjs-38-bin-dbg
``````
:~$ apt-cache show gnome-shellPackage: gnome-shell
Priority: optional
Section: universe/gnome
Installed-Size: 6857
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>
Architecture: amd64
Version: 3.16.2-1ubuntu1
Depends: gir1.2-clutter-1.0 (>= 1.22), gir1.2-glib-2.0 (>= 1.39.90-4~), gir1.2-gtk-3.0 (>= 3.16), gir1.2-mutter-3.0 (>= 3.16.1), gir1.2-networkmanager-1.0, gir1.2-soup-2.4 (>= 2.40.1), gir1.2-telepathyglib-0.12, adwaita-icon-theme, dconf-gsettings-backend | gsettings-backend, libatk-bridge2.0-0 (>= 2.5.3), libatk1.0-0 (>= 1.12.4), libc6 (>= 2.14), libcairo2 (>= 1.10.0), libcanberra-gtk3-0 (>= 0.25), libcanberra0 (>= 0.2), libclutter-1.0-0 (>= 1.22.0), libcogl-pango20 (>= 1.17.4), libcogl20 (>= 1.17.4), libcroco3 (>= 0.6.2), libdbus-glib-1-2 (>= 0.78), libecal-1.2-16 (>= 3.5.91), libedataserver-1.2-18 (>= 3.5.91), libgcr-base-3-1 (>= 3.8.0), libgdk-pixbuf2.0-0 (>= 2.22.0), libgirepository-1.0-1 (>= 0.9.2), libgjs0-libmozjs-24-0, libgjs0e (>= 1.42.0), libglib2.0-0 (>= 2.39.90), libgstreamer1.0-0 (>= 1.4.0), libgtk-3-0 (>= 3.16), libical1a (>= 1.0), libjson-glib-1.0-0 (>= 0.13.2), libmozjs-24-0, libmutter0f, libnm-glib4 (>= 0.8.998), libnm-util2 (>= 0.8.998), libpango-1.0-0 (>= 1.14.0), libpangocairo-1.0-0 (>= 1.14.0), libpolkit-agent-1-0 (>= 0.99), libpolkit-gobject-1-0 (>= 0.94), libpulse-mainloop-glib0 (>= 0.99.1), libpulse0 (>= 0.99.1), libsecret-1-0 (>= 0.7), libstartup-notification0 (>= 0.11), libsystemd0, libtelepathy-glib0 (>= 0.17.5), libx11-6, libxfixes3, evolution-data-server (>= 3.7.90), gir1.2-gdm-1.0 (>= 3.5.90), gir1.2-accountsservice-1.0, gir1.2-atspi-2.0 (>= 2.9.91), gir1.2-caribou-1.0 (>= 0.4.8), gir1.2-freedesktop, gir1.2-gdesktopenums-3.0 (>= 3.12), gir1.2-gcr-3 (>= 3.7.5), gir1.2-gkbd-3.0, gir1.2-gnomebluetooth-1.0 (>= 3.6.0), gir1.2-gnomedesktop-3.0 (>= 3.12.0), gir1.2-gweather-3.0, gir1.2-ibus-1.0 (>= 1.5.2), gir1.2-nmgtk-1.0 (>= 0.9.8), gir1.2-pango-1.0, gir1.2-polkit-1.0, gir1.2-telepathylogger-0.2 (>= 0.8.0), gir1.2-upowerglib-1.0 (>= 0.99), gjs (>= 1.39.0), gnome-session, gnome-settings-daemon (>= 3.4.0), gnome-shell-common (= 3.16.2-1ubuntu1), gnome-themes-standard, gnome-backgrounds (>= 3.13.90), gsettings-desktop-schemas (>= 3.14), mutter (>= 3.16.1), python3, telepathy-mission-control-5
Recommends: gkbd-capplet, gnome-contacts, gnome-control-center, gnome-user-guide, network-manager, unzip, gdm (>= 3.5.90)
Conflicts: gnome-screensaver (<< 3.6)
Breaks: fglrx-driver (<< 1:11-10), gdm (<< 3.5.90), gnome-control-center (<< 1:3.0), gnome-session (<< 3.0), gnome-tweak-tool (<< 3.5)
Filename: pool/universe/g/gnome-shell/gnome-shell_3.16.2-1ubuntu1_amd64.deb
Size: 622312
MD5sum: 50a1bef8db79018062deec4a096de97f
SHA1: 7b50ebe1bf65957d3a6f40a8d4080d873580ad35
SHA256: 055d2e7b3f05f3ff0f2d15a3186b950f0b2f3219c883e08eff17afb45e8c0418
Description-en: graphical shell for the GNOME desktop
 The GNOME Shell provides core interface functions like switching
 windows, launching applications or see your notifications. It takes
 advantage of the capabilities of modern graphics hardware and
 introduces innovative user interface concepts to provide a
 delightful and easy to use experience. GNOME Shell is the defining
 technology of the GNOME 3 user experience.
Description-md5: 51a5a94e6b632e350489b7b8d27ab9fc
Homepage: http://live.gnome.org/GnomeShell
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Task: ubuntu-gnome-desktop


Package: gnome-shell
Priority: optional
Section: universe/gnome
Installed-Size: 6866
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>
Architecture: amd64
Version: 3.14.4-0ubuntu1
Depends: gir1.2-clutter-1.0 (>= 1.17), gir1.2-glib-2.0 (>= 1.39.90-4~), gir1.2-gtk-3.0 (>= 3.8), gir1.2-mutter-3.0 (>= 3.14.4), gir1.2-networkmanager-1.0, gir1.2-soup-2.4 (>= 2.40.1), gir1.2-telepathyglib-0.12, adwaita-icon-theme, dconf-gsettings-backend | gsettings-backend, libatk-bridge2.0-0 (>= 2.5.3), libatk1.0-0 (>= 1.12.4), libc6 (>= 2.14), libcairo2 (>= 1.10.0), libcanberra-gtk3-0 (>= 0.25), libcanberra0 (>= 0.2), libclutter-1.0-0 (>= 1.15.90), libcogl-pango20 (>= 1.17.4), libcogl20 (>= 1.17.4), libcroco3 (>= 0.6.2), libdbus-glib-1-2 (>= 0.78), libecal-1.2-16 (>= 3.5.91), libedataserver-1.2-18 (>= 3.5.91), libgcr-base-3-1 (>= 3.8.0), libgdk-pixbuf2.0-0 (>= 2.22.0), libgirepository-1.0-1 (>= 0.9.2), libgjs0-libmozjs-24-0, libgjs0e (>= 1.42.0), libglib2.0-0 (>= 2.39.90), libgstreamer1.0-0 (>= 1.4.0), libgtk-3-0 (>= 3.13.2), libical1a (>= 1.0), libjson-glib-1.0-0 (>= 0.13.2), libmozjs-24-0, libmutter0e, libnm-glib4 (>= 0.8.998), libnm-util2 (>= 0.8.998), libpango-1.0-0 (>= 1.14.0), libpangocairo-1.0-0 (>= 1.14.0), libpolkit-agent-1-0 (>= 0.99), libpolkit-gobject-1-0 (>= 0.94), libpulse-mainloop-glib0 (>= 0.99.1), libpulse0 (>= 0.99.1), libsecret-1-0 (>= 0.7), libstartup-notification0 (>= 0.11), libsystemd0, libtelepathy-glib0 (>= 0.17.5), libx11-6, libxfixes3, evolution-data-server (>= 3.7.90), gir1.2-gdm-1.0 (>= 3.5.90), gir1.2-accountsservice-1.0, gir1.2-atspi-2.0 (>= 2.9.91), gir1.2-caribou-1.0 (>= 0.4.8), gir1.2-freedesktop, gir1.2-gdesktopenums-3.0 (>= 3.12), gir1.2-gcr-3 (>= 3.7.5), gir1.2-gkbd-3.0, gir1.2-gnomebluetooth-1.0 (>= 3.6.0), gir1.2-gnomedesktop-3.0 (>= 3.12.0), gir1.2-ibus-1.0 (>= 1.5.2), gir1.2-nmgtk-1.0 (>= 0.9.8), gir1.2-pango-1.0, gir1.2-polkit-1.0, gir1.2-telepathylogger-0.2 (>= 0.8.0), gir1.2-upowerglib-1.0 (>= 0.99), gjs (>= 1.39.0), gnome-session, gnome-settings-daemon (>= 3.4.0), gnome-shell-common (= 3.14.4-0ubuntu1), gnome-themes-standard, gnome-backgrounds (>= 3.13.90), gsettings-desktop-schemas (>= 3.11), mutter (>= 3.14.4), python (>= 2.6), telepathy-mission-control-5
Recommends: gkbd-capplet, gnome-contacts, gnome-control-center, gnome-user-guide, network-manager, unzip, gdm (>= 3.5.90)
Conflicts: gnome-screensaver (<< 3.6)
Breaks: fglrx-driver (<< 1:11-10), gdm (<< 3.5.90), gnome-control-center (<< 1:3.0), gnome-session (<< 3.0), gnome-tweak-tool (<< 3.5)
Filename: pool/universe/g/gnome-shell/gnome-shell_3.14.4-0ubuntu1_amd64.deb
Size: 614648
MD5sum: 0c79bf200f9abf38534dc0696e6bdc46
SHA1: 577d5629de13c817a286a436f987e695e9fdb299
SHA256: 383eb95149b02145b0f5410c7f138c6cbda6e2dbd50b5c64db7a2d75c3001c05
Description-en: graphical shell for the GNOME desktop
 The GNOME Shell provides core interface functions like switching
 windows, launching applications or see your notifications. It takes
 advantage of the capabilities of modern graphics hardware and
 introduces innovative user interface concepts to provide a
 delightful and easy to use experience. GNOME Shell is the defining
 technology of the GNOME 3 user experience.
Description-md5: 51a5a94e6b632e350489b7b8d27ab9fc
Homepage: http://live.gnome.org/GnomeShell
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Task: ubuntu-gnome-desktop

``````
:~$ dpkg -l|grep wayland
ii  gnome-session-wayland                                 3.14.0-3ubuntu2                                    amd64        GNOME Session Manager - GNOME 3 session
ii  libwayland-client0:amd64                              1.7.1+git201506050212.56a5a89-1626~ubuntu15.04.1   amd64        wayland compositor infrastructure - client library
ii  libwayland-cursor0:amd64                              1.7.1+git201506050212.56a5a89-1626~ubuntu15.04.1   amd64        wayland compositor infrastructure - cursor library
ii  libwayland-egl1-mesa:amd64                            10.6.0~git20150528+10.6.ffd133bd-0ubuntu0ricotz    amd64        implementation of the Wayland EGL platform -- runtime
ii  libwayland-server0:amd64                              1.7.1+git201506050212.56a5a89-1626~ubuntu15.04.1   amd64        wayland compositor infrastructure - server library
ii  weston                                                1.7.0+git201506060502.97b9b17-4309~ubuntu15.04.1   amd64        reference implementation of a wayland compositor
ii  xwayland                                              2:1.17.1-0ubuntu4                                  amd64        Xwayland X server
```

---

### Post by harry332 on 2015-06-08
> **juha-rautiala said:**
> Gnome-Weather breaks down :(

This and gjs (1.43.3) are in proposed now, should fix it.

gnome-weather (3.16.2.1-0ubuntu2) wily; urgency=medium

  * Bump gjs dependency to >= 1.43.3, as gnome-weather won't start without
    that version of gjs (or greater) (LP: [#1462834]("https://launchpad.net/bugs/1462834")).

---

### Post by grahammechanical on 2015-06-24
Email date: Friday June 19th

> - Updated GNOME packages to 3.16

[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-June/004669.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-June/004669.html)

---

### Post by BigCityCat on 2015-06-24
It is working well but the file roller does not work properly. There is no way to execute an action after it opens. This happens when trying to use it for uploading a user picture, extracting files and choosing a folder to import in my music application. Where do you guys suggest I file a bug report? I am using a few programs from elementary os but this does this in nautilus as well when I try to extract a file.

[http://i276.photobucket.com/albums/kk14/bigcitycat/Screenshot%20from%202015-06-24%2019-10-31_zpsmietvjjr.png](http://i276.photobucket.com/albums/kk14/bigcitycat/Screenshot%20from%202015-06-24%2019-10-31_zpsmietvjjr.png)

---

