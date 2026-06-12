---
title: "Ardour- can't record when opening old session"
date: 2009-06-05
forum: Ubuntu Studio
---

### Post by mypetjaws on 2009-06-05
Hello all-

This is strange. I can record, playback, do everything fine with Ardour and my Firepod / FP-10...very happy with the results!

However I have noticed, for some odd reason, that when opening an old session, I lose the ability to record. I don't think ardour is recognizing my inputs. 

First, I just opened an old session without starting jack first. I did this because when I started the session originally I had used Ardour to automatically start jack itself. So, I assumed upon opening the session everything would resume as before. When the firepod wasn't detected (light remained red) but I saw that Ardour was running in realtime, the confusion started. SO-

I shut down Ardour, started qjackctl first, made sure the firepod was detected, then started ardour and went into the same previous session. Still, no recording/monitoring ability on the track I had recorded already, or on any new tracks that I add.

After this, I went into the mixer (alt+m) to try to fiddle with the inputs. I was able to have "master" detect the firepod, monitor the input, etc. I clicked the "input" button under 'master' and chose "in1+2'
 which is the first 2 in's on the firepod. However, for the track inputs, this option is not present. I rescanned a bunch of times, nothing detected.

I'm slightly baffled.
Shouldn't ardour save the state a session was in when I save and quit?
Is there something I'm not doing when I save and quit?
Is ardour not implementing FFADO when opening an old session (ALSA is the default, but there is no option to adjust this when opening an old session)?

Any help would be much appreciated, even links to similar threads, etc.
Thanks!

---

### Post by Firepod on 2009-06-07
Is it only with legacy ardour files or are you unable to record with multi-track format period? If so, I am having the same problem. I can record solo, playback solo, but cannot record WHILE playing back the sound.

Please let me know if we are having the same problem. Although neither of us may have the solution, at least we can band our efforts together and more likely solve this issue.

Looking forward to hearing your response

---

### Post by mypetjaws on 2009-06-09
Hhaha...turns out my problem is that I'm a knucklehead. It's so dumb I don't even want to tell you. I can record while playing back. When I record on a second track the first plays back automatically.

In reference to your problem, what exactly is wrong- when you add a second track you can't record on it? Or is it that you can record a second track, but when you do the first track doesn't playback while you're recording?

While I don't have much info about your problem at the moment, I'll suggest this: If you open a new session, don't start qjackctl first. Allow Ardour to start jack itself. When you do this, in the startup window for Ardour an "Audio Setup" tab is present. You can choose FFADO as the driver. See if fiddling with these presets makes any improvements.

The only problem I've had with this is that if you open an old session without starting jack first, Ardour starts jack but the firepod doesn't get detected. However, the simple workaround is just that you first start qjackctl independently before opening Ardour to go into any old sessions.

Just out of curiosity, is the 'mixer' knob on your firepod at 12 o'clock? it's the knob below the headphone volume and main level knobs. It's has to be at 12 o'clock to enable both monitoring and playback (all the way to the left is monitoring only, all the way to the right is input 1 + 2 playback only).

Hope this helps!

---

