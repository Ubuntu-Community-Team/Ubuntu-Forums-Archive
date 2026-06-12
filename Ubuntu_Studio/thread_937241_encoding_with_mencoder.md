---
title: "encoding with mencoder"
date: 2008-10-03
forum: Ubuntu Studio
---

### Post by lrudor on 2008-10-03
First post on ubuntu forums, great os I must admit ;)
here is my issue:
I am attempting to re-encode a video with mencoder on ubuntu 8.04 (64 bit if it matters) from mkv to mp4 

so I extracted the h264 and audio streams from the mkv
changed "67 64 00 33" to "67 64 00 29" using hexedit, no problems

I then re-encode the video to something smaller:

```

mencoder "/videos/toencode/test.h264" -o "/videos/encoded/test.temp.264"  -passlogfile "/videos/encoded/test.temp.log" -vf scale=848:480 -nosound -ovc x264 -x264encopts bitrate=1200:frameref=8:bframes=3:b_adapt:b_pyramid:weight_b:partitions=all:8x8dct:me=umh:subq=6:trellis=2:brdo:threads=auto:pass=1:analyse=all -ofps 23.976

```

and

```

mencoder "/videos/toencode/test.h264" -o "/videos/encoded/test.temp.264"  -passlogfile "/videos/encoded/test.temp.log" -vf scale=848:480 -nosound -ovc x264 -x264encopts bitrate=1200:frameref=8:bframes=3:b_adapt:b_pyramid:weight_b:partitions=all:8x8dct:me=umh:subq=6:trellis=2:brdo:threads=auto:pass=2:analyse=all -ofps 23.976

```

ok, spends about 1 hour doing that. no problem

I use encode the audio using neroAacEnc

now here is where I start getting issues:

```

MP4Box -fps 23.976 -add test.264 -add audio.mp4 output.mp4

```

mp4 box:

```

Cannot find H264 start code
Error: BitStream Not CompliantError importing test.264: BitStream Not Compliant

```

I have been looking for 2 days on how to solve this issue, but have not come across anything on how to fix this. if someone could tell me what I am doing wrong that would be great ^^. (I can play the video fine in vlc so I don't know why MP4Box hates it so much...)

Thanks for your help :D

---

### Post by eye208 on 2008-10-06
> **lrudor said:**
> so I extracted the h264 and audio streams from the mkv
No need to do that. MEncoder can read MKV files too.

> changed "67 64 00 33" to "67 64 00 29" using hexedit, no problems
What was that for?

> now here is where I start getting issues:

```

MP4Box -fps 23.976 -add test.264 -add audio.mp4 output.mp4

```

mp4 box:

```

Cannot find H264 start code
Error: BitStream Not CompliantError importing test.264: BitStream Not Compliant

```

I have been looking for 2 days on how to solve this issue, but have not come across anything on how to fix this. if someone could tell me what I am doing wrong that would be great ^^.
The .264 extension makes MP4Box expect a raw H.264 bitstream. By default the output of MEncoder will always be AVI unless you specify something else using the -of option. For raw stream output use "-of rawvideo".

Of course there is no need to do all the encoding again. MP4Box has an option to extract bitstreams from AVI files.

---

### Post by lrudor on 2008-10-06
> **eye208 said:**
> No need to do that. MEncoder can read MKV files too.
 ok, will have to try that.
> 
What was that for?

No idea, I read that it was needed in order to change from mkv to mp4

> 
The .264 extension makes MP4Box expect a raw H.264 bitstream. By default the output of MEncoder will always be AVI unless you specify something else using the -of option. For raw stream output use "-of rawvideo".

Of course there is no need to do all the encoding again. MP4Box has an option to extract bitstreams from AVI files.

ok, will have to re-encode it with the "-of rawvideo" command and see how it goes.

Thanks for your help.

---

### Post by eye208 on 2008-10-07
> **lrudor said:**
> ok, will have to re-encode it with the "-of rawvideo" command and see how it goes.
I just said there is no need to re-encode.

Your existing file "test.264" is an AVI file. You can use MP4Box to extract the raw H.264 bitstream from it and put that into an MP4 container.

---

### Post by lrudor on 2008-10-07
Sorry, I was re-encoding to get to a smaller file size. 

and when I try and just do the mkv file directly Mencoder gives me a segmentation fault.

---

### Post by Railsbuntu on 2008-11-09
Can someone write down the steps to do that, I don't understand anything at all. I have encoded a file with mencoder using x264, the file is output.avi

I extracted the video and audio with mplayer to output.h264 and output.aac, now trying to remux them in an mp4 file using mp4box gives me the error message: Error importing output.h264: BitStream Not Compliant

So what to do now that I have all these files?

EDIT: it seems mplayer doesn't seem to produce valid streamsn when demuxing: [http://forum.doom9.org/showthread.php?t=102064]("http://forum.doom9.org/showthread.php?t=102064")

Can I use mp4box to do that instead then remux after?

---

