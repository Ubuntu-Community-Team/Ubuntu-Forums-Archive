---
title: "I need help with a Behringer UCA202"
date: 2010-02-21
forum: Ubuntu Studio
---

### Post by Starving Artist on 2010-02-21
Hi there, I did a search and saw a couple other threads dealing with this subject but because I'm about as clueless as a noob can get I'm making a new thread.

I'm trying to run my UCA202 into Audacity and I'm not getting any sound. When I put headphones in the device  I can hear my mics so I know it's not the device itself and even though I don't see it listen in my plugged in devices list my machine seems to recognize it because it adds a USB audio tab onto my mixer. Is there some special way I'm supposed to connect it to audacity or is there another recording program someone on here would like to recommend.

Thanks.

---

### Post by cariboo on 2010-02-23
This might be a better place for your question.

---

### Post by cchhrriiss121212 on 2010-02-23
If you are recording music, you will want to use something with a few more capabilities than Audacity (Ardour for example is a great multi-track recording program). Have a look at Jack which is the excellent low latency sound server for linux. There are many great programmes in the Ubuntu Studio release for audio work too. A realtime kernel is recommended for any audio work but you can still record without it. All this stuff is in synaptic.

---

### Post by Starving Artist on 2010-02-27
Alright, I went and downloaded Ardour so I'm going to be learning how to use that but I can't seem to get JACK. I'm confused by the downloads on the website and the package downloader doesn't seem to install it. If you have any idea, how should I go about actually getting it on my system so I can connect all the dots between my microphones and Ardour?

---

### Post by AutoStatic on 2010-02-28
> **Starving Artist said:**
> I'm confused by the downloads on the website and the package downloader doesn't seem to install it.The JACK daemon is in Synaptic, so open Synaptic (System - Administration - Synaptic Package Manger), click 'Search', enter *jackd* as the search item and install it.

---

### Post by Starving Artist on 2010-03-03
Alright, I apologize if I'm being to vague about this or if there's something obvious that I'm missing. This is my first kubuntu system and I haven't had it for very long, nor am I that knowledgeable when it comes to computers in the first place. I don't have synaptic but I do have a program called KPackageKit. Through that I have, apparently, installed ardour and jackd. I installed jack once before but I ran into a problem with this laptop and we ended up formating it and reinstalling kubuntu. Back before formatting it jack appeared as an actual program and by that I mean I could open it from my start menu and interact with it. Now, even though kpackagekit says I have it installed it's not showing up anywhere. This is my roadblock. Apparently I need to actually open jack to configure the setting for it to connect to ardour. Now like I said this could all be a problem caused by my general ignorance of the new programs but if there's any other way for me to install jack please point me to it. Would installing synaptic be any help? I can get it from kpackage but they just seem like the same program.

---

### Post by AutoStatic on 2010-03-03
You should also install QjackCtl, that's the GUI frontend for JACK.
And the Kubuntu equivalent of Synaptic is called Adept if I'm correct, not a Kubuntu user myself.

---

### Post by Starving Artist on 2010-03-10
Thanks for the help guys. I seem to have everything together. Now I'm just working on learning the programs.

---

