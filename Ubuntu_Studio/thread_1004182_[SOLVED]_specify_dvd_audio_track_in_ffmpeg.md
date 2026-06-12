---
title: "[SOLVED] specify dvd audio track in ffmpeg?"
date: 2008-12-07
forum: Ubuntu Studio
---

### Post by blakecraw on 2008-12-07
I'm using ffmpeg to back up some dvds, but I can't find how to make it read a specific audio track on the .vob file.

This would be alright, but on one dvd I have ffmpeg defaults to the spanish track, so how do I specify a different one?

also, I will be using ffmpeg for this, so please don't tell me how to do it with mencoder :)


edit: when I ripped the .vob I used 

mplayer -aid 128 (which does indeed play the english track) to dump the stream, but I still get a .vob that plays with spanish audio.

---

### Post by FakeOutdoorsman on 2008-12-07
You need to use the map option.  A good explanation is at [Using ffmpeg to manipulate audio and video files]("http://howto-pages.org/ffmpeg/#map").  I've never used "mplayer -aid 128" before.  I have good experiences with vobcopy.

---

### Post by blakecraw on 2008-12-07
> **FakeOutdoorsman said:**
> You need to use the map option.

Perfect, thanks.

Now, I have a follow-up question.

I'm now trying to use the -map option to grab a subtitle stream, but it seems to be at twice the fps as the movie, so I get this:

"Seems stream 0 codec frame rate differs from container frame rate: 29.97 (30000/1001) -> 59.94 (60000/1001)"

The audio and video alone work, but throwing in subtitles causes it to fail. So, how do I change the fps of the subtitle stream, or otherwise fix this?

---

### Post by FakeOutdoorsman on 2008-12-07
I'm not going to be much help because I have no experience with subtitles.  You may have to use mencoder.  Also, avidemux has some subtitling functionality.  andrew.46 has a good mplayer / mencoder guide and might be able to help:

[[Howto] Successfully install the svn mplayer + gmplayer + all the codecs]("http://ubuntuforums.org/showthread.php?t=558538")

---

### Post by blakecraw on 2008-12-07
Alright, thanks.

---

