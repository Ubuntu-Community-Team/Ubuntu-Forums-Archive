---
title: "Lubuntu 12.10 problem with Radio Tray"
date: 2012-09-10
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by George99 on 2012-09-10
Some bad issues with two simultaneously running browsers caused me to try a switch from Lubuntu 12.04 to 12.10. 
I'm aware that this version is not finished yet and until now my main problem vanished, but at this time I have problems with Radio Tray 0.7.3 (installed the newer version from the developer in hope it would work better with this, but it doesn't).

There are so many log files, I don't know in which to seek for any error messages. 

I checked all dependencies mentioned at the [Radio Tray site]("http://radiotray.sourceforge.net/"), all installed.

Depending on which radio station I choose, I receive different error messages.
Examples for Radio Tray messages: 

> ([Radio Baroque]("http://yp.shoutcast.com/sbin/tunein-station.pls?id=272763") )
Radio Error
gstplaysink.c(1906): gen_audio_chain ():/
GstPlayBin2:player/GstPlaySink:playsink0

> ([Smooth 70s]("http://yp.shoutcast.com/sbin/tunein-station.pls?id=145118") )
Radio Error
gstdecodebin2.c(3576): gst_decode_bin_expose ():/
GstPlayBin2:player/GstURIDecodeBin:uridecodebin6/
GstDecodeBin2:decodebin24:
no suitable plugins found

These links run fine with VLC player or Firefox (Firefox only mp3 stream).

Any idea, or should I simply wait for some weeks?
Thanks in advance.

---

### Post by arochester on 2012-09-10
Check that you have the gsteamer  plugins installed - good, bad, ugly **AND **the ffmpeg one.

Radiotray can be a bit slow updating. Exit the program if necessary and start it again

---

### Post by Elfy on 2012-09-10
*Thread moved to **Ubuntu +1 (Quantal Quetzal)**.*

---

### Post by George99 on 2012-09-10
> **arochester said:**
> Check that you have the gsteamer  plugins installed - good, bad, ugly **AND **the ffmpeg one.

Radiotray can be a bit slow updating. Exit the program if necessary and start it again


The GStreamer plugins from the "bad" set were missing.
Thanks arochester! [IMG]http://www.greensmilies.com/smile/smiley_emoticons_hug.gif[/IMG]

---

