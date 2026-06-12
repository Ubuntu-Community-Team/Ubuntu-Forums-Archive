---
title: "pixbuf trouble..."
date: 2012-12-13
forum: Ubuntu Development Version
---

### Post by zika on 2012-12-13
```
Unpacking replacement onboard ...

(gtk-update-icon-cache-3.0:12015): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory

This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being.

(gtk-update-icon-cache-3.0:12016): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory

This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being.
Processing triggers for man-db ...
Processing triggers for libglib2.0-0:amd64 ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for gconf2 ...
Processing triggers for hicolor-icon-theme ...

(gtk-update-icon-cache:13407): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory

This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being.

(gtk-update-icon-cache-3.0:13408): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory

This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being.
Setting up libgdk-pixbuf2.0-common (2.26.5-0ubuntu3) ...
Setting up libgdk-pixbuf2.0-0:amd64 (2.26.5-0ubuntu3) ...
Setting up libpango1.0-0:amd64 (1.30.1-1ubuntu1) ...
Setting up iproute (20121211-2) ...
Installing new version of config file /etc/iproute2/ematch_map ...
Setting up gir1.2-gdkpixbuf-2.0 (2.26.5-0ubuntu3) ...
Setting up gir1.2-pango-1.0 (1.30.1-1ubuntu1) ...
Setting up python3-virtkey (0.63.0-0ubuntu1) ...
Setting up onboard (0.99.0~alpha1~tr1190-0ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
                                         
Current status: 0 updates [-8].
:~$ gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
bash: /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache: Permission denied
:~$ sudo gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
bash: /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache: Permission denied
:~$
``````
:~$ cat /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
# GdkPixbuf Image Loader Modules file
# Automatically generated file, do not edit
# Created by gdk-pixbuf-query-loaders from gdk-pixbuf-2.26.5
#
"/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so"
"png" 5 "gdk-pixbuf" "The PNG image format" "LGPL"
"image/png" ""
"png" ""
"\211PNG\r\n\032\n" "" 100

"/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-ras.so"
"ras" 4 "gdk-pixbuf" "The Sun raster image format" "LGPL"
"image/x-cmu-raster" "image/x-sun-raster" ""
"ras" ""
"Y\246j\225" "" 100

"/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-qtif.so"
"qtif" 4 "gdk-pixbuf" "The QTIF image format" "LGPL"
"image/x-quicktime" "image/qtif" ""
"qtif" "qif" ""
"abcdidsc" "xxxx    " 100
"abcdidat" "xxxx    " 100

"/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-tiff.so"
"tiff" 5 "gdk-pixbuf" "The TIFF image format" "LGPL"
"image/tiff" ""
"tiff" "tif" ""
"MM *" "  z " 100
"II* " "   z" 100
"II* \020   CR\002 " "   z zzz   z" 0

"/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-wbmp.so"
"wbmp" 4 "gdk-pixbuf" "The WBMP image format" "LGPL"
"image/vnd.wap.wbmp" ""
"wbmp" ""
"  " "zz" 1
" `" "z " 1
" @" "z " 1
"  " "z " 1

"/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-pnm.so"
"pnm" 4 "gdk-pixbuf" "The PNM/PBM/PGM/PPM image format family" "LGPL"
"image/x-portable-anymap" "image/x-portable-bitmap" "image/x-portable-graymap" "image/x-portable-pixmap" ""
"pnm" "pbm" "pgm" "ppm" ""
"P1" "" 100
"P2" "" 100
"P3" "" 100
"P4" "" 100
"P5" "" 100
"P6" "" 100

"/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/io-wmf.so"
"wmf" 0 "gdk-pixbuf" "Windows Metafile" ""
"image/x-wmf" ""
"wmf" "apm" ""
"\327\315\306\232" "" 100
"\001" "" 100

"/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-ani.so"
"ani" 4 "gdk-pixbuf" "The ANI image format" "LGPL"
"application/x-navi-animation" ""
"ani" ""
"RIFF    ACON" "    xxxx    " 100

