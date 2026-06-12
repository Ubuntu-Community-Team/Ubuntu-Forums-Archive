---
title: "Audio problems / Installing RT kernel?"
date: 2010-07-16
forum: Ubuntu Studio
---

### Post by techx4 on 2010-07-16
Hello all, 

First post and I'm pretty new to ubuntu studio and am finding it challenging to get it working properly. I am running the latest build in a VM and am having audio issues, choppiness/distored sounds in the apps that I've tried like hyrdogen and zynaddsubfx. So from my research I find people mostly recommending to install the realtime kernel. When running uname -r it reports 2.6.32-23-generic. Ok so I found a command to install the RT kernel on ubuntu support:[FONT=monospace]

[/FONT]sudo apt-get install linux-rt linux-headers-rt

So that installed successfully but when I run uname -r i still get the same 2.6.32-23-generic. How do I get it REALLY installed and running? 

Any help is appreciated, because troubleshooting all of this stuff is not so much fun :/

UPDATE: I little more searching and I found the while 'hold shift while booting' and am now running the RT kernel so thats cool.. but when i run zynaddsubfx, and hit one of the keys on the synthesizer it sounds like there are regular and fast breaks in the sound, like somehow the audio is getting muted and unmuted very fast..

---

### Post by theraje on 2010-07-17
Have you tried running it straight, and not in a VM? That would be my first hunch as to why you would get that kind of issue (not that it couldn't be something else!).

---

### Post by techx4 on 2010-07-17
> **theraje said:**
> Have you tried running it straight, and not in a VM? That would be my first hunch as to why you would get that kind of issue (not that it couldn't be something else!).

 hah i hear ya, i would love to but i dont have a extra pc powerful enough to run studio so i have no choice but to run it on the vm :(

---

### Post by theraje on 2010-07-17
Hmm... :/

Are you running Windows then? If so, I can probably recommend some applications if you can give a better idea of what you want to accomplish. :)

---

### Post by cchhrriiss121212 on 2010-07-17
> **techx4 said:**
> hah i hear ya, i would love to but i dont have a extra pc powerful enough to run studio so i have no choice but to run it on the vm :(
You know you can dual boot Ubuntu with windows providing you have a bit of disk space.

---

### Post by techx4 on 2010-07-17
> **theraje said:**
> Hmm... :/

Are you running Windows then? If so, I can probably recommend some applications if you can give a better idea of what you want to accomplish. :)

Yes running win vista x64.. As for dual booting, I've never been one to do that, I just don't want any issues with this rig and I usually just run VMs for linux. Thanks for the suggestions though :)

---

### Post by cchhrriiss121212 on 2010-07-17
You will get far more issues running a VM than you would with a dual boot, especially when you are using hardware ins and outs for audio work.
I'd recommend buying a cheap HD, just an 80GB or something and use it for Linux only. That way you can select it with your BIOS at boot, and you won't need to worry about messing up your windows OS.

---

### Post by techx4 on 2010-07-17
> **cchhrriiss121212 said:**
> You will get far more issues running a VM than you would with a dual boot, especially when you are using hardware ins and outs for audio work.
I'd recommend buying a cheap HD, just an 80GB or something and use it for Linux only. That way you can select it with your BIOS at boot, and you won't need to worry about messing up your windows OS.

Ahh yes, I thought you meant install linux on the same hdd as win.. but on a separate hdd yea i could do that, i actually did do that once before with xp.. problem is i've run out of space in my case with 5 hdds already installed lol!, guess i will need to choose to sacrifice one so i can finally enjoy studio!!

thanks again :)

---

### Post by techx4 on 2010-07-20
I was experimenting with the jack settings and enabled SOFT MODE. After that several apps that i was having issues with suddenly work very well. Such as zynaddsubfx and hydrogen. There is no longer the horrible audio stuttering/crackling.. that isn't to say I'm completely without problems, I do occasionally get some clicking sounds when I'm using the apps, I used audacity to record some stuff and those clicks/crackling were recorded so its not my speakers or anything.. oh well.. it's certainly a start.

---

### Post by theraje on 2010-07-22
> **techx4 said:**
> I do occasionally get some clicking sounds when I'm using the apps, I used audacity to record some stuff and those clicks/crackling were recorded so its not my speakers or anything.. oh well.. it's certainly a start.

What kind of mic setup are you using? If you happen to be using a laptop, and the built-in mic (doubtful, but still), it's probably your mic picking up the hard drive's clicks as it seeks.

If that's not it, please describe your recording setup, and we'll see what else might be the culprit.

---

### Post by RaumTrug on 2010-07-23
does the "xrun" count raise by one or more when you record and such a click is happening?

if yes, you can do these things:

1) disable cpu scaling for all of your cpu's, for example by adding the cpu scaling applet to the panel, 1 for each core, and putting them all to "performance". you can "ondemand" them after being finished with jack.

2) just use a bigger latency, like go through the "frames/period" value and make it bigger. this will make audio "lag" more, though, not good if you plan to play some synth live, or want to monitor cpu-processed (with effects) mic or instrument signal.

---

### Post by hardcopy on 2010-07-23
set zyn and hydrogens internal buffer size the same as jacks frames/period size. that should clear up the nasty pops & clicks

---

