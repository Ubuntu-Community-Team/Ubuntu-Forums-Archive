---
title: "Still Frames From Movie"
date: 2008-07-27
forum: Ubuntu Studio
---

### Post by startherepodcast on 2008-07-27
Hi,

I saw that you can make a movie from still frames using ffmpeg but what I need is the opposite.

I need to export still frames one by one from a movie. Is this possible? If so how?

Thanks

---

### Post by FakeOutdoorsman on 2008-07-27
From FFmpeg FAQ: [How do I encode movie to single pictures?]("http://ffmpeg.mplayerhq.hu/faq.html#SEC15")
> Use:
```
ffmpeg -i movie.mpg movie%d.jpg
```
The `movie.mpg' used as input will be converted to `movie1.jpg', `movie2.jpg', etc...

Instead of relying on file format self-recognition, you may also use

`-vcodec ppm'
`-vcodec png'
`-vcodec mjpeg'

to force the encoding.

Applying that to the previous example:
```
ffmpeg -i movie.mpg -f image2 -vcodec mjpeg menu%d.jpg
```
Beware that there is no "jpeg" codec. Use "mjpeg" instead.

---

### Post by BLTicklemonster on 2008-07-28
Avidemux has this feature in it.

---

### Post by cotcot on 2008-07-28
Can be done with VLC as well.
Set the snapshot directory in Settings --> Preferences --> Video.
Play the video and pauze where you want the snapshot. Click --> Video --> Snapshot. 

There is also a video editor that converts a video clip in single frames when you load it and want to edit it. After editing it converts the frames again in video. I do not remember which one it was (pitivi , jahshaka , lives ? ... )

---

