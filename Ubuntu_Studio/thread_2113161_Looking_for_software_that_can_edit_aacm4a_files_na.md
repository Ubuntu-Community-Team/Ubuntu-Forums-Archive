---
title: "Looking for software that can edit aac/m4a files natively"
date: 2013-02-06
forum: Ubuntu Studio
---

### Post by n3mmr on 2013-02-06
All I need is cutting and splicing and splitting and joining.

I sometimes get aac files in fixed-time chunks and the program parts will often span across chunks.

The SW needs to do the actual operations on the aac data w/o any conversions.

Ubuntustudio 12.10

---

### Post by jejeman on 2013-02-06
What did you tried?
Avidemux can do stuff like that for some files.

---

### Post by n3mmr on 2013-02-07
> **jejeman said:**
> What did you tried?
Avidemux can do stuff like that for some files.
Are you saying that Avidemux can edit aac/m4a audio w/o reencoding the edited audio??

I tried Avidemux and it can't even open an m4a file.

---

### Post by jejeman on 2013-02-07
Sorry, I overlooked it is a m4a, the only audio container. My bad.

With ffmpeg you can probably cut and split, but you can't join.

---

### Post by n3mmr on 2013-02-07
> **jejeman said:**
> Sorry, I overlooked it is a m4a, the only audio container. My bad.

With ffmpeg you can probably cut and split, but you can't join.

Maybe if I first stuff that aac stream into blank images video containers???

---

### Post by jejeman on 2013-02-07
Well, maybe it will work. I haven't tried AAC codec with copy function, and after that you will probably need to extrat that audio from saved video.
You can also look in sox program, it can join files, but I haven't used it. See if you can split files with it, then join it. 

Does reencodig looses that much quality? Is it noticable?

---

### Post by n3mmr on 2013-02-07
> **jejeman said:**
> Well, maybe it will work. I haven't tried AAC codec with copy function, and after that you will probably need to extrat that audio from saved video.
You can also look in sox program, it can join files, but I haven't used it. See if you can split files with it, then join it. 

Does reencodig looses that much quality? Is it noticable?

Actually, all aac encoders have significant artefacts,  sometimes quite audible to the wary and well prepared ear.
Even so, applying any aac encoder once is not very noticeable, and any artefacts are carefully designed not to be very annoying.

However, even at 96kb/s per channel, aac encoding applied twice is very noticeable and, with classical music and a trained ear, very annoying. I dare say acoustically and spatially dense, and of course artificially generated, music fares better, but, say, a single female soprano voice with highly dynamic piano accompaniment sometimes becomes laughably annoying. It all depends on how the piano attacks and voice starts are distributed for the two sound sources.

My main concern is that the client (sadly not a paying customer, but a non-profit organization ) requested "no reencodings" and I foolishly agreed.... I thought it was mp3.... I'd prefer not to back down, but do as they asked.

---

### Post by FakeOutdoorsman on 2013-02-07
> **jejeman said:**
> With ffmpeg you can probably cut and split, but you can't join.

You can join in ffmpeg with the *concat* demuxer, protocol, or filter. Refer to [How can I join video files?](http://ffmpeg.org/faq.html#How-can-I-join-video-files_003f)

---

### Post by jejeman on 2013-02-07
Well this concat filters are new to me. Maybe it is a new thing in ffmpeg.

Cool, looks like it could do the job. It only needs a test with AAC in m4a.

---

### Post by n3mmr on 2013-02-07
> **FakeOutdoorsman said:**
> You can join in ffmpeg with the *concat* demuxer, protocol, or filter. Refer to [How can I join video files?]("http://ffmpeg.org/faq.html#How-can-I-join-video-files_003f")

As I read that documentation, reencoding is unavoidable. Am I wrong in interpreting the doc in that way?

---

### Post by jejeman on 2013-02-07
It says> 
FFmpeg has a concat demuxer which you can use when you want to avoid a re-encode and your format doesn’t support file level concatenation. So, this option is what you should try.

---

### Post by n3mmr on 2013-02-08
> **jejeman said:**
> It saysSo, this option is what you should try.
format there, is that the "container" format, then????

OK, so this might be the way forward. Thanks.


I STILL wish there was a graphical native aac editor. I suppose I'd have to buy a MAC for that.

---

### Post by jejeman on 2013-02-08
I've tested ffmpeg and it works, but you need the latest version. The version I've tested is from Januray 2013. This concat demuxer was introduced something like in december 2012.

This was my parts
```
Format                                   : MPEG-4
Format profile                           : Apple audio with iTunes info
Codec ID                                 : M4A 
Audio
ID                                       : 1
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format profile                           : LC
Codec ID                                 : 40
Duration                                 : 10s 8ms
Bit rate mode                            : Variable
Bit rate                                 : 225 Kbps
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 44.1 KHz
Compression mode                         : Lossy
```
I've used this command to cut/split the files
```
ffmpeg -i orig_file.m4a -ss 70 -t 7.6 -acodec copy part.m4a
```-ss is seek in seconds. -t is duration in seconds.

To join the parts
1. Make the list of parts - plain ASCII file, I named it "input.txt"
```
file ./part.m4a
file ./part2.m4a
file ./part3.m4a
```As you can see the format is "file /path/to/file.m4a"
2. run the command
```
./ffmpeg -f concat -i input.txt -c copy out.m4a
```The files are joined (concatenated) gaplessly.
This is how out file looks
```
General
Complete name                            : out.m4a
Format                                   : MPEG-4
Format profile                           : Apple audio with iTunes info
Codec ID                                 : M4A 
File size                                : 861 KiB
Duration                                 : 32s 594ms
Overall bit rate mode                    : Variable
Overall bit rate                         : 216 Kbps
Writing application                      : Lavf54.61.104

Audio
ID                                       : 1
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format profile                           : LC
Codec ID                                 : 40
Duration                                 : 32s 594ms
Bit rate mode                            : Variable
Bit rate                                 : 215 Kbps
Maximum bit rate                         : 225 Kbps
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 44.1 KHz
Compression mode                         : Lossy
Stream size                              : 854 KiB (99%)
```
Well, it is not much, but it can get the job done. You will spend most of the time in cutting the parts, joining is instant.

Here is the documentation
[http://ffmpeg.org/trac/ffmpeg/wiki/How%20to%20concatenate%20%28join%2C%20merge%29%20media%20files](http://ffmpeg.org/trac/ffmpeg/wiki/How%20to%20concatenate%20%28join%2C%20merge%29%20media%20files)

---

### Post by FakeOutdoorsman on 2013-02-08
> **jejeman said:**
> Here is the documentation
[http://ffmpeg.org/trac/ffmpeg/wiki/How%20to%20concatenate%20%28join%2C%20merge%29%20media%20files](http://ffmpeg.org/trac/ffmpeg/wiki/How%20to%20concatenate%20%28join%2C%20merge%29%20media%20files)

Good to see that you figured it out.

Just to clarify that is Community Contributed Wiki Documentation, but there is also the official documentation for the ffmpeg [concat demuxer](http://ffmpeg.org/ffmpeg-formats.html#concat).

---

