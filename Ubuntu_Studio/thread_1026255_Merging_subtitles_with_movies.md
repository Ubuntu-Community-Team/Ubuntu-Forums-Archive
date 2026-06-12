---
title: "Merging subtitles with movies"
date: 2008-12-30
forum: Ubuntu Studio
---

### Post by japtar10101 on 2008-12-30
I was wondering if there's any program that could fuse srt subtitle files to avi movie files, so that the subtitles appear with the movie visuals.  I need a single movie file as a conclusion.

Thanks for the help.

Edit: I'm currently trying to use mencoder right now.  Is there a subtitle file that contains different font styles, and that mencoder/mplayer supports correctly?  My friend suggested VobSub, but I can't find a SRT-to-VobSub converter compatible with linux.

---

### Post by japtar10101 on 2009-01-03
That's sad.  This web page *almost* nails it:
[http://kensai.team88.org/node/13](http://kensai.team88.org/node/13)
> ```
mencoder -o fileiwantatend.avi -sub subtitlesfile.srt -oac copy -ovc lavc -lavcopts vcodec=mpeg4:mbd=2:trell theactualmovie.avi
```
I've tested it, but it doesn't show italics or bold styles, which I use extensively in my translations.

I might also add that for whatever reason, Avidmux can't open my video files, either.

---

