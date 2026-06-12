---
title: "Convert WAV file to .. WAV file"
date: 2014-10-09
forum: Ubuntu Studio
---

### Post by vinsbg on 2014-10-09
Hi,
Is there a way to change one wav file from?
```
[COLOR=#000000][FONT=Consolas]RIFF (little-endian) data, WAVE audio, Microsoft PCM, 8 bit, mono 8000 Hz[/FONT][/COLOR]
```
to
```
[COLOR=#000000][FONT=Consolas]RIFF (little-endian) data, WAVE audio, ITU G.711 u-law, mono 8000 Hz[/FONT][/COLOR]
```
What can I use? Can ffmpeg do this?

---

### Post by jejeman on 2014-10-09
I see only this codecs in avconv
```
DEA... pcm_mulaw            PCM mu-law
DEA... pcm_alaw             PCM A-law
DEA.L. adpcm_g726           G.726 ADPCM (decoders: g726 ) (encoders: g726 )
DEA.L. adpcm_g722           G.722 ADPCM (decoders: g722 ) (encoders: g722 )
D.A.L. g723_1               G.723.1
..A.L. g729                 G.729
```

---

### Post by vinsbg on 2014-10-09
Hm, I have numbers of wavs with this codec - [COLOR=#000000][FONT=Consolas]ITU G.711 u-law ..
The problem is that I have 2 wavs with [/FONT][/COLOR][COLOR=#000000][FONT=Consolas]Microsoft PCM [/FONT][/COLOR][FONT=Consolas]and they doesn't wont to play .. I can't play only[/FONT][COLOR=#000000][FONT=Consolas] [/FONT][/COLOR][COLOR=#000000][FONT=Consolas]ITU G.711 u-law[/FONT][/COLOR]

---

### Post by andrew.46 on 2014-10-10
Should be able to be done with FFmpeg at least, I don't know much about avconv:

```

andrew@ilium~$ **[COLOR="#FF0000"]ffmpeg -encoders 2>/dev/null | grep PCM [/COLOR]**
 A..... adpcm_adx            SEGA CRI ADX ADPCM
 A..... g722                 G.722 ADPCM (codec adpcm_g722)
 A..... g726                 G.726 ADPCM (codec adpcm_g726)
 A..... adpcm_ima_qt         ADPCM IMA QuickTime
 A..... adpcm_ima_wav        ADPCM IMA WAV
 A..... adpcm_ms             ADPCM Microsoft
 A..... adpcm_swf            ADPCM Shockwave Flash
 A..... adpcm_yamaha         ADPCM Yamaha
 A..... pcm_alaw             PCM A-law / G.711 A-law
 A..... pcm_f32be            PCM 32-bit floating point big-endian
 A..... pcm_f32le            PCM 32-bit floating point little-endian
 A..... pcm_f64be            PCM 64-bit floating point big-endian
 A..... pcm_f64le            PCM 64-bit floating point little-endian
**[COLOR="#FF0000"] A..... pcm_mulaw            PCM mu-law / G.711 mu-law[/COLOR]**
 A..... pcm_s16be            PCM signed 16-bit big-endian
 A..... pcm_s16be_planar     PCM signed 16-bit big-endian planar
 A..... pcm_s16le            PCM signed 16-bit little-endian
 A..... pcm_s16le_planar     PCM signed 16-bit little-endian planar
 A..... pcm_s24be            PCM signed 24-bit big-endian
 A..... pcm_s24daud          PCM D-Cinema audio signed 24-bit
 A..... pcm_s24le            PCM signed 24-bit little-endian
 A..... pcm_s24le_planar     PCM signed 24-bit little-endian planar
 A..... pcm_s32be            PCM signed 32-bit big-endian
 A..... pcm_s32le            PCM signed 32-bit little-endian
 A..... pcm_s32le_planar     PCM signed 32-bit little-endian planar
 A..... pcm_s8               PCM signed 8-bit
 A..... pcm_s8_planar        PCM signed 8-bit planar
 A..... pcm_u16be            PCM unsigned 16-bit big-endian
 A..... pcm_u16le            PCM unsigned 16-bit little-endian
 A..... pcm_u24be            PCM unsigned 24-bit big-endian
 A..... pcm_u24le            PCM unsigned 24-bit little-endian
 A..... pcm_u32be            PCM unsigned 32-bit big-endian
 A..... pcm_u32le            PCM unsigned 32-bit little-endian
 A..... pcm_u8               PCM unsigned 8-bit
 A..... roq_dpcm             id RoQ DPCM
andrew@ilium~$ 


```

So I suspect something like the following might help out:

```

ffmpeg -i input.wav \
      -c:a pcm_mulaw -ar 8000 -ac 1 \
      output.wav

```

but I have to admit I have not tested this.... Mind you a decent Ubuntu system should be able to play most wav types so this is a little odd?

---

### Post by vinsbg on 2014-10-10
> **andrew.46 said:**
> Should be able to be done with FFmpeg at least, I don't know much about avconv:

```

andrew@ilium~$ **[COLOR=#FF0000]ffmpeg -encoders 2>/dev/null | grep PCM [/COLOR]**
 A..... adpcm_adx            SEGA CRI ADX ADPCM
 A..... g722                 G.722 ADPCM (codec adpcm_g722)
 A..... g726                 G.726 ADPCM (codec adpcm_g726)
 A..... adpcm_ima_qt         ADPCM IMA QuickTime
 A..... adpcm_ima_wav        ADPCM IMA WAV
 A..... adpcm_ms             ADPCM Microsoft
 A..... adpcm_swf            ADPCM Shockwave Flash
 A..... adpcm_yamaha         ADPCM Yamaha
 A..... pcm_alaw             PCM A-law / G.711 A-law
 A..... pcm_f32be            PCM 32-bit floating point big-endian
 A..... pcm_f32le            PCM 32-bit floating point little-endian
 A..... pcm_f64be            PCM 64-bit floating point big-endian
 A..... pcm_f64le            PCM 64-bit floating point little-endian
**[COLOR=#FF0000] A..... pcm_mulaw            PCM mu-law / G.711 mu-law[/COLOR]**
 A..... pcm_s16be            PCM signed 16-bit big-endian
 A..... pcm_s16be_planar     PCM signed 16-bit big-endian planar
 A..... pcm_s16le            PCM signed 16-bit little-endian
 A..... pcm_s16le_planar     PCM signed 16-bit little-endian planar
 A..... pcm_s24be            PCM signed 24-bit big-endian
 A..... pcm_s24daud          PCM D-Cinema audio signed 24-bit
 A..... pcm_s24le            PCM signed 24-bit little-endian
 A..... pcm_s24le_planar     PCM signed 24-bit little-endian planar
 A..... pcm_s32be            PCM signed 32-bit big-endian
 A..... pcm_s32le            PCM signed 32-bit little-endian
 A..... pcm_s32le_planar     PCM signed 32-bit little-endian planar
 A..... pcm_s8               PCM signed 8-bit
 A..... pcm_s8_planar        PCM signed 8-bit planar
 A..... pcm_u16be            PCM unsigned 16-bit big-endian
 A..... pcm_u16le            PCM unsigned 16-bit little-endian
 A..... pcm_u24be            PCM unsigned 24-bit big-endian
 A..... pcm_u24le            PCM unsigned 24-bit little-endian
 A..... pcm_u32be            PCM unsigned 32-bit big-endian
 A..... pcm_u32le            PCM unsigned 32-bit little-endian
 A..... pcm_u8               PCM unsigned 8-bit
 A..... roq_dpcm             id RoQ DPCM
andrew@ilium~$ 


```

So I suspect something like the following might help out:

```

ffmpeg -i input.wav \
      -c:a pcm_mulaw -ar 8000 -ac 1 \
      output.wav

```

but I have to admit I have not tested this.... Mind you a decent Ubuntu system should be able to play most wav types so this is a little odd?
Thank's for this info. I'll try it later and will let you know what is happen.

---

### Post by vinsbg on 2014-10-10
I think I don't have codecs installed?
```
ffmpeg -i 110.wav -c:a pcm_mulaw -ar 8000 -ac 1 output.wavFFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-shared --disable-static --enable-amr_nb
  libavutil version: 49.3.0
  libavcodec version: 51.38.0
  libavformat version: 51.10.0
  built on Dec  7 2007 16:31:16, gcc: 3.2.3 20030502 (Red Hat Linux 3.2.3-24)
Input #0, wav, from '110.wav':
  Duration: 00:00:06.8, start: 0.000000, bitrate: 64 kb/s
  Stream #0.0: Audio: pcm_u8, 8000 Hz, mono, 64 kb/s
ffmpeg: unrecognized option '-c:a'
```

```

 ffmpeg -codecs
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-shared --disable-static --enable-amr_nb
  libavutil version: 49.3.0
  libavcodec version: 51.38.0
  libavformat version: 51.10.0
  built on Dec  7 2007 16:31:16, gcc: 3.2.3 20030502 (Red Hat Linux 3.2.3-24)
ffmpeg: missing argument for option '-codecs'

```

---

### Post by vinsbg on 2014-10-10
Ok, I've make some conversion but the output file is
```
RIFF (little-endian) data, WAVE audio, ITU G.711 mu-law, mono 8000 Hz

```
I need 
```
RIFF (little-endian) data, WAVE audio, ITU G.711 u-law, mono 8000 Hz

```
The different part is **m** in **m**u-law. So what for is this **m **&#8203;and are they equal or?

---

### Post by andrew.46 on 2014-10-10
> **vinsbg said:**
> I think I don't have codecs installed?

You have an old version of FFmpeg :). I believe the older option is actually *-acodec* rather than *-c:a*.

---

### Post by andrew.46 on 2014-10-10
> **vinsbg said:**
> The different part is **m** in **m**u-law. So what for is this **m **&#8203;and are they equal or?

These are both English versions of the Ancient Greek letter for m, the letter 'mu' or '&#956;'. Should functionally be the same...

---

