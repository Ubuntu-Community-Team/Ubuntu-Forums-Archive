---
title: "Rosegarden: Finishing a Track"
date: 2009-04-20
forum: Ubuntu Studio
---

### Post by Forgath on 2009-04-20
I have a short Question.
I`ve made a track with Rosegarden.

Now, what have I to do to get a WAV oder MP3?
Is there any function inside of Rosegarden to do that?

I already tried to record it with Audacity,
but that gave a very unclear sound....

Greetings, Forgath

---

### Post by eric71 on 2009-04-20
I haven't used Rosegarden for a long time, but I found the easiest way was to first set a program that can save an audio file in the format you want (Audacity is ideal) as the default audio editor in Rosegarden. Then, in Rosegarden, create a new audio track. For its input, select master out. Recording to this track will record your full mix to one stereo track. Then just double click on this track and Audacity will open it, at which point you can export it to ogg or mp3.

One caveat is, if you are using MIDI tracks (which you probably are in Rosegarden) you have to have a DSSI plugin on each track for the audio to be coming through Rosegarden's master out. If you are using an external softsynth like Qsynth, you are better of using Jack to route Rosegarden's audio tracks and the external synths output into a Jack aware recorder like Ardour.

Hope that made sense. It's been a long day.

---

### Post by B4RR13N705 on 2009-04-20
Ive done this with Ardour, and i got a really clean sound! :popcorn:

---

### Post by Forgath on 2009-04-24
The first suggest did it...
But i`ll think i try out Ardour anyway.

Thanks!

---

### Post by partofthething on 2009-12-19
I just figured out an alternative way to do this with some help from [http://ubuntuforums.org/showthread.php?t=701868. ]("http://ubuntuforums.org/showthread.php?t=701868")

1. Make a new track in rosegarden underneath all your finished tracks by right-clicking it and selecting Audio-1 or something. 

2. Highlight the track and set in to In 1 in Instrument Parameters (bottom left). 

3. Go into your qjackctrl audio connections tab and connect all the outputs of your various synths (hydrogen, zynaddsubfx, etc.) into In1 of rosegarden. 

4. Back in rosegarden, hit record. All audio you here should end up in that audio 1 track, which will then sit as a wav file in your audio-out directory (as specified in rosegarden settings). 

Sweet.

---

