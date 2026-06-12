---
title: "Strange files in my home folder. Not mine?"
date: 2012-01-15
forum: Security
---

### Post by themanfromdelmonte on 2012-01-15
One samples from the very large files registry.i686.bin and registry.x86_64.bin Can you tell me what these strange files are? I have no streams or ports open. Thank you



    g721, g722, g723_3, g723_5 }####w##&#65533;&#65533;TN########gconfelements#elements  wrapping the GStreamer/GConf audio/video output  settings#/usr/lib/gstreamer-0.10/libgstgconfelements.so#0.10.30#LGPL#gst-plugins-good#GStreamer  Good Plugins  (Ubuntu)#[https://launchpad.net/distros/ubuntu/+source/gst-plugins-good0.10#2011-06-15##GstElementFactory#gconfvideosink##################GConf](https://launchpad.net/distros/ubuntu/+source/gst-plugins-good0.10#2011-06-15##GstElementFactory#gconfvideosink##################GConf)  video sink#Sink/Video#Video sink embedding the GConf-settings for video  output#GStreamer maintainers  <gstreamer-devel@lists.sourceforge.net>#GstChildProxy#GstElementFactory#gconfvideosrc####################GConf  video source#Source/Video#Video source embedding the GConf-settings for  video input#GStreamer maintainers  <gstreamer-devel@lists.sourceforge.net>#GstChildProxy#GstElementFactory#gconfaudiosink##################GConf  audio sink#Sink/Audio#Audio sink embedding the GConf-settings for audio  output#Jan Schmidt  <thaytan@mad.scientist.com>#GstChildProxy#GstElementFactory#gconfaudiosrc##################GConf  audio source#Source/Audio#Audio source embedding the GConf-settings for  audio input#GStreamer maintainers  <gstreamer-devel@lists.sourceforge.net>#GstChildProxy##&#65533;&#65533;###&#65533;&#65533;M########fsmsnconference#Farsight  MSN Conference  plugin#/usr/lib/gstreamer-0.10/libfsmsnconference.so#0.0.29#LGPL#farsight2#Farsight#[http://farsight.freedesktop.org/###GstElementFactory#fsmsncamsendconference##################Farsight](http://farsight.freedesktop.org/###GstElementFactory#fsmsncamsendconference##################Farsight)  MSN Sending Conference#Generic/Bin/MSN#A Farsight MSN Sending  Conference#Richard Spiers <richard.spiers@gmail.com>, Youness  Alaoui <youness.alaoui@collabora.co.uk>, Olivier Crete  <olivier.crete@collabora.co.uk>############sink_%d#ANY#########src_%d_%d_%d#ANY#GstChildProxy#GstImplementsInterface#FsConference#GstElementFactory#fsmsncamrecvconference##################Farsight  MSN Reception Conference#Generic/Bin/MSN#A Farsight MSN Reception  Conference#Richard Spiers <richard.spiers@gmail.com>, Youness  Alaoui <youness.alaoui@collabora.co.uk>, Olivier Crete  <olivier.crete@collabora.co.uk>############sink_%d#ANY#########src_%d_%d_%d#ANY#GstChildProxy#GstImplementsInterface#FsConference##&#65533;&#65533;##&#65533;&#65533;TN####     ###isomp4#ISO base media file format support (mp4, 3gpp, qt,  mj2)#/usr/lib/gstreamer-0.10/libgstisomp4.so#0.10.30#LGPL#gst-plugins-good#GStreamer  Good Plugins  (Ubuntu)#[https://launchpad.net/distros/ubuntu/+source/gst-plugins-good0.10#2011-06-15##GstElementFactory#qtdemux#####################QuickTime](https://launchpad.net/distros/ubuntu/+source/gst-plugins-good0.10#2011-06-15##GstElementFactory#qtdemux#####################QuickTime)  demuxer#Codec/Demuxer#Demultiplex a QuickTime file into audio and video  streams#David Schleef <ds@schleef.org>, Wim Taymans  <wim@fluendo.com>############sink#video/quicktime; video/mj2;  audio/x-m4a;  application/x-3gp#########video_%02d#ANY##########audio_%02d#Ac/Depayloader/Network#Extracts,

---

### Post by 0011235813 on 2012-01-15
Delete them immediately if they are not yours- something has gone wrong. If you find files that are not yours on your computer, then it means that one way or another your computer has been breached. When did you find the files? Has anyone had physical access to your PC within the last couple of days? Have there been any firewall breaches? I recommend you backup all your important files- have you checked none of **your** files are missing? Do a fresh install of Ubuntu if you can.

---

### Post by wyliecoyoteuk on 2012-01-15
They are gstreamer registry files, apparently associated with aMSN.

---

### Post by mattxhand on 2012-01-15
Yep, those are definitely from gstreamer.

[http://gstreamer.freedesktop.org/](http://gstreamer.freedesktop.org/)

If those aren't yours, delete them immediately, change your password(s), disable remote login, and review your access logs to see who logged in except you.

---

