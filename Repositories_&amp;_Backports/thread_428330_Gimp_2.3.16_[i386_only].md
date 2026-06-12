---
title: "Gimp 2.3.16 [i386 only]"
date: 2007-04-30
forum: Repositories &amp; Backports
---

### Post by zgornel on 2007-04-30
Made a package of The Gimp 2.3.16, use the wrapper script instructions [here]("http://gimp.org/release-notes/gimp-2.3.html") after installing it (the installation directory is /opt/gimp-2.3.16)
[[download gimp-2.3.16-i386.deb]]("http://files-upload.com/199504/gimp_2.3.16-1_i386.deb.html") (wait for the counter arrive to 0)

Configuration:
```
Building GIMP with prefix=/opt/gimp-2.3, datarootdir=${prefix}/share
Desktop files install into ${datarootdir}

Extra Binaries:
  gimp-console:        yes
  gimp-remote:         yes

Optional Features:
  D-Bus service:       no

Optional Plug-Ins:
  Ascii Art:           no (AA library not found)
  Help Browser:        yes
  LCMS:                yes
  JPEG:                yes
  MNG:                 yes
  PDF:                 yes
  PNG:                 yes
  Print:               yes
  PSP:                 yes
  Python:              yes
  Script-Fu:           yes
  SVG:                 yes
  TIFF:                yes
  TWAIN (MacOS X):     no
  TWAIN (Win32):       no
  URI:                 yes (using gnome-vfs)
  Windows ICO          yes
  WMF:                 yes
  XJT:                 yes
  XPM:                 yes

Plug-In Features:
  EXIF support:        yes
  GNOME UI:            yes
  GNOME keyring:       yes

Optional Modules:
  ALSA (MIDI Input):   yes
  Linux Input:         yes (HAL support: no)
  DirectInput (Win32): no
  Color Correction:    yes
  Soft Proof:          yes

```

---

### Post by girishv on 2007-04-30
Sorry the link not working, says, they are upgrading the service

thanks

Girish

---

### Post by xyz on 2007-04-30
Site's back up and thank you for this.

---

### Post by zgornel on 2007-04-30
> **xyz said:**
> Site's back up and thank you for this.

No problem, just report any errors if any and report the bugs to the gimp development team.  ;)

---

### Post by disturbedite on 2007-04-30
the download is really slow, but thanks for the upload!
UPDATE:
i'm on kubuntu gutsy and i'm getting an error while trying to install it.  its a conflict with the gcc package.  its trying to overwrite a file within  that gcc package...

---

### Post by zgornel on 2007-04-30
Try forcing the installation. If you are not sure, try checking the versions of the file. Gutsy is pretty small now, maybe it is the same version of the file. :D Theoretically, it should not create any problems. If it does, you uninstall gimp and reinstall gcc.

---

### Post by disturbedite on 2007-04-30
yeah, i planned on doing that, but i hadn't got around to it yet.  the file that it couldn't overwrite was /usr/lib/gcc/i486-linux-gnu/4.1.2/crtbeginS.o.  so i thought i'd just rename it and try to reinstall this (gimp) package but it turns out that file doesn't exist!  it looks like a typo, but the only file close to that filename is crtbegin5.o...

well i updated to gcc 4.2 since feisty (& gutsy since i upgraded to it) only ship with gcc 4.1.2, but that didn't help...  (i figured it wouldn't, but i thought it wouldn't hurt to try, and it didn't).

---

### Post by ruimoura on 2007-05-02
working fine. Thank you.

Ps: how did you do it? With checkinstall?

---

### Post by zgornel on 2007-05-03
> **ruimoura said:**
> working fine. Thank you.

Ps: how did you do it? With checkinstall?
yes. the strange thing was that normally it would not work because it said that it could not find the installation directories. I had to install it with make install and then create the package with checkinstall.

---

### Post by hikaricore on 2007-05-28
Thanks for the package :)  I'll be trying this out soon.  Hopefully some of my issues with 2.3.13 are resolved in this build. lol

---