"/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-jpeg.so"
"jpeg" 5 "gdk-pixbuf" "The JPEG image format" "LGPL"
"image/jpeg" ""
"jpeg" "jpe" "jpg" ""
"\377\330" "" 100

"/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-tga.so"
"tga" 4 "gdk-pixbuf" "The Targa image format" "LGPL"
"image/x-tga" ""
"tga" "targa" ""
" \001\001" "x  " 100
" \001\t" "x  " 100
"  \002" "xz " 99
"  \003" "xz " 100
"  \n" "xz " 100
"  \v" "xz " 100

"/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-jasper.so"
"jpeg2000" 4 "gdk-pixbuf" "The JPEG 2000 image format" "LGPL"
"image/jp2" "image/jpeg2000" "image/jpx" ""
"jp2" "jpc" "jpx" "j2k" "jpf" ""
"    jP" "!!!!  " 100
"\377O\377Q" "" 100

"/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-gif.so"
"gif" 4 "gdk-pixbuf" "The GIF image format" "LGPL"
"image/gif" ""
"gif" ""
"GIF8" "" 100

"/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so"
"svg" 2 "gdk-pixbuf" "Scalable Vector Graphics" "LGPL"
"image/svg+xml" "image/svg" "image/svg-xml" "image/vnd.adobe.svg+xml" "text/xml-svg" "image/svg+xml-compressed" ""
"svg" "svgz" "svg.gz" ""
" <svg" "*    " 100
" <!DOCTYPE svg" "*             " 100

"/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-ico.so"
"ico" 5 "gdk-pixbuf" "The ICO image format" "LGPL"
"image/x-icon" "image/x-ico" "image/x-win-bitmap" ""
"ico" "cur" ""
"  \001   " "zz znz" 100
"  \002   " "zz znz" 100

"/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-icns.so"
"icns" 4 "gdk-pixbuf" "The ICNS image format" "GPL"
"image/x-icns" ""
"icns" ""
"icns" "" 100

"/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-xpm.so"
"xpm" 4 "gdk-pixbuf" "The XPM image format" "LGPL"
"image/x-xpixmap" ""
"xpm" ""
"/* XPM */" "" 100

"/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-pcx.so"
"pcx" 4 "gdk-pixbuf" "The PCX image format" "LGPL"
"image/x-pcx" ""
"pcx" ""
"\n \001" "" 100
"\n\002\001" "" 100
"\n\003\001" "" 100
"\n\004\001" "" 100
"\n\005\001" "" 100

"/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-xbm.so"
"xbm" 4 "gdk-pixbuf" "The XBM image format" "LGPL"
"image/x-xbitmap" ""
"xbm" ""
"#define " "" 100
"/*" "" 50

