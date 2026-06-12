---
title: "Recording Studio Equipment recommendation"
date: 2009-02-03
forum: Ubuntu Studio
---

### Post by rpatros on 2009-02-03
I am trying to build a studio machine for our Choir. I have convinced my Choir conductor to use Ardour as the multitracking recording software instead of purchasing ProTools. Budget wise I am limited to $1000 worth of hardware.

I already have a machine with the following system specs:
P4 2.4ghz
1GB of RAM
Sound Blaster Live

I will add more RAM later but here is where I need your help with your suggestions. 

What soundcard interface would you recommend?

I had in mind M-Audio 1010LT but I read an article that said the M-Audio 1010lt is no longer recongnized by 64Studio/Ubuntu Studio as the card was redesinged in 2007 so that go me paused. The reason I thought of the 1010lt because of it's connection but I believe it lacks phantom power. 

Which card would be recommended in which the following connections are need?

Midi
MIC 
1/4 jacks

Also what studio monitors would you recommend?

Which Microphone would be recommended? 
I saw the M-Audio MXL 990 but it requires phantom power.
I also saw the Shure SM57 Instrument/Vocal Mic (SM57-LC). Not sure if this one requires phantom power

Need you recommendation on the following devices:

Sound card (Recommend PCI, Firewire or USB)?
Recording Mic for Solo
What monitors to use
Mic filter

Your suggestions would be greatly appreciated. 

Rony P.

---

### Post by mikeymo1741 on 2009-02-04
Rony, 

I've read that the Lexicon Omega USB audio interface will work seamlessly with Ardour. It has 1/4 and XLR inputs.  It's an 8 input/4 bus. 

I would definitely use SM-58 mics for individual singers.  They are a workhorse, and pretty much a standard for vocals.  Of course, for a choir, you might be better off with condensors, as they do not require as much sound pressure.  Either something like a CAD GXL2200 or a dedicated choir mic.  Do NOT use a '57 for this application.   

A condensor mic will require phantom power.  (The Omega has it.)  A '58 does not.

---

### Post by rpatros on 2009-02-05
Mikey,

I really appreciate your response and input. I will check the Lexicon Omega USB card.

Will it work with either UbuntuStudio or 64Studio and what version?

---

### Post by drumfire420 on 2009-02-05
If you're looking for something small and easy I've had good luck with the Tascam US-122L (NOT the US-122).  As a general rule for Linux hardware don't get the latest and greatest came-out-yesterday stuff.

Studio monitors are a personal choice thing, it's more important that you know your monitors and the room you're in than what the monitors and room are.  Be sure to not get the cheapest thing being sold and try to get a name brand and you'll be fine.
  Once you get them though, get a disk or two (NOT MP3s) of songs you know that you know that you know and listen to it on several systems you know then many times on your new monitor setup, go back and forth a couple of times.  Take note of what you hear differently.  The important thing here is that you know your monitor system, and can predict how it will sound on other stuff compared to your monitor system.

Mics are really a thing that you have to know what you're getting into.  Are you doing voice overs, pod casts, demo stuff with you on your guitar, full choir ... etc. Mics are to recording as paintbrushes are to a painter.  Get the mic that is useful in the situation you are in.  that being said Shure SM-58 is a standard for vocals that is tough to go wrong with SM-57 for instruments.   If your looking to go a bit nicer than basics and looking to save some money Heil is putting out some really impressive stuff now, for not too expensive.

---

### Post by bolex100 on 2009-02-06
> Mics are really a thing that you have to know what you're getting into. Are you doing voice overs, pod casts, demo stuff with you on your guitar, full choir ... etc. Mics are to recording as paintbrushes are to a painter.

At beginner level mics DON'T matter as much as talent.  People always argue about mics, but there's a lot of good stuff been recorded with Sh*t mics and load more sh*t recorded with Neumans.  SM58s and SM57s actually use the same cartridge. There is very little difference.  Madonna recorded her "ray of light" album with an old, cracked 57.

No-one mentioned preamps.  You can't just plug a mic into a 1010.  it needs line level input.

---

### Post by rpatros on 2009-02-06
bolex100 thank you for the reply. I appreciate your input. I was also looking at the following components and not sure if they would be a good setup for the choir. Now this will be setup at our conductor's house so it would not be done at the church. 

Audio Interface: Lexicon Omega
AKG Perception 120 Condenser Microphone
Musicians Gear Double Pop Filter
M-Audio Studiophile AV 40 Powered Reference Speaker System
Or the SM58 MIC.

