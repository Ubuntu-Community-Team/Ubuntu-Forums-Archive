---
title: "sound recording is really... disgusting."
date: 2008-01-01
forum: System76 Support
---

### Post by Squish on 2008-01-01
So I got the serval, the most recent one.

And a few things about my sound. 
The regular sound causes something inside my computer to do a lil vibrate, which is super annoying. Any idea what I can do?

My main problem is though however, sound recording. It is absolutely abismal with the on board mics
I have a mic hanging around, but was just wondering if this was an alsa thing, or do the onboard mics actually suck like that. Basically, I can get it to record. If I want any volume at all, I get tremendous static. Clicks and gurps come and go as well. Ive played around with my setting, although I dont really know totally what I am doing... I can seem to get any decent sound.
I want to start youtubing, but I had this quality. What should I do?

---

### Post by imhavoc on 2008-01-01
Well, I guess it depends on what you're recording for.

If you're recording for a podcast, it would be unwise to use the onboard sound card, even with an external mic. The problem is that internal sound cards aren't isolated from the rest of the computer enough to make decent recordings. Even with a desktop, and a high-end sound card, you're going to pick up noise from the system. With an integrated sound card -- especially in a notebook, it's going to be at least one order of magnitude worse.

I have had good success using Logitech's USB headsets. There is some noise that I have to scrub out in post production, but for $50.00, it's good enough. If you're an audiophile and you're trying to produce high quality sound, you'll want to buy a separate device to record to. I know several podcasters who use various devices from Archos for recording, then transfer the recordings to their PCs for production.

---

### Post by thomasaaron on 2008-01-02
If memory serves, the Serval requires messing around with both the Capture and the Digital slider to optimize the recording. Still it's a bit rough and is essentially an ALSA issue.

I've found that for using Skype, a USB headset is a pretty awesome way to go. Lot's of clarity.

---

### Post by Squish on 2008-01-09
I found a mic, and it records absolutely beautifully, 

Well, guess its alsa

Anyways, I am noticing a vibrating noise when I turn my sound up (the speaker that is)

Should I just tighten screws or something, or what is the proper course of action...?

Essentially, I turn my sound up, and I can hear something in my lappy vibrate.

---

### Post by thomasaaron on 2008-01-10
If it is a buzzing sound coming from your speakers, you might want to turn down the PCM a bit.

If not, where does it sound like it is coming from. I can pull a Serval apart and see what might be loose.

---

### Post by Defrector on 2008-01-11
I can confirm this. Something in the engine itself is clipping/distorting the sound at high levels. This probably means that something in one of the mixers or on the volume control has a gain of more than 0dB. 

I haven't found any linux-based mixers with slider markers relevant enough to give insight of where unity gain (0db) is and it is a problem for anyone seriously considering recording in ubuntu. If anyone has information on an interface which provides this please post. Else, perhaps it is time to contribute to various projects and implement markings for official gain settings.

---

### Post by asmiller-ke6seh on 2008-01-11
Have you looked at AUDACITY. The Vu meter interface might be what you are looking for; I'm not sure how accurate the readout is, but in my experience it seems to work well.

---

### Post by tedrampart on 2008-01-11
I love audacity myself, its one of the more useful recording softwares I've tried so far. 

but the only thing I would worry about this suggestion, would be that if the master alsa levels are still finicky, then there could still be issues.  I can't remember off hand if audacity controls the master volume in the program itself (its been awhile since I used it for recording, since our band got donated a nice pcmcia emu pro card/mixer setup that only works in windows right now *bleh*, so we've been using cubaseSX again)..

---

