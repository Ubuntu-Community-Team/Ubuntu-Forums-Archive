---
title: "Which Equipment Should I Get?"
date: 2008-10-24
forum: Ubuntu Studio
---

### Post by Th3Professor on 2008-10-24
I'll be building a new computer and am wondering what parts/components/etc. to get to help me with recording music.

I'd like to record music and compose music.

Is there any budget-friendly gear that works well with Ubuntu Studio?

(I will be going with 64-bit on the new computer.)

Any particular PCI?

External audio device/interface?

Mixer?

Thanks! :)

---

### Post by Th3Professor on 2008-10-25
bump

---

### Post by kayosiii on 2008-10-25
Well here goes - for audio work you want to as quite a computer as possible - having maximum performance isn't really that critical. A case with some sort of accoustic treatment can be good. Soundcard wise I have a preference for external firewire based cards - if you go this route then head over to the ffado website and see which cards are supported also if you are going to do firewire then make sure you get a system with a texas instruments firewire chipset - these perform very a lot more reliably than anything else out there. Gigabyte is one of the few mainboard manufacturers that tend to use Texas Instruments Chipsets on their mainboards but check first.

Beyond that you are going to probably want a couple of decent microphones - these can range in price from a couple of hundred to a couple of thousand dollars. Also you are going to want a decent pair of studio monitors (speakers) if you don't already.

What does your budget look like...

---

### Post by Th3Professor on 2008-10-26
> **kayosiii said:**
> Well here goes - for audio work you want to as quite a computer as possible - having maximum performance isn't really that critical. A case with some sort of accoustic treatment can be good. Soundcard wise I have a preference for external firewire based cards - if you go this route then head over to the ffado website and see which cards are supported also if you are going to do firewire then make sure you get a system with a texas instruments firewire chipset - these perform very a lot more reliably than anything else out there. Gigabyte is one of the few mainboard manufacturers that tend to use Texas Instruments Chipsets on their mainboards but check first.

Beyond that you are going to probably want a couple of decent microphones - these can range in price from a couple of hundred to a couple of thousand dollars. Also you are going to want a decent pair of studio monitors (speakers) if you don't already.

What does your budget look like...

My budget is TBA at the moment. I originally had the music-side of the budget set somewhere between $500 and $1,500, and although that is a pretty large range from low to high I am possibly going to have to restrict it to a pretty low budget (at least for this year). There's still a potential of going higher on the budget, though I'm not sure yet if I can do that, there are too many factors with my computer building process that will help determine what music gear I can currently get.

There is one potential "contradiction" in this computer that I'm building... that it is partly for gaming and partly for music production. I understand gaming comps get loud with fans running, etc., and the opposite is needed for music comps. However, someone else made a good suggestion - that I manually turn the fans down with music production and back up with gaming.

