---
title: "no sound ubuntu 18.04 after last updates"
date: 2018-01-11
forum: Ubuntu Development Version
---

### Post by rburkartjo on 2018-01-11
just me or anyone else /tks

---

### Post by jimmy-frydkaer on 2018-01-11
No sound here either but if I fire up youtube the sound is there with out possibility of controlling volume at all

---

### Post by zika on 2018-01-12
> **rburkartjo said:**
> just me or anyone else /tksPulseAudio refuses to (re)start.
> **jimmy-frydkaer said:**
> No sound here either but if I fire up youtube the sound is there with out possibility of controlling volume at allBecause browser reverted to ALSA.

---

### Post by vasa1 on 2018-01-12
Which browser would that be?

Firefox 57.0.1 YouTube videos have audio and the volume slider works.

VLC 3.0.0-rc4 Vetinari works.

OP, could you please be more verbose?

---

### Post by zika on 2018-01-12
> **vasa1 said:**
> Which browser would that be?The one (s)he've opened YT in...
It should work now:```
pulseaudio (1:11.1-1ubuntu4) bionic; urgency=high

  * 0030-load-module-switch-on-connect.patch: **Correct typo in default.pa**
    _causing pulseaudio startup failure_. (LP: #1742750, LP: #1732629)
  * Refresh patches to apply more cleanly:
    - 0802-alsa-mixer-Add-support-for-usb-audio-in-the-Dell-doc.patch
    - 0803-build-sys-add-the-Dell-dock-TB16-configuration.patch


 -- Daniel van Vugt <daniel.van.vugt@canonical.com>  Fri, 12 Jan 2018 10:23:11 +0800
```
Update&#8321;: It does work now as good as before the upgrade of yesterday's with typo...

> **vasa1 said:**
> Which browser would that be?
Firefox 57.0.1 YouTube videos have audio and the volume slider works.
VLC 3.0.0-rc4 Vetinari works.
OP, could you please be more verbose?You've edited post of Your's so to clarify: there was an upgrade of PA in the meantime with a typo in default.pa. Solved by latest upgrade. If You did not upgrade in the meantime You would not notice any trouble... ;)

---

### Post by vasa1 on 2018-01-12
I'm not sure that Firefox 57 can "revert to ALSA". They dumped ALSA some versions ago causing much distress to Lubuntu users.

---

### Post by zika on 2018-01-12
> **vasa1 said:**
> I'm not sure that Firefox 57 can "revert to ALSA". They dumped ALSA some versions ago causing much distress to Lubuntu users.Chromium can. Not automagically, true... I do use```
--alsa-output-device=iec958:CARD=DAC,DEV=0
```for my preferred device... I needed that yesterday before noticing typo in defult.pa... I was not following Ff closely lately but this could be helpfull for those in distress: [https://codelab.wordpress.com/2017/12/11/firefox-drops-alsa-apulse-to-the-rescue/](https://codelab.wordpress.com/2017/12/11/firefox-drops-alsa-apulse-to-the-rescue/) :=)

---

### Post by vasa1 on 2018-01-12
That's why I asked. We were going on about the Firefox/ALSA story here: [https://ubuntuforums.org/showthread.php?t=2355092](https://ubuntuforums.org/showthread.php?t=2355092)

---

### Post by zika on 2018-01-12
> **vasa1 said:**
> That's why I asked. We were going on about the Firefox/ALSA story here: [https://ubuntuforums.org/showthread.php?t=2355092](https://ubuntuforums.org/showthread.php?t=2355092)Nice. I'm tunnel-visioned only to this forum... ;)

---

### Post by rburkartjo on 2018-01-12
this mornings updates fixed issue/tks

---

### Post by cariboo on 2018-01-12
Sound works again for me on Xubuntu, but I don't have a speaker icon, or access to sound settings.

---

### Post by jfrancl on 2018-04-27
I've always had a problem with sound after an upgrade. What worked in the past was to download ALSA Mixer and check the "Enable Audigy Analog/Digital Output". It's always baffled me as to why I would have to do such a strange thing, but it's always worked. ALSA Mixer has been redesigned now, and that option isn't available. I'm at a loss as to what to do. Maybe enable the onboard sound?

---

### Post by cariboo on 2018-04-27
Thread Closed. If you are still having problems, please start a new thread in [General Help]("https://ubuntuforums.org/forumdisplay.php?f=331").

---

