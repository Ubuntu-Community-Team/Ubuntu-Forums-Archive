---
title: "Progressive Scan Video Capture with Mencoder"
date: 2008-10-21
forum: Ubuntu Studio
---

### Post by lexen on 2008-10-21
I was wondering if there is an option in mencoder (or any other program) to capture video in progressive scan.  I can capture it interlaced then deinterlace it, but it takes a lot of time and I'm told it will lower the quality.  Everything I have been able to find so far refers to ripping DVDs or converting existing videos.

   I am capturing from an HD Camcorder that outputs standard cables.



Thanks,
Lexen

---

### Post by paulmerchant on 2008-10-21
These days, most capture processes simply transfer the exact same digital data from one device to another (i.e. from the tape to a hard drive), although you can often process video while capturing. I shoot progressive using a Panasonic 24p advanced setting. To convert my footage to pure 24p, all I have done in the past is dropped every fifth frame (the blended frame) during a conversion. I do this after the footage has been captured to my hard drive.

What format does your camera shoot? What storage device are you using? How does your camera handle progressive (the pulldown, etc). What are you using to perform the capture? You are right that many deinterlacing processes will downgrade the quality of your video.

---

### Post by lexen on 2008-10-21
I am using a PCI video capture card which has a simple RBY input like the back of a VCR.  The camcorder can output a resolution of 720x480 which uses miniDV.

   I guess all I am looking for is a command that records in progressive scan.

---

### Post by paulmerchant on 2008-10-22
Someone with more information about your capture card or more Mencoder experience might come along with a different answer.

If I were you, I would bypass your capture card and use a firewire connection and dvgrab to capture an exact digital copy of the HDV content on your mini DV tape. Right now, you are going from digital to analog to digital. Even if your PCI capture card supports 720p, which it may not, you will be losing some quality and may be losing some of the options that would give you pure progressive frames.

---

### Post by americanknight on 2009-03-04
> **paulmerchant said:**
> These days, most capture processes simply transfer the exact same digital data from one device to another (i.e. from the tape to a hard drive), although you can often process video while capturing. I shoot progressive using a Panasonic 24p advanced setting. To convert my footage to pure 24p, all I have done in the past is dropped every fifth frame (the blended frame) during a conversion. I do this after the footage has been captured to my hard drive.


Paulmerchant,

I also shoot with a Panasonic camera in advanced 24p mode. I capture the video through Kino, and I see that it always records it as 29.97p. When I used to capture with Vegas on Windows, I would always get exactly what I had recorded: 23.97p. I'm guessing that Vegas automatically through out every fifth frame, like you were talking about. In any case, is there a way to have this happen automatically with DVgrab? If not, how do I go about throwing out every fifth frame like you mentioned? Thanks

---

### Post by punx45 on 2009-03-05
check out chapters 10 and 11 of this document

[http://www.mplayerhq.hu/DOCS/HTML/en/index.html](http://www.mplayerhq.hu/DOCS/HTML/en/index.html)

but you really should find another way to capture your video.   if you are recording in HD there is no reason to take it into your pc composite.

---

