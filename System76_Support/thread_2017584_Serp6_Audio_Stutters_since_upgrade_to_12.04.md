---
title: "Serp6 Audio Stutters since upgrade to 12.04"
date: 2012-07-05
forum: System76 Support
---

### Post by ShokTHX on 2012-07-05
Since updating to 12.04 my Serp6 has developed a stutter.
It's almost a perfect Ma, Ma, Ma, Max Headroom effect.
This happens on all playback audio, MP3's and even CD's.

How can I fix this?

---

### Post by Bufke on 2012-07-06
I just started having a stutter problem with my gazp6. Can you describe your issue more? 

For me it will randomly repeat small bits of audio, usually less than a second. It will happen once every 30 seconds to a several minutes. Very annoying. Headphones or laptop speakers make no difference. It happens with flash and rhythmbox.

I can't reproduce it reliably, it's very random. Maybe an update? Maybe something related to the high heat I'm having? I checked cpu temp but it's at a tolerable 50C. Stressing out the computer with glxgears doesn't reproduce it. I don't see anything obvious in syslog.

---

### Post by mgolden on 2012-07-07
I saw this today for the first time, I believe.  I managed to eliminate it by killing the pulseaudio process, which restarts itself and everything was fine.

---

### Post by ShokTHX on 2012-08-17
I'm still having this problem. Pretty much exactly as Bufke describes as far as the symptoms.

---

### Post by isantop on 2012-08-17
You did an upgrade to 12.04, rather than a fresh install, right? Try it from a LiveCD. I'm guessing that the problem won't occur there.

---

### Post by ShokTHX on 2012-08-21
I have now done a complete clean re-install (still installing software and copying files back).

It is still happening although it could be a just a bit less.

James

> **isantop said:**
> You did an upgrade to 12.04, rather than a fresh install, right? Try it from a LiveCD. I'm guessing that the problem won't occur there.

---

### Post by mgolden on 2012-08-23
I have a GazP6, and I sometimes have this as well.  It seems to be related to the use of Chrome.  I never have it when I use Firefox.

That happening to you?

---

### Post by ShokTHX on 2012-08-23
No, I don't think this is a browser issue. This same stutter occurs in Rhythmbox playing MP3's.

James

---

### Post by jdnier on 2012-08-23
Same problem here on a Gazelle Professional i7, GeForce 560M (using nvidia's driver). I've been running 12.04 all along. Seems like every second or third google-chrome update Flash gets screwed up (videos running at super speed). This cycle of Flash breaking (super speed problem), then eventually getting fixed, then breaking again has happened several times for me with 12.04. However, it's not just Chrome: I have the same Flash problem in Firefox, although it's even worse in Chrome. 

Recently (this week) I started having similar stuttering for audio (e.g., Spotify app).

I have no clue what's going on, but am very tired of 12.04's instability...

Thanks for any suggestions.

---

