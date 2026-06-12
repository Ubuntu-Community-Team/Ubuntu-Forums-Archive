---
title: "Need some help with Ardour, jack and an analog mixer"
date: 2010-12-06
forum: Ubuntu Studio
---

### Post by w33k on 2010-12-06
Hello!

I have a mixer (Behringer 1202) connected to my computer through the input. It is recognised by alsa as "Microphone 1" and I can record my guitar through the mixer with the simple sound recorder. Sound preferences also offer "Microphone 2" and "Line-in" but the jack I'm using is presented as "Microhpone 1".

Now, jack control shows the following when choosing the "connections" menu and having Ardour running: see attached picture.

I suspect that the 8 playback_N are the mixer tracks, as there are 8 of them.

When I press record and play a little on the guitar nothing is recorded. 

The output from the computer is also wired through the mixer and works well in all other applications. I have a soundblaster X-fi.

What is wrong? Any help is appreciated!

---

### Post by Pablo_F on 2010-12-06
Hi, 

Can you give the terminal outputs of:

cat .jackdrc 
arecord -l |grep -v "Subdevice"
aplay -l |grep -v "Subdevice"

Note that sound recorder and probably the other apps you mention are using pulseaudio. Pulseaudio is the default audio server and gnome sound preferences is a pulseaudio front-end. Don't get confused by it, when jack is up and running (and of course, when ardour is up and running) it is useless. 

You can always have access to the card's internal mixer through a lower level application called alsamixer (alsamixer in CLI or gamix, gnome-alsa-mixer and other as GUI's). 

The keys are qjackctl configuration and audio card's alsa mixer configuration. 

Cheers, Pablo

---

### Post by w33k on 2010-12-07
Hi there and thanks for the reply. Since my last post I played around with the settings and jack and got ardour to record input from my mixer. Now the problem is that I cannot hear what I have recorded, ie ardour produces no sound.

```
cat .jackdrc: 
/usr/bin/jackd -dalsa -r44100 -p1024 -n2 -D -Chw:1,0 -Phw:1,0 -s -m

arecord -l |grep -v "Subdevice"
**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
card 0: NVidia [HDA NVidia], device 2: ALC888 Analog [ALC888 Analog]
card 1: XFi [Creative X-Fi], device 0: ctxfi [Front/WaveIn]

aplay -l |grep -v "Subdevice"
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
card 1: XFi [Creative X-Fi], device 0: ctxfi [Front/WaveIn]
card 1: XFi [Creative X-Fi], device 1: ctxfi [Surround]
card 1: XFi [Creative X-Fi], device 2: ctxfi [Center/LFE]
card 1: XFi [Creative X-Fi], device 3: ctxfi [Side]
card 1: XFi [Creative X-Fi], device 4: ctxfi [IEC958 Non-audio]
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]

```

As you can see in the screenshot, jack uses hw:1,0 which is Front/WaveIn. This works to record things.

hw:1,0 does not produce any output though. I have also tried the other options. 

So, now, the problem is which device to wire jack's output to. Perhaps the problem is in ardour...

Thanks. :)

---

### Post by Pablo_F on 2010-12-07
Hi, 

I assume you are conecting from the green 1/8" jack in the XFi. This should be the front output if I am not wrong.

To narrow down the sources of the problem, try playing music through a jack-aware audio player. I suggest aqualung. 

Double check the jack connections and don't forget to take a look at alsamixer. Use "alsamixer -cn" where n is the number of the XFi card. In this example, -c1 but that can change... check the order of your cards with "aplay -l" or "cat /proc/asound/cards" before running alsamixer.

A bit OT but worth knowing:

In this case and at this moment, hw:1,0 is the XFi Front/Wavein but that can change when you have several audio cards. That is why I strongly recommend you use the name of the card. So, instead of hw:1 use hw:XFi. For example, "hw:XFi,0" for capture and "hw:XFi,0" for playback. However in this case, you can also leave capture and playback devices in "(default)" and use the interface "hw:XFi", which will default to device 0 for capture and playback.

Also, if you are not going to use it at all, I suggest you disable the onboard card from BIOS.

Cheers, Pablo

---

### Post by w33k on 2010-12-08
Hello again! After some tweaking (ie changing the output in jack) I can now record and hear stuff in audacity but no longer in ardour... I have no idea what I changed to make it not work but it must be something in ardour.

Attached is a ss of ardour with one added track and jack

Any ideas?

---

### Post by w33k on 2010-12-09
Problem solved! It turns out that jack changed the device name (as you said...) so at some boots it worked and at others it didn't. Once I figured that out I remembered what device should be used and now it works.

Thanks for your help!

Rock on!

---

