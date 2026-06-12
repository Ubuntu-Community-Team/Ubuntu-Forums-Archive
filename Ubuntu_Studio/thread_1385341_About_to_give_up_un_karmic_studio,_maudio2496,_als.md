---
title: "About to give up un karmic studio, maudio2496, alsa."
date: 2010-01-19
forum: Ubuntu Studio
---

### Post by evozero on 2010-01-19
About to give up un karmic studio, maudio2496, alsa.
Hi all,
I am having a nightmare with karmic studio, and wanted to know if any one else has had all the same problems.
Fresh install, went very smoothly, booted up no problem.
Load jack, i got the usual memory limit warnings.
Tried studio controls, doesn't work, found out its a bug.
Manually edited the /etc/sec/limits.conf, working.
Then i get no sound through the maudio2496 ice1712, ok load up envy24 control,thinking the channels would be muted, no joy.
Tried Ardour, sound works, very odd...
Another day of messing around pulling my hair out, find out its another bug
edit the ICE1712.conf, it works!
So by this point i have spent a good few days on this, but think i have finally cracked it...
load LMMS, sound is completely screwed up, out putting garbage via Alsa, ok try jack, i get loads of messages about latency timings and keeps crashing out.
I have tried upgrading alsa, pulse, jackd, added the backports ( then i loose the RT kernel ) you name it!
I know lots of other people are having similar problems, so my question is what should i do next? My config is very basic, AMD2600, 1 gig ram, onboard sound card disabled.
I really want to use UBstudio, especially Ardour, LMMS, and the latest versions if possible, is this asking too much at the moment?
Sorry for the rant, and i am looking for some constructive suggestions.
Thanks
Ian

---

### Post by AutoStatic on 2010-01-19
> **evozero said:**
> I have tried upgrading alsa, pulse, jackd, added the backports ( then i loose the RT kernel ) you name it!Hello Ian, apparently you borked your system with this particular step. And LMMS doesn't work well with JACK, it's a known issue. I haven't got any more constructive suggestion than advising you to think about reinstalling and hope that JACK support for LMMS gets better soon. Or maybe you could try figuring out what you updated exactly, maybe you can roll back some stuff.

---

### Post by evozero on 2010-01-19
Thanks for the reply.
Well i am still hoping to make some progress, so i should clarify further. I was running UBS 8.10 before and didnt have these problems, i wanted the new versions of Ardour etc. So i decided to do a fresh install to 9.10. Thats when the above problems started.
I have just moved my Maudio card to my quad core 3.4g, 4GBram to see what happend. I have to go through the same mods to /etc/sec/limits.conf,ICE1712.conf to get the card working. No problem.
Then i load LMMS using ALSA, nothing! set LMMS to use Jack, works a bit with Xruns every 5 seconds or so, with the jack timeout increased. not a workable solution.
"upgrading alsa, pulse, jackd, added the backports." Reinstalled karmic 5 or 6 times.
This was done in desperation after trying lots of other individual steps.
I am just amazed that this card is not working out of the box, or at least tested, as it must be one of the most popular for studio? 
Is reloading 8.10 and upgrading the individual apps and RT kernal a good idea?
thanks
Ian

---

### Post by AutoStatic on 2010-01-19
No, I wouldn't advise upgrading, also because a lot has changed from 8.10 to 9.04.
LMMS is the bottleneck. It can't use ALSA because PulseAudio has already claimed the ALSA backend. So you have to kill PulseAudio first. Therefore you have to create a *~/.pulse/client.conf* with the following line:

*autospawn = no*

Then you can kill PulseAudio with **pulseaudio -k** and then LMMS can use ALSA. And LMMS doesn't work well with JACK. That has got nothing to do with JACK or your soundcard but everything with LMMS.

---

### Post by evozero on 2010-01-20
Thanks autostatic, i will give this a try.
Does appear that studio 9.10 hasnt been very well tested, if the most popular apps and hardware dont work together, and why use pule in the first place. Was there a reason?
Thanks
Ian

---

### Post by AutoStatic on 2010-01-20
Hello Ian, PulseAudio is tightly integrated with Ubuntu and since UbuntuStudio is built on top of Ubuntu it comes with Pulse too. But it can be disabled in a few steps. On my music PC I've disabled it completely, but on my notebook on which I do all my other stuff I prefer to keep it.
And about testing. Ubuntu is a free operating system which contains only free software. Most people who participate in the Ubuntu community do this on a voluntary basis. With that in mind I think they're doing a hell of a good job.

---

