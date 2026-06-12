---
title: "autoremove"
date: 2013-01-14
forum: Ubuntu Development Version
---

### Post by jerrylamos on 2013-01-14
Anyone have a clue, after today's update sudo apt-get autoremove on raring amd64 wants to remove 87 files.  What gives??  Would this trash my install?

  glib-networking:i386 gstreamer0.10-plugins-base:i386 gstreamer0.10-plugins-good:i386
  gstreamer0.10-x:i386 libaa1:i386 libasound2:i386 libavc1394-0:i386 libcaca0:i386 libcairo-gobject2:i386
  libcairo2:i386 libcdparanoia0:i386 libdatrie1:i386 libdrm-intel1:i386 libdrm-nouveau2:i386
  libdrm-radeon1:i386 libdv4:i386 libexpat1:i386 libflac8:i386 libfontconfig1:i386 libfreetype6:i386
  libgcrypt11:i386 libgdk-pixbuf2.0-0:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libglapi-mesa:i386
  libglu1-mesa:i386 libgnome-keyring0:i386 libgnutls26:i386 libgpg-error0:i386
  libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386 libgudev-1.0-0:i386 libice6:i386
  libiec61883-0:i386 libjack-jackd2-0:i386 libjasper1:i386 libjbig0:i386 libjpeg-turbo8:i386 libjpeg8:i386
  libllvm3.1:i386 libogg0:i386 liborc-0.4-0:i386 libp11-kit0:i386 libpango1.0-0:i386 libpciaccess0:i386
  libpixman-1-0:i386 libproxy1:i386 libraw1394-11:i386 libsamplerate0:i386 libshout3:i386 libsm6:i386
  libsoup-gnome2.4-1:i386 libsoup2.4-1:i386 libspeex1:i386 libsqlite3-0:i386 libstdc++6:i386
  libtag1-vanilla:i386 libtag1c2a:i386 libtasn1-3:i386 libthai0:i386 libtheora0:i386 libtiff5:i386
  libtxc-dxtn-s2tc0:i386 libv4l-0:i386 libv4lconvert0:i386 libvisual-0.4-0:i386 libvisual-0.4-plugins:i386
  libvorbis0a:i386 libvorbisenc2:i386 libwavpack1:i386 libx11-6:i386 libx11-xcb1:i386 libxau6:i386
  libxcb-glx0:i386 libxcb-render0:i386 libxcb-shm0:i386 libxcb1:i386 libxdamage1:i386 libxdmcp6:i386
  libxext6:i386 libxfixes3:i386 libxft2:i386 libxml2:i386 libxrender1:i386 libxt6:i386 libxv1:i386
  libxxf86vm1:i386

---

### Post by ventrical on 2013-01-14
I'm not sure but it looks like they are all i386 files.

---

### Post by jfernyhough on 2013-01-14
Yeah, looks like an i386 program was updated (or removed) which removed a load of unnecessary depends/recommends. Could also be a multiarch update that had the same effect.

---

### Post by jerrylamos on 2013-01-15
Thanks for your advice, I did the autoremove of (74?) files and raring is still booting and running.  

Do note I also tried to install today's daily build amd64, which failed.  Using an existing partition, no partition change, ubiquity complains about trying to install to a partition outside the drive.  ?  I'll try again tomorrow.

---

