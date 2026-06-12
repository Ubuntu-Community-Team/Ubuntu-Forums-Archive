---
title: "How to use Theroa Encoder (using libtheora-bin package)"
date: 2008-09-10
forum: Ubuntu Studio
---

### Post by Vyoma on 2008-09-10
After a bit of digging around, I found (I assume) libtheora-bin package has a Theora video encoder. Unfortunately, I was unable to find the man pages or even which command(binary) is contained in this package. 

A link to its document would be much appreciated.

In particular, here is what I want to do:
- Encode a series of images to video file(s)
- Screen capture using RecordMyDesktop
- Concatenate all the video files to a single file

I would like to do all these with as little steps as possible to preserve the details. I am stuck with Theora because RecordMyDesktop is able to output only to Theora, and I found troubles with frame-rate when I tried 'XVidCap Screen Capture'.

Basically, I want to do a couple of screen captures - and string them along with few images to create one video, with best possible quality. (Hence, I am focusing on reducing the number of steps - as repeated encoding would repeatedly degrade the quality).

I am welcome to any suggestions for alternative workflow too.

**Edit:**
Doh! I found the command by examining the bin folder:
```
/usr/bin$ **ls -1 | grep theora**
theora_dump_video
[COLOR="DarkGreen"]theora_encoder_example[/COLOR]
theora_player_example
```

But it seems like I cannot encode a series of image into a Theora video:
```
/usr/bin$ **theora_encoder_example -help**
theora_encoder_example: invalid option -- h
Usage: encoder_example [options] [audio_file] [COLOR="Red"]video_file[/COLOR]

Options: 
........
........
encoder_example accepts only uncompressed RIFF WAV format audio and
YUV4MPEG2 uncompressed video.


```
Seems like it takes only a video file as input.

---

### Post by eye208 on 2008-09-11
> **Vyoma said:**
> After a bit of digging around, I found (I assume) libtheora-bin package has a Theora video encoder. Unfortunately, I was unable to find the man pages or even which command(binary) is contained in this package. 

A link to its document would be much appreciated.
libtheora is a library, not an application. ffmpeg2theora is the package you are looking for.

> I am stuck with Theora because RecordMyDesktop is able to output only to Theora
Blender's integrated video editor can read and transcode Theora files. The best practice is to record at the highest possible quality setting (will result in large files), edit, then export to a format suitable for distribution. Theora's quality at low bitrates is rather poor (although it's about to improve with the latest codec revisions) and most online video portals don't support it anyway. I recommend exporting to MP4 (H.264, AAC).

---

### Post by Vyoma on 2008-09-11
> **eye208 said:**
> libtheora is a library, not an application. ffmpeg2theora is the package you are looking for.
...
Yes indeed. But as I mentioned above, there is another packcage **libtheora-bin** which seems to contain 'bin's that uses the libraries from libtheora.

> **eye208 said:**
> ...
Blender's integrated video editor can read and transcode Theora files. The best practice is to record at the highest possible quality setting (will result in large files), edit, then export to a format suitable for distribution. Theora's quality at low bitrates is rather poor (although it's about to improve with the latest codec revisions) and most online video portals don't support it anyway. I recommend exporting to MP4 (H.264, AAC). Ah! I did not try yet with MP4(H.264) - going to try that.

---

### Post by CmmBinoo on 2008-09-12
**[[color=red]Buy Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Test drive our brand new real-time traffic estimator and create your campaign. Choose text, banner, or interstitial ads. Target by site, keyword, demographic. Create or upload multiple ads. **[[color=red]Sell Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Find out how we can help you generate more revenue from your ad space. Customize ads to match your site Approve and reject ads for your site Works alongside other ad programs [**[size=3][color=red]Make money online,now![/color][/size]**[color=#0000cc][/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)

---

