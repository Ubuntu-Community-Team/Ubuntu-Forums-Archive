---
title: "JACK / kernel questions"
date: 2009-02-20
forum: Ubuntu Studio
---

### Post by Ouia on 2009-02-20
Hi there,

I'm new to Ubuntu and I have a few questions  regarding JACK and the RT-kernel. I hope you can help me with them and I couldn't find them elsewhere. I'm having quite few a problems with studio that I'm trying to understand.

Thanks in advance

1) Does JACK work under a generic kernel? If it does, is it useful to do so?
2) I figured out what A RT-kernel is and that it runs with low latency. But what is the drawback of a low latency kernel?
3) Slightly less studio related, but is it a problem to install programs in one kernel (RT) and run them in another (generic). I had to do that since wireless doesn't work under RT, as well as my video card.
4) Are JACK and ALSA different varieties of the same thing or different things. Should they, or can they be run together?

---

### Post by Reeman on 2009-02-20
1) Does JACK work under a generic kernel? If it does, is it useful to do so?
...................................................................................
in short yes
...................................................................................
2) I figured out what A RT-kernel is and that it runs with low latency. But what is the drawback of a low latency kernel?
...................................................................................
stability issues when certain processes require system access...it is far better to 
use the realtime when not on the net or doing any sql, wifi, ssl login, encryption with strange local host connections etc. Therefore it is far better to setup an offline boot for audio only work with Ubuntu Studio in realtime. Issues with 64bit video drivers are also showing up. The same thing that plagued the first release of Vista BTW and still causes windows users headaches.
...................................................................................
3) Slightly less studio related, but is it a problem to install programs in one kernel (RT) and run them in another (generic). I had to do that since wireless doesn't work under RT, as well as my video card.
....................................................................................
If your video card gets pooched with the RT kernel then you might have to use the VESA driver exclusively until the issues are resolved to get a realtime desktop.
I have the same problem...and am just waiting for the rt kernel issues to be ironed out. The guys at 64Studio are getting close with the latest patches. I hope Ubuntu Studio devs are getting close with the 2.6.28 release stuff as well. I know that the 2.6.28 might be a while in the making but it seems that the .27 stuff is pooched.
................................................................................
4) Are JACK and ALSA different varieties of the same thing or different things. Should they, or can they be run together?
.................................................................................
Alsa is the sound drivers, jack uses alsa and must have access to /dev though alsa to work.

Hope this clears things up for you.

---

### Post by Ouia on 2009-02-20
It clears a lot, thanks. I'm getting a lot of different errors on different moments. With my knowledge of Ubuntu (or computers for that matter) I can't seem to find a common denominator on what's going wrong.

I did install 64bit 8.04 Ubuntu. Before changing to Studio, I had troubles with the set up for my video card on generic as well (Nvidia 9600GT), but i got there in the end. I haven't tried the same thing on the RT kernel yet, as I'm afraid to ruin what I have on the generic kernel.


------------
"must have access to /dev though alsa to work."

How can I check this?

---

### Post by Stochastic on 2009-02-20
> **Ouia said:**
> 1) Does JACK work under a generic kernel? If it does, is it useful to do so?
Yes, but many systems will experience either a very high latency setting or too many XRuns (lost packets of audio) with the vanilla kernel.
> **Ouia said:**
> 2) I figured out what A RT-kernel is and that it runs with low latency. But what is the drawback of a low latency kernel?
Reeman touched on a few drawbakcs; in general, you'll see more issues with hardware support etc... (the Intrepid RT kernel still has a bug that only allows one core to be used on multi-core processors).  As time goes on, there are fewer and fewer differences between RT and vanilla (from what I understand, I'm no kernel hacker).
> **Ouia said:**
> 3) Slightly less studio related, but is it a problem to install programs in one kernel (RT) and run them in another (generic). I had to do that since wireless doesn't work under RT, as well as my video card.
No.  The kernels are interchangeable and the only issues will be if you need to work around bugs on one kernel.  It shouldn't matter what kernel you're running when you install a program.
> **Ouia said:**
> 4) Are JACK and ALSA different varieties of the same thing or different things. Should they, or can they be run together?
You've just stepped into a pile of muck that is the linux audio-server chain.  ALSA and JACK are different items.  In broad terms JACK is higher level than ALSA and often piggybacks on ALSA drivers - but not always, ALSA is not needed for JACK to run (I rarely use ALSA drivers with JACK).

As for running them 'together' I assume you mean playing audio out of the same soundcard from both a jack app (i.e. Ardour) and an alsa app (i.e. Totem Move Player), this is tricky as jack kind of takes over the server it's using.  There are workarounds, I'd recommend routing Pulse Audio into Jack (see other topics in this forum for more info, i.e. [http://ubuntuforums.org/showthread.php?t=1062120](http://ubuntuforums.org/showthread.php?t=1062120)).

Here's a handy diagram (note that these are the possible routes, they're not all connected at once): [IMG]http://i33.tinypic.com/23mk9om.png"[/IMG]

---

### Post by markbuntu on 2009-02-22
What I do is have separate installs(actually 5 right now) for different purposes. I have UbuntuStudio amd64 8.04 which I use when I do audio production and a generic ubuntu 386 for other stuff and a bunch of other installs for testing etc.

I deliberately set the UbuntuStudio up for optimum audio production and never configured my email or other stuff. This helps me concentrate on the task at hand and makes the system faster and less prone to glitches and interruptions. Getting an email popup in the middle of a live session can really ruin your day when it glitches the recording.

If I want to surf the web or check my email or any other time wasting things while I am in production mode I need to reboot into another install. It is psycological warfare against myself and it works.

---

### Post by Ouia on 2009-02-23
Thanks. From what you tell, the easiest thing to do is to have another install and see what that separation gives me... I assume were talking about an install on another partition, btw.

---

### Post by markbuntu on 2009-02-23
Another partition, another drive, whatever. If you do install this to another partition/drive and you already have a grub in the master boot record, put the grub for the new install on the new partition/drive and add a chainloader to the new partition/derive from the first grub. It will save you a lot of potential trouble with kernel updates etc.

---

