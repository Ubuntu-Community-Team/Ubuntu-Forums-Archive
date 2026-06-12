---
title: "Pro Audio Hardware Support"
date: 2010-12-15
forum: The Cafe
---

### Post by mr_sausage on 2010-12-15
Hey,
Now, I am still a fairly new Ubuntu user,
So please forgive my ignorance if I ask a few questions that have answers that are common knowledge.
Not my intention to offend.
However, I am a fairly heavy weight Pro Audio Enthusiast, who uses computers during the process of writing, recording, engineering and producing music. And have used computer for these purposes for at least 15 or so years.
Now, my main question is hardware support.
As from what i have seen, Pro Audio Hardware doesn't seem to be that well supported. I.e. drivers/software etc.
I was wondering if any one has approached the manufacturers of the most commonly used hardware,
or if any independent programmers/developers are working on developing drivers for some of these popularly used devices?

The companies that I personally would consider the most useful for 1st Stage development would be as follows.
Digidesign (owned by Avid) make Protools. 

Protools are known world wide for their manufacture of Pro Audio software/DSP hardware/Control Surfaces/Pro Audio Interfaces.
Their studio hardware comes in a variety of configurations and are aimed primarily at Pro recording and A/V post production.
There are also countless 3rd party software manufacturers that develop  products for use in the Digidesign recording and live sound  environments.

Digidesign also manufacture DSP based Live Sound / Sound Reinforcement Technologies which also employ the use of 3rd Party Plug ins.

M-Audio is the sister company of Digidesign that manufactures Pro Audio hardware aimed more at the Project / Home Studio Market. They make a number of Audio / Midi Cards, Midi Controller Keyboards and Midi Control surfaces.
Many of their Audio Cards that M-Audio manufacture are compatible with the LE version of Protools, as well as being compatible with other leading Digital Multi Tracks.

If their range of hardware was made compatible with Ubuntu, Ubuntu and M-Audio/Digidesign would become stronger market players, perhaps biting into the market that Apple and Windows have dominated for so many years.

I would also suggest developing the following Audio / Midi Multitracks,
As every user likes to work in their own favoured environment

Steinberg Cubase
Fruity Loops Studio

Apple Logic Pro (and Express) (although I imagine that porting Logic to any other OS is the last thing that Apple plan to do).

Anyway. 
Just some suggestions.
Thanks for reading

---

### Post by cchhrriiss121212 on 2010-12-15
This topic seems very similar to another one you created a few days ago:
[http://ubuntuforums.org/showthread.php?t=1643846](http://ubuntuforums.org/showthread.php?t=1643846)

In any case:
> As from what i have seen, Pro Audio Hardware doesn't seem to be that well supported. I.e. drivers/software etc.Some devices work great, others do not work at all, working drivers require the co-operation of the manufacturer. 

> I was wondering if any one has approached the manufacturers of the most commonly used hardware,
or if any independent programmers/developers are working on developing drivers for some of these popularly used devices?Yes, this is basically what they do at ALSA:
[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)
Similarly for firewire, there is ffado:
[http://www.ffado.org/](http://www.ffado.org/)

> If their range of hardware was made compatible with Ubuntu, Ubuntu and  M-Audio/Digidesign would become stronger market players, perhaps biting  into the market that Apple and Windows have dominated for so many years.A large number of M-audio products are already supported on Linux:
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-MAudio](http://www.alsa-project.org/main/index.php/Matrix:Vendor-MAudio)
The delta range has full support and most of the USB devices work. The firewire cards from M-audio are not at the same support level, but Focusrite have good support with that format. There are plenty of supported devices out there of a pro quality, all you need to do is research before buying one.

> I would also suggest developing the following Audio / Midi Multitracks,
As every user likes to work in their own favoured environment

Steinberg Cubase
Fruity Loops Studio

Apple Logic ProIf you want to see ports of existing software to Linux, write to the companies who make them. There is nothing the developers of Ubuntu can do about this (even if they could, none of them actually post on these forums).

---

