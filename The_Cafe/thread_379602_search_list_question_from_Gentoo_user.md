---
title: "search list question from Gentoo user"
date: 2007-03-08
forum: The Cafe
---

### Post by organicorange on 2007-03-08
Hi I'm not sure where to put this.... so I'll put it here?

Ok. I've been a long time Gentoo user and decided to try Ubuntu since everyone I know who has tried it, raves about it. Is there something similar to "emerge -s" in Ubuntu, or I guess I should say in Synaptic, that I can run from the command line? Is it something like apt-get cache or something? I know it isn't apt-get cache, but I mean something similar. I loved emerge and how robust it is. 

Thanks. I attempted a quick search but it yielded nothing, and don't yell at me to Google it!

---

### Post by Nikron on 2007-03-08
I assume emerge -s means search, so the it would be apt-cache search

---

### Post by organicorange on 2007-03-15
that's true, but I was hoping for something that gave me more of a description, say like if I had it installed (but I know that might be asking a bit much as there is no portage tree type of thing (that I am aware of) already installed on my system (also without using Synaptic, I am not to familiar with it and usually just use apt). I have used apt-cache, but I thought I heard someone mention something else, something a little more "robust." You know, it would do a quick search and maybe tell me what packages which might conflict or even what versions. I was hoping for something with more tags than only -s or -S. 

I don't know, maybe I'm a dreamer, but this is something I really miss (but I must say, for me the pros of do outweigh the cons!)

but, maybe I am wrong... and such a thing does not exist! :( If you know of anything more of what I am looking for, then that would be excellent!!!!

:)

---

### Post by tbroderick on 2007-03-15
> **organicorange said:**
> that's true, but I was hoping for something that gave me more of a description, say like if I had it installed (but I know that might be asking a bit much as there is no portage tree type of thing (that I am aware of) already installed on my system (also without using Synaptic, I am not to familiar with it and usually just use apt). I have used apt-cache, but I thought I heard someone mention something else, something a little more "robust." You know, it would do a quick search and maybe tell me what packages which might conflict or even what versions. I was hoping for something with more tags than only -s or -S. 

Try sudo aptitude show *packagename*. It will show you a detailed description, confilcts, depends, version #, replaces, provides, and much more, including if it's installed or not. Here is an example of sudo aptitude show konqeuror.
```

scratch@blackark:~$ sudo aptitude show konqueror
Package: konqueror
State: installed
Automatically installed: no
Version: 4:3.5.6-0ubuntu14
Priority: optional
Section: web
Maintainer: Jonathan Riddell <jriddell@ubuntu.com>
Uncompressed Size: 5460k
Depends: kdelibs4c2a (>= 4:3.5.5-1), libacl1 (>= 2.2.11-1), libart-2.0-2 (>=
         2.3.16), libattr1 (>= 2.4.4-1), libaudio2, libc6 (>= 2.5-0ubuntu1),
         libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.2), libgcc1 (>= 1:4.1.2),
         libice6 (>= 1:1.0.0), libidn11 (>= 0.5.18), libjpeg62, libkonq4 (>=
         4:3.5.5-1), libpng12-0 (>= 1.2.13-4), libqt3-mt (>= 3:3.3.8), libsm6,
         libstdc++6 (>= 4.1.2), libx11-6, libxcursor1 (> 1.1.2), libxext6, libxft2
         (> 2.1.1), libxi6, libxinerama1, libxrandr2 (>= 2:1.2.0), libxrender1,
         libxt6, zlib1g (>= 1:1.2.1), kcontrol (= 4:3.5.6-0ubuntu14),
         kdebase-kio-plugins (= 4:3.5.6-0ubuntu14), kdesktop (=
         4:3.5.6-0ubuntu14), kfind (= 4:3.5.6-0ubuntu14)
Suggests: khelpcenter, konq-plugins, ksvg, gij-4.1, libgcj7-awt, libjessie-java
Conflicts: kdebase-audiolibs (< 4:3.0.0), kdebase-libs (< 4:3.0.0)
Replaces: kdebase (< 4:3.0.0), kdebase-audiolibs (< 4:3.0.0), kdebase-doc (<
          4:3.0.0), kdebase-libs (< 4:3.0.0)
Provides: info-browser, man-browser, www-browser
Description: KDE's advanced file manager, web browser and document viewer
 Konqueror is the file manager for the K Desktop Environment. It supports basic
 file management on local UNIX filesystems, from simple cut/copy and paste
 operations to advanced remote and local network file browsing.

 It is also the canvas for all the latest KDE technology, from KIO slaves (which
 provide mechanisms for file access) to component embedding via the KParts object
 interface, and it is one of the most customizable applications available.

 Konqueror is an Open Source web browser with HTML4.0 compliance, supporting Java
 applets, JavaScript, CSS1 and (partially) CSS2, as well as Netscape plugins (for
 example, Flash or RealVideo plugins).

 It is a universal viewing application, capable of embedding read-only viewing
 components in itself to view documents without ever launching another
 application.

 This package is part of KDE, and a component of the KDE base module. See the
 'kde' and 'kdebase' packages for more information.

 Homepage: http://konqueror.kde.org

```

