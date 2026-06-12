---
title: "Guitar / bass interfaces with Linux (Rosegarden, Ardour)"
date: 2008-05-26
forum: Ubuntu Studio
---

### Post by das letzte einhorn on 2008-05-26
I have downgraded my X-FI to an Audigy 2, and now sound in Linux works. The next step for me is to purchase recording hardware which I could use with Rosegarden and Ardour to record mostly guitar, bass and voice lines. Originally I was thinking about the M-Audio firewire Solo module ([http://www.m-audio.com/products/en_us/FireWireSolo-main.html](http://www.m-audio.com/products/en_us/FireWireSolo-main.html)), but I have not found yet if it is still compatible with ALSA ([http://www.alsa-project.org/main/index.php/Matrix:Vendor-MAudio](http://www.alsa-project.org/main/index.php/Matrix:Vendor-MAudio)). I was wondering if any other musicians here have suggestions of hardware to purchase. I am looking for quality vs price, and I am ready to spend about 200-250$.

Thanks!

---

### Post by dspiteri on 2008-05-26
> **das letzte einhorn said:**
> The next step for me is to purchase recording hardware which I could use with Rosegarden and Ardour to record mostly guitar, bass and voice lines. Originally I was thinking about the M-Audio firewire Solo module

The Firewire Solo would be the perfect candidate, but the support is not there yet. It works fine but you need a windows installation handy to set the internal mixer and none of these firewire interfaces work with ALSA. A cheap alternative is possibly the Audiophile 2496 and an outboard preamp or desk-mixer.

---

### Post by SynthesizersFTW on 2008-05-26
> A cheap alternative is possibly the Audiophile 2496 and an outboard preamp or desk-mixer.

That's exactly what I was doing for years with an original Creative Audigy for scratch demos, since I rarely did anything more than track-at-a-time.  Get yourself an inexpensive tabletop mixer (8 channels is overkill for what you're going to use it for) and the right cables/adapters (I used a 1/4"-to-RCA DJ cable with a stereo RCA-to-1/8" y-adapter to connect the main outs to the line in) and you'll do fine.  Just make sure your individual tracks are at the right level (and relatively noise-free, watch out for grounding problems and AC-related hum) and your mixes will be more than passable.

The upside on the mini-mixer is that you can leave things plugged in continuously, it eliminates a lot of downtime.

Some relevant links to find compatible hardware below, if you're not satisfied with the Audigy:

[ALSA's compatibilty matrix]("http://www.alsa-project.org/main/index.php/Matrix:Main")
[URL="http://www.ffado.org/?q=devicesupport/list"]
FFADO (formerly FreeBoB) firewire driver devices[/URL]

Good luck!

---

### Post by robeast on 2008-05-27
I wouldn't recommend getting a mixer. You may as well get an interface with many inputs for around the same price as a mixer and then you can record tracks simultaneously and be able to mix them down in software later. I think it's much more flexible this way and at the same cost. 

Check the Linux Studio Pro link in my sig for a long list of (almost) all the officially supported audio interfaces out there.

---

### Post by das letzte einhorn on 2008-05-27
> **robeast said:**
> I wouldn't recommend getting a mixer. You may as well get an interface with many inputs for around the same price as a mixer and then you can record tracks simultaneously and be able to mix them down in software later. I think it's much more flexible this way and at the same cost. 

Check the Linux Studio Pro link in my sig for a long list of (almost) all the officially supported audio interfaces out there.

In the studio link you have, the M-Audio Firewire Solo module is listed as linux compatible with FreeBoB (FFADO). On the FFADO website however, it says "reported to work", not "supported". Should I feel confident with this information or I should wait until the status becomes "supported"? That would be the module I aim for, though I am not closed to alternatives.

---

### Post by robeast on 2008-05-27
Check this out:
[http://freebob.sourceforge.net/index.php/List_of_Supported_Devices](http://freebob.sourceforge.net/index.php/List_of_Supported_Devices)

It says that the FireWire Solo is supported by the freebob driver, of which ffado is the child. I don't know why they would have it as reported to work with ffado, since I would assume that whatever is supported by freebob is also supported by ffado. Possibly they haven't had one to test with ffado yet and simply assume that it should work? 

My site does not list ffado-only devices because ffado is not officially released yet--you would have to compile it from source to use it--not a big deal, but you could be in for some nasty surprises using pre-released drivers! 

As a side note, the devs also don't want to give support for code they haven't declared stable yet. However, they would appreciate thorough bug reports if you decide to try them ;)

Here's a link from my resources section that gives an example of jack settings that work well with the FWSolo: (it's a little ways down the page)
[http://westcoastsuccess.wordpress.com/2008/03/23/m-audio-firewire-solo-ubuntu/](http://westcoastsuccess.wordpress.com/2008/03/23/m-audio-firewire-solo-ubuntu/)

I think you can buy this interface with confidence! If you do buy one, leave a comment on my site about your experience.

---

### Post by das letzte einhorn on 2008-05-27
Ok then, I shall look into that. I have installed the Ubuntu Studio upgrade, therefore the support should be maximal. Where do I report bugs? Is this with Launchpad or another dedicated website?

Thanks for your help :)

EDIT: One last question, do you know if there is a way to activate 5.1 sound in Ubuntu? I have googled, and what I have found so far is that 2.1 sound is the latest sound available. But since you told me that there is a way to make the Firewire Solo work while originally I did not found anything about it, I am wondering if the same rhetoric could be applied to 5.1 sound..!

---

### Post by SynthesizersFTW on 2008-05-28
> **robeast said:**
> I wouldn't recommend getting a mixer. You may as well get an interface with many inputs for around the same price as a mixer and then you can record tracks simultaneously and be able to mix them down in software later. I think it's much more flexible this way and at the same cost. 

I respectfully disagree...  
It boils down to 1) how you work, and 2) bang for the buck - price check: A Delta 1010 is still around $500 US, Firewire MOTU 828mkII's are even higher.  In the $200-250 price range, the interfaces are either 2 ins / 2-4 outs over Firewire, or a snake connected to a PCI card (e.g., 1010LT, which is great).  You just don't get that many inputs over Firewire at that price point.  Firewire is a basically just a frill unless you're mobile.

