---
title: "Why VLC is not installed in worldwide distributions initially"
date: 2024-05-29
forum: The Cafe
---

### Post by lapispodozritelen2024 on 2024-05-29
Good afternoon/evening/morning/night!


My teacher asked me such an interesting question “why VLC player is not installed in the world distributions right out of the box, for example in the same Ubuntu, but it is in the repositories?”.


I tried to find the answer to this question for three days in all the languages I can read myself and Yandex can translate, I could not find anything clear....


I again came to the teacher and he told me that it is, let's say, related to some “politics”, it did not get better and I came here in search of help....


Maybe someone knows...

---

### Post by currentshaft on 2024-05-29
127

---

### Post by grahammechanical on 2024-05-30
There is another form of politics going on here. Ubuntu uses the Gnome 3 desktop environment and the Gnome 3 shell user interface. Ubuntu also default installs many Gnome applications. These Gnome applications include a music player (Rhythmbox) and a video player (Videos). So, it could be reasoned that Ubuntu already has a more or less complete set of applications for the ordinary user. I guess it is convenient to have one organisation responsible for maintaining these applications.

I also note that an install of Ubuntu 24.04 LTS with the Extended Selection option chosen does not install any Gnome games. This is a change.  It should also be noted that VLC in Ubuntu Software is a snap packaged application. Replacing Rhythmbox and Videos with a snap packaged VLC application might upset a lot of long time users of Ubuntu. New users would not know any difference.

Regards

---

### Post by ian-weisser on 2024-05-30
It also raises the more basic question: "Which applications should (or should not) be included with the install media?"

You cannot install everything, as it would make the install .iso slow to download, require an unnecessarily large USB drive, etc.
For every person who wants their favorite application, there's another person who considers it bloat.

Balancing the two opposite requirements (full-featured vs avoiding bloat) is also politics.

---

### Post by VMC on 2024-05-30
```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  fonts-freefont-ttf libaribb24-0t64 libcddb2 libdc1394-25 libdca0
  libdouble-conversion3 libdvbpsi10 libdvdnav4 libebml5 libfaad2 libixml11t64
  libkate1 liblirc-client0t64 liblua5.2-0 libmad0 libmatroska7 libmd4c0
  libmpcdec6 libopenmpt-modplug1 libpcre2-16-0 libprotobuf-lite32t64
  libproxy-tools libqt5core5t64 libqt5dbus5t64 libqt5gui5t64 libqt5network5t64
  libqt5qml5 libqt5qmlmodels5 libqt5quick5 libqt5svg5 libqt5waylandclient5
  libqt5waylandcompositor5 libqt5widgets5t64 libqt5x11extras5
  libresid-builder0c2a libsidplay2 libspatialaudio0t64 libssh2-1t64
  libupnp17t64 libvlc-bin libvlc5 libvlccore9 libvncclient1 libxcb-composite0
  libxcb-xinerama0 libxcb-xinput0 qt5-gtk-platformtheme qttranslations5-l10n
  qtwayland5 vlc-bin vlc-data vlc-l10n vlc-plugin-access-extra vlc-plugin-base
  vlc-plugin-notify vlc-plugin-qt vlc-plugin-samba vlc-plugin-skins2
  vlc-plugin-video-output vlc-plugin-video-splitter vlc-plugin-visualization
Suggested packages:
  libdvdcss2 lirc qgnomeplatform-qt5 qt5-image-formats-plugins
  qt5-qmltooling-plugins vlc-plugin-fluidsynth vlc-plugin-jack
  vlc-plugin-pipewire vlc-plugin-svg
The following NEW packages will be installed:
  fonts-freefont-ttf libaribb24-0t64 libcddb2 libdc1394-25 libdca0
  libdouble-conversion3 libdvbpsi10 libdvdnav4 libebml5 libfaad2 libixml11t64
  libkate1 liblirc-client0t64 liblua5.2-0 libmad0 libmatroska7 libmd4c0
  libmpcdec6 libopenmpt-modplug1 libpcre2-16-0 libprotobuf-lite32t64
  libproxy-tools libqt5core5t64 libqt5dbus5t64 libqt5gui5t64 libqt5network5t64
  libqt5qml5 libqt5qmlmodels5 libqt5quick5 libqt5svg5 libqt5waylandclient5
  libqt5waylandcompositor5 libqt5widgets5t64 libqt5x11extras5
  libresid-builder0c2a libsidplay2 libspatialaudio0t64 libssh2-1t64
  libupnp17t64 libvlc-bin libvlc5 libvlccore9 libvncclient1 libxcb-composite0
  libxcb-xinerama0 libxcb-xinput0 qt5-gtk-platformtheme qttranslations5-l10n
  qtwayland5 vlc vlc-bin vlc-data vlc-l10n vlc-plugin-access-extra
  vlc-plugin-base vlc-plugin-notify vlc-plugin-qt vlc-plugin-samba
  vlc-plugin-skins2 vlc-plugin-video-output vlc-plugin-video-splitter
  vlc-plugin-visualization
0 upgraded, 62 newly installed, 0 to remove and 2 not upgraded.
Need to get 36.3 MB of archives.
After this operation, 151 MB of additional disk space will be used.
Do you want to continue? [Y/n]
``` **Snap** is not listed here using my install of **VLC**

