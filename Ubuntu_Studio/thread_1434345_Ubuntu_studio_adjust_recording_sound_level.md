---
title: "Ubuntu studio adjust recording sound level"
date: 2010-03-20
forum: Ubuntu Studio
---

### Post by amalgamas on 2010-03-20
I am new to ubuntu studio and use it with a m-Audio delta 1010 soundcard.  Currently I am recording old LPs with Audacity, but i cannot find any way to regulate the recording level.  Everything I try does not seem to have any effect on the recorded waveform in Audacity.  

Any suggestions?

---

### Post by Capoeira on 2010-03-20
you have to use the gnome-mixer or any other mixer.

it's a setting of your soundcard, so you can't regulate it in Audacity itself

looks something like that: [http://www.domenech.org/bt878a-adc/gnome-alsa-mixer-ensoniq.png](http://www.domenech.org/bt878a-adc/gnome-alsa-mixer-ensoniq.png)

---

### Post by RaumTrug on 2010-03-20
I think the card has the chip "ice1712"? then install the package "alsa-tools-gui", will bring you a prog called "envy24control". start either in the multimedia menu (it installs a few other mixers for other cards hike rme hdsp, too...ignore them), or in a terminal with "envy24control".

you can manipulate all those settings with a regular alsa mixer, too, the e24ctrl prog actually uses the alsa mixer interface, but it is a bit more intuitively designed & features level meters for all the channels

you can config the internal mixer with this tool, and the input levels are best set with the right "adc" sliders for the channels you record, with the proper channels set in internal mixer to max on the right l und r channel. rule the adc's until the level meters don't enter red anymore, but as they got no resettable peak/clip display, I'd recommend using some other metering tool. there are some for the jack environment, like "jack meterbridge".

I have no clue how the prog really looks for the 1010lt, I only have a 2496 which has far less channels, but I guess it is similliar - it tries to mimick the windows/mac m-audio mixer.

---

### Post by amalgamas on 2010-03-20
Thank you for your responses [Capoeira]("http://ubuntuforums.org/member.php?u=621122") and [RaumTrug]("http://ubuntuforums.org/member.php?u=826324"), but I have tried all I can think of with both mixers and about every other thing I can think of.  Nothing I do seems to change the recorded waveform in Audacity.  I reckon there must be something wrong with my sound system, some driver or setting problem, but being an unexperienced ubuntu-user, I have no idea of what it might be.
I use Ubuntustudio 9.10

---

### Post by cchhrriiss121212 on 2010-03-22
What exactly is the problem with your recorded waveform, too loud or too quiet?
What does your recording chain look like? You should be using some kind of pre-amp in between the turntable and the delta, which is what I would use to regulate the sound level.

---

### Post by RaumTrug on 2010-03-22
are you sure you really fiddled with the right "ADC" sliders? (adc is short for analog to digital converters, those controll the preamps of your inputs) normally you should at least be able to lower the volume with them, if they're at zero, no input should be recorded. test that to find the channels!

also test if the "dac" (preamps for output) sliders do something with the output volume! if not, there might indeed be probs with the driver/mixer...

I just guess you've fiddled with mixer sliders (where one left & one right are for each input & output channel, with meters next to them & mute/link buttons in envy24control) - for example for my card they only work when the monitor mixer is enabled! those won't control your recording volumes/preamps, unless you record from the monitor mixer channels, for example with jack (on my card it's capture channels 11 & 12).

it's a bit confusing, I know, but just try again to see if the adc/dac sliders work for your card - yours has 10in 10out, so there should be the corresponding number of adc/dacs in envy24control (if your card has s/pdif, those channels have no preamps).

---

### Post by amalgamas on 2010-03-28
> **cchhrriiss121212 said:**
> What exactly is the problem with your recorded waveform, too loud or too quiet?
What does your recording chain look like? You should be using some kind of pre-amp in between the turntable and the delta, which is what I would use to regulate the sound level.
It is to quiet, and I want to be able to control the input volume.

---

### Post by amalgamas on 2010-03-28
> **RaumTrug said:**
> are you sure you really fiddled with the right "ADC" sliders? (adc is short for analog to digital converters, those controll the preamps of your inputs) normally you should at least be able to lower the volume with them, if they're at zero, no input should be recorded. test that to find the channels!

also test if the "dac" (preamps for output) sliders do something with the output volume! if not, there might indeed be probs with the driver/mixer...

I just guess you've fiddled with mixer sliders (where one left & one right are for each input & output channel, with meters next to them & mute/link buttons in envy24control) - for example for my card they only work when the monitor mixer is enabled! those won't control your recording volumes/preamps, unless you record from the monitor mixer channels, for example with jack (on my card it's capture channels 11 & 12).

it's a bit confusing, I know, but just try again to see if the adc/dac sliders work for your card - yours has 10in 10out, so there should be the corresponding number of adc/dacs in envy24control (if your card has s/pdif, those channels have no preamps).
After my last post the Ubuntustudio crashed, possibly due to some fiddling from my curious son.  I have resinstalled and will post back in a few days...

---

