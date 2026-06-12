---
title: "Elec Guitar help"
date: 2010-12-10
forum: Ubuntu Studio
---

### Post by ksadil on 2010-12-10
I need some help with using an electric guitar with ubuntu. I must be missing something simple. I have all the jack, rakarrack, jackctl, etc. 

I cannot get a peep out of jack :(

I can plug in my guitar and record a track in audacity, so I am sure there is hope

My setup is lucid amd64 with 4G ram and the phenom 965X4, so there should be lots of processing grunt. Please help (in little steps)

---

### Post by transmogrifox on 2010-12-11
Probably jack configuration is the best place to start.  Have you been able to start jack successfully?

The first thing is, open a terminal and type
```

$alsamixer

```
then use the tab key, or F4 go get to the capture sources.  Select on the desired capture source (arrow keys) then press spacebar.  That will toggle that source as a capture source.  If it is already a capture source, then leave it on, then turn up the input level on it.

Next make sure all the relevant outputs are active and turned up.  The reason I recommend alsamixer from the command line is because most of the GUI mixers seem to leave out certain switches, channels or options.  Sometimes that's the one option you need to click.

Once you are sure the capture sources are properly configured, then you can use qjackctl.  Make sure you select the proper input & outputs from the correct sound card.

Click start to start jackd.  If it starts and does not give you an error, then that's good.  If not, then fiddle with sample rate, frames/period, etc, until it works.

Next, use a media player like Totem, or audacious (with jack plugin selected as audio source) and play some music through jack to make sure you can get sound out.

Then open Rakarrack and connect capture to rakarrack input, and rakarrack output to the system output(s). Make sure it's activated. Play guitar.  If you don't see the VU bars bouncing you don't have any input, so that would be the place to start looking for problems.

It should be pretty simple once you begin to understand what's going on.  I don't know how much reading you have done on your own, but it is helpful to read the JACK FAQ's on the project web site and learn about what jack is and what it does for you.  Another good thing to do is to kill pulseaudio -- it often fights jack for rights to the audio hardware.  

Finally, Rakarrack help has some relatively extensive detail about how to connect jack & things.  If you have rakarrack open, then F1 will bring up the help browser.  If you can't get jack started and running, then you can get to the help on the project web site.

have fun :)

Edit:  As for recording with Audacity, you have to go into Audacitie's settings menu and select jack as audio input and output source.  Audacity will connect itself to the channel(s) you select in the menu when you press play or record, so don't be concerned if you don't see it active in qjackctl.

---

### Post by ksadil on 2010-12-11
> **transmogrifox said:**
> Probably jack configuration is the best place to start.  Have you been able to start jack successfully?

The first thing is, open a terminal and type
```

$alsamixer

```
....

Oh oh, I get stuck at the first step:

when I start alsa mixer, F6 to select the input sound card, F4 to set capture controls and it says:

This sound device does not have any capture controls. 

I know it does, as I can record onto audacity. Ideas?

---

### Post by Pablo_F on 2010-12-11
Hi, 

Not having capture controls does not mean that there are not capture ports. 

Can you give the terminal output of the following commands please?

Your audio cards and devices for capture and playback:

**arecord -l |grep -v "Subd" && aplay -l |grep -v "Subd"**

Your current jack settings:

**cat .jackdrc**

BTW, kudos to transmogrifox and rakarrack team! :popcorn:

Cheers, Pablo

---

### Post by ksadil on 2010-12-11
kadil@piserver02:~$ arecord -l |grep -v "Subd" && aplay -l |grep -v "Subd"
**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
card 0: NVidia [HDA NVidia], device 2: ALC888 Analog [ALC888 Analog]
card 1: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
card 1: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
kadil@piserver02:~$ cat .jackdrc
/usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2 -H -M


The [USB Audio] is my guitar adaptor.

---

### Post by Pablo_F on 2010-12-11
Hi, 

You are selecting the wrong interface. 

Write down "hw:default" (no quotes) in the interface field of qjackctl's setup. 

Cheers, Pablo

---

### Post by ksadil on 2010-12-13
> **Pablo_F said:**
> Hi, 

You are selecting the wrong interface. 

Write down "hw:default" (no quotes) in the interface field of qjackctl's setup. 

Cheers, Pablo

Can you please explain what I should have in interface/inputdevice/output device fields of Jack setup?

I want my USB guitar as input and my pc speakers as output.

---

### Post by Pablo_F on 2010-12-13
Hi, 

Try:

Interface: (default)
Audio: Duplex
Input device: hw:default,0
Output device: hw:NVidia,0
Input channels: (default)
Output channels: (default)

