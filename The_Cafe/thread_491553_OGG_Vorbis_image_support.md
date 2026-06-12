---
title: "OGG Vorbis image support?"
date: 2007-07-03
forum: The Cafe
---

### Post by maniacmusician on 2007-07-03
Does the vorbis audio format allow for the writing of images into it's tag? I know that ID3 tags support this functionality. With mp3's, you can embedd an image directly into a track, which is usually the CD cover. However, when I tried to do this in EasyTag with ogg files, I was unable to do so.

---

### Post by Polygon on 2007-07-03
ive never seen a mp3 file with a image embedded into it, or a program that supports it.... but im not sure you can do this with OGG files. the ogg tags for artist and song title are pretty lacking compared to what ID3 has though...

---

### Post by DoctorMO on 2007-07-03
This might be something to consider adding to the ogg format rather than the vorbis tagging. we can pack more than 1 thing into an ogg file and each has it's reason for instance theora + vorbis + meta data = ogg video.

We might end up with ogg png

---

### Post by FuturePilot on 2007-07-03
I'd like to know too. I've been thinking about using OGG but I don't want to lose my album art since a lot of it is embedded in the mp3 file itself.

---

### Post by maniacmusician on 2008-01-30
any news on this? months later, and I still haven't discovered any plans to add image support to vorbis tags. Can anyone shed any light on this? Particularly if you know about any official plans to add this to Vorbis, or if it has already been accomplished, what tag editors and audio players can take advantage of it?

---

### Post by FuturePilot on 2008-01-30
Funny I was about to bump this thread as well. I haven't found much out about it either. I'm not sure why they don't add this to the format. It's one of the few that don't support this. But interestingly enough Vorbis claims it can do this
[http://www.vorbis.com/faq/#container]("http://www.vorbis.com/faq/#container")
I'm just more confused now :-k

---

### Post by maniacmusician on 2008-01-30
> **FuturePilot said:**
> Funny I was about to bump this thread as well. I haven't found much out about it either. I'm not sure why they don't add this to the format. It's one of the few that don't support this. But interestingly enough Vorbis claims it can do this
[http://www.vorbis.com/faq/#container]("http://www.vorbis.com/faq/#container")
I'm just more confused now :-k
looking at that, the only conclusion I can draw is that there's no standard for it. For example, a tag editor (like EasyTag) could decide to add support for adding images to Vorbis files. However, since this has never been done before, audio players (such as Amarok) wouldn't know how to retrieve the images from the ogg container. Or rather, there just wouldn't be any code to retrieve the image, because it's never been done. It's been a staple of ID3 for a long time, so of course, Amarok retrieves images from mp3 files with ID3 tags.

Or it could be the other way around; maybe Amarok does have code to retrieve images from Ogg Vorbis files, but there aren't any popular tag editors that support adding images. [shrug] That's my best guess. Maybe someone should file a report against both EasyTag and Amarok about this feature. If I have time this weekend, I could look into doing that...but if anyone else feels like doing it, and has more time than me, please please please do it.

---

### Post by saulgoode on 2008-01-30
[http://lists.xiph.org/pipermail/ogg-dev/2007-April/000452.html](http://lists.xiph.org/pipermail/ogg-dev/2007-April/000452.html)

---

### Post by maniacmusician on 2008-01-30
> **saulgoode said:**
> [http://lists.xiph.org/pipermail/ogg-dev/2007-April/000452.html](http://lists.xiph.org/pipermail/ogg-dev/2007-April/000452.html)
I see. That's kind of a bummer, doesn't look like anyone wants to pick it up. If I had an ounce of coding skill in me, it's something that I would have liked to pursue.

---

