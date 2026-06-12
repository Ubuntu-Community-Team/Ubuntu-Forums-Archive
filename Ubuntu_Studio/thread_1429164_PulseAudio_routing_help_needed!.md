---
title: "PulseAudio routing help needed!"
date: 2010-03-13
forum: Ubuntu Studio
---

### Post by Broodrust on 2010-03-13
I'm posting this in the studio forum mostly because it's a fairly advanced audio question.

This is my problem; I have a Delta 1010lt card, and I want to be able to do some basic routing between my different speaker configurations (atm, I have 4 stereo outputs that I want to be able to use), and since I'm not going to do any music work in my 'buntu, I'd rather not have JACK for this, since I'll be using Pulse anyway and I remember getting this to work ok (rather unstable though) a couple of versions ago (hardy heron I believe).

Simply, I want to be able to choose different sinks for different programs from the Pulse-menu (pavucontrol), basically my crappy comp speakers for game/flash sounds, and my stereo for music.

As things were in that version, after configuring, I was able to choose for each program which stereo output I wanted to use (virtual sinks, or whatever they were called), but after a lot of fiddling in profile-files and whatnot, I've realized there doesn't even seem to be any way to choose output sink from the GUI anymore.

So, is this a lost cause, and I should go with JACK anyway, or can it be done?

Thanks in advance!

---

### Post by rlameiro on 2010-03-14
Broodrust, did you tried the pulseaudio Device chooser? maybe it could help you.

---

### Post by Broodrust on 2010-03-14
Feelin' a bit stupid now, I was in the wrong program. :) Thanks a lot!
Only need a bit of fiddling now and it should work.

---

