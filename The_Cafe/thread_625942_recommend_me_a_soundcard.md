---
title: "recommend me a soundcard"
date: 2007-11-28
forum: The Cafe
---

### Post by bionnaki on 2007-11-28
I had an audigy 2 ZS that recently stopped working properly (intense crackling and pops in the sound on both ubuntu and windows), so I'm in the market for a new soundcard. 

I'd like something that sound amazing but yet is affordable. I was pleased with the sound on the audigy 2 ZS. Seems as though the card is no longer available. I have been looking at the [Creative Labs Sound Blaster Audigy SE](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1870098&Sku=C44-3272) but I'm not sure how this will sound compared to the audigy 2 ZS and how well supported the card is with alsa. 

Basically, I want a card that sounds amazing and pretty much works out of the box - with minimal configuration. 

have any recommendations?

---

### Post by bionnaki on 2007-11-29
well, I purchased the SE...and it sucks in Ubuntu Gutsy. Keyboard volume and control panel volume control does not work and there is no equlizar options with alsamixer - no bass, no treble, etc. I'll be returning this card ASAP unless someone knows how a fix (doubt it though - seems alsa options for this card is limited).

Any recommendations for a card that works great?

---

### Post by jrusso2 on 2007-11-29
[http://www.turtlebeach.com/products/mtgoddl/home.aspx](http://www.turtlebeach.com/products/mtgoddl/home.aspx)

---

### Post by toupeiro on 2007-11-29
> **jrusso2 said:**
> [http://www.turtlebeach.com/products/mtgoddl/home.aspx](http://www.turtlebeach.com/products/mtgoddl/home.aspx)

Whats the linux support like for this guy?  I used to be a pretty big turtle beach fan, but havent owned any of their cards since the Santa Cruz

---

### Post by regomodo on 2007-11-29
i personally wouldn't get an audigy se. I saw at efficientpc.co.uk that it has been fully supported since edgy. It isn't. I'm missing a lot of functionality and it doesn't appear i'll get it any time soon by looking at the alsa site.

---

### Post by blueturtl on 2007-11-29
I have an [M-Audio Revolution 5.1]("http://www.m-audio.com/products/en_us/Revolution51-main.html"). It's inexpensive (at least if you get one used) and kicks some serious Creative butt as far as sound quality is concerned. I used to have an Audigy2 that is supposed to be on-par with this card, but the M-Audio sounds way better. Works out of the box with Ubuntu. The only problem I've experienced is that the left channel is muted on startup due to a bug in ALSA (simply touching the volume glider will fix this though).

I cannot stress how satisfied I'm with this card. With Creative cards the sound always seemed muffled and distorted in some respect. You'd end up cranking the volume because you can't get proper detail, but soon you'd feel like cranking it back down because of the increasing distortion in the sound. This card sounds amazing at low AND high volumes.

Good luck with your hunt.

---

### Post by bionnaki on 2007-11-29
yeah, the Audigy SE is total crap and not supported by ALSA very well. I reinstalled my Audigy2 ZS and its back to the same problem - pops and crackles and static even when there is no sound playing. If you google audigy 2 and crackle, you'll see this is a common problem. apparently, it's a long-standing problem with PCI Latency - I tried the solutions that were posted but they did not work. I am considering purchasing another Audigy2 ZS because the card I had worked great for 2-3 years before I had this static trouble, although I dont want to risk running into this problem again. 

So, the M-Audio Revolution 5.1 eh? I'm familiar with their products - sounds that much better than a Creative? Are volume controls working with this card (keyboard and panel volume applet)? Does alsamixer provide an Equalizer (bass, treble, etc)? I see on this page [http://seehuhn.de/pages/revolution](http://seehuhn.de/pages/revolution) that headphone output does not work? Is this true?

And how well is the Turtle Beach Montenegro supported in Ubuntu?

thanks

---

### Post by blueturtl on 2007-11-29
> If you google audigy 2 and crackle, you'll see this is a common problem. apparently, it's a long-standing problem with PCI Latency

> I am considering purchasing another Audigy2 ZS because the card I had worked great for 2-3 years before I had this static trouble

If the problem evolved suddenly I doubt it's because of PCI latency (I mean the latency doesn't vary does it). You should check to see that the card is tightly in it's socket. Also be sure your power supply is providing stable voltages.

> So, the M-Audio Revolution 5.1 eh? I'm familiar with their products - sounds that much better than a Creative? Are volume controls working with this card (keyboard and panel volume applet)? Does alsamixer provide an Equalizer (bass, treble, etc)? I see on this page [http://seehuhn.de/pages/revolution](http://seehuhn.de/pages/revolution) that headphone output does not work? Is this true?

Well I have some fairly good speakers (the Boston Acoustics BA635) and I could tell a clear difference between the Revolution 5.1 and the Audigy 2 Platinum I used to own. The Revolution has more detail and does a better job separating things so it's sound doesn't become so hard on the ears once you turn the volume up.

The volume control applet and the mixer in Ubuntu both work without problems (although I can't tell what all those different sliders are for). I normally just use PCM and Master anyway. No separate controls for bass or tremble, but could always use the speakers own controls?

I cannot confirm about the headphone output as I don't have headphones.

I was hoping they'd fix the 'left channel mute at boot thing' by Gutsy but apparently it's still a work in progress. I expect for this problem as well as the possible headphone output to be working soon as the drivers evolve. This is a fairly well supported card, it works with Windows, OS X and Linux. I think I remember reading somewhere that the specs are open (so it's not like we're dangling for M-Audio to support us) but I can't provide a reference so I'm not sure.

If you like listening to music or watching movies it's a good card, that's all I can say.

---

### Post by bionnaki on 2007-11-29
> If the problem evolved suddenly I doubt it's because of PCI latency (I mean the latency doesn't vary does it). You should check to see that the card is tightly in it's socket. Also be sure your power supply is providing stable voltages.

the crackling did develop gradually - it started about 6 months ago and has gotten progressively worse to point where I have to mute even when there is no music or sound because the crackling and pops were too loud. I have taken the card out of its slot a dozen times and into other PCI slots and I still have the same trouble. As for stable voltages, I am not sure how to check that. voltmeter? I know that the PS has more than enough to power the card & everything else.

> Well I have some fairly good speakers (the Boston Acoustics BA635) and I could tell a clear difference between the Revolution 5.1 and the Audigy 2 Platinum I used to own. The Revolution has more detail and does a better job separating things so it's sound doesn't become so hard on the ears once you turn the volume up.

The volume control applet and the mixer in Ubuntu both work without problems (although I can't tell what all those different sliders are for). I normally just use PCM and Master anyway. No separate controls for bass or tremble, but could always use the speakers own controls?

I cannot confirm about the headphone output as I don't have headphones.

I was hoping they'd fix the 'left channel mute at boot thing' by Gutsy but apparently it's still a work in progress. I expect for this problem as well as the possible headphone output to be working soon as the drivers evolve. This is a fairly well supported card, it works with Windows, OS X and Linux. I think I remember reading somewhere that the specs are open (so it's not like we're dangling for M-Audio to support us) but I can't provide a reference so I'm not sure.

If you like listening to music or watching movies it's a good card, that's all I can say.

good to know - sounds like a card I'd want to get. thanks for the suggestion.

---

### Post by blueturtl on 2007-12-01
> the crackling did develop gradually - it started about 6 months ago and has gotten progressively worse to point where I have to mute even when there is no music or sound because the crackling and pops were too loud. I have taken the card out of its slot a dozen times and into other PCI slots and I still have the same trouble. As for stable voltages, I am not sure how to check that. voltmeter? I know that the PS has more than enough to power the card & everything else.

Sounds like something could indeed be wrong with the soundcard. Especially if you've tried other cards and they do not display the same symptoms. A quick and easy way to check voltages would be in the BIOS if your system has that functionality. I am able to see system core voltages and temperatures in the BIOS. Lot's of power supplies boast powerful wattages but don't actually measure up. If you're certain your power supply is of good quality you can probably disregard the PSU as a possible cause.

You can also check your motherboard. See that the capacitors don't bulge or look burnt. You can do that for your soundcard as well.

Finally you could try and see if muting any of the extra inputs on the soundcard has an effect. Sometimes things like Line-In, CD-in, and SPDIF while enabled add hiss and other anomalities to the signal. These are not likely to solve your problem, the symptoms you've told about suggest hardware failure (the gradual increase of crackle). Nevertheless, it doesn't hurt to rule out other possible causes.

Happy [insert your celebration for the time of year here] to you!

---

