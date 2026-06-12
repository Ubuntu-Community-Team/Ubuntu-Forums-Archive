---
title: "Levelling out volume for audio tracks. how to do it?"
date: 2014-03-27
forum: Ubuntu, Linux and OS Chat
---

### Post by DisappearingOak on 2014-03-27
I'm looking for an audio player that will help me achieve this:
For normal volume files, I'll adjust hardware volume knob to match them. For other files that are high volume due to poor source, or recording, I want something that will level out all sound exceeding a certain limit that I set while not touching other portions, just the higher volume portions. What audio player will effectively help me achieve this? THanks.

---

### Post by Thee on 2014-03-27
I don't think there is any player that will allow you to do that.

What you can do is, use an audio editor like Audacity to manually adjust the audio level of the files that you need. I believe the "Normalize" option in Audacity would be of help.
[http://wiki.audacityteam.org/index.php?title=Amplify_and_Normalize](http://wiki.audacityteam.org/index.php?title=Amplify_and_Normalize)

---

### Post by DisappearingOak on 2014-03-27
> **Thee said:**
> I don't think there is any player that will allow you to do that.

What you can do is, use an audio editor like Audacity to manually adjust the audio level of the files that you need. I believe the "Normalize" option in Audacity would be of help.
[http://wiki.audacityteam.org/index.php?title=Amplify_and_Normalize](http://wiki.audacityteam.org/index.php?title=Amplify_and_Normalize)

I found that using Audacious (the music player, not Audacity) with a LADSPA software dsp called Fast Look Ahead Limiter seems to do the trick. (I think, have to test everything properly now). Linux can be frustrating sometimes, with PulseAudio I got tiny distortions and clicks in my music which had me upset at the sound coming out of my new hifi speakers. I've removed PulseAudio and now to test if everything is working well. I never, NEVER had any skips, clicks, or distortions on Windows XP with foobar2k.

---

### Post by Jonor on 2014-03-27
If you would be willing to provide a simple step-by-step how-to of getting it working in Audacious i would appreciate it.
Currently i attempt a similar effect by editing with Audacity using popmute/normalize/amplify.

---

### Post by andrew.46 on 2014-03-30
> **DisappearingOak said:**
>  I never, NEVER had any skips, clicks, or distortions on Windows XP with foobar2k.

If your heart is set on foobar I believe that it will run under wine ....

---

### Post by ssam on 2014-03-31
Have a look at [https://en.wikipedia.org/wiki/Replay_Gain](https://en.wikipedia.org/wiki/Replay_Gain)

---

### Post by David_Wright on 2014-03-31
Further to **ssam's **reply above - the linked article mentions **MP3Gain **which I understand scans your entire MP3 library and makes *non-destructive* changes to the MP3 files so as to balance the entire library.

I haven't used it yet (halfway through, finally, digitising my entire CD collection) but have bookmarked it for this purpose.

---

### Post by DisappearingOak on 2014-03-31
Okay, I was using Dynamic Compressor and Fast Look Ahead Limiter. I tried both system-wide >> [http://askubuntu.com/questions/95716/automatically-adjust-the-volume-based-on-content](http://askubuntu.com/questions/95716/automatically-adjust-the-volume-based-on-content)
and also using Audacious' LADSPA effect (had to install swh-plugins ubuntu package). It seems to work, definitely, it lowers high volume on the fly, but I think I probably need to tweak the settings because it is lowering the high volume parts too much, making songs sound unnatural. In the end, I've just applied ReplayGain tags with mp3gain and metaflac. I might give the Dynamic Compressor thing another go in the future.

---