---

### Post by RAV TUX on 2007-03-15
> **organicorange said:**
> Hi I'm not sure where to put this.... so I'll put it here?

Ok. I've been a long time Gentoo user and decided to try Ubuntu since everyone I know who has tried it, raves about it. Is there something similar to "emerge -s" in Ubuntu, or I guess I should say in Synaptic, that I can run from the command line? Is it something like apt-get cache or something? I know it isn't apt-get cache, but I mean something similar. I loved emerge and how robust it is. 

Thanks. I attempted a quick search but it yielded nothing, and don't yell at me to Google it!

> **organicorange said:**
> that's true, but I was hoping for something that gave me more of a description, say like if I had it installed (but I know that might be asking a bit much as there is no portage tree type of thing (that I am aware of) already installed on my system (also without using Synaptic, I am not to familiar with it and usually just use apt). I have used apt-cache, but I thought I heard someone mention something else, something a little more "robust." You know, it would do a quick search and maybe tell me what packages which might conflict or even what versions. I was hoping for something with more tags than only -s or -S. 

I don't know, maybe I'm a dreamer, but this is something I really miss (but I must say, for me the pros of do outweigh the cons!)

but, maybe I am wrong... and such a thing does not exist! :( If you know of anything more of what I am looking for, then that would be excellent!!!!

:)

do you mean something like:
> 
emerge -va```
localhost ravtux # emerge -va konqueror

These are the packages that would be merged, in order:

Calculating dependencies... done!
[ebuild     U ] x11-libs/qt-3.3.8 [3.3.6-r5] USE="cups gif immqt-bc ipv6 opengl postgres xinerama -debug -doc -examples -firebird -immqt -mysql -nas -nis -odbc -sqlite (-pertty%)" 17,094 kB
[ebuild     U ] kde-base/kdelibs-3.5.6-r2 [3.5.5-r10] USE="acl alsa arts avahi cups jpeg2k kdeenablefinal kdehiddenvisibility kerberos openexr spell ssl tiff xinerama zeroconf -debug -doc -fam -legacyssl -lua -utempter% (-pertty%)" LINGUAS="he" 15,187 kB [1]
[ebuild     U ] kde-base/libkonq-3.5.6 [3.5.5] USE="arts kdeenablefinal kdehiddenvisibility xinerama -debug" 23,590 kB
[ebuild     U ] kde-base/kdebase-data-3.5.6 [3.5.5] USE="kdeenablefinal xinerama -debug (-arts%*) (-kdehiddenvisibility%*)" 0 kB
[ebuild     U ] kde-base/kdebase-kioslaves-3.5.6 [3.5.5-r1] USE="arts hal kdeenablefinal kdehiddenvisibility openexr samba xinerama -debug -ldap*" 21 kB
[ebuild     U ] kde-base/khotkeys-3.5.6 [3.5.5] USE="arts kdeenablefinal kdehiddenvisibility xinerama -debug" 0 kB
[ebuild     U ] kde-base/kdesu-3.5.6 [3.5.5] USE="arts kdeenablefinal kdehiddenvisibility xinerama -debug" 6 kB
[ebuild     U ] kde-base/khelpcenter-3.5.6 [3.5.5] USE="arts kdeenablefinal kdehiddenvisibility xinerama -debug" 0 kB
[ebuild     U ] kde-base/kcminit-3.5.6 [3.5.3] USE="arts kdeenablefinal kdehiddenvisibility xinerama -debug" 0 kB
[ebuild     U ] kde-base/kfind-3.5.6 [3.5.5] USE="arts kdeenablefinal kdehiddenvisibility xinerama -debug" 0 kB
[ebuild     U ] kde-base/kicker-3.5.6-r91 [3.5.5-r92] USE="arts kdeenablefinal xinerama -beagle% -debug -xcomposite" 0 kB [1]
[ebuild     U ] kde-base/kcontrol-3.5.6-r90 [3.5.5] USE="arts ieee1394 kdeenablefinal kdehiddenvisibility logitech-mouse opengl ssl xinerama -debug" 7 kB [1]
[ebuild     U ] kde-base/konqueror-3.5.6 [3.5.5] USE="arts java kdeenablefinal kdehiddenvisibility xinerama -debug" 0 kB

Total: 13 packages (13 upgrades), Size of downloads: 55,903 kB
Portage overlays:
 [1] /usr/portage/local/layman/sabayon

Would you like to merge these packages? [Yes/No]
```

