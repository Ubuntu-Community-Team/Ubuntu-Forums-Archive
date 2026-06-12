---
title: "New System Build - Design for Ubuntu Studio Audio"
date: 2010-11-26
forum: Ubuntu Studio
---

### Post by jis4joe on 2010-11-26
NOTE: I started this same thread earlier with a dumb title. Sorry. Hopefully this title will draw attention from intended audience. Sorry.
 
I have been playing with Ubuntu for a few months. I've even gotten as far as getting a wireless card working with a little help from our friends on these forums. A few weeks ago I found out about Ubuntu Studio. Since then I've tried fairly unsuccesfully to evaluate/educate myself using a low budget Intel Atom board D510MO with nothing but the onboard audio. I'm quite confused by the reading various threads about the seemingly overlapping functionality of ALSA, PULSE, JACK, GNOME SOUND UIs, and have had a hard time find any thread that does a good job of explaining how these cooperate/compete for resources. No success whatsoever in getting Audacity or Ardor to do anything productive. I'm not certain I ever got the hardware functioning correctly let alone configuring the software to do anything with it.
 
So here I am... captured by the tought of building a system from scrach (within a reasonable budget) to by design work with all the wonderfull audio tools provided by Ubuntu Studio. The foundation of the system will be a DX58SO motherboard with an i7. Everything else is on the table.
 
Simple question: What would you do? Onboard Audio? USB Audio? Firewire Audio? PCI Audio? Manufacturer? Product?

---

### Post by JC Cheloven on 2010-11-26
Hi. A lot of different things in your post.

As for your statement about not being able to do productive work "with nothing but the onboard audio", it suggests that you have other audio devices at hand. If that's the case, telling us which one is it could help us help you.

As for the confusion (indeed it somehow exists) with sound systems. You can thing in ALSA as the basis on which the other things rely. It could be OSS, but it is ALSA. Jack and PulseAudio are "getting on" better lately, but there were conflicts until recent dates. If you're planning serious audio work (multitrack recording/editing and such) you'll need JACK, ALSA, and nothing else. Nowadays PULSE will not get in your way either (with rare exceptions), so you can simply let it alone. In some sense, Jack could be regarded as the professional audio sound server, while pulse is more apropriate for a general purpose desktop environment. Not to say that it's worse or better, just different. If you want to look further, the [Ubuntu Community Documentation]("https://help.ubuntu.com/community") is an excellent source of information.

Now, as for what seems to be your main question:
> **jis4joe said:**
> Simple question: What would you do? Onboard Audio? USB Audio? Firewire Audio? PCI Audio? Manufacturer? Product?
You indeed have to be careful, as not every device out there works in linux. 
Also the kind of device suitable for you depends entirely of what you intend to do. 
- If you intend to do multitrack recording, yo ushould consider firewire. Have a look on the [ffado site]("http://www.ffado.org/?q=devicesupport/list") for supported devices. The presonus firepod is a usual reference in these forums. I own a phonic helix board.
- If two inputs are enough for you, and you don't need xlr/phantom for your mics, then a pci card is probably the optimal choice regarding quality/price. Something from Hammerfall uses to be excellent and fully supported (but be aware that the particular model DSP 9632 suffers from a bug in how alsa/pulse communicate: it won't work in the presence of pulse, you would have to completely remove pulse, which is not as easy without messing your ubuntu).
- If 2 inputs are enough 4u, but you need xlr/phantom connections, the optimal choice goes IMO to a usb device. The edirol UA25 is really nice for example. Note: we are mostly limited to run usb audio devices in usb 1.0 mode, so only 2 channels in full duplex can be handled.
To find out if a particular pci or usb device is supported, you should look at the [ALSA pages]("http://www.alsa-project.org/main/index.php/Matrix:Main").

Uff... Please next time try to be more specific. You'll get better chances of getting a useful answer ;)
JC

---

### Post by jis4joe on 2010-11-27
Thank you JC Cheloven.  Your response was exactly what I was looking for.  I don't have other audio devices in hand at the moment... but rather I would like to build a system from ground up to "just work" with Ubuntu Studio.  The only thing I have in hand as a foundation is the motherboard, processor, 250GB HDD, and 4GB of DDR3.

Everything else is 100% flexible with no preconceived favorite interface, manfucturer, or product line.  Even the case has yet to be purchased.  All of this said I will be limiting my search for an audio card to the ALSA and the ffado site and specifically those with FULL SUPPORT or equivalent.  My gut tells me to look first at firewire (top of your list below).  I think this is primarily because I'm not happy about no support for USB 2.0 (faster is always better) and PCI is very limiting these days (typically only one card slot per motherboard if any).  What say you on this?

BTW - Your response was extremely useful and I sincerely appreciate the effort you put into it.  You've probably narrowed my list to three options... 1 from each of the three interface options.  Thank you.

---

### Post by cchhrriiss121212 on 2010-11-27
> PCI is very limiting these days (typically only one card slot per motherboard if any)
I think you might be thinking of something else here, possibly PCIe, as the majority of motherboards will come with 2 PCI slots minimum. 

A Firewire device will have better performance, but a PCI card will be much easier to set up IMO. Plus firewire devices will **only** work through jack, which means regular audio (firefox, mplayer etc.) will not go through it without tinkering.

It would be easier to recommend one if you explain what and how you intend to record. For example: how many inputs/outputs you'd like, whether you need MIDI ports, whether you need built in pre-amps, whether you need digital ins/outs, etc.

