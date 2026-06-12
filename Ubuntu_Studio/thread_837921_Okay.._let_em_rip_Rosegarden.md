---
title: "Okay.. let em rip: Rosegarden"
date: 2008-06-23
forum: Ubuntu Studio
---

### Post by Sakrimo on 2008-06-23
Okay, so I'm finally making the switch from recording on an XP system to Linux and as my replacement for the good old friendly cubase (which i have been using for the last 5 years since I was first introduced to Notation), my replacement for Cubase Studio looks as though to be Rosegarden.


As far as I can tell, this is the only software that can really do the job, I had audacity installed on my 64 bit-laptop (the one im one right now!), and thought it was absolutely useless? 

I've heard raving reviews about it though, so maybe the 64-bit version they decided to make it more like.. Windows sound recorder, than an actual possible replacement for a recording environment(why would i want to have 10 programs to do the job of one)..


So after possibly offending a few die-hard audacity users out there, i ask:

Rosegarden: 

1) Good enough? 
2) Capture well Acoustic guitar through microphone (Shure SM58A beta, Alesis USB mixer)
3) Work well with M-Audio Oxygen 8 25-key


And finally, any alternative recommendations?


P.S sorry, audacity fans.. just really didn't like it.

---

### Post by eric71 on 2008-06-23
Rosegarden will work well with your M-audio keyboard. I have a keystation 49 that works fine. You have to get used to the fact that Rosegarden likes to manage all of the MIDI connections itself and doesn't always do it consistently. Just hage to make sure everything is enabled and connected in Rosegarden's settings from time to time.

I hardly can play keyboards and really only add a little organ to guitar pieces. I still at times preferred Rosegarden to Ardour, just for its simplicity. The drawback is that audio recording is very rudimentary in RG. There's no volume or panning envelopes. Things like this need to be done with an external editor, I usually used Audacity. Unfortunately, after making changest in the external editor, the wave is not redrawn in RG, which is less than optimal. If you do mostly midi stuff and like to work with notation, RG really is your best bet, though. And with dssi-vst it is probably the easiest way to use VST and VSTi in linux. It seemed a bit odd for me sometimes having four or five guitar tracks with audio drum loops and just one midi organ track, though. But for whatever reason I don't have the patience for Ardour for simple recording.

As I really record mostly guitar and vocals and have enjoyed Reaper in windows, I mostly use Reaper with wineasio these days. It doesn't do notation, but for my needs the midi is fine, and the audio is far and beyound anything linux has to offer. So that might be another option for you. A good guide is here: 
[http://www.cockos.com/forum/showthread.php?t=16786](http://www.cockos.com/forum/showthread.php?t=16786)

---

### Post by thorgal on 2008-06-23
... may I ask you why you left winXP ? 5 years with a soft means that you know it well, have developed a workflow, etc. Why the change ? I am asking because linux is not winXP, there's no such thing as a one-do-it-all app and that is its power somehow.

What I would suggest is (and it takes time and effort to have it right but is worth it) to have jackd set up and running well at the latency you prefer. Then use ardour and rosegarden as jack slaves so they are sync'ed down to the frame. If you have a dual monitor setup, you can have the rosegarden window on one screen and on the other ardour's track editor window. You will have almost the feeling that you work with one app since activating transport in one will automatically activate transport in the other one. That's the beauty of JACK. So you do all your MIDI in rosegarden, which is what it is best at, and all the audio in ardour, which is what it is amazingly good at when you know how to use it (I use it every f..cking day and I tell you, it's a wonder!)

When I am done with my current project (double-album) I may eventually write a set of tutorials and post a few videos but that's not gonna happen anytime soon ... too busy with music :)

---

