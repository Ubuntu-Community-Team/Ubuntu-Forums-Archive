---
title: "ALSA errors on boot"
date: 2008-05-29
forum: Server Platforms
---

### Post by opus on 2008-05-29
I just upgraded a server from 7.10 to 8.04.  Worked great.  But now I have errors on boot (could have been there before the upgrade too, not sure).  The errors from dmesg are:

```
[   21.128432] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-server/sound/alsa-driver/pci/via82xx.c:581: codec_read: codec 0 is not valid [0xfe0000]
[   21.134664] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-server/sound/alsa-driver/pci/via82xx.c:581: codec_read: codec 0 is not valid [0xfe0000]
[   21.140982] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-server/sound/alsa-driver/pci/via82xx.c:581: codec_read: codec 0 is not valid [0xfe0000]
[   21.147209] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-server/sound/alsa-driver/pci/via82xx.c:581: codec_read: codec 0 is not valid [0xfe0000]

```

I uninstalled alsa from using aptitude, but the errors are still there. I realize that it probably isn't causing any problems with the server, but I still would like a clean environment.  Any ideas how to get rid of the errors?

---

