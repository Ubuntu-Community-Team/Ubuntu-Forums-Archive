---
title: "No Thumbnail Preview in Nautilus on Ubuntu Cosmic"
date: 2018-10-08
forum: Ubuntu Development Version
---

### Post by manmath on 2018-10-08
Hi, nautilus unable to create thumbnails for any file including images, pdfs, videos, etc. I tried both tumbler and ffmpegthumbnailer. So far, no success. Please suggest me if I'm missing anything, any package. Here's what my installation has that may relate to thumbnails:

gvfs packages:

gvfs
gvfs-backends
gvfs-bin
gvfs-common
gvfs-daemons
gvfs-fuse
gvfs-libs

gdk packages:

gir1.2-gdkpixbuf-2.0
libgdk-pixbuf2.0-0
libgdk-pixbuf2.0-bin
libgdk-pixbuf2.0-common

ffmpeg packages:

ffmpeg
ffmpegthumbnailer
libffmpegthumbnailer4v5

gstreamer packages:

gir1.2-gstreamer-1.0
gstreamer1.0-alsa
gstreamer1.0-clutter-3.0
gstreamer1.0-gl
gstreamer1.0-gtk3
gstreamer1.0-libav
gstreamer1.0-plugins-bad
gstreamer1.0-plugins-base
gstreamer1.0-plugins-base-apps
gstreamer1.0-plugins-good
gstreamer1.0-pulseaudio
gstreamer1.0-tools
gstreamer1.0-vaapi
gstreamer1.0-x
libgstreamer-gl1.0-0
libgstreamer-plugins-bad1.0-0
libgstreamer-plugins-base1.0-0
libgstreamer-plugins-good1.0-0
libgstreamer1.0-0

nautilus packages:

gir1.2-nautilus-3.0
libnautilus-extension1a
nautilus
nautilus-data

Also, I checked nautilus preferences. It's set to always show thumbnail for files below 4GB.

---

### Post by manmath on 2018-10-09
Ok. No answers, no views. That means Ubuntu and the community have no solutions to this issue or they simply don't care. So much for free software!

---

### Post by wildmanne39 on 2018-10-09
> **manmath said:**
> Ok. No answers, no views. That means Ubuntu and the community have no solutions to this issue or they simply don't care. So much for free software!
The view counter on the forum is broken, your thread has actually had eighteen views so I imagine the person that has the answer has not seen your thread yet but I a sure you we do care.

---

### Post by manmath on 2018-10-09
Thank you for the prompt reply. But where's the solution? (I know I'm not entitled to one)

I don't know how the view counter is broken. I for sure did not break it.
Desperately I posted it on AskUbuntu. Suckingly, that platform termed it off-topic and put the query on hold.
[https://askubuntu.com/questions/1082160/no-thumbnails-for-any-files-on-ubuntu-cosmic](https://askubuntu.com/questions/1082160/no-thumbnails-for-any-files-on-ubuntu-cosmic)

---

### Post by wildmanne39 on 2018-10-09
I do not have the answer either that is why I said.
> I imagine the person that has the answer has not seen your thread yet
No you did not break the view counter it is broken forum wide not just on your threads.

---

### Post by wildmanne39 on 2018-10-09
It looks like a bug since 18.04.

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1769358](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1769358)

---

### Post by manmath on 2018-10-09
Thank you. But my problem is not related to the bug you pointed. I'm unable to see thumbnail both in list view and normal view. Besides, I did not experience this specific problem in 18.04. I'm having it on Cosmic, 18.10.

---

### Post by QIII on 2018-10-09
Cosmic has not been released yet.  Of course everyone would like to hear that you are having an issue and provide support if we are able, but reporting it to Canonical as a bug via apport or directly on launchpad might be a better course of action.  That might get an answer from the developers and might help the community by drawing attention to the issue so that it can be fixed before release.

We are all volunteers here, including the Staff, and we do not work for Canonical.  We cannot affect changes to the code, neither can we demand such.

---

### Post by manmath on 2018-10-09
Pathetic! Then why do you have a separate "Ubuntu Development Version" section in this forum? Besides, isn't this issue a gross case of shoddy QA when the Cosmic RC is just around the corners? These kind of issues should not leap past Alpha versions.
I'm sorry for the harsh words. But hope you got the point. There's not much QA at all in Ubuntu.

---

### Post by QIII on 2018-10-09
Thank you for your interest in Ubuntu.  The Development Version sub-forum exists so that end users can discuss issues and determine if some action needs to be requested of Canonical.  Canonical is a small company with approximately 500 employees.  This sub-forum is a venue for end user QA.

Closed.

---

