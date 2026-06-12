---
title: "Noise Reduction from Built in Videocamera Mike"
date: 2009-07-15
forum: Ubuntu Studio
---

### Post by Black Razor on 2009-07-15
Hey guys, I got a class assignment where we have to make a film for class final, and the camera we had to use didnt have an external mike input.  So I had to record using the built in.  I picked up a lot of motor noise, and I need to remove it.  

Anyone have a simple way to do this?  I already figure in having to extract the audio from the video and then sampling the noise and using that sample to reduce the noise, but I dont know HOW to do this.  I got an idea from this.

[http://www.atpm.com/10.12/howto.shtml](http://www.atpm.com/10.12/howto.shtml)

Anyone know how I can do this in Ubuntu?

---

### Post by ajgreeny on 2009-07-15
I can't help with the extraction of the audio part of your problem, which I'll have to leave to others, but once you have it separated from the video, for the noise reduction part, have a look at audacity.  Provided the audio file type can be read by audacity, you can sample the noise from a "silent" section of the audio, and then easily remove it from the whole file.

---

### Post by Black Razor on 2009-07-15
Um, yes sir.  I realized that already.  May I inquire how?

---

### Post by Stochastic on 2009-07-16
If you had to make the film with that hardware, then you really don't need to worry about the quality of the audio - they can't/shouldn't grade you down if that's the only hardware available.

If you have the extra time on your hands these would be the apps to research more on:
ffmpeg - converter
audacity or rezound - audio editors

---

### Post by ajgreeny on 2009-07-16
> **Black Razor said:**
> Um, yes sir.  I realized that already.  May I inquire how?
Have you actually looked at audacity to find out how, as it is very easy?
Simply open the sound file in audacity, go to Effect - Noise removal and it will almost talk through the action needed, but basically, select a sample of noise from the file and click on *Effect -Noise removal*.  There you will see a button "Get noise profile".  Now hit Ctrl+A to select the whole file and go to Noise removal again, click OK, and the noise will be removed; it's as simple as that, and very effective.

---

### Post by kayosiii on 2009-07-16
Either Audacity or Gnome Wave Cleaner (gwc) can be used to remove noise from audio. You will almost certainly find that the noise removal takes away more than the noise - the best way around this is to apply noise removal on a copy of the track and then mix the original track into the copy until you get the best mix of camera noise and artifacts created by the noise removal.

---

