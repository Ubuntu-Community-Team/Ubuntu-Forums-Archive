---
title: "Anyone heard of an avi frame grabber?"
date: 2008-07-14
forum: Ubuntu Studio
---

### Post by kaspar_silas on 2008-07-14
Hi All, 

Im looking a way to convert a specific frame on a gray scale uncompressed ".avi" file to a ".csv" file (or a table of numbers).  

I can't use "non-loopable" solutions like screen capture as, all in all, I have about 10,000 frames to do.

My google ponderings have been tremendously unproductive. So any help or nods in the right direction is very greatly appreciated. 

Kaspar

---

### Post by kaspar_silas on 2008-07-15
Just in case anyone else comes up to the same problem. My solution was to install the great program ffmpeg then use the command

ffmpeg -i [name].avi frame%d.bmp

Then I wrote a small program to read in the bmp files and spit out csv. Im sure there is a pre packaged program for this last step but I don't know it.

---

