---
title: "Compiling mplayer-snapshot"
date: 2009-02-06
forum: Ubuntu Studio
---

### Post by Ajunta on 2009-02-06
Hi all!


I found [this]("http://ubuntuforums.org/showthread.php?p=6493398") instruction how to compile mplayer-snapshot on ubuntu, but in case of kubuntu that is not enough. ./configure fails with:

```

checking for MPLAYER_SNAPSHOT... configure: error: Package requirements (glib-2.0 gdk-pixbuf-2.0 cairo-png  ) were not met:

No package 'gdk-pixbuf-2.0' found
No package 'cairo-png' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables MPLAYER_SNAPSHOT_CFLAGS
and MPLAYER_SNAPSHOT_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

What packages should I install?

---

