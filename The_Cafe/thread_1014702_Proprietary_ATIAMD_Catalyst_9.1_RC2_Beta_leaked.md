---
title: "Proprietary ATI/AMD Catalyst 9.1 RC2 Beta leaked"
date: 2008-12-18
forum: The Cafe
---

### Post by w0ng on 2008-12-18
Wasn't sure whether or not to post this here, but it seems like it's already spread throughout the Internet pretty quickly.
[http://news.ati-forum.de/index.php/news/48-spiele-und-software/182-catalyst-91-rc2-fuer-linux-download](http://news.ati-forum.de/index.php/news/48-spiele-und-software/182-catalyst-91-rc2-fuer-linux-download)

[quote=Google Translation]
The latest Catalyst 9.1 beta (RC2) drivers for Linux is available exclusively at us we ready to download.

The driver with the number 8:57 owns, the eagerly anticipated, Hybrid CrossfireX support for Linux. In addition, the key Composite & Video Support for free now stopped (for example, for desktop effects, which now work easily in conjunction with videos).

Have fun for free!

Comment from ATi-Forum.de:

We point out that the use of appropriate beta driver is done at your own risk and we have no liability for any resulting damagers (loss of data, etc.) take over!
[/quote]

```

Format: 1.8
Date: Thu, 18 Dec 2008 15:18:42 +1100
Source: fglrx-installer
Binary: xorg-driver-fglrx xorg-driver-fglrx-dev fglrx-kernel-source fglrx-amdcccle fglrx-modaliases libamdxvba1
Architecture: amd64
Version: 2:8.570-0ubuntu1
Distribution: intrepid
Urgency: low
Maintainer: Mario Limonciello <superm1@ubuntu.com>
Changed-By: ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
Description: 
 fglrx-amdcccle - Catalyst Control Center for the ATI graphics accelerators
 fglrx-kernel-source - Kernel module source for the ATI graphics accelerators
 fglrx-modaliases - Identifiers supported by the ATI graphics driver
 libamdxvba1 - AMD Unified Video Decoder library
 xorg-driver-fglrx - Video driver for the ATI graphics accelerators
 xorg-driver-fglrx-dev - Video driver for the ATI graphics accelerators (devel files)
Changes: 
 fglrx-installer (2:8.570-0ubuntu1) intrepid; urgency=low
 .
   * New upstream release.
Checksums-Sha1: 
 d0869a4f490965995b2f44caa52dfd86f511867c 22637706 xorg-driver-fglrx_8.570-0ubuntu1_amd64.deb
 2fdde9eb9530a97bdb8bb684334f45ebf5cf8252 88398 xorg-driver-fglrx-dev_8.570-0ubuntu1_amd64.deb
 bbfe59c8297c6cf21b0a06c91e44be42a3add2ac 1498536 fglrx-kernel-source_8.570-0ubuntu1_amd64.deb
 969d0a0d1d7ecac24650157caf8c8a355d79dcab 6706632 fglrx-amdcccle_8.570-0ubuntu1_amd64.deb
 f879c1b020016c53c086b01f713a6aa041dbbffc 11090 fglrx-modaliases_8.570-0ubuntu1_amd64.deb
 893d4292d2aedfd46a98d70bafb180ba166dbe67 960660 libamdxvba1_8.570-0ubuntu1_amd64.deb
Checksums-Sha256: 
 9cbc66b67911d8328e245db2351f32c47e1faef01b00a51ad081ca117713a041 22637706 xorg-driver-fglrx_8.570-0ubuntu1_amd64.deb
 776b6852b8ed5ebaf280b5327fc2aab73174282a67066ddb941a6664ddbd50de 88398 xorg-driver-fglrx-dev_8.570-0ubuntu1_amd64.deb
 7526471c728123036d1d61348c9c6f5547385813e1ddcb2ac7cd0de814a9e027 1498536 fglrx-kernel-source_8.570-0ubuntu1_amd64.deb
 bd2151c67d74e71774bdeca4b976c7e63ad9ff821b8899e156efd3a7652fe822 6706632 fglrx-amdcccle_8.570-0ubuntu1_amd64.deb
 9c29539acaa3b2e6df9b88084326871255adfc9f7762a59dd66c2d938e720465 11090 fglrx-modaliases_8.570-0ubuntu1_amd64.deb
 53bd6bbfc944af1c1c4b87884aa9c9e9b909b65f572d4bf289501933c5e2f6c2 960660 libamdxvba1_8.570-0ubuntu1_amd64.deb
Files: 
 3a91aaf69b8b66bb70521afdcc62e0dd 22637706 restricted/misc extra xorg-driver-fglrx_8.570-0ubuntu1_amd64.deb
 895a1da2b35a1d12d9613f53c955ce16 88398 restricted/misc extra xorg-driver-fglrx-dev_8.570-0ubuntu1_amd64.deb
 f96e67dfd25b3704f5382b18a4cdaa6f 1498536 restricted/misc extra fglrx-kernel-source_8.570-0ubuntu1_amd64.deb
 5726513b8e3d6ce4cea8d66d2e73e286 6706632 restricted/misc extra fglrx-amdcccle_8.570-0ubuntu1_amd64.deb
 2356431624bb86e68c7012e81f8ce1d8 11090 restricted/misc extra fglrx-modaliases_8.570-0ubuntu1_amd64.deb
 bdb34ce42a1d7e91bb8a1eb5ebda8590 960660 restricted/misc extra libamdxvba1_8.570-0ubuntu1_amd64.deb
```

Very glitchy. I reverted back to 8.12 after about 10mins of testing it.

Whilst playing a video in gnome-mplayer with Xv and compiz enabled:
- no longer flickers
- Moving gnome-mplayer window: works fine
- video still tears
- system sometimes freezes when switching from windowed mode to full-screen
- Windowed mode: video cropped/offset from the top
- Resizing: causes gnome-mplayer's UI to distort, lose some buttons, etc

Screenshots:
[[IMG]http://img261.imageshack.us/img261/8181/12654407on4.th.jpg[/IMG]](http://img261.imageshack.us/my.php?image=12654407on4.jpg)[[IMG]http://img261.imageshack.us/img261/5084/73954324np6.th.jpg[/IMG]](http://img261.imageshack.us/my.php?image=73954324np6.jpg)[[IMG]http://img214.imageshack.us/img214/5420/61596281ep0.th.jpg[/IMG]](http://img214.imageshack.us/my.php?image=61596281ep0.jpg)

---

### Post by binbash on 2008-12-18
i will test it out tonight

---

### Post by theApokalypsis on 2009-01-18
thanks for the post. checking it out as well. :D

---

### Post by Martje_001 on 2009-01-18
I hope the finally finished UVD and release some documentation for it :(.

---

### Post by theApokalypsis on 2009-01-18
I found this thread over on Phoronix as well. Just some extra info.

[http://www.phoronix.com/forums/showthread.php?t=14458](http://www.phoronix.com/forums/showthread.php?t=14458)

Anyways,

Im just happy that the progress is there in beta stage for xV/Compiz. At least IM still running HD 3300 onboard until i get my card back HD 4850 from ASUS. damn holidays!

---

### Post by MaindotC on 2009-01-30
> **w0ng said:**
> 
Very glitchy. I reverted back to 8.12 after about 10mins of testing it.

Whilst playing a video in gnome-mplayer with Xv and compiz enabled:
- no longer flickers
- Moving gnome-mplayer window: works fine
- video still tears
- system sometimes freezes when switching from windowed mode to full-screen
- Windowed mode: video cropped/offset from the top
- Resizing: causes gnome-mplayer's UI to distort, lose some buttons, etc


I just installed this as well on my laptop and desktop.  The desktop I don't have any problems, but my laptop has the above mentioned issues so I'll downgrade as well.  I usually delete the /etc/ati folder and then re-install the driver.  Is that the correct procedure for removal?

---

### Post by zika on 2009-01-30
> **strAlan said:**
> I just installed this as well on my laptop and desktop.  The desktop I don't have any problems, but my laptop has the above mentioned issues so I'll downgrade as well.  I usually delete the /etc/ati folder and then re-install the driver.  Is that the correct procedure for removal?
final 9.01 is out. it works better than 8.12 but still not just great ... :lol:
isn't the proper way of uninstalling it```
cd /usr/share/ati
sudo sh ./fglrx-uninstall.sh
```...?

---

### Post by forrestcupp on 2009-01-30
Do they really have betas of release candidates now?

---

