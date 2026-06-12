---
title: "Audio distortion on JACK"
date: 2009-04-04
forum: Ubuntu Studio
---

### Post by teel on 2009-04-04
Hi there,
I'm having problems with sound quality with JACK running and PREEMPT RT kernel (Ubuntu Studio 8.04.2, 2.6.24-23-rt)

When I start JACK and QSynth the first minute it is ok but then an xrun appears and some time after this effect (xrun itself does not destroy the audio in this case): [http://inet24.pl/~morales/export.wav](http://inet24.pl/~morales/export.wav)

Now, starting or stoppin recording in Ardour or restarting QSynth causes the audio to return to normal state. Anyone has any idea on what may be wrong?

Regards,
teel

---

### Post by babarosa on 2009-04-04
Hi,

which soundcard/interface do you use?

Did you adjust etc/security/limits.conf file as adviced in very many threads in this forum? (use the search function!).

For example this one:
[http://ubuntuforums.org/showthread.php?t=965611&highlight=babarosa](http://ubuntuforums.org/showthread.php?t=965611&highlight=babarosa)

Regards, Michael

---

