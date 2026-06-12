---
title: "mpeg 2 swf"
date: 2005-07-09
forum: The Cafe
---

### Post by macewan on 2005-07-09
Has anyone successfully converted an mpeg movie to a flash movie? Such as ->
[this WashingtonPost video](http://www.washingtonpost.com/wp-dyn/content/video/2005/06/02/VI2005060200747.html) <-

---

### Post by macewan on 2005-07-14
[QUOTE=macewan]Has anyone successfully converted an mpeg movie to a flash movie? Such as ->
[this WashingtonPost video](http://www.washingtonpost.com/wp-dyn/content/video/2005/06/02/VI2005060200747.html) <-[/QUOTE]

ffmpeg appears to be what I'm looking to use

---

### Post by Devon001 on 2005-07-15
[QUOTE=macewan]Has anyone successfully converted an mpeg movie to a flash movie? Such as ->
[this WashingtonPost video](http://www.washingtonpost.com/wp-dyn/content/video/2005/06/02/VI2005060200747.html) <-[/QUOTE]

To me it's not that hard.. All you need is Macromedia Flash and import your .mpeg movie and place it on a scene. Then you, Test Scene, after you get the .swf and voila! you got a .swf movie, ofcourse you can add time track.. Even a beginner can do that ;).. You can google it :).. Hope this helps :)

---

### Post by WildTangent on 2005-07-15
[QUOTE=Devon001]To me it's not that hard.. All you need is Macromedia Flash and import your .mpeg movie and place it on a scene. Then you, Test Scene, after you get the .swf and voila! you got a .swf movie, ofcourse you can add time track.. Even a beginner can do that ;).. You can google it :).. Hope this helps :)[/QUOTE]
they dont make flash for linux. in case you didnt notice, this is a linux forum. sorry if im sounding mean, or flamey, but this really doesnt help linux users, or even most windows users, because flash costs many hundreds of dollars.

-Wild

---

### Post by macewan on 2005-07-17
;)

Thanks WildTangent. Devon001, since [Macromedia]("http://www.macromedia.com/") doesn't provide a Linux port of their software I have to rely on the good will of programmers with the knowledge and skill to provide an open alternative to the costly combination of the Windows platform and Dreamweaver MX.

To convert a video from the .mpg format into something suitable for streaming with [Flash Video]("http://www.macromedia.com/devnet/mx/flash/video.html") I used [ffmpeg]("http://ffmpeg.sourceforge.net/index.php") to convert the file. Although not perfect - I have managed as of this morning to create the working example found at the link below.

[http://www.macewan.org/streaming-test/]("http://www.macewan.org/streaming-test/")

---

### Post by macewan on 2005-07-19
I've settled on using a WordPress plugin (modified somewhat) to use the Flowplayer. <a href="http://ffmpeg.sourceforge.net/" title="FFmpeg">FFmpeg</a> is used to convert the .mpg file to the .flv which is then uploaded.

---

### Post by maruchan on 2005-07-19
You could also ask these guys, maybe they can help:

[http://f4l.sourceforge.net/](http://f4l.sourceforge.net/)

---

### Post by Marsellus Wallace on 2006-09-12
**macewan** could you be so kind and post the ffmpeg command you used. Inspired by your result I tried it myself with the following command:
```
ffmpeg -i Hello_my.mpeg Hello_my.swf
```
Unfortunately it didn't work and ended with the following prompt.
```
Unsupported codec for output stream #0.1
```
I woudl be very glad if someone has a solution to my problem.

---

