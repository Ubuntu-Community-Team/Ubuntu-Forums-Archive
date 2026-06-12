---
title: "Fast Track Solo + qjackctl + rakarack + audacity"
date: 2015-06-10
forum: Ubuntu Studio
---

### Post by pascal-resin on 2015-06-10
Hello everyone,

It feels like this is a redundant topic and I went through many posts trying different solutions before deciding to write my own.

Setup:
- One PC with Ubuntu Studio freshly installed
- One 'Fast track solo box', connected through USB
- One guitar connected to the 'Fast track'
- speakers connected to the output of my PC (minijack)

SW:
- Well pretty much what is installed on Ubuntu studio: Audacity, rakarack, Qjacktl

Goals:
1) Simply connect guitar to PC and use it as amp
2) Add rakarack in the middle
3) Add Audacity to record (while hearing directly) a chords line and be able to play on top of it afterwards

So far:
- If not launching qjackctl, I was able to record my guitar (without hearing it) and afterwards playing the recorded track
which means not much...

I'd be happy to provide any information you need.

From what I've seen, the main point comes down to opening qjckctl settings, click on [>] and select USB Fast track. This I can do, but if then starting qjaqcktl, then no sound can be heard at all from the PC.

Thanks for any help provided, would be very cool to be able to use Ubuntu this way....

Cheers

---

### Post by jejeman on 2015-06-10
Not a good idea to use two sound cards with JACK at once. Connect output od Fast track to the speakers. Connect "capture" to "playback" for monitoring, or use options from DAW for monitoring.
Don't use Audacity with JACK, better use Ardour or similar DAW which are better designed to work with JACK.

---

### Post by pascal-resin on 2015-06-11
Thanks for the reply! Will do a test with it.

In terms of taking the sound from Fast Track Solo, it appears that the sound is totally messed up. Something is clearly happening, since the noise varies with the sound, but there's clearly something wrong.

The good news is: after hours of tries of every possible combination of jack settings, rakarack settings, ubuntu sound settings and audacity settings, I got something working!!!!!  (being able to record rakarack output, while hearing it real-time on my speakers, connected to my internal sound card). Still there is a little delay and I was wondering whether this is unavoidable or not.

I can send a screenshot of my config if any need. (basically, needed to select a different output (second sound card) on jack, and configure the preferences in audacity))

---

