---
title: "Need help with my setup VaioF12/Edirol FA-66"
date: 2011-01-12
forum: Ubuntu Studio
---

### Post by Strayfolk on 2011-01-12
Hello!

My story as follows:
Been working with Edirol FA-66 + Ubuntu Studio 10.04 64bit on my Sony Vaio F12 since august 2010. I've been working with Ubuntu Studio since 9.04, so I would classify myself as a intermediate end user. Been tweaking with Jack and trying to get acceptable performance out of my setup for a long time. I've been reading all the HOW-TOs and low latency tutorials and followed them to the degree that I've been able to. Thanks to all you people in the community who've made all this possible!

Now I'm working on an EP, with live recordings in Ardour (about 20 channels), synths and midi in Renoise (about 5 channels). I use Calf plugins (about 10 at a time...) and soft synths (maybe 2 at a time), bristol and hexter and I've tried all the most common software - with various results. CPU usage lies between 3% and 45%. Physical memory @ about 30%. But lots of xruns.

At this moment - I'm trying to mix and make the final magic happen. I run jack at 3x512samples (which is way huge IMO) @ 44,1 kHz but I suffer from very poor performance and stability issues basically regardless of which programs I'm running. I manage to crash all programs except for Renoise and Calf monosynth. Also I tried version Ubuntu studio 10.10 for a while, but it wasn't any better.

I guess what I'm asking for is your opinions of what you think is the problem!

Either I use too many plugins and asking too much of my setup. But I never feel the strain from my computer. Just tens or hundreds of Xruns after a while.

I know I haven't mentioned the possibility that my firewire port is of poor quality, which it probably is. It works @ 3x128samples, but only for audio. No plugins, no fun.

I've tried both the realtime kernel and the lowlatency, but I couldn't get the graphics to work, or it wouldn't boot at all, much because of my other hardware. I got the lowlatency working, but the performance was the same as with the preempt only less stable.

I would love if someone could decipher my story and the output of ffado-diag, 'cos I'm starting to run out of ideas!

Thank you very much for your answers,
Strayfolk

---

### Post by Aztek on 2011-01-12
Run:

```
lspci
```

And look for the line concerning firewire. That'll tell you what chipset you're running (TI is optimal).

Also run 

```
cat /proc/interrupts
```

and post the line about firewire. That'll show if there's anything else hogging the FW bus. My instinct tells me you're trying to run to much stuff but my lack of knowledge tells me to shut up and wait for someone who knows what they're talking about to come along :)

---

### Post by AutoStatic on 2011-01-12
Hello Strayfolk,

