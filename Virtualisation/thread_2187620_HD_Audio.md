---
title: "HD Audio"
date: 2013-11-13
forum: Virtualisation
---

### Post by logicomyu on 2013-11-13
Hi,

I need 192Khz audio support under vmware 9 or 10.
Asus Xonar D1 is dedicated/specified to Ubuntu VM host but once I play audio it is re-sampled since ubuntu recognize/installs ensonic drivers.

Here is output from aplay:

```
$ aplay -v -D plughw:0,0 192Khz.wav
Playing WAVE '192Khz.wav' : Signed 16 bit Little Endian, Rate 192000 Hz, Stereo
Plug PCM: Rate conversion PCM (48000, sformat=S16_LE)
Converter: libspeex (builtin)
Protocol version: 10002
Its setup is:
  stream       : PLAYBACK
  access       : RW_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 2
  rate         : 192000
  exact rate   : 192000 (192000/1)
  msbits       : 16
  buffer_size  : 65536
  period_size  : 16384
  period_time  : 85333
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 16384
  period_event : 0
  start_threshold  : 65536
  stop_threshold   : 65536
  silence_threshold: 0
  silence_size : 0
  boundary     : 1073741824
Slave: Hardware PCM card 0 'Ensoniq AudioPCI' device 0 subdevice 0
Its setup is:
  stream       : PLAYBACK
  access       : MMAP_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 2
  rate         : 48000
  exact rate   : 48000 (1572864000/32768)
  msbits       : 16
  buffer_size  : 16384
  period_size  : 4096
  period_time  : 85333
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 4096
  period_event : 0
  start_threshold  : 16384
  stop_threshold   : 16384
  silence_threshold: 0
  silence_size : 0
  boundary     : 1073741824
  appl_ptr     : 0
  hw_ptr       : 0
```

Once it is not virtualized it works ok:

```
$ aplay -v -D plughw:0,0 192Khz.wav
Playing WAVE '192Khz.wav' : Signed 16 bit Little Endian, Rate 192000 Hz, Stereo

Plug PCM: Hardware PCM card 0 'Xonar D1' device 0 subdevice 0
Its setup is:
  stream       : PLAYBACK

  access       : RW_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 2
  rate         : 192000
  exact rate   : 192000 (192000/1)
  msbits       : 16

   buffer_size  : 96000
  period_size  : 24000
  period_time  : 125000
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 24000
  period_event : 0
  start_threshold  : 96000
  stop_threshold   : 96000
  silence_threshold: 0
  silence_size : 0
  boundary     : 1572864000
  appl_ptr     : 0
  hw_ptr       : 0
```

What would be the way to force ubuntu to use drivers which are supporting hi sound resolution under vmware ?

Kind Regards.

---

