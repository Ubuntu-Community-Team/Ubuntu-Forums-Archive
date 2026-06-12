---
title: "Linux audio system - why are there 2 audio programs, alsa and pulseaudio?"
date: 2019-08-09
forum: Ubuntu, Linux and OS Chat
---

### Post by Skaperen on 2019-08-09
can someone who understands the audio system in Linux explain why one audio program (alsa or pulseaudio) is not enough, and what the different roles of alsa and pulseaudio are?

i would think there would just need to be a few kernel drivers for a few things like sound cards, and then the generic drivers for bluetooth, USB, internet interfaces ... then a single program the knows how to access each one and routes audio from the sources to the sinks as specified by whoever controls it.  i can envision it working like a multi-channel mixer matrix allowing each output the have whatever mix of inputs is specified.  connection can be made by users where allowed and they can mix up whatever they want from sources they want, and do as many of these as allowed.  and they can produce sound and be a source or two to go to the speakers or wherever.  named sockets should suffice for most of this and internet protocols used for real networking of sound.

so where have it hit on the need for 2 separate programs.  or did i forget something?

---

### Post by guiverc on 2019-08-09
The following maybe worth reading 
[https://ubuntuforums.org/showthread.php?t=1794581](https://ubuntuforums.org/showthread.php?t=1794581)

(*I remember many many articles about it back when Pulse Audio was new, even recall some functions I used becoming easier, but it was too long ago..*)

---

### Post by Skaperen on 2019-08-09
the chart in that thread must be wrong.  it has TCP/IP completely apart from network stack.

what i have not been able to find is how to connect to PulseAudio and get sound data ... to be a sink.

---

### Post by Skaperen on 2019-08-09
i could understand it being hard to mix 2 audio sources running at different sample rates, especially at rates like 44100 and 48000.  maybe the way it's done is to run the server at some fixed rate and let the application make the changes, such as by invoking ffmpeg.

---

### Post by oldrocker99 on 2019-08-11
There's also JACK audio server, BTW.

---

### Post by Skaperen on 2019-08-13
i've been thinking about JACK.  i wonder how much work is involved in setting it up.  that and taking PulseAudio down.  i don't want to remove it, just disable it.

---

