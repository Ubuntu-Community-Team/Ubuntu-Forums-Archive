---
title: "console vlc magic"
date: 2009-10-26
forum: Ubuntu Studio
---

### Post by rahilm on 2009-10-26
I was playing with vlc -I ncurses to play mp3 today when I decided to experiment it with video files. Surprisingly, it creates a VLC media window and the video started playing.

I thought of repeating it in the virtual console. So, i entered vlc -I ncurses aaa.mp3 and it played well
But then i did vlc vvv.avi ...
I still can't believe what i saw!! Try it if you haven't yet
Would someone explain this phenomenon and how to use it??
with regards

---

### Post by gdubey on 2009-11-03
There is no magic, if u can look and understand the trick behind magic.

so the trick is [libcaca]("http://caca.zoy.org/"), the industry-standard colour ASCII-art library.
when you play video files (.avi etc) on console ie out of X server, vlc itself picks this library to render video output as other high level libs for rendering are not available.

as for as ncurses is concerned it is used for providing gui interface to vlc and not for rendering.

you can select color ascii-art output even in X server (while running desktop) from tools ->preferenece -> video->output.

some other players  like Mplayer also support color ascii-art output. commad line for that is
mplayer -vo caca <videofile>

so where is magic now:p

---

