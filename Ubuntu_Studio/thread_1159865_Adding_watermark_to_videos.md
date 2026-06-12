---
title: "Adding watermark to videos"
date: 2009-05-15
forum: Ubuntu Studio
---

### Post by galvao on 2009-05-15
Greetings. 

I have a very specific need and almost no experience with video editing: I need to add a watermark (logo) to some video files.

I'd like someone to recommend me a tool and/or tutorials on how to achieve this.

This (adding watermark) is all I need for now, so the simpler the better.

TIA,

---

### Post by cotcot on 2009-05-15
Suggestion using blender VSE.

Create an image (with Gimp for example) with a black background and the text or whatever you want to watermark in very dark grey. 
Open blender sequence editor, load your movie, load the image on a seperate track. Make the image as long as the video. Select the video strip and than the image strip and apply an effect (--> Add --> Effect --> Add).

There are other video editors able to 'add' tracks together. The idea is the same. Black is 0 (on a scale from 0 to 255). It adds nothing to the video. Dark grey is something like 10. It adds a little bit to the video. So you will see a slight color shift where you have grey on the image.

---

### Post by lovinglinux on 2009-05-15
Avidemux can do that. Click the video filter option and look in the "Misc" category.

---

### Post by cotcot on 2009-05-16
> **lovinglinux said:**
> Avidemux can do that. Click the video filter option and look in the "Misc" category.
Thanks for pointing to this (and the other) option(s). I tried to add a png as logo. However with text I see that the text is deformed.(see screenshot added) In the you should see 2 times the word 'water'. With a foto as image it is ok.

EDIT :  This was with Avidemux 2.4.1 in Hardy. With Avidemux 2.4.4 in Jaunty it is OK.

---

### Post by galvao on 2009-05-17
Thank you *very* much, this was exactly what I was looking for.

---

### Post by biker3 on 2009-05-28
> **cotcot said:**
> Thanks for pointing to this (and the other) option(s). I tried to add a png as logo. However with text I see that the text is deformed.(see screenshot added) In the you should see 2 times the word 'water'. With a foto as image it is ok.

EDIT :  This was with Avidemux 2.4.1 in Hardy. With Avidemux 2.4.4 in Jaunty it is OK.

And also with transparency?:o

---

### Post by enhu on 2010-10-10
where can i locate the misc tab in 2.5.2 version?

---

### Post by echofloripa on 2010-11-22
From what I see, the logo plugin of avidemux was removed in the current version (2.5).

How can I install version 2.4?

---

### Post by khashochir on 2010-12-26
Hi all.This software is not run.How add watermark in video .please say best solution to me !

---