If this does not work, another option is:

Interface: hw:default

Then run in a terminal

alsa_out -dhw:NVidia

Then make connections.

A third option you can try:

Interface: hw:NVidia

In a terminal:

alsa_in -dhw:default

Please report back, I cannot test.

Cheers, Pablo

---

### Post by transmogrifox on 2010-12-13
> **ksadil said:**
> Can you please explain what I should have in interface/inputdevice/output device fields of Jack setup?

I want my USB guitar as input and my pc speakers as output.

Usually it will have something with USB in the name.  If not, just try all the interfaces available until you get the right one.

---

### Post by ksadil on 2010-12-13
Thanks guys, it works now. 

I just have to get the latency down somehow. Currently at 69ms. Is this bad or normal. Feels bad to play :(

I have a realtime image installed and also ubuntu studio controls. Any ideas on parameters that will move latency in the right direction?

---

### Post by transmogrifox on 2010-12-13
> **ksadil said:**
> Thanks guys, it works now. 

I just have to get the latency down somehow. Currently at 69ms. Is this bad or normal. Feels bad to play :(

I have a realtime image installed and also ubuntu studio controls. Any ideas on parameters that will move latency in the right direction?

Reduce Frames/Period to 256 or less. A faster sample rate will also cause the latency to go down, but processing requirement for all jack applications goes up. Periods/Buffer should be 2 unless you really need something else here to start jack.

Check the "Realtime" box.  

If jack starts, then reduce the Frames/Period. I typically use 128 frames/period at a sample rate of 48kHz, which yields a latency of about 5ms.  

I personally can barely detect any presence of latency when it is less than 10ms.

Some people have jack configured to run at less than 1ms latency.  This requires an audio interface that supports latencies that low, and a minimalistic fine-tuned system typically with a real-time kernel.

It's not worth the effort for me.  I have had good success using stock kernels with jack configured for 5ms latency.

Either way, Frames/Period is the magic parameter.  It tells jack how many audio samples to grab from the sound card at a time.  Setting it to a lower number means your computer takes smaller bites more frequently (lower latency).

---

### Post by ksadil on 2010-12-13
> **transmogrifox said:**
> Reduce Frames/Period to 256 or less. A faster sample rate will also cause the latency to go down, but processing requirement for all jack applications goes up. Periods/Buffer should be 2 unless you really need something else here to start jack.

Check the "Realtime" box.  

If jack starts, then reduce the Frames/Period. I typically use 128 frames/period at a sample rate of 48kHz, which yields a latency of about 5ms.  

I personally can barely detect any presence of latency when it is less than 10ms.

Some people have jack configured to run at less than 1ms latency.  This requires an audio interface that supports latencies that low, and a minimalistic fine-tuned system typically with a real-time kernel.

It's not worth the effort for me.  I have had good success using stock kernels with jack configured for 5ms latency.

Either way, Frames/Period is the magic parameter.  It tells jack how many audio samples to grab from the sound card at a time.  Setting it to a lower number means your computer takes smaller bites more frequently (lower latency).

Cool, thanks.

Jack WAS working but now will not, with exactly the same settings. My test machine is Ubuntu with ubuntu studio packages installed.

 I am burning an ubuntustudio dvd now to try it on another pc, this time intel based.

See if I can get more reliability out of this machine?

---

### Post by transmogrifox on 2010-12-13
> **ksadil said:**
> Cool, thanks.

Jack WAS working but now will not, with exactly the same settings. My test machine is Ubuntu with ubuntu studio packages installed.

 I am burning an ubuntustudio dvd now to try it on another pc, this time intel based.

See if I can get more reliability out of this machine?

Sometimes when ubuntu reboots it changes the device number on whatever you had plugged in. Especially if you left the USB audio interface plugged in when you booted, then udev may enumerate devices differently.

In that case you should have a look at the device actually selected for jack input/output and make sure it's the USB card and not the other.

That is the only thing that comes to mind for me.  There is a way to configure a text file to force a certain identity to each card so it never changes between boots (I did it on my desktop, and now I can't remember how...but some 'net searching will turn up some instructions).

My quick'n'dirty solution is to unplug the USB interface, then plug it in after the machine is already booted and running.  That way the internal card gets designation hw:0, and the USB card gets hw:1

---

### Post by ksadil on 2010-12-13
> **transmogrifox said:**
> Reduce Frames/Period to 256 or less. A faster sample rate will also cause the latency to go down, but processing requirement for all jack applications goes up. Periods/Buffer should be 2 unless you really need something else here to start jack.

Check the "Realtime" box.  

If jack starts, then reduce the Frames/Period. I typically use 128 frames/period at a sample rate of 48kHz, which yields a latency of about 5ms.  

I personally can barely detect any presence of latency when it is less than 10ms.

Some people have jack configured to run at less than 1ms latency.  This requires an audio interface that supports latencies that low, and a minimalistic fine-tuned system typically with a real-time kernel.

It's not worth the effort for me.  I have had good success using stock kernels with jack configured for 5ms latency.

Either way, Frames/Period is the magic parameter.  It tells jack how many audio samples to grab from the sound card at a time.  Setting it to a lower number means your computer takes smaller bites more frequently (lower latency).

Hmmmm Frames per period <1024 gets choppy. I have the frequency scaling set to performance as well. Any particular settings for nice make a difference?

New machine is a 2.2GHz intel cpu laptop with 2G ram

Built in sound card and this usb guitar adaptor

Latency sounds better than the other machine

---

### Post by ksadil on 2010-12-14
Interesting, I had another laptop I could try it on and being the slowest of the group, I expected poor performance, but it had the best performance, and without even the realtime kernel. Quite acceptable latency and occasional jitter for just practicing at home

---

### Post by AutoStatic on 2010-12-14
> **transmogrifox said:**
> Periods/Buffer should be 2 unless you really need something else here to start jack.Most USB audio cards work better with a buffer setting of 3 periods: [http://lists.linuxaudio.org/pipermail/linux-audio-user/2010-January/066765.html](http://lists.linuxaudio.org/pipermail/linux-audio-user/2010-January/066765.html)

Best,

Jeremy

---

### Post by ksadil on 2010-12-14
> **AutoStatic said:**
> Most USB audio cards work better with a buffer setting of 3 periods: [http://lists.linuxaudio.org/pipermail/linux-audio-user/2010-January/066765.html](http://lists.linuxaudio.org/pipermail/linux-audio-user/2010-January/066765.html)

Best,

Jeremy

mmm tried that, but still not good

---

### Post by ksadil on 2010-12-17
YES!!! finally solved :) The latency seems to be related to the USB adapter that I plug the guitar into. Or maybe it's interface with my system.

I bought a little cheap 4 channel mixer $40, and hooked up

guitar **to** shielded cable **to** mixer **to** unshielded cable **to** line in of my onboard line-in port

I can set latency down to 8 msec !!!

Funny thing is I seem to be tuned in to a local radio station with this setup, I think through the unshielded cable.

Thanks for the help, I need to buy some more shielded cables

---

### Post by RaumTrug on 2010-12-18
hi! I've had a similliar prob. with an usb-device (in my case a mic...). I wished to "monitor" it in realtime on another soundcard, but like in your case selecting different devices for input and output made jack stutter & even crash when latencies were below a certain (still unusable) amount.

you could try doing "record only"-mode with the usb-device with a low latency. you won't of course hear anything, but if you can record without dropouts/xruns, you know you're affected by the same "bug" as me.

I found help in using alsa_in/alsa_out, or jack2 audioadapter, search this forum for hints on using it. you basically start jack, with little latency with the device you wish to record, and then add your onboard or whatever soundcard with a shell command to jack. or other way 'round.

maybe this helps you to eb able to use your usb-adapter instead of the preamp. but imho single-souncard sollutions are always best (though the guitarplug will probably have better quality than your soundcard's line-in).

---

### Post by ksadil on 2010-12-20
> **RaumTrug said:**
> hi! I've had a similliar prob. with an usb-device (in my case a mic...). I wished to "monitor" it in realtime on another soundcard, but like in your case selecting different devices for input and output made jack stutter & even crash when latencies were below a certain (still unusable) amount.

you could try doing "record only"-mode with the usb-device with a low latency. you won't of course hear anything, but if you can record without dropouts/xruns, you know you're affected by the same "bug" as me.

I found help in using alsa_in/alsa_out, or jack2 audioadapter, search this forum for hints on using it. you basically start jack, with little latency with the device you wish to record, and then add your onboard or whatever soundcard with a shell command to jack. or other way 'round.

maybe this helps you to eb able to use your usb-adapter instead of the preamp. but imho single-souncard sollutions are always best (though the guitarplug will probably have better quality than your soundcard's line-in).

With this cheap mixer with the onboard sound, everything is simple and performs well. No USB, 1 MIC input and we can use 4 instruments to jam. I can see me using midi devices in future, but for jamming nothing else is required.

The guitar was an ebay bargain, so the quality difference is not evident, at least to me. If I need better quality, I will buy a better sound card in place of the onboard unit, and use it for both in and out.

But what I have works perfectly now for my application.

---

