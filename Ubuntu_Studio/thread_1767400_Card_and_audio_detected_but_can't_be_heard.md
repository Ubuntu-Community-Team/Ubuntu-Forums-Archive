---
title: "Card and audio detected but can't be heard"
date: 2011-05-25
forum: Ubuntu Studio
---

### Post by leekaiwei on 2011-05-25
I'm using 11.04 and have M-Audio Audiophile 2496. Pulseaudio control detects the card and the bar under the output volume control varies from left to right as the volume of the media changes. However I still can't hear anything.

---

### Post by Pablo_F on 2011-05-25
Hi, 

Take a look at the sound preferences, configuration tab. Do you see an option for  "analog output" or are there all of them for digital configurations? If the latter is true, it is a known issue with pulseaudio and this kind of cards, easily solved by editing a configuration file. We will tell you how, but please, check first.

Cheers, Pablo

---

### Post by leekaiwei on 2011-05-25
Yes there is an option for Stereo Analogue Output.

---

### Post by Pablo_F on 2011-05-25
Just to confirm, you mean for the ICE1712 [Envy24] (which is the m-audio).

Please, install alsa-tools-gui and run envy24control. It is similar to the program you will see in the m-audio user manual. If you are in doubt, run amixer and paste here the output.

(just in case you have more than a soundcard, check this:

cat /proc/asound/cards

If the m-audio is the second one (numbered 1 as counting is zero based), the amixer command should be "amixer -c1".

Cheers, Pablo

---

### Post by leekaiwei on 2011-05-26
Thanks very much. It works now.

---

### Post by leekaiwei on 2011-05-27
I have another sound problem but I'm not sure if I should make a new thread. Sound doesn't work after suspend/hibernate. I tried force reloading ALSA but that didn't work. Works fine after a full reboot though.

---

### Post by mudster on 2011-06-08
sorry to butt in on this thread, but I'm just trying to configure 11.04 & I'm having the same problem as Leekaiwei. I'm a complete newbie to Ubuntu and I'm finding my around, so bear with me. I've used Synaptic to install Alsa Tools, but I can't find Alsa tools anywhere even though Synaptic reports it being installed. Where do I find Alsa in order to launch it?

---

### Post by Pablo_F on 2011-06-08
You need to install alsa-tools-gui which includes envy24control (as well as other control apps for different audio cards).

You can find it under the Sound and Video menu. If unsure, you can always launch it from the command line ([ALT-F2] or a terminal) by typing *envy24control*

Note that this app is for accessing hardware controls. Let's say, it is a low level application. 

Ubuntustudio has higher level software, the so-called sound servers, namely, the default pulseaudio (via Sound Preferences) and jackd (via Jack Control). 

The m-audio audiophile 2496 PCI works like a charm with jack. I am not sure about pulseaudio in 11.04, it could work out of the box or you might need a little tweak in a text configuration file.

---

### Post by mudster on 2011-06-08
ok, thanks Pablo. I've launched Envy24control. Now lets see if I can configure the sound card:confused:

---

### Post by mudster on 2011-06-08
the card is recognised as number 1 in envy24control, but I still can't get any sound. I've read elsewhere that pulseaudio needs to be removed. In synaptic pulseaudio seems to have a lot of dependencies and I'm not sure of what to remove?

On edit: Fixed. The analogue level were at zero in default, which is damn silly and has cost me hours of farting around.

---

### Post by bluesscream on 2011-06-12
That's Linux hehe, those coder nerds shut down their  brains just in time proggy is running ;)

---

