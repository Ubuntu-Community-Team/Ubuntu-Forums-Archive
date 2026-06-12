---
title: "updating gnome-shell to 3.91 for testing."
date: 2013-05-11
forum: Ubuntu Development Version
---

### Post by bmbaker on 2013-05-11
was just trying out the ricotz/staging ppa with a fresh and saucy install aka 13.10 :-)
after adding the ppa and update and upgrade got this !

```
The following packages will be REMOVED:  gnome-core gnome-sushi libgjs0c libmutter0a ubuntu-gnome-desktop
The following NEW packages will be installed:
  libgjs0d libmutter0b
The following packages will be upgraded:
  clutter-1.0-tests gir1.2-clutter-1.0 gir1.2-clutter-gst-2.0 gir1.2-cogl-1.0
  gir1.2-coglpango-1.0 gir1.2-freedesktop gir1.2-glib-2.0 gir1.2-gtk-3.0
  gir1.2-mutter-3.0 gjs gnome-accessibility-themes gnome-shell
  gnome-shell-common gnome-shell-dbg gnome-shell-extensions
  gnome-themes-standard gnome-themes-standard-data gnome-tweak-tool
  gobject-introspection gstreamer1.0-clutter libclutter-1.0-0
  libclutter-1.0-common libclutter-1.0-dev libclutter-gst-2.0-0
  libclutter-gst-2.0-dev libcogl-common libcogl-dev libcogl-pango-dev
  libcogl-pango12 libcogl12 libgail-3-0 libgail-3-dev libgirepository-1.0-1
  libgirepository1.0-dev libgjs-dev libglib2.0-0 libglib2.0-0:i386
  libglib2.0-bin libglib2.0-data libglib2.0-dev libglib2.0-doc libgtk-3-0
  libgtk-3-bin libgtk-3-common libgtk-3-dev libgtk-3-doc libmutter-dev
  libvala-0.20-0 mutter mutter-common mutter-dbg valac-0.20 valac-0.20-vapi
53 upgraded, 2 newly installed, 5 to remove and 0 not upgraded.
Need to get 37.2 MB of archives.
After this operation, 11.1 MB of additional disk space will be used.
Do you want to continue [Y/n]?



```

seems the change in Gjs from libgjs0c to  libgjs0d breaks gnome-sushi which in turn removes ubuntu-gnome-desktop and gnome-core.

---

### Post by jfernyhough on 2013-05-11
-desktop and -core are meta-packages so you don't need to worry about those.

gnome-sushi should have a compatible version, though. Did you add the other PPAs required by Rico's PPA?

---

### Post by bmbaker on 2013-05-12
yes all 3 ppa's enabled

gnome3-team/gnome3, gnome3-team/gnome3-staging and ricotz/testing

still no sushi :-)

---

