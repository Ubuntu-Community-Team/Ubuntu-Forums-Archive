---
title: "recording noob - want to record electric guitar"
date: 2010-10-01
forum: Ubuntu Studio
---

### Post by borderblu on 2010-10-01
Hi all,

I am totally new to recording electric guitar. I'd just like an affordable solution that lets me plug in to my dv6000 laptop from my amp, and listen with headphones on. Suggestions?

---

### Post by cchhrriiss121212 on 2010-10-02
There are a few ways to do this. 
If you want to connect your amp directly then you will need an amp with a line out socket, does yours have one? Connecting from the speaker output is not a good idea.
You could also use a mic to record your amp, which means you will need to buy a preamp and mic.
Or you could plug guitar straight into a preamp for a cleaner sound.
 
I'd recommend a USB recording device like the[ UA-25EX]("http://www.roland.com/products/en/UA-25EX/index.html") which is fully supported. It will allow you to use all sort of programs (multitrack recording, FX etc.) with low latency. 

Or, if you want something cheaper, a guitar OD/distortion pedal (I assume you already have one) can double as a usable preamp. All you need then is a 1/4' jack to 1/8' jack cable, which are easily found on eBay.

---

### Post by sgx on 2010-10-02
> **borderblu said:**
> Hi all,

I am totally new to recording electric guitar. I'd just like an affordable solution that lets me plug in to my dv6000 laptop from my amp, and listen with headphones on. Suggestions?
A brand new product is out, the Fender Mustang 1 digital amplifier,
at $99 it is ultra no-brainer. Check it on youtube. There are a dozen or more videos. The MusicRadar vid best shows the range of sound.
Cheers

---

### Post by borderblu on 2010-10-02
Hey, thanks for the reply.

My amp is a Line 6 spider III 30-watt amp that has a 1/4 female plug that reads "phones/Record out" where I plug in my phones. Is that what I need for getting a dual splitter with a 1/4 to 1/8 adaptor connected and recording (with headphones so I can hear)?? I'm not a big effects person, altho I play around with the built-in distortion that comes with the amp - I don't have any pedals or addons, just the amp and guitar.

So the edirol UA-25EX plugs in via usb? Does Studio Ubuntu 10.04 detect it at present, or is there a lot of configuration. Could I expect a cleaner sound from it (sorry, really have no experience with a recording equip :P)?  Would the edirol allow me to adjust the recording and headphones volume indepently?

---

### Post by borderblu on 2010-10-02
@sgx

Thanks for the reply sgx - I'll check out the tips on that product.

-borderblu

---

### Post by Pablo_F on 2010-10-02
Hi, 

I use a [Behringer UCA202]("http://www.behringer.com/EN/Products/UCA202.aspx") in my netbook which does what you want but no more than that. Well, you will have a spare input. It is not a pro thing though. It has no preamps but it should be enough. You will need a 1/4 jack to RCA male cable, or a jack 1/4 female to RCA male adapter, for the input.

