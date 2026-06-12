---
title: "ffmpeg help: wav bit depth conversion"
date: 2011-05-11
forum: Ubuntu Studio
---

### Post by lykwydchykyn on 2011-05-11
I have a large number of 16bit/44.1kHz wav files I need to convert to 32bit/96 floats.  (Yes, I know I won't gain any quality, it's for compatibility with another person's gear).

I'm trying to figure out the ffmpeg command to do this, but 
 - it doesn't seem to offer a bit depth setting (only bit *rate*)
 - I'm confused about the float part

Can anyone offer advice on how to script this with ffmpeg?

---

### Post by jejeman on 2011-05-11
you should youse one of this codecs

pcm_f32be       PCM 32-bit floating point big-endian
pcm_f32le       PCM 32-bit floating point little-endian

I realy dont know the difference between big-endian and little-endian.

```
ffmpeg -i input-file.wav -acodec pcm_f32le -ar 96000 output-file.wav
```

---

### Post by lykwydchykyn on 2011-05-11
Thanks; that's exactly what I need.

I'll have to find out which kind they want.

---

### Post by andrew.46 on 2011-05-12
You could also use sox to accomplish this. For example I have the following wav file:

```

andrew@skamandros~/Desktop$ mediainfo test.wav 
General
Complete name                    : test.wav
Format                           : Wave
File size                        : 78.4 MiB
Duration                         : 7mn 46s
Overall bit rate                 : 1 411.2 Kbps

Audio
ID                               : 0
Format                           : PCM
Format settings, Endianness      : Little
Codec ID                         : 1
Codec ID/Hint                    : Microsoft
Duration                         : 7mn 46s
Bit rate                         : 1 411.2 Kbps
Channel(s)                       : 2 channels
[B][COLOR="Red"]Sampling rate                    : 44.1 KHz
Bit depth                        : 16 bits[/COLOR][/B]
Stream size                      : 78.4 MiB (100%)

```

Now to convert to your specifications I ran the following:

```

sox -S test.wav -r 96k -b 32 output.wav

```

and this produced what I believe you are after:

```

andrew@skamandros~/Desktop$ mediainfo output.wav 
General
Complete name                    : output.wav
Format                           : Wave
File size                        : 341 MiB
Duration                         : 7mn 46s
Overall bit rate                 : 6 144 Kbps

Audio
ID                               : 0
Format                           : PCM
Format settings, Endianness      : Little
Format settings, Sign            : Signed
Codec ID                         : 00001000-0000-0100-8000-00AA00389B71
Codec ID/Hint                    : Microsoft
Duration                         : 7mn 46s
Bit rate mode                    : Constant
Bit rate                         : 6 144 Kbps
Channel(s)                       : 2 channels
Channel positions                : Front: L R
[B][COLOR="Red"]Sampling rate                    : 96.0 KHz
Bit depth                        : 32 bits[/COLOR][/B]
Stream size                      : 341 MiB (100%)

```

Might be a less cumbersome way of doing it than unleashing FFmpeg?

Andrew

---

### Post by lykwydchykyn on 2011-05-12
That is much easier; of course, I got it all done last night with a little help from the find command, but I'll add sox to my arsenal for the future.

Thanks!

---

