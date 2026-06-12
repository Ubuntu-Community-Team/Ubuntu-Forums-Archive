---
title: "Speakers not recognized"
date: 2012-09-30
forum: Server Platforms
---

### Post by hawaiiman on 2012-09-30
Speakers worked fine under 12.04 32bit, but when I went to 64bit (server) the sound page shows no devices, so no sound. I upgraded kernel to 3.2.0-31, but no change.

---

### Post by anonymouschief on 2012-10-15
Hello,

it appears as though you're running the desktop version of Ubuntu. You're referring to a Sounds page. Are you running Ubuntu server with GUI? If so, which GUI are you using?

---

### Post by hawaiiman on 2012-10-15
I am running 10.04 64bit server with gnome after installed.

---

### Post by cariboo on 2012-10-16
Are the sound modules loaded? Use the following command to check:

```
lsmod | grep snd
```

depending on the audio chip set, the output should look similar to this:

```
lsmod | grep snd
snd_hda_codec_realtek   224173  1 
snd_hda_intel          33773  0 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
snd_timer              29990  1 snd_pcm
snd                    78855  6 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
```

---

### Post by hawaiiman on 2012-10-16
It's an intel g41 express chipset.
 
nd_hda_codec_realtek 279072 1 
snd_hda_intel 25805 0 
snd_hda_codec 85663 2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep 6778 1 snd_hda_codec
snd_pcm_oss 41234 0 
snd_mixer_oss 16107 1 snd_pcm_oss
snd_pcm 87312 3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy 1782 0 
snd_seq_oss 30999 0 
snd_seq_midi 5829 0 
snd_rawmidi 23116 1 snd_seq_midi
snd_seq_midi_event 7267 2 snd_seq_oss,snd_seq_midi
snd_seq 57417 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer 23649 2 snd_pcm,snd_seq
snd_seq_device 6888 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd 71074 12 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore 8052 1 snd
snd_page_alloc 8500 2 snd_hda_intel,snd_pcm

---