---

### Post by organicorange on 2007-03-16
That "aptitude show packagename" is pretty cool! Thanks! But, is there a way where I could search the repositories through the console? Like when I do emerge -s, it searches the whole tree for me and also tells me everything in aptitude show package name. I guess what I am asking for is an "aptitude show package name + apt-cache search" function. Can I search the repository list without having to go to the ubuntu packages list via the web (or via using X11)?

My main thing is, maybe I don't want to startx and THEN an internet browser just to search for packages. I want to know if that option exists for me with ubuntu, where I can search, see if it is installed, and get a description (much like the show packagename, but one of those entries for each item that came up in the search). Oh and I don't want to navigate using lynx either.

the emerge -va thing is useful, but I am coming FROM Gentoo and am currently using Ubuntu -- but thanks for your input anyway.

If anyone knows of such a wonderful function, I'd be must grateful!!!

---

### Post by jpkotta on 2007-03-16
```
dpkg -l <glob>
``` where <glob> is a regular shell glob (e.g. ? = arbitrary character, * = arbitrary string) should be close to what you want.  You may want to put <glob> in single quotes.

Example:
```
dpkg -l emacs*
```

---

### Post by yabbadabbadont on 2007-03-16
> **organicorange said:**
> That "aptitude show packagename" is pretty cool! Thanks! But, is there a way where I could search the repositories through the console? Like when I do emerge -s, it searches the whole tree for me and also tells me everything in aptitude show package name. I guess what I am asking for is an "aptitude show package name + apt-cache search" function. Can I search the repository list without having to go to the ubuntu packages list via the web (or via using X11)?

My main thing is, maybe I don't want to startx and THEN an internet browser just to search for packages. I want to know if that option exists for me with ubuntu, where I can search, see if it is installed, and get a description (much like the show packagename, but one of those entries for each item that came up in the search). Oh and I don't want to navigate using lynx either.

the emerge -va thing is useful, but I am coming FROM Gentoo and am currently using Ubuntu -- but thanks for your input anyway.

If anyone knows of such a wonderful function, I'd be must grateful!!!
aptitude search <insert search pattern here>

---

### Post by RAV TUX on 2007-03-16
> **organicorange said:**
> That "aptitude show packagename" is pretty cool! Thanks! But, is there a way where I could search the repositories through the console? Like when I do emerge -s, it searches the whole tree for me and also tells me everything in aptitude show package name. I guess what I am asking for is an "aptitude show package name + apt-cache search" function. Can I search the repository list without having to go to the ubuntu packages list via the web (or via using X11)?

My main thing is, maybe I don't want to startx and THEN an internet browser just to search for packages. I want to know if that option exists for me with ubuntu, where I can search, see if it is installed, and get a description (much like the show packagename, but one of those entries for each item that came up in the search). Oh and I don't want to navigate using lynx either.

the emerge -va thing is useful, but I am coming FROM Gentoo and am currently using Ubuntu -- but thanks for your input anyway.

If anyone knows of such a wonderful function, I'd be must grateful!!!

here is an example of emerge -s

