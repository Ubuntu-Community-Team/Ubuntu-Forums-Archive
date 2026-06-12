---
title: "Virtual Box Sound Help"
date: 2009-06-13
forum: Virtualisation
---

### Post by NovaWasp on 2009-06-13
Alright,

Jaunty 32 bit, 2.6.30 Kernel

I have windows XP installed in VB PUEL, but I can't get the sound working at all.  

I go into settings for the machine select enable audio, ACH 97, and Pulse Audio.

XP then recognizes that there is a sound card but that it needs a driver.

I have configured all of the settings in Ubuntu's Sound Control Panel to use pulse Audio.  
I've added myself to all pulse and Virtual Box groups.

thoughts?

What other info would help?

thanks,

---

### Post by eival on 2009-06-13
try using a different audio driver, this is what i use for my windows xp vm

Host Driver
ALSA Audio Driver

Controller
ICH AC97

---

