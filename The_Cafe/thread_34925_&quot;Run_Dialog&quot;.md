---
title: "&quot;Run Dialog&quot;"
date: 2005-05-16
forum: The Cafe
---

### Post by kvidell on 2005-05-16
I'm using Openbox now and would like some sort of "run dialog" (similar to the "Run Application" thinger in Gnome/Metaicty... actually... I wouldn't mind using that one.)
I can't find one... or the one in Gnome. Apparently that's part of the panel/metacity? :-\
I dumped ps aux in to foo with it open and bar without it running and diff'd the files and didn't see it.
I'd do apt-cache search run | less but that just sounds like trouble.

Any ideas?
Thanks,
- Kev

---

### Post by kvidell on 2005-05-16
I found one!
That was too much effort for such a small app, but here ya go, for anyone else who's curious:
```
Package: gmrun
Priority: optional
Section: universe/x11
Installed-Size: 188
Maintainer: David B Harris <david@eelf.ddts.net>
Architecture: i386
Version: 0.9.1-1
Depends: libatk1.0-0 (>= 1.6.0), libc6 (>= 2.3.2.ds1-4), libgcc1 (>= 1:3.3.4-1), libglib2.0-0 (>= 2.4.1), libgtk2.0-0 (>= 2.4.4), libpango1.0-0 (>= 1.5.2), libstdc++5 (>= 1:3.3.4-1)
Filename: pool/universe/g/gmrun/gmrun_0.9.1-1_i386.deb
Size: 49498
MD5sum: 6cbbec4a13a58175a0decb6abf309aad
Description: Featureful CLI-like GTK+ application launcher
 This is gmrun; a small fast, yet featureful application launcher for use
 under X11, which uses GTK+ widget toolkit. Some features include tab-
 completion of file names and programs, history, easy x-terminal-emulator
 launching, and URL handling.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
```
Enjoy!
- Kev

---

### Post by grizzly on 2006-11-03
Hey gmrun is nice. 
BUT! it closes after launching an app. So it hs to be starte everytime, and the problem with that is that it takes 2 seconds too longer to start it.
Possible to minize it? or anything else that wouldn't close?

---

### Post by jpeddicord on 2006-11-03
Did you try Alt+F2? That is the Run dialog similar to the one in KDE and Windows.

Jacob

---

### Post by grizzly on 2006-11-04
The kde dialog box is 'bound' to kdesktop, which I don't run/require.

---

### Post by xyz on 2006-11-04
To read more about it, in a terminal:
```
man dialog
```
> DESCRIPTION
       Dialog is a program that will let you to present a variety of questions
       or display messages using dialog boxes  from  a  shell  script.   These
       types  of  dialog boxes are implemented (though not all are necessarily
       compiled into dialog):


---

### Post by 23meg on 2006-11-04
> **grizzly said:**
> Hey gmrun is nice. 
BUT! it closes after launching an app. So it hs to be starte everytime, and the problem with that is that it takes 2 seconds too longer to start it.
Possible to minize it? or anything else that wouldn't close?
Maybe running it from a RAM disk?

---

