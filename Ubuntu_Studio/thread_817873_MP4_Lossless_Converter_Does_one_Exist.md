---
title: "MP4 Lossless Converter? Does one Exist?"
date: 2008-06-04
forum: Ubuntu Studio
---

### Post by Cody Jordan on 2008-06-04
Right now I'm looking for a Lossless Converter that will sync the audio and video perfect and exact video conversion.
Someone Plz Help!

---

### Post by Stochastic on 2008-06-04
What format are you looking to convert from/to?

---

### Post by Cody Jordan on 2008-06-04
avi and mkv

---

### Post by Stochastic on 2008-06-04
Maybe do a search in these forums for FucoTools.  I think it's just a gui wrapper for a command line utility such as mencoder though.

---

### Post by Cody Jordan on 2008-06-05
i have it but it doesnt work right cause i dont wana change the size of it or the quality of video and audio just from avi to mp4 and it wont even do it the fixed way.

---

### Post by Creative2 on 2008-06-05
well you have to write your command line and then use on fuoco tools 

you should see what kind of resolution and bitrate your original video has and then rencoding .... 

if you re-encoding you will lost quality with every converter. 

Avi formats like mpeg or wmv are capsules, for example i can use an video with codec mpeg2video and audio codec mp2 . when i choose the file name i can use **myfile.avi ** but instead is not an true avi but a vob

so if you have a mp4 with xvid codec and mp3 you could only change the capsule without lost quality because xvide and mp3 codec can be used to "build" an avi file.

if you have to resyncronize anc change your capsule  you could go (many time it works fine but sometime of course you have to delay manually this is automatic..so..)

fuoco tools----->Repair----->to avi --------> Resyncronizing---->mencoder INPUT -ovc copy -oac copy -forceidx -o OUTPUT 

you can use that command line with your mp4 and automatically will change file's capsule from mp4 to avi without re-encoding

---

