---
title: "Wine + TF2 + Sound"
date: 2009-05-02
forum: Wine
---

### Post by Jesst3r on 2009-05-02
Hey all,

I'm just wondering if anybody is able to play TF2 with wine on 9.04.  I keep getting an error about 3/4 through loading the maps that says:  " CAudioSourceMemWave (random sound file) GetDataPointer failed"

I've searched long and hard for solutions, but I can't seem to get anything to work.  I've tried:
- Disabling microphone boost
- Disabling mic all together
- Disabling community stuff in game
- Emulating without Driver Emulation (??)
- Emulating with Driver Emulation
- Disabling ALSA (the only sound enabled)
- Using Windows Vista simulation (Doesn't let me load steam at all because of some service)

The only thing that lets me play is disabling ALSA, but then I get no sound at all.  This is obviously not all that fun, so a solution that actually fixes the sound would be super swell.  

Thanks for any help you can provide.  This seems to be a pretty common bug, so hopefully somebody knows how to fix it.

---

### Post by Jesst3r on 2009-05-03
Shameless bump

---

### Post by olaboy- on 2009-05-03
I read getting rid of the pulseaudio drivers while leaving alsa makes it work.

---

### Post by Jesst3r on 2009-05-03
Running "killall pulseaudio" before trying didn't help any.  I don't imagine uninstalling the stuff all together would help much since I've got the driver set to ALSA in the wine configuration.  I guess I could be wrong though.

Does the CAudioSourceMemWave stuff sound like something wine would be doing, or something TF2 would be doing?  

BAH, this is the only thing keeping me on windows, so it'd be really nice to get it working :(

---

### Post by Jesst3r on 2009-05-03
Ok, so, question from a complete noob.  Is ALSA linked to pulseaudio at all?  After I ran that killall command, i noticed that I didn't have any sound at all unless i switched to OSS.  ALSA didn't work anymore.  Once I ran pulseaudio -k and then pulseaudio -D --log-target=syslog, everything came back to life.  

So yeah, is ALSA linked to puseaudio?  Should I try completely uninstalling all pulseaudio stuff I can find to try to fix this TF2 issue?  

Man I wish I knew what I was doing haha

---

### Post by u235sentinel on 2009-05-04
> **Jesst3r said:**
> Ok, so, question from a complete noob.  Is ALSA linked to pulseaudio at all?  After I ran that killall command, i noticed that I didn't have any sound at all unless i switched to OSS.  ALSA didn't work anymore.  Once I ran pulseaudio -k and then pulseaudio -D --log-target=syslog, everything came back to life.  

So yeah, is ALSA linked to puseaudio?  Should I try completely uninstalling all pulseaudio stuff I can find to try to fix this TF2 issue?  

Man I wish I knew what I was doing haha

Me 2.  I have everything except the Mic working and it's annoying.  You would think something this popular would have the mic working too :/

---

### Post by Jesst3r on 2009-05-04
This is getting crazy frustrating!!

I followed two different guides to remove pulseaudio because I was apparently missing parts of each.  

[http://www.ubuntugeek.com/how-to-remove-pulse-audio-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-remove-pulse-audio-ubuntu-810-intrepid-ibex.html)
[http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/](http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/)

pulseaudio isn't in the list in wine anymore, but it is still in the dropdowns in System->Preferences->Sound.

I'm assuming everything's removed, but I'm still getting this error.

Is anybody able to play TF2 in Jaunty?  If so, do you have pulseaudio installed?  What are your TF2 settings?  What are your wine settings?  What am I missing?

Thanks again for your help.

---

### Post by m00 on 2009-05-12
Hello, it doens't seem to work on Jaunty, I am having the same error as well, 
```
CAudioSourceMemWave (vo\heavy_cartmovingforwardoffense13.wav): GetDataPointer() failed.
```

It actually happened on my previous distribution (ArchLinux). If I disabled my sound from winecfg (disable ALSA) it works. Any one knows how to make my sound work with this?

---

### Post by thelamer on 2009-05-22
The Spy Sniper Update broke it all together now. 

I have Pulse Killed and autorespawn disabled. Which worked, but only like half the time before and it does nothing now. 

I have a;

"GetDataPointer data failed" every time I load up a game or start my own. 

This happens regardless of settings. 

TF2+Jaunty=Fail

---

### Post by Jesst3r on 2009-06-10
Glad I'm not the only one who still gets this error. 

Think this is a Jaunty, Wine or TF2 issue?

---

### Post by NightMKoder on 2009-06-10
pasuspend wine ...

that'll make pulseaudio shut itself up. Try it.

---