```
localhost-2 ravtux # emerge -s firefox

Searching...
[ Results for search key : firefox ]
[ Applications found : 2 ]

*  www-client/mozilla-firefox
      Latest version available: 2.0.0.2
      Latest version installed: 2.0.0.2
      Size of files: 42,834 kB
      Homepage:      http://www.mozilla.org/projects/firefox/
      Description:   Firefox Web Browser
      License:       MPL-1.1 GPL-2 LGPL-2.1

*  www-client/mozilla-firefox-bin
      Latest version available: 2.0.0.2
      Latest version installed: [ Not Installed ]
      Size of files: 15,960 kB
      Homepage:      http://www.mozilla.org/projects/firefox
      Description:   Firefox Web Browser
      License:       MPL-1.1 GPL-2 LGPL-2.1

```

here is a better example:

```
localhost-2 ravtux # emerge -s gimp

Searching...
[ Results for search key : gimp ]
[ Applications found : 7 ]

*  app-doc/gimp-help
      Latest version available: 0.11-r2
      Latest version installed: [ Not Installed ]
      Size of files: 50,838 kB
      Homepage:      http://docs.gimp.org/
      Description:   GNU Image Manipulation Program help files
      License:       FDL-1.2

*  app-doc/gimp-user-manual
      Latest version available: 2.0
      Latest version installed: [ Not Installed ]
      Size of files: 25,847 kB
      Homepage:      http://manual.gimp.org
      Description:   A user manual for GIMP
      License:       OPL

*  dev-perl/gimp-perl
      Latest version available: 2.2_pre1
      Latest version installed: [ Not Installed ]
      Size of files: 387 kB
      Homepage:      http://search.cpan.org/~sjburges/Gimp/
      Description:   Perl extension for writing Gimp Extensions/Plug-ins/Load & Save-Handlers
      License:       Artistic GPL-2

*  media-gfx/gimp
      Latest version available: 2.3.14
      Latest version installed: 2.3.14
      Size of files: 15,659 kB
      Homepage:      http://www.gimp.org/
      Description:   GNU Image Manipulation Program
      License:       GPL-2

*  media-gfx/gimp-freetype
      Latest version available: 0.6
      Latest version installed: [ Not Installed ]
      Size of files: 206 kB
      Homepage:      http://freetype.gimp.org/
      Description:   Freetype text plugin for The Gimp 2
      License:       GPL-2

*  media-gfx/gimp-print
      Latest version available: 4.2.7
      Latest version installed: 4.2.7
      Size of files: 5,056 kB
      Homepage:      http://gimp-print.sourceforge.net
      Description:   Gimp Print Drivers
      License:       GPL-2

*  sci-mathematics/gimps
      Latest version available: 24.14-r1
      Latest version installed: [ Not Installed ]
      Size of files: 864 kB
      Homepage:      http://mersenne.org/
      Description:   GIMPS - The Great Internet Mersenne Prime Search
      License:       as-is

```

---

### Post by mips on 2007-03-17
Uhm people, the OP does NOT want to know about emerge.

He is using Ubuntu and want to know about and apt/aptitude search feature.

He wants to have somthing like emerge -s but for Debia/Ubuntu via apt/aptitude.

---

### Post by joflow on 2007-03-17
isn't it apt-cache search package-name.  I don't remember exactly and can't test it as I no longer use ubuntu or any debian based distro

---

### Post by RAV TUX on 2007-03-17
> **mips said:**
> Uhm people, the OP does NOT want to know about emerge.

He is using Ubuntu and want to know about and apt/aptitude search feature.

He wants to have somthing like emerge -s but for Debia/Ubuntu via apt/aptitude.
Uhm Mips those post were to help Ubuntu users understand what the OP is talking about so they can help him. For those Ubuntu users who have not used Gentoo, clarification is always helpful.:)

---

### Post by scxtt on 2007-03-17
search for a package:
[INDENT]**(sudo) aptitude search *<package name>*** (if it has an "i" in the leftmost column, it's installed)[/INDENT]
more info on a package:
[indent]**(sudo) aptitude show *<package name>***[/indent]
"simulate" a package install:
[INDENT]**(sudo) aptitude -s install *<package name>***[/INDENT]

---

