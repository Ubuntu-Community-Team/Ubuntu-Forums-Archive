---
title: "MKV to MP4 for XBOX360 - the usual"
date: 2008-08-04
forum: Ubuntu Studio
---

### Post by jcr1 on 2008-08-04
Been trying for too long now to solve this. Tried a handful of scripts... some work some don't. The ones that do work, only partially work.

I have two that almost work perfectly. The one by Jexxie and another I am not sure where from. Interestingly, they both have the same problem.

The resulting mp4 plays with the wrong aspect ratio. They both get squeezed into a format that isn't what the original was. All pixel information is there, but its as if it is being forced into an aspect ratio of 16:9 when the original is wider. 

Although the weird thing is, both original and new MP4 have the same resolution. The new one is just squashed side to side.

Any ideas anyone? Its driving me mad... hate it when I install tons of stuff to try something then it doesn't work, then I feel my system is full of god knows what.

---

### Post by jcr1 on 2008-08-04
I also dont see why this can't be done as simply as something like:

ffmpeg -i input.mkv -vcodec copy -acodec aac -ac 2 output.mp4

Obviously I am no boffin with ffmpeg, but to me thats just copying the h264 video, and converting the audio to 2 channel, AAC. This is what the xbox requires to play.

But it don't seem to work that easy and need a long script to do it.

---

### Post by jcr1 on 2008-08-04
ok bit of progression.

When I do MKVInfo on the original video these items stand out to me:

```

+ Video track
|   + Pixel width: 936
|   + Pixel height: 528
|   + Interlaced: 0
|   + Display width: 1280
|   + Display height: 528

```

So to me the data of the video is 936 x 528, but the "Display width and height" is different... wider.

So when I just extract the video and put it into an MP4 container, obviously it just takes and display a video of 936 width... 

So... how to make it display at 1280 width?

---

### Post by jcr1 on 2008-08-06
bump

---

### Post by rsambuca on 2008-08-13
Try adding the -aspect command into your ffmpeg instructions so that it looks something like this...

```
ffmpeg -i input.mkv -vcodec copy -aspect 2.42 -acodec aac -ac 2 output.mp4
```

I am not an ffmpeg expert, but have been fiddling with it lately to transcode some video files into Xbox360 compatible Xvids for streaming via ushare.  I finally have found something that works reasonably well.

---

### Post by jcr1 on 2008-08-14
> **rsambuca said:**
> Try adding the -aspect command into your ffmpeg instructions so that it looks something like this...

```
ffmpeg -i input.mkv -vcodec copy -aspect 2.42 -acodec aac -ac 2 output.mp4
```

I am not an ffmpeg expert, but have been fiddling with it lately to transcode some video files into Xbox360 compatible Xvids for streaming via ushare.  I finally have found something that works reasonably well.

Am sure I have tried that method, but I will try again...

I am intrigued to know what you have found that has worked!?!