Someone else said don't get a mixer but to get separate MADI and A/D D/A devices. That's neat and all, though I'm thinking I can get all of that combined in a mixer, I just don't know what mixer covers that, at least the ad/da. The MADI, multichannel audio digital input, device is kind of a given, considering mixers are just that (although they're not PCI cards, nor are the affordable ones digital).

And someone, somewhere else, frowned upon even the thought of using an analog mixer. Wow... well, there are a lot of opinions out there but unfortunately several of them aren't the most helpful sources for reliable information. So I asked an old professor, and he has since replied with some thoughts, which have helped tremendously, though they've also sparked a lot more questions in turn.

Multiple people have said don't use firewire in Linux. Why is that?

I'm currently looking at ASUS mobos, AM2+ socket and nVidia/SLI chipset, though I'm not sure where to look for the T.I. chipset you mentioned. I have heard great things about Gigabyte motherboards. If there's a board with my socket/chipset, and with the TI chipset, then I'll definitely try to get it.

Where do I look on the board specs lists for the TI chipset?

Multiple people have also said don't use USB. I don't know why. ((( ? )))

Most have recommended connecting external devices to computer via PCI cards.

I was thinking about getting just 1 microphone, though if 2 would be a much more ideal thing, I can consider that.

Speakers/monitors... those are very expensive. I'd need a pair, though where can I get a quality pair at a good price?

I thought I'd need the following to record:

+ Instruments (I have those).
+ Microphone (1 or more), with cable(s) and boom stand(s).
+ Mixer - that can connect to computer and works in Linux. (No idea.)
+ Possibly an audio interface? (connecting mixer to computer?)
+ Sound card - probably with the appropriate inputs/outputs for
connecting with the mixer and/or other audio interfaces.
+ Correct drivers/firmware to get all of that hardware to work on the
computer.

Though I'm open to any ideas/input.

Thank you!

---

### Post by Th3Professor on 2008-10-27
bump

---

### Post by cek on 2008-10-27
Well, I'm far (far, far, far) from a music production expert, but I have done some recording in the past with some excellent results.

Software side -- it's important that you get the kernel to have as low latency as possible for recording/monitoring.  So, the -rt kernel is a must -- ubuntustudio comes with this as the default I believe.

Then jackd (qjackctl in the repos is a very nice front end), and ardour2 (pro-tools like DAW).  There are some other cool apps (like meterbridge and jack-rack) for audio manipulation (effects, etc.) through jack which I haven't really played around with much.

Hardware side -- again, you want quality with low latency.  I've been out of the game for a LONG time, but I went with an M-Audio Delta 44.  This is a really nice PCI card (works flawlessly with the IceEnvy 1712 driver in linux) with a 4in/4out breakout box.


At the time we did the recording we opted to use all external effects, so the DAW was simply recording the audio as we played -- all effects were added pre-DAW.

Doing it this way gives a VERY straight-forward setup for a musician.  You have all your effects set as you normally would, and just PLAY.

We were on a VERY tight budget, so we mic'd up everything with a set of 4 Shure SM58's.  These aren't top of the line microphones by any means, but they give good dynamic range for the cost and are VERY sturdy.

The mics went into a 12 channel ANALOG Mackie mixer where individual line levels were set -- we recorded one instrument at a time making sure to balance out the levels of the mic(s) used for the best sound quality.

The L/R outputs of the mixer were run directly to the 1/2 ins on the M-Audio interface.

The L/R outputs of the M-Audio interface were fed into an Alesis PA100 reference amplifier which fed to JBL reference monitors.

This was a VERY low budget application (especially since we already had MOST of the items, like mics and amplifiers, etc.)

---

### Post by apetay on 2008-10-27
i'm in this same situation...  the reason you don't want usb is because it's slower.  if you are trying to multi-track record, your playback of the tracks you want to play along with will be skewed, so your new track will be off by nearly half a second.  i'm still looking into firewire options, such as an analog to digital tascam firewire soundboard (search musician's friend, going for about $600).  let me know if you've made any progress, some day i'll have the finances to get this same type project off the ground.

---

### Post by cek on 2008-10-27
> **apetay said:**
> i'm in this same situation...  the reason you don't want usb is because it's slower.  if you are trying to multi-track record, your playback of the tracks you want to play along with will be skewed, so your new track will be off by nearly half a second.  i'm still looking into firewire options, such as an analog to digital tascam firewire soundboard (search musician's friend, going for about $600).  let me know if you've made any progress, some day i'll have the finances to get this same type project off the ground.

Throughput is important for latency concerns.  With the above mentioned PCI card (M-Audio) I was able to get jackd down to ~2ms latency.

---

### Post by Th3Professor on 2008-10-30
> **cek said:**
> Software side -- it's important that you get the kernel to have as low latency as possible for recording/monitoring.  So, the -rt kernel is a must -- ubuntustudio comes with this as the default I believe.

I might be using 64 Studio since I'll be running 64-bit. Though, I don't know how Ubuntu Studio runs in 64-bit. I believe that 64 Studio uses the same real time kernel though.

> **cek said:**
> Then jackd (qjackctl in the repos is a very nice front end), and ardour2 (pro-tools like DAW).  There are some other cool apps (like meterbridge and jack-rack) for audio manipulation (effects, etc.) through jack which I haven't really played around with much.

I'm running Ubuntu Studio now, and although it is a "container" for apps from all over the realm of open source, it is a pretty interesting container. All of those apps are quite impressive.

Prior to installing Ubuntu Studio I was mostly a Unix user (including BSD and SysV, specifically OpenBSD and Solaris), I used Slackware also for a while, and I've always enjoyed trying various Linux distros and Unix flavors.

I put Ubuntu Studio on the current computer so I could get a feel for it for when my new computer is built (with recording gear and all). However, I may very well use 64 Studio instead. ;) Though it's pretty close anyway. Another container for what could end up amounting to the same apps. It's pretty neat.

If I had to choose between Debian and Red Hat, I'd go for Debian without hesitation, it is very nice. Though, I am more of a Unix user and a Slacker. :) Needless to say, I will be using Linux (a "studio" variant) for my audio/music recording functions.

> **cek said:**
> Hardware side -- again, you want quality with low latency.  I've been out of the game for a LONG time, but I went with an M-Audio Delta 44.  This is a really nice PCI card (works flawlessly with the IceEnvy 1712 driver in linux) with a 4in/4out breakout box.

This is what I'm trying to figure out at present... which hardware to get.

I purchased my computer components yesterday, will be piecing my new baby together in the next week or so. I decided to put purchasing recording gear on hold until the computer is up and running and I have an improved physical understanding of what options might be ideal for recording gear with that computer.

I took a quick look at the M-Audio Delta 44, it looks pretty cool. Are those unbalanced lines for the I/O? (Not sure.)

> **cek said:**
> At the time we did the recording we opted to use all external effects, so the DAW was simply recording the audio as we played -- all effects were added pre-DAW.

That would seem like the ideal choice. There are perks to inserting effects post though if the context of the music is something meant to be easily reproduced in a live setting (such as at a concert/gig) then that'd definitely be an ideal choice.

> **cek said:**
> We were on a VERY tight budget, so we mic'd up everything with a set of 4 Shure SM58's.  These aren't top of the line microphones by any means, but they give good dynamic range for the cost and are VERY sturdy.

I had considered the SM57 but opted out and am going to get cardioid condensors instead, a couple AT2020 mics.

> **cek said:**
> The L/R outputs of the mixer were run directly to the 1/2 ins on the M-Audio interface.

So that audio interface is also an AD/DA converter? Cool beans.

> **apetay said:**
> i'm in this same situation...  the reason you don't want usb is because it's slower.

Yeah, I'll avoid USB. :)

> **apetay said:**
> i'm still looking into firewire options, such as an analog to digital tascam firewire soundboard (search musician's friend, going for about $600).  let me know if you've made any progress, some day i'll have the finances to get this same type project off the ground.

At present I'm going to stay away from firewire. Although there's ffado. Though I will most likely be going with PCI. PCIe would be nice though I'd need more PCIe slots on my mainboard. lol PCI is a solid standard anyway, so I'll try take advantage of that option.

> **cek said:**
> Throughput is important for latency concerns.  With the above mentioned PCI card (M-Audio) I was able to get jackd down to ~2ms latency.

Speaking of 2ms... the 24" monitor I purchased has that, among other goodies. :)

Is the "c" in "cek" pronounced with a "j" sound? A friend of mine goes by "Jon" but his name starts with a "c". I think that's pretty cool.

---

### Post by cek on 2008-10-30
M-Audio Delta 44 supports both balanced and unbalanced IO.  It is a AD/DA converter as well.

As for the name -- cek are just my initials  ;)

