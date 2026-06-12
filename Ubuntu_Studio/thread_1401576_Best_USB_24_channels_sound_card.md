---
title: "Best USB 2/4 channels sound card"
date: 2010-02-08
forum: Ubuntu Studio
---

### Post by Tarrasque on 2010-02-08
Hello.

I'm coming back to Ubuntu Studio after some time, and I'd like some help catching up with the supported technology.

What I want is basically use my laptop as a mobile light studio for:

 - recording into ardour (mainly guitar)
 - use the laptop as a guitar effect rack
 - occasionally, play VST instruments with a connected USB keyboard (already have a M-Audio which works flawlessly)

Since my requests are fairly basic, I think I can go with a 2 or maybe 4 in/out channel external soundcard. Since my pc does not have firewire, I'm stuck with USB 2.0

What is the cheapest card I can get that suits my needs, and has perfect out of the box compatibility with Ubuntu Studio?

Thank you all very much for reading.

---

### Post by AutoStatic on 2010-02-08
Hello Tarrasque,

[Edirol UA-25EX]("http://www.roland.com/products/en/UA-25EX/")

It's not the cheapest card though.

---

### Post by Tarrasque on 2010-02-09
Seems fine. Not too overboard in regards of price.

One more question: the other Edirol model I see on the products page is a 10 in/10 out, which is DEFINITELY too many (and too expensive).

Is there an out of the box 4 in / 4 out card, even from another vendor, around?

Thank you very much.

---

### Post by LinuxUser9 on 2010-02-09
Here is some food for thought for now and I'll get into the research as to compatibility and get back to you. Without a maximum price range, we'll just throw you some decent choices here and go from there. The Roland (Edirol) is a relatively inexpensive compared to MOTU (Mark of The Unicorn) products that you could spend thousands on. 

If your laptop has a card slot, you can check out the SB Audigy2 ZS Notebook sound card.

