---
title: "CELP+ADPCM  Format/s supported?"
date: 2008-05-02
forum: Ubuntu Studio
---

### Post by Leon945 on 2008-05-02
Hello people,
I have a quick question..
I'm thinking of buying a digital voice recorder, and it says it records in this format CELP+ADPCM.

I don't know the format/s but i just want to know if it is supported in ubuntu so i can edit the recordings with audacity?

thanks in advanced

---

### Post by nomeat on 2008-05-09
Some players like Mplayer and Xine will read the ADPCM WAV format but Audacity definitely can not load them.

The Audicity wiki mentions that mplayer could decode it to a usable format for editing.
All I found is a command line module called memcoder that belongs to mplayer which is explained here:

[http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#menc-feat-enc-libavcodec-audio-codecs-pcmadpcm](http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#menc-feat-enc-libavcodec-audio-codecs-pcmadpcm) 

but you might need to be a software engineer to figure out the comand line to convert ADPCM WAV to standard WAV.

If some one has done it before I would also be grateful if they could post the code here.

... or another solution to convert WAV files recorded on mp3 players to an editable format.

---

### Post by Leon945 on 2008-05-12
there is a program called "audio converter" or something like that..

does anyone know if that program reads/converts from these formats?

---

### Post by ron999 on 2008-05-12
> **Leon945 said:**
> there is a program called "audio converter" or something like that..

does anyone know if that program reads/converts from these formats?
Hi
There's a package called 'SoundConverter' but I don't know whether it supports unusual codecs.

I think that ffmpeg will accept those ADPCM formats. To use it from the command line it's like this:-
```
ffmpeg -i <filename> outputfile.wav
```
There's a GUI for ffmpeg called 'Winff'. It has a pre-set 'WAV for CD'. This will maybe do what you need.
You can get Winff (Debian/Ubuntu package) from here:-[http://www.winff.org/]("http://www.winff.org/")

---

### Post by nomeat on 2008-05-15
Thanks buddy

ffmpeg -i <filename> outputfile.wav

worked for me :)
It created a file about 4x larger than the original and Audacity had no problems with it.

However Winff using 'WAV for CD' gave an error 'truncated and/or corrupted file'

---