Here's the rationale: A typical home recording setup only needs more than 2 channels at a time if you're doing live drums, no mention of that.  The poster wanted something to do guitar or bass, presumably solo track-at-a-time recording, and with Behringer mixers starting at under $80 for 8-channel/2-XLR ins, you still have money to buy some monitors, good headphones, or more importantly, a half-decent mic.  Bass direct is fine, but guitars sound pretty fake unless you mic a cab/acoustic.  If the mixer has direct outs on each channel, all the better:  No worries about zero-latency monitoring in software, just route the direct outs to the soundcard and mains to the monitors and dedicate one stereo channel for the soundcard output coming back.  It's a lot easier to turn a trim knob on hardware than to keep clicking around to get levels right.  I've found this works much faster than constantly adjusting controls in software - I still do this with my 828.  Everything stays connected, no downtime - faders pretty much at unity, pot up or down, off you go. 

I'd recommend not throwing your whole budget at an overpowered interface (most of the features, in my experience, go completely unused).  I might really sound like a fogey stuck in analog-land (good analog sound is what really counts; that's why people shell out for Apogee converters), but the point I'm arguing is that it's all about how you use what you've got.

Peace

---

### Post by thorgal on 2008-05-28
just make sure your mixer does not introduce too much noise, and the quality of the preamps is at least decent. A mixer can easily degrade the sound if not chosen properly.

---

### Post by das letzte einhorn on 2008-05-28
> **SynthesizersFTW said:**
> I respectfully disagree...  
It boils down to 1) how you work, and 2) bang for the buck - price check: A Delta 1010 is still around $500 US, Firewire MOTU 828mkII's are even higher.  In the $200-250 price range, the interfaces are either 2 ins / 2-4 outs over Firewire, or a snake connected to a PCI card (e.g., 1010LT, which is great).  You just don't get that many inputs over Firewire at that price point.  Firewire is a basically just a frill unless you're mobile.

