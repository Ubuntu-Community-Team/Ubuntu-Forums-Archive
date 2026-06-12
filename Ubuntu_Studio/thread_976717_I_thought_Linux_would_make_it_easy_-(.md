---
title: "I thought Linux would make it easy :-("
date: 2008-11-09
forum: Ubuntu Studio
---

### Post by bolex100 on 2008-11-09
The reason I bought a Linux machine was do get rid of the unnecessary aps that sapped the processor so I could run simple music applications. There are loads about but none seem to work properly/simply.

Where can find an idiots guide to music production in Ubuntu? I only want to run a drum machine, and a few samples.

---

### Post by snowpine on 2008-11-09
Hi Bolex, the first thing you'll want is the "linux-rt" kernel. It is a real time kernel, which means it is designed for low latency audio production. Basically what it does is keep other applications from stealing processor cycles from the current application. You can install linux-rt on its own using apt-get or synaptic. When you reboot, you should be able to choose it from Grub. It is also part of Ubuntu Studio, which is definitely worth researching if you're serious about making music with Ubuntu.

Hydrogen is a pretty good drum machine, easy to get started with. I haven't experimented with sampling yet so I can't help you there.

Good luck!

ps A descriptive title for your thread would be more likely to catch the attention of the music experts... :)

---

### Post by Stochastic on 2008-11-09
Some good tutorials are in the ubuntustudio wiki: [https://help.ubuntu.com/community/UbuntuStudio](https://help.ubuntu.com/community/UbuntuStudio)
though some of those are pretty old & out of date.

In general audio on linux is pretty complex, but that allows for greater flexibility in the end; it's possible to do many more combinations of things, but getting organized first can be difficult.

---

### Post by mrhelpman on 2008-11-09
> **bolex100 said:**
> The reason I bought a Linux machine was do get rid of the unnecessary aps that sapped the processor so I could run simple music applications. There are loads about but none seem to work properly/simply.


[rosegarden]("http://www.rosegardenmusic.com/") has a drum martix as well as the ability to add audio - either live recordings or samples. I think version 1.6 is in the 8.04 repositories. I don't know which version is in 8.10.  You can down load the source and build the latest version if you wish (1.7.3 out soon) which is not that difficult and is described in the above link.

However as Dr snowpine says, Hydrogen appears to be the drum machine of choice.
John T.

---

