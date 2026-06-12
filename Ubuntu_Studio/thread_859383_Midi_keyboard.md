---
title: "Midi keyboard?"
date: 2008-07-14
forum: Ubuntu Studio
---

### Post by Olav on 2008-07-14
Dear musicians,

Although very new to playing music I would like to learn to play the piano/keyboard. In fact, my goal is to be able to play a few (*slow! simple! short!*) classical piano pieces within a year. I have always wanted to do this and finally decided I should go ahead - or forget about it.

I am a long time user of Ubuntu (and Linux in general) and I do have a fairly good, recent computer. So my plan is to install Ubuntu Studio and then use a simple but good MIDI keyboard for practice. Could someone please recommend a keyboard that may be suitable for my endeavour?

I think these are my requirements:
[LIST]
[*]must work with Ubuntu Studio, connect through USB
[*]full sized and "sensitive" piano keys
[*]capable (with software) of fairly natural piano sound
[*]would like good build quality, not something that falls apart when only looking at it - you know what I mean
[*]NO distracting extra features, controls, displays et cetera (unless they don't add to the price)
[*]as inexpensive as reasonably possible, all other requirements considered
[/LIST]
Not sure if I need the full width of 88 keys. I suppose I could get going with a few less.

I was thinking about perhaps an M-AUDIO keyboard, because I have seen one in a shop, but I am not sure if there aren't any cheaper options. My budget is tighter than I would like. So the less money needed the better.

Will I also need another sound card? My computer only has an on-board sound thingie, it seems sufficient for playing sound files and videos.

Any input will be much appreciated.

---

### Post by Sharkadder on 2008-07-14
sent you a pm dude

:guitar:

---

### Post by Olav on 2008-07-15
[BUMP] Are there any musicians out there who have experience using a MIDI keyboard in Ubuntu Studio? Thank you.

---

### Post by Peter Anselmo on 2008-07-15
I had a Casio Privia PX-700 Hooked up to 8.04 and it worked fine.  I really liked the keyboard, the whole Privia series offers a lot of features (full size, weighted keys, etc) at a good price.

---

### Post by Stochastic on 2008-07-15
It sounds most like you're looking to learn how to play classical piano.  For this, you'll be MUCH and I mean MUCH better off in the long run if you get a fully weighted keyboard - they are a bit more expensive, but you'll thank yourself later and probably end up sticking with it longer.  The fully 88-keys will be nice to have (you won't have to upgrade later), but certainly not needed for a beginner, however most fully weighted keyboards will have 88-keys anyway.  Beyond that, just play them in the store and take a listen yourself.  Usually they'll make a fairly realistic piano sound out of the box.  Look for a trusted name such as Korg, Yamaha, or Roland (there are many others).

