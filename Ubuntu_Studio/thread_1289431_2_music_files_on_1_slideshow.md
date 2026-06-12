---
title: "2 music files on 1 slideshow??"
date: 2009-10-12
forum: Ubuntu Studio
---

### Post by KanineN on 2009-10-12
hello! I am tryng to put 2 songs after each other in a slideshow that I created in MANdvd. It doesn't have to be on MANdvd were you can put another music track after the first. I hope you understand and I am in a bit of a hurry because it has to been done by tomorrow.

---

### Post by azmo35 on 2009-10-12
Hi, my sugestion is join the two on audacity and u can use kino make the file silence and then add this file,maybe this help.

---

### Post by cotcot on 2009-10-12
concatenate the songs together :
```
cat song1.mp3 song2.mp3 > audio.mp3
```

Add audio to video
```
ffmpeg -i video.mpeg -i audio.mp3 -acodec copy -vcodec copy -ab 128k -ar 44100 finaloutput.mpeg

```

---

