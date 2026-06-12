---
title: "No sound from MIDI instrument in ZynAddSubFX"
date: 2014-03-20
forum: Ubuntu Studio
---

### Post by kazoo on 2014-03-20
I'm not sure if my problem is due to running the OS from a live dvd - it is NOT installed.

I was able to use QjackCtl to get ZynAddSubFX reading input from my MIDI keyboard, but the computer produces no sound this way. On startup of Zyn, it says "Default IO did not initialize. Defaulting to NULL backend." 

Sound *is* produced if I click the piano keys of the Zyn interface. I also get sound from Youtube videos. I *was* able to get the keyboard to generate sound in LMMS as well. Any thoughts?

---

### Post by su:bhatta on 2014-03-20
Hi.
3 steps to get it working.
Ignore the "Default IO did not initialize. Defaulting to NULL backend."  window . Press ok, in case it comes, if you start Jack first it shouldn't pop up.

1) Start Jack using QJackCtl first.
2) Start ZynAddSubFX
3)Use the 'Connection-> Audio Tab' in the Jack window to connect ZynAddSubFX to the System playback..

Then play Midi keyboard. you should get sound.
To use a GUI to do the connections you can use Patchage, it is easy to use.

---

### Post by kazoo on 2014-03-20
Thank you!
ZynAddSubFX did not appear under Audio Tab. What appears there "PulseAudio Jack sync" and "system". ZynAddSubFX did appear under ALSA tab and I connected my USB keyboard to it, so the ZynAddSubFX reads the keyboard. But still no sound from the system.

---

### Post by su:bhatta on 2014-03-20
Just connect " Pulse audio Jack sync" to  System and see. 
Sorry, But I am not having Pulse audio jack sync as I am using Jackd1,. I think you should try opening  up Patchage once and try connecting from there it will be easier.

---

### Post by jejeman on 2014-03-20
You need to start ZynAddSubFx with JACK audio back end in order to appear in Audio tab of Qjackctl. ZynAddSubFx supports both ALSA and JACK audio back end.

---

### Post by kazoo on 2014-03-20
Yes! I did discover that just now. I started the Jack version of ZynAddSubFX, and was able to connect it to the system sound, but then my USB MIDI cable appears under ALSA only, and so I couldn't connect it to ZynAddSubFX. Kind of the reverse problem as before.

OK using your suggestions here (thank you!) and a bit more info I found elsewhere, the problem seemed to be with my MIDI interface. Under JACK Audio Connection, I clicked "Setup," the under Setting tab, in lower R corner, set "MIDI Driver" to "seq." Then I opened ZynAddSubFX - JACK. Then in JACK connections, under Audio, I connected zynadd with system; under MIDI, system to zynadd (this was new, apparently triggered by the previous setting), and under ALSA, I connected both items there to each other (my USB MIDI device, the UX16, and "Midi through"). 

Patchage didn't make sense to me until I discovered that I had to expand the window to see any of the connections, as all I could see when I started it was the menu bar at top. 

Anyway it seems to be working now - thanks a lot!

---

### Post by su:bhatta on 2014-03-21
Glad you got that sorted out kazoo. I know very well how frustrating things seem when simple things like these don't workout.

And about Patchage, yes, after opening just click 'View-" and hit 'Arrange' that would get all available connections lined up real nice. After you start using Patchage, you will see it is one of the most handy and nifty little things available to sort out connections 
 :)

---