[http://www.soundblaster.com/products/product.asp?category=1&subcategory=205&product=10769](http://www.soundblaster.com/products/product.asp?category=1&subcategory=205&product=10769)

It's priced at around $350.00, but it has Dolby Digital EX, DTS-ES 6.1 decoding, 7.1-channel output. 24-bit/192KHz output for two-channel DVD-Audio. AutoStatic's excellent suggestion rolls in at around $250.00.


The Creative Professional E-MU 0202 USB 2.0 Sound card - 192 kHz &#8211; 24-bit (same company, E-MU is their pro division) is less than a hundred bucks.

[http://www.emu.com/products/product.asp?category=610&subcategory=611&product=15186](http://www.emu.com/products/product.asp?category=610&subcategory=611&product=15186)

 

StarTech.com has a USB 2.0 to stereo sound card audio adapter for less than twenty bucks.

[http://www.startech.com/item/ICUSBAUDIO-USB-20-to-Audio-Adapter.aspx](http://www.startech.com/item/ICUSBAUDIO-USB-20-to-Audio-Adapter.aspx)


I hope this helps for now...

---

### Post by AutoStatic on 2010-02-09
I would stay away from Creative products.
And the StarTech device will work but but it is no way comparable with all the other devices mentioned.

---

### Post by AutoStatic on 2010-02-09
> **Tarrasque said:**
> Seems fine. Not too overboard in regards of price.And it works out of the box, has decent pre-amps and is a sturdy device. I have its predecessor, the UA-25, and it has never let me down.

> **Tarrasque said:**
> Is there an out of the box 4 in / 4 out card, even from another vendor, around?USB1 is not suited for 4 IO's as far as I know (too little bandwidth), don't know about USB2. The problem with USB2 audio cards though is that they don't respect any standard so there are very few USB2 soundcards that will work with Linux.

---

### Post by LinuxUser9 on 2010-02-09
AutoStatic,

Once again I agree, but his first point was price and we haven't heard if he has a card slot yet. If so, I'd go with a Firewire interface over USB. What do you think of the Focusrite Saffire Pro 24 DSP and a FW PC Card (if he has one)?
[http://www.focusrite.com/products/audio_interfaces/saffire_pro_24_dsp](http://www.focusrite.com/products/audio_interfaces/saffire_pro_24_dsp)

Another option is M-Audio's Fast Track Pro (4 x 4). The Fast Track Ultra is USB 2, But he doesn't need 8x8. I thought your UA-25 runs on Mac OS9, so I would imagine it would be USB1. The EX should serve him well and he said it wasn't a bad price.

---

### Post by raboofje on 2010-02-09
> **LinuxUser9 said:**
> I thought your UA-25 runs on Mac OS9, so I would imagine it would be USB1.

Correct - same for the UA-25EX. That means no full duplex in 96khz mode - a limitation I can live with easily.

---

### Post by Tarrasque on 2010-02-09
Thank you for the answers so far!!

Unfortunately my laptop currently has: no firewire - no cards, so USB is the only option.

I wasn't very clear on the price range, I admit. What I want to achieve is a decent portable recording studio. I intend to play real instruments into the laptop, and maybe use it as a sound module on stage.

So I recognize that low level cards are not suited. At least the cards should have jack / cannon inputs and outputs. So while I'd like to stay as low as possible, I don't reasonally expect to be under the 100$ mark. :)

A 4 in / 4 out would be nice, because I would be able to use the pc for stereo sample playing and guitar sound shaping simultaneously on separate channels (let's say a guitar multieffect and a keyboard music module in the same box).

I don't know if this is possible due to the USB limitations I'm reading now...

---

### Post by hardcopy on 2010-02-09
a little while back i emailed focusrite about their saffire 6 usb audio interface (i too have a laptop i'd like to use for linux audio), they were quite helpful in giving me the info i wanted- the saffire 6 usb is fully usb 1.1 compliant so in theory it will work on linux(?)... im still deciding whether to just go for it and try it out

also they showed an interest in helping the linux community write drivers for the saffire usb, i forwarded the info to the main alsa dev, not sure if anything will come of that, or even if i sent the right person an email

---

### Post by AutoStatic on 2010-02-09
> **LinuxUser9 said:**
> Another option is M-Audio's Fast Track Pro (4 x 4). The Fast Track Ultra is USB 2...Aren't those two cards still cumbersome to get going?
Fast Track Pro: [http://www.joegiampaoli.com/blog/?p=462](http://www.joegiampaoli.com/blog/?p=462) (low and behold, 109 comments ;) )
And the Fast Track Ultra: [http://ubuntuforums.org/showthread.php?t=1350362](http://ubuntuforums.org/showthread.php?t=1350362)

So if you buy those cards you have to either compile your own kernel or wait until they get integrated into the Ubuntu kernel/ALSA driverstack.

---

### Post by AutoStatic on 2010-02-09
> **hardcopy said:**
> ...the saffire 6 usb is fully usb 1.1 compliant so in theory it will work on linux(?)...Yes it will, it complies to [this standard]("http://www.usb.org/developers/devclass_docs/audio10.pdf") and there's a generic Linux driver available which comes standard with Ubuntu: [http://www.alsa-project.org/main/index.php/Matrix:Module-usb-audio](http://www.alsa-project.org/main/index.php/Matrix:Module-usb-audio)

---

### Post by LinuxUser9 on 2010-02-09
raboofje - I thought I saw USB2 for UA-25EX, but I find nothing on a second glance... Thanks.
-----------------------
hardcopy &#8211; I don't know about Tarrasque, but for me... I wish I was that capable with Linux.
-----------------------
AutoStatic &#8211; I'm just throwing out gear. Tarrasque's laptop is not listed/shown here. If the Fast Track Ultra (being USB2, and if his laptop is 2.0) is of interest to Tarrasque, he might be able to have the Linux tasks done for him. And: Provided the tasks at hand will work at 1.1 levels (how many connections to the interface/latency). PreSonus has a decent FW interface that does him no good as well.
---------------------------------------------------------

How about a USB2 mixer???

---

### Post by LinuxUser9 on 2010-03-16
[Tarrasque]("http://ubuntuforums.org/member.php?u=15461"),  Have you made a purchase yet? Which route did you wind up taking and how is it working out?

---

### Post by Capoeira on 2010-03-16
I have an older one, the M-Audio Duo
[http://www.zzounds.com/item--MDODUO](http://www.zzounds.com/item--MDODUO)
it has nice pre-amps and works verry fine for me on linux.
that one, one can get verry cheap

---

### Post by jsedwards on 2010-03-17
I bought a Fast Track Ultra last year, but I have just tried to use it for the first time in the last few days.  I should have done more checking before purchasing it, from the several threads I've read it looks like it is a real pain to get working.  I could probably recompile the driver and all that junk, but I really don't have time to fool around with that stuff.

So I am thinking of selling it and just buying a decent 2 or 4 channel PCI audio card.  I was thinking something in the $200 to $300 range.  It might be handy to have MIDI at some point but not essential.  It would be nice if it could do 192 KHz, but I could live with 96 KHz.  Is there anything like that, which would be more or less plug and play on GNU/Linux?

Or would it be better to just go with that E-MU USB device mentioned earlier in this thread?

Thanks for any advice
  -Scott

---

### Post by arnoutvos on 2010-03-29
a site with compatible hardware
[http://www.linuxstudiopro.com/](http://www.linuxstudiopro.com/)

---

### Post by arnoutvos on 2010-03-30
i just bought the Roland Cakewalk (formerly Edirol) UA-25 EX for 200 euro. 

the device was immediately recognised by my ubuntu 9.10 and i selected the device in my sound preferences. i don't know if it's necessary to change settings in Ardour (in setup i changed interface to "USB audio". i haven't fully tested the device but the 2 inputs both work.

my point is: after 2 minutes i was already recording in 48 kHz without having to open the terminal or do strange things.

---

### Post by MIJ-VI on 2010-04-08
> **arnoutvos said:**
> i just bought the Roland Cakewalk (formerly Edirol) UA-25 EX for 200 euro. 

the device was immediately recognised by my ubuntu 9.10 and i selected the device in my sound preferences. i don't know if it's necessary to change settings in Ardour (in setup i changed interface to "USB audio". i haven't fully tested the device but the 2 inputs both work.

my point is: after 2 minutes i was already recording in 48 kHz without having to open the terminal or do strange things.

  And, since the OP mentioned live use as part of his audio interface needs, the [UA-25EX]("http://www.rolandus.com/products/productdetails.php?ProductId=970") has a ground lift switch.

---

### Post by maghoxfr on 2010-05-08
Is anyone sure that the focusrite saffire 6 usb would work in Lucid? Because I haven't found anything certain, I would really like to get that card.

---

### Post by JC Cheloven on 2010-05-08
Sorry, but as I see over here
[http://www.focusrite.com/products/saffire/saffire_6_usb](http://www.focusrite.com/products/saffire/saffire_6_usb)
the focusrite 6 is 2 input. I'm quite unsure if that will fit the stated needs of any of the above posters.

But if someone considers as an option a 48kHz/24bit usb interface with 2 inputs (one XLR phantom mic input and one trs instrument input), I'd consider the m-audio fast track (not pro!). [This one]("http://la.m-audio.com/products/es_la/FastTrack.html"). It works flawlessly (as the more expensive and featured -but 2 ins anyyway-  edirol ua25 does). 

THat is in the usb 1.0 realm anyway.

---

### Post by maghoxfr on 2010-05-22
> But if someone considers as an option a 48kHz/24bit usb interface with 2 inputs (one XLR phantom mic input and one trs instrument input), I'd consider the m-audio fast track (not pro!). This one. It works flawlessly (as the more expensive and featured -but 2 ins anyyway- edirol ua25 does). 

How do you know it works flawlessly, do you have it? I'm just asking because I don't see it [here]("http://www.linuxstudiopro.com/#"). I really need an interface and that m-audio seems to fit my needs, I was kind of after the saffire 6 but I just want a "plug and play" one, no problems and the less I use the terminal the better because I'm not a programmer. I would be recording myself playing guitar, bass or doing some voices, recording nylon string guitar with condenser.

---

### Post by cub on 2010-05-24
Edirol UA-25EX seems to be a great way to go, but I have to issue a warning as it will not work well with a Sony Vaio VPC-EB1S1E (16 bit, 44.1kHz only).

---

### Post by maghoxfr on 2010-05-24
ok thanks, It seems to be a great interface indeed, sadly here it's price is quite high, U$S 400!!! I'd love to get it but I also have to buy a condenser studio mic and my budget won't suffice. Thank you

---

### Post by JC Cheloven on 2010-05-24
> **maghoxfr said:**
> How do you know it works flawlessly, do you have it? I'm just asking because I don't see it [here]("http://www.linuxstudiopro.com/#"). 

Yes, I've got it. I use it with a dell mini9 netbook and a behringher condenser mic to do recordings on the go (usually to record individual parts from some musicians at his home). I also bought (and extensively tested) an UA25 for a friend. 
Although "your mileage may vary", you may find this of interest:
[http://ubuntuforums.org/showthread.php?t=1324473](http://ubuntuforums.org/showthread.php?t=1324473)

EDIT: BTW, see [this]("http://www.thomann.de/es/cakewalk_ua_25_ex_cw.htm") for the UA25. Not 400&#8364; !

Saludos desde España :)

---

### Post by maghoxfr on 2010-05-24
Hola! Gracias por el link y también por contarme tu experiencia con la tarjeta, ahora estoy en un "período de investigación" porque hace un tiempito que ando por comprarme una interfase y no me quiero equivocar, entre otras cosas porque mi presupuesto es muy limitado. Sé que el precio de la Edirol (ahora Cakewalk) es alto pero vivo en Uruguay y las cosas importadas son caras, las compres acá o las compres por internet te terminan saliendo lo mismo. Además nunca compré nada tan caro por internet (sólo algún libro). Te hago una preguntita más, recomendarías la fast track sobre la alesis multimix 4 usb? Yo tengo un oxygen 61 (blue) de m-audio y estoy más que conforme con esa marca. La saffire 6 usb era mi tarjeta soñada pero no funciona en  linux...Gracias y saludos!

---

### Post by adrjork on 2010-05-25
Hi Guys, a rapid question: I'd like to buy a cheep netbook (I'd like Asus 1201pn) to use with a cheep USB audio card to manage 4 mic-ins and 4 mic-outs.
Which 4*4xlr/trs-combo USB card could be compatible with ubuntu-studio (and ALSA)?
Thanks

---

### Post by jangal on 2010-05-25
hey!
i too am in the market for an audio interface 4/4 for under $300 and have been researching extensively. my biggest issue it that almost all of them come bundled with unecessary software.
 
my shortlist is as follows:
 
1. Stanton Final Scratch FireWire Audio Interface @ $99 
though this has final scratch in the name it doesn't come with any software and connects via firewire only :( 
 
2. Native Instruments AUDIO KONTROL 1 USB 2.0 Audio/MIDI Interface @249
this one is pretty well known with a slew of trakktor software
 
3. M-Audio FastTrack Ultra USB 2.0 Audio Interface @ $350
is pretty solid, though it needs to be plugged in for power to use all channels, also all the ins are xlr
 
 
as you can see from the above my goal is to use mixx and use a midi everynow and then. the main thing is figuring out your goals for which i found a site to be useful on a pure musical/quality level - no gnu/linux info here. but useful nonetheless
 
[http://tweakheadz.com/index.html](http://tweakheadz.com/index.html) 
 
if anyone has useful info on my comments (contradictions) please let me know - jangal

---

### Post by maghoxfr on 2010-05-25
> 3. M-Audio FastTrack Ultra USB 2.0 Audio Interface @ $350
is pretty solid, though it needs to be plugged in for power to use all channels, also all the ins are xlr

Not all of them are XLR, it has two combo XLR/TRS, [check it out]("http://www.m-audio.com/products/en_us/FastTrackUltra.html").

besides it has midi in, check [this picture]("http://www.m-audio.com/images/global/media_hqpics/FastTrack%20Ultra%20-back.jpg")

I think I'm buying the Fast Track (the smallest one) next week. My budget is small but my dreams are big LOL. I don't know much about dj software so I can't give you much help but I've been reading a lot about audio and interfaces, If you have a question and I could help I'll gladly do so.

Good luck

---

### Post by JC Cheloven on 2010-05-25
> **maghoxfr said:**
> (...)Te hago una preguntita más, recomendarías la fast track sobre la alesis multimix 4 usb? (...)
I'm affraid I haven't any experience with that card. It's not listed in alsa, which I guess is bad:
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Alesis](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Alesis)

@adrjork, jangal, and anyone thinking in 4 in/out:
Please notice that usb 1.0 has just enough bandwidth for managing 2 mono channels at decent resolution. All above this needs usb 2.0, which unfortunately lacks a standard. Thus it's quite uncertain whether a given usb 2.0 device will work or not in linux. Some are reported to work, be it partially, though (this one comes to mind [http://www.roland.com/products/en/M-16DX/index.html](http://www.roland.com/products/en/M-16DX/index.html)).
Greetings
JC

---

### Post by adrjork on 2010-05-26
> Please notice that usb 1.0 has just enough bandwidth for managing 2 mono channels at decent resolution. All above this needs usb 2.0, which unfortunately lacks a standard. Thus it's quite uncertain whether a given usb 2.0 device will work or not in linux.

And what about firewire? Does Linux work better with firewire-cards?

---

### Post by uOpt on 2010-05-26
I use a Tascam US-122 (the old model with real knobs). Good audio quality, local input clipping LED, microphone preamp, XLR input (I think symmetric).

It's a hassle to load the firmware in Linux but once done it does the job.

Also has MIDI so you don't have to fiddle with the internal plugs on what you probably have for an internal soundcard to get one.

---

### Post by adrjork on 2010-05-26
I've found a forum where a guy says that Edirol UA-101 and UA-1000 work on Linux through USB-2.0 because there are the specific drivers.
[http://ardour.org/node/3517](http://ardour.org/node/3517)
These two cards could be good for multitrack purposes!

---

### Post by kamlapati on 2010-05-26
Linux works great with Firewire cards, just check the ffado site for which interfaces have complete support.

FYI, I am using a Focusrite Saffire Pro 26 i/o with both my desktop and laptop, and all it is completely functional.

---

### Post by dumdidum on 2010-05-26
> **jangal said:**
> hey!
i too am in the market for an audio interface 4/4 for under $300
 
my shortlist is as follows:
 
2. Native Instruments AUDIO KONTROL 1 USB 2.0 Audio/MIDI Interface @249
this one is pretty well known with a slew of trakktor software


don't recommend. i've got nothing but problems with NI products on Lucid. edit: sry, i use ubuntu, not ubuntu studio; somehow got to this thread without noticing

---

### Post by jangal on 2010-05-27
maghoxfr, jc cheloven, dumdidum - thanks for the tips. will be making sure wherever i buy from has an easy return policy. i ended up buying the stanton scratch interface for $100, according to ffado site it was reported to work. so we'll soon find out...jangal

---

### Post by maghoxfr on 2010-05-27
Good luck!!! Please write back to tell us how is it working. It sure seems to be a good interfase, it's design specifically for djing so it should suit you need perfectly.

---

### Post by JC Cheloven on 2010-05-27
@adrjork: sure, firewire is THE way, according to many experts (not usb)

> **jangal said:**
> maghoxfr, jc cheloven, dumdidum - thanks for the tips. will be making sure wherever i buy from has an easy return policy. i ended up buying the stanton scratch interface for $100, according to ffado site it was reported to work. so we'll soon find out...jangal

Actually, I just ordered this evening this [firewire device]("http://www.thomann.de/es/phonic_phhb18fw_helix_board.htm"). It's to substitute a tascam fw1804 I sold out coz didn't ran on linux.
Lest's hope the best :-)

---

### Post by uOpt on 2010-05-28
Any recommendations for a firewire audio interface that has S/PDIF in (in, not out)?

---

### Post by jangal on 2010-05-28
jc - the mixing board looks pretty sick. worst case you have to make a trip to the post office... uOPT - i beleive the motu ultralite mk3 has S/PDIF in and out. it can also work with both firewire or usb2.0. on ffado it has been reported to work - to what level isn't mentioned.p.s the stanton is due to arrive today so i should have a report by the weekend.

---

### Post by JC Cheloven on 2010-05-28
> **jangal said:**
> jc - the mixing board looks pretty sick.
Emmm... Why? 
The specs seem fine, and I expect it to work under linux.

---

### Post by jangal on 2010-05-28
jc - so sorry, its the ocean between us. i meant it looks awesome. bad = good; sick = awesome.

---

### Post by maghoxfr on 2010-05-29
it looks awesome indeed, go back in time only 10 years and this was just a luxurious dream. Congratulations, enjoy it! Please post your thoughts on it and if it works properly in ubuntu.

---

### Post by JC Cheloven on 2010-05-30
> **jangal said:**
> jc - so sorry, its the ocean between us. i meant it looks awesome. bad = good; sick = awesome.
LOL, I have to take some modern-u.s.-english lessons. Sorry, I understood the opposite :)

> it looks awesome indeed, go back in time only 10 years and this was just a luxurious dream. Congratulations, enjoy it! Please post your thoughts on it and if it works properly in ubuntu.

Will do! I expect it to arrive by june 3. I should have something to report by june 10 or so.

---

### Post by tHeNeXuS on 2010-05-31
You might also want to check out the Lexicon Lambda/Omega.
I own a Lambda and I works really well since a few kernel releases.
The only real limit is that you only get stereo input at 44/48 kHz (some other USB 1.0 interfaces manage to do 96), although the internal processing is done at 24-bit as the best cards around.

The Lambda is a 4x2 (or 4x2x2 as they call it), the Omega is an 8x4x2.

---

### Post by jangal on 2010-06-01
[INDENT]so i got the stanton final scratch firwire audio interface on friday and spent the next 24 hours trying to get it to work - i was unsuccessful. this is what the situation is, i'm running lucid with real-time kernal, have the latest jack and ffado from medibuntu on my dell xps m140, which has the 1394 firewire port (the really small one). from my understanding if firewire is selected in the jack setup menu it should automatically start the ffado-dbus-server and it should work - it didn't. so then i started dbus server at terminal and it started to run, then i opened ffado mixer it registered the device! and then i went to jack and got this:
[/INDENT]```

no message buffer overruns
could not open driver .so '/usr/lib/jack/jack_freebob.so': libfreebob.so.0: cannot open shared object file: No such file or directory
no message buffer overruns
could not open component .so '/usr/lib/jack/jack_freebob.so': libfreebob.so.0: cannot open shared object file: No such file or directory
JACK server starting in realtime mode with priority 10
libffado 2.0.0 built Mar 31 2010 14:47:42
00442983919: Fatal (ffado.cpp)[ 174] ffado_streaming_init: There are no devices on the bus
firewire ERR: FFADO: Error creating virtual device
Cannot attach audio driver
JackServer::Open() failed with -1
no message buffer overruns
Failed to start server

```
 
 

[INDENT]at this point i re-read everything again to make sure i did everything accordingly and then repeated the steps, on my second/third attempt the ffado mixer wouldn't register device which it did the first. had it not lured me like that the first time i would have given up earlier, but it did register the device once so i kept at it. by now my pre-simian traits rose to the surface and i cursed, beat my chest and stomped out of my studio to bed. 
[/INDENT][INDENT]so final conclusions it doesn't work with ubuntu (ffado) out of the box. i'm sure it is possible to make it work if one has the knowledge which i don't. the device itself works really well, i tried it on my macbook pro (gen-5,5 OS-X) with mixx 1.7. sound quality was good i was afraid the basslines would be diminshed. though i did notice a difference between playing a digi-track via mixx versus directly through cds. i am going to keep the device to use with mac and mixx which i think is a great deal the interface was a $100, the software is cost-free and liberating, and timecodes can be downloaded again for at no-cost.if anyone has any thoughts on the jack error message above it will be much appreciated. peace - jangal 
 
[/INDENT]

---

### Post by jangal on 2010-06-01
good news (for me atleast)! 
i got it to work! after a number of attempts of going over my steps, the solution was simple yet all the more mystifying. the trick - i started jack via termial as described on the ffado wiki and it worked. all my channels appear (the 2 main ins and outs), the aux/mic in, and the midi in/out as well yea!!!! the sad thing is after all this work i can't get mixx to open -its never ending - jangal

---

### Post by maghoxfr on 2010-06-01
Well congratulations! You'll eventually make it work with mixx. But yes, it's never ending. In the end it gives you great satisfaction though LOL

Enjoy it!

---

### Post by vanzippee on 2010-06-01
I was looking at [_[COLOR="Navy"]this one[/COLOR]_]("http://www.artproaudio.com/products.asp?id=124&cat=1&type=79") from ART. I have used the non-usb in an analogue setup with good results.
From the looks of it there is no reason it shouldn't work, it requires no additional drivers on other os. I was just wondering it anyone has given this one a try before.

Thanks

---

### Post by JC Cheloven on 2010-06-09
Well, here I am, as promised :-)

The Phonic Helix Board 18 firewire arrived home some days ago. I've been doing some testing, and everything is fine. I posted my experience in a specific thread so that everyone benefits. Please see:

[http://ubuntuforums.org/showthread.php?p=9437662#post9437662](http://ubuntuforums.org/showthread.php?p=9437662#post9437662)

Cheers
JC
___________

---

### Post by paninari on 2010-06-18
> **JC Cheloven said:**
> Emmm... Why? 
The specs seem fine, and I expect it to work under linux.

  	 	 	 	 	 	  [SIZE=3]From Tom Doody [www.doody,ws](www.doody,ws) to: [email]support@startech.com[/email]:[/SIZE]
 [SIZE=3]I put Andrew in the subject, because I talked to him this morning, but this message is for anyone who is working on the usbaudio7/Linux patch.  Vivek wrote this specifically for me and the usbaudio7/Linux problem.  Vivek is an above-first-level-support person at Ubuntu/Dell support in India (866-622-1947 dwtv3l1).  If I were to imagine myself as a product manager of usbaudio7, and think of the people best qualified to fix the usbaudio7/Linux problem I would consider Vivek at the top of the list.  He is also a nice guy.  I am eager to have my VOIP phone usable on my Dell netbook, so call me at 718-490-9270.[/SIZE]
 

 [SIZE=3]On a rare occasion I put text from someone else in my blog.  This is one of those rare occasions.  From Vivek who is an Indian in the south of India and speaks Tamil -- nandri.[/SIZE]
 

 [SIZE=3]Dear Tom Doody, [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]Thank you for contacting Dell Hardware Technical Support. [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]Regd. Case             : 817098216 [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]This mail is in reference with your contact made with us on 16/06/2010.Please follow the below article and informed we will give a followup call on the same. [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]Basic Troubleshooting Steps [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]Note: Most of these steps apply equally to Ubuntu, Kubuntu and Xubuntu. The core of all of these systems is the same, and sound is a "core" functionality. [/SIZE]
 [SIZE=3]Is your volume turned up, or is the speaker muted? [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]Double click on the "speaker" icon in the upper right hand corner of the screen. This will launch the Volume Control application, which has various sliders to control the volume. Make sure that the speaker, headphone and master sliders are not muted, and have the volume up from zero. On a fresh install of Ubuntu 8.10, the Speaker volume is turned all the way down. [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]Is the system recognizing your sound card? [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]Open a terminal window, and type "aplay -l". Your output should look something like this: [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]**** List of PLAYBACK Hardware Devices **** [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog] [/SIZE]
  [SIZE=3]Subdevices: 0/1 [/SIZE]
  [SIZE=3]Subdevice #0: subdevice #0 [/SIZE]
 [SIZE=3]If you see aplay: device_list:221: no soundcard found..., Ubuntu is not recognizing your sound card for playback. Check that you have the proper modules installed. [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]Do you have the sound modules installed? [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]Open a terminal window, and type "find /lib/modules/`uname -r` | grep snd". You should see a whole list of items come up. If you don't, it means that the upgrade process missed installing the kernel modules for sound. To fix this, type this at the command line: [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]sudo aptitude install linux-ubuntu-modules-`uname -r` linux-generic [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]After installing the modules, you will need to reboot. [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]If the modules are already installed, check to see whether your hardware is recognizing the sound card as installed [/SIZE]
 [SIZE=3]Is the sound card physically installed and recognized by your hardware? [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]Open a terminal window, and type "lspci -v | less". This will check your computer's motherboard, and attempt to list out all devices that it's recognized as installed. There is probably a lot of things listed, but the one you're looking for will be labeled "Audio device". Mine is listed below: [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) [/SIZE]
        [SIZE=3]Subsystem: Toshiba America Info Systems Device ff01 [/SIZE]
        [SIZE=3]Flags: bus master, fast devsel, latency 0, IRQ 22 [/SIZE]
        [SIZE=3]Memory at dc440000 (64-bit, non-prefetchable) [size=16K] [/SIZE]
        [SIZE=3]Capabilities: <access denied> [/SIZE]
        [SIZE=3]Kernel driver in use: HDA Intel [/SIZE]
        [SIZE=3]Kernel modules: snd-hda-intel [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]Most users have a "built in" sound card for their computer on the motherboard. If yours is built in, and isn't showing up in this step, then you probably need to enable it in your BIOS. When you first boot, or reboot your computer, there's usually a key sequence telling you how to enter the BIOS Configuration Screen. You'll need to sort through your BIOS and enable the built in sound card. [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]If you are not using a built in sound card, and this step does not show your audio card, the card may be seated incorrectly on your motherboard, or may be bad or otherwise incompatible with your motherboard. You will probably want to test the card in another computer to see if it works there. [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]Is my SoundCard supported? [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]The Advanced Linux Sound Architecture (ALSA) is the system that Ubuntu uses for managing Sound output. There is a listing of all of the sound cards supported by ALSA at [http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main) . You should look for the information that was listed by lspci in the previous step. If it turns out that your soundcard is not supported by ALSA, you have basically two different options: Get a new soundcard that is supported by ALSA, or contact the ALSA developers to request support for your soundcards. [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]Important syntax note: ALSA modules are denoted by the prefix 'snd' followed by the dash ' - ', followed by the module name (i.e. 'via82xx'). So the full name might be something like snd-via82xx. However, in some cases you will see an underscore ' _ ' instead of the dash. This is OK, do not let it confuse you. When mentioning module names (to install them or communicate their names to others) only use the dash ' - '. [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]Manual Installation [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]Once you've done the basic troubleshooting listed above, if things still aren't working, you may have found a bug in Ubuntu. It could be something as simple as not detecting your hardware the first time or evidence of a deeper problem. Ubuntu developers need your feedback to see what is not working for you. If you've reached this point, you should file a bug report on [http://launchpad.net](http://launchpad.net) under the Ubuntu distribution. You should probably include the lspci and aplay output listed above in your bug report. Filing a bug report may seem like a worthless exercise, but it really helps in the development process. [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]Manually starting the Audio driver [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]Open a terminal and type sudo modprobe snd-[NAME OF YOUR SOUNDCARD'S DRIVER]. For example, my driver is a via82xx so I would type, sudo modprobe snd-via82xx. [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]After this, try playing some sound. You may want to check the volume levels again, if you hear sound, it means that your installation isn't auto-detecting your sound card, but you have all of the right software. We've temporarily loaded the driver, but it will not be installed on the next reboot. [/SIZE]
 [SIZE=3]You can override the auto-detection and force your computer to load the driver on every reboot by adding the driver (i.e. snd-via82xx) to the /etc/modules file. Type gksudo gedit /etc/modules at the command line, and add your sound driver as the last line of the file. Save the file, and reboot to verify that the sound is working after a reboot. Even if this step works, you should file a bug with the Ubuntu developers at [http://launchpad.net](http://launchpad.net) so they can begin working on it to understand why your computer isn't auto-detecting the soundcard. [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]Refreshing/Reinstalling the drivers [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]Sometimes, sound might be configured correctly, but for some reason or another (tinkering) it stops working. If this is the case, you can purge your custom changes, and restore your system to a clean base. This may clear up your problem, and restore you to a working state. [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]Open a terminal and type sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2. This will purge any custom configurations that you've made, and any hand-compiled modules that you've built, and restore your sound stack to the "Official" Ubuntu core. You can also do this as two separate steps: sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils and then sudo apt-get install linux-sound-base alsa-base alsa-utils , but this may result in some other packages which depend on the sound-base and alsa-utils from being removed, such as gdm and ubuntu-desktop. If this happens, then do sudo apt-get install gdm ubuntu-desktop [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]Another way to restore ALSA to the Ubuntu default [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]I installed alsa from source, and wanted to revert so I wouldn't have to reinstall alsa everytime the kernel moved. The above did not work for me. Here's a safer way that did. [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]That re-grabs all of the alsa binaries and modules. You may also need to [/SIZE]
 [SIZE=3]ls -lt /lib/modules/`uname -r`/kernel/sound/ [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]And delete anything from the day you manually installed alsa. [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]ALSA driver Compilation [/SIZE]
 [SIZE=3] [/SIZE]
 •       [SIZE=3]If you are here, then either your soundcard driver could not be loaded with modprobe, or you want to compile the drivers yourself from scratch. Good luck to you! [/SIZE]
 [SIZE=3] [/SIZE]
 •       [SIZE=3]There are two main ways the sources of alsa-drivers are made available to you. One is through the apt-get system. Using this system would be the recommended system since most of the heavy lifting is done for you. [/SIZE]
 [SIZE=3] [/SIZE]
 •       [SIZE=3]The other way, is getting the latest drivers from alsa-project.org. This page has the latest drivers available, which you might want to fix problems with. However, these have not been tested with Ubuntu and therefore should be used with caution. [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]Using alsa-source [/SIZE]
 [SIZE=3] [/SIZE]
 •       [SIZE=3]Open up a shell: (note: module-assistant is optional, it will compile the package for you) [/SIZE]
 •       [SIZE=3]Type sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source [/SIZE]
 •       [SIZE=3]Type sudo dpkg-reconfigure alsa-source [/SIZE]
 •       [SIZE=3]You now have a big blue dialog box (left and right keys to choose 'Yes' and 'No', Enter key proceed). Answer yes (for ISA-PNP - recommended by package maintainers), then yes again (for debugging - recommended by package maintainers). [/SIZE]
 •       [SIZE=3]Now you must pick which driver you want to install. Use space to select and deselect modules, and up and down to navigate. [/SIZE]
 •       [SIZE=3]From General Help step 3, you should know the name of your driver. Deselect 'all' (the * will go away), and select your driver. In my case, I deselected 'all' then selected 'via82xx'. Hit Enter. Almost home free! [/SIZE]
 •       [SIZE=3]If you chose module-assistant sudo module-assistant a-i alsa-source. If the progress bar reaches 100% with no errors, you will have installed the drivers successfully. Resume this guide from General Help step 4. [/SIZE]
 •       [SIZE=3]If you did not choose module-assistant - Remember the name of your soundcard driver (eg. via82xx) and use it in place of <insert driver> below. [/SIZE]
 [SIZE=3]cd /usr/src [/SIZE]
 [SIZE=3]sudo tar xjvf alsa-driver.tar.bz2 [/SIZE]
 [SIZE=3]cd alsa-driver<insert alsa version, if necessary> [/SIZE]
 [SIZE=3]sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=<insert driver> --with-oss=yes [/SIZE]
 [SIZE=3]sudo make [/SIZE]
 [SIZE=3]sudo make install [/SIZE]
 •       [SIZE=3]If you get no error messages, you will have installed the drivers successfully. [/SIZE]
 •       [SIZE=3]*Success - Resume this guide from General Help step 4. [/SIZE]
 •       [SIZE=3]*Failure - Start a new thread in this thread of the forum. Paste the error message that you get and state that you were following instructions on this page. [/SIZE]
 [SIZE=3]Using drivers from alsa-project [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]Update: The instructions below are outdated. Please see [http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695) for a convenient script that will build the latest ALSA release [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]The alsa-project route is very similar to the alsa-source route without the module-assistant. First you would have to get the alsa-driver tar from alsa-project then pretty much do configure, make and make install again. However, I do recommend that you make a specific directory when you compile something from source. Remember the name of your soundcard driver and use it in place of the blue text below. [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]mkdir src [/SIZE]
 [SIZE=3]cd src [/SIZE]
 [SIZE=3]mkdir alsa [/SIZE]
 [SIZE=3]cd alsa [/SIZE]
 [SIZE=3]sudo apt-get install build-essential linux-headers-$(uname -r) [/SIZE]
 [SIZE=3]wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.12.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.12.tar.bz2) [/SIZE]
 [SIZE=3]tar -xvjf alsa-driver-1.0.12.tar.bz2 [/SIZE]
 [SIZE=3]cd alsa-driver-1.0.12 [/SIZE]
 [SIZE=3]sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=<enter driver name here e.g. via82xx> --with-oss=yes [/SIZE]
 [SIZE=3]sudo make [/SIZE]
 [SIZE=3]sudo make install [/SIZE]
 [SIZE=3]If you get no errors from doing the above then you have successfully compiled alsa-drivers from source. Resume this guide from General Help step 4. [/SIZE]
 [SIZE=3]Using alsamixer [/SIZE]
 •       [SIZE=3]Type this into a shell alsamixer [/SIZE]
 [SIZE=3]You will now see what appears to be a graphical equalizer. It is more like ten different volume controls in the sample place. [/SIZE]
 •       [SIZE=3]To navigate around: [/SIZE]
 •       [SIZE=3]*Left and Right Arrow Keys - Move left and right (if you move long enough in one direction you will get back to where you started - you will not fall off the screen ) [/SIZE]
 •       [SIZE=3]*Up and Down Arrow Keys - Increase and decrease volume respectively. [/SIZE]
 •       [SIZE=3]*Letter M Key - Mutes/unmutes. If a channel is unmuted, then there is a green box underneath the volume slider. If the channel is muted, the box is grey. [/SIZE]
 [SIZE=3]Saving Sound Settings [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]Do this step to ensure that your alsamixer settings are reloaded with each boot. First make sure you have your settings just the way you like them in alsamixer. Then do sudo alsactl store 0 or if this is your nth sound card (where n is the number of soundcards in your computer) replace 0 with n-1. Many thanks to xpix for trying this out. [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]Loading a working sound configuration [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]If you can find someone with similar HW as yours and has working sound, you could take their settings and try them on your HW. [/SIZE]
 [SIZE=3]1.      Get a working /var/lib/alsa/asound.state from someone who has similar hardware [/SIZE]
 [SIZE=3]2.      Save it as /tmp/asound.state [/SIZE]
 [SIZE=3]3.      alsactl -F -f /tmp/asound.state restore [/SIZE]
 [SIZE=3]Getting more than one application to use the soundcard at the same time [/SIZE]
 •       [SIZE=3]You might want to play a game and listen to music on your favorite music player at the same time. To do this successfully, you will have to use ALSA since it supports this feature the best. On all the music players I know of, you can configure the sound engine, to any module that is available. [/SIZE]
 •       [SIZE=3]The setting is usually found under something like Tools >>> Configure >>> Player Engines. [/SIZE]
 •       [SIZE=3]For games, it is a bit more tricky since there is not always a way to configure the player engine directly. Most games, however, do support the OSS. ALSA has an OSS module that allows OSS applications to use the ALSA driver. [/SIZE]
 •       [SIZE=3]To do this you will need the alsa-oss package sudo apt-get install alsa-oss [/SIZE]
 •       [SIZE=3]After doing this step, it is very easy to use alsa-oss. In the shell, you can type 'aoss' then the name of the program name you want to use with alsa-oss. [/SIZE]
 [SIZE=3]Configuring default soundcards / stopping soundcards from switching [/SIZE]
 [SIZE=3]Note: This section assumes that you have installed each soundcard properly. [/SIZE]
 •       [SIZE=3]In a shell, type cat /proc/asound/modules [/SIZE]
 •       [SIZE=3]This will give the the name and index of each soundcard you have currently. Make a note of the names, and decide which one you want to be the default card. [/SIZE]
 •       [SIZE=3]Now type sudo nano /etc/modprobe.d/alsa-base [/SIZE]
 •       [SIZE=3]At the very end of the file, add the following (assuming you have 3 cards with module names A, B and C and you want to have them in the order CAB) [/SIZE]
 [SIZE=3]options snd-C index=0 [/SIZE]
 [SIZE=3]options snd-A index=1 [/SIZE]
 [SIZE=3]options snd-B index=2 [/SIZE]
 [SIZE=3]Getting MIDI To Work - *EXPERIMENTAL* [/SIZE]
 [SIZE=3]This section assumes you can successfully hear sound from your soundcard. First of all, make sure that you actually have a MIDI port on your soundcard. Most onboard soundcards do not have a MIDI port. [/SIZE]
 [SIZE=3]Next, open up this file: [/SIZE]
 [SIZE=3]sudo nano /etc/modprobe.d/alsa-base Then add this options line options <snd module name here i.e. snd-via82xx> mpu_port=0x330 OR if you already have a options line for this soundcard add mpu_port=0x330 to the line. [/SIZE]
 [SIZE=3]The default MIDI port is 330. You should verify this number in your BIOS if you are not sure. If the number is not listed, it is most likely that the number is 330 (add the 0x for the file). [/SIZE]
 [SIZE=3]If you get no errors, you have successfully installed your MIDI port. At the moment, I do not know if any further configuration is necessary. [/SIZE]
 [SIZE=3]Getting Line Input to work (Microphone, etc) [/SIZE]
 [SIZE=3]Changing default subdevice configuration [/SIZE]
 •       [SIZE=3]Some sound devices have multiple capture subdevices (eg. hda-intel), but pulseaudio only seems to detect the parent device, and only listens to subdevice #0. ALSA may not be configured to use your preferred device as subdevice #0 by default. [/SIZE]
 [SIZE=3]o       Open the pulseaudio record meter (pavumeter --record) [/SIZE]
 [SIZE=3]o       Talk into your chosen device while you carry out the process and watch the meter. [/SIZE]
 &#61607;       [SIZE=3]Some channels are quite noisy even with no input (especially on integrated chipsets), so we are watching for movements that correspond to our voice. [/SIZE]
 [SIZE=3]o       Use alsamixer -c n (where n is your sound card number, probably 0) [/SIZE]
 &#61607;       [SIZE=3]Press F4 to get to the capture console [/SIZE]
 &#61607;       [SIZE=3]Make sure the first capture channel is enabled ("CAPTUR" in red, press space to toggle), and the volume turned up. [/SIZE]
 &#61607;       [SIZE=3]Check the first input source is switched to your chosen plug (Mic, in my case) [/SIZE]
 [SIZE=3]o       At this point, you should see the record meter bouncing in response to your voice. [/SIZE]
 [SIZE=3]Miscellaneous Tips and Tricks [/SIZE]
 [SIZE=3]Here are a few things that other people have dug up over the course of this guide. Not all tips are meant to work for all hardware (believe me hda-intel will probably have like a mini guide of it's own one day). [/SIZE]
 •       [SIZE=3]shaviro found the following from this post [http://www.ubuntuforums.org/showthread.php?t=153752](http://www.ubuntuforums.org/showthread.php?t=153752) [/SIZE]
 [SIZE=3]I wasn't getting any sound out of my Sony Vaio PCG-4B1L ...The crucial thing is to enable everything in alsamixer EXCEPT "external amplifier." (I had to turn off microphone too, to stop feedback). [/SIZE]
 •       [SIZE=3]Useff had a very annoying problem where he could get sound through alsa from one user, but not through is main account. [http://www.ubuntuforums.org/showthread.php?p=1221754](http://www.ubuntuforums.org/showthread.php?p=1221754). He and I managed to fix the problem by making sure the main account was in the audio group in /etc/group (which he was) and deleting the .asoundrc file in the main account's /home directory. [/SIZE]
 •       [SIZE=3]Bo Rosén solved his ISA problem the following way. Thanks to FarEast for his help in the matter. [/SIZE]
 [SIZE=3]o       Thanks to [[[http://ubuntuforums.org/showthread.php?t=127402]]](http://ubuntuforums.org/showthread.php?t=127402]]) this post I got soundblaster 16 isa working. In short add{{{snd-sb16{{{ to /etc/modules then create a new file: {{{gedit /etc/modprobe.d/sound and enter this line: [/SIZE]
 [SIZE=3]options snd-sb16 isapnp=0 port=0x220 irq=5 dma8=1 dma16=5 [/SIZE]
 [SIZE=3]sudo update-modules [/SIZE]
 [SIZE=3]reboot}}} [/SIZE]
 •       [SIZE=3]webbca01 figured out how to get AC'97 work with the help of the second last post here and this post. Basically, if you have an intel8x0 module, you can get AC'97 working by sudo nano /etc/modprobe.d/alsa-base and adding this as the last line: "options snd-intel8x0 ac97_quirk=3" [/SIZE]
 •       [SIZE=3]scragar noticed that sometimes even if ubuntu is set to use a particular sound card it still attempts to use a default sound card that may or may not be set, in which case [/SIZE]
 [SIZE=3]sudo apt-get install asoundconf-gtk && asoundconf-gtk [/SIZE]
 [SIZE=3]will allow you to quickly change your default sound card(you may also uninstall asoundconf-gtk afterwards, provided you select remove and not "completely remove", from synaptic, or purge from the command line). [/SIZE]
 •       [SIZE=3]Sound did not work after resuming from suspend on my Acer Aspire 4720 running Kubuntu Hardy. /etc/init.d/alsa-utils restart (or reset) did not work, neither did any modprobing. Finally, sudo /sbin/alsa force-reload worked. [/SIZE]
 •       [SIZE=3]Make sure you are part of the audio group. This can be done by issuing the command groups. If you don't see audio here add youself to the audio group. [/SIZE]
 [SIZE=3] [/SIZE]
 [SIZE=3]Thank you for choosing Dell. [/SIZE]
 [SIZE=3]Vivek [/SIZE]
 [SIZE=3]Resolution Specialist.[/SIZE]

---

