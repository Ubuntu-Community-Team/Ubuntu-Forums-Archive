---
title: "old computer w/ xp pro &gt; linux. What is going on?"
date: 2008-07-31
forum: Windows
---

### Post by dracule on 2008-07-31
I honestly had to do this 3-4 times. I couldnt believe my eyes.

Well, I was going to reinstall Fluxbuntu on this old computer w/
16mb video card (TNT2)
256mb RAM
PIII 450MHZ

I just had all the parts sitting in a cardboard box.


So I put the disk in, and to my surprise I accidentally grabbed an XP pro disc.
I thought "eh, what is the worst that can happen? it probably will run slow anyways"

So i just kept on installing it. I played a few EMU's on it, (GBA emulator requires too much to run though)
Then i turned it off.

When I turned it on, I looked away for a minute and to my surprise, it was already booted. I thought "ok must be a fluke"
I restarted, did the same thing.
got out a stop watch, ~35 seconds to boot to a fully usable desktop!

I am freaking out! ok, fluxbuntu is one of the lightest possible versions of ubuntu. heck the cd image is only 200mb.
When i timed fluxbuntu, it took 3 min 12 seconds to boot to a usable desktop (i timed it 4 times, each time came out about there)

XP pro uses both less ram, and boots faster.
I have home edition on my laptop, which takes much longer to boot (probably well over a minute)

if i put it in hibernate (lol) then it boots in 5 seconds. you barely even see the "resuming windows" bar.

I am amazed that XP runs so well on this machine designed for windows 98.

---

### Post by K.Mandla on 2008-07-31
I know this is technically a thread extolling Windows, but I feel obligated to mention: There was a quirk in Fluxbuntu that made the splash screen drag on some video cards; try editing the Grub boot line to take out "splash". On my machine the boot went from 3+ minutes to under 1.

---

### Post by snowpine on 2008-07-31
I agree, Microsoft made a mistake pulling the plug on XP because a lot of people like it. Time to boot is only one measure of a computer's speed though. I have a dual boot with XP and it does indeed boot quicker, but applications take longer to load. Also there are Linux distros that (unlike Ubuntu) you compile specifically for your hardware, and they boot much quicker. Ubuntu trades boot time for hardware adaptability to a certain extent.

ps +1 on taking out the splash in fluxbuntu, it is a bug and removing it will speed it up a lot.

---

### Post by fiddledd on 2008-07-31
I had a PC with similar specs that I used as an Internet Gateway, before I got a router (a few years ago). It did the job with XP pro, but once I installed Antivirus and Firewall I got nowhere near your boot time. I never timed it but I'm sure it was more than a minute. So it looks like you've been lucky. BTW I use, and have no complaints with Vista and XP, so this isn't an anti Windows post. :)

---

### Post by darrelljon on 2008-07-31
Fluxbuntu has lots of apps and driver support.
A fresh install of XP does not.

---

### Post by Archmage on 2008-07-31
Did you compare a Linux distro from 2001 with XP or Vista with the latest Fluxbuntu?

I'm really courious about the boot time of Vista compared to Fluxbuntu.

---

### Post by dracule on 2008-07-31
> **fiddledd said:**
> I had a PC with similar specs that I used as an Internet Gateway, before I got a router (a few years ago). It did the job with XP pro, but once I installed Antivirus and Firewall I got nowhere near your boot time. I never timed it but I'm sure it was more than a minute. So it looks like you've been lucky. BTW I use, and have no complaints with Vista and XP, so this isn't an anti Windows post. :)

yeah, it is not connected to the internet, so i dont care about updates, antivirus or anything. 


The reason I had to reinstall fluxbuntu was because I got a "segmentation fault" in almost every program i ran from the terminal. I couldnt run anything. I did a memtest and everything came out fine. 

I asked on these forums, and on IRC but nobody answered. Ill probably just stick w/ XP now.

---

### Post by fiddledd on 2008-07-31
> **dracule said:**
> (..). Ill probably just stick w/ XP now.

Yeah, use what works for you.:)

---

### Post by snowpine on 2008-07-31
> **Archmage said:**
> Did you compare a Linux distro from 2001 with XP or Vista with the latest Fluxbuntu?

I'm really courious about the boot time of Vista compared to Fluxbuntu.

There is no "latest fluxbuntu" :) but the 7.10 rc is not any quicker-booting than ubuntu in my experience.

---

### Post by Twitch6000 on 2008-07-31
> **snowpine said:**
> There is no "latest fluxbuntu" :) but the 7.10 rc is not any quicker-booting than ubuntu in my experience.

that is not the latest version <.<?!?!?!?
8.04 is

Anyways I have always notice alot of people count you logging into Ubuntu part of the boot up which is kind of stupid...when you don't do it for xp.
Anyways why care about a stupid boot time anyways?I rather have great hardware support.Besides with a few tweaks I can make any Linux faster on boot up.

---

### Post by snowpine on 2008-07-31
> **Twitch6000 said:**
> that is not the latest version <.<?!?!?!?
8.04 is

Sorry, poor choice of words. :) What I meant to say is the latest version of Fluxbuntu is 7.10 Release Candidate. It is very slow booting on some computers due to the splash screen, which I would imagine is part of the reason it's still a "release candidate" months later. (And is the likely explanation for the OP's slow boot time--Dracule, you should try deleting 'splash' from your boot and let us know if that solves the problem.)

---

### Post by K.Mandla on 2008-07-31
> **Twitch6000 said:**
> Anyways why care about a stupid boot time anyways?
Strange, I was just answering this question yesterday.

[http://kmandla.wordpress.com/2008/07/31/why-bother/](http://kmandla.wordpress.com/2008/07/31/why-bother/)

---

