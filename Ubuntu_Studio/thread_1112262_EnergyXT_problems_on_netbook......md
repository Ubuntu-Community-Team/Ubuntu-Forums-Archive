---
title: "EnergyXT problems on netbook....."
date: 2009-03-31
forum: Ubuntu Studio
---

### Post by fracturedmorals on 2009-03-31
Okay, So here's my deal:

I KNOW there's a way to do this.

I've been fiddling around with using my netbook (A Dell Inspiron Mini 9) as a sort of mobile music-creation suite.

I've got Renoise, and EnergyXT 2.5 installed.

Renoise seems to work okay(ish) and energyXT ...well....doesn't.

Audio playback under ALSA works, but is very VERY stuttery, playback under JACK is a nightmare that locks EnergyXT up.

I'm actually using the Jaunty beta with PAM configured to allow users of the "audio" group to use Realtime audio.

I don't have a realtime-patched kernel, and never really saw the need for one, as I've never really had TOO many latency issues.

Any ideas?

---

### Post by simtaalo on 2009-04-01
you shouldn't need the realtime kernel for using energy xt.

could you provide a screenshot of the sound settings option box?

---

### Post by danflash on 2010-02-14
you need to add some .cpp file and compile a couple of things so that EnergyXT can use Jack.

Google 'EnergyXT Jack Ubuntu' - there's a few complete howto's out there, and all are very very easy to follow and do.

In my experience - Ubuntu doesn't like XT's MIDI stuff really at all.  Neither does Fedora.  Or any other distro I tried for that matter. (in the end I paid the $50 US for the Indamixx Transmission OS, and now this netbook screams and EnergyXT is finally very happy to play nice)

Depending on your needs you might have success though.

---

### Post by hxcobd on 2010-02-14
> **fracturedmorals said:**
> 

I'm actually using the Jaunty beta with PAM configured to allow users of the "audio" group to use Realtime audio.

I don't have a realtime-patched kernel, and never really saw the need for one, as I've never really had TOO many latency issues.

Any ideas?

I was under the impression that you couldn't use realtime audio UNLESS you had a realtime kernel...?

---

### Post by AutoStatic on 2010-02-15
You can. You don't need a realtime kernel for realtime audio. You do need to set your permissions right: create an audio group if it doesn't exist yet, add your account to it and add the following lines to your */etc/security/limits.conf*:
```
@audio - rtprio 90       # maximum realtime priority
@audio - memlock unlimited  # maximum locked-in-memory address space (KB)
```

That should do the trick.

---

