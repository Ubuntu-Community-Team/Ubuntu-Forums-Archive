---
title: "noob  q?  how to save youtube vid?"
date: 2007-07-16
forum: The Cafe
---

### Post by silent1643 on 2007-07-16
how the hell do i save a you tube video file? i assume its flv

---

### Post by FuturePilot on 2007-07-16
[https://addons.mozilla.org/en-US/firefox/addon/2390]("https://addons.mozilla.org/en-US/firefox/addon/2390")
:)

---

### Post by silent1643 on 2007-07-16
love you long time

---

### Post by kiddo on 2007-07-16
or you could use the command-line tool "youtube-dl", available in synaptic.

I use it all the time, and then I convert the videos to an Open format, ogg theora, by doing
```
ffmpeg2theora --sync --optimize something.flv
```

---

### Post by shen-an-doah on 2007-07-16
Or you can try Democracy player: [http://www.getdemocracy.com/](http://www.getdemocracy.com/)

It allows you to search, download and play Youtube videos all in one player.

---

### Post by Dark Aspect on 2007-07-16
Jesus,why would you want to save youtube videos the quality is horrible.

---

### Post by stmiller on 2007-07-17
Lots of people have made scripts to download youtube vids, using wget.  If you want to really get your geek on and impress the ladies:

[http://mmassonnet.blogspot.com/2007/03/wanna-download-youtube-video.html](http://mmassonnet.blogspot.com/2007/03/wanna-download-youtube-video.html)

---

### Post by Dimitriid on 2007-07-17
> **Dark Aspect said:**
> Jesus,why would you want to save youtube videos the quality is horrible.

Availability.

---

### Post by Polygon on 2007-07-17
you can also use vixy.net

if it keep giving you errors like cant resolve, header error, keep trying and eventually it will work.

---

### Post by aidanr on 2007-07-17
or [keepvid.com]("http://keepvid.com")

---

### Post by aimran on 2007-07-17
> **Dark Aspect said:**
> Jesus,why would you want to save youtube videos the quality is horrible.

Using ffmpegtheora I'm able to get better a higher quality .ogg vid than in the .flv format.

---

### Post by Polygon on 2007-07-17
> **aimran said:**
> Using ffmpegtheora I'm able to get better a higher quality .ogg vid than in the .flv format.

how do you take something thats low quality and then magically make it better quality?

---

### Post by free10 on 2007-07-22
> **Polygon said:**
> how do you take something thats low quality and then magically make it better quality?



Let me try that one and I am not saying it is true because I don't know and the only coding I have done is with html, but with that said I may write html for a page and it looks great with one encoder (browser), but terrible with another encoder (browser), soooo the encoding quality in does not always match the "decoding" software coming back out on the quality of the end product. The FLV encoding of sound/music may be much better than what we think it is, because we are judging it off the quality of the decoding which normally might not be that great. Different decoding and then "translation" might result, just in theory, of decoding and capturing what actually was encoded there, and then the end result might be far better. I don't know anything about doing this type of software but just looking at the difference with html decoding quality I can see where this might be true.

Now with a flv file I have just been using Kino and opening them with Kino and then translating to DVI-avi (import), and then using Kino to turn the DVI-avi into regular MPEGs, which anything can play. Slow process and bigger files though, but it works and it is simple. There are probably are better and faster ways though. Right now converting just a 20mb flv into the avi that is then coverted into a huge 1.2 GIG DV file. The DV file sounds bad in Kino on my lowlly hardware with Ubuntu 6.06 and skips and pops, but stripping just the audio out of Kino' DV file using the Lame MP3 choice under audio sounds fine and was a 5mb file, and playing the same DV file in VLC is better than Kino, but still is not great on sound. Now convert the whole FLV to MPEG and the sound and video is once again OK say in VLC or Totem. This is not fast on my 500mb of ram and 1 gig CPU even with a very fast hard drive using Kino, but Kino offers editing and other things too.

Sound and encoding and decoding it all is not the same, at all, and neither are the results you might see in my experience of playing with this over many different types of software for different operating systems. So yes I can see how a certain level of encoded sound may decode different and recode back at an even better quality level. It just doesn't seem to make sense at first from one perspective--Dwight

---

### Post by ice60 on 2007-07-22
you can just find the file on your HDD too, i do that a lot.

there's a really good firefox extension that i use to find the file on my HDD (although firefox often saves it to /tmp), and it will also show you the url so you can use a download tool like wget to download the file, it's called cacheviewer.

BTW, i'm just cutting and pasteing this (below) from a post i made eariler today if anyone's interested. -

i really like greasemonkey too, i've got 2 GM scripts i use at youtube. one makes the video much bigger automatically and the other puts a download link at the top of the page.
[http://userscripts.org/scripts/show/4037](http://userscripts.org/scripts/show/4037)
[http://userscripts.org/scripts/show/3975](http://userscripts.org/scripts/show/3975)

the screenshot shows the size the script makes the videos and the download link at the top.

[[img]http://xs217.xs.to/xs217/07290/Screenshot_YouTube_Yoga_Mozilla_Firefox.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs217&d=07290&f=Screenshot_YouTube_Yoga_Mozilla_Firefox.png)

---

### Post by original_jamingrit on 2007-07-23
> **silent1643 said:**
> how the hell do i save a you tube video file? i assume its flv

Darn it, silent, look at what you've started :lolflag:

I also use youtube-dl

---

### Post by Footissimo on 2007-07-23
Like Ice, I'll just locate the flash file in /home/[user]/.mozilla/firefox/[profileid]/cache then convert it to somethin more useful (usually an mp4 for the nokia) using [Media Convert](http://media-convert.com/) or one of the zillion different ways to convert video files.

---

### Post by Col-1023 on 2007-09-13
I've tried the firefox plubin and get an error message saying that the url is not valid, even though I can watch the video.

Any ideas?

---

### Post by Col-1023 on 2007-09-13
Here's the error messave I get from the firefox plugin.

[youtube.com] Error: Not a valid URL ([http://www.youtube.com/watch?v=K1MYoEcwfc4](http://www.youtube.com/watch?v=K1MYoEcwfc4)). Visit our web to know in detail what video sites are supported.

I don't know whether the url is valid, but I can watch the video, it's Mondo Rock - Chemistry.

I tried to download it with youtube-dl and it failed, it could log onto the web site but it couldn't get the clip.

Thanks in advance.

---

### Post by solitaire on 2009-09-27
Im using GreaseMonkey with the "Youtube without flash auto" script in FF 3.5. 
Basically it uses your own fave media player instead of the flash player to play youtube videos so you get GOOD fullscreen playback!!! lol

You can also download the video with a single click as well (including HD versions)

---

