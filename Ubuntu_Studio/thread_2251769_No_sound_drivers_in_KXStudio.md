---
title: "No sound drivers in KXStudio"
date: 2014-11-06
forum: Ubuntu Studio
---

### Post by rstolfus on 2014-11-06
I recently installed KXStudio on my Toshiba Satelite C55D. The live version went off without a hitch, but once I installed a lot of drivers were missing.
For wifi, after some Googling, I found I had to:

sudo apt-get install linuc-generic-headers build-essential
sudo modprobe mac80211 rtlwifi rtl_pci rtl8188ee

That got my wifi working, but I'm having trouble with sound also. By comparing 'lsmod' between the installed and live versions, I found that my installed KXStudio is missing the following sound mods:
soundcore
snd_
snd_
snd_seq
snd_seq_dummy
snd_seq_midi
snd_seq_midi_event
snd_seq_device
snd_page_alloc
snd_raw_midi
snd_timer
snd_pcm
snd_hwdep
snd_aloop
snd_hda_codec
shd_hda_codec_realtek
snd_htrtimer
rts_5139

Can someone help me find these mods, only 'soundcore' is currently installd? I tried the proprietary driver from realtek, but './configure' comes back with a fatal error, something about an ';' being in the wrong place, so I can't install it either.

---

### Post by jejeman on 2014-11-07
There should be no "big" difference between live and installed system.
Looks like bad install.
Check the ISO, medium and reinstall.

---

