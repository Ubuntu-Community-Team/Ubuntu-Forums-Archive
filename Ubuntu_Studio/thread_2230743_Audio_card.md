---
title: "Audio card"
date: 2014-06-20
forum: Ubuntu Studio
---

### Post by Tristan_Williams on 2014-06-20
I need an audio card that has 1/4" inputs for guitars.

What would be the best choice?

---

### Post by MartyBuntu on 2014-06-21
I'd recommend a pre-amp (you can get a USB powered one) and then go 1/8th LINE OUT from the pre-amp to 1/8th LINE IN on your computer.

That's my guitar setup. More info, if you'd like.

---

### Post by CrocoDuck on 2014-06-21
> **MartyBuntu said:**
> I'd recommend a pre-amp (you can get a USB powered one) and then go 1/8th LINE OUT from the pre-amp to 1/8th LINE IN on your computer.

Yeah, basically the smartest idea. You may want to search deep specs for your current sound card by the way: If you have an integrated soundcard in the motherboard you could have a not very nice result. That is because the built-in filters and preamps in the integrated soundcards inputs are designed to be cheap and calibrated on human voice first. For example, the soundcard of my laptop introduce attenuation and distortion above 5 kHz (this is a staple). You may want to have a nice and simple external soundcard and enter its output with a preamp. For example, I use a [FCA202]("http://www.behringer.com/EN/Products/FCA202.aspx"), her inputs connected to the outs of a mixer. I connect my guitar or bass to the mixer with a DI box. Of course, you see that is not actually a very portable setup (some wiring is required).

You may be asking for something compact you can move around easly. [This should work]("http://global.focusrite.com/usb-audio-interfaces/scarlett-2i2") (make sure it works with linux searching on [alsamatrix]("http://www.alsa-project.org/main/index.php/Matrix:Main") and/or all over the internet). Also, I don't know about linux support for [these]("http://www.behringer.com/EN/products/UMC204.aspx"), but they should work (have a search online).

So, to sum up:


[LIST]
[*]If you have a good soundcard, just interface your guitar through a preamp or mixer + DI box. 
[*]If not, choose a better soundcard and interface your guitar as above or  choose a better soundcard you can interface directly with guitar. 
[/LIST]

Now you just have to search for the solution that fits best your needs, budget and linux support ;)! Other suggestions in [this recent thread]("http://ubuntuforums.org/showthread.php?t=2230386"). Lastly, I've used [this]("http://www.behringer.com/EN/Products/UCA202.aspx") for years. It needs a preamp or mixer + DI, but it is very cheap and not that bad, but also not that good, since it is only 16 bit / 48 kHz.
[B]
EDIT:[/B]

Found also [this one]("http://www.presonus.com/products/AudioBox-22VSL"). A guy in [this thread]("http://www.linuxmusicians.com/viewtopic.php?f=6&t=7543#p31378") stated that it works under UStudio 12.04.

---

### Post by slonk on 2014-06-30
Do you plan to do the processing on the computer or is the computer just recording?

The most straightforward thing to do is getting a multieffect with USB (or S/PDIF) out, then you can have that one handle all the distortion and speaker simulation. Makes the setup a lot easier.

---

### Post by brianmc on 2014-07-11
> **Tristan_Williams said:**
> I need an audio card that has 1/4" inputs for guitars.

What would be the best choice?

As Johnny Five says, ... "*Need more input*!" That's not-just referring to you looking for high-impedance inputs, but what are your options card-wise? USB? PCI? PCI-E?

There are quite a lot of fairly good USB cards out there which also serve as a breakout box with built-in preamps and quality high-impedance connections equivalent to a DI box.

So as well as asking what options are open to you, there's the matter of budget; and, what else you might want to connect up. You say "guitars" (plural) - is that one at a time, or several? Do you also need mic inputs? Line-ins?

The only people who'll confidently tell you what the "best choice" is  are the salesdroids on commission when you walk into a store. The more information you give, the better people can narrow-down the options they suggest on here. If you're just wanting to connect up a single guitar it could be the case you just pick up a DI pedal, use your onboard sound card's line in, and you've a spare piece of kit that'd allow you to go straight into a PA without lugging around half-a-ton of guitar amp.

---

