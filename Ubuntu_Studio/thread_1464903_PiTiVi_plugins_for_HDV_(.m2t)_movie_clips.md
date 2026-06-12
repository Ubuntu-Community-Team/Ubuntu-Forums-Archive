---
title: "PiTiVi plugins for HDV (.m2t) movie clips"
date: 2010-04-28
forum: Ubuntu Studio
---

### Post by maheshasolkar on 2010-04-28
Not sure if this is Lucid specific, but since I am using PiTiVi under Lucid, I though I'd ask here.

I am trying to import some clips from my Sony HD camcorder. I used dvgrab to grab them from the camcorder. They came out as a bunch of .m2t files.

When I import them into PiTiVi, it gives out the following errors:

```
  **URI:**clip_2-2008.08.24_11-22-49.m2t
  **Problem:**Missing plugins:
  HDV AUX-V decoder
  HDV AUX-A decoder
```

PiTiVi tried to search for some plugins, but could not find them.

Which plugins am I missing? Where do I get them from? Am I missing some repository? I already have these:

```
deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb http://archive.canonical.com/ubuntu lucid partner
deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
```

---

### Post by cariboo on 2010-04-28
This is probably a better place to get your question answered.

---

### Post by BrokeMahPC on 2010-04-29
Not sure about PiTiVi but VLC saves it's recordings and plays in that format. You might be able to convert them using ffmpeg? Long time since I looked at that but try investigating video conversion.

I have codec troubles too - the mpeg files I record from MeTV from terrestrial TV (DVB-T) don't play well on Media Player and it asks for a codec.
I have medibuntu, restricted extras and win32 codecs. I am also wondering what else I need?

---

### Post by calc on 2010-05-02
I just ran into this problem myself. I know some older versions of Ubuntu support playing back this format as I have a Canon HV20 that natively shoots this format (HDV MiniDV tape). I'm not sure why it won't play back in Lucid.

Edit (added the following):

**It appears between Ubuntu 9.04 and 9.10 detection for HDV video was added and now it complains even though it can play in totem.**

It also appears the workaround of just ignoring it complaining does not work for PiTiVi.

I filed this issue as bug 574050.

-----
 8.04
  Installs gstreamer0.10-ffmpeg, gstreamer0.10-fluendo-mpegdemux, gstreamer0.10-plugins-bad

  Still does not work.

  -

  Manual install gstreamer0.10-plugins-ugly allows it to play.

-----
 9.04
  "MPEG-2 Transport Stream demuxer"

  Installs gstreamer0.10-plugins-bad

  Still does not work.

  -

  Manual install gstreamer0.10-plugins-ugly allows it to play.

-----
 9.10
  "MPEG-2 Transport Stream demuxer"

  Installs gstreamer0.10-plugins-bad
  
  -
  
  "MPEG-2 Video decoder"
  "HDV AUX-V decoder"
  "HDV AUX-A decoder"
  "MPEG-1 Audio decoder"
  
  Installs gstreamer0.10-ffmpeg, gstreamer0.10-fluendo-mp3, gstreamer0.10-plugins-ugly
  
  -

  "HDV AUX-V decoder"
  "HDV AUX-A decoder"
  
  no plugins found

  -

  If you ignore the no plugins found on 9.10 it will then play ok.

-----
10.04
 "MPEG-2 Transport Stream demuxer"

 Installs gstreamer0.10-plugins-bad

 -

 "MPEG-2 Video decoder"
 "HDV AUX-V decoder"
 "HDV AUX-A decoder"
 "MPEG-1 Audio decoder"

 Installs gstreamer0.10-ffmpeg, gstreamer0.10-fluendo-mp3, gstreamer0.10-plugins-ugly

 -

 "HDV AUX-V decoder"
 "HDV AUX-A decoder"

 no plugins found

 -

 If you ignore the no plugins found on 10.04 it will then play ok, but seems a bit crashy.

-----

---

