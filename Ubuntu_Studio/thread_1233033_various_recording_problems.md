---
title: "various recording problems"
date: 2009-08-06
forum: Ubuntu Studio
---

### Post by Lorenz on 2009-08-06
Hi guys,

I have a couple of issues that prevent me from recording my songs and I'm hoping you could help me with it. I'm currently using Jokosher, but I have the same problem with other multitrack programs such as audacity. 

First of all, I start by importing a drum track done with Hydrogene. That works pretty well, but the first beat is cut, so it starts a split of a second late. That is not too bad though, I can live with that.

The next thing is that whenever I add another instrument, say a guitar, and start recording via a microphone plugged in to the mike-out of my laptop, it also records the drum track again on the guitar track. It is as if the computer would not only record the input from the microphone, but also the output of the soundcard. How can I stop this?

Also, there is always a delay for the guitar track (or whatever track I add), but I guess this is caused by the kernel, afaik. Is there an easy solution for this, other than moving the tracks around until they fit?

Many thanks for your help!

---

### Post by sgx on 2009-08-07
> **Lorenz said:**
> Hi guys,

I have a couple of issues that prevent me from recording my songs and I'm hoping you could help me with it. I'm currently using Jokosher, but I have the same problem with other multitrack programs such as audacity. 

First of all, I start by importing a drum track done with Hydrogene. That works pretty well, but the first beat is cut, so it starts a split of a second late. That is not too bad though, I can live with that.

The next thing is that whenever I add another instrument, say a guitar, and start recording via a microphone plugged in to the mike-out of my laptop, it also records the drum track again on the guitar track. It is as if the computer would not only record the input from the microphone, but also the output of the soundcard. How can I stop this?

Also, there is always a delay for the guitar track (or whatever track I add), but I guess this is caused by the kernel, afaik. Is there an easy solution for this, other than moving the tracks around until they fit?

Many thanks for your help!

Hi, without a dedicated audio interface, you'll need Ubuntu Studio 8.04 and its real-time kernel, to have lag-free recording. And in the preference or options pages of Jokosher/audacity etc, you will have to experiment with the options to monitor your first track, while recording a second track. Once you install 8.04 (or Studio64, JAD, Musix, or avlinux2) upgrade the apps you use, and make connections in qjackctl. The audacity connection only appears after pressing the record button, and select what device to record, using its preferences recording pages. Its input is called portaudio, in the qjackctl panel, press the pause button while you connect things, press it again to resume recording. Not sure about jokosher, probably similar.

In the meantime, in qjackctl, open the settings panel, and set the priority to 70, and see if that helps with the lag. It won't help unless the apps you use are connected in qjackctl. Ardour is another recording option worth spending the time on in the long run, and is fully functional with qjackctl.

Cheers:D
Cheers

---

### Post by bluelamp999 on 2009-08-07
This article might help...

[http://createdigitalmusic.com/2009/08/04/linux-music-workflow-switching-from-mac-os-x-to-ubuntu-with-kim-cascone/](http://createdigitalmusic.com/2009/08/04/linux-music-workflow-switching-from-mac-os-x-to-ubuntu-with-kim-cascone/)

---

### Post by Lorenz on 2009-08-09
Thank you both for your answers!
Audio production is probably one of those topics were Linux is still really behind Windows and obviously miles behind Apple. Quite a pity that a rather simple task such as multi-track recording is almost impossible with a vanilla Ubuntu configuration.

---

