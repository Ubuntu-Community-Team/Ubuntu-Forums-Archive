---
title: "About Autoremove of packages mysql and python"
date: 2015-08-07
forum: Ubuntu Development Version
---

### Post by v3.xx on 2015-08-07
I thought I had a bullet proof set up.  Two virtual machines (mate15.10) that get updated, rebooted, played with for a few minutes.  I then update the host (mate15.10).
Today this pops up in only the host in autoremove after the update/upgrade.

fonts-roboto javascript-common libavfilter-ffmpeg5 libavresample-ffmpeg2 libcec2 libdirac-encoder0 libgegl-0.2-0 libhdhomerun1
  libjs-iscroll libjs-jquery libmicrohttpd10 libmysqlclient18 libnfs4 libpcrecpp0 libpgm-5.1-0 libpostproc-ffmpeg53 libpython3.5-minimal
  libpython3.5-stdlib libsodium13 libssh-4 libswscale-ffmpeg3 libtinyxml2.6.2 libzmq3 linux-headers-4.1.0-2 linux-headers-4.1.0-2-generic
  linux-image-4.1.0-2-generic linux-image-extra-4.1.0-2-generic [COLOR=#b22222]mysql-common[/COLOR] [COLOR=#b22222]python3.5 python3.5-minimal[/COLOR]

The ones in red worry me.

---

### Post by mc4man on 2015-08-07
Not sure where python3.5 came from as virtually nothing depends on it, it's not on the current manifest.
mysql-common has some users but if you don't need it then no reason to keep.

Both can be manually re-installed or marked as such if you so desire.

---

### Post by Chanath on 2015-08-07
Maybe you should re-install the Wily Mate...

---

### Post by v3.xx on 2015-08-07
Thanks mc4man

@mc4man
Autoremoved it all and seems to be ok :)  Guess I will mark this solved.  Thanks

@chanath
That is one naive idea.

---

### Post by Chanath on 2015-08-08
> **v3.xx said:**
> I thought I had a bullet proof set up...
Wily is still on development, so not bullet proof. If you are having these continuous "autoremove" problems, its not naive to re-install Mate.;)

---

### Post by howefield on 2015-08-08
Closed at the request of the OP.

---