What do you think?

---

### Post by ttoine on 2009-02-06
I can share a bit of experience as I use Ubuntu and Ardour 2 to make stereo / ambiance recording of live gigs, work session of rock bands, acoustic gigs, demos, etc... for more than 2 years now. I did the choice of Ubuntu / Ardour because of price and usability, so I can spend more money in hardware.

If you prefer a pci sound card, you can. Good brand and well supported hardware are from Echo Audio and RME. Otherwire, I would suggest Firewire. Forget USB, it is not reliable on Linux (and Win or Mac, too...)

I won several kind of hardware, in order to do the tests for Ubuntu Studio. For that kind of purpose, I would use :
 - a firewire Presonus Firepod (2 line inputs, 2 pre-amp XLR with phantom power, 6 line output, and a headphone output with volume control). It works very well using Qjackctl
 - for the mic, I own a pair or Rhode NT5, and a pair of SE Electronic SE3. both mic are condenser and need phantom power. SE Electric are a bit more expensive,  but they have a more "hot" sound, as we say in french.
 - monitoring is a very hard choice point... The better way to choose is to go at a music hardware shop with 2 or 3 reference audio cd, you are often listening. It will help you a lot : the most important is to hear different pairs with the same musics. My choice is Fostex PM0.5 MKII, and some of my friends are using the PM1 MKII, in order to have a better response in low frequencies. One of the better quality / price on this range of product.
 - then, take some time choosing your cables, it is more important than is appaers ;-)

To use a firewire sound card with jackd, use Qjackctl, in setup windows, you just have to choose "freebob" in the driver choice, instead of "Alsa". then choose your frequency and period, put the period/buffer at 3 (it will not start, else).

I let you the link to the page I maintain about everything about how to setup Ubuntu to make audio production:
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

You will find a lot of info here. To help you choose your hardware in confidence, I suggest you have a look at those website :
 - for pci/usb sound cards: [http://alsa-project.org/main/index.php/Matrix:Main](http://alsa-project.org/main/index.php/Matrix:Main)
- for firewire sound cards: [http://ffado.org/?q=devicesupport%2Flist&filter0=&filter1=&op2=OR&filter2](http://ffado.org/?q=devicesupport%2Flist&filter0=&filter1=&op2=OR&filter2)[]=perfect

Don't hesitate to contact me if you need help to setup your hardware. And if you need more advices on harware choice, of course.

Toine

---

### Post by Graham C Williams on 2009-02-07
Monitoring is probably the most important part of the system. If you cannot hear what you're recording you stand little chance of getting it right! With limited funds you might try getting second hand equipment but make sure it is good stuff.
For this type of work I'd look for BBC Design Monitor style speakers and a good set of cans. Try for second hand:
Harbeth HL5 monitors - A good QUAD 306 amp to drive them.
Cans - You'll never go wrong with SENNHEISER. The HD580 or whatever the latest version is!

Mics and mic amps.
Keep your eyes open you can get some very good mics at reasonable prices. From most expensive to less so:
NEUMANN U87Ai - be sure it's the Ai
NEUMANN TLM 170 - An overlooked great mic
AKG C414 - You can get these in a number of flavors now, they all very good but can be a bit toppy. Don't be afraid to try some older versions of this mike.

(A U87 (as M) and a TLM170 (as the S) make a great MS Stereo pair - the sound will blow your socks off!)

CAD M179 - I was surprised by these. Yes, not as clean as the expensive stuff above but good mics.

If you have a large Choir you may be better with a spaced Omni array. 2 omni mics 2 to 3 feet apart and use the SM58s as spot mics. For this again I'd suggest some of the better Omni mics- Look at: Earthworks, B&K (DK), Schoeps etc.for the better sounding stuff.

Mic amps. Well if you can get one second hand at a good price the:
Earthworks 1022 mic amp is one of the best I've heard. 
Oh well that's probably a dream. To be frank most modern mic amps are quite good provided you watch your headroom and understand that some vocal transients can be 20dB or more above the average level!

Hope this helps.
Graham.

---

### Post by jonathonblake on 2009-02-07
> **Graham C Williams said:**
> try getting second hand equipment but make sure it is good stuff.

How can I tell if something is good, or not? (This appliestoboth new,and used equipment.)

I know _nothing_ about studio recording, but have to set up an AV Studio from scratch.

jonathon

---

### Post by ttoine on 2009-02-08
Graham... the aim of the topic was to build a complete recording setup ofr less than 1000 $... I don't think it will be possible with your harware list...

---

