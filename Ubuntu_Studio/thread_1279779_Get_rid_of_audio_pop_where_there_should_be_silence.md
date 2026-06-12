---
title: "Get rid of audio pop where there should be silence"
date: 2009-10-01
forum: Ubuntu Studio
---

### Post by FunkyRes on 2009-10-01
I'm trying to make a 2 second copyright notice clip that I can add to my movies (in kino).

Started with two jpg images, one all black and one with notice.

Imported into kino, each with ~ 1.5 second duration, and used disolve transition, resulting in 2 second clip. Exported result to dv.

Problem is a slight crackle has been introduced in the transition.

Here is the clip as ogv file (less than a mb):

[http://www.shastaherps.org/media/ogv/credit001-sd.ogv](http://www.shastaherps.org/media/ogv/credit001-sd.ogv)

(grab with curl or wget, firefox has issues playing super short clips)

What's the easiest way to just replace any/all audio in the dv file with nothing so that when I put the copyright clip at end of videos and use dissolve to join my content with the copyright, no audible audio (crackle or otherwise) is there?

Thanks for suggestion.

---

### Post by FunkyRes on 2009-10-01
OK - not sure if the best way, but this worked.

Exported audio from kino to foo.wav

edited in audacity, flattened all audio, saved as foo2.wav

ffmpeg -i credit001.dv -i foo2.wav -map 0:0 -map 1:0 -y credit002.dv

That seemed to result in quiet clip I can work with :)

---

