---
title: "help with wavsplit"
date: 2009-01-05
forum: Ubuntu Studio
---

### Post by sn0m on 2009-01-05
Hi guys,I'm trying to write a script that downloads and stores wav file from live radio broadcasting.
I've got stuck at spiting the wav file in 4 or 5 min chunks before burning it to audio cd. I've got wavsplit installed but I'm finding hard to work with it.
This is what I get in terminal:


sn0m@sn0m-laptop:~/Music$ wavsplit -q stream.wav 10:00 10:00 10:00 10:00 10:00 11:01 

WAVSPLIT version 1.1.0 ([http://www.fomalhaut.de](http://www.fomalhaut.de))
Licensed under GPL by author Tobias Weihmann
Hour patch by Sacha Bartok (sacha@myrealbox.com)
Modified for frames, hours, seconds, decimal seconds by Alan Fitch

Bad file format
sn0m@sn0m-laptop:~/Music$ 

file stream.wav is 1hour1min1sec long

all help appreciated,
Thanks
Sokol

---

### Post by logos34 on 2009-01-05
man wavsplit

try hours or seconds option:
> 
wavsplit -q -H stream.wav 0:10:00 0:20:00 0:30:00 ...
wavsplit -q -s stream.wav 600.0 1200.0 ...

or if 5 min chunks,

wavsplit -q -H stream.wav 0:05:00 0:10:00 0:15:00 ...
wavsplit -q -s stream.wav 300.0 600.0 ...

---

### Post by sn0m on 2009-01-05
tried, no luck
This is the output:

sn0m@sn0m-laptop:~/Music/project$ ls
str.wav
sn0m@sn0m-laptop:~/Music/project$ file str.wav 
str.wav: RIFF (little-endian) data, WAVE audio, Microsoft PCM, 32 bit, mono 22050 Hz
sn0m@sn0m-laptop:~/Music/project$ wavsplit -q -H  str.wav 0:10:00 0:20:00 0:30:00 0:40:00 0:50:00 0:60:00

WAVSPLIT version 1.1.0 ([http://www.fomalhaut.de](http://www.fomalhaut.de))
Licensed under GPL by author Tobias Weihmann
Hour patch by Sacha Bartok (sacha@myrealbox.com)
Modified for frames, hours, seconds, decimal seconds by Alan Fitch

ERROR: When using Hours, minutes must be >= 0  and < 60
sn0m@sn0m-laptop:~/Music/project$ wavsplit -s 600.0 1200.0 1800.0 2400.0 3000.0 3600.0

WAVSPLIT version 1.1.0 ([http://www.fomalhaut.de](http://www.fomalhaut.de))
Licensed under GPL by author Tobias Weihmann
Hour patch by Sacha Bartok (sacha@myrealbox.com)
Modified for frames, hours, seconds, decimal seconds by Alan Fitch

INFO: Seconds only option selected
Bad format: Cannot find RIFF file marker
sn0m@sn0m-laptop:~/Music/project$ 

Quite frustrating, dosen't seem to work, no mater what I do.
Regards
Sokol

---

### Post by logos34 on 2009-01-05
i don't think we made a mistake because here's the examples:
> 
wavsplit --frames 30 file.wav 32:21:15 45:10:0
       wavsplit --Hours file.wav 1:32:21:59.2 1:45:10:0.3
       wavsplit --seconds file.wav 300.1 500.2

>   **-H**, --Hours
              Use Hours as well as minutes and seconds. You may combine this with the --frames option.

       **-s**, --seconds
              Use Seconds. You may not specify hours, minutes, or frames.

hmm...

---

### Post by logos34 on 2009-01-05
YOu might try Wavbreaker gui (which is what I use--without a problem, btw), but as it probably uses wavsplit as the backend I'm not sure that would help you.

---

### Post by sn0m on 2009-01-05
Hi mate
Wavbraker works fine, however I'm trying to write a script that downloads live radio stream wav format, splits it in 10min tracks and burn's it as audio cd, ready to play in my car's stereo.
Difficult??
Regards
Sokol

---

### Post by sn0m on 2009-01-05
this is ever so funny.
I've changed the sample bitrate from 32bit to 16bit and it worked fine.
This is the output:

sn0m@sn0m-laptop:~/Music/project$ ls
str1  str1.wav  str.wav
sn0m@sn0m-laptop:~/Music/project$ file str1.wav
str1.wav: RIFF (little-endian) data, WAVE audio, Microsoft PCM, 16 bit, mono 44100 Hz
sn0m@sn0m-laptop:~/Music/project$ rm -r str1
sn0m@sn0m-laptop:~/Music/project$ wavsplit -s str1.wav 600.0 1200.0 1800.0 2400.0 3000.0 3600.0

WAVSPLIT version 1.1.0 ([http://www.fomalhaut.de](http://www.fomalhaut.de))
Licensed under GPL by author Tobias Weihmann
Hour patch by Sacha Bartok (sacha@myrealbox.com)
Modified for frames, hours, seconds, decimal seconds by Alan Fitch

INFO: Seconds only option selected
Channels: 1
Samplerate: 44100Hz
Samplebits: 16
Databytes: 317517712

Split         Hours  Mins   Seconds         Bytes         %
[01]	until     0     0   600.000      52920000    16.67%
[02]	until     0     0  1200.000     105840000    33.33%
[03]	until     0     0  1800.000     158760000    50.00%
[04]	until     0     0  2400.000     211680000    66.67%
[05]	until     0     0  3000.000     264600000    83.33%
[06]	until     0     0  3600.000     317520000    100.00%
Success.

sn0m@sn0m-laptop:~/Music/project$ 

Does this mean that I have to degrade wav file from 32bit to 16bit to work??strange What's even funnier is that wavbraker splits it fine, even the 32bit sample?
If so what's your opinion, is it worth it or should I dig more to find a program that splits 32bits?
Regards
Sokol

---

### Post by logos34 on 2009-01-05
> **sn0m said:**
> this is ever so funny.
I've changed the sample bitrate from 32bit to 16bit and it worked fine.

...

Does this mean that I have to degrade wav file from 32bit to 16bit to work??strange What's even funnier is that wavbraker splits it fine, even the 32bit sample?
If so what's your opinion, is it worth it or should I dig more to find a program that splits 32bits?
Regards
Sokol

I would never have guessed to check that...16-bit 44.1K is the default

---