---

### Post by Th3Professor on 2008-10-30
> **cek said:**
> M-Audio Delta 44 supports both balanced and unbalanced IO.  It is a AD/DA converter as well.

As for the name -- cek are just my initials  ;)

Oh cool. lol ya never with online names... :)

That's cool that the delta 44 supports balanced and is an ad/da converter. VERY cool!

And it works fine in Linux, I'm assuming. :)

---

### Post by alienprdkt on 2008-10-30
> **Th3Professor said:**
> Oh cool. lol ya never with online names... :)

That's cool that the delta 44 supports balanced and is an ad/da converter. VERY cool!

And it works fine in Linux, I'm assuming. :)

good choice I use the [delta 1010lt]("http://www.zzounds.com/item--MDOD1010LT") ;)

---

### Post by Th3Professor on 2008-10-31
> **alienprdkt said:**
> good choice I use the [delta 1010lt]("http://www.zzounds.com/item--MDOD1010LT") ;)

That Delta 1010lt is pretty cool.

"10 in/10 out 24bit 96kHz audio card with mic preamps, digital I/O, MIDI I/O and more."

If I get two AT2020 mics (with cable/stands) it looks like they'd connect directly into that.

Is the Delta 1010lt also an A/D D/A converter (so the analog from mics would convert to digital into the computer)?

I might get that. :)

What would be an RME version of that?

I'm curious which would be more compatible with either "64 Studio" or "Ubuntu Studio 64-bit".

---

### Post by thorgal on 2008-10-31
> **Th3Professor said:**
> 
Is the Delta 1010lt also an A/D D/A converter (so the analog from mics would convert to digital into the computer)?


... uh ... isn't it the purpose of a soundcard ?

---