"/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-bmp.so"
"bmp" 5 "gdk-pixbuf" "The BMP image format" "LGPL"
"image/bmp" "image/x-bmp" "image/x-MS-bmp" ""
"bmp" ""
"BM" "" 100
``````
:~$ ls -alt /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
-rw-r--r-- 1 root root 4501 Dec 13 16:25 /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
```

But:
```
:~$ for z in /usr/share/icons/*; do sudo gtk-update-icon-cache-3.0 -f $z; done
gtk-update-icon-cache-3.0: No theme index file.
gtk-update-icon-cache-3.0: Cache file created successfully.
gtk-update-icon-cache-3.0: No theme index file.
gtk-update-icon-cache-3.0: Cache file created successfully.
gtk-update-icon-cache-3.0: Cache file created successfully.
gtk-update-icon-cache-3.0: No theme index file.
gtk-update-icon-cache-3.0: Cache file created successfully.
gtk-update-icon-cache-3.0: Cache file created successfully.
gtk-update-icon-cache-3.0: No theme index file.
gtk-update-icon-cache-3.0: Cache file created successfully.
gtk-update-icon-cache-3.0: No theme index file.
gtk-update-icon-cache-3.0: No theme index file.
gtk-update-icon-cache-3.0: Cache file created successfully.
gtk-update-icon-cache-3.0: Cache file created successfully.
gtk-update-icon-cache-3.0: Cache file created successfully.
gtk-update-icon-cache-3.0: Cache file created successfully.
gtk-update-icon-cache-3.0: No theme index file.
:~$ for z in /usr/share/icons/*; do sudo gtk-update-icon-cache-3.0 -ft $z; done
gtk-update-icon-cache-3.0: Failed to open file /usr/share/icons/dwm.png/.icon-theme.cache : Not a directory
gtk-update-icon-cache-3.0: Cache file created successfully.
gtk-update-icon-cache-3.0: Cache file created successfully.
gtk-update-icon-cache-3.0: Cache file created successfully.
gtk-update-icon-cache-3.0: Cache file created successfully.
gtk-update-icon-cache-3.0: Cache file created successfully.
gtk-update-icon-cache-3.0: Cache file created successfully.
gtk-update-icon-cache-3.0: Cache file created successfully.
gtk-update-icon-cache-3.0: Cache file created successfully.
gtk-update-icon-cache-3.0: Cache file created successfully.
gtk-update-icon-cache-3.0: Cache file created successfully.
gtk-update-icon-cache-3.0: Cache file created successfully.
:~$ for z in /usr/share/icons/*; do sudo gtk-update-icon-cache-3.0 -ftv $z; done
gtk-update-icon-cache-3.0: File not found: /usr/share/icons/default/icon-theme.cache
gtk-update-icon-cache-3.0: File not found: /usr/share/icons/DMZ-Black/icon-theme.cache
gtk-update-icon-cache-3.0: File not found: /usr/share/icons/DMZ-White/icon-theme.cache
gtk-update-icon-cache-3.0: File not found: /usr/share/icons/dwm.png/icon-theme.cache
gtk-update-icon-cache-3.0: File not found: /usr/share/icons/handhelds/icon-theme.cache
gtk-update-icon-cache-3.0: File not found: /usr/share/icons/HighContrastInverse/icon-theme.cache
gtk-update-icon-cache-3.0: File not found: /usr/share/icons/LowContrast/icon-theme.cache
gtk-update-icon-cache-3.0: File not found: /usr/share/icons/redglass/icon-theme.cache
gtk-update-icon-cache-3.0: File not found: /usr/share/icons/whiteglass/icon-theme.cache
:~$ for z in /usr/share/icons/*; do sudo gtk-update-icon-cache-3.0 -v $z; done
gtk-update-icon-cache-3.0: File not found: /usr/share/icons/default/icon-theme.cache
gtk-update-icon-cache-3.0: File not found: /usr/share/icons/DMZ-Black/icon-theme.cache
gtk-update-icon-cache-3.0: File not found: /usr/share/icons/DMZ-White/icon-theme.cache
gtk-update-icon-cache-3.0: File not found: /usr/share/icons/dwm.png/icon-theme.cache
gtk-update-icon-cache-3.0: File not found: /usr/share/icons/handhelds/icon-theme.cache
gtk-update-icon-cache-3.0: File not found: /usr/share/icons/HighContrastInverse/icon-theme.cache
gtk-update-icon-cache-3.0: File not found: /usr/share/icons/LowContrast/icon-theme.cache
gtk-update-icon-cache-3.0: File not found: /usr/share/icons/redglass/icon-theme.cache
gtk-update-icon-cache-3.0: File not found: /usr/share/icons/whiteglass/icon-theme.cache
:~$ locate icon-theme.cache
/usr/share/app-install/icon-theme.cache
/usr/share/icons/HighContrast/icon-theme.cache
/usr/share/icons/Humanity/icon-theme.cache
/usr/share/icons/Humanity-Dark/icon-theme.cache
/usr/share/icons/LoginIcons/icon-theme.cache
/usr/share/icons/gnome/icon-theme.cache
/usr/share/icons/hicolor/icon-theme.cache
/usr/share/icons/locolor/icon-theme.cache
/usr/share/icons/ubuntu-mono-dark/icon-theme.cache
/usr/share/icons/ubuntu-mono-light/icon-theme.cache
/usr/share/icons/unity-icon-theme/icon-theme.cache
/usr/share/icons/unity-webapps-applications/icon-theme.cache
:~$ ls -alt /usr/share/icons/ubuntu-mono-dark/i*
-rw-r--r-- 1 root root 143424 Dec 13 17:44 /usr/share/icons/ubuntu-mono-dark/icon-theme.cache
-rw-r--r-- 1 root root   2006 Dec 11 12:48 /usr/share/icons/ubuntu-mono-dark/index.theme
```everything looks like it's working like it should be...

---

### Post by ventrical on 2012-12-13
I have had that error msg  several time this release .. I think it is a f/p.

---

### Post by zika on 2013-02-28
Here we go again:
```
Processing triggers for hicolor-icon-theme ...

(gtk-update-icon-cache:23507): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory

This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being.

(gtk-update-icon-cache-3.0:23508): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory

This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being.
Processing triggers for libglib2.0-0:amd64 ...
Processing triggers for ureadahead ...
Processing triggers for gnome-icon-theme ...

(gtk-update-icon-cache-3.0:23786): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory

This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being.
```

---

### Post by zika on 2013-03-26
Again...

```
(gtk-update-icon-cache:4460): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory

This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being.


(gtk-update-icon-cache-3.0:4461): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory


This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being.
...
```
```
:~$ gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
bash: /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache: Permission denied
```
```
:~$ sudo gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
bash: /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache: Permission denied
```

Update&#8321;: Does this means that I've &#8222;solved&#8220; the problem?:
```
:~$ sudo apt-get install --reinstall  gtk2-engines-pixbufReading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 18.6 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ raring/universe gtk2-engines-pixbuf amd64 2.24.17-0ubuntu2 [18.6 kB]
Fetched 18.6 kB in 0s (129 kB/s)             
(Reading database ... 263863 files and directories currently installed.)
Preparing to replace gtk2-engines-pixbuf:amd64 2.24.17-0ubuntu2 (using .../gtk2-engines-pixbuf_2.24.17-0ubuntu2_amd64.deb) ...
Unpacking replacement gtk2-engines-pixbuf:amd64 ...
Setting up gtk2-engines-pixbuf:amd64 (2.24.17-0ubuntu2) ...
```

---

### Post by dino99 on 2013-03-26
got the latest package upgraded on i386, without issue

---

### Post by zika on 2013-03-26
> **dino99 said:**
> got the latest package upgraded on i386, without issue
I'm on amd_64...

---

### Post by dino99 on 2013-03-26
thats why i've commented on my side :P

---

### Post by ventrical on 2013-03-26
same here .. just now .. on 32bit

```

(gtk-update-icon-cache-3.0:3113): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory

This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being.

```

---

### Post by ventrical on 2013-03-26
same on 64bit..

```

(gtk-update-icon-cache-3.0:2866): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory

This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being.
Preparing to replace openssh-client 1:6.1p1-3 (using .../openssh-client_1%3a6.1p1-4_amd64.deb) ...
Unpacking replacement openssh-client ...
Preparing to replace gir1.2-gdkpixbuf-2.0 2.27.1-1ubuntu1 (using .../gir1.2-gdkpixbuf-2.0_2.28.0-0ubu

```

---

### Post by dino99 on 2013-03-26
You might need to clean your system.  You seem having still old package installed : pixbuf is at 2.28.x now, not 2.10.x

---

### Post by ventrical on 2013-03-26
> **dino99 said:**
> You might need to clean your system.  You seem having still old package installed : pixbuf is at 2.28.x now, not 2.10.x


It is a relatively a fresh install.   Only these:

```



The following packages will be REMOVED:
  libdb5.3 linux-headers-3.8.0-11 linux-headers-3.8.0-11-generic
  linux-headers-3.8.0-12 linux-headers-3.8.0-12-generic
  linux-image-3.8.0-11-generic linux-image-3.8.0-12-generic
  linux-image-extra-3.8.0-11-generic linux-image-extra-3.8.0-12-generic
0 upgraded, 0 newly installed, 9 to remove and 7 no


```

---

### Post by dino99 on 2013-03-26
Are you sharing a single /home with multiple distros/versions ?  With such cases, then a possible conflict with oldish settings inside .gnome2, .local, .config, .gconf

---

### Post by zika on 2013-03-26
> **dino99 said:**
> Are you sharing a single /home with multiple distros/versions ?  With such cases, then a possible conflict with oldish settings inside .gnome2, .local, .config, .gconfIf that question is addressed to me (as OP) the answer is "no", 13.04 is the only inhabitant of this whole machine... This install is originating from 12.10 being upgraded not more than couple of weeks from the very start of 13.04 testing... I think it (again) got resolved with my "install --reinstall" of packages that address that file... I'm not sure yet...
If ithat question is not addressed to me, disregard my answer given above...

---

### Post by ventrical on 2013-03-26
> **dino99 said:**
> Are you sharing a single /home with multiple distros/versions ?  With such cases, then a possible conflict with oldish settings inside .gnome2, .local, .config, .gconf

My 64bit install is a fresh install from USB .iso on a new partition on a 1/2m TB WD hdd with 4 other installs, 1 12.04, one 10.10,  and two Quantals upgraded from Oneric. So , no, I am not sharing single home as each install has it's own mountpoint.

---

### Post by ventrical on 2013-03-26
> **zika said:**
> If that question is addressed to me (as OP) the answer is "no", 13.04 is the only inhabitant of this whole machine... This install is originating from 12.10 being upgraded not more than couple of weeks from the very start of 13.04 testing... I think it (again) got resolved with my "install --reinstall" of packages that address that file... I'm not sure yet...
If ithat question is not addressed to me, disregard my answer given above...

 Oh .. I apologize for interfering on your space. Keep up the fine work.


Best Regards,

---

### Post by zika on 2013-03-26
> **ventrical said:**
> Oh .. I apologize for interfering on your space. Keep up the fine work.
Best Regards,You quote answer I gave to @dino99... I quoted his question and gave my answer, conditioned on the fact if it was addressed to me... I do not see how You found Yourself in that answer of mine let alone where I mentioned &#8222;my space&#8220; or any other space...

---

### Post by ventrical on 2013-03-26
> **zika said:**
> You quote answer I gave to @dino99... I quoted his question and gave my answer, conditioned on the fact if it was addressed to me... I do not see how You found Yourself in that answer of mine let alone where I mentioned „my space“ or any other space...



 I think I was in outer space there for a moment. :)

---

### Post by Harry33 on 2013-03-27
> **zika said:**
> Again...

...

Update&#8321;: Does this means that I've „solved“ the problem?:
```
:~$ sudo apt-get install --reinstall  gtk2-engines-pixbufReading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 18.6 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ raring/universe gtk2-engines-pixbuf amd64 2.24.17-0ubuntu2 [18.6 kB]
Fetched 18.6 kB in 0s (129 kB/s)             
(Reading database ... 263863 files and directories currently installed.)
Preparing to replace gtk2-engines-pixbuf:amd64 2.24.17-0ubuntu2 (using .../gtk2-engines-pixbuf_2.24.17-0ubuntu2_amd64.deb) ...
Unpacking replacement gtk2-engines-pixbuf:amd64 ...
Setting up gtk2-engines-pixbuf:amd64 (2.24.17-0ubuntu2) ...
```

The gdk-pixbuf installation issue is due to the source package "gdk-pixbuf", where the latest versin in RR is 2.28.0-ubuntu1
but not the source package "gtk+2.0", where the latest version in RR is 2.24.17-0ubuntu2.
Usually reinstallation of gdk-pixbuf helps (no more warnings).
However, I have't seen a case where such a warning would actually have produced any functional issues.

---

### Post by eddier on 2013-03-27
I ran into exactly the same problem with studio 13.04,also the freezing when updating the kernel in the same pass.

I am also still stuck with low resolution display-Nvidia 304 installed by default during installation.

I know its beta1,I'm just reporting the issue.


Its a clean install with reformatted partitions on an amd 64X2 system using a 7600GS nvidia card.

eddie

---

