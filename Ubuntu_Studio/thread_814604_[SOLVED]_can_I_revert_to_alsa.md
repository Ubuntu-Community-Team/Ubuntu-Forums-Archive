---
title: "[SOLVED] can I revert to alsa?"
date: 2008-05-31
forum: Ubuntu Studio
---

### Post by Kissell on 2008-05-31
I used to use Ubuntu Gutsy x64 and everything worked fine.

Now I use Ubuntu Hardy x64 and it switched my audio driver to be PulseAudio instead of ALSA.

PulseAudio works fine, except I need to use EKIGA and that software only sees ALSA, no pulseaudio devices.

When I go into SYSTEM, ADMINISTRATION, SOUND everything is set to PULSEAUDIO and if I test it they work...  but if I change them to ALSA they don't work.  :(

Is there a way I can get ALSA again working and use it instead of PulseAudio?

---

### Post by Stochastic on 2008-06-01
First I should make a note that this isn't really the forum to ask this in.  You should post any further questions on the subject into Multimedia & Video.  This forum is intended for professional multimedia production software, not softphones.  If I was lame, I would report your thread then refuse to answer it, but I'm not, so:

The best route I can advise is to use pulse audio as the main default server, as ekiga should soon support it, and then you haven't downgraded your system.  But for the time being, when you want to run ekiga do ```
pasuspender -- ekiga
```

This will temporarily suspend pulse audio while ekiga is running, the allow it to resume once ekiga closes - from what I read, I have yet to use it though.

---

### Post by chiefci on 2008-06-02
I drive a car, but I don't want to go back to a horse driving.
So, please try to use Pulseaudio and not Alsa.

Chief

---

### Post by Kissell on 2008-06-02
ALSA works great for everything I need it to do.

PulseAudio is not selectable inside of Ekiga software, which makes it worthless.  I must have audio for cheap international VoIP calls with my diamondcard account.

---

### Post by Kissell on 2008-06-02
BTW: Everything is working now, as I was able to make ALSA work again.

---