---

### Post by guiverc on 2024-05-31
> **lapispodozritelen2024 said:**
> 
My teacher asked me such an interesting question &#8220;why VLC player is not installed in the world distributions right out of the box, for example in the same Ubuntu, but it is in the repositories?&#8221;.


Lubuntu comes *out of the box* with it installed.  It's the default music/movie player.

You can view what is included on the Lubuntu 24.04 LTS *manifest* file, and then search for what is found on the ISO.. though not all packages on the ISO will be installed (eg. if you select a *minimal* install), let alone the installer itself not being written to the installed system.

[https://cdimage.ubuntu.com/lubuntu/releases/24.04/release/lubuntu-24.04-desktop-amd64.manifest](https://cdimage.ubuntu.com/lubuntu/releases/24.04/release/lubuntu-24.04-desktop-amd64.manifest)

VLC packages included on 24.04 are

```

libvlc-bin:amd64    3.0.20-3build6
libvlc5:amd64    3.0.20-3build6
libvlccore9:amd64    3.0.20-3build6
libvncclient1:amd64    0.9.14+dfsg-1build2

phonon-backend-vlc-common    0.12.0-3build3
phonon4qt5-backend-vlc:amd64    0.12.0-3build3vlc    3.0.20-3build6

vlc-bin    3.0.20-3build6
vlc-data    3.0.20-3build6
vlc-l10n    3.0.20-3build6
vlc-plugin-access-extra:amd64    3.0.20-3build6
vlc-plugin-base:amd64    3.0.20-3build6
vlc-plugin-notify:amd64    3.0.20-3build6
vlc-plugin-qt:amd64    3.0.20-3build6
vlc-plugin-samba:amd64    3.0.20-3build6
vlc-plugin-skins2:amd64    3.0.20-3build6
vlc-plugin-svg:amd64    3.0.20-3build6
vlc-plugin-video-output:amd64    3.0.20-3build6
vlc-plugin-video-splitter:amd64    3.0.20-3build6
vlc-plugin-visualization:amd64    3.0.20-3build6

```

Do note, that VLC being a Qt5 application, makes sense on Lubuntu (using LXQt or Qt5), far more than it does on many of the GTK based GNU/Linux distributions (eg. Ubuntu Desktop with GNOME (GTK4))

To have an efficient system, you want the desktop & applications running to *share* resources... Lubuntu aims to be a *fast* and light system.  To be *light* everything needs to *share* resources, thus applications that will be *light* must use Qt5 libraries/toolkit as that is what our desktop (LXQt) uses.

If you are running a Qt5 desktop, and use a GTK3 app for example, you'll need Qt5 libraries to be in RAM so your desktop can run, plus GTK3 *libs* so the app can work, even if those *libs* do exactly the same thing (*just slightly differently*). it's wasting RAM for little benefit. VLC as an app both works, as is efficient on the LXQt/Lubuntu desktop; thus we (Lubuntu) include it.

---

### Post by 909mjolnir on 2024-06-01
I don't mind Parole and similar.  VLC is powerful, but has way too many settings.  
But it is no simple matter about which items are included in Linuxes.  
I wish wine was included by default.

---

