---
title: "good small supported no hassles sound card"
date: 2009-11-16
forum: Ubuntu Studio
---

### Post by extendedping on 2009-11-16
I have another thread opened regarding trying to get my firepod working with ubuntu studio, I am going to keep trying but I have a bad feeling it is just not going to work. so while I continue to see if that can be fixed I figured it was time to start scouring ebay and craigslist for things that will work for certain. I DO NOT WANT TO USE CUBASE/WINDOWS and am committed to learning the process of home recording on my ubuntu system. let me give you my setup and what I am (hopefully) going to be using it for. I have a 220 gb hard drive 4 gb of mem and my cpu is (from /proc/cpu)
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz
stepping        : 6
cpu MHz         : 2128.000
cache size      : 2048 KB

it is a dual so there is a processor 1 as well same specs. my motherboard has built in ethernet and sound, I currently have 2 pci slots, one holding the firewire card connected to the firepod that can be removed and the other free. 

my goal is to record rock songs playing instruments (guitar and bass), and doing vocals separately as I work on songs. I have a zoom g9.2tt for guitar effects that would go into the soundcard. I would hope to be able to use hydrogen or some other linux stuff to get drums in. if jack rack or this creox thing I see in my menu is good I would plan on selling that monster pedal (or I'd consider trading it for a supported sound card) and recording going straight into the sound card from my guitar/bass. so...

for this type of setup is usb sufficient? I have heard it has much higher latency issues then firewire but someone told me that for individual tracking which is what I will be doing (meaning no live band) that it is "ok". or should I be looking for a pci sound card with some sort of breakout box? 

the important things for me (as per my title) are that the interface is small, can produce a good recording level and above all will be free of the hassles that I am seeing with my firewire interface. thank you very much in advance...please help me dump windows for good I really like ubuntu for everything else....

---

### Post by AutoStatic on 2009-11-16
> **extendedping said:**
> my goal is to record rock songs playing instruments (guitar and bass), and doing vocals separately as I work on songs. I have a zoom g9.2tt for guitar effects that would go into the soundcard. I would hope to be able to use hydrogen or some other linux stuff to get drums in. if jack rack or this creox thing I see in my menu is good I would plan on selling that monster pedal (or I'd consider trading it for a supported sound card) and recording going straight into the sound card from my guitar/bass. so...I don't know the Zoom but if it's a bit like the Line6 Pod then I would keep it. Stuff like Creox/JackRack/Guitarix/Rackarrak is nice to play with for electric guitar but a simple Pod sounds way better.

> **extendedping said:**
> for this type of setup is usb sufficient? I have heard it has much higher latency issues then firewire but someone told me that for individual tracking which is what I will be doing (meaning no live band) that it is "ok". or should I be looking for a pci sound card with some sort of breakout box?If you are not planning on recording more than 2 tracks at once then USB will suffice. Higher latency? I'm on 4ms now with my USB soundcard and JACK doesn't complain.

> **extendedping said:**
> the important things for me (as per my title) are that the interface is small, can produce a good recording level and above all will be free of the hassles that I am seeing with my firewire interface. thank you very much in advance...please help me dump windows for good I really like ubuntu for everything else....Get yourself a class compliant device (like the Edirol UA-25) and dump it!

As for PCI devices, no experience with those.

---

### Post by extendedping on 2009-11-16
ok so just to confirm...provided there is nothing inherently wrong with my computer (which I don't think there is) the Edirol UA-25 should just plug in, start qjackctl with a different driver (I don't see usb in the choices) and I should be able to start learning ardour/hydrogen etc??? as opposed to endless tweaking like I am doing on my firepod? I could make that my xmas gift....and I am supposing I could still use it for cubase on my laptop???

also when you say "class compliant" do you mean any usb soundcard should work?

---

### Post by extendedping on 2009-11-16
> **AutoStatic said:**
> I don't know the Zoom but if it's a bit like the Line6 Pod then I would keep it. Stuff like Creox/JackRack/Guitarix/Rackarrak is nice to play with for electric guitar but a simple Pod sounds way better.

If you are not planning on recording more than 2 tracks at once then USB will suffice. Higher latency? I'm on 4ms now with my USB soundcard and JACK doesn't complain.

Get yourself a class compliant device (like the Edirol UA-25) and dump it!

As for PCI devices, no experience with those.

off the top of mount crumpit?

---

### Post by AutoStatic on 2009-11-16
> **extendedping said:**
> off the top of mount crumpit?
[Looks good to me!]("http://img.photobucket.com/albums/v329/SassTheGrinch/Grinch/MtCrumpit.jpg")

As for class compliant USB devices: [http://en.wikipedia.org/wiki/Sound_card#USB_sound_.22cards.22](http://en.wikipedia.org/wiki/Sound_card#USB_sound_.22cards.22)

The Edirol UA-25 is such a device, so you can just plug it in, it will get automatically detected and the snd-usb-audio module will be loaded and you're good to go. OK, it's a USB1 device but for me it works really well, besides, there are no USB2 devices yet that work well with Ubuntu apparently: [http://ubuntuforums.org/showthread.php?t=1235322&page=3](http://ubuntuforums.org/showthread.php?t=1235322&page=3)

---

### Post by extendedping on 2009-11-16
> **AutoStatic said:**
> [Looks good to me!]("http://img.photobucket.com/albums/v329/SassTheGrinch/Grinch/MtCrumpit.jpg")

As for class compliant USB devices: [http://en.wikipedia.org/wiki/Sound_card#USB_sound_.22cards.22](http://en.wikipedia.org/wiki/Sound_card#USB_sound_.22cards.22)

The Edirol UA-25 is such a device, so you can just plug it in, it will get automatically detected and the snd-usb-audio module will be loaded and you're good to go. OK, it's a USB1 device but for me it works really well, besides, there are no USB2 devices yet that work well with Ubuntu apparently: [http://ubuntuforums.org/showthread.php?t=1235322&page=3](http://ubuntuforums.org/showthread.php?t=1235322&page=3)

that is what I need, I will just limit my search to that card, perhaps I can even get someone to trade for the firepod who knows...(but not on this forum for sure)

love that pic...:)

---

### Post by AutoStatic on 2009-11-16
As long as you don't dump me from Mt Crumpit when in the end the UA-25 doesn't work either ;)

---

### Post by extendedping on 2009-11-16
> **AutoStatic said:**
> As long as you don't dump me from Mt Crumpit when in the end the UA-25 doesn't work either ;)

no thats my wife's job (we will be going down together).

---

### Post by sgx on 2009-11-16
I've been using a pci mAudio 24/96 for years. Look for older second-hand units, where people sell due to upgrading. (New units may be different, and fail. I pass this on as 'rumour' only) 

The i/o is
left-right line in gold rca
left-right line out gold rca
midi in/out on breakout cable
left-right digital i/o rca gold on breakout cable

Quality wise, I can't tell a difference between my productions, and
commercial CDs. It is probably the easiest to setup, and most bulletproof device for linux audio.

I prefer rakarrack  over the Amplitube/Guitar Rig crowd, and also use it
for hydrogen, as the EQ really opens up the percussion track option. We all have favorites,  the presets in rakarrack need careful use do to volume inconsistancies, but the multi-fx are great. Your taste may vary.

Creox has a very nice layout for phaser, echo, and tremolo.

I use Reaper in a wine/wineasio linux setup, the output of which can be routed in qjackctl to my linux apps, very flexible! If I don't render the Reaper output, I record the total jackd setup with timemachine, and edit it as needed in audacity. 

Hydrogen is simple and great. Make a pattern, listening as it loops while you add beats on the adjustable grid, place the pattern on the song grid,
then make more patterns for fills, intros, endings, place each on the song grid where desired. Save as songs, patterns, and export midi files!

Zynaddsubfx is a great softsynth, again, rackarrack and creox are fine to
augment its built-in multi-fx, which are good to begin with.

Have you tried Studio64? Noone will hate you for trying! It has similar
underpinnings to ubuntu, and theres nowhere to go but up, at the moment;)

---

### Post by extendedping on 2009-11-17
> **sgx said:**
> I've been using a pci mAudio 24/96 for years. Look for older second-hand units, where people sell due to upgrading. (New units may be different, and fail. I pass this on as 'rumour' only) 

The i/o is
left-right line in gold rca
left-right line out gold rca
midi in/out on breakout cable
left-right digital i/o rca gold on breakout cable

Quality wise, I can't tell a difference between my productions, and
commercial CDs. It is probably the easiest to setup, and most bulletproof device for linux audio.

I prefer rakarrack  over the Amplitube/Guitar Rig crowd, and also use it
for hydrogen, as the EQ really opens up the percussion track option. We all have favorites,  the presets in rakarrack need careful use do to volume inconsistancies, but the multi-fx are great. Your taste may vary.

Creox has a very nice layout for phaser, echo, and tremolo.

I use Reaper in a wine/wineasio linux setup, the output of which can be routed in qjackctl to my linux apps, very flexible! If I don't render the Reaper output, I record the total jackd setup with timemachine, and edit it as needed in audacity. 

Hydrogen is simple and great. Make a pattern, listening as it loops while you add beats on the adjustable grid, place the pattern on the song grid,
then make more patterns for fills, intros, endings, place each on the song grid where desired. Save as songs, patterns, and export midi files!

Zynaddsubfx is a great softsynth, again, rackarrack and creox are fine to
augment its built-in multi-fx, which are good to begin with.

Have you tried Studio64? Noone will hate you for trying! It has similar
underpinnings to ubuntu, and theres nowhere to go but up, at the moment;)

thanks for all the info. I tried hydrogen (just clicking on my keyboard) and the drums sounded great, as good as the bfd I used with cubase except for the kick which sounded unusable :(

---

### Post by sgx on 2009-11-17
Here is a list of Hydrogen kits, all I can find on google, some good kicks are in there, and the various EQ/fx exist to fatten the lot. The gscw kits are large downloads.

3355606kit
Boss DR-110
Classic-626
Columbo
DeatMetal
easternHop-1
ElektricEmpireKit
GSCW-1
GSCW-2
HipHop-1
HipHop-2
K-27_Trash_Kit
Millo-Drums_v.1
Millo_Multilayered2
Millo_MultiLayered3
Roland TR-606
Roland TR-626
Roland TR-808
Roland TR-909
Synthie-1
Techno-1
TR808909
VariBreaks
Yamaha Vintage Kit

Cheers

---

### Post by Bigneil on 2009-11-18
i use an old creative soundblaster card with a live drive head unit. i picked it up on ebay for almost nothing.

i record electic guitar, accoustic guiter, keyboard, bass guitar no probs.

---

### Post by extendedping on 2009-11-18
> **Bigneil said:**
> i use an old creative soundblaster card with a live drive head unit. i picked it up on ebay for almost nothing.

i record electic guitar, accoustic guiter, keyboard, bass guitar no probs.

thats sounds like a viable thing to try (I like almost nothing) as I don't want to spend a lot on something that may or may not work. can i ask as a recording newbie what is a "live drive head unit"??? and are there issues with vocals which I don't see in your post??? do you know the exact card???

---

### Post by AutoStatic on 2009-11-18
A live drive unit is probably the extension card you can attach to it which provides some extra inputs and outputs.
Personally I would stay away from Creative stuff. But that's just my opinion, I have no experience whatsoever with using Creative devices in Ubuntu.

---

### Post by sgx on 2009-11-18
> **extendedping said:**
> thats sounds like a viable thing to try (I like almost nothing) as I don't want to spend a lot on something that may or may not work. can i ask as a recording newbie what is a "live drive head unit"??? and are there issues with vocals which I don't see in your post??? do you know the exact card???

An good route would be an inexpensive but high quality preamp for vocals/instruments:

[http://www.sweetwater.com/store/detail/TubeMP/reviews/](http://www.sweetwater.com/store/detail/TubeMP/reviews/)

This would give superior results with an maudio card when properly
set up.
Cheers

---

### Post by Bigneil on 2009-11-19
> **AutoStatic said:**
> A live drive unit is probably the extension card you can attach to it which provides some extra inputs and outputs.
Personally I would stay away from Creative stuff. But that's just my opinion, I have no experience whatsoever with using Creative devices in Ubuntu.

the recording i do is on a very amateur level, anybody who is a bit more serious about it would probably find they need more advanced gear.
 Here is a pic of live drive. it goes in the front of your box like a cd drive and provides extra inputs and outputs. it connects to an appropriate sound card. they are not to everyones liking but it works for me.[IMG]http://is.gumtree.com/ad_image/live/big/249265478.jpg[/IMG]

---

### Post by extendedping on 2009-11-19
thanks everyone for the helpful responses, as I could not get the firepod working I am thinking the edirol ua25 if I can pick one up used as I can use it on different computers. too bad bout the firepod.

---

### Post by MIJ-VI on 2010-06-29
> **extendedping said:**
> thanks for all the info. I tried hydrogen (just clicking on my keyboard) and the drums sounded great, as good as the bfd I used with cubase except for the kick which sounded unusable :(

Hi extendedping.

You've likely learned about this by now, but in case someone else hasn't, the...

[FONT=Courier New]hydrogen-drumkits[/FONT]

...package in Synaptic Package Manager will install more kits sporting proper sounding kicks.

---

