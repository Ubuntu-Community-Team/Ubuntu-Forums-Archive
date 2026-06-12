---
title: "Kernel 3.8.0.9.23 and multiarch"
date: 2013-03-01
forum: Ubuntu Development Version
---

### Post by Budovi on 2013-03-01
Hi all,

today (in fact since yesterday I think) I'm facing another "partial upgrade" caused by virtualgl-libs:i386 recommended by bumblebee. I have raring-proposed and ppa:bumblebee/testing as additional sources. I think this will clear situation faster than my words :D :

```
~$ sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libx11-6 libx11-xcb1 linux-generic linux-headers-generic linux-image-generic
The following packages will be upgraded:
  appmenu-gtk appmenu-gtk3 apport apport-gtk compiz compiz-core compiz-gnome
  compiz-plugins-default gnome-desktop3-data indicator-printers
  language-selector-common language-selector-gnome libcompizconfig0
  libdecoration0 libgnome-desktop-3-4 libido3-0.1-0 libpulse-mainloop-glib0
  libpulse0 libpulsedsp libpurple-bin libunity-core-6.0-5 pulseaudio
  pulseaudio-module-bluetooth pulseaudio-module-x11 pulseaudio-utils
  python3-apport python3-problem-report telepathy-indicator unity unity-common
  unity-services
31 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Need to get 6 702 kB of archives.
After this operation, 8 192 B disk space will be freed.
Do you want to continue [Y/n]?
```

```
~$ sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  libgl1-mesa-glx:i386 libx11-6:i386 libx11-xcb1:i386 libxdamage1:i386
  libxext6:i386 libxfixes3:i386 libxv1:i386 libxxf86vm1:i386
  virtualgl-libs:i386 virtualgl-libs-ia32:i386
The following NEW packages will be installed:
  linux-headers-3.8.0-9 linux-headers-3.8.0-9-generic
  linux-image-3.8.0-9-generic linux-image-extra-3.8.0-9-generic
The following packages will be upgraded:
  appmenu-gtk appmenu-gtk3 apport apport-gtk compiz compiz-core compiz-gnome
  compiz-plugins-default gnome-desktop3-data indicator-printers
  language-selector-common language-selector-gnome libcompizconfig0
  libdecoration0 libgnome-desktop-3-4 libido3-0.1-0 libpulse-mainloop-glib0
  libpulse0 libpulsedsp libpurple-bin libunity-core-6.0-5 libx11-6 libx11-xcb1
  linux-generic linux-headers-generic linux-image-generic pulseaudio
  pulseaudio-module-bluetooth pulseaudio-module-x11 pulseaudio-utils
  python3-apport python3-problem-report telepathy-indicator unity unity-common
  unity-services
36 upgraded, 4 newly installed, 10 to remove and 0 not upgraded.
Need to get 64,0 MB of archives.
After this operation, 232 MB of additional disk space will be used.
Do you want to continue [Y/n]?
```

```
~$ aptitude why virtualgl-libs-ia32:i386
i   bumblebee                Recommends virtualgl-libs-ia32
i A virtualgl-libs-ia32:i386 Provides   virtualgl-libs-ia32
```

```
~$ apt-cache depends virtualgl-libs-ia32:i386
virtualgl-libs-ia32:i386
  Depends: virtualgl-libs:i386
```

```
~$ apt-cache depends virtualgl-libs:i386
virtualgl-libs:i386
  Depends: libc6:i386
 |Depends: libgl1-mesa-glx:i386
  Depends: <libgl1:i386>
    libgl1-mesa-glx:i386
  Depends: libx11-6:i386
  Depends: libxext6:i386
  Depends: libxv1:i386
  Depends: libturbojpeg:i386
  PreDepends: multiarch-support:i386
    multiarch-support
  Replaces: virtualgl-libs
  Breaks: virtualgl-libs
```

Obviously, there is some deep hidden conflict with that. Anyways, I do not really need virtualgl-libs:i386 at all (or I did not find out that :P ).

Question is, are there any known changes in providing multiarch-support for virtualgl, or this situation is caused by different incompatible package versions?

Thanks.

---

### Post by alphacrucis2 on 2013-03-01
Similar issue at the moment with skype and google-earth which depend on i386 packages. It's been like that for two or three days.

---

### Post by Budovi on 2013-03-01
Oh I got it, with synaptic package manager.

Of course it have nothing with kernel and software center, I upgraded that with synaptic without problems with dependencies.

Problem is with packages libx11-6 and libx11-xcb1, because their :i386 alternatives were not upgraded. And it is obviously impossible to have two different versions of same package (even if for i386 architecture).
Available version of libx11-6 and libx11-xcb1 is 2:1.5.0-1ubuntu1, for libx11-6:i386 and libx11-xcb1:i386 2:1.5.0-1. Which immediately caught my attention.

And I looked at changelog, and there is problem, because it is pretty short and only says "* Update symbols file for arm64 (LP: #1129389)" which means, this update probably did not change anything in functionality and there won't be update for :i386 version. This is in fact bug, and i386 version should get bump...

---

### Post by alphacrucis2 on 2013-03-03
Looks like the problem for me was mainly caused by having the raring proposed repo enabled. Apparently you aren't supposed to enable proposed for development releases. I downgraded all packages installed from proposed using synaptic and then disabled the proposed repo (including libx11-6 and libx11-xcb1). I still have a problem with a package installed from ricotz ppa that I am trying to figure out how to backout without borking my raring install.


Edit. Found the the ricotz package I mention above was actually from quantal xorg edgers ppa. I forgot I had that enabled when I updated from quantal to raring but some xorg-edgers quantal packages were actually newer than raring normal repos. To resolve the problem I enabled xorg edgers for raring, dist upgraded it and then ppa-purge to get back to a more standard raring install. I was then able to install ia32-libs and then skype and google-earth and they are both running fine.

---

### Post by Budovi on 2013-03-03
Yes, I agree, new packages are in proposed repository only. But it is "bug" anyway, of course I don't care now because I except that they will fix it in main repository...

I don't have problems with it, just did not install that packages. If some new dependency shows up, I can consider next move, including removing :i386 libraries (not too useful now) or removing raring-proposed from sources.

---

### Post by cariboo on 2013-03-03
Packages are put in the proposed repository, while awaiting dependencies to be built, once everything is done, they are released to the main repository.

---

