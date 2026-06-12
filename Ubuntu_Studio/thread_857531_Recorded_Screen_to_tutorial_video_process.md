---
title: "Recorded Screen to tutorial video process"
date: 2008-07-12
forum: Ubuntu Studio
---

### Post by justtech on 2008-07-12
I have tried to get this figured out on my own and just can't seem to get it.  I am trying to record my desktop and have managed to be able to successfully accomplish this with "recordMyDesktop".  I end up with a .ogg file.  Then I need to lay a audio file over that and ended up having to go back in to a Winblows computer to accomplish this as I couldn't find the solution on the bright side with Ubuntu.  So I used movie maker and everything ended up well.  Then I needed to be able to convert it into a .flv file for the software that I am using on a webpage.  FFmpeg did a great job with it.. keeping the quality and everything but lost the sound.  I ended back in Winblows working with another program that just butched the quality of the video so bad that now I am back a square one.  Anyone have any solutions.  I have about 15-20 more to go and would like to stay in Ubuntu at all costs.  Anyone know what I am doing wrong with the conversion to lose the audio?  Any help would be appreciated.

---

### Post by Creative2 on 2008-07-12
well, you have lost your sound on flv because i think you have FREE ffmpeg compiled 

so you need to :

-add medibuntu repository (search medibuntu on google the first link then .----medibuntu repository how to)
- reinstall ffmpeg 

so you  will be able to use ffmpeg compiled with no-free encoders..

search for fuoco tools if you have want a universal converter you can always use its command line if you don't like it

---

### Post by justtech on 2008-07-12
I have checked the Synaptic Package Manager and it does say that the ffmpeg version that I am running is the medibuntu version.

---