And here is how I consider audio on Linux:
hardware > ALSA > jack/pulse > software

---

### Post by jis4joe on 2010-11-27
Thank you cchhrriiss121212.
 
Very helpful insight on Firewire.  In that case, I guess the onboard audio could still provide the "regular" audio... unless I had to remove PULSE to eliminate conflicts.  Hmmmm.
 
I want to multi-track record various instruments.  Not worried about ultra-high-super-duper-best-very expensive quality.  CD quality is fine.  Two channels is plenty.  
I have a UM-1 USB midi interface so don't need this from the audio card.  My signal chain is:
 
Various Instruments > 12 Channel Mixer (Rec Output) > Computer

---

### Post by cchhrriiss121212 on 2010-11-28
I use a [M-Audio Delta 44]("http://www.amazon.com/M-Audio-DELTA-44-Digital-Professional/dp/B00006J075") which would handle what you need. It has 4 ins and 4 outs, all 1/4" jack analogue. It is affordable and gives good sound quality at a low latency, uses hardware mixing and more importantly it is fully supported with Linux.

---

### Post by JC Cheloven on 2010-11-28
As "Double Chris" indicates, PCI should not be disregarded either. It has a wider range of linux compatibile products, and usually better price for equivalent quality. On the other hand, you'll find less flexibility regarding lots of inputs, mic preamps with xlr connection and such.
For example, I use (for different purposes) a Hammerfall pci card, an M-Audio FastTrack & an Edirol UA25 usb external cards, and a 18 input firewire Phonic Helix Board. In terms of quality of sound handling, and d/a conversions, I'd say I prefeer the pci hammerfall! Not endorsing it, only noting that a pci card may be a good option.

> **jis4joe said:**
> 
I want to multi-track record various instruments.  Not worried about (...)  My signal chain is: 
Various Instruments > 12 Channel Mixer (Rec Output) > Computer
Mmm.. I'm affraid human nature is such that you'll want to stream independent channels to the pc after some months :D
Just in case that happens, be prepared for firewire. Texas Instruments firewire pci controllers typically work fine under linux. Mine does, it is (as listed in lspci)
> FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

But for now, I'd say that a decent pci card connected to your current analog mixing board will make you happy. 
Hope so!

---

### Post by jis4joe on 2010-11-30
Last night after lots of reading and Pugh Analysis, a trip to Guitar Center to find that they had none of the options I've been reading about in stock, and searching for Cyber Monday deals on firewire cards I tried an experiment with my existing Intel Atom D510MO and its onboard Intel HDA hardware.  I installed plain old Ubuntu next to Ubuntu Studio and added Audacity.  After a few minutes determining what input was what and unmuting things I got Audacity to record and play/record simultaneously.  I quickly made it up to 5 tracks and was so happy to be playing my guitar again that I just kept playing.  I then realised that I've spent an unreasonable amount of time/effort trying to get Studio to work... just because it is called Studio.

I am enamoured by the idea of an RTOS (low latency response) and will likely pursue dedicated hardware for capturing the sound but I think I'm going to be taking a break from the computer for a while and get back to playing music.  I'd probably have Eugene's Bag of Tricks down by now if I had been studying that instead.

To close the thread out, for those who may be interested, I will share MHO the options are ranked as follows:

1a)  Firewire
Pros:  Great performance (400Mbps) & portable
Cons:  Expensive & takes most effort to configure
1b)  PCI
Pros:  Highest performance (1Gbps) & easiest to configure
Cons:  Zero portability & limits other system options (limited number of slots available)
3)  USB
Pros:  Highly portable
Cons:  I can't conceive of purchasing something that I know is capable of 480Mbps but I will only be able to squeeze 12Mbps out of it.  Off the table.

---

### Post by prokoudine on 2010-12-01
> **jis4joe said:**
> I'm quite confused by the reading various threads about the seemingly overlapping functionality of ALSA, PULSE, JACK, GNOME SOUND UIs, and have had a hard time find any thread that does a good job of explaining how these cooperate/compete for resources.

To get rid of confusion regarding PulseAudio and JACK read [this article]("http://0pointer.de/blog/projects/when-pa-and-when-not.html") written by PA developer

> **jis4joe said:**
> Simple question: What would you do? Onboard Audio? USB Audio? Firewire Audio? PCI Audio? Manufacturer? Product?

There is no simple answer to that.

Onboard audio sucks. You never realize that until you listen how proper audio interfaces sound.

USB audio can work just fine, but in some cases you will get only a fraction of features or it won't work at all.

Firewire audio works only via JACK, not all interfaces are supported, and drivers for some of the supported interfaces need a lot of polishing. Take it from Focusrite Saffire user.

If you want least confusion, go for PCI. M-Audio has nice interfaces from Delta series that are known to work rather well. Or you could get a USB audio, but make a proper research before you buy one. I nearly bought a Fasttrack that turned out to be completely unsupported.

---

### Post by marcoharder on 2010-12-01
Heya,

I actually have a working  d510 system which I use to record demos. Just a few tips from my 2-3 month love affair with this machine.

- Get the latest BIOS Flash update, as I was not able to install 10.04 until I flashed the bios.

- Stay away from Firewire soundcards. Been doing a lot of reading on this and it appears that there is a separate workstream developing stuff for firewire cards [FFADO] and it seems that most manufacturers of these cards aren't very helpful.

Good luck!

MH

---

