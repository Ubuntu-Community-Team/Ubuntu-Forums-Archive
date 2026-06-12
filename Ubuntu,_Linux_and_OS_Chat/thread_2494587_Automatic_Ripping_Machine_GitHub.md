---
title: "Automatic Ripping Machine GitHub"
date: 2024-01-20
forum: Ubuntu, Linux and OS Chat
---

### Post by p2ranger on 2024-01-20
There is a project on GitHub called [Automatic Ripping Mahcine]("https://github.com/automatic-ripping-machine/automatic-ripping-machine"). It is to automate ripping of DVDs and CD's onto your computer. Does anyone here have experience with getting it to run on Ubunutu? I have an Ubuntu server at home. I've tried installing the software, but I'm not getting anywhere to get it to run. Just not sure where to go to look for tutorials or support. Thanks

Jason

---

### Post by Dennis N on 2024-01-20
Did you see the "Getting Started" info?
[https://github.com/automatic-ripping-machine/automatic-ripping-machine/wiki/Getting-Started](https://github.com/automatic-ripping-machine/automatic-ripping-machine/wiki/Getting-Started)

---

### Post by #&amp;thj^% on 2024-01-20
They have changed things over the years, and it looks now a KVM with "arm support will be needed".

This sounds very complex now, and i wouldn't touch it due to the hardware needed just to run the docker install.

That's just my opinion though. The concept was good a couple of years ago. I used it then but as I said it not worth it for my needs today.

I guess I could point you to a more readable step by step: [https://blog.lohannes.com/2018/08/automatic-disk-ripping-machine-full.html](https://blog.lohannes.com/2018/08/automatic-disk-ripping-machine-full.html)
NOTE: That date is form 2018.

---

### Post by TheFu on 2024-01-23
I've never used that tool.

For music CDs, I use **abcde** with a little script wrapper.
```
#!/bin/bash

abcde -a cddb,read,encode,tag,move,clean -d /dev/cdrom \
      -j 4  -o flac,vorbis:"-q 6" -V -x
```

I re-ripped my audio CD collection a few years ago. Originally, I'd ripped most of it in the late 1990s.  Times have changed and things are much easier/faster now. I think an audio CD takes about 5 minutes to process these days.  As for organization into directories, I use some custom scripts that pull the ID3 tags from the music files directly, create directories based on it and create m3u playlists for the directory/album.
```
genre/artist/album/XX-Track_Title.ogg
```
There's also EasyTag, but sometimes it is buggy.  I never have spaces or odd characters in filenames. It cannot be allowed.

For DVDs, well, I haven't ripped any recently, but if I want everything and don't want to transcode, I used **vobcopy**.  If I just want the main tittle and transcode using h.264 or h.265 encoding, then I'd use **Handbrake**. Handbrake has presets or you can create your own.  I think the last time I ripped a DVD was probably 2017-ish.

I prefer vorbis for audio (music and videos), so my custom presets transcode any multi-channel audio into vorbis quality of 6 (about 192Kbps) which my ears cannot tell from a flac 100% rip.  Vorbis does an excellent job at maintaining quality audio, like the newer AAC, but without licenses or patents. Vorbis is supported in all modern browsers and on Android for a very long time too.  

We don't have any bluray in the house. Dealing with those is much, much, much harder on Linux. There is a commercial tool, **makemkv** for Blurays.  It can also handle some aggressive DRM on DVDs that vobcopy is confused over.

If you are doing your whole collection, it is just like eating an elephant.  1 bite at a time and consistency is the trick.  This last time, I retained the flac, so I don't plan to ever need to rip the CDs again, should I desire to transcode to some more efficient audio codec in the future.  

That reminds me, I have 6 CDs trapped inside my car 6-disc changer that I need to get out.  Hard to believe I've been without Back In Black nearly 20 yrs and only have the mp3 transcodes from 1999. Eeeew.

---

### Post by Tadaen_Sylvermane on 2024-01-25
You can use Handbrake from the command line. Maybe a python or shell script and away it goes. Shouldn't be to complicated. Don't need a special tool.

---

### Post by TheFu on 2024-01-26
> **Tadaen_Sylvermane said:**
> You can use Handbrake from the command line. Maybe a python or shell script and away it goes. Shouldn't be to complicated. Don't need a special tool.

I use to use handbrake cli. The problem is that different inputs require different settings to get the best outcome. I had 10 different handbrake-cli profiles, each with different settings and had to figure out which should be used, when.  I scripted about 4 of those, since the choice was dependent on the true cropping needed.  The handbrake auto-crop isn't always correct.  Eventually, it was too much hassle and I just used the GUI to load up a number of handbrake batch processes to run overnight.

There are times when "some" encoding is fine and I use 2 scripts for that today.  One does h.264 encoding and the other does h.265 encoding. Neither do cropping. Both are for "watch once" things - so mostly TV recordings.  In the scripts, I can retain the existing resolution or scale to 720p which still looks good, but uses 50% less space than the source and is easier to playback across all my devices.  720p h.264 encodings take about 20 minutes for an hour show, whereas h.265 encodings take a little longer than playback of the show to encode - about 65m for an hour show. Not worth it for watch-once encodings.  

I need to find the way to get a GPU involved in h.265 encoding, if that is possible with my hardware AND the results are good enough.  I suspect my GPUs are all too low-end for that, however.

---

### Post by sarfaraj23n on 2024-02-15
That&#8217;s exactly my setup. I stack them three high- they are sturdy and don&#8217;t wobble or make noise. The footprint is actually very small. I use a MacBook Pro with 4 usb c ports. The fourth port I use for my charger cable. I rip three dvds at a time and can usually get through about 6 rips per hour. Ps- I bought the superdrives used off eBay for a little less than half the retail price[9apps apk]("https://9apps.ltd/dl/")

---

### Post by TheFu on 2024-02-15
> **TheFu said:**
>  I need to find the way to get a GPU involved in h.265 encoding, if that is possible with my hardware AND the results are good enough.  I suspect my GPUs are all too low-end for that, however.

I figured out how to use the GPU and to both h.264 and h.265 transcoding of videos. It runs between 3 and 20x faster, depending on the video codec used.  The file output sizes and quality for the same size aren't anywhere as good as what Handbrake creates. There are fewer supported options with the hardware encoders, it seems.  OTOH, it is nice NOT to see a CPU pegged for 30-60 minutes during transcoding.

I have a Ryzen 5600G. Using the iGPU for transcoding.
Recorded a Nature show off PBS last night.  62 minute recording.  The recording was OTA at 1920x1080 with mpeg2/ac3 in a TS container.  4.0 GB in size.  PBS only has commercials at the beginning and end of each show. I won't bother removing the leading/trailing commercials. It is just a watch-once show anyway.

Kicked off transcoding from mpeg2 to h.264 this morning - keeping the original resolution.  3MB/sec is the way to control the quality of the transcode.  Should be fine.  
It is running at 3.95x speed. So the full transcode will finish in about 15 minutes.  Resolution is the main part of the "how long will this take" question.
Top shows the CPU 96+% idle.
```
load average: 0.58, 0.57, 0.58
%Cpu(s):  0.8 us,  0.6 sy,  1.2 ni, 97.4 id,  0.1 wa,  0.0 hi,  0.0 si,  0.0 st
```
If the CPU was being used, it would be 95% used and the load averages would be close to 12 (there are 12 cores).

Finished. Time says it was 
```
real    15m36.074s
user    2m13.755s
sys     0m8.003s
```

The resulting h.264 file is 1.5G in size. I convert the AC3 stereo into 2-channel Vorbis audio as well.  Comparing a few frames, the transcode is beautiful.

For fun, transcoded to h.265 as well, using the GPU. It is running at the same speed - just under 4x too, which surprises me. speed=3.92x
```
real    15m44.569s
user    2m17.008s
sys     0m10.169s
```
So h.265 transcoding time was about the same.
```
$ \du N*v
1554576 Nature-Attenborough_and_the_Jurassic_Sea_Monster-hevc-long.mkv
4146688 Nature-Attenborough_and_the_Jurassic_Sea_Monster-huge-mpg.mkv
1554404 Nature-Attenborough_and_the_Jurassic_Sea_Monster-long.mkv

```
Both use 3MB/sec as the maxrate, so the file sizes are the same. In theory, h.265 could use a lower bitrate for the same quality.  When I tested using 2MB/sec, there were artifacts with h.265.  Anyway, the result of the transcode is beautiful too.

```
Type      h:m:s   VCodec     WxH     VRate  ACodec  AChan Filename
-------- -------- ------  ---------  -----  ------  ----- --------
lavfpref    62:00   hevc  1920:1080  29.97   VORB   2     Nature-Attenborough_and_the_Jurassic_Sea_Monster-hevc-long.mkv
lavfpref    62:00  mpeg2  1920:1080  29.97    ac3   2     Nature-Attenborough_and_the_Jurassic_Sea_Monster-huge-mpg.mkv
lavfpref    62:00   h264  1920:1080  29.97   VORB   2     Nature-Attenborough_and_the_Jurassic_Sea_Monster-long.mkv

```
I'm using Vorbis quality 6 (192Kbps) for audio. That, to me and many "audio experts", is indistinguishable from the source audio.  I can't tell the difference between FLAC lossless audio and Vorbis at 192Kbps. I've tried. Can't.

BTW, the instructions I followed were in the Jellyfin HW Transcoding how-to.  I was surprised how easy it was to setup.  The HW transcoding also works in jellyfine. [https://jellyfin.org/docs/general/administration/hardware-acceleration/amd/](https://jellyfin.org/docs/general/administration/hardware-acceleration/amd/)  There are instructions there for Intel and Nvidia GPUs too, but I didn't look at them at all.

The scripts I use to batch encode are pretty trivial, just with lots of options that I don't want to type over and over and over. The transcode lines are very similar.
[LIST]
[*]h.264
```
    nice /usr/lib/jellyfin-ffmpeg/ffmpeg \
          -hwaccel vaapi \
          -hwaccel_device /dev/dri/renderD128 \
          -hwaccel_output_format vaapi \
          -i  "${file}" \
          -map 0 \
          -c:v **h264_vaapi** -b:v 3M -maxrate 3M \
          -c:a libvorbis -q:a 6 \
        "${new}-long.mkv"

```
[*]h.265
```
    nice /usr/lib/jellyfin-ffmpeg/ffmpeg \
          -hwaccel vaapi \
          -hwaccel_device /dev/dri/renderD128 \
          -hwaccel_output_format vaapi \
          -i  "${file}" \
          -map 0 \
          **-vf 'scale_vaapi=format=p010'** \
          -c:v **hevc_vaapi -profile:v 2** -b:v 3M \
          -c:a libvorbis -q:a 6 \
        "${new}-hevc-long.mkv"

```
[*]h.264 using the CPU
```
    nice /usr/lib/jellyfin-ffmpeg/ffmpeg -y -i  "${file}" \
       -map 0  -vcodec **libx264** -crf 19.5 \
       -preset **medium** -c:a libvorbis -q:a 6 \
       "${file}.medium.long.mkv"

```
[/LIST]
I wish the crf (quality) setting could be used with the HW encoding. 

For archival, I still use handbrake and the CPU for encoding, usually with a 19.5 or 20 crf setting. I don't like artifacts. My ffmpeg SW encoding tests have never resulted in the same quality + small file size as what handbrake creates and certainly not as easily.  I tested using all the "presents" for h.264 and was using "faster" as the watch-once setting. The time to encode with it was significantly faster than on medium and actually smaller than the "fast" preset for the same quality.

The "best" codec and transcoding method for your needs depends on the playback devices, quality demands, source material and how sensitive you are to file size. Since every DVD, every OTA recording, every Bluray are different sources with different encodings, there's no single answer for all inputs, all needs.

Anyway, probably more information than anyone wants. Hope it is useful to someone.

---

### Post by #&amp;thj^% on 2024-02-15
> **TheFu said:**
> 

Anyway, probably more information than anyone wants. Hope it is useful to someone.
Nope just right.
I've now setup jellyfin, still in the fine tune stage ATM

---

