---
title: "Brasero not burning right."
date: 2009-05-19
forum: Ubuntu Studio
---

### Post by Extol11 on 2009-05-19
Hi! I have Ubuntu 9.04 64bit on my PC and I was trying to make some copies of my audio cds since I don't plan on playing the original ones in my car. I started Brasero and selected Disc Copy, I told it to make an image of the disc, saved it in a folder in my home directory and let brasero choose the image type. After that, I took out the disc, put in the blank cd and choose Burn image. When I search for the file, it only shows the .toc one, which was the one I remember using in the older versions of Ubuntu to burn with Brasero, so I choose that one. It keeps telling me that no image has been selected and yet the .toc are the only files it lists. I choose " all Files" and see that there's a secondary file with no .toc at the end. I chose that one and only then will it let me burn the disc. When I tried it the first time, it told me that the disc had not burned correctly. The disc didn't work in any of my players and Ubuntu didn't even give me an option of what to do with it when I put it in my machine Like "Open With: VLC, brasero, Movie Player" and all of that stuff. It simply does nothing. 

So, can anyone tell me what I'm doing wrong? It's been a long time since I used this one to burn cds, I don't want to have to install K3b and have two programs that do the exact same thing and Nero makes my XP 64 work weird after installing it. XP 64 will not show anything in the menu when I insert some new form of media, like : Browse Files, Media Player, VLC, Synch and all of that stuff. I have to burn a crap load of stuff to be able to listen in my car because God and only God knows how much I hate scratches on my discs. So your help will be greatly appreciated.

---

### Post by Extol11 on 2009-05-20
No one knows?

---

### Post by Extol11 on 2009-05-20
Can it really be that nobody knows? I looked in the help section of the ubuntu website, it said to do things just as I was doing it. Can anybody give me any help on what might be wrong with brasero or the type of image files I'm using?

---

### Post by DavePlummer on 2009-05-23
I saw your post and tried the same thing on my machine. I had the same problem. Searching around a bit, I discovered a brasero bug report stating that the brasero should require or recommend package cdrdao. I installed package cdrdao via synaptic, and the problem went away. Hope this info helps you.

---

### Post by oregonbob on 2009-05-23
I just spent a CD or two trying to burn a simple audio CD with Brazier (Brasero?) It just went on forever processing saying it was normalizing the audio CD. ****. Things to make audio CD's should work. I am 64bit with 9.04

Right now any Ubuntu workstation should just be 32bit machines. 64bit software has not caught up with the hardware yet. Drivers, popular programs like Boxee, Skype, etc. etc. do not offer 64bit versions until recently. Many are beta and/or buggy.

Damn, I'd like to make a folder of mp3 music files a nice audio CD. I'll have to experiment I guess to see which program if any works.

---

### Post by oregonbob on 2009-05-23
Solved it for me, in preferences turn off (uncheck profiling). It then wrote a complete audio cd in a few minutes or so.

---

