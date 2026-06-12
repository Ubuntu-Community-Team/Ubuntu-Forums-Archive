---
title: "PulseAudio"
date: 2010-09-16
forum: The Cafe
---

### Post by scottuss on 2010-09-16
I've been listening to some podcasts and reading some articles and everyone seems to bash PulseAudio.

I've read tonnes of support threads on the subject too, and by no means am I saying that I don't believe it has issues. 

However, my question is: Am I the only one who since Hardy hasn't had a single problem with PulseAudio. Not a blip, not a hiss, not a crash, not anything..?

---

### Post by blueturtl on 2010-09-16
You're not alone, aside from having to set my WINE to use ESD instead of ALSA output, there hasn't been a single hiccup for me really.

---

### Post by sandyd on 2010-09-16
> **scottuss said:**
> I've been listening to some podcasts and reading some articles and everyone seems to bash PulseAudio.

I've read tonnes of support threads on the subject too, and by no means am I saying that I don't believe it has issues. 

However, my question is: Am I the only one who since Hardy hasn't had a single problem with PulseAudio. Not a blip, not a hiss, not a crash, not anything..?
people are screaming at pulseaudio because 
a) its new, and it had a bad reputation from the start since Ubuntu implements pulseaudio terribly

b) you have no idea how many people have issues with alsa too, except that those users simply sit down with us and get help instead of uselessly screaming and bashing it.

c) the issues with pulseaudio are overhyped. right now, even some users have to use pulseaudio in order to get sound because of the fact that some apps think that they should have exclusive rights to the computer's sound

and pulseaudio has been working for me, up to lucid. however, it has (suprisingly) never worked for me in gentoo.....

---

### Post by FuturePilot on 2010-09-16
> **scottuss said:**
> I've been listening to some podcasts and reading some articles and everyone seems to bash PulseAudio.

I've read tonnes of support threads on the subject too, and by no means am I saying that I don't believe it has issues. 

However, my question is: Am I the only one who since Hardy hasn't had a single problem with PulseAudio. Not a blip, not a hiss, not a crash, not anything..?

No. I have not had a single issue with PulseAudio since Hardy.

> **sandyd said:**
> people are screaming at pulseaudio because 
a) its new, and it had a bad reputation from the start since Ubuntu **implemented** pulseaudio terribly

FTFY

They really screwed it up with PulseAudio in Hardy and it gave pretty much everyone some kind of problem or another. Since then they have been working hard to make it work nicely for everyone.

---

### Post by Frogs Hair on 2010-09-16
No problems in 9.10 or 10.04 , I'm using the Pulse Audio equalizer and I love it .

---

### Post by jerenept on 2010-09-16
> **Frogs Hair said:**
> No problems in 9.10 or 10.04 , I'm using the Pulse Audio equalizer and I love it .

Pulseaudio equaliser? Do please tell us about this. I had no idea this existed.

---

### Post by Simian Man on 2010-09-16
> **sandyd said:**
> people are screaming at pulseaudio because 
a) its new, and it had a bad reputation from the start since Ubuntu implements pulseaudio terribly

[Source from the PA lead dev.]("http://0pointer.de/blog/projects/pa-in-ubuntu.html")

---

### Post by sandyd on 2010-09-16
> **jerenept said:**
> Pulseaudio equaliser? Do please tell us about this. I had no idea this existed.
```
sudo apt-get -y install pavucontrol
```

---

### Post by Frogs Hair on 2010-09-16
Enjoy ! It works great for me and check mute buttons after installation. I use the rock preset.
[URL="http://digitizor.com/2010/02/08/how-...-10-and-10-04/"]http://digitizor.com/2010/02/08/how-to-install-system-wide-pulseaudio-equalizer-in-ubuntu-9-10-and-10-04/
[/URL]

---

### Post by jerenept on 2010-09-16
> **Frogs Hair said:**
> Enjoy ! It works great for me and check mute buttons after installation. I use the rock preset.
[URL="http://digitizor.com/2010/02/08/how-...-10-and-10-04/"]http://digitizor.com/2010/02/08/how-to-install-system-wide-pulseaudio-equalizer-in-ubuntu-9-10-and-10-04/
[/URL]

useless link is useless.

---

### Post by FuturePilot on 2010-09-16
> **Simian Man said:**
> [Source from the PA lead dev.]("http://0pointer.de/blog/projects/pa-in-ubuntu.html")

[Fixed.]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/406702")

---

### Post by jerenept on 2010-09-16
> **Frogs Hair said:**
> Enjoy ! It works great for me and check mute buttons after installation. I use the rock preset.
[URL="http://digitizor.com/2010/02/08/how-...-10-and-10-04/"]http://digitizor.com/2010/02/08/how-to-install-system-wide-pulseaudio-equalizer-in-ubuntu-9-10-and-10-04/
[/URL]

no worky on Maverick

---

### Post by Frogs Hair on 2010-09-16
Sorry about the Link. For 9.10 & 10.04 only

sudo add-apt-repository ppasyke83/ppa

sudo apt-get update

sudo apt-get install pulseaudio-equalizer

---

