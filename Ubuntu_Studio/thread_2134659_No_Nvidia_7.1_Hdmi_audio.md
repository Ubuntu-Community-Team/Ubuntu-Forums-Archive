---
title: "No Nvidia 7.1 Hdmi audio"
date: 2013-04-11
forum: Ubuntu Studio
---

### Post by kanaida on 2013-04-11
This isn't ubuntu studio specific, but in previous ubuntu versions I could choose HDMI 7.1
In 12.04/12.10 I get some duplicated options, some output sound, some don't. I've tried all the nvidia drivers, same deal:

Hdmi Stereo
Hdmi Stereo
Hdmi 5.1
Hdmi 5.1

Right now i'm using 5.1 and setting my receiver to PROLOGIC IIX (5.1 -> 7.1) but i'd rather let ubuntu do it since it sounds very nice. I was pretty impressed with the quality of the automatic conversion from 2.0 channel -> 5.1. Windows will just give you 2 channels, and bass when you do that.

I have an Nvidia Geforce 460 GTS/GTX -> SONY STR-DH710 (or similiar) amp -> LG LM7600 Smart 3d tv

Sometimes changing hdmi input on my amp to xbox hdmi then back to pc will leave the screen flashing black. I can hear audio but not see video. I have to shut off the amp, and turn it back on to get a picture.

---

### Post by zequence on 2013-04-11
The audio part will not have anything to do with the nvidia drivers. What drives the audio chip is ALSA. And the server that you are using to access the card with applications is pulseaudio. 
So, this is really a pulseaudio/alsa question. 

Where are you setting these options for stereo and 5.1? In an application, or in the pulseaudio settings/mixer application?

---

