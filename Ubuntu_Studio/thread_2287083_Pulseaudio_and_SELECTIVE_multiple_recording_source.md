---
title: "Pulseaudio and SELECTIVE multiple recording sources."
date: 2015-07-16
forum: Ubuntu Studio
---

### Post by halfnote52 on 2015-07-16
Hi all!
Is there any way using Pulseaudio (which seems to be the standard on this new flavor of Xubuntu) for recording from multiple interfaces? 

I CAN'T use the null sink because I DON'T want system sounds and I DON'T want all mics. 

I want to be able to, say, specify that I want mic 1, 2, 4, 7 and 9, but NOT 3, 5, 6, 8, OR the cheesy onboard mic. 

It's be especially good (necessary, really) if I could get them all to record to separate channels. 

I've had bad luck monkeying with jack - succeeding in breaking my system sounds temporarily when Cadence killed the ~/.pulse/  files' auto-restart/persistence, but NO luck actually recording anything from anywhere. 

By the way, I'm using Xubuntu Vivid Vervet on an Intel core i5 64-bit machine. Desktops are XFCE and Cinnamon, (that last bit which shouldn't make a difference, but I just KNOW someone's gonna ask.) ; )

---

### Post by TheFu on 2015-07-16
I haven't tried it,but [https://ardour.org/features.html](https://ardour.org/features.html) seems to have what you seek.  I'll be monitoring this thread in hopes of a good answer.  

OBS [https://obsproject.com/](https://obsproject.com/) just isn't stable enough under Linux to be useful at this stage. I've only had about 20 min of recording work under Linux, but almost 3 hrs under *another OS,* cough, muxing multiple audio and video channels together into a final output video.

Good luck.

---

### Post by halfnote52 on 2015-07-16
Nnnope. It uses jack. Looks **gorgeous** though. Wish I could swap out pulse and have the default audio preview and stuff work.

---

### Post by jejeman on 2015-07-17
Ardour4 works with ALSA, no need for JACK.
Problem is multiple interfaces. Ask some one with ALSA knowledge to help you set it. Or maybe, if it is possible, run two JACK servers, with two recording apps.

---

### Post by halfnote52 on 2015-07-17
So I'm guessing that going through Pulse is, in fact, either not possible, or at the very least not advised?

(Only I'd like to NOT have to disable/re-enable my system sounds every bloody time I want to switch over and listen to something via the onboard headphone jack. = /

---

### Post by halfnote52 on 2015-07-17
(Also, I should mention for techincal accuracy that I keep getting a "Can't start jack" error due to the fact that pulse is still running)

---

