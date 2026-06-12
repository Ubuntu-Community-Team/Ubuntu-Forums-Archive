---
title: "Ubuntu Studio - Audio Interface advice"
date: 2008-10-10
forum: Ubuntu Studio
---

### Post by Snoo on 2008-10-10
Hi there.

I am soon to set out recording my band using Hardy Heron. This involves buying some interface hardware and parting with some cash!
So I've got a few questions to hopefully avoid a headache.

_Firewire:_ Is this supported well? Are there any specific types of boards I should head for?

_Interface:_ I'm really liking the Alesis IO26 due to it's flexibilty. Is anybody running one? Is it supported? If not, could people suggest alternatives? (Presonus?)

The biggest thing I shall be recording is the drums requiring 6 mics. The rest will be straight DI inputs from amps.

Thanks in advance for any help.

---

### Post by thorgal on 2008-10-10
if you are using a desktop, go PCI or PCI-e. PCI is your safest bet.

Firewire is experimental (FFADO project, formerly freebob which does not cover most interfaces).

If your band has some bucks to gather, get an RME system (HDSP combined with a Multiface II box, and some RME Octamic Preamps). This is pricy for an individual alone but for a band, that shall be OK.

I myself (lone individual) own a PCI HDSP card + Multiface II IO box, combined with a RME Quadmic preamp (I don't have a drum to record, but I do have a few acoutic instruments that require mic preamp). It's the BEST investment I made for my home studio. Latency is peanuts, audio quality is amazing (signal to noise ratio, transparency of the preamp, etc).

DO yourself a favor, get your band to collect the necessary money and gear up with RME PCI devices.

---

### Post by Snoo on 2008-10-10
Hi Thorgal.

Thanks for your reply. I'm afraid it's a tad over my head though. (Although I know what PCI & e is!)

Low cost is the aim. I'd rather go with a 1 box such as the Alesis or a firepod. So Firewire isn't an option? How is USB2 for interfaces?

---

### Post by thorgal on 2008-10-10
firewire could be an option but it is a bit of a lottery, be sure to read everything you can on the subject. 

USB2 is also an option, it's just more CPU intensive than firewire. If you want to record drums, make sure you have some hardware monitoring. With USB2, I don't think you can achieve _stable_ (aka no xruns) sub 5ms software latency, which for the drums may be a problem. 

Still, it is unfortunate that amateur musicians and music producers have to compromise between quality and budget. Save some bucks, make a decent demo, give some gigs and upgrade with better gears later on :)

---

### Post by Snoo on 2008-10-10
Anybody else had any experience with the Alesis or Presonis Firepod et al?

Be interested to hear what people are running.

Cheers!

---

### Post by cb951303 on 2008-10-10
I'm not sure if it covers your need but look at this: [http://www.lexiconpro.com/ProductIndex.aspx?ProductID=6](http://www.lexiconpro.com/ProductIndex.aspx?ProductID=6)

it works with linux

---

### Post by aeiah on 2008-10-11
unless you've got all your mics already, id go for good solid mics and then just something like an m-audio delta 10/10. its pci with a breakoutbox. rackmountable i think. i just have the delta 44 but the 10/10 has 10 inputs and 10 outputs which you'll need if you're recording your band at least half live. but yea, no point spending a million dollars on a great sound interface if your mics are **** or you dont know how to record drums properly. drums are a bitch :(

---

### Post by babarosa on 2008-10-11
Hello Folks!

Of course it is always a matter of taste and your personal needs which interface suits you best.

_Firewire:_
If you consider to buy a firewire-interface be sure to check all information sites _especially_ ffado's site: Only consider purchasing one which is described there as "supported". But still you will have some problems to overcome.
The most important advantage: You'll reach stable latencies appr. 2-3 ms at 44.1 KHz doing multichannel recording.

I am using a terratec phase88 rack firewire. while providing a fine audio quality it works very well with "ffado" but some work has to be done until you can use it. Of course the community helps you. because it is from 2004 this interface goes at a rather fine price - € 299,- e.g. here in austria). 

_USB2:_
To my mind the most uncomplicated tool is using one of the modern "analog"-looking mixer consoles with a built-in usb audio-interface (mackie, behringer) - BUT THEY ARE NOT MULTI-CHANNEL RECORDING INTERFACES.

Anyway subscribe to ffado's user list and ask there for additional help - the guys are very supportevly!

Best wishes,
Michael

---

### Post by roaldz on 2008-10-11
I´d go for the presonus fp10 (firepod), it has good preamps on 8 mic inputs (XLR), and 2 line-in´s (Jackplug) (it´s a 10 in/10 out interface). Some people have it running on FFADO, so it is possible:) Otherwise it is possible to use it with FreeBob.

**Please** read this: [http://www.ardour.org/linux_system_requirements](http://www.ardour.org/linux_system_requirements)

Snippet from that page:
> Audio interface

For high-end use, the RME Hammerfall series and the M-Audio Delta series are both recommended choices. These devices are well-supported under Linux, have excellent hardware designs, and work well in more or less every respect.

For cheaper hardware, any of the cards based on the ICE1712 or ICE1724 chipsets will work well (Terratec and M-Audio use these, as well as the EZ8), and the Ensoniq cards and onboard chipsets also are well supported and fairly reliable. On laptops, you may run into cheap builtin audio interfaces that have a single fixed sample rate. This is a poor situation to be in for pro-audio work: resampling is rarely computationally cheap, and always causes compromises with quality.

See the page on audio hardware support for more information on support of particular devices.
Things Not To Do

    * Do not plan to gang together cheap stereo soundcards to make a multichannel system: this will not work.
    * Do not plan to use USB audio interfaces if low latency is important to you 

So I´d not recommend USB, it is better to use firewire for mobile recording, or PCI.

In a few days i´m going to buy the Presonus FP10, because i know it will work.

---

### Post by robeast on 2008-10-11
I also recommend the FirePod or FP10. The FP10 is the new version and works just as well as the FirePod. I don't know what kind of advances they made with it. You could probably find a used FirePod for a steal. I got mine a little over a year ago for about $400. Great cost to ability ratio on this thing. Do you have microphones?

---

### Post by roaldz on 2008-10-12
> **robeast said:**
> I also recommend the FirePod or FP10. The FP10 is the new version and works just as well as the FirePod. I don't know what kind of advances they made with it. You could probably find a used FirePod for a steal. I got mine a little over a year ago for about $400. Great cost to ability ratio on this thing. Do you have microphones?

I´m looking to one priced at €275 ($365). A new one costs €400 around here.

---

### Post by Snoo on 2008-10-13
> **babarosa said:**
> 
To my mind the most uncomplicated tool is using one of the modern "analog"-looking mixer consoles with a built-in usb audio-interface (mackie, behringer) - BUT THEY ARE NOT MULTI-CHANNEL RECORDING INTERFACES.


That's a very useful bit of advice.
Thanks all. I think I'm leaning toward the fire pod.

---

### Post by roaldz on 2008-10-14
> **Snoo said:**
> That's a very useful bit of advice.
Thanks all. I think I'm leaning toward the fire pod.

I think that would be a wise choice. Mine is sent to me today, so I should have it tormorrow:) I'll try to let you know how it works with my 8.04 install.
I'm going to record our rehearsal session thursday, that will be the first recording.

---

