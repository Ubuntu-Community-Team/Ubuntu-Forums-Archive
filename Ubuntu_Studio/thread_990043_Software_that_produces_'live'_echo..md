---
title: "Software that produces 'live' echo."
date: 2008-11-22
forum: Ubuntu Studio
---

### Post by Absinthe Minded on 2008-11-22
Hello all,

This might be an odd request and I don't know if there's any software to support it.

My 6 year old is driving me nuts; she wants to sing into a microphone and hear the sound echoed back to her - she's trying to replicate the 'Wishing Well' song in the old Disney cartoon, Snow White. I've installed Audacity, but she's too young to use it and you have to post process the audio - better would be something that added the echo instantly.

So, I've looked all over for a cheap and easy way to do this, but no good. I'm wondering if there might be a packege out there to help me, so I'm asking you guys. If decay, etc could be adjusted - that would be a bonus. Please help me before she drives me mad!

Cheers,
Nick.

P.S. I have Ubuntu Hardy, and an old laptop with Xubuntu on it (I'd prefer a package for this, but if she has to use my Ubuntu machine, so be it!)

---

### Post by thorgal on 2008-11-22
tough problem ... unless your box is configured to use the audio server jack, I wouldn't know. If you know nothing about jack, then it may not be the road you want to take. If it does not scare you, it could open up much more than what you ask. 

I built up a linux DAW (digital audio workstation). The audio layer I am using for my audio work is jack, a low latency server that allow multiple clients to exchange audio stream (a bit like h/w that you plug to other h/w via jack cables). There are tons of softwares for FX and jack compliant  hosts for these FX. So in this case, you would have a software FX rack with a delay or echo line on between your input and output, all handled by the jack server. Once you have jack up and running, it is very easy to plug softwares together or to your physical sound system. The tough part is to get jack running flawlessly, that requires some time configuring and understanding your system.

So, I don't know what else to say except that a dad could do a lot to please his 6 year old daughter, even transforming his linux box into a pro audio workstation :D

---

### Post by Absinthe Minded on 2008-11-22
thorgal,

Many thanks - I've never heard of JACK, but I'll give it a shot, I don't mind spending some time looking into it and it would be great to get it working for her.

One question; how do I install it? I've seen a few guides to configuration, but nothing on installation.

Thanks for your help, very much appreciated!

Nick.

---

### Post by thorgal on 2008-11-22
OK, mmmm, that's also not obvious for me to answer as I tend to customize my DAW, which means compiling stuff myself. But let's see.

If you open your package manager (synaptic), search for qjackctl and install it. In the ideal world, it will come up with the necessary dependencies (jackd, libjack, etc).

Qjackctl is the GUI frontend from where you can configure and launch jackd (the jack server daemon).

But from there, it requires a few system settings because jack works best with so-called realtime privileges. So you need to elevate your level of system privileges (aka superuser). One way to do it is for your linux user (under which you log in) to belong a unix group called audio and modify a system file, namely /etc/security/limits.conf with the appropriate stuff. You have to google this around because I don't have time to write up a userguide. 


By the way, what's your sound chip ? if it is driven by ALSA, then no prob. Is it some onboard chip or PCI card ?
But yeah, the question was about installing so try and install qjackctl.

---

### Post by Absinthe Minded on 2008-11-22
OK, installed through Synaptic and all looks good for now. The GUI opens from the Applications menu, so presumably that means nothing's amiss.

I'm going to do some Googling to see if I can get it to work - thanks for your help.

Sound is onboard, btw. Hopefully that doesn't mean it won't work!

Wish me luck and thanks again,

Nick.

---

### Post by markbuntu on 2008-11-24
jackrack has the delay you are looking for along with a whole pile of other effects. I think one of the delays can go up to 10 seconds. Once you get jack working all you need to do is connect jackrack between the sytem in which would be the mic and system out in the connections box which would be the sound card and select the delay, set it up and enable it. Should be no problem with on board sound but just make sure nothing else is using the sound when you start jack.

---

### Post by BLTicklemonster on 2008-11-24
In all of God's universes, what are the odds you would find someone called absinthe minded asking a question about software that echoes? I mean really, think about it. Hours of hilarity. Couple of sips, crank it up:
WOP WOP WOP WOP WOP WOP WOP WOP BOINK BOINK BOINK BOINK BOINK BOINK BOINK BOINK ECHO ECHO ECHO ECHO ECHO ECHO ECHO ECHO


Dude, can I come over and play?

---

### Post by Absinthe Minded on 2008-11-28
> **markbuntu said:**
> jackrack has the delay you are looking for along with a whole pile of other effects. I think one of the delays can go up to 10 seconds. Once you get jack working all you need to do is connect jackrack between the sytem in which would be the mic and system out in the connections box which would be the sound card and select the delay, set it up and enable it. Should be no problem with on board sound but just make sure nothing else is using the sound when you start jack.

OK, markbuntu, that's good - thanks for the advice. If I post a screenshot, would you mind taking a look as I'm a bit lost to be honest. It would be great to get this going as it looks like its exactly what I need.

I'm just using a standard PC Mic into the input jack of the onboard sound.

Cheers,
Nick.

---

### Post by Absinthe Minded on 2008-11-28
> **BLTicklemonster said:**
> In all of God's universes, what are the odds you would find someone called absinthe minded asking a question about software that echoes? I mean really, think about it. Hours of hilarity. Couple of sips, crank it up:
WOP WOP WOP WOP WOP WOP WOP WOP BOINK BOINK BOINK BOINK BOINK BOINK BOINK BOINK ECHO ECHO ECHO ECHO ECHO ECHO ECHO ECHO


Dude, can I come over and play?

Ha ha, yeah - it is kinda funny! You're welcome to come and play - just bring a bottle and you're IN!

---

