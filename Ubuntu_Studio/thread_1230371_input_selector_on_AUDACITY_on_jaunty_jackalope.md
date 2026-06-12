---
title: "input selector on AUDACITY on jaunty jackalope"
date: 2009-08-03
forum: Ubuntu Studio
---

### Post by shantiq on 2009-08-03
[B][COLOR=Blue]i am using rosegarden and cannot see how i can export my midi compositions to a wave file

so i decided i would play it in real time and record it on audacity and then saVe to wave


BUT I SEE NO INPUT SELECTOR SO how does one pick stereo mix or line in option

anyone knows how to remedy that???


i have the audacity that came with ubuntu studio[/COLOR][/B]

---

### Post by sgx on 2009-08-03
Hi, using qjackctl, you won't see the Audacity Port Audio connector listed until you hit the record button. Try

Start qjackctl and jackd
Start Rosegarden and load the midi file
Start Audacity and press the record button, then the pause button
Go back to qjackctl, and in the audio tab, connect Rosegarden to Port Audio (which should have appeared out of nowhere, this is the Audacity 'line in'.
Press the pause button again to resume recording.
Start playing the midi file in Rosegarden. Of course, there must be a sound source loaded that Rosegarden can use to generate audio for the midi data, in case someone new to recording midi/audio is reading. I admit
that sometimes I forget that step, and check to see if my headphones came unplugged :D

Using wineasio enabled vst hosts like Reaper, and Cantabile, their plugins output can be connected to Audacity, or to fx like Creox and Rakarrack, then route those to Audacity, makes for quick and easy sessions.
Cheers

---