### Post by Th3Professor on 2008-10-31
> **thorgal said:**
> ... uh ... isn't it the purpose of a soundcard ?

I certainly hope so.

Anyway back to my main question:
What would be an RME version of the M-Audio Delta 1010lt?

---

### Post by thorgal on 2008-10-31
RME HDSP 9632 ?

[img]http://www.rme-audio.de/images/products/products_hdsp_9632_balanced.jpg[/img]
[http://www.rme-audio.de/en_products_hdsp_9632.php](http://www.rme-audio.de/en_products_hdsp_9632.php)

---

### Post by Th3Professor on 2008-10-31
> **thorgal said:**
> RME HDSP 9632 ?


[http://www.rme-audio.de/en_products_hdsp_9632.php](http://www.rme-audio.de/en_products_hdsp_9632.php)

Ah yes. It's still a bit high in the price range. ADAT won't be necessary. 16 ch. is very nice.

Is there one closer to the $200 range?

Or a device in that range that has XLR, MIDI, and 192kHz?

---

### Post by XVampireX on 2008-11-01
the RME one is not budget friendly :) Th3Professor - Try M-Audio Audiophile 192 if you need the 192kHz but are you seriously going to do professional audio on Linux? I don't suggest, there's mostly crap software (I apologize to the makers of that software, but I also apologize by not being able to use that software because it really doesn't fit my needs...) I got a little question to you though, what kind of midi controller are you going to use? If it's not a secret ;)

Oh and another thing, you might like, there's this nice M-Audio audio interface called NRV10: [http://www.m-audio.com/products/en_us/NRV10.html](http://www.m-audio.com/products/en_us/NRV10.html)

And another one you can try out which is without the mixer but it's a midi controller that looks awesome with motorized faders :) - [http://www.m-audio.com/products/en_us/ProjectMixIO.html](http://www.m-audio.com/products/en_us/ProjectMixIO.html)

AFAIK - Most if not all M-Audio products are supported on Linux.

---

### Post by Phreaker on 2008-11-02
The midi keyboards/controllers by E-Mu work out of the box

---

### Post by Th3Professor on 2008-11-14
I'm still working on a decision with gear for audio/music recording... specifically an 8 bus mixer, a PCI card with 8 XLR ins, and a MIDI keyboard.

Some updates on narrowing things down:

So far I've been unable to find an 8 bus mixer that isn't within "a few hundred dollars" price.

PCI card with 8 XLRs... I don't know, however, maybe I could use an external unit that has 8 XLR ins and allows for a digital (spdif or similar) output, with which I could use the spdif input on a PCI card... if, that is, that set-up would still allow for simultaneous recording of 8 tracks (8 mono or 4 stereo) onto the computer.

MIDI keyboard - I'm looking into getting a 4-octave one, which would fit perfect on my desk, would love to get a black one ;) though haven't found one yet that fits that bill.

---

### Post by warbread on 2008-11-17
> **XVampireX said:**
> the RME one is not budget friendly :) Th3Professor - Try M-Audio Audiophile 192 if you need the 192kHz but are you seriously going to do professional audio on Linux? I don't suggest, there's mostly crap software (I apologize to the makers of that software, but I also apologize by not being able to use that software because it really doesn't fit my needs...) 

I admit to really liking most commercial audio apps (especially Ableton), but I'd hardly call all of the Linux audio suite "crap software".  No matter what else I get, I'll love Ardour for recording instruments and Jamin for mastering.  I would love a graphical EQ in Linux- and maybe one day will have one - but most everything else I want exists in LADSPA.  ZynAddSubFX is one of my favorite synths ever.  No other drum sequencer has been as easy for me to use as Hydrogen (though the quality is pretty far removed from Session Drums, Ezdrummer and the like, but that's understandable).  I won't deny the coolness and usefulness of commercial apps, plugins and libraries, but writing off open source software as crap is just cold and wrong.  Besides, "pro quality" is more about acoustic treatment, mics and preampes, right?  Oh, not to mention talent :)

As for equipment, I should point out that just about everything in M-Audio's Axiom line is going to be wasted on Linux.  The sem-weighted keys are nice, but I could never figure out how to use the knobs and buttons effectively.  I have my eyes on a keystation 61 or 88, which should work fine.

---

### Post by Th3Professor on 2008-11-17
Any ideas on how this keyboard works in Linux?
M-Audio KeyRig 49 49-Key USB MIDI Controller

I'm thinking about sticking with 6-bus instead of 8-bus for now, the Yamaha 16x6 mixer is as close to what I want as I can get right now... though a PCI card that supports 6 XLRs?

Is there an A/D D/A converter that has 6+ XLR inputs and an SPDIF out?

If there is, I could just use the 1010LT PCI card. If I get the USB MIDI keyboard controller, I won't need the additional MIDI I/Os for that, so I could use the MIDI on the 1010LT for my electronic drumset. I could get an ADDA converter later, when I have 6+ mics, for hooking up more than 2 simultaneous tracks (only getting 2 mics for now).

Anybody have any experience with the KRK RP5G2 Rokit G2 (powered 2 way) active monitors?

At the moment I'm looking at KRK RP5G2 monitors (might go with Yamaha instead), M-Audio KeyRig 49-key MIDI USB, AT2020 mics (x2), Yamaha MB166C mixer, M-Audio Delta 1010LT PCI card, and lots of cables. Any thoughts?

---

### Post by Th3Professor on 2008-11-17
<double post>

---

### Post by ryanisablond on 2008-11-17
> **thorgal said:**
> ... uh ... isn't it the purpose of a soundcard ?

Sorry to dig up an old post, but this is a decent question that didn't get answered.

Yes, a soundcard is an A/D/A converter. But most commercial ones aren't intended for the quality demanded for recording. Recording interfaces are designed specifically for transparency and efficiency. Dedicated A/D/A boxes are even more so.

Once again, it's just another toy... I mean tool... to spend money on in the pursuit of "better tone."

---

### Post by Th3Professor on 2008-11-18
Anybody have thoughts on my recent ?s ? Thanks :)

