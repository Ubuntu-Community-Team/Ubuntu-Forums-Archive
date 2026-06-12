---
title: "Ubuntu Studio 9.10 or 8.04?"
date: 2009-11-12
forum: Ubuntu Studio
---

### Post by homerj742 on 2009-11-12
I currently have 8.04 running, and have been contemplating the upgrade to 9.10 (clean install). You see, although 8.04 has been working pretty well, lately Jack has been disconnecting my sessions and I've been getting quite a few xruns (I've made multiple adjustments in jack to try and help but to no avail). 

is 9.10 stable compared to 8.04? Any suggestions would be greatly appreciated. Thank you!

---

### Post by trulan on 2009-11-12
I moved to 9.10 and have not regretted it.  Time will tell whether or not it will be as stable as 8.04 has been, and your mileage may vary.  9.10 is definitely a big improvement from 9.04, at least as far as the real time kernel is concerned.  I'd say go for it.

---

### Post by JC Cheloven on 2009-11-12
Perhaps you run in problems with pulse audio and your hardware. Things seem to be still a bit messy between pulseaudio and alsa, IMO. 

If that happens, it could be better to stay with 8.04, as uninstalling  pulseaudio (without breaking your system) is much easier in that than in 9.10. 

I would say: be prepared to try both, perhaps 9.10 as a first option.

---

### Post by homerj742 on 2009-11-13
Uninstalling pulseaudio is a problem in 9.10?

---

### Post by trulan on 2009-11-13
You'll have to research that.  I know it has been done.  I also know that a lot more of the sound chain (for example, the volume controls) has been turned over to Pulse rather than Alsa Mixer.  So I'm pretty sure it's a bit more involved to remove Pulse in Karmic.

I'm not a Pulse hater though - I've never had a problem with it.  But I know a lot of people would love to be rid of it.

---

### Post by markbuntu on 2009-11-13
If you are concerned about pulseaudio and jack not getting along, that has been mostly worked out by the pulse and jack devs so no worries there with 9.10

If you want to use 9.10 I would reccomend waiting a few weeks or months while the bugs are squashed.

---

### Post by AutoStatic on 2009-11-14
> **homerj742 said:**
> Uninstalling pulseaudio is a problem in 9.10?The uninstalling itself is not a problem. Yes, it uninstalls ubuntu-desktop also, that could have implications with updating and upgrading.
I wonder how many sound apps will still work properly though after uninstalling PulseAudio, and that includes stuff like Flash Player, system sounds etc.

---

### Post by homerj742 on 2009-11-15
> **markbuntu said:**
> If you are concerned about pulseaudio and jack not getting along, that has been mostly worked out by the pulse and jack devs so no worries there with 9.10

If you want to use 9.10 I would reccomend waiting a few weeks or months while the bugs are squashed.

Thanks for the recommendation. I guess I will wait and see what happens...

---

### Post by JC Cheloven on 2009-11-19
> **homerj742 said:**
> Uninstalling pulseaudio is a problem in 9.10?

Sorry, not anymore :-)  [http://ubuntuforums.org/showthread.php?p=8349609](http://ubuntuforums.org/showthread.php?p=8349609)

But it wasn't easy either. That way seem to break nothing, and fix the serious issues I had. I'm glad now. I can stay at ubuntu.

EDIT (a day after): Of course you loose the pulse volume icon in the panel.

---

