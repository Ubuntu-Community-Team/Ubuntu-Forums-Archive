---
title: "Help needed to improve set up Focusrite Saffire"
date: 2011-01-13
forum: Ubuntu Studio
---

### Post by elysithea on 2011-01-13
Hi :D, I am very new to Ubuntu and this is my first post so please be patient with me.

I installed Ubuntu 10.10 on a HP nx7010 notebook and then added the Audio package from ubuntu studio. I followed the guides and read a lot on the forum and managed to get the Focusrite Saffire working but with a lot of XRUN's. When I get this working well I will add a Novation Remote 49SL and some other stuff, my goal is to learn and adapt. 

I have attached a screenshot and the results of:

[LIST]
[*]**lspci | grep 1394**
[*]**cat /proc/interrupts**
[*]**ffado-diag**
[/LIST]
and a screen shot showing Jack setup and Patchage.

I am stuck, not sure if things are set up correctly and don't even know what specific question I should be asking ( :D total noob )

A few questions/confusions/doubts:

I have disabled processor scaling (? sp.) in the bios, which improved things, but there are not many options to do much more there, so is there any other way of changing the assigned IRQ's as it seems to be a bit crowded on the interrupt where the firewire is?? 

Also I have read a thread where it seems possible to install a lowlatency kernel from **ppa:abogani/ppa **but I do not understand how to do this :confused: - please could someone explain how to do this??

Any other suggestions or advice will be gratefully received :D

---

### Post by AutoStatic on 2011-01-13
Hello elysithea,

Which Saffire is this about? I assume a Pro 10 IO? And yes, the IRQ on which your FireWire controller sits is a bit crowded so the xruns might be caused by this. If that's the cause a -lowlatency kernel won't help, then you'll probably need a -realtime kernel and the rtirq-init script.
But try setting periods/buffe to 3 first instead of 2. And maybe the -S (synchronous) switch will work with Jack. I think you can add that option to the Jack server path in QjackCtl.

Best,

Jeremy

---

### Post by elysithea on 2011-01-13
Hi Jeremy,

Thanks for the reply :D. It worked and I am not getting any XRUN's with a latency of 8.71ms.

Do you think that there is anything else that can be done now to reduce the latency? 

The Saffire is an original Saffire (quite old lol). I am setting this up with spare bits of equipment so I can learn Ubuntu and how to use the studio tools. I hope I can get my head around all of this as I am a bit fed up with the rather more expensive alternatives from Steinberg et al.

I have already plugged in the Novation Remote 49SL Compact and can see two windows in patchage with 3 midi ports in each - I guess I need to connect this to a synth and the synth to the Saffire but I am not sure which applications to use, I will also need a sequencer/mixer/other. Can you recommend a good starting point?

Thx. 
Sarah

---

### Post by elysithea on 2011-01-13
Hi Jeremy,

I forgot to say that I tried reducing the Frames/Period setting to 64 but started getting XRUN's again.

Thanks so much for your help
Sarah

---

### Post by AutoStatic on 2011-01-14
> **elysithea said:**
> Thanks for the reply :D. It worked and I am not getting any XRUN's with a latency of 8.71ms.

Do you think that there is anything else that can be done now to reduce the latency?Hello sarah, you could check here maybe: [http://wiki.linuxmusicians.com/doku.php?id=system_configuration](http://wiki.linuxmusicians.com/doku.php?id=system_configuration)

> **elysithea said:**
> The Saffire is an original Saffire (quite old lol).A quite old original Saffire is not an official Focusrite Saffire model ;) What is the exact type? Is it a grey one with blue leds?

> **elysithea said:**
> I have already plugged in the Novation Remote 49SL Compact and can see two windows in patchage with 3 midi ports in each - I guess I need to connect this to a synth and the synth to the Saffire but I am not sure which applications to use, I will also need a sequencer/mixer/other. Can you recommend a good starting point?Sequencer: Qtractor, seq24
Mixer: Qtractor
Softsynths: Yoshimi, PHASEX, amSynth

And regarding 64 frames and xruns, what number of periods are you using? It is best to use a periods setting of 3 instead of 2 for bus devices (USB/FireWire).

Best,

Jeremy

---

### Post by elysithea on 2011-01-14
Hi Jeremy,

Thanks for the link, I will work through it and see what I end up with :D (see note below)

