---
title: "Live guitar effects.. Is my hardware good enough?"
date: 2010-05-03
forum: Ubuntu Studio
---

### Post by decomp on 2010-05-03
Hi all,

Sorry if this question has been asked before but I'm not sure how to phrase it.

I would like to run an electric (bass) guitar into my computer and use ubuntu studio for amp simulator, effects, and live looping, all controlled via a midi foot pedal. I intend to be pretty effects heavy - 1-4 amp simulators on different channels and 1-5 effects running on each simulator at the same time (ie make it sound like multiple guitars, all with different effects.)

I have a Sony Vaio pcg-v505ecp laptop, 1500 mhz pentium M processor with 1gb ram, and lshw gives my soundcard as a intel ac97.

My questions are:

1. Do I need a preamp or something before I plug my guitar in? Since I'm using an amp simulator can I just plug it in? I have no line-in jack, only mic-in.

2. Is my sound card enough? Do I need some external firewire thing? Ram is cheap so I can toss another gb of that on if it will help.

3. Will I be able to control everything via midi? jackd seems very decentralized, but I should still be able to turn channels on and off and control any effect I want right?

---

### Post by sgx on 2010-05-03
> **decomp said:**
> Hi all,

Sorry if this question has been asked before but I'm not sure how to phrase it.

I would like to run an electric (bass) guitar into my computer and use ubuntu studio for amp simulator, effects, and live looping, all controlled via a midi foot pedal. I intend to be pretty effects heavy - 1-4 amp simulators on different channels and 1-5 effects running on each simulator at the same time (ie make it sound like multiple guitars, all with different effects.)

I have a Sony Vaio pcg-v505ecp laptop, 1500 mhz pentium M processor with 1gb ram, and lshw gives my soundcard as a intel ac97.

My questions are:

1. Do I need a preamp or something before I plug my guitar in? Since I'm using an amp simulator can I just plug it in? I have no line-in jack, only mic-in.

2. Is my sound card enough? Do I need some external firewire thing? Ram is cheap so I can toss another gb of that on if it will help.

3. Will I be able to control everything via midi? jackd seems very decentralized, but I should still be able to turn channels on and off and control any effect I want right?Hi, you will need a line in, and
for now, rakarrack and guitarix are excellent linux multi-fx apps, but you'll need a usb or firewire audio interface, and either a preamp, or a hardware guitar processor that has a preamp, or a digital guitar amp, (Line 6 Spider with line out), any of these will give a boost to the signal so the usb interface line-in can hear and record it at high quality. There are some interfaces with built in preamps, which could be cheaper/easier to deal with.

Check here for interfaces known to work:

[http://www.linuxstudiopro.com/](http://www.linuxstudiopro.com/)

There are a few youtubes of rakarrack, its 10 fine fx in one gui.

Cheers

---

### Post by thorgal on 2010-05-03
guitarix has a preamp as well :)

check the buttons in the bottom left area.

[IMG]http://guitarix.sourceforge.net/images/guitarix.png[/IMG]

---

