---
title: "No sound in your Wine apps? Remove pulseaudio."
date: 2009-09-02
forum: Wine
---

### Post by sherl0k on 2009-09-02
Apparently, sound issues with Wine is quite the problem. In nearly all cases I've come across, though, PulseAudio is always the culprit.

**Why?**

Well, it's simply because Wine doesn't support it. Sure some apps will work through pulse, but anything that's really intensive on the sound card - games, music apps, and the like - will toss errors or give no sound.

**What else could I try instead of removing it?**

You could try piping the app through padsp "padsp wine apphere.exe" - but that induces sound lag, and doesn't always work. To go a step further, pipe it through padsp and THEN aoss - "padsp aoss wine apphere.exe" but now you get even more lag, and still no guarantee that it works.

**So how do I go about removing it?**

Either remove the pulseaudio package through synaptic or through the console - 'sudo aptitude remove pulseaudio' - and then reboot. ALSA is still there, you get all your sound, and you don't have to worry about pulse interfering with your apps.

**What do I lose by removing pulse?**

Mainly two things: network streaming of your audio, and per-application volume levels. If you can live without these two features, you can live without pulse.

**Other apps broke after removing pulse!**

Any app that supports pulse, supports ALSA by default. Remember, pulse is just a layer on top of ALSA. Chances are your sound preferences for that app just need to be changed.

**I want to bring pulse back.**

Then just re-install it via synaptic or the console.



I hope this helps people out with solving their Wine issues, and can live without the few amenities of pulse. :) The sound system just seems to cause more problems than offer solutions.

---

