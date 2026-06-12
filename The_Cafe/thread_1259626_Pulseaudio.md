---
title: "Pulseaudio"
date: 2009-09-06
forum: The Cafe
---

### Post by ravalox on 2009-09-06
Is there a personification of pulse audio out there I can punch a few times?  Everything was working fine with Ubuntu until this came along.  Now I've got all these sound issues.

---

### Post by PurposeOfReason on 2009-09-06
So remove it?

---

### Post by hanzomon4 on 2009-09-06
What sound problems

---

### Post by qamelian on 2009-09-06
> **ravalox said:**
> Is there a personification of pulse audio out there I can punch a few times?  Everything was working fine with Ubuntu until this came along.  Now I've got all these sound issues.

Maybe everything was working fine on your hardware, but I don't ever recall a time when there weren't post complaining that two programs couldn't use sound at the same time or that sound was poor or just didn't work at all. Pulseaudio still has some growing pains to get through, but in my opinion, I'm getting better sound on both my laptop and desktop with PA that I did without.

---

### Post by ddrichardson on 2009-09-06
> **ravalox said:**
> Is there a personification of pulse audio out there I can punch a few times?  Everything was working fine with Ubuntu until this came along.  Now I've got all these sound issues.

Lennart Poettering. Works for Red Hat. Always found him to be very personable in his mailings.

Sure wouldn't punch him.

---

### Post by BuffaloX on 2009-09-06
> **ravalox said:**
> Is there a personification of pulse audio out there I can punch a few times?  Everything was working fine with Ubuntu until this came along.  Now I've got all these sound issues.

My wife had some audio issues too, she made this cool little Python proggie she calls Audio Tweaks.

[http://www.sandgreen.dk/index.php?side=python_uat]("http://www.sandgreen.dk/index.php?side=python_uat")

You can try to disable Pulse to see if it's really the problem, but if you remove Pulse, it won't help you reinstall it again.
Also don't mess with real-time kernel except if you really need it.

---

### Post by gradinaruvasile on 2009-09-06
Pulseaudio gave more headaches than solving problems. 
There are some programs that can use it well, but most of the programs cannot (there is support for it here and there but typically PA ends up using 100% of CPU and/or outputting crackling sound or crashing). I removed it from all computers i used with Ubuntu and the sound works the way it supposed to.
The promise of PA is great, but it just doesnt delivers. For the time being. It is around for 3 releases, but still not working properly. I am curious about karmic with its integrated PA support. Cause if will work as it is now... 
IMO PulseAudio is not there yet. ALSA was/is working great, it is an established standard and i really dont get the idea why PulseAudio must be pushed forward when is not ready. It makes Ubuntu/Linux look broken/difficult to use for newcomers who dont really get the idea of unstable software knowingly being included in an OS. Honestly, neither do i.

---

### Post by hanzomon4 on 2009-09-06
Pulse Audio did not replace ALSA it replaced esound

---

### Post by Exodist on 2009-09-06
Yea I am not real sure about PA atm. I belive we should have kept it in the repositories for a few work arounds, but held it back at least another year before pushing it into ubuntu. IMHO.

---

### Post by gradinaruvasile on 2009-09-07
> **hanzomon4 said:**
> Pulse Audio did not replace ALSA it replaced esound

I was referring to the PulseAudio/ALSA combination.

---

