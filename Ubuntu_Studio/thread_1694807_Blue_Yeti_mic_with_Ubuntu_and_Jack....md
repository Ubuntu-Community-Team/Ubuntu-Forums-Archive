---
title: "Blue Yeti mic with Ubuntu and Jack..."
date: 2011-02-24
forum: Ubuntu Studio
---

### Post by ragtag on 2011-02-24
I'm considering getting the Blue Yeti mic, and was wondering if it works with Ubuntu and Jack. Someone mentioned in a post here that they used it with Alsa and Audacity, but I would like to be able to use it with Jack too.

Anyone have this microphone, and know if it works.

I'm currently running 10.04, but may upgrade if I need to. :)

---

### Post by AutoStatic on 2011-02-25
If it works with ALSA and Audacity it will also work with JACK. JACK is not a driver stack, it's a sound daemon that can use the ALSA driver stack as its backend.

Best,

Jeremy

---

### Post by ragtag on 2011-06-05
Just an update, in case anyone else is considering getting a Blue Yeti. I've used it with Ubuntu 10.04, and it was completely unproblematic. Just plug it in and choose it as an input/output device from the sound preferences. The sound quality was nice too, at least for some home recording.

:guitar:

---

### Post by veli on 2011-06-12
Blue Yeti works for me as well (10.04). As ragtag mentioned, choose it in pulseaudio preferences input tab. Also, if you use jack, in jackcontrol/setup you have to select it as input device. I record my kid playing the violin (with Ardour). The mic is pretty good for the quality and money. Here is a sound sample:
[http://dl.dropbox.com/u/6667604/bach%20sonata%202_may%2015%202011.wav](http://dl.dropbox.com/u/6667604/bach%20sonata%202_may%2015%202011.wav)

---

### Post by weudel on 2011-06-12
No issues on 11.04 with my Yeti either..

---

### Post by jeeradate on 2011-08-10
Blue Yeti is workable for me on Unbuntu 10.10 too but there is no sound on the monitoring head phone by default.

The solution to the monitoring head phone is in below link. 

[http://ubuntuforums.org/showthread.php?t=1635050]("http://ubuntuforums.org/showthread.php?t=1635050")

---

### Post by hoboghost on 2012-02-05
I have Ubuntu 11.04 on an Atom 1.6 processor notebook with 3 gigs of ram and a 500GB HD.

The Blue Yeti mic works on Audacity for the first track just fine.  I have trouble recording additional tracks.

At first it would not record a second track at all citing latency problems.

I fiddled with settings and GNOME ALSA mixer and got it to record additional tracks but the recording was cutting in and out at a fast speed, creating unusable tracks.

Once in a while it will record a good additional track without issue, but it is not consistent.

If I delete all the tracks, and record just one again, it does so without issue.

Maybe I have a driver problem; I am not sure.

Audacity works fine with the built in microphone, so I'm not quite sure what is going on.

---

