---
title: "Enhancing single track live audio recording Ardour JAMin"
date: 2014-02-09
forum: Ubuntu Studio
---

### Post by Derelinquat fenestras on 2014-02-09
Hello all!

I recently uncovered an old HI8 video tape of a show that my band played many years ago.  I was pretty excited because I thought the show was lost for ever.  

I wanted to make a bootleg audio CD out of it so I recorded the audio through Audacity via my line in mic port, duplicated the track and made it into a stereo track.  I exported a rough draft cut to listen to on my MP3 player and it sounds exactly like what is is...  a terrible bootleg recording from a camcorder.  

I've been playing around with it in Ardour (my DAW of preference) and JAMin to master it.  But I can't seem to get rid of the horrible abrasive high end out of the mix without severely diminishing the sound quality.  I've used Ardour/JAMin to master before, but I am in no way a pro.  I've primarily used it for more electronic music, and this is an extreme metal band.  So far I have tried to put both a lowpass and highpass filter on it to try to get rid of some of the unwanted ranges, but I've had limited success.  I would really like it increase the presence of the band and cut out some of the more abrasive frequencies.  If anyone has any advice for me, I would be greatly appreciative.

I'm using a relatively new install of Ubuntu Studio 12.04.  Not too sure about the sound card, but everything seems to run fine.  If you have any questions or need any more info, I will gladly comply to the best of my ability!

---

### Post by CrocoDuck on 2014-02-10
Hi! Here what I would do:
First, make it sound the best before mastering. You could try some noise reducer plugin. Select a region of the tape where the noise is high in volume and then elaborate a profile of the noise. You can do it with audacity. You may want to find a place in the tape where there is just the noise for an accurate profile. Then you can try to remove it. Proceed for little adjustments. Then you could run a mutiband filter with a lot of bands and Q value parameters to balance the frequency spectrum of the tape. Firstly, you use it to locate precisely the bandwith of the noise you don't want to hear. Then you proceed to reduce it, making the bandwinth of any instruments to sound louder. Then you can master it, and it must be the last step since compression can make noise loud as the rest.

---

### Post by Derelinquat fenestras on 2014-02-10
Hello!  Thank you for your reply!

I'm kind of new to the audio production game and have never really made use of filters before.  I just dug through all of the plugins I have in Audacity, and haven't found any that are explicitly called multiband filter...  I have C*Sweep VFII-resonant filter with f and Q swept, Combfilter, Multiband EQ, Notch filter, Triple band parametric with shelves (I think is a compressor), and various high/lowpass filters... Do you think any of those would work or do you recommend any specific packages with multiband filtering?
 
Thanks!

---

### Post by CrocoDuck on 2014-02-10
The 12 band equalizer form Calf plugins should be enough. There's also an equalizer that is part of Guitarix, it may be useful. Yeah, what I have in mind is more often colled Equalizer or Multiband equalizer.

---

### Post by Derelinquat fenestras on 2014-02-10
Thanks!  I believe I have both of those!

Do you have any tips on how to go about finding the offending frequencies?

Also do you have any tips on compression and mastering?

Thanks!

---

### Post by CrocoDuck on 2014-02-10
Have a look at here: [http://wiki.audacityteam.org/wiki/Reducing_noise](http://wiki.audacityteam.org/wiki/Reducing_noise) . It is the Audacity wiki, but there are pretty much general infos. Well, I'm used to do like this: I start removing the noise with plugins. Then I try to adjust what remains with the EQs. I move one band at a time of the equalizer, putting all down the level, so I can notice clearly into wich bands is located the noise. Your ear and a spectral analyzer can help you: with the ear you can hear how high in pitch is the noise, so you gess the bands into which the noise is present. With a good analyser you can even find what kind of noises and disturbances are present in the tape and make a quantification of the issue, maybe elaborating a very accurate profile to statistically remove them. I never tried so technical, but have a look at this: [http://www.baudline.com/](http://www.baudline.com/) , it is an essential tool in my opinion.

Anyhow, once you have found the bands that contain the noise, try to reduce the level, using the Q factor to shape and optimize the bandwith. Also, try to boost a little the good parts of the tape, locating in the same way the bands where the single instruments are (it will be quite hard I guess, since you said that has been recorded live...). Proceed by small adjustments and take your time.

Before mastering I have a rule for my recordings (but I'm not expert and you easily find that my recordings are not such good... I should practice more): The mix must play loud and complete by itself. I mean, every instrument should have a window in the spectrum into wich it is present, with not too much overlaps with other instruments. Everything should sound equilibrate and loud at the end of the mixing. Then mastering comes easier, you just have to adjust the overall frequency behaviour and boost up the volume without compressing too much: dynamics are cool!

---

### Post by Derelinquat fenestras on 2014-02-10
Thank you so much for all of your help...

I will try this and try to get the best sound I can!

---

### Post by stickman2 on 2014-10-07
Great advise from CrocoDuck here!!! For advise on masterting make sure you have a nice balance for the instruments. Think about instrument levels and instrument panning. I presume you now only have stereo tracks of the whole mix and not the isolated instruments? If you have all the tracks there's a lot more to work with. I found the following [article]("http://www.functioncentral.co.uk/blog/2014/04/producing_covers_demo/") really helpful when thinking about mastering and mixing tracks

---

### Post by luctor on 2014-10-12
> **stickman2 said:**
> Great advise from CrocoDuck here!!! For advise on masterting make sure you have a nice balance for the instruments. Think about instrument levels and instrument panning. I presume you now only have stereo tracks of the whole mix and not the isolated instruments? If you have all the tracks there's a lot more to work with. I found the following [article]("http://www.functioncentral.co.uk/blog/2014/04/producing_covers_demo/") really helpful when thinking about mastering and mixing tracks

he has a single track from a camcorder, so no way to balance instruments and the like ...

---

### Post by Rob Sayer on 2014-10-12
Here's a rough guide to the frequency spectrum of musical instruments (there are others):

[http://www.independentrecording.net/irn/resources/freqchart/main_display.htm](http://www.independentrecording.net/irn/resources/freqchart/main_display.htm)

A little EQ often goes a long way.

Some of the problems you have on the source may not be amplitude related but due to other artifacts in the recording.  It may be difficult to reduce them without compromising something else ... 'presence' and 'screechy' often deals with the same frequency region.

I'd suggest looking into the audacity forums.  There's some serious knowledge there.

---