As Chris suggested (but I don't think you need a distortion pedal) you can just connect your amp to the onboard audio device, but that can be very tricky to setup and probably bad quality.

As for the support in Linux, both the Edirol and the UCA202 are supported and they work out of the box... kind of.

You will need the jack server up and running (qjackctl is the graphical frontend you should use), with the alsa driver, in realtime mode and probably some software tweaks to avoid xruns.

I strongly recommend rakarrack for a bit of signal processing and ardour as a multitrack recorder. 

Cheers! Pablo

---

### Post by cchhrriiss121212 on 2010-10-02
> **borderblu said:**
> Hey, thanks for the reply.

My amp is a Line 6 spider III 30-watt amp that has a 1/4 female plug that reads "phones/Record out" where I plug in my phones. Is that what I need for getting a dual splitter with a 1/4 to 1/8 adaptor connected and recording (with headphones so I can hear)?? I'm not a big effects person, altho I play around with the built-in distortion that comes with the amp - I don't have any pedals or addons, just the amp and guitar.

So the edirol UA-25EX plugs in via usb? Does Studio Ubuntu 10.04 detect it at present, or is there a lot of configuration. Could I expect a cleaner sound from it (sorry, really have no experience with a recording equip :P)?  Would the edirol allow me to adjust the recording and headphones volume indepently?
If you have a line out then all you need is the right cable.

What you should invest in depends on what your goals are:
Do you just want to record a few ideas with no FX? Use the line-out from your amp and Audacity to record.
Do you want to get into recording multitrack songs with additional instruments? Look into a dedicated soundcard which will give you good quality and latency. Then use jack and Arodur as recording software.

In both cases you will be able to adjust monitoring volume through software.

I don't own the edirol card, but it should be easy to set up. Buying the right hardware is the easy part, using software will be the hard part.

---

### Post by borderblu on 2010-10-02
To let you guys know what I'm doing. I have an album's worth of original acoustic and electric compositions. Originally I was just going to record it as an all acoustic album, but really some pieces where composed on and are meant to be played on electric. The songs are all self-contained, composed to be performed solo, I don't need to add effects, I just need to be able to faithfully record what I'm hearing, preferably at as high a quality (for as little money) as possible. Anyway, thanks for all the input - much appreciated, I think I have a better grasp of the process.

-Borderblu

---

### Post by RaumTrug on 2010-10-02
why don't you just plug the "record out" to the "line in" (if your computer has one...) with a good cable (I hope the plug on the amp is stereo...it should, if it works for headphones). take care with the output levels from the amp, and the input amplification of your pc.
maybe you'll want to get jack up running (in realtime mode), and then use audacity, or better ardour to record what you play. the jack server kind of assures that the signal quality is as good as possible with the soundcard you're running on: no resampling, no gaps (if in realtime-mode), etc...highly recommended!
play around with the "alsamixer"-tool to get a direct passthrough of your guitar input to the headphones of your pc. that way you won't even have to tune your jack-latency to the minimum, as long as you don't want to listen to your sound with digital fx from your computer in realtime. plus you can playback some "backing track" in parrallel, and record the guitar without it. just use some audio-player that can output via jack, and don't connect it's out to the recording-program's input (just plug the "capture" in there).

as said, be a little careful with the input/output levels of the connection amp->line-in, first set both very low, and then turn up slowly amp&capture-amplification to get the level without clipping and not having distortion because the amp's signal is "to hot" for the soundchip. "jack meterbridge" is a nice tool to check the levels of the signal while using jack. in alsamixer the "output" to the headphone can be ruled to your ears' needs. in alsamixer, input amplification is ruled in the "capture"-tab ("f4"-key I think) and amplification of that to the headphone in the "playback"-tab ("f3"-key). if you're in bad luck, the alsa-driver of your soundchip won't work properly in those regards :(. also many drivers work differently, but in output-tab you generally rule amplification to sound-output (speakers, headphones), and in capture-tab you normally rule by how much the input-signal is amplified before passed to the output, or it is recorded (and sometimes you have to select the right source of input in alsamixer, too).

for first experiments, you won't need to buy an extra guitar-effects box or sound interface, I'd say; onboard pc soundchips aren't "best quality", but not the worst either...if you're "lucky", have a line-in, and 48k 16bit are enough for you, you'll be fine.

also it needs to be said, the whole jack audio world in linux needs a little of "digging in" first, so you better search the web for tutorials on jack, ardour, audacity or whatever you're using to record your songs. those programs aren't as simple to set up and use as many windows progs are.

I wish you good luck; let your fingers fly, and your guitar shine like your face would shine if it reflected your musical phantasies. peace!

---

### Post by borderblu on 2010-10-03
@RaumTrug

thanks for the reply, I'm going and the good wishes, I think I'll see what I can do with a simple cable first. 

cheers,
Borderblu

---

### Post by sgx on 2010-10-03
> **borderblu said:**
> @RaumTrug

thanks for the reply, I'm going and the good wishes, I think I'll see what I can do with a simple cable first. 

cheers,
Borderblu
I have also a Spider III, and you can set a clean tone, and send that from the headphone out to the computer line in, and use rakarrack on that line in, for fx. Autostatic has V6.x in his PPA. The volumes vary wildly in some rakarrack presets, but you can change permissions on /usr/share/rakarrack, and save the bank as Default.rkb after you have set proper volumes. Its a great powerhouse multi-fx for guitar. Worth spending mmany hours with. It has an excellent built-in help section.
Cheers

---

