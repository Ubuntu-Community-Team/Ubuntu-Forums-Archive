---
title: "Calling out audio enthusiasts: HTPC soundcard hunt"
date: 2010-07-26
forum: The Cafe
---

### Post by blueturtl on 2010-07-26
I have been spamming the forums yet and again with audio related threads. This time I need to find a high quality sound card that works with Ubuntu but also meets the following requirements:

* Must be low-profile (to fit inside the small HTPC enclosure).
* Must be PCI-express (as no free PCI slots remain).
* Stereo analog outputs are preferable but with amp friendly RCA jacks

A quick Google search brought up the [ASUS Xonar Essence STX]("http://www.elitebastards.com/index.php?option=com_content&task=view&id=696&Itemid=27&limitstart=2").

Is there something like the Xonar Essence that would be low-profile and Linux friendly on the market?

---

### Post by Lucradia on 2010-07-26
What kind of PCIe slot?

[http://en.wikipedia.org/wiki/PCI_Express#Physical_layer](http://en.wikipedia.org/wiki/PCI_Express#Physical_layer)

---

### Post by blueturtl on 2010-07-26
Looks to me based on the link you provided that this is a PCIe x1 type slot.

---

### Post by CharlesA on 2010-07-26
Most sound cards/NICs work in x1 slots, but they can be placed in x4, x8 and x16 slots if you don't have a skirt on them.

@OP: Not a clue as to what would be a good card, as I've only been using HDMI out for that.

---

### Post by Frogs Hair on 2010-07-26
Here's one to check out . [http://www.hardwarecanucks.com/forum/hardware-canucks-reviews/5599-asus-xonar-dx-7-1-pci-e-sound-card-review.html](http://www.hardwarecanucks.com/forum/hardware-canucks-reviews/5599-asus-xonar-dx-7-1-pci-e-sound-card-review.html)

---

### Post by blueturtl on 2010-07-26
> **CharlesA said:**
> Most sound cards/NICs work in x1 slots, but they can be placed in x4, x8 and x16 slots if you don't have a skirt on them.

@OP: Not a clue as to what would be a good card, as I've only been using HDMI out for that.

I figured as much.

HDMI output is not an option for me though because my amp is an old stereo model. No digital processing of any kind so it needs to be fed with analog signal.

> 
Here's one to check out . [http://www.hardwarecanucks.com/forum...rd-review.html](http://www.hardwarecanucks.com/forum...rd-review.html)  

Thank you for the heads up ... Frogs Hair. Is this a Linux compatible card? They never have that penguin logo on the box...

---

### Post by blueturtl on 2010-07-26
Ok... found the following quote on Newegg:

> Pros: Linux Xonar driver supported through the linux Kernel. This is why I wanted the ASUS Xonar, for Linux support. I'm using Kubuntu 910 x64, and it works!

So it looks like a supported card. The only thing that bugs me is that I will have to use a converter to plug in to the amp (amp uses bigger RCA inputs) but other than that looks like a really good deal.

I wonder if using a converter will affect the sound though... :-k

---

### Post by Frogs Hair on 2010-07-26
I used a converter from Radio Shack to record with Cake Walk on my old pc without any problem , just be careful no to tug on the cord once connected .

---

### Post by blueturtl on 2010-07-27
Marking thread as solved as I basically got my answer. If alternatives to the Xonar DX exist, I would like to know but so far this card is the only one that has turned up that meets the necessary requirements.

---

### Post by blueturtl on 2010-08-23
Review to follow:

**Initial impressions**

I received the card today. I was slightly anxious to see if it would really be better than the integrated audio in my Scaleo E HTPC. After all the Scaleo was built for living room use and has real RCA outputs. The sound was never particularly bad. The Xonar DX on the other hand has 3.5mm mini outputs (clearly intended for use with computer equipment, not livingroom AV stuff).

**Installation**

I had to fiddle a bit because it requires a separate AUX power connector directly from the PSU (and the cable included was too short to reach the PSU in the Scaleo). After a bit of scissors and tape (sounds bad I know) I managed to hook up the card from the same line that feeds my custom GPU fan. A little unsure of myself I booted the computer.

Nothing blew up and soon I was greeted by Ubuntu (HTPC still runs 9.10). The sound card worked out of the box! I only had to mod the /etc/modprobe.d/alsa-base.conf to include the line

#options snd-hda-intel index=-2

so that the integrated card wouldn't be the primary card any more. After that I had to play some tunes...

**Listening tests**

All I can say is: WOW. I know the Xonar DX is the budget model in the series. I also thought the 3.5mm plug-to-RCA thin cable would not provide a very good starting point for audio but dang. The sound is so much more clear than the Scaleo integrated audio it's like I had my ears rinsed. For one thing despite the flimsy plugs and thin cable the card is much louder than the integrated audio. More importantly it actually sounds good. The soundscape is well balanced, the instruments clearly separated. I can easily pick up more details out of my music. Even with the crummy MP3 files my collection mostly consists of. Subjectively I can't tell if the card is biased any way. It's not too bass heavy for my taste at least.
If someone is wondering about stuff like this, the Xonar DX makes a very living room friendly card. It looks finicky but has a really good analog output, even to be fed directly to an amp.

I use Pioneer A-504R with the Cerwin-Vega! CD-20 full range speakers.

---

### Post by cascade9 on 2010-08-23
> **blueturtl said:**
> Marking thread as solved as I basically got my answer. If alternatives to the Xonar DX exist, I would like to know but so far this card is the only one that has turned up that meets the necessary requirements.

Too late now, but there is one other option I know of- Auzentech X-Fi Forte 7.1- 

[http://www.auzentech.com/site/products/x-fi_forte.php](http://www.auzentech.com/site/products/x-fi_forte.php)

Its just creative X-Fi chipset on a low profile card. From what I've seen, the Asus Xonar DX is a better card, and you arent paying any money to creative, which is a bonus ;)

---

### Post by blueturtl on 2010-08-23
> **cascade9 said:**
> Too late now, but there is one other option I know of- Auzentech X-Fi Forte 7.1- 

[http://www.auzentech.com/site/products/x-fi_forte.php](http://www.auzentech.com/site/products/x-fi_forte.php)

Its just creative X-Fi chipset on a low profile card. From what I've seen, the Asus Xonar DX is a better card, and you arent paying any money to creative, which is a bonus ;)

Yeah. I discarded the Forte as soon as I learned it was Creative X-Fi. Last Creative card I used was the Audigy2. Thought it was a good card until I tried M-Audio. Creative software for Windows was always crap, so the only "advantage" Creative has had in my book for a long time has been the SoundBlaster brand name. They have never really been leaders in sound quality which is pretty much the only criterion you have left when using Linux.

The Xonar DX is a budget card so if they ever make a really high end card like the D2X or STX that fits a low-profile slot, I'll be interested. Till then, the DX is my new favorite, that is in the HTPC at least.

---

### Post by cascade9 on 2010-08-24
> **blueturtl said:**
> Yeah. I discarded the Forte as soon as I learned it was Creative X-Fi. Last Creative card I used was the Audigy2. Thought it was a good card until I tried M-Audio. Creative software for Windows was always crap, so the only "advantage" Creative has had in my book for a long time has been the SoundBlaster brand name. They have never really been leaders in sound quality which is pretty much the only criterion you have left when using Linux.


Creative has, IMO, been 'resting on its laurels' since they combined with ensonic (mainly because ensonic had actually made a working ISA emulation for its PCI sound cards, which creative hadnt been able to do then). 

I've been looking at the asus sound cards since I heard one at a friends place, very good sound quality. My old favourite is long gone now (chiantech AV-710) and while the asus cards are nowhere near as well priced as the chaintech was, better asus than creative. I just wish I hadnt sold my last AV-710, but I was told that they were still avaible by the suppliers.....when I went to order one the next day, all gone :(

---

### Post by Rahbee Kannuhn on 2010-08-24
Get a good early 70's Marantz amp, pump any decent onboard sound through it, nirvana ensues, short of just pushing a solid LP on an excellent turn table, but I'm assuming were just pushing out mp3's or something similar from a computer.

---

### Post by handy on 2010-08-24
> **cascade9 said:**
> Creative has, IMO, been 'resting on its laurels' since they combined with ensonic (mainly because ensonic had actually made a working ISA emulation for its PCI sound cards, which creative hadnt been able to do then).  ...

I remember being amazed way back when Creative bought E-MU.

There was a time when every keyboard player worth his salt had at least one E-MU Proteus rack mounted sound module, as they set the professional standard for sound samples for quite some time.

---

### Post by blueturtl on 2010-08-24
I can't say I like hating Creative.

I remember when I bought my first separate audio card: the SoundBlaster Live! I read all the hype about EMU10k and the hardware audio effects it could do (EAX) and was in fact a fairly happy owner. After all that promise it was a sad to find out that eventually, the only game I could run with the promised effects was Half-Life. All the other EAX games either exhibited weird bugs or crashed all together. Later on when I developed a more serious taste in high quality sound I discovered all the weird stuff their hardware was doing (resampling the signal back and forth!) that degraded output quality. After some research I bought the M-Audio Revolution 5.1 and have since then consistently only contributed towards Linux friendly HQ solutions.

---

### Post by cascade9 on 2010-08-24
> **Rahbee Kannuhn said:**
> Get a good early 70's Marantz amp, pump any decent onboard sound through it, nirvana ensues, short of just pushing a solid LP on an excellent turn table, but I'm assuming were just pushing out mp3's or something similar from a computer.

Spend a bit more for a decent sound card and it just gets better. Onboard sound, while better now than ever before, has nothing on a good sound card. 

> **handy said:**
> I remember being amazed way back when Creative bought E-MU.
 
 There was a time when every keyboard player worth his salt had at least one E-MU Proteus rack mounted sound module, as they set the professional standard for sound samples for quite some time.
 
 That makes 2 of us. I remember having to explain why I was suprised at the time to a lot of gamers who knew nothing about samplers...or music at all in some cases. 
 
> **blueturtl said:**
> I can't say I like hating Creative.

I've flipped back and forth between hating creative and massive confusion. How can a company that did so well go so bad? 

I've settled down into the same sort of relationship I have with microsoft. Hating is a waste of time and energy, I dont want to give them my money, and think there are better options around.  

I think I've run every soundblaster they made at some point, using them not only as sound cards but also as a CD drive interface. The earlier cards I've got a lot of good memories from, I've still got an AWE64 gold I just cant bear to part with, even though I dont own a single computer with the ISA slot needed anymore. 

BTW, I'm still using a SB Live in my media box. Its better than the onboard AC97......

---

### Post by bcschmerker on 2011-09-25
The Xonar DX is in fact the winner for your requirements; standard 3.5mm-to-dual-RCA "insert" cables are sufficient to adapt the card to external audio equipment.  Be advised that the Xonar D*n* series is occasionally undetected in Windows boxes due to a design flaw that can result in an on-board firmware EEPROM being overwritten under heavy code traffic (a non-issue with the snd-oxygen module in Kernels 2.6.34-up); this flaw is not present in full-height PCI and PCI-Express x1 audio cards from ASUSTeK.

I have been researching upgrade audio cards for two systems; on the LinUX side, I had to rule out the [Auzentech® X-Fi® Forte™ 7.1]("http://www.auzentech.com/") (Creative Laboratories® CA20K2 chipset), which would otherwise fit your requirements, as Creative Technology, Ltd., has been uncooperative with the [Advanced LinUX Sound Architecture Project]("http://www.alsa-project.org/") concerning driver support for the CA20K1 and CA20K2 chipsets (proposed driver: emu20k1).

---

### Post by thatguruguy on 2011-09-25
This thread is over a year old.  Do you think he's still trying to make up his mind?

---

### Post by sffvba[e0rt on 2011-09-26
> **thatguruguy said:**
> This thread is over a year old.  Do you think he's still trying to make up his mind?

I think you have a good point there...


***Thread closed***



404

---