You have a Ricoh FireWire controller in your notebook and your mileage may vary with those: [http://subversion.ffado.org/wiki/HostControllers#Ricoh](http://subversion.ffado.org/wiki/HostControllers#Ricoh)
But since the card is being recognized and actually works I don't think your controller is the origin of your xruns.

Your FireWire controller shares its IRQ with an USB bus, your onboard soundcard and your graphics card. That's probably where the xruns come from. So best thing to do is install a realtime kernel and use rtirq to prioritize your FireWire controller. I'm using the Tango Studio kernel myself which is quite good: [http://tangostudio.tuxfamily.org/en/apt-repository](http://tangostudio.tuxfamily.org/en/apt-repository)

And did you disable CPU frequency scaling? Nice system btw. A core i7 ought to perform better than this. I have a less powerful machine with which I run projects that equal the number of things you're running (Qtractor with 20+ audio tracks, lots of plugins, several instances of yoshimi, FluidSynth-DSSI etc.) and over here it runs at 3x64 @ 48Khz.

So I'd try the Tango Studio realtime kernel together with the rtirq-init package from the standard Lucid repo's. if you need any help on setting that up, glad to assist.

Best,

Jeremy

---

### Post by Strayfolk on 2011-01-12
lspci[INDENT]...
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
02:00.0 Network controller: Intel Corporation WiFi Link 6000 Series (rev 35)
03:00.0 SD Host controller: Ricoh Co Ltd Device e822
03:00.1 System peripheral: Ricoh Co Ltd Device e230
**03:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832**
03:00.4 SD Host controller: Ricoh Co Ltd Device e822
04:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4380 (rev 10)
... 
[/INDENT]I put the output of cat /proc/interrupts in a text file 

I'm also running jackdmp 1.9.7 and ffado 2.0.1 ardour 2.8.11

Edits: 
Aztek & AutoStatic. Thank you for your quick answers! I'll consider the RT-kernel and Tangostudio after some more research and backups of my works! As I sort of mentioned, I'm afraid some crucial backport drivers for my internal sound and wireless lan might be unavailable with the realtime kernel. Will have to double check that again though.

Thanks!
Strayfolk

---

### Post by AutoStatic on 2011-01-12
The **ffado-diag** command outputs the same info as both **lspci** and **cat /proc/interrupts**.
But thanks anyhoo :)

---

### Post by Pablo_F on 2011-01-12
> At this moment - I'm trying to mix and make the final magic happen. I run jack at 3x512samples (which is way huge IMO) 

Huge? I disagree. You don't need low latency for mixing and you don't want to stress your CPU with useless demands. To be on the safe side, increase the period size. 

Of course, you need to improve your system configuration as Auto and Aztek suggest. 

Cheers! Pablo

---

### Post by trulan on 2011-01-12
> **AutoStatic said:**
> You have a Ricoh FireWire controller
He's got a Ricoh e832 - that's exactly what I have and mine works great.
> Your FireWire controller shares its IRQ with an USB bus, your onboard soundcard and your graphics card. That's probably where the xruns come from.That's not a good sign.  You can try using an RT kernel and rtirq like AutoStatic suggested, but I'm afraid you may need to use a PC-Card firewire controller to get your firewire controller off that busy IRQ.  On my laptop, the firewire controller shares its IRQ with the wireless card and no amount of tweaking is enough to let me use them both - I have to shut the wireless card off, then ffado is happy.  You can't exactly turn your graphics card off... :(

---

### Post by Aztek on 2011-01-12
> **AutoStatic said:**
> The **ffado-diag** command outputs the same info as both **lspci** and **cat /proc/interrupts**.
But thanks anyhoo :)

That's good to know, thanks! Like I said, it was a good idea to wait for someone who knew what they were talking about :D

---

### Post by AutoStatic on 2011-01-13
> **trulan said:**
> He's got a Ricoh e832 - that's exactly what I have and mine works great.Cool, so that rules out that it could be the controller.

> **trulan said:**
> That's not a good sign.  You can try using an RT kernel and rtirq like AutoStatic suggested, but I'm afraid you may need to use a PC-Card firewire controller to get your firewire controller off that busy IRQ.  On my laptop, the firewire controller shares its IRQ with the wireless card and no amount of tweaking is enough to let me use them both - I have to shut the wireless card off, then ffado is happy.  You can't exactly turn your graphics card off... :(Getting a separate FireWire controller is probably the best option. I do get my FireWire card to work with my FireWire controller that sits on a crowded IRQ (WiFi, GPU, USB port, cardreader and FireWire) but haven't stressed it yet so can't say if it's really reliable.

---

### Post by Strayfolk on 2011-01-13
> **AutoStatic said:**
> Getting a separate FireWire controller is probably the best option.

I've decided to try this before anything else. It makes most sense and hopefully covers the issue in future versions of ubuntu studio aswell.

One question though: How do I check whether my ExpressCard-slot shares IRQ with other hardware? I can't identify it.

---

### Post by jezstudio on 2011-01-30
> How do I check whether my ExpressCard-slot shares IRQ with other hardware? I can't identify it. 	  	

Look lines in /cat/interrupts ; line --> IRQ

---

### Post by trulan on 2011-02-01
> **Strayfolk said:**
> One question though: How do I check whether my ExpressCard-slot shares IRQ with other hardware? I can't identify it.
The /cat/proc/interrupts information is in the ffado-diag output you posted.  Unfortunately, I can't find your card slot either.  On mine I get a 'yenta' driver showing up, but on my old laptop the express card slot only showed up when I actually plugged a card into it.  There may be a way to find it aside from plugging something in, but I'm not aware of it.

---

### Post by Strayfolk on 2011-05-17
I'm reviving this thread after buying a LYCOM firewire expresscard controller with TI chip and testing out different kernels.

1. With the Ubuntu studio 10.04 2.6.32-31-preempt I had a slight improvement in performance. A little less xruns, no weird error messages, just XRUNs. Works well @ 3x1024 samples' buffers. :)

2. Tried the current -realtime kernels from both tango studio and kxstudio. Neither would build with my nvidia-current package. I tested the tango kernel with nouveau drivers but it kept hanging the whole system. Sound performance was good, for the 3 minutes my system would allow. Everything else also seemed to work. I would very much like to use one of these, if my graphics would work. :confused:

3. Which brings me to the 2.6.31-rt from the Ubuntu Repos. After fiddling with the rtirq script I have almost perfect performance. 3x128 buffers. Almost no XRUNS. On the downside, I have no wifi, no internal digital sound output (HDA intel). It's a smaller kernel number, which in my layman's point of view means less support for my <1 year old laptop.

4. Most recently I tried the 2.6.38-lowlatency kernel from kxstudio. Internal sound fully supported, wacom tablet detected and working 90%, touchpad supported without scrolling etc. Firewireaudio worked poorly with a lot of crashes and xruns. New firewire stack only option. No rtirq-settings work as far as I'm concerned. Not really an option.

5. Hoping the future 2.6.39 kernel will do the trick for me. I won't update to 11.04, because of what I experienced with the 2.6.38 kernel.

As you can suspect, I'm rather frustrated that A works in kernel X but not in Y, while B works with kernel Y but not in X, etc. Right now, I'm settling for paragraph number 1. and 3. Rebooting between kernels whenever I want to record. Rebooting again when I want to skype and surf wirelessly. Alternatively I'd like to use a modern -realtime kernel with nvidia.

Also, a BIG thanks to holstein and AutoStatic for their support @ #ubuntustudio.

Happy producing,
Strayfolk

---

### Post by trulan on 2011-05-17
I think you'll like 2.6.39.  Threaded IRQ handlers, the part of the realtime kernel patch that makes the rtirq script work and makes the realtime kernels so good for firewire audio, have been merged into mailine.  It performs better for me than any RT kernel I've used in the past.  I've been testing the RC's, 2.6.39 stable should be out tonight, and hopefully a lowlatency build will be available in a ppa soon.  Be sure to boot with the 'threadirqs' flag in the boot command line, and to set rtirq to prioritize 'firewire' (instead of 'ohci1394' like you use for the older kernels), with those two things set properly 2.6.39 should outperform all the other kernels.

Edit:  You'll need the 270 series NVidia driver to work with 2.6.39 though...

---

### Post by Pablo_F on 2011-05-17
> I tested the tango kernel with nouveau drivers but it kept hanging the whole system...

Have you tried with the kernel boot option "nouveau.noaccel=1"?

---

### Post by Strayfolk on 2011-05-18
Thanks for your input, guys! 

Trulan, that's good news. I'm using nvidia 270.29 atm, so I hope it'll work! (I'll post future results here)

