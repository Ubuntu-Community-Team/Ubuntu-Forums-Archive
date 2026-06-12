---
title: "MP3 Creation with 8.04 Sound Juicer"
date: 2008-08-27
forum: Ubuntu Studio
---

### Post by Bruce R on 2008-08-27
FOR INFORMATION

In Sound Juicer 2.22.0 Edit Preferences, Format,  select 'CD Quality MP3' and Edit the GStreamer profile to :
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=1
vbr=4 vbr-min-bitrate=32 vbr-max-bitrate=320 vbr-quality=3 ! id3v2mux

This changes the mode to j stereo, selects 'new' VBR coder for VBR coding between 32K and 320K at much better encoding quality than default settings

Try it,  you should be impressed by the results.

NB only works for this recent version of Sound Juicer (also in Mint5)

---

