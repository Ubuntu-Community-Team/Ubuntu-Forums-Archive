---
title: "Simple video editor"
date: 2009-07-07
forum: Ubuntu Studio
---

### Post by desperateone on 2009-07-07
Hello, I'd like just to extract the last two minutes from a mp4 file, what tool should I use?

---

### Post by trulan on 2009-07-07
I use AVIDemux (it's in the repositories).  It's really easy to crop a video file with it.

Saving files can be a little tricky, it's easy to mess up the encoder settings.  But if you use one of the presets in the menu, it's fairly straightforward.

There is probably an easier to use program out there, but AVIDemux works for me.

---

### Post by jerrrys on 2009-07-07
[http://fixounet.free.fr/avidemux/](http://fixounet.free.fr/avidemux/)

[http://cinelerra.org/](http://cinelerra.org/)

[http://www.kdenlive.org/](http://www.kdenlive.org/)

[http://www.kinodv.org/article/static/2](http://www.kinodv.org/article/static/2)

[http://lives.sourceforge.net/](http://lives.sourceforge.net/)

[http://lumiera.org/](http://lumiera.org/)

[http://www.openmovieeditor.org/](http://www.openmovieeditor.org/)

---

### Post by agathian on 2009-07-07
if you are comfortable with command line, you can try mencoder..


for ex...
```
mencoder  -oac copy -ovc copy -ss 00:08:00 -endPos 00:10:00  <inputfile> -o <outputfile>
```

copy, from input file, starting from 8th minute to 10th minute, onto output file.

---

