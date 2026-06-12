---
title: "Ardour playback problems"
date: 2009-05-17
forum: Ubuntu Studio
---

### Post by be_samurai on 2009-05-17
i can record with no problem. it's just that when i play back what i record, it's all fuzzy. my guess is that it has something to do with the fact that i can't even get jack running. i would post the long message i get whenever i try to start it, but i can't even get online with ubuntu studio (i'm using my other laptop to post this) and i'm a little too frustrated to be typing a ridiculously long list.  i've been producing my own music for about 5 years now and decided to get serious using ubuntu studio just recently. got a new dell inspiron 1545 for that purpose, but i'm having to use Ableton Live Lite on my windows partition, which is way too limited (came with my midi controller).  any help is greatly appreciated beyond words.

---

### Post by be_samurai on 2009-05-30
thanks a lot for the help guys. i really appreciate it.

---

### Post by dawiba on 2009-05-30
It might be helpful to tell others what you're using to record.

What interface/soundcard? What are you recording, keys, vocals, guitar?

Once people know what you're trying to record and how you're putting that into your computer, they might be able to help.

Fuzzy playback is a bit vague ;)

---

### Post by be_samurai on 2009-05-31
thanks for the tips on getting help.

  i'm recording my classical guitar using some dynex computer mic i got from best buy. so it's really nothing fancy until i can get a bit more cash.

  audio interface is just what the laptop came with: 2 channel High Definition Audio IDT 92HD71  do you require any more info?

---

### Post by kayosiii on 2009-06-01
AFAIK If you can record with Ardour then you have Jack running... Ardour does not work without jack. 

Could you be a bit more descriptive of this fuzzy sound as it could help figure out the root cause.

Here are a few things you could try...

Try exporting the audio and playing it back in something else... eg Audacity (have a look at the waveform or indications of clipping etc)...
This will give you some indication as to whether the problem is actually in the recording or the playback.

if its the recording.

You may want to go into the mixer panel for you sound card and play around with the microphone level and preamp boost options. 

Check the position of the Mic in relation to the insrument... Guitars can be quite boomy at the bottom end and these frequencies when summed can cause buzz in speakers. Recordings will be less boomy if you record away from the soundhole around (where the body meets the neck is a good place to start). Even then, especially if you have more than one part, it is a good idea to run a high pass at about the lowest frequency your guitar notes at and use an equaliser to drop the signal from 400hz downwards.  

If it is in the playback on the other hand. try

disable pulse-audio, pulse can on some systems interfere with the proper operation of jack. Recently work has gone into making pulse co-operate with jack - but this is not part of jaunty. search the forums for "disable pulse audio" for instructions on how to do this

xruns can cause audio glitches, I would not usually call this sounding fuzzy but it is a common problem. there are two things you can do one is to increase the buffer size (frames/period) and put up with the increased latency. The second is to configure jack for realtime usage... Again search the forums as instructions on this have been written many many times.

---

### Post by be_samurai on 2009-06-03
thanks for every bit of advice given so far!

i'm getting a pretty ridiculous amount of clipping.

to elaborate on the playback sound quality (which i forgot to do, sorry): the best way i can describe it is like an old sega genesis game glitching like crazy. i have to turn the volume up very high to hear it.
i've seriously messed with jack's settings many, many times. i've done so by looking through a lot of posts. i've enabled and disabled realtime, messed with the buffer size, and still get the same results every single time.

plus, i'm having problems with ubuntu studio in general. when i first messed around with ardour and had this messed up playback, i used the "hardware testing" thing. whenever it gets to testing the video, i get a blank screen. whenever i minimize a window, it goes towards the bottom-right of the screen, never to be seen again (i can't bring it back up no matter where i click). it does not read my wireless card thing to get to the internet.

i've just about had it with this ubuntu junk. i seriously just don't get it. i don't experience any of these problems when booting windows and using ableton live lite. i'd uninstall ubuntu and buy ableton, but they can take that $350 they're asking and shove it. so, it would be awesome to get this stuff going.

---

### Post by dawiba on 2009-06-04
Since you're managing to record without any software difficulties, it sounds like you need to lower your input levels.

How are you setting your input levels?

---

