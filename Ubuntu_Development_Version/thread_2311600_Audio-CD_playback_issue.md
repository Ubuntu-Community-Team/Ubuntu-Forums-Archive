---
title: "Audio-CD playback issue"
date: 2016-01-28
forum: Ubuntu Development Version
---

### Post by WebDrake on 2016-01-28
I've recently installed Ubuntu 16.04 from the daily releases.  Largely all is good, but one noticeable problem is playing audio CDs: there is an audible, strong "buzz" through which some aspects of the expected music can faintly -- and choppily -- be heard.  I've tried this both with Rhythmbox and Goobox with the same results.  FLAC files etc. play back without problem, and normal audio playback from other sources (system sounds, YouTube videos etc.) is fine, so it's not a general audio problem, but something specific to do with CDs.

I'm not sure what could be wrong, or which package I should report a bug against -- could anyone advise?

My system is a ThinkPad T420 with a built-in CD/DVD player (can look up further details if that would be useful).

Thanks in advance for any advice/feedback.

---

### Post by mc4man on 2016-01-29
Yeah, Rb & that goobox are terrible with audio cd's. Audacious & vlc are fine so possibly a gstreamer issue.
Actually quite bad here, more buzzing, ect. than music
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1539700](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1539700)

---

### Post by Yellow Pasque on 2016-01-29
I believe gstreamer has two plugins for reading CD's. If you could find some way to use the non-cdparanoia variant, that would be an interesting test:
```
Plugin Details:
  Name                     cdio
  Description              Read audio from audio CDs
  Filename                 /usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstcdio.so
  Version                  1.6.3
  License                  GPL
  Source module            gst-plugins-ugly
  Source release date      2016-01-20
  Binary package           GStreamer Ugly Plugins (Debian)
  Origin URL               http://packages.qa.debian.org/gst-plugins-ugly1.0

  cdiocddasrc: CD audio source (CDDA)


Plugin Details:
  Name                     cdparanoia
  Description              Read audio from CD in paranoid mode
  Filename                 /usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstcdparanoia.so
  Version                  1.6.3
  License                  LGPL
  Source module            gst-plugins-base
  Source release date      2016-01-20
  Binary package           GStreamer Base Plugins (Debian)
  Origin URL               http://packages.qa.debian.org/gst-plugins-base1.0

  cdparanoiasrc: CD Audio (cdda) Source, Paranoia IV
```

---

### Post by Yellow Pasque on 2016-01-29
I tried these two commands on my Debian sid system and they both played fine:
```
gst-launch-1.0 cdiocddasrc mode=1 ! audioconvert ! audioresample ! alsasink
gst-launch-1.0 cdparanoiasrc mode=1 ! audioconvert ! audioresample ! alsasink
```

Obviously, if you're trying this on Ubuntu, you'll need gstreamer ugly plugins installed and you'll probably want to use pulsesink instead of alsasink.

---

### Post by mc4man on 2016-01-29
> **Temüjin said:**
> I tried these two commands on my Debian sid system and they both played fine:
```
gst-launch-1.0 cdiocddasrc mode=1 ! audioconvert ! audioresample ! alsasink
gst-launch-1.0 cdparanoiasrc mode=1 ! audioconvert ! audioresample ! alsasink
```

Obviously, if you're trying this on Ubuntu, you'll need gstreamer ugly plugins installed and you'll probably want to use pulsesink instead of alsasink.

cdparanoiasrc with either alsasink or pulsesink shows same bad sound
cdiocddasrc with pulsesink is also bad however with alsasink it's ok.

---

### Post by WebDrake on 2016-01-29
> **mc4man said:**
> Yeah, Rb & that goobox are terrible with audio cd's. Audacious & vlc are fine so possibly a gstreamer issue.
Actually quite bad here, more buzzing, ect. than music
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1539700](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1539700)

Yea, that's exactly what I'm getting.  Good that someone already reported it.

Thanks everyone for the thoughts on how to work around the problem or track down its exact nature.  Much appreciated!

---