---

### Post by warbread on 2008-11-18
> **Th3Professor said:**
> Any ideas on how this keyboard works in Linux?
M-Audio KeyRig 49 49-Key USB MIDI Controller

I'm thinking about sticking with 6-bus instead of 8-bus for now, the Yamaha 16x6 mixer is as close to what I want as I can get right now... though a PCI card that supports 6 XLRs?

Is there an A/D D/A converter that has 6+ XLR inputs and an SPDIF out?

If there is, I could just use the 1010LT PCI card. If I get the USB MIDI keyboard controller, I won't need the additional MIDI I/Os for that, so I could use the MIDI on the 1010LT for my electronic drumset. I could get an ADDA converter later, when I have 6+ mics, for hooking up more than 2 simultaneous tracks (only getting 2 mics for now).

Anybody have any experience with the KRK RP5G2 Rokit G2 (powered 2 way) active monitors?

At the moment I'm looking at KRK RP5G2 monitors (might go with Yamaha instead), M-Audio KeyRig 49-key MIDI USB, AT2020 mics (x2), Yamaha MB166C mixer, M-Audio Delta 1010LT PCI card, and lots of cables. Any thoughts?

In my experience, USB midi keyboards work fine in Linux, but I'm a little confused as to what you're planning on doing with the mixer and 6+ XLR inputs.  How are you planning to get sound from the mixer to the soundcard?  If you're going to be doing "in the box" (ITB) mixing, I suggest getting as many discrete channels of sound in as your soundcard will allow.  A mixer with 8 direct outs will let you record each mixer channel separately.

What will help you is to be very clear about what you want to accomplish.  Do you have 16 channels of instruments you want to record at once?  If you've got an e-drum set, and you're not going to be tracking a whole band, then I would look into a cheaper setup with less inputs.  The Audiophile 24/96 is half the price of the 1010LT and still has MIDI in.  If all you need is to record a guitar or two at a time, you could get by with that card and a small mixer like the [Yamaha MG102C]("http://pro-audio.musiciansfriend.com/product/Yamaha-10INPUT-STEREO-MIXER?sku=630138"), which looks like a great little mixer with pre amps (which you'll need for the AT2020's) and even compressors on channels 1 & 2.  With that, you can get two channels out to your soundcard, stereo in from the card and hook up your monitors.  

The monitors are pretty nice, but be wary of the light bass that comes from 5" cones.  As long as you're really listening to your mixes, it shouldn't be a big deal, but if you're into more bass-driven music, you might want to look into 8" speakers, like the KRK RP8.

In general, buy the best gear you can afford for what you want to do.  If you don't need more than two channels, don't buy more than that, and then put the money you saved into a FMR Really Nice Preamp, a ribbon mic or a sample library you like.

---

