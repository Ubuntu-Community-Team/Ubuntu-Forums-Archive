---
title: "Recording computers sound"
date: 2008-09-24
forum: Ubuntu Studio
---

### Post by pwaugh on 2008-09-24
I'd like to record the sound from a youtube video as it plays, or other sounds the computer is making.  I have a webcam with a built in mic, and am wondering how I can do this.

Patrick

---

### Post by groeswenphil on 2008-09-25
Cheap and dirty way.....and the method that I use when all else fails.

Get one of those leads that has a headphone jack at both ends. Most good electrical or hifi stores sell these.
Put one jack in the speaker outlet and the other one in the line-in hole.
Now, play your sounds using one piece of software and record it with another.

There are probably cleaner ways.
Phil

---

### Post by paulmerchant on 2008-09-25
A better way would be to route the audio output of Firefox to your recording software using Jack. I've never done this with Firefox, but this thread is supposed to give you some ideas on how to do it:

[http://ubuntuforums.org/showthread.php?t=843012]("http://ubuntuforums.org/showthread.php?t=843012")

---

### Post by aeiah on 2008-09-25
use audacity and set it to 'record what you hear'. you can probably do it with other sound recorders too. its a bit cheaper and easier than buying a cable. better quality too.

if you're wanting it just for youtube videos though and you're gonna do a lot of them, it might be better use a script that downloads the flv and strips the audio out.

---

### Post by cotcot on 2008-09-26
Download the youtube video with youtube-dl. Convert it to an avi file with avidemux if you want it as an avi. You can also extract the audio with avidemux (audio tab, save after you have chosen the audio codec such as ac3 wav or mp3).

```
sudo apt-get install youtube-dl
youtube-dl name_of_the_website_with_the_youtube_clip_you_want
```

---

