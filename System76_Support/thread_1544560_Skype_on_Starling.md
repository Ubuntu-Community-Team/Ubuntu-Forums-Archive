---
title: "Skype on Starling"
date: 2010-08-02
forum: System76 Support
---

### Post by Teasdale on 2010-08-02
I have a Starling that I got a few months ago, first generation, and I'm trying to get Skype to work on it.

I was able to get it installed, and I searched threads here and learned how to open it by typing

/bin/sh -c "PULSE_SERVER=127.0.0.1 /usr/bin/skype

into the terminal.

When I do a "test call," I get no sound, meaning that my mic and Skype aren't working together. I've tested my mic by recording a few words in "sound recording" from "sounds and video" and it plays back, but when I use it in Skype, I don't get anything. By playing with options in Skype (selecting which sound card to use?) I can get variations of faint static and what sounds like a garbled voice in the distance.

I haven't installed Pulse Audio or anything -- one of the posts from thomasaaron said that installing various fixes can make it harder to get Skype working, so I haven't tried anything beyond using the terminal command.

---

### Post by bruvverjak on 2010-08-02
I ran into this issue and found a recommendation somewhere that suggested installing pulse audio volume control. Locate the mic input and slide either one of the mic inputs all the way to the left.  This fixed the problem for me. YMMV

jack

---

### Post by Teasdale on 2010-08-03
It looks like pulse audio control is already part of the default installation on the Starling...

---

### Post by bruvverjak on 2010-08-03
PulseAudio Volume Control (pavucontrol) listed in Ubuntu Software Center.

Then go to Sound and Video section and open this control and unlock the Input Devices channels and turn either one of them all the way off.  Now lock the channels again and see if that fixes your problem.  I don't know why this works, but several of us have been successful with this fix.

jack

---

### Post by isantop on 2010-08-03
Can you test the sound in another application? This will rule out configuration problem or Skype configuration.

---

