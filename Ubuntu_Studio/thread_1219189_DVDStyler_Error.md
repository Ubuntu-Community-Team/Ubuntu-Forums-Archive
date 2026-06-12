---
title: "DVDStyler Error"
date: 2009-07-21
forum: Ubuntu Studio
---

### Post by daemon3 on 2009-07-21
I tried to make a DVD menu with DVD Styler.  The movies are encoded (using Cinelerra) as Microsoft AVI with Microsoft MPEG-4 for sound and video.  However, when I burn the DVD, I get the following output (this outputs iteratively for each frame--this is just a sample):
```
ERROR: step_index = 89
unused byte should be null but is 93!!
Multiple frames in a packet from stream 1
ERROR: step_index = 210
unused byte should be null but is 186!!
ERROR: step_index = 221
unused byte should be null but is 171!!
Multiple frames in a packet from stream 1
ERROR: step_index = 230
```
**Please help soon.  Someone is relying on this DVD.**  In the meantime, I'll see how QDVDAuthor treats me.

Thanks in advance.

---

### Post by daemon3 on 2009-07-21
I think I actually found a huge problem, but I don't know what's causing it: I'm able to render a DVD menu in qdvdauthor.  I then burn it to a disk.  When I pop the disk in and try to select a video from the menu, only about five seconds of the video plays and the freezes while the sound continues playing.(*,)  What's a safe codec to use for video/audio?:(]

---

### Post by daemon3 on 2009-07-24
Please help!  This is urgent!

---

### Post by cotcot on 2009-07-25
The mpeg4 video will be re-encoded by DVDstyler to get a DVD compatible format. Maybe there is something wrong in this conversion. I tried dvdstyler several times and it did never work properly. Installation was already a problem. (it is not a generalised comment; I only report from my own experience)

As you say that it is urgent I could recommend to use [[COLOR="Blue"]Devede[/COLOR]]("http://www.rastersoft.com/programas/devede.html").

---

### Post by Labello on 2009-07-25
[http://ubuntuforums.org/showthread.php?t=652843](http://ubuntuforums.org/showthread.php?t=652843)

this tool is perfect for encoding to a DVD format since it already offers the perfect default settings for that. this worked perfectly on intrepid but i haven't tried it on jaunty yet.

read the post carefully and try to follow the steps correctly to get fuocotools working. once you got it it rocks as hell :-)

good luck

---

### Post by daemon3 on 2009-07-26
Thanks.  I already tried two other DVD programs: devedee (a program that's just the bones) and qdvdauthor.  QDVDAuthor did the same as dvdstyler, and for some odd reason devedee claimed I was out of memory (I'm sure 4G is enough).  I'll go through the instructions for dvdstyler since that seems to be the most stable program.

Thanks again...I'll keep you posted.

---

### Post by Labello on 2009-07-26
> **daemon3 said:**
> Thanks.  I already tried two other DVD programs: devedee (a program that's just the bones) and qdvdauthor.  QDVDAuthor did the same as dvdstyler, and for some odd reason devedee claimed I was out of memory (I'm sure 4G is enough).  I'll go through the instructions for dvdstyler since that seems to be the most stable program.

Thanks again...I'll keep you posted.

Well you should keep in mind that dvdstyler does not really have anything to do with encoding videos. I once had a bigger video project and my production pipeline was as follows:
-DV import with kino
-cutting and editing the footage with cinelerra (replacing audio, adding titles and MANY filters)
-rendered and exported it from cinelerra to raw-dv
-converted it with fuocotools to the proper MPEG format
-designed menu in dvd-styler, simply added the clips
-created image, burned it

so there was no encoding needed after having used fuocotools. you just should make shure that you already have the clips in the right format before using dvdstyler.

---

