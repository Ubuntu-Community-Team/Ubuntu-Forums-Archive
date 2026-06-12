---
title: "JACK audio inside VirtualBox VM?"
date: 2017-05-11
forum: Virtualisation
---

### Post by &amp;KyT$0P# on 2017-05-11
Is it possible to have JACK audio inside a Xubuntu 16.04 VirtualBox VM?  If so, how to do it?

So far, the best I've done is this.  By selecting "Yes" for enabling realtime while installing qjackctl and jack-tools, and adding myself to the [FONT=Courier New]audio[/FONT] group, JACK and associated programs don't hang and crash.  But there is no sound.

Everything else I've tried either had no effect or made things worse.

Internet searching only turned up stuff related to using JACK on the host.  That is not what I'm looking for.  What I'm looking for is to try out, inside the VirtualBox guest, some programs that depend on JACK.  (Unfortunately I don't have a bare-metal system I can use for this.)

Any help would be appreciated.

---

### Post by &amp;KyT$0P# on 2017-05-20
bump

---

### Post by &amp;KyT$0P# on 2017-05-26
bump

---

### Post by Bucky Ball on 2017-05-27
In Virtualbox, NOT while the virtual machine is running, click on the virtual machine and check its settings. Under 'Audio' what do you have selected there for 'Host Audio Driver' and 'Audio Controller'? You may need to experiment, but generally you would use 'Pulseaudio' for the former and 'ICH AC97' for the latter.

Just a word about audio in a virtual machine, though. If you are intending to do resource heavy audio production/editing, I would never do that in virtual box. Not the environment for anything pro-audio-ish. This applies even more so to graphics and video production.

---

### Post by &amp;KyT$0P# on 2017-05-27
> **Bucky Ball said:**
> In Virtualbox, NOT while the virtual machine is running, click on the virtual machine and check its settings. Under 'Audio' what do you have selected there for 'Host Audio Driver' and 'Audio Controller'? You may need to experiment, but generally you would use 'Pulseaudio' for the former and 'ICH AC97' for the latter.
Host audio driver is PulseAudio (only one that works for me) and Audio Controller was ICH AC97.  I'm trying the 'Intel HD Audio' audio controller, but still not hearing any sound from JACK.

> Just a word about audio in a virtual machine, though. If you are intending to do resource heavy audio production/editing, I would never do that in virtual box. Not the environment for anything pro-audio-ish. This applies even more so to graphics and video production. 
Yep.  I don't particularly expect this to become a production environment.  I'm just trying out some apps to see whether they would be useful to me.

---

### Post by &amp;KyT$0P# on 2017-06-12
bump

---

### Post by &amp;KyT$0P# on 2017-06-20
bump

---

### Post by &amp;KyT$0P# on 2017-06-28
#-o

Well, this is embarrassing.  The "no sound" problem was only because I didn't know I had to **manually** connect jack-play to JACK from inside qjackctl's Connections window!

Also, the instability in JACK seems to be mostly gone if I set qjackctl > Setup > Settings > Advanced > Audio: Playback Only.

But, there is still one last problem.  While I now have sound from [FONT=Courier New]jack-play[/FONT], it sounds like it's pitched waaaaay down and slowed waaaaay down.  I tried changing the JACK sample rate, frames/period, and periods/buffer, but none of that brought the sound to normal speed.

[FONT=Courier New]paplay[/FONT] and [FONT=Courier New]aplay[/FONT] both work fine.

How to fix this last JACK issue?

---

### Post by Bucky Ball on 2017-06-28
Can't help you there, but might help your chances of support if you mark this as solved and start a new thread. This older and its title unrelated to your current issue. Good luck.

---

### Post by &amp;KyT$0P# on 2017-06-28
Thanks Bucky Ball. :KS

[https://ubuntuforums.org/showthread.php?t=2364834]("https://ubuntuforums.org/showthread.php?t=2364834")

---

