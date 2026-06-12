---
title: "Request: Avidemux"
date: 2005-06-16
forum: Ubuntu Backports
---

### Post by xhaker on 2005-06-16
On debian marillat repositories.

---

### Post by steven_ellis on 2005-06-16
I had a go at building this and had to remove a couple of entries from the dsc file due to the lack of divx libraries.

Avidemux itself appears to work fine, but the video capture tool ffv1rec doesn't quite work correctly and i'm still looking at that. Some of the capture codecs don't appear to be enabled.

Ive been using this tool for quite some time on RedHat and happy to assist with any work to officially support this on Ubuntu.

```
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA1

Format: 1.0
Source: avidemux
Version: 1:2.0.40-0.0
Binary: avidemux
Maintainer: Christian Marillat <marillat@debian.org>
Architecture: any
Standards-Version: 3.6.1
Build-Depends: debhelper (>> 3.4.4), libgtk2.0-dev, liblame-dev,
 libmad0-dev, liba52-dev, libvorbis-dev, libmjpegtools-dev, libxvidcore4-dev,
 libfreetype6-dev, libxml2-dev,
 libasound2-dev, libsdl-dev, libfaac-dev (>= 1.24), libfaad2-dev
Files:
 eed30487a2ae62f927c8a84dbc889e6d 3755632 avidemux_2.0.40.orig.tar.gz
 f4ea7a66c98203727de67b093212b88c 4006 avidemux_2.0.40-0.0.diff.gz

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.1 (GNU/Linux)

iD8DBQFClF2ZB9xWPR9BuQcRAgIbAJ0fN93+ZdYHcVcqihI2nnRfK78Z/wCfRg8x
2+PxH4CT2TIHc7oRDonAHJ4=
=2i1k
-----END PGP SIGNATURE-----
```

---

