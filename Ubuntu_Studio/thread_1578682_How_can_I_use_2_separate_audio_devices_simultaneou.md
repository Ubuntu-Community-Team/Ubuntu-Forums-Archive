---
title: "How can I use 2 separate audio devices simultaneously?"
date: 2010-09-20
forum: Ubuntu Studio
---

### Post by Druid57 on 2010-09-20
I am experimenting with UbuntuStudio Maverick beta 64  bit. The release notes suggested that JACK and PulseAudio could run side-by-side, which I hoped meant that I could direct output from different programs to different devices. I have built-in sound ( *0 [NVidia         ]: HDA-Intel - HDA NVidia        HDA NVidia at 0xfe024000 irq 22*) and a Logitech wireless headset w/ microphone (*1 [Headset        ]: USB-Audio - Logitech Wireless Headset              Logitech Logitech Wireless Headset at usb-0000:00:0b.1-2.1, full speed*). Despite several attempts at configuring JACK to use one sink and Pulseaudio the other, and Googling in vain for answers, I have been unsuccessful. Ideally, I would like to have Audacity play through the built-in sound, and everything else go through the headset. I would be grateful for any advice! TIA

---

### Post by Pablo_F on 2010-09-21
The problem might have to do with qjackctl launching pasuspender (I am not sure what happens in Maveric. Try qjackctl in a terminal and check). 

If this is so, launch jackd from CLI. Then you can use patchage to make jack connections. I also suggest you use pavucontrol for pulseaudio configuration and control.

Make sure you launch jackd with the correct parameters, especially the right soundcard. 

We can help better if you show the output of

aplay -l

Cheers! Pablo

---

### Post by Pablo_F on 2010-09-21
Sorry, I am in maverick now. I see that qjackctl is not launching pasuspender anymore.

So I don't know what happens. Launch jack with your usb card, then pavucontrol. In the configuration tab you shoud see the onboard audio card.

I don't know what the problem is. It works for me in maverick. make sure that the apps you launch are clients of the right server. 

You can test this with two instances of mplayer:

mplayer -ao jack some-music.ogg

In another terminal:

mplayer -ao pulse some-music.ogg

That said, in response to the original question, you also can use both cards with one audio system, pulseaudio or jack. 

If you want to use both cards with jack, you should use the alsa_out client, or alsa_in for capture.


EDIT:

Wait a minute. Are you sure you need jack? As I pointed out, if you run the jack server, only "jackified" apps will have sound. I am not sure if you want this. You can use pulseaudio with both cards simultaneously, I think. pavucontrol is the tool you need.

Cheers! Pablo

---

