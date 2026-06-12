---
title: "request XFE 0.84"
date: 2005-07-07
forum: Ubuntu Backports
---

### Post by dlpfmVfH on 2005-07-07
can you please backport XFE 0.84
[http://roland65.free.fr/xfe/index.php?page=download](http://roland65.free.fr/xfe/index.php?page=download)

Xfe 0.84 requires the FOX 1.4.x library and neither works with FOX 1.0.x, nor FOX 1.2.x, nor FOX 1.5.x!

don't know if it is in breezy but I would sure like it backported...
compared to rox this file-manager is easier, smaller and faster

---

### Post by Darrena on 2005-07-07
That looks interesting, there is a debian package posted on their site so I may try that...

---

### Post by dlpfmVfH on 2005-07-07
the debian package didn't install with my setup...

---

### Post by dlpfmVfH on 2005-07-07
xfe 7.2-6 is in breezy...maybe that one can be backported...it has the following deps:

[list]
[*][libc6]("http://packages.ubuntu.com/breezy/base/libc6") (>= 2.3.4-1)GNU C Library: Shared libraries and Timezone data
[*][img]http://packages.ubuntu.com/Pics/dep.gif[/img]  libfox1.2Package not available
[*][img]http://packages.ubuntu.com/Pics/dep.gif[/img]  [libgcc1]("http://packages.ubuntu.com/breezy/libs/libgcc1") (>= 1:4.0-0pre6ubuntu4)GCC support library
[*][img]http://packages.ubuntu.com/Pics/dep.gif[/img]  [libpng12-0]("http://packages.ubuntu.com/breezy/libs/libpng12-0") (>= 1.2.8rel)PNG library - runtime
[*][img]http://packages.ubuntu.com/Pics/dep.gif[/img]  [libstdc++5]("http://packages.ubuntu.com/breezy/base/libstdc++5") (>= 1:3.3.4-1)The GNU Standard C++ Library v3 
[/list]

---

### Post by ubuntu_demon on 2005-07-08
[QUOTE=aboe]xfe 7.2-6 is in breezy...maybe that one can be backported...it has the following deps:

[list]
[*][libc6]("http://packages.ubuntu.com/breezy/base/libc6") (>= 2.3.4-1)GNU C Library: Shared libraries and Timezone data
[*][img]http://packages.ubuntu.com/Pics/dep.gif[/img]  libfox1.2Package not available
[*][img]http://packages.ubuntu.com/Pics/dep.gif[/img]  [libgcc1]("http://packages.ubuntu.com/breezy/libs/libgcc1") (>= 1:4.0-0pre6ubuntu4)GCC support library
[*][img]http://packages.ubuntu.com/Pics/dep.gif[/img]  [libpng12-0]("http://packages.ubuntu.com/breezy/libs/libpng12-0") (>= 1.2.8rel)PNG library - runtime
[*][img]http://packages.ubuntu.com/Pics/dep.gif[/img]  [libstdc++5]("http://packages.ubuntu.com/breezy/base/libstdc++5") (>= 1:3.3.4-1)The GNU Standard C++ Library v3 
[/list][/QUOTE]
 hoary has libc6 version : 2.3.2.ds1-20ubuntu13
So backporting from breezy is not an option (unless hacking a bit works :-P)

Also what about rox-filer ? That's a lightweigh filemanager too.

---

### Post by jdong on 2005-07-08
XFE probably does build for Hoary. I'll try that backport now.

Note that some dependencies (like libc and other libraries) are generated at build-time, depending on the build system's libraries.

---

### Post by jdong on 2005-07-08
CORRECTION:

libfox1.2-dev is not available in Hoary... So no, it won't build

---

### Post by ubuntu_demon on 2005-07-08
[QUOTE=jdong]
Note that some dependencies (like libc and other libraries) are generated at build-time, depending on the build system's libraries.[/QUOTE]
 I didn't know that. Why can't they make the ubuntu package database more precise then ?(just curious)

---

### Post by dlpfmVfH on 2005-07-09
libfox 1.2 comes from the foxtoolkit...
but thanks for trying...

I liked xfe better than rox...cause it is easier to work with.
it is more consistent with the interface.

---

### Post by dlpfmVfH on 2005-07-09
[libfox1.2-dev]("http://packages.ubuntu.com/breezy/libdevel/libfox1.2-dev") (1.2.13-1.1ubuntu1) [universe]Development files for the FOX C++ GUI Toolkit : is in breezy  [http://packages.ubuntu.com/breezy/allpackages](http://packages.ubuntu.com/breezy/allpackages)

so can you please try again....building it with hoary deps...please

---

### Post by rwabel on 2005-07-09
I would also like to test the new version for xfe. if you can backport, it would be cool! thanks

---

### Post by dlpfmVfH on 2005-07-12
I build the xfe7.2 breezy version with the ubp-build-script..:
just added the breezy sources...to my apt-sourceslist

and first build the libfox1.2dev package..
and then the xfe7.2 package...

they installed fine...and I have working XFE 7.2 on my system build with for hoary

---

### Post by Dax0r on 2005-07-16
[QUOTE=aboe]I liked xfe better than rox...cause it is easier to work with.
it is more consistent with the interface.[/QUOTE]

Xfe looks like windows explorer...I dont like it.
I prefer evidence [http://evidence.sourceforge.net/features.html](http://evidence.sourceforge.net/features.html)

---

### Post by rwabel on 2005-07-16
[QUOTE=Dax0r]Xfe looks like windows explorer...I dont like it.
I prefer evidence [http://evidence.sourceforge.net/features.html](http://evidence.sourceforge.net/features.html)[/QUOTE]
 xfe has 2 panels! that's the main reason. Every one that has 1 panel like "nautilus, konqueror, evidence etc are more looking like explorer. I don't understand why they don't implement the 2 panel thing. It's the most effective way to work with file.

---