Pablo, I'll try that, if I ever will switch to nouveau again!

Thanks,
Strayfolk

---

### Post by Strayfolk on 2011-08-13
I have some new results:

Sony Vaio F12 running Ubuntu Studio 11.04 64 bit
TI firewire controller
Edirol FA-66

Ardour 2.8 and plugins

I installed 11.04 studio with kxstudio repos a while ago. I instantly upgraded to a 2.6.39 kernel and nvidia drivers. All is good, internal mic works for the first time!

I got firewire audio up pretty painlessly, following all the steps here: [https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)

But still with mindbogglingly many xruns. They seem to occur randomly aswell as being induced by window switching. I've tried different compiz-settings and also running without compiz.

Then it occured to me:

All this time, whenever I've recorded or tried to produce anything, I've always added plugins, IR my favourite, and calf delays and compressors. Filters, the usual. WELL! I opened up a problem child session in ardour (about 25 channels), that's been impossible to mix because of xruns, no matter the buffer sizes. SO I decided to disable all plugins, and VOILA, I can play the whole session at 3x64 buffers, while listening to Spotify AND a 720p Youtube video through jack-pulse. While mixing!

It's a stupid test, but it sort of shows where the problem's been all this time.

Without plugins the amount of xruns is invertedly proportional to the buffer size.
With plugins the amount of xruns is plentyful regardless of buffer size. 3x128, 3x256, 3x512, 3x1024 etc.

So one problem is solved and one problem remains. My hardware is capable and seems to work, even recording at 3x32 works without xruns and a few channels in ardour.

But the problem remains if I want to use plugins... I won't go as far as to blame ardour 2 for the xruns just yet. I will have to do some more research. Some of the ardour3 alphas have provided me some productivity. I'm sort of hoping to be able to mix in a3, whenever it's more stable. 

...To be continued... :)

---

