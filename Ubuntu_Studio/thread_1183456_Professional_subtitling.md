---
title: "Professional subtitling"
date: 2009-06-10
forum: Ubuntu Studio
---

### Post by Danus on 2009-06-10
Hi everyone.
I wasn't really sure as of where to post this thread, so sorry if it's the wrong place.
Does anyone here know of programs that professional TV channels\movie makers use for subtitles? 
I mean a program that can easily handle MPEG and maintain the file's quality. 
One that's easy to operate, yet professional non the less.
I do not expect it to be free, so don't hesitate on suggesting such programs.
Thanks a lot!!! :) ;)

---

### Post by lovinglinux on 2009-06-10
Do you need a program to manage subtitle timings and edit them or do you need a program to embed existing subtitles in the video?

Subtitle Editor is the best tool I have used for editing subtitles. Avidemux has a filter to load and embed the subtitles in the video. Both are available through repositories.

If you want something more complex, then Cinerella should probably be able to embed subtitles.

---

### Post by Danus on 2009-06-11
Hi, I meant a program in which i can create subtitles from nothing.
Meaning, I watch a certain MPEG video, then make the subtitles, timing, and embed them in the video. (so that the subs are an inseparable[COLOR=#000099][FONT=arial][/FONT][/COLOR][COLOR=#000099][FONT=arial][/FONT][/COLOR] part of the video)

---

### Post by Danus on 2009-06-11
oh and i forgot to mention.
it has to be very user friendly.
a program that someone who's not a computer wiz can operate xD
thanks a lot!

---

### Post by emeraldgirl08 on 2009-06-11
Have you checked in applications>>add/remove ???

I'm curious about this also as I like to watch Eastern films and television shows.

---

### Post by emeraldgirl08 on 2009-06-11
I'm looking through add/remove apps and see a program called subtitle editor. It seems to support your criteria. I'm thinking the subdownloader. I'll give it a try and let us know how your search goes :)

---

### Post by lovinglinux on 2009-06-11
> **Danus said:**
> Hi, I meant a program in which i can create subtitles from nothing.
Meaning, I watch a certain MPEG video, then make the subtitles, timing, and embed them in the video. (so that the subs are an inseparable[COLOR=#000099][FONT=arial][/FONT][/COLOR][COLOR=#000099][FONT=arial][/FONT][/COLOR] part of the video)

Subtitle Editor is what you are looking for. It has support for MPEG, but it can't embed the subtitles directly in the videos. For that you will have to re-encode the video applying the subtitles over the video image. Avidemux has a filter to do that.

Embedding the subtitles into the video is not a good idea, unless you really need, because you can't edit or remove them later.

To distribute the video with subtitles, but without separated subtitle files and without embedding them directly into the video image, you can use mkvtoolnix. The only issue is that the file format (container) will be mkv. You can add any number of subtitle files you want and if the user has a player with mkv support it will be able to select between different subtitles or even disable them.

---