The Saffire is White ish (lol maybe it needs a clean) with green/orange leds - please let me know if this is a supported one or how to determine if it is. There is one problem that I noticed - The FFado-mixer seemed to stay saying Reconfiguring the bus, Please Wait and never completed opening (I started to read through the FFado site but didn't get to any conclusion as to what was going on).

When I set the frames to 64 I left the periods at 3 as you had suggested.

Last night I ended up going through the software that was installed from the audio package and tried a bunch of stuff to see what each thing was. Some things semed to work and others not but I sort of came to the conclusion that it had to do with the relationship between Jack/Pulse/ALSA which I am still confused about. Also the whole thing surrounding the realtime/RT/lowlatency Kernel and Maverick is a bit beyond me and I started to think that maybe it would be better to install 10.04 where this exists as it became clear that 8.71ms is a bit too high to be useable. (Note: I still need to try the suggestions in the link you sent).

At the moment I have 2 boot options:

1. Maverick 10.10 setup with all the day to day backoffice stuff I need.
2. Maverick 10.10 with the audio things (this is where I did the audio package install)

I will add a 3rd option:
3. 10.04 

My doubt is- is it best to install 10.04 ubuntu studio or install normal 10.04 and add the packages/RT kernel etc. Or is this just a really bad idea :confused:

Thanks for the suggestions of the softsynths/sequencer I will install them now :D and thankyou again for your help.

Sarah

---

### Post by AutoStatic on 2011-01-14
> **elysithea said:**
> The Saffire is White ish (lol maybe it needs a clean) with green/orange leds - please let me know if this is a supported one or how to determine if it is.That's the Saffire. So just Saffire :) And it is fully supported by FFADO: [http://ffado.org/?q=node/15](http://ffado.org/?q=node/15)

> **elysithea said:**
> There is one problem that I noticed - The FFado-mixer seemed to stay saying Reconfiguring the bus, Please Wait and never completed opening (I started to read through the FFado site but didn't get to any conclusion as to what was going on).Iirc you have to start **ffado-dbus-server** manually on Maverick.

> **elysithea said:**
> When I set the frames to 64 I left the periods at 3 as you had suggested.Ok, then it's probably something else that is causing the xruns. But you already suggested yourself to try out 10.04. I think that's worth a try. I prefer installing plain Ubuntu myself, so no Ubuntu Studio. And then you could try installing the realtime kernel from Tango Studio: [http://tangostudio.tuxfamily.org/en/apt-repository](http://tangostudio.tuxfamily.org/en/apt-repository)
The realtime kernel is in the low-latency repository (so you'll have to add 'low-latency' to the APT line, without the quotes).

Best,

Jeremy

---

### Post by cchhrriiss121212 on 2011-01-14
Quick question: Are you testing jack by using VLC? I always get xruns when using vlc through jack, but everything else I use is stable. Try using Hydrogen or something that has native jack support.

---

### Post by cchhrriiss121212 on 2011-01-14
Quick question: Are you testing jack by using VLC? I always get xruns when using vlc through jack, but everything else I use is stable. Try using Hydrogen or something that has native jack support.

---

### Post by cchhrriiss121212 on 2011-01-14
Double post

---

### Post by dawiba on 2011-01-14
Hi

I have a Saffire LE. It has a slightly different number of i/o and no onboard dsp, but other than that is essentially the same.

From a clean install of regular Ubuntu 10.10, all I did was install a few audio packages, set up Jack and add myself to the audio group. I've had no need to start ffado-dbus-server manually.

If I try to run with Frames/Period at 64, it will run but I do get xruns. I've attached a screenshot of my Jack settings. At these settings, I sometimes get an xrun when opening or closing a program and that's pretty much it. I find the settings good enough not to have any bother with latency.

Hope this helps

---

### Post by elysithea on 2011-01-14
Hi Cchriss

At first I used vlc just to get some sound but then I started hooking up other things - midi keyboard, mic, guitar, synth and other softsynths, ardour etc. I agree that vlc produces more xrun's but I was also getting quite a few from the audio inputs on the saffire. I think the problem comes from the crowded interrupts, and the lack of an RT kernel / config to setup priorities on the interrupts means I can't do a lot about it. At 128 frames I got no dropouts when recording audio but at 64 there were some (vlc at 64 there were lots :eek: ). 

I am not going to give up on Maverick but I am going to try out Lucid aswell :D

Thanks

Sarah

---

### Post by elysithea on 2011-01-14
Hi Cchriss

At first I used vlc just to get some sound but then I started hooking up other things - midi keyboard, mic, guitar, synth and other softsynths, ardour etc. I agree that vlc produces more xrun's but I was also getting quite a few from the audio inputs on the saffire. I think the problem comes from the crowded interrupts, and the lack of an RT kernel / config to setup priorities on the interrupts means I can't do a lot about it. At 128 frames I got no dropouts when recording audio but at 64 there were some (vlc at 64 there were lots :eek: ). 

I am not going to give up on Maverick but I am going to try out Lucid aswell :D

Thanks

Sarah

---

### Post by elysithea on 2011-01-14
Hi Cchriss

At first I used vlc just to get some sound but then I  started hooking up other things - midi keyboard, mic, guitar, keyboard/synth and  other softsynths, ardour etc. I agree that vlc produces more xrun's but I  was also getting quite a few from the audio inputs on the saffire. I  think the problem comes from the crowded interrupts, and the lack of an  RT kernel / config to setup priorities on the interrupts means I can't  do a lot about it. At 128 frames I got no dropouts when recording audio  but at 64 there were some (vlc at 64 there were lots :eek: ). 

Hi dawiba

Thanks for your help -  the settings you are using also give me 8.71ms latency which is good and more than acceptable. 


Maybe I am too fussy but I would like to see a number closer to 3ms just to avoid Vocal verbis or drummer decay both of which are harder to deal with than computer problems :lolflag:  ( I appologise for rubbish sense of humor)

I am not going to give up on Maverick but I am going to try out Lucid aswell :D

Thanks

Sarah

---

### Post by Pablo_F on 2011-01-14
Once you have the lowest possible latency, measure it by means of jack_delay (jdelay). That will show you the real round-trip latency. Anyway, trust your ears above all. 

Cheers! Pablo

---