Here's the rationale: A typical home recording setup only needs more than 2 channels at a time if you're doing live drums, no mention of that.  The poster wanted something to do guitar or bass, presumably solo track-at-a-time recording, and with Behringer mixers starting at under $80 for 8-channel/2-XLR ins, you still have money to buy some monitors, good headphones, or more importantly, a half-decent mic.  Bass direct is fine, but guitars sound pretty fake unless you mic a cab/acoustic.  If the mixer has direct outs on each channel, all the better:  No worries about zero-latency monitoring in software, just route the direct outs to the soundcard and mains to the monitors and dedicate one stereo channel for the soundcard output coming back.  It's a lot easier to turn a trim knob on hardware than to keep clicking around to get levels right.  I've found this works much faster than constantly adjusting controls in software - I still do this with my 828.  Everything stays connected, no downtime - faders pretty much at unity, pot up or down, off you go. 

I'd recommend not throwing your whole budget at an overpowered interface (most of the features, in my experience, go completely unused).  I might really sound like a fogey stuck in analog-land (good analog sound is what really counts; that's why people shell out for Apogee converters), but the point I'm arguing is that it's all about how you use what you've got.

Peace

Right now what I would like to do is to create demos of what I do and record my improvisations in order to make the writing process easier. I have been referred to the firewire solo by one of my friends, which uses one to record his tracks. I am definitely not to the same level than him in terms of recording experiences however, therefore anything cheaper in price/Linux compatible/efficient in sound will be perfect.

If you could provide me a quick tutorial in terms of setting the device and the computer together once I purchase your recommendations (Behringer again?), it would be greatly appreciated :)

---

### Post by SynthesizersFTW on 2008-05-28
There's a wide variety of mixers at that price range, but to keep costs down I do recommend Behringer (basically, German reverse-engineed and Chinese-assembled Mackie clones).  A quick look online yields:

[http://www.zzounds.com/cat--Behringer-Mixers--2950]("http://www.zzounds.com/cat--Behringer-Mixers--2950")

The XENYX 802 or 1204 would do fine.  Can't say I can recommend the 502 in terms of features.

If your Audigy is working ok already, you'll have no problem routing with the cables and adapters I mentioned in the previous post.  Monitor speakers are also a frill, good headphones will also work just fine.  It wouldn't be any trouble for me to sketch out a diagram of how to hook everything up if you need help.  Are you using the Audigy2 NX USB box or the vanilla card?  I think in either case your ins/outs are going to be 1/8" female stereo, thus the need for the Y-adapters.

---

### Post by das letzte einhorn on 2008-05-29
I am not sure what the vanilla card is, but what I have is a SB Audigy 2 PCI card. Are these two terms the same? The outputs of the card are indeed 1/8.

I will be probably looking for the 802 instead, not only because it is cheaper, but also because I have a POD module for the effects already. I might also use a program on the computer (if I can find a linux alternative to GuitarRig) to create other effects.

I will also be upgrading my speaker set soon because they began to screech a little while ago. I am just finishing using them until I find a suitable deal for larger speakers which can handle guitar/bass sound. I definitely have some budget, but I want to spend wisely; according to my actual ambitions.

---

### Post by Drunky on 2008-05-29
I've never use GuitarRig, but [Jack Rack]("http://jack-rack.sourceforge.net/"), [Creox]("http://zyzstar.kosoru.com/?creox") and [Rakarrack]("http://rakarrack.sourceforge.net/") all allow you to add effects (e.g. distortion, flanger, reverb) to your guitar sound.

I hope you find this useful.

---

### Post by robeast on 2008-05-29
> **SynthesizersFTW said:**
> I respectfully disagree...  

Good breakdown, I didn't realize that mixers were so cheap! Looks like a good option if you are on a very tight budget--or if you don't want to go into debt like me ;)

I bought a Presonus Firepod last summer and have only used 4 channels simultaneously so far (out of 8 mic/line). However, I bought this interface with intentions of eventually recording drums, setting up some crazy signal chains in and out of my computer and generally experimenting. What I really need now is a patch bay so I don't have to fumble around behind the thing all the time.

---

### Post by warbread on 2008-05-30
Just to throw in my two cents, I started with a humble [Alesis multimix8]("http://www.musiciansfriend.com/product/Alesis-MultiMix-8USB-Mixer-with-USB-and-DSP?sku=630166") and an[ M-Audio 24/96]("http://www.musiciansfriend.com/product/MAudio-Audiophile-2496-PCI-Digital-Audio-Card?sku=701341").  I highly suggest the M-Audio card, which can be found on eBay for cheaper, but be careful with the Alesis.  My microphone preamp just blew and I've only had it for 6 months!

---

