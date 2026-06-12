---
title: "How to switch to hdmi audio?"
date: 2012-03-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by 749 on 2012-03-20
In Ubuntu 11.10 it was really simple, System setting -> Sound and you could choose any output recognized by the system; in 12.04 there is no more hdmi audio output. Is this a bug? Does anyone know how to fix it?
Tried on two different computers, both working with 11.10.

---

### Post by skewty on 2012-03-20
What is the bug # for this?  I might see if I too suffer from the same issue later this evening.

---

### Post by 749 on 2012-03-20
No idea, I don't even know if there is an open bug on launchpad, I did a quick search but couldn't find it. Anyhow I'm not sure which package should be checked.

---

### Post by Gregory Lee on 2012-03-20
> **749 said:**
> Anyhow I'm not sure which package should be checked.
Alsa, I'd guess.  I don't have hdmi sound, myself.  Here's a web page that might be a help: [http://wiki.xbmc.org/index.php?title=HOW-TO:Setup_HDMI_audio_on_GeForce_GT210,_GT220,_or_GT240](http://wiki.xbmc.org/index.php?title=HOW-TO:Setup_HDMI_audio_on_GeForce_GT210,_GT220,_or_GT240).

---

### Post by 749 on 2012-03-20
I don't think there is any issue about alsa, I checked audio output with hardinfo and hdmi is correctly recognized. Also, xbmc lets me choose it, so I guess the fact sound output can't be switched in System Settings is a sort of graphical issue.

---

### Post by 749 on 2012-03-21
These pictures explain what I'm talking about.

---

### Post by 749 on 2012-03-21
Whoever might be interested, this is the bug on launchpad: [Bug #961286]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/961286")

---

### Post by Harry33 on 2012-03-22
> **749 said:**
> Whoever might be interested, this is the bug on launchpad: [Bug #961286]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/961286")

You should post a bit more info here (graphics card, drivers etc.).
Precise setup will automatically show the HDMI output option if it is available.
I have two setups with HDMI output, one with ATI graphics card (open source drivers) and one with NVidia graphics card (proprietary drivers).
The HDMI output is clearly visible in "System Settings" - "Sound" - "Output" -tab.

---

### Post by 749 on 2012-03-22
Actually I tried on both AMD (open source drivers) and Nvidia (latest proprietary version). Now the bug is investigated against the Nvidia system, you can find very accurate details on launchpad.

---

### Post by dilodicus on 2012-03-24
I experience the same problem with 12.04 x64, HDMI audio not recognised, only option is built in speakers.
sys specs:
Dell Inspiron n411z
Intel core i5 2430m (on die GPU, no discrete controller)
4GB RAM
640GB HDD


Just tried the fix in the bug listing on launchpad, worked a charm!!

------------------------------------
edited /usr/share/pulseaudio/alsa-mixer/paths/hdmi-output-0.conf

required-any = any
edited to:
required = ignore

in terminal enter "pulseaudio -k"
-------------------------------------

THANK YOU David Henningsson, works perfectly now :)

---