### Post by Th3Professor on 2008-11-18
I'd like to be able to upgrade with minimal replacements when I do upgrade. In the beginning I'll need I/Os for 2 XLRs and 2 MIDIs, though would like to be able to upgrade (without replacing components) to 8 XLRs and 4 MIDIs. I understand there are MIDI boxes ("4x4") - something like that would probably be appropriate when I upgrade the MIDI. When I get more mics I'll need to have access to XLR I/Os that allow for separate simultaneous tracks.

I'm liking that MIDI keyboard I saw, and it's nice that it's USB (especially that USB-connecting MIDI keyboards work in Linux).

I may actually swap out studio monitors for a pair that totals $100 more ($400 instead of $300 for 2 speakers). I'm considering the Yamaha speakers that I mentioned earlier.

RE: Mixer with 6+ XLRs. It's easy getting a mixer with 6+ XLR ins, it's not so easy getting a mixer with matching outs (buses, basically). There are lots of 4 and 6 -bus mixers out there, though they are not "true" 6-bus mixers, as they are usually shared, 1+2, 3+4; pan 1 to 3 or 2 to 4; that kind of thing.

RE: How am I planning on getting sound from mixer to soundcard? I'm trying to figure that out right now. I'm looking for the PCI card that is just right for my current purposes, yet ready to take on more sources as I add more in future upgrades.

RE: Mixer with 8 outs. Yes, it will let me record each channel separately, though I have yet to find a mixer under $500 that has 8 true outs.

I'm also trying to find a PCI card that can accept 8 ins (XLR).

I'm wondering if I can accomplish 8 separate but simultaneous XLRs/tracks via S/PDIF or similar. The PCI card and mixer might both have the necessary digital I/Os, though the mixer will still need to have the capability of bussing 8 true separate tracks.

RE: Being very clear with what I want to accomplish. I'd like to be able to record 8 simultaneous mic'd tracks (4 stereo or 8 mono), even if I am only starting out with 2 mics. (More mics will come later.) I would also like to be able to record 2+ MIDI instruments, even if I am only starting out with 1 MIDI instrument (drumset). (The MIDI keyboard will be USB, so that won't require a MIDI I/O.)

RE: Do I have 16 channels of instruments I want to record simultaneously?  Yes, that is, 8 stereo tracks for recording purposes with the potential of portability in live gigging, although the studio is the main focus here. I will require 8 XLRs before 16, so I could consider a mixer with 8 channels, though that would require replacing equipment when upgrading, which I am avoiding. There could even be a necessity for 16 separate (mono) tracks, a la the addition of percussion instruments.

The Roland drumkit takes care of the "mic the drums" issue.

However, I will definitely be tracking an entire band at once. I need I/Os.

I took a look at the Audiophile 24/96 and the higher-end version of it, both look nice. Though, it doesn't appear to be upgradeable without being replaced.

I actually did consider the Yamaha MG102C at one point in time. I was also looking at some Mackies at the same time. Although I was finding mixers with enough ins, none had enough true outs to achieve enough separate simultaneous tracks.

That's something that has boggled me - why mixers don't just default at the same number of busses or separate outs as they have ins. In most cases, if you wish to have  8 or 16 buses, you require a 32+ channel mixer, which is definitely more than I'm looking for.

For monitoring, I'd like to have 2 outs on the mixer, lead those to 2 ins on the PCI, lead 2 outs on the PCI to 2 ins on the mixer, then lead 2 outs from the mixer to the 2 studio monitors. Separate from that, I'd like to have 6+ (hopefully 8 ) independent outs, one per XLR/mic'd channel.

I will start with 2 mics, though will eventually have 8.

Thank you for mentioning the bass point on monitors. I had considered getting the Yamahas with subwoofer, though that's another $400 just for the sub. The Yamahas I'm looking at are, I believe,  a little larger in diameter than the KRKs that I recently listed. I'll have to double-check that. Though, I will also consider the 8" KRKs (and other 8"s) like you mentioned. That could save me a pretty penny, letting me avoid a sub.

My original idea was to drop $500 on recording gear, though I'm considering pushing that up to $1000 to $2000 for my "starting" set-up.

Music is my profession, I'm just hoping I make the appropriate decisions suitable for what I'm wanting out of my recording. ;)

(note: by "upgrade" recording gear I mean "add" gear, so I don't technically replace things.)

---

### Post by Th3Professor on 2008-11-20
In any case, I'm meeting with a colleague at a professional recording studio tomorrow... should get some certified advice there. ;)

---

