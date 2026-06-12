---
title: "Raspberry Pi and ffmpeg"
date: 2016-03-01
forum: Ubuntu/Debian BASED
---

### Post by coldraven on 2016-03-01
Has anyone compiled ffmpeg for the PI and  is willing to share it? I also need a link to using ffmpeg for screen video capture, I've used it in the past but have lost the script somewhere.
TIA

---

### Post by QDR06VV9 on 2016-03-01
Hey coldraven I have used this twice on friends PI devices..with good success.[URL="http://www.jeffreythompson.org/blog/2014/11/13/installing-ffmpeg-for-raspberry-pi/"]
[/URL][http://www.jeffreythompson.org/blog/2014/11/13/installing-ffmpeg-for-raspberry-pi/](http://www.jeffreythompson.org/blog/2014/11/13/installing-ffmpeg-for-raspberry-pi/)



Streaming Guide
[https://trac.ffmpeg.org/wiki/StreamingGuide](https://trac.ffmpeg.org/wiki/StreamingGuide)

---

### Post by coldraven on 2016-03-02
> **runrickus said:**
> Hey coldraven I have used this twice on friends PI devices..with good success.[URL="http://www.jeffreythompson.org/blog/2014/11/13/installing-ffmpeg-for-raspberry-pi/"]
[/URL][http://www.jeffreythompson.org/blog/2014/11/13/installing-ffmpeg-for-raspberry-pi/](http://www.jeffreythompson.org/blog/2014/11/13/installing-ffmpeg-for-raspberry-pi/)



Streaming Guide
[https://trac.ffmpeg.org/wiki/StreamingGuide](https://trac.ffmpeg.org/wiki/StreamingGuide)


I had seen that blog but step 2 is a bit vague. I'm a bit clueless with all those codec formats. But thanks anyway, I'll give it a go.

---

### Post by QDR06VV9 on 2016-03-02
I should have mentioned I skipped Step 2 and no real show stoppers have happened..
But I should mention here that if the need comes up to trans-code MPEG-2 content..well Transcoding this content is not a practical option for HD MPEG2 content.   It takes a very long time to convert a 1080i MPEG2 program to H.264. That's about all I can warn on for now at least.
Oh I forgot for screen capture with ffmpeg use this command:
```
ffmpeg -video_size 1920x1080 -framerate 30 -f x11grab -i :0.0 -c:v libx264 -qp 0 -preset ultrafast capture.mkv

```
I will kind of watch this thread coldraven to see if things are going well for you..Not that I am an expert on the PI's but sometimes 2 heads are better...LOL
Kind Regards

---

### Post by coldraven on 2016-03-04
> **runrickus said:**
> I should have mentioned I skipped Step 2 and no real show stoppers have happened..
But I should mention here that if the need comes up to trans-code MPEG-2 content..well Transcoding this content is not a practical option for HD MPEG2 content.   It takes a very long time to convert a 1080i MPEG2 program to H.264. That's about all I can warn on for now at least.
Oh I forgot for screen capture with ffmpeg use this command:
```
ffmpeg -video_size 1920x1080 -framerate 30 -f x11grab -i :0.0 -c:v libx264 -qp 0 -preset ultrafast capture.mkv

```
I will kind of watch this thread coldraven to see if things are going well for you..Not that I am an expert on the PI's but sometimes 2 heads are better...LOL
Kind Regards

Thanks for the info :) This is for a friend who lives on another island, I have not gone there yet so results will be slow. Hopefully I'll post back next week.

---

