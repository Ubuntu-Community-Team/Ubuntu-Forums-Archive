---
title: "audio troubles"
date: 2009-09-19
forum: Ubuntu Studio
---

### Post by curtk69 on 2009-09-19
hey guys, every time i use different media players or websites my audio mutes out , quits working. like if i goto youtube then try n listen to a song on my computer theres no sound or vice versa

whats going on here?

my 8.04 install should be completely up to date
it gets fixed by rebooting computer but what a pain to do that 5  times a nite.

---

### Post by MisterBark on 2009-09-19
it's the same for me.
I think it's "normal"...
because each player (or firefox flash) wants the alsa driver in the same time.
But if you wanna use different sources for the same alsa output, you have to use jack...
I'm not perfectly sure but I think that's the reason.

Then :
1- be sure each program dropped the alsa driver before running another one
2- if it's crashed, do  [alsa force-reload]

(we're gonna wait for the other replies to confirm ... or to see if there's another solution... )

---

### Post by raboofje on 2009-09-20
> **curtk69 said:**
> hey guys, every time i use different media players or websites my audio mutes out, quits working. like if i goto youtube then try n listen to a song on my computer theres no sound or vice versa

whats going on here?

I think what you're experiencing is multiple applications competing for the soundcard.

The general problem is explained at [http://wiki.linuxaudio.org/wiki/audio_layers_overview](http://wiki.linuxaudio.org/wiki/audio_layers_overview) and [http://wiki.linuxaudio.org/wiki/troubleshooting_exclusive_sound_card_access](http://wiki.linuxaudio.org/wiki/troubleshooting_exclusive_sound_card_access)

Basically you'd want to find out which application is holding your sound card hostage, and convince it to use Dmix or some sound server such as PulseAudio (on the desktop) or JACK (for audio work).

---

