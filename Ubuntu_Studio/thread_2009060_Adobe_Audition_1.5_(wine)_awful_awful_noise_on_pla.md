---
title: "Adobe Audition 1.5 (wine) awful awful noise on playback"
date: 2012-06-23
forum: Ubuntu Studio
---

### Post by Jonatello on 2012-06-23
Hi, I'm not sure what changed (audition 1.5 on wine used to work like a charm for me), but lately, i cannot play any file in audition (multitrack or single, mp3 or wave, including past session files that used to work) without hearing nothing but terrible awful grotesque mess of noise that sounds like someone is trying to eat my computer without any ketchup or bbq sauce. 
 
i checked in the device setup to verify that playback is set to 16 bit

don't know what happened...

was it an ubuntu update? i'm still on ocelot, so my ubuntu version hasn't changed.

has anyone else experienced this?

---

### Post by Precipitous on 2012-06-24
I am sorry, I do not have an answer to your issue...  I was just wondering how you were able to get Audition 1.5 to run properly in Wine. I have never been able to do so and had always heard it was not possible...

---

### Post by Jonatello on 2012-06-25
Really? I always heard it was among the most compatible versions. All i did was install it.

It used to work great. Don't know what's happening now.

---

### Post by Precipitous on 2012-06-25
> **Jonatello said:**
> Really? I always heard it was among the most compatible versions. All i did was install it.

It used to work great. Don't know what's happening now.
My bad. I was thinking of version 3.0, not 1.5...  To that end, though, if anyone knows how to get version 3.0 to run in Wine I would LOVE to know how to do it. Version 1.5 runs OK for me, but there are some mastering filters in version 3.0 I would like to be able to use...

---

### Post by Jonatello on 2012-06-27
here's what i did yesterday

i completely and utterly wiped out wine and everything else in it from my computer (system76 serval)

reinstalled everything from scratch

audition worked!

opened it back up this morning

its all messed up again!

cannot figure out what happened over night while i was asleep. makes no sense to me, but the audio is back to sounding like a scrambled mess of ear-piercing sounds.

Also, i just verified that the issue ONLY affects playback...i just tried a test project of editing and chopping some wave chunks, mixing-down and exporting an mp3 and playing the mp3 in another application. It sounds fine there.

---

### Post by Jonatello on 2012-06-27
more details:

the sound in the organizer panel (the panel on the left side that lists the various audio files that have been loaded in a session and lets you preview them with a tiny play button) works perfectly (as long as i have 16 bit checked off in playback of course). 

So it just seems to be the main areas (multitrack mode or single wave edit mode) that go wrong. When 16 bit is checked, they sound hideous and scrambled for a brief moment before the sound goes completely blank. When 16 bit playback is unchecked, its a more uniform white noise, and the little audio file preview area on the left gets the same white noise.

---

### Post by sgx on 2012-06-28
I once did a system search for 22050, 44100 and 48000,
and discovered a text file, where the wrong setting existed,
causing mismatched sound.

When you have a working system, run htop and note which apps
are running, then if things go bad, run htop, and see if different
apps are running. 

With usb devices, you could have something switching assignments.
You could have hardware stealing interrupts. Turn off bluetooth,
webcam, power management, networking etc in the bios. If it starts
working, turn them on one boot at a time, until the villain is revealed.

If its a usb soundcard, boot with it unplugged. Run commands
aplay -l  and  cat /proc/asound/cards, copy the items in
brackets.

plug in the device, repeat the commands, and compare the output,
your sound device should now be evident in brackets. Command

killall pulseaudio

can be used to shut down that app before running adobe,
if pulse is getting out of line.

Cheers

---

