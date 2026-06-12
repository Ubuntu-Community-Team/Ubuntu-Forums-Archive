---
title: "some backports missing in i386 arch"
date: 2005-11-22
forum: Ubuntu Backports
---

### Post by duffman25 on 2005-11-22
Hi

I have 2 machines, an amd64 desktop & a centrino laptop. Today initial backports appeared, but some of them only appeared for amd64. I'm using the es.archive.ubuntu.com mirror. In particular, rhythmbox 0.9.1 didn't show up, and some others. I've checked archive.ubuntu.com from it's web interface & the same happens. Any ideas?

---

### Post by ubuntu_demon on 2005-11-22
you probably just have to have a but more patience :)

---

### Post by duffman25 on 2005-11-22
[QUOTE=ubuntu_demon]you probably just have to have a but more patience :)[/QUOTE]

According to this page:
[http://packages.ubuntu.com/breezy-backports/gnome/rhythmbox](http://packages.ubuntu.com/breezy-backports/gnome/rhythmbox)

There's no i386 package (look at the end in Download rhythmbox). This happens with other packages, like gnomebaker. Any ideas? Is this a bug or do we really have to wait?

---

### Post by jdong on 2005-11-22
There were some weird issues with the build server, so I'm gonna let things sit a bit then re-push them to James Troup.


If anyone is willing to help, go through all the Backports source packages, and track down exactly which ones are missing binaries. Thanks!

---

### Post by duffman25 on 2005-11-22
[QUOTE=jdong]There were some weird issues with the build server, so I'm gonna let things sit a bit then re-push them to James Troup.


If anyone is willing to help, go through all the Backports source packages, and track down exactly which ones are missing binaries. Thanks![/QUOTE]

I've gone through this list:
[http://packages.ubuntu.com/breezy-backports/allpackages](http://packages.ubuntu.com/breezy-backports/allpackages)

and this are the binary packages missing in the 386 arch:
[http://packages.ubuntu.com/breezy-backports/gnome/gnome-peercast](http://packages.ubuntu.com/breezy-backports/gnome/gnome-peercast)
[http://packages.ubuntu.com/breezy-backports/gnome/gnome-power-manager](http://packages.ubuntu.com/breezy-backports/gnome/gnome-power-manager)
[http://packages.ubuntu.com/breezy-backports/gnome/gnome-vlc](http://packages.ubuntu.com/breezy-backports/gnome/gnome-vlc)
[http://packages.ubuntu.com/breezy-backports/gnome/gnomebaker](http://packages.ubuntu.com/breezy-backports/gnome/gnomebaker)
[http://packages.ubuntu.com/breezy-backports/graphics/gvlc](http://packages.ubuntu.com/breezy-backports/graphics/gvlc)
[http://packages.ubuntu.com/breezy-backports/otherosfs/k3b](http://packages.ubuntu.com/breezy-backports/otherosfs/k3b)
[http://packages.ubuntu.com/breezy-backports/libs/k3b-mp3](http://packages.ubuntu.com/breezy-backports/libs/k3b-mp3)
[http://packages.ubuntu.com/breezy-backports/libs/k3blibs](http://packages.ubuntu.com/breezy-backports/libs/k3blibs)
[http://packages.ubuntu.com/breezy-backports/libdevel/k3blibs-dev](http://packages.ubuntu.com/breezy-backports/libdevel/k3blibs-dev)
[http://packages.ubuntu.com/breezy-backports/kde/kvlc](http://packages.ubuntu.com/breezy-backports/kde/kvlc)
[http://packages.ubuntu.com/breezy-backports/libdevel/libvlc0-dev](http://packages.ubuntu.com/breezy-backports/libdevel/libvlc0-dev)
[http://packages.ubuntu.com/breezy-backports/tex/lilypond](http://packages.ubuntu.com/breezy-backports/tex/lilypond)
[http://packages.ubuntu.com/breezy-backports/sound/lmms](http://packages.ubuntu.com/breezy-backports/sound/lmms)
[http://packages.ubuntu.com/breezy-backports/gnome/mail-notification](http://packages.ubuntu.com/breezy-backports/gnome/mail-notification)
[http://packages.ubuntu.com/breezy-backports/tex/mftrace](http://packages.ubuntu.com/breezy-backports/tex/mftrace)
[http://packages.ubuntu.com/breezy-backports/graphics/mozilla-plugin-vlc](http://packages.ubuntu.com/breezy-backports/graphics/mozilla-plugin-vlc)
[http://packages.ubuntu.com/breezy-backports/graphics/qvlc](http://packages.ubuntu.com/breezy-backports/graphics/qvlc)
[http://packages.ubuntu.com/breezy-backports/gnome/rhythmbox](http://packages.ubuntu.com/breezy-backports/gnome/rhythmbox)
[http://packages.ubuntu.com/breezy-backports/gnome/sensors-applet](http://packages.ubuntu.com/breezy-backports/gnome/sensors-applet)
[http://packages.ubuntu.com/breezy-backports/graphics/vlc](http://packages.ubuntu.com/breezy-backports/graphics/vlc)
[http://packages.ubuntu.com/breezy-backports/graphics/vlc-plugin-alsa](http://packages.ubuntu.com/breezy-backports/graphics/vlc-plugin-alsa)
[http://packages.ubuntu.com/breezy-backports/graphics/vlc-plugin-arts](http://packages.ubuntu.com/breezy-backports/graphics/vlc-plugin-arts)
[http://packages.ubuntu.com/breezy-backports/graphics/vlc-plugin-esd](http://packages.ubuntu.com/breezy-backports/graphics/vlc-plugin-esd)
[http://packages.ubuntu.com/breezy-backports/graphics/vlc-plugin-ggi](http://packages.ubuntu.com/breezy-backports/graphics/vlc-plugin-ggi)
[http://packages.ubuntu.com/breezy-backports/graphics/vlc-plugin-sdl](http://packages.ubuntu.com/breezy-backports/graphics/vlc-plugin-sdl)
[http://packages.ubuntu.com/breezy-backports/graphics/wxvlc](http://packages.ubuntu.com/breezy-backports/graphics/wxvlc)

It seems that the problem has only afected the 386 archive. Hope this helps.

---

### Post by jdong on 2005-11-22
Thanks! I'll re-push this to James

---

### Post by jdong on 2005-11-22
UPDATE: spoke with a build server admin; the problem has been fixed and binaries for those packages should appear soon :)

---

### Post by duffman25 on 2005-11-23
[QUOTE=jdong]UPDATE: spoke with a build server admin; the problem has been fixed and binaries for those packages should appear soon :)[/QUOTE]

Thanxs man!

---

