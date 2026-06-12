---
title: "[SOLVED] Muse Score (mscore) and Midi problems"
date: 2008-08-14
forum: Ubuntu Studio
---

### Post by etienne@Rofti on 2008-08-14
Hi! My name is Etienne, and I regularly write sheet music as part of my income.

I have been using Rosegarden with Timidity installed until I found out about the new project Muse Score, and installed it.

However, it will not open and I cannot explain why.
The error that I receive when the program is run is as follows:

```

Suspending PulseAudio
ALSA lib pcm_dmix.c:996:(snd_pcm_dmix_open) unable to open slave
Alsa_driver: Cannot open PCM device default for playback.
init ALSA audio driver failed
no ALSA audio found
sequencer init failed
Couldn't resolve property: 2
Couldn't resolve property: 2
WARNING: Child process terminated by signal 11
Failure to resume: Invalid argument

```

Apart from that problem, it is extremely difficult to continue to write music as whenever a Midi program is running such as Timidity, Rosegarden, or QSynth, I cannot play any audio files (such as .mp3 or .ogg)

I would really appreciate any help in this regard!

Thank you!

---

### Post by silentb on 2008-08-17
The reason is simple. These programs exclusively access your sound hardware, so that no other software can use it at the same time. That's the sole reason why JackD exists. Exclusive hardware access is necessary for low latencies and JackD guarantees both low latencies and suitable mixing capabilities.

Audacity can be configured to use JackD, too, so use it to listen to songs.

---

### Post by etienne@Rofti on 2008-08-17
Thank you! I will be looking into how to use Jack! I found a HowTo that might just help me...

If anyone can help me with my inability to open Muse Score (mscore), I would appreciate it too!

---

### Post by etienne@Rofti on 2009-01-02
I have solved my Midi problems, and now run Rosegarden and Muse Score smoothly without problems!

I did it by installing the package "linux-rt" (although I don't even think it is necessary!), and then using Qsynth and JACK to speak to each other:

Having installed Qsynth and Jack (packages "qsynth" and "qjackctl") I ran Jack, and then ran Qsynth, with qsynth's audio driver set to "Jack" in its settings.

I am now starting to write a manual for installing and using Muse Score (Rosegarden has many manuals!) and playing MIDI though computer speakers, so for more information, log onto my website ([www.micmusic.co.za](www.micmusic.co.za)) and visit the forum!

---

