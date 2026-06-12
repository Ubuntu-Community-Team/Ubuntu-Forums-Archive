---
title: "Frustrated with ardour and jack control"
date: 2010-04-22
forum: Ubuntu Studio
---

### Post by shanehaua on 2010-04-22
Hi,
I had ardour and jack going fine. now it just won't play when i use the transport buttons on either jack or ardour. Please help me to stop tearing my hair out. I am using 9.10 studio.

---

### Post by trulan on 2010-04-22
You mean it doesn't play, as in, nothing moves, Ardour doesn't respond at all, or, it doesn't play, as in, it looks like it is playing but you can't hear anything?

---

### Post by shanehaua on 2010-04-22
> **trulan said:**
> You mean it doesn't play, as in, nothing moves, Ardour doesn't respond at all, or, it doesn't play, as in, it looks like it is playing but you can't hear anything?

When I click the play icon the stop icon stays lit and nothing happens.....

---

### Post by cub on 2010-04-23
I understand it worked before? And now it doesn't? Has anything changed? As for me I have an external soundcard with a couple of small switches on the back, if one is changed JACK won't run with the settings I used before.

---

### Post by sgx on 2010-04-24
> **shanehaua said:**
> Hi,
I had ardour and jack going fine. now it just won't play when i use the transport buttons on either jack or ardour. Please help me to stop tearing my hair out. I am using 9.10 studio.
Hi, I have seen where using audio apps that access OSS or alsa, instead of jackd, can produce a condition where the soundcard you selected earlier,
shifts posting in the naming conventions used to set preferences in qjackctl. In the qjackctl Setup page, on the  right side, halway down,

Input device   >
Output deveice >

click the >   to see your available sound devices, and choose the one you want, then check to make sure Ardour has seen that device, and choose it
in Ardour preferences, if that is required.

On my computer, I had to blacklist the motherboard soundchip to prevent
this realignment repeating itself after watching a movie, playing mp3s etc

---

### Post by shanehaua on 2010-04-25
> **sgx said:**
> Hi, I have seen where using audio apps that access OSS or alsa, instead of jackd, can produce a condition where the soundcard you selected earlier,
shifts posting in the naming conventions used to set preferences in qjackctl. In the qjackctl Setup page, on the  right side, halway down,

Input device   >
Output deveice >

click the >   to see your available sound devices, and choose the one you want, then check to make sure Ardour has seen that device, and choose it
in Ardour preferences, if that is required.

On my computer, I had to blacklist the motherboard soundchip to prevent
this realignment repeating itself after watching a movie, playing mp3s etc

Thanks, will try that.

---