MIDI controllers (keyboards that only send MIDI signals and don't have any synth engine built in) are not what you should be looking for.  They do not have fully weighted keys.  You'll be mad at yourself down the road if this is all you buy.

As for software on Ubuntu to make realistic piano sounds, your best bet is commercial software.  There is a VSTi that's known to work well in Wine called Pianoteq, and I'm blown away by the quality of sound it outputs.  The other option is QSynth + a realistic sound font - this is a decent setup, and usually entirely free.

The only other piece you'll need is a soundcard that is MIDI capable (you can find a USB MIDI adapter for $20 at most music stores).  It's the soundcard that you need to worry about Ubuntu compatability with, not the MIDI keyboard - and most USB cards are fully standards compliant (i.e. work with alsa drivers).  All MIDI keyboards will send standard MIDI data to your soundcard, Ubunutu grabs this from the card, not from the keyboard (unless the keyboard attaches to the computer via USB rather than the 5-pin MIDI connector).

---

### Post by Sharkadder on 2008-07-15
hi olav, you mentioned in a private message i sent that other operating systems are not an option.

Install the software using the wine emulator on ubuntu, advanced midi editors such as guitar pro and simple ones like anvil studio are well worth a look.  You don't need to look for linux only midi software on linux.

As mentioned in pm i have a casio LK-90 TV keyboard, it works for what i need but you may want to opt for more key's keyboard than the stanard 61 mine has.  You can get keyboards with both midi and usb output or individually although you requested one with usb output like one such as mine has.

If you want quallity then go for a yamaha or roland, otherwise something like a casio will do you, they are ok and work fine for what you will need.

You can easilly download sheet music off the web and then learn it on your keyboard.  alternatively you can download guitar pro files which people have created themselves for you to learn the song.  thwe reason i was suggesting guitar pro in the first place was for that very reason, you can get many guitar pro files of songs which can all be converted to midi, learn them on a a keyboard and generally they are quite accurate.  You really need a keyboard with a memory or a card slot to allow you to put midi songs onto there.  As mentioned in the pm a keylighting feature or a show what note to press on the fret like mine does is a great feature.

since keyboards use general midi anyways, your sound card should not be a problem, mine isn't.  Although if you get one with added effects then you will need a sound card ideal for musical purposes.

Hope that help's a bit.  but generally some keyboards work with some programs, some they won't work with, i figured out it's mainly trial and error when i got mine.

Price wise, go on ebay and have a look, you may not trust things off there but that's where mine came from and it's great and was cheap.

---

### Post by Olav on 2008-07-16
> **Peter Anselmo said:**
> I had a Casio Privia PX-700 Hooked up to 8.04 and it worked fine.  I really liked the keyboard, the whole Privia series offers a lot of features (full size, weighted keys, etc) at a good price.
I had to google that thing. Looks very elegant!

Thanks for your suggestion, I will keep it in mind.

---

### Post by Olav on 2008-07-16
> **Stochastic said:**
> It sounds most like you're looking to learn how to play classical piano.
Just a bit. It's mainly because I need a new hobby. I have no ambition to ever become a concert pianist. Age-wise it's too late for that anyway...

So nice little classical pieces and children's stuff seem the way to go. But I also like jazz and blues music so I may want to try that, too, one day. If I ever get my fingers loose enough.

> For this, you'll be MUCH and I mean MUCH better off in the long run if you get a fully weighted keyboard - they are a bit more expensive, but you'll thank yourself later and probably end up sticking with it longer.
Just to be clear about me being an absolute newbie: is "fully weighted" a characteristic entirely separate from "touch sensitive"? If it is, would I be correct to think that the latter is slightly more important? I have seen it advertised in rather affordable (read: cheap) keyboards.

A keyboard that got me thinking was this one: [Axiom61]("http://www.m-audio.com/products/en_us/Axiom61-main.html"). It says it has "semi weighted" keys. So what is the difference, exactly, and perhaps will they be OK, too?

> The fully 88-keys will be nice to have (you won't have to upgrade later), but certainly not needed for a beginner, however most fully weighted keyboards will have 88-keys anyway.  Beyond that, just play them in the store and take a listen yourself.  Usually they'll make a fairly realistic piano sound out of the box.  Look for a trusted name such as Korg, Yamaha, or Roland (there are many others).

MIDI controllers (keyboards that only send MIDI signals and don't have any synth engine built in) are not what you should be looking for.  They do not have fully weighted keys.  You'll be mad at yourself down the road if this is all you buy.

As for software on Ubuntu to make realistic piano sounds, your best bet is commercial software.  There is a VSTi that's known to work well in Wine called Pianoteq, and I'm blown away by the quality of sound it outputs.  The other option is QSynth + a realistic sound font - this is a decent setup, and usually entirely free.
VSTi? QSynth? More stuff to Google...

> The only other piece you'll need is a soundcard that is MIDI capable (you can find a USB MIDI adapter for $20 at most music stores).  It's the soundcard that you need to worry about Ubuntu compatability with, not the MIDI keyboard - and most USB cards are fully standards compliant (i.e. work with alsa drivers).  All MIDI keyboards will send standard MIDI data to your soundcard, Ubunutu grabs this from the card, not from the keyboard (unless the keyboard attaches to the computer via USB rather than the 5-pin MIDI connector).
I was under the impression that MIDI nowadays can be done entirely in software. If this is not the case and I need to get another sound card then which is the minimum standard card that works well with Ubuntu?

I can hardly play 4 or 5 notes yet, and I do fear having to spend hundreds of Euros before I can even get started. I am currently living on disability so-called "benefits", so money is extremely tight sometimes.

But thank you, you convinced me that I really need to do more research. I hope you will be around next time I'm asking dumb questions.

---

### Post by Olav on 2008-07-16
> **Sharkadder said:**
> hi olav, you mentioned in a private message i sent that other operating systems are not an option.

Install the software using the wine emulator on ubuntu, advanced midi editors such as guitar pro and simple ones like anvil studio are well worth a look.  You don't need to look for linux only midi software on linux.
I will have to look into that. I haven't yet researched much music software, but of course I came across RoseGarden. Seems to offer much more features than I will probably ever need. Have you used it and could you tell me a bit about your experience with that?

> As mentioned in pm i have a casio LK-90 TV keyboard, it works for what i need but you may want to opt for more key's keyboard than the stanard 61 mine has.  You can get keyboards with both midi and usb output or individually although you requested one with usb output like one such as mine has.

If you want quallity then go for a yamaha or roland, otherwise something like a casio will do you, they are ok and work fine for what you will need.

You can easilly download sheet music off the web and then learn it on your keyboard.  alternatively you can download guitar pro files which people have created themselves for you to learn the song.  thwe reason i was suggesting guitar pro in the first place was for that very reason, you can get many guitar pro files of songs which can all be converted to midi, learn them on a a keyboard and generally they are quite accurate.  You really need a keyboard with a memory or a card slot to allow you to put midi songs onto there.  As mentioned in the pm a keylighting feature or a show what note to press on the fret like mine does is a great feature.
I agree that does seem quite neat. I may want to try that out.

> since keyboards use general midi anyways, your sound card should not be a problem, mine isn't.  Although if you get one with added effects then you will need a sound card ideal for musical purposes.

Hope that help's a bit.  but generally some keyboards work with some programs, some they won't work with, i figured out it's mainly trial and error when i got mine.

Price wise, go on ebay and have a look, you may not trust things off there but that's where mine came from and it's great and was cheap.
Will do. Thank you again.

---

### Post by Olav on 2008-07-16
Just wanted to add, I found this website: [http://www.tweakheadz.com/tips_on_buying_a_keyboard.html](http://www.tweakheadz.com/tips_on_buying_a_keyboard.html)

Reading all the advice there is going to keep me busy for a while... ;)

Of course, if anyone here wants to share his/her thoughts on the matter I would still be very grateful.

---

### Post by Olav on 2008-07-16
Here I am again, did some more web browsing. I saw a [Casio CDP-100]("http://www.casio.com/products/Musical_Instruments/Cabinet_Digital_Pianos/CDP-100/") on offer for EUR 399. Also saw some positive reviews from piano teachers and such. I'm beginning to think this might fit my needs.

---

### Post by Sharkadder on 2008-07-16
that keyboard doesn't come with usb connection as you requested, although midi in/out will do the same thing.  I have not used that software you mentioned but i will look into it later and try my keyboard with it, if it is compatible.

The CDP-100 seems to only come with 6 different tones, this means that you can only have 6 different instruments on the keyboard itself, to you it may work but to me it i'd want more than that.

I also noticed thatthet keyboard you showed has polyphonic tones, you really would be better off with general midi as well if you are wanting to use the computer aswell, the site went down when i went to look at the specs again so i couldn't clarify if it supported general midi or not, but again that keyboard may do you.

Only thing is the price, it looks very steep to me that, in uk pounds it is about £250, very pricey for such a basic keyboard.  Maybe you can shop around and find one cheaper.

---

### Post by Stochastic on 2008-07-16
> **Olav said:**
> Age-wise it's too late for that anyway...
It's NEVER too late!

> **Olav said:**
> Just to be clear about me being an absolute newbie: is "fully weighted" a characteristic entirely separate from "touch sensitive"? If it is, would I be correct to think that the latter is slightly more important? I have seen it advertised in rather affordable (read: cheap) keyboards.

Yes, they are different.  Fully weighted means that the keyboard keys themselves have the same mass as a regular piano's keys.  Many cheaper keyboards will have flimsy hollow plastic keys - you don't want these.  Touch Sensitive means that the internal computer that senses when the key is pressed also senses the force with which the key is pressed - this is also a very good feature.

> **Olav said:**
> I was under the impression that MIDI nowadays can be done entirely in software. If this is not the case and I need to get another sound card then which is the minimum standard card that works well with Ubuntu?

MIDI can be done entirely with software.  What I was referring to was that the midi cable (a 5-pin circular connector) from your keyboard will need to plug into the computer somehow (most easily with a $20 USB to MIDI adapter - which is actually seen by Ubuntu as a soundcard).  The keyboards that plug directly into a computer via USB basically have this piece built in, however, many of them use chips that Ubuntu is not compatible with - so buyer beware - you'll probably be more successful with a USB to MIDI adapter.

> **Olav said:**
> But thank you, you convinced me that I really need to do more research. I hope you will be around next time I'm asking dumb questions.

Research is always a good thing on any large purchase.  But no question is ever dumb unless it's not asked.

P.S. Sharkadder: Polyphony is not related to General MIDI compatability at all.
Polyphony is the ability for multiple keys to be played at once (on that given keyboard 32 notes can sound simultaneously).
General MIDI is a communications standard that is described well here: [http://en.wikipedia.org/wiki/MIDI](http://en.wikipedia.org/wiki/MIDI) It can operate on keyboards with or without polyphony; and both monophonic and polyphonic keyboards have equal likelihood of supporting general midi.

---

### Post by eddyvillagran on 2008-07-23
I use an E-MU Xboard midi usb keyboard and a Lexicon Omega, both works great i didnt have to install anything else than the alsa driver that comes with ubuntu studio.  Lexicon Omega is compatible with ardour using 4 individual inputs at the same time.  the Xboard is compatible with all programs in ubuntu studio running jack. You can use Qsynth and search for soundfonts in internet, i have several piano sounds that sounds like real acoustic piano.  The only thing you have to do is to make some changes in jack setup to avoid xruns depending on your hardware. I prefer the Xboard because it has 16 rotary midi controls fully assignable. I can tell you that since i learned to use the programs in ubuntu studio i dont need to use windows anymore, the only program i really miss is Ableton Live but i can live without it.

---

### Post by warbread on 2008-08-14
> **Stochastic said:**
> 
As for software on Ubuntu to make realistic piano sounds, your best bet is commercial software.  There is a VSTi that's known to work well in Wine called Pianoteq, and I'm blown away by the quality of sound it outputs.  The other option is QSynth + a realistic sound font - this is a decent setup, and usually entirely free.


I use LinuxSampler for most of my piano needs.  [The packages need to be downloaded manually]("http://download.linuxsampler.org/packages/debian/"), however, as the LinuxSampler server isn't included in the repositories.  Once that's done, Qsampler can be installed from the repositories.  [The Maestro Concert Grand]("http://www.linuxsampler.org/instruments.html") giga bank is freely available for use.  Run it through a Plate 2x2 reverb in Jack Rack and it's golden.  

:)

---

### Post by thorgal on 2008-08-14
I rented a Kawai CA5 digital piano for a year. The grand piano sounds were OK but I found them a bit strange in the mids. The strength of this piano is the keyboard! simply bluffing! just read the specs if you want to know why. This piano is pricy, reason why I did not buy it. Renting it was nice and cheap. That's the best way to learn classical piano at home to my mind, unless you are the fortunate owner of a real acoustic grand piano.

For the sound, I just patched it with a software sound generator called Pianoteq. It comes in two formats : standalone app (.exe) or VSTi. In both cases, Wine works perfectly with it. The standalone app requires wineasio to work with jack. The VSTi is nicely handled by the jack compliant VST host dssi-vst (by Chris Cannam). I now have another digital piano that was given to me, much less interesting keyboard-wise but what I care about is the sound. Pianoteq is delivering so I am very satisfied :)

---

### Post by Queequeg on 2008-08-14
Fully weighted keys are a must if you intend to spend a long time playing and you are going to use the keyboard to learn some classical or jazz music, which means a lot of time at the keyboard. Not only you need the feel of resistance from the keys for your training: an unweighted keyboard could injure your fingers in the long run due to the stress that non-resistant keys may cause to them.

On jazz: you are going to need sound musical theory foundation to even have a casual go to it.

---

### Post by Peter Bell on 2008-08-14
I have always liked the idea of owning a Fatar keyboard - has always had good reviews over the years ... here is one possible : [http://www.dv247.com/invt/31181/](http://www.dv247.com/invt/31181/)

However, I have just bought myself something more akin to a real piano ... a Yamaha CLP270 - but way above your budget.  When the new house is finished, I'll have a go at using the midi interface to connect up to the computer.

---

### Post by mondoUNC on 2008-08-14
Hey Olav

I'm a music student at Uni and I'v been experimenting with Ubuntu studio and for the most part I am satisfied with what i offers. Rosegarden seems like a fantastic program for writing music (for me personally since I like to work with sheet music) and there are alot of other good programs. I really like using Ardour for recording, and Hydrogren is fun to make beats with.

As far as Midi use goes I was using a cheap casio that had midi out/in that i fed into an M-Audio FastTrack Pro (a midi to USB converter that has to 1/4" inputs for my guitars and midi). So that took care of the hardware, and the hardest thing software wise was setting up jack to use the right inputs out of the M-audio soundcard. 

Using Patchage to route midi inputs into a synth then into rosegarden is easy to do. And with all the options I don't see why you'd need to by any software (unless you want some nicer synths); Although i do love Ableton Live.

Also on picking a keyboard go to a local shop and get a feel for weighted and semi-weighted, after learning on real pianos its hard for me to play on the cheap hollow keys since i don't get the tactile feedback a real piano provides. Weighted keys give you some feeling for how hard your pressing the keys so I like it but i might not matter to you and if semi weight is cheaper then full weight it might be an easy way to cut corners for cost.

---

