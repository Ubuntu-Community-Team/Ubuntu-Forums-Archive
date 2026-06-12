---
title: "Applying mencoder options?"
date: 2009-10-06
forum: Ubuntu Studio
---

### Post by Vadi on 2009-10-06
I'd like to apply the "subq=5:8x8dct:frameref=2:bframes=3:b_pyramid:weight_b" options the h264 codec has when encoding with mencoder, but I'm not sure where to stick it into the line.

Trying something like

> mencoder -demuxer y4m - -ovc x264 -x264encopts subq=5:8x8dct:frameref=2:bframes=3:b_pyramid:weight_b -audiofile audio2.wav -oac mp3lame -o video2.avi

Gave me a "Cannot find codec matching selected -vo and video format 0x32315659.".

(the video is pipied to mencoder)

---

### Post by VertexPusher on 2009-10-07
> **Vadi said:**
> Gave me a "Cannot find codec matching selected -vo and video format 0x32315659.".
This is usually the result of an error that happened earlier in the MEncoder filter chain. Check the output above that message.

However, storing H.264 video in AVI is a bad idea anyway. How about using MKV instead?

You can feed YUV4MPEG streams into the command line x264 encoder. This will give you access to some additional codec options which are not accessible through MEncoder yet. x264 can output MKV files.

You can use FAAC to encode the WAV file to AAC. If you pass the -w parameter to FAAC, it will wrap the AAC stream in a standard MP4 container. Use mkvtoolnix (CLI or GUI) to mux the H.264 file with the AAC file. The resulting MKV file will be compatible with "DivX Plus"-certified consumer electronics. Check out the DivX website for more info.

---

### Post by Vadi on 2009-10-07
Thanks, I'll give it a go. No particular affections, just trying to get a good quality and filesize for my videos.

---

### Post by Vadi on 2009-10-08
edit: nevermind, misread

---

### Post by Vadi on 2009-10-18
Can you recommend any guides on x264 itself and optimization?

I've been tinkering with the different "tunes" it gives, and it seems that ssim one gives the best filesize for good quality - until I discovered that doing two passes makes it even better. Wondering if there is a more optimal way to find this out...

---

### Post by VertexPusher on 2009-10-19
Encoding with x264 is always a compromise between speed and quality. If you max out the motion estimation settings (me, me-range and subme), you'll get a very good quality/bitrate ratio, but you'll wait ages for the encode to finish. So the "best" setting depends on what you want, and how long you are willing to wait for it.

2-pass mode is a waste of time. I would recommend 1-pass CRF mode unless there are file size constraints of some sort.

Note that some encoding options can make the resulting file incompatible with Quicktime, iPod, PS3, Xbox 360 and/or other hardware media players. H.264 is a complex format with many profiles and levels. If you require compatibility with a particular class of devices, find out which profile/level it supports, and then choose encoding options accordingly.

---

### Post by Vadi on 2009-10-19
Yes, there are file size constraints - my videos are from 40min to an hour, and I need to upload them to a streaming website after that.

What would you recommend to optimize on the filesize while keeping the quality decent? (in some experiments there would be huge blur that would get periodically fixed, and I don't like that kind of quality).

---

### Post by VertexPusher on 2009-10-20
You can either control file size or quality, but not both. If you use 2-pass encoding, the encoder will give you the best possible quality at a given file size, but if that size is too small for the given duration of the video, quality will be bad anyway. On the other hand, 1-pass CRF encoding will guarantee a constant level of quality, and the encoder will make the file just as large as necessary to get there.

If quality is important to you, 1-pass CRF is the preferable mode. But you may have to split up the file afterwards to meet the size requirements of the upload site.

---

### Post by Vadi on 2009-11-01
>         --crf <float>
               Quality-based VBR (nominal QP)

What does the number range from?

Also, how can I make it auto-pad such that compression will not suffer? I tried giving a compatible resolution but it is not happy:

> vadi@vadi-laptop:~$ x264 --pass 1 --crf 1 -o video-twopass2.mkv test2.y4m **720x464**
yuv4mpeg: 720x450@30/1fps, 0:0
x264 [warning]: width or height not divisible by 16 (**720x450**), compression will suffer.


---

