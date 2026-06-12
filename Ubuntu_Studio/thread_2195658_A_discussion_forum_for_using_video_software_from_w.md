---
title: "A discussion forum for using video software from within Ubuntu Studio?"
date: 2013-12-25
forum: Ubuntu Studio
---

### Post by Paul King on 2013-12-25
I didn't see anything like this, so I thought I would start one.

I am using Ubuntu Studio to create videos with voiceovers. I have videos, and ways of producing and storing them, but they often end up without sound, or without the right kind of sound. Is there such an animal in Ubuntu Studio that anyone can recommend that can:

[LIST=1]
[*]Add sound from a mike
[*]Failing that, adding sound from a file (created by Audacity, for example)?
[*]delete an unwanted sound track
[*]Adding titles
[*]adding subtitles, graphic inserts, etc.
[/LIST]

Thanks

Paul

---

### Post by bashiergui on 2013-12-26
Openshot does all of those things perfectly, it's packaged in ubuntu studio.

---

### Post by Paul King on 2013-12-26
Thanks. Found it. It seems to be a tad unwieldy in the sense that importing a video (such as a screenshot from RecordMyDesktop) successfully does not necessarily make it playable. If I can't place it on the timeline, nothing can get off the ground. But I guess I'll play with it some more and look at the docs before I gripe in earnest.

Thanks again.

---

### Post by bashiergui on 2013-12-27
IMO Openshot is not terribly intuitive. I spent a lot of time with the manual before it was much use.

---

### Post by joe4ska on 2013-12-30
I prefer **Pitivi** which can be found in the repositories and is a good replacement for openshot
sudo apt-cache seach pitivi

I also find **Kazam** pretty solid as a screen capture tool.
sudo apt-cache search kazam

---

### Post by dannyboy79 on 2014-01-03
kdenlive is by far the most feature rich NLE for Linux IMO. If you want something to record your desktop, simplescreenrecorder is your best bet as well, it has code built in for keeping audio and video in sync where ffmpeg and vlc fall short, i love it for screencasting as well as livestreaming to twitch or hitbox.

---

