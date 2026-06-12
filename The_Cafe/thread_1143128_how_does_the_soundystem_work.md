---
title: "how does the soundystem work?"
date: 2009-04-29
forum: The Cafe
---

### Post by Screwdriver0815 on 2009-04-29
Hi all,

I would like to post my story "how did I manage to get sound in Debian Lenny" and ask some questions to understand why it is now like it is and how I can maybe improve it.

so here is the story:

as mentioned the OS is Debian Lenny which I also have on my computer, beside Jaunty (Dualboot).

I have two soundcards in my computer. One is an ATI which is on the mainboard (I don't want to use it) and one Creative Soundblaster Audigy which I want to use. 

Jaunty and all the other ubuntu-versions recognised both cards and play sound over the soundblaster card by default. Jaunty does not play any sound on the ATI and this is like I want it. 

Debian Lenny did recognise both cards too but did not play any sound on both cards. So after reading wiki's and stuff and fooling around with asoundconf and so on, I decided to compare the preferences of Ubuntu and Debian in the soundconfiguration and also in Alsamixer.

The result was really confusing: both, Jaunty and Lenny have the same settings in Alsamixer. And these settings are: device = ATI!! The card which I don't use!! But Jaunty plays the sound over the Soundblaster!

So I read the wiki regarding soundproblems again and found something which I ignored all the time by no specific reason.

This hint was about setting indexes on modules. So I changed the file /etc/modprobe.d/alsa-base by putting 

```
options CA0106 index=0
options SB index=1
```

at its end. CA0106 is the module of the Soundblaster (which I want to use) and SB is the module of the ATI.
The result of these lines is, that the module of the Soundblaster is loaded earlier than the module of the ATI. 

Et voila! I had sound in Lenny! But: it was on the wrong soundcard!! It played only via the ATI card! The Soundblaster was remaining silent.
So I changed the file /etc/modprobe.d/alsa-base again by exchanging the modules:

```

options SB index=0
options CA0106 index=1

```

nothing happened - sound is only available via ATI card in Lenny. 

So now this is quite interesting and confusing to me and I just wanted to ask if you could give some advise - so that I understand what happened here and why it all is like it is. Furthermore I would like to get some hints to get the Soundblaster working in Lenny.

1. why does Ubuntu play sound via the soundblaster, when it has the ATI in Alsamixer? Okay, in the Audio-settings (system -> preferences -> Audio) it has the Soundblaster as default mixertrack, but when I move the volume control in Alsamixer, the volume in the speakers changes too

2. why does Lenny play sound via the ATI only even when I set all the Audio and sound settings exactly like they are in Ubuntu? 

3. why do I get sound in Lenny only when I change the /etc/modprobe.d/alsa-base but when I change it again to get my prefered hardware working it doesn't have any effect?

4. I learned that the soundblaster card supports hardwaremixing too. So if I set up the whole soundsystem for Alsa only, I have to fill-in the file asoundrc with appropriate text. But then I only can find further explainations about softwaremixing. What do I have to do to configure the hardwaremixing in the right way?

any useful answer would be very much appreciated

Thanks

best regards
Steffen

---

### Post by Screwdriver0815 on 2009-05-03
okay, just to get the topic complete:

I got answers to some of my questions on my own I think, but I am not really sure.

1. question: no answer - just a correction: the volume doesn't change when I change the volume level in alsamixer (for the onboard soundcard). But I really can not figure out why Ubuntu has the onboard card in alsamixer but plays via the Soundblaster

2. Debian Lenny has no driver for the soundblaster included so it can not play sound via the Soundblaster card

3. Lenny does not load the module of the soundcards but when I do the mentioned change to the modprobe file it recognises the onboard-card as it is the only one which has drivers in the system

4. hardwaremixing is not possible because of missing driver

Installation of the driver is too much effort (for me) as it means compiling and so on.

---

### Post by kostkon on 2009-05-03
Actually, *Ubuntu* uses *PulseAudio* and it ignores the *ALSA* conf files, and thus the index of the cards in */etc/modprobe.d/alsa-base*

In *Ubuntu*, to set the default audio device, you need to install the *PulseAudio Device Chooser* utility.

For some more info, you can check this how-to [here]("http://ubuntuforums.org/showthread.php?t=843012"), for example.

---

### Post by Screwdriver0815 on 2009-05-04
thanks for pushing me in the right direction!

I got it and I have now the soundsettings I wanted. Sometimes its like you stand in front of the thing you want but you don't see it because it is already there...:confused:

I have set the CA0106 as the default card with the pulseaudio device chooser and in all the settings too. Then all the channels to be controled... thats it. Really easy.

once again: thank you!

---

