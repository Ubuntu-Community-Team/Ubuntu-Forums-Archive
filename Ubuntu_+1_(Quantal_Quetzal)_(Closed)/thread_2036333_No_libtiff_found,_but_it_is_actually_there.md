---
title: "No libtiff found, but it is actually there?"
date: 2012-08-01
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Rallg on 2012-08-01
Odd situation. Might apply to all Ubuntu, but since I'm in QQ I'll ask here:

I looked through my file system for a libtiff file (any version, any file type, any link, anythin at all). I could not find it manually in /usr/lib, where I would expect it. File search did not show anything with libtiff in the file name (except for a fake file that I created in home, just to see if search could find it). I also manually looked in other possible locations. No joy.

Yet synaptic shows that libtiff (version) is installed, and if I run Gimp 2.8 and create a TIF file, it works, and the file is recognized by another graphics program. Reinstalled libtiff, no change.

So, libtiff is out there somewhere in my file system. But where? Is there a bug in the file manager that conceals certain files? Libtiff is not a hidden dotfile. Note that the "which" command won't find libtiff, since it's not in a bin folder.

---

### Post by effenberg0x0 on 2012-08-01
Hi, I believe the answer you expect would be /usr/lib/x86_64-linux-gnu/libtiff.so.5, but for comprehensiveness here's all I found on my system:

```

[17:23:41] ahsl@AL-DESK01:[/usr/lib]: find . -name *tiff*
./gimp/2.0/plug-ins/file-tiff-load
./gimp/2.0/plug-ins/file-tiff-save
./vmware-installer/2.0/lib/libconf/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-tiff.so
./vmware-installer/2.0/lib/libconf/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-tiff.a
./cups/filter/pstotiff
./vmware/libconf/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-tiff.so
./vmware/libconf/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-tiff.a
**./x86_64-linux-gnu/libtiff.so.4**
./x86_64-linux-gnu/ImageMagick-6.7.7/modules-Q16/coders/tiff.so
./x86_64-linux-gnu/ImageMagick-6.7.7/modules-Q16/coders/tiff.la
./x86_64-linux-gnu/qt4/plugins/imageformats/libqtiff.so
**./x86_64-linux-gnu/libtiff.so.5**
./x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-tiff.so
**./x86_64-linux-gnu/libtiff.so.4.3.6**
**./x86_64-linux-gnu/libtiff.so.5.1.0**
./evince/4/backends/libtiffdocument.so
./evince/4/backends/tiffdocument.evince-backend
./ImageMagick-6.6.9/modules-Q16/coders/tiff.so
./ImageMagick-6.6.9/modules-Q16/coders/tiff.la
./kde4/kritatiffimport.so
./kde4/kritatiffexport.so

```Searching on root I get the same plus some mentions on /var/cache/apt/archives/libtiff*.deb and /var/lib/dpkg/info/libtiff4* too.
```

[17:24:52] ahsl@AL-DESK01:[/usr/lib]: ls -la /var/cache/apt/archives/libtiff*.deb
-rw-r--r-- 1 root root 166958 Jul 19 12:33 /var/cache/apt/archives/**libtiff5_4.0.2-1ubuntu2_amd64.deb**
[17:25:13] ahsl@AL-DESK01:[/usr/lib]: dpkg-query -W -f='${binary:Package} ${Version}\t${Description}\t${Provides}\n' **libtiff5**
**libtiff5:amd64 4.0.2-1ubuntu2**    Tag Image File Format (TIFF) library
 libtiff is a library providing support for the Tag Image File Format
 (TIFF), a widely used format for storing image data.  This package
 includes the shared library.    

```Regards,
Effenberg

---

### Post by Rallg on 2012-08-01
Tried that. Didn't work. Also tried things such as launching Nautilus from terminal, exposing hidden files, and so forth. No joy.

Still, my system works just fine, as far as I can tell. Since I use a few packages that are not part of the QQ distribution (upstream graphics, mostly) it is quite possible that something is interfering with my file manager. The problem might be my own fault. Not a big deal. This is "testing." :P

---

### Post by mc4man on 2012-08-01
Next time you're in synaptic for any such just highlight the package > properties > installed
or in addition to previous post you can use locate, like in any of these - 

locate libtiff
locate libtiff.
locate libtiff.so

---

### Post by Harry33 on 2012-08-02
There are currently two tiff source packages in QQ:
- the older libtiff4 (package libsdl-image1.2 still depends on this, needed by VLC)
- the new libtiff5
Here:
[https://launchpad.net/ubuntu/+source/tiff/4.0.2-1ubuntu2/+build/3668613](https://launchpad.net/ubuntu/+source/tiff/4.0.2-1ubuntu2/+build/3668613)

You can see all the files installed by this package with synaptic.
Just locate the package from the "installed" list, then choose "properties2 and files from there.

---

### Post by Rallg on 2012-08-02
OK, found the files via Synaptic, as suggested above. Thanks. I hadn't thought of that (you learn somethin new every day).

Since I also use MinGW/MSYS on the Windows side, I had an expectation that the files would be in the same folders in Ubuntu. Not necessarily. For example, libtiff(version) is in /usr/lib in MinGW/MSYS, but it's in /usr/lib/i386-linux-gnu in my Ubuntu. I would never have thought of looking there.

If I didn't find it via Natilus search, then I'll probabably have to re-learn Nautilus. I notice that Nautilus looks and behaves differently than it did just a month ago, so I might have mis-used it.

---

### Post by mc4man on 2012-08-02
> **Rallg said:**
> 

If I didn't find it via Natilus search, then I'll probabably have to re-learn Nautilus. I notice that Nautilus looks and behaves differently than it did just a month ago, so I might have mis-used it.
The new search in nautilus ranges from doing ok to crappy, it seems to depend on where you're searching from & how many characters you use.
(if searches anywhere in file name, not left to right
So for libtiff it produces results  here from /usr, /usr/lib, & /usr/lib/x86_64-linux-gnu

Searching from / gives nothing, as does from Home even if All Files is selected.
Seemed to work a bit better with a tracker enabled nautilus when more than the default indexed were enabled though at times tracker* used huge amounts of memory 

(plus at least here nautilus has some performance issues while in /usr/lib as compared to other FM's, takes some time to open & context menu is delayed on opening on files in /usr/lib

---

### Post by Rallg on 2012-08-02
Ah. I was searching from /. Didn't think of searching from a folder.

---