I did find a good script that worked (a different one to jexxie's) but it doesn't take into account the aspect ratio, so if the original video is crap like the one I have, it comes out squashed.

---

### Post by rsambuca on 2008-08-14
I am sure there are some video experts out there that will laugh at my code, but it was basically just put together via trial & error and looking at a lot of different configurations from around the net.  Eventually I tried something that worked, and I will stick with it and tweak it as I go along.  I am astounded at the lack of decent documentation for ffmpeg.  Rather appalling, actually.

Anyways, I was trying to convert an mpg music video into a Xvid for streaming to the 360, and this code seemed to produce OK results.  The reason I am set on using Xvid is that it is also compatible with my Archos portable media player, so now I can view them on TV or on my player.

```
/usr/bin/ffmpeg -i "/media/Fergie - Big Girls Don't Cry.mpg"  -croptop 56 -cropbottom 56 -vcodec libxvid -vtag XVID -aspect 1.87 -maxrate 1200k -b 900k -qmin 3 -qmax 5 -bufsize 4096 -mbd 2 -bf 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -g 300 -acodec libmp3lame -ar 44100 -ab 224k -ac 2 -passlogfile "/media/pass1.log" -pass 1 -y "/media/pass1.avi" && /usr/bin/ffmpeg -y -i "/media/pass1.avi" -vcodec libxvid -vtag XVID -aspect 1.87 -maxrate 1200k -b 900k -qmin 3 -qmax 5 -bufsize 4096 -mbd 2 -bf 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -g 300 -acodec libmp3lame -ar 44100 -ab 224k -ac 2 -passlogfile "/media/pass1.log" -pass 2  "/media/fergietest.avi"
```

---

### Post by jcr1 on 2008-08-15
Wow very long... my code I have been using so far is a fraction of that. There are probably so many variables I could use to improve the quality but I don't think I will ever get round to learning the best way.

Thanks for your help!

---

### Post by cjsimmons on 2008-11-17
> **rsambuca said:**
> I am sure there are some video experts out there that will laugh at my code, but it was basically just put together via trial & error and looking at a lot of different configurations from around the net.  Eventually I tried something that worked, and I will stick with it and tweak it as I go along.  I am astounded at the lack of decent documentation for ffmpeg.  Rather appalling, actually.

Anyways, I was trying to convert an mpg music video into a Xvid for streaming to the 360, and this code seemed to produce OK results.  The reason I am set on using Xvid is that it is also compatible with my Archos portable media player, so now I can view them on TV or on my player.

```
/usr/bin/ffmpeg -i "/media/Fergie - Big Girls Don't Cry.mpg"  -croptop 56 -cropbottom 56 -vcodec libxvid -vtag XVID -aspect 1.87 -maxrate 1200k -b 900k -qmin 3 -qmax 5 -bufsize 4096 -mbd 2 -bf 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -g 300 -acodec libmp3lame -ar 44100 -ab 224k -ac 2 -passlogfile "/media/pass1.log" -pass 1 -y "/media/pass1.avi" && /usr/bin/ffmpeg -y -i "/media/pass1.avi" -vcodec libxvid -vtag XVID -aspect 1.87 -maxrate 1200k -b 900k -qmin 3 -qmax 5 -bufsize 4096 -mbd 2 -bf 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -g 300 -acodec libmp3lame -ar 44100 -ab 224k -ac 2 -passlogfile "/media/pass1.log" -pass 2  "/media/fergietest.avi"
```

I have just tried this command to covert a mkv so I can view it on my 360, but I'm getting and error "Unknown encoder 'libxvid'". What package do I need to install to get his working?? I'm running Ubuntu 8.10. Done a apt-cache search for libxvid and have installed libxvidcore4, but still get the error.

Any ideas??

---

### Post by stooshbunutu on 2008-11-17
you say it's for the xbox360, the new xbox 360 media player allows you to change the aspect ratio of the videos you play anyway, if your connected to LIVE it should have automatically updated about a month ago, even if you only have silver not gold. If no live then I believe you can get it by using the backwards compatability update, download CD.

As for video conversions I just use the WinFF front end for the ffmpeg codec, and it does everything I need it to.

Regards, Michael

---

### Post by FakeOutdoorsman on 2008-11-17
> **cjsimmons said:**
> I have just tried this command to covert a mkv so I can view it on my 360, but I'm getting and error "Unknown encoder 'libxvid'". What package do I need to install to get his working?? I'm running Ubuntu 8.10. Done a apt-cache search for libxvid and have installed libxvidcore4, but still get the error.

Any ideas??

You need the "unstripped" ffmpeg:
```
sudo apt-get update
sudo apt-get purge ffmpeg
sudo apt-get install libavcodec-unstripped-51 libavdevice-unstripped-52 libavformat-unstripped-52 libavutil-unstripped-49 libpostproc-unstripped-51 libswscale-unstripped-0 ffmpeg
```

---

