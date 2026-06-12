---
title: "all formats"
date: 2007-12-08
forum: The Cafe
---

### Post by mouseboyx on 2007-12-08
i made a script to make it so you can play all formats in totem there is probably already one out there like this, but i think it is an improvement on not having any installed in the first place
```

#!/bin/sh
mkdir allgstreamer
cd allgstreamer
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-good0.10/gstreamer0.10-esd_0.10.6-0ubuntu4_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gstreamer0.10-ffmpeg/gstreamer0.10-ffmpeg_0.10.2-2ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gst-fluendo-mp3/gstreamer0.10-fluendo-mp3_0.10.5.debian-1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gst-fluendo-mpegdemux/gstreamer0.10-fluendo-mpegdemux_0.10.12-0ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-bad0.10/gstreamer0.10-gl_0.10.5-4ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-base0.10/gstreamer0.10-gnomevfs_0.10.14-1ubuntu3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gnonlin/gstreamer0.10-gnonlin_0.10.9-1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gnonlin/gstreamer0.10-gnonlin-dev_0.10.9-1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gstreamer0.10-pitfdll/gstreamer0.10-pitfdll_0.9.1.1+cvs20070321-1ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-bad0.10/gstreamer0.10-plugins-bad_0.10.5-4ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-bad0.10/gstreamer0.10-plugins-bad-doc_0.10.5-4ubuntu1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/multiverse/g/gst-plugins-bad-multiverse0.10/gstreamer0.10-plugins-bad-multiverse_0.10.5-1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-base0.10/gstreamer0.10-plugins-base_0.10.14-1ubuntu3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-base0.10/gstreamer0.10-plugins-base-apps_0.10.14-1ubuntu3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-base0.10/gstreamer0.10-plugins-base-doc_0.10.14-1ubuntu3_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-farsight/gstreamer0.10-plugins-farsight_0.12.2-1ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-good0.10/gstreamer0.10-plugins-good_0.10.6-0ubuntu4_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-good0.10/gstreamer0.10-plugins-good-doc_0.10.6-0ubuntu4_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-ugly0.10/gstreamer0.10-plugins-ugly_0.10.6-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-ugly0.10/gstreamer0.10-plugins-ugly-doc_0.10.6-0ubuntu2_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/multiverse/g/gst-plugins-ugly-multiverse0.10/gstreamer0.10-plugins-ugly-multiverse_0.10.6-0ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/universe/s/schroedinger/gstreamer0.10-schroedinger_0.6.1-3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-bad0.10/gstreamer0.10-sdl_0.10.5-4ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gstreamer0.10/gstreamer0.10-tools_0.10.14-1ubuntu3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-base0.10/gstreamer0.10-x_0.10.14-1ubuntu3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-bad0.10/gstreamer0.10-plugins-bad-dbg_0.10.5-4ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/multiverse/g/gst-plugins-bad-multiverse0.10/gstreamer0.10-plugins-bad-multiverse-dbg_0.10.5-1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-base0.10/gstreamer0.10-plugins-base-dbg_0.10.14-1ubuntu3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-good0.10/gstreamer0.10-plugins-good-dbg_0.10.6-0ubuntu4_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-ugly0.10/gstreamer0.10-plugins-ugly-dbg_0.10.6-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/multiverse/g/gst-plugins-ugly-multiverse0.10/gstreamer0.10-plugins-ugly-multiverse-dbg_0.10.6-0ubuntu1_i386.deb

sudo aptitude install gstreamer0.10-esd_0.10.6-0ubuntu4_i386.deb
sudo aptitude install gstreamer0.10-ffmpeg_0.10.2-2ubuntu1_i386.deb
sudo aptitude install gstreamer0.10-fluendo-mp3_0.10.5.debian-1_i386.deb
sudo aptitude install gstreamer0.10-fluendo-mpegdemux_0.10.12-0ubuntu1_i386.deb
sudo aptitude install gstreamer0.10-gl_0.10.5-4ubuntu1_i386.deb
sudo aptitude install gstreamer0.10-gnomevfs_0.10.14-1ubuntu3_i386.deb
sudo aptitude install gstreamer0.10-gnonlin_0.10.9-1_i386.deb
sudo aptitude install gstreamer0.10-gnonlin-dev_0.10.9-1_i386.deb
sudo aptitude install gstreamer0.10-pitfdll_0.9.1.1+cvs20070321-1ubuntu1_i386.deb
sudo aptitude install gstreamer0.10-plugins-bad_0.10.5-4ubuntu1_i386.deb
sudo aptitude install gstreamer0.10-plugins-bad-doc_0.10.5-4ubuntu1_all.deb
sudo aptitude install gstreamer0.10-plugins-bad-multiverse_0.10.5-1_i386.deb
sudo aptitude install gstreamer0.10-plugins-base_0.10.14-1ubuntu3_i386.deb
sudo aptitude install gstreamer0.10-plugins-base-apps_0.10.14-1ubuntu3_i386.deb
sudo aptitude install gstreamer0.10-plugins-base-doc_0.10.14-1ubuntu3_all.deb
sudo aptitude install gst-plugins-farsight/gstreamer0.10-plugins-farsight_0.12.2-1ubuntu1_i386.deb
sudo aptitude install gstreamer0.10-plugins-good_0.10.6-0ubuntu4_i386.deb
sudo aptitude install gstreamer0.10-plugins-good-doc_0.10.6-0ubuntu4_all.deb
sudo aptitude install gstreamer0.10-plugins-ugly_0.10.6-0ubuntu2_i386.deb
sudo aptitude install gstreamer0.10-plugins-ugly-doc_0.10.6-0ubuntu2_all.deb
sudo aptitude install gstreamer0.10-plugins-ugly-multiverse_0.10.6-0ubuntu1_i386.deb
sudo aptitude install gstreamer0.10-schroedinger_0.6.1-3_i386.deb
sudo aptitude install gstreamer0.10-sdl_0.10.5-4ubuntu1_i386.deb
sudo aptitude install gstreamer0.10-tools_0.10.14-1ubuntu3_i386.deb
sudo aptitude install gstreamer0.10-x_0.10.14-1ubuntu3_i386.deb
sudo aptitude install gstreamer0.10-plugins-bad-dbg_0.10.5-4ubuntu1_i386.deb
sudo aptitude install gstreamer0.10-plugins-bad-multiverse-dbg_0.10.5-1_i386.deb
sudo aptitude install gstreamer0.10-plugins-base-dbg_0.10.14-1ubuntu3_i386.deb
sudo aptitude install gstreamer0.10-plugins-good-dbg_0.10.6-0ubuntu4_i386.deb
sudo aptitude install gstreamer0.10-plugins-ugly-dbg_0.10.6-0ubuntu2_i386.deb
sudo aptitude install gstreamer0.10-plugins-ugly-multiverse-dbg_0.10.6-0ubuntu1_i386.deb


```

---

### Post by smartboyathome on 2007-12-08
Why don't you just install the packages from the repositories?

EDIT: Just noticed that you download those packages for no reason, as they ARE being installed from the repo.

---

### Post by mouseboyx on 2007-12-08
this is automatic ... its for extreme laziness....

---

### Post by hanzomon4 on 2007-12-08
> **smartboyathome said:**
> Why don't you just install the packages from the repositories?

I guess cause it's faster that way, I don't get the wgets though.. Do rmvb videos work?

---

### Post by DoctorMO on 2007-12-08
You could create a meta package if you wanted to.

---

### Post by az on 2007-12-08
> **DoctorMO said:**
> You could create a meta package if you wanted to.
Isn't that what ubuntu-restricted-extras is?

---

