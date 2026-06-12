---
title: "Jack prevents audio playback"
date: 2016-10-10
forum: Ubuntu Studio
---

### Post by stelkork on 2016-10-10
Hello,

I use Ubuntu Studio so that I can practice the guitar without making much noise. My main interest is to use guitarix (amp simulator) along with a playback program (such as playitslowly), in order to transcribe songs. My problem is that when Jack server is started, the playitslowly pauses the song and I can't make it continue playing unless I stop the jack server. [Playitslowly]("https://29a.ch/playitslowly") is supposed to work with jack, but I am not sure how to do it. 

Any ideas how to solve this problem?

FYI, I notice the same behaviour with Clementine, Parole, SMPlayer. On  the other hand, VLC does not pause, but it is not heard. I suppose I  need to search a bit more how to connect VLC to Jack.

Thank you in advance

---

### Post by CrocoDuck on 2016-10-12
Hi. As long as VLC is concerned, look at the very bottom of [this]("https://wiki.archlinux.org/index.php/JACK_Audio_Connection_Kit#VLC_-_no_audio_after_starting_JACK") page.

According to my understanding, Ubuntu Studio should be configured to allow PulsAudio to play through jack out of the box, so not sure why it is not the case for you. I am afraid the only documentation I can pick now is [from Arch Linux]("https://wiki.archlinux.org/index.php/PulseAudio/Examples#PulseAudio_through_JACK"). I don't know whether this will work the same on Ubuntu. Try to google something like "Pulsaudio through Jack Ubuntu", unfortunately I am not on Ubuntu anymore, so I cannot help too much...

---

