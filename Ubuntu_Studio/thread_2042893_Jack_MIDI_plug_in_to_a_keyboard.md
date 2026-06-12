---
title: "Jack MIDI plug in to a keyboard"
date: 2012-08-15
forum: Ubuntu Studio
---

### Post by animegizze10 on 2012-08-15
Hi, I can´t plug in my keyboard to my computer in the Jack programs. I want to record when I play but. I tried in a lot of different Jack programs but I can´t make the MIDI connection to work. I have ubuntu studio version 12.4. Help please! :)

//animegizze10

---

### Post by jejeman on 2012-08-15
If your MIDI device is in ALSA realm, you need to bring it to JACK MIDI realm.
Two ways, depends on hardware you use.
1. if you use ALSA sound card, you can bring it with choosing seq as MIDI driver option in jack settings.
2. or using program a2jmidid. Which is somehow better way.

---

### Post by sgx on 2012-08-15
> **animegizze10 said:**
> Hi, I can´t plug in my keyboard to my computer in the Jack programs. I want to record when I play but. I tried in a lot of different Jack programs but I can´t make the MIDI connection to work. I have ubuntu studio version 12.4. Help please! :)

//animegizze10

Hi, look at the 4th and 8th links at the wiki.

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

zynaddsubfx software synthesizer is used as an example. Yoshimi is the newer release
of that, but requires installing and running the command a2jmidid,
found here:

[http://packages.debian.org/unstable/sound/](http://packages.debian.org/unstable/sound/)

install with 

sudo dpkg -i name-of.deb

The yoshimi connection will be in qjackctl Midi tab, zynaddsubfx
connection in the Alsa tab. Both need connection in the Audio tab,
as shown in the 8th wiki link.

To record sounds from a hardware device, connect the line-out
or headphone-out to your soundcard line-in, which will be in
qjackctl Audio tab, on the left side, the soundcard output is on
the right side.

Cheers

---

### Post by smartboyhw on 2012-08-16
> **animegizze10 said:**
> Hi, I can´t plug in my keyboard to my computer in the Jack programs. I want to record when I play but. I tried in a lot of different Jack programs but I can´t make the MIDI connection to work. I have ubuntu studio version 12.4. Help please! :)
 
//animegizze10
 
animegizze10: Hello.
 
First of all, let me state that next time type 12.04 instead of 12.4. It's a bit different.:P
 
Anyways, the third post's suggestion is correct. Follow it and see if you still have any questions.
 
I wish you a happy day on Ubuntu Studio.
 
Regards,
Howard Chan
Ubuntu Studio Team member in [https://wiki.ubuntu.com/UbuntuStudio/TeamStructure](https://wiki.ubuntu.com/UbuntuStudio/TeamStructure)

---

### Post by animegizze10 on 2012-09-23
Hi! 

I´m sorry that I wrote wrong in my question but thanks for all the help! :D
Now I can use the Jack plug in system.

//animegizze10

---

