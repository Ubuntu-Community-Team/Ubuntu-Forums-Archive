---
title: "Anyone got an opinion on LinuxDSP plugins?"
date: 2012-10-17
forum: Ubuntu Studio
---

### Post by Sylos on 2012-10-17
Hello all.

Like many amatuer musicians I feel my sound sucks! (at least I hope its not just me [-o< ).

To be precise, its mainly my guitar sound that sucks. I have an old Yamaha Pacifica guitar running through a Marshall VS100 combo amp with an SM57 shoved in front for close mic recording. And it sounds awful, seemingly regardless of what I do to it.

None of the equipment I use is ideal for recording a sweet guitar sound but the fact is I cant afford to upgrade most of it. But I was wondering whether the Linux DSP plugins could make a difference. So the question is: does anyone have an opinion on whether these are better than the free plugins offering similar functionality? I currently use things like the TAP EQ and SC4 Mono compressor - sometimes the calf compressor. Just wondered if there is a discernible difference.

PS: I know garbage in is grabage out so I dont expect any plugin to suddenly make me sound like the ghost of Hendrix.

Cheers

---

### Post by CrocoDuck on 2012-10-18
Hi. In my experience I found that the chain before the computer's audio device is decisive. I'm usually work with one of those two setups:

Guitar directly plugged in a DI box plugged in a mixer, that is plugged to the audio device.

Guitar plugged into the amplifier, then the sound is cought by a condenser microphone (plugged in the same mixer used  above).

The goal of those chains is simple: they have to be as linear as possible. In other words: a chain is good if the sound that it pass to the soundcard is very close to the sound you hear. Fidelty is the key. Using plugins is very effective, but we can drive the sound where we want only if we have a good chain (that doesn't filter and distort the signal without our control). I'm usually use Guitarix, Rakarrack, Calf, TAL plugins.

Condenser microphones are good for this goal, even if we speak about the cheap ones, becouse  the technology with which they are made. Remeber that the sound you hear after recording (or throught your monitors while playing) depends strongly on monitors and room shape, so have a try by listening your recordings in another set of monitors, sterero, mp3 player etc.. etc...

Here the mics and monitors I use, I think they are a good compromise:

[http://www.behringer.com/EN/Products/C-2.aspx](http://www.behringer.com/EN/Products/C-2.aspx)
"Monitors" (better than computer speakers): Empire S600

At last, something we don't want could be introduced by the soundcard (noise, slew rate of preamplifiers, other sources of distortion and bad quality conversion are common in the input stage of integrated soundcards and those things can change very deeply the sound).

---

### Post by Sylos on 2012-10-18
Thanks for the input Corcoduck.

Isnt using a condensor mic to capture a guitar amp dangerous? I always though it was too sensitive for close micing an amp and could break the diaphram (or whatever the hell a condensor uses).

I have my amp in an isolation box so I can get some drive out of it. That would make the pressure in there too much for a condensor (unless someone wants to correct me on that).

As for monitors - I dont actually have any. Due to space, money and (most importantly) girlfriend constraints I actually have to do everything on headphones (I know - its a terrible way to mix). When Im getting halfway near a decent mix I then play it through my stereo and burn it to CD to play in the car. If it sounds good in the car it will sound good on most things I reckon. Sadly it never seems to.

I supposed some more fiddling with things is in order. It does seem like Im trying to polish a turd most of the time. I've tried going straight in and then using Guitarix, Rackarrack etc but the distortions always seem a bit fuzzy for my liking. 

Even if it isnt the way forward for my problem, I'd still be interested to see if people think the Linux DSP plugins are better than the free plugins available.

Cheers

---

### Post by CrocoDuck on 2012-10-18
OUPS... forgot to speak about it... I've tried some free demo of LinuxDSP and Loomer Plugins ([http://www.loomer.co.uk/index.htm](http://www.loomer.co.uk/index.htm)). I think they are very interesting and good! Dunno if better than free and opensource... I'm fine with free so I'm not thinking about them a lot. I reccomend you to try the demos and purchase them only if they fits your needing. In my personal opinion, investing money for software is a good thing, if you invested in hardware the right amount that you want to invest in order to have a good capture quality: even if we consider good ones, plugins can't rebuild your sound from scratch. Always in my personal opinion: the studio has to be designed in order to capture the musician's performance as close as possible as they played it (digital effects and plugins can be both a part of your sound, as I do with guitarix, and a tool to make your records sound right).

As you said, condenser mics have to be used carefully (expecially into isolation boxes), but they can be used almost for everything. Refer to the manual to know about their working parameters and warnings. In my home studio I have small volumes from the amplifier (that is a small 15W), but I used a Samson C03 condenser mic on stage too, capturing my Peavy Blues Classic.

---

### Post by sgx on 2012-10-18
The $110 Fender Mustang 1 usb amp/interface works flawlessly in
linux, records noise free by usb or line-in, has three banks
of 8 sounds each on one dial, and a linux editor is available
to create/modify sounds. 

[http://www.youtube.com/watch?v=Wl2Q8SNVnPU](http://www.youtube.com/watch?v=Wl2Q8SNVnPU)

[http://www.musiciansfriend.com/amplifiers-effects/fender-mustang-i-20w-1x8-guitar-combo-amp](http://www.musiciansfriend.com/amplifiers-effects/fender-mustang-i-20w-1x8-guitar-combo-amp)

[http://piorekf.org/plug/](http://piorekf.org/plug/)

Sounds great using Guitarix2 and Rakarrack, cal/invada plugins etc.
The Linux DSP plugins you mention are also excellent.
:guitar:

---

### Post by Sylos on 2012-10-19
Corocoduck - seems like there isnt a massive difference between the free plugins and those offered through linuxDSP then. I had a feeling it might be the case. I may still buy them in the end (it seems like a good way to support linux audio - if people pay for software it might encourage other software companies to make their programes available on linux). As I said in my OP - garbage in is garbage out and it seems my problem solution is likely to be found in sorting out my signal at source.

sgx - I hope fender are paying you commission - seems the mustang usb interface is your most frequent recomendation :) As I cant really afford the money (or space) for any more equipment for now I shall have to go back to fiddling with the mic position and amp settings. Anyone got any recomendations on how to get a nice death metal sound? So far I've scooped out a lot of the middle, boosted the bass up a bit and left a reasonable amount of high end on it. The SM57 is about an inch away from the mesh over the speaker and pointing head on near the edge of the cone (pretty standard I imagine). May try angling the mic and seeing what that does.

Cheers

---

### Post by CrocoDuck on 2012-10-19
> **Sylos said:**
> Corocoduck - seems like there isnt a massive difference between the free plugins and those offered through linuxDSP then. I had a feeling it might be the case. I may still buy them in the end (it seems like a good way to support linux audio - if people pay for software it might encourage other software companies to make their programes available on linux). As I said in my OP - garbage in is garbage out and it seems my problem solution is likely to be found in sorting out my signal at source.

sgx - I hope fender are paying you commission - seems the mustang usb interface is your most frequent recomendation :) As I cant really afford the money (or space) for any more equipment for now I shall have to go back to fiddling with the mic position and amp settings. Anyone got any recomendations on how to get a nice death metal sound? So far I've scooped out a lot of the middle, boosted the bass up a bit and left a reasonable amount of high end on it. The SM57 is about an inch away from the mesh over the speaker and pointing head on near the edge of the cone (pretty standard I imagine). May try angling the mic and seeing what that does.

Cheers

AWW YEAH! Keep on experimenting with mic position, I'm sure it will be effective: sm57 is a good mic! I'm usually play with the mic close to the cone, on it's axis. On the cone's axis the wavefronts of each wave that, with their frequencies, compose the sound are basically parallel, so the capture of the mic is "democratic", as a condenser mic has a good flat frequencies response. If we put the mic close to the cone's border we'll start to cutoff hight frequencies.

So I suggest you to put your mic on the cone's axis and test a clean sound with the amplifer flat-equalized. Acting like this we'll find how much your mic affects the tone of the sound. Then you'll be able to adjust an equalizer (maybe a plugin) in order to restore the natural sound. How about the other stuff in the chain (mixer, audio device)?

---

### Post by offgridguy on 2012-10-19
Interesting stuff, one thing the sm57 is not a good mic. it is a great mic. :P

---

### Post by offgridguy on 2012-10-19
> **Sylos said:**
> 

PS: I know garbage in is grabage out so I dont expect any plugin to suddenly make me sound like the ghost of Hendrix.

Cheers

Most musicians want to record themselves at some point in time.  you obviously understand, you will only sound as good as you are.  I would suggest treating your
 guitar/amp setup like an acoustic rig,  set up and record yourself in as simple a setting as possible, ie; mic your amp,use a reasonable volume, not ear splitting levels.
Play whatever you are comfortable with, for as long as possible , 1/2 hr or more
record everything, ignore the mistakes, ideally play until you forget you are recording.
Play it back and listen. don't be overly critical, just be honest with yourself.  You may
be very pleased with the results, you may say I have got a lot of woodsheding to do.

Best wishes to you. :guitar:

---

### Post by sgx on 2012-10-19
> **Sylos said:**
> 
sgx - I hope fender are paying you commission - seems the mustang usb interface is your most frequent recomendation :) As I cant really afford the money (or space) 
You would do well to sell the Marshall, mic, and cables,
and buy the Mustang. Coupled with Guitarix2, and Rakarrack,
the Mustang is spectacular. Record at 2AM, while neighbors
slumber in peace
:guitar:
In addition to the 12 amp models and array of fx in the Mustang,
it also includes Amplitube Fender LE, which provides 3 amp models,
a Fender Twin Reverb, SuperSonic, and Metalhead 500 amp,
and these can be added to Amplitube 3.9 Custom Shop version,
giving you modeled mics and positioning,
among the 27 free Amplitube gear models,
that work quite nicely using wine/wineasio.

Here is another free alternative, nicely excellent in wineasio.

[http://www.native-instruments.com/#/en/products/producer/guitar-rig-5-player/](http://www.native-instruments.com/#/en/products/producer/guitar-rig-5-player/)

There are also Behringer usb guitar interfaces at $20
to use with linux and wine based amp/fx software

[http://www.amazon.com/Guitar-Interface-Computer-Recording-Adapter/dp/B0048F0QWA/ref=sr_1_11?s=musical-instruments&ie=UTF8&qid=1350686932&sr=1-11&keywords=behringer+interface+usb](http://www.amazon.com/Guitar-Interface-Computer-Recording-Adapter/dp/B0048F0QWA/ref=sr_1_11?s=musical-instruments&ie=UTF8&qid=1350686932&sr=1-11&keywords=behringer+interface+usb)

Cheers

---

### Post by CrocoDuck on 2012-10-20
> **offgridguy said:**
> Most musicians want to record themselves at some point in time.  you obviously understand, you will only sound as good as you are.  I would suggest treating your
 guitar/amp setup like an acoustic rig,  set up and record yourself in as simple a setting as possible, ie; mic your amp,use a reasonable volume, not ear splitting levels.
Play whatever you are comfortable with, for as long as possible , 1/2 hr or more
record everything, ignore the mistakes, ideally play until you forget you are recording.
Play it back and listen. don't be overly critical, just be honest with yourself.  You may
be very pleased with the results, you may say I have got a lot of woodsheding to do.

Best wishes to you. :guitar:
\\:D/Very good advice: my guitar teacher was usually recomend to always record when playing and practicing, is the best way to understand what we do with our hands and mind. Before the gears there are always hands (and acting like this you will really improve them). I don't want to say that you probably suck : I'm sure  that you are a good guitarist, with a good hand (I'm still wondering on hardware issues that could ruin your sound, like unmatched impedances in the chain). Is just an advice.

P.S.: your gear is not so bad... You'll find the right sound, and starting from a simple setting is a good idea to understand how to do it.

---

### Post by offgridguy on 2012-10-20
> **CrocoDuck said:**
> \\:D/Very good advice: my guitar teacher was usually recomend to always record when playing and practicing, is the best way to understand what we do with our hands and mind. Before the gears there are always hands (and acting like this you will really improve them). I don't want to say that you probably suck : I'm sure  that you are a good guitarist, with a good hand (I'm still wondering on hardware issues that could ruin your sound, like unmatched impedances in the chain). Is just an advice.

P.S.: your gear is not so bad... You'll find the right sound, and starting from a simple setting is a good idea to understand how to do it.

To expand a bit on what i posted before, although I did not directly address the issue 
of hardware and it's effect on sound,   I have known people who have spent lots of $$$$
on recording equipment, most of which sits in a dusty basement corner unused because
they were simply not capable of playing well, and no equipment can change that.
Conversely I have heard beautiful music that was recorded on a casette tape deck sitting on a kitchen table.  The difference - talent .
I work  hard at developing that , the recording can wait until the product is the result
of talent, not equipment.  Music stores love guitar players, they spend a lot of $$$
on equipment.  Thank you for the reply, and keep on "pickin". :P

---

### Post by Sylos on 2012-10-20
SGX - whilst Im sure you are right about the Fender mustang input box being better than my setup for recording it unfortunately doesnt have the multi use of my current gear (amp can be used live and mic doubles for my vocal work as well as recording the guitar). I dont want to seem like Im ignoring your advice (because I know its good advice) but it doesnt serve my purposes at the moment. 

> **CrocoDuck said:**
>  I don't want to say that you probably suck : I'm sure  that you are a good guitarist,


Nah - you were right the first time - I do suck as a guitarist. I know it. I'm not one of those people who was born really gifted with the guitar and frankly, I dont get enough practice. Add to that the fact that I have a liking for death metal etc (so very fast picking, quick left hand finger work required etc) and it's a recipe for a lame sounding recording. I recently bought myself a metronome to practice with as trying to record to a drum track showed me how bad my timing was. My belief is thus "a great guitarist can make bad gear sound good, but great gear cant make a bad guitarist sound good" - its a universal constant!

That being said, my current problem (the one I was originally trying to remedy) is to do with the sound of my guitar - not my playing (as far as I can tell). The guitar sounds muddy, thin and chainsawey and generally just horrible. The fact that I then make an *** of playing is a separate issue :)

It could just be my amp settings - Im really not sure. Or maybe even my guitar (she's old and due to a period in storage has a little rust in places we both wish she didnt)  I've fiddled a fair bit on and off in the past but never seem to get very far.

Offgridguy - trying to record songs over the last year has definitely taught me the benefit of listening back what you actually play - hearing it back is a world away from what you think you hear when you are actually practising (at least it is for me).

Im gonna go away and try further fiddling with mic positioning and amp settings - may try reducing the volume in the box a little too and see if its some sort of reflective sound issue bouncing around the box. Thanks to everyone for the advice and, of course, if anyone has any other pearls of wisdom Im all ears.

Cheers

---

### Post by sgx on 2012-10-20
When using software, you want the cleanest,
least effected sound possible going in to the computer,
because the software is written with that as the basis

Whats your soundcard and input device? Any ad/da convertors
used by them, all effect the recorded sound. Pickups also
are often chosen based on preferred music style.

to-do-list

New strings, of a type and size preferred for metal
clean the nut grooves when changing strings
truss rod ajustments for a straight neck
adjust string height to match the neck radius
adjust string action height
adjust the gap between pickups and strings
clean and tighten the pots, switches, and connectors
replace old caps if needed

verify the mic is working correctly
get the amp off the floor, and open or close
the back for variations.

discussion of pickups regarding metal:

[http://www.ultimate-guitar.com/forum/showthread.php?t=1477088](http://www.ultimate-guitar.com/forum/showthread.php?t=1477088)

[http://www.ultimate-guitar.com/reviews/electric_guitars/yamaha/pacifica_112/index.html](http://www.ultimate-guitar.com/reviews/electric_guitars/yamaha/pacifica_112/index.html)  In these many reviews, are mentions
of the things people do to modify the Pacifica, it's a much loved instrument!

---

### Post by sgx on 2012-10-20
[http://www.youtube.com/watch?v=7F1K8EJoWC4&feature=youtu.be](http://www.youtube.com/watch?v=7F1K8EJoWC4&feature=youtu.be)

This was recorded dry, by Hencky Backer,
and reamped, using the Headcase vst. Not
yet working with wine/wineasio.

But Guitarix, Rakarrack, Calf, Invada, MDA, LinuxDSP plugins, and
many Ladspa fx can be used in the same way.
Cheers :popcorn:

---

### Post by Sylos on 2012-10-22
Thanks for the advise sgx - I will be getting going on the "to-do list" asap.

My soundcard is the Maudio Delta 66 with the OMNI breakout box (has its own preamps etc) so that shouldnt be an issue. I suppose the only caveat is that both the maudio and the mic were bought second hand so could have come with faults, but I think its unlikely. 

I hadnt reallt thought much about fiddling with my guitar (I did it many years ago as an uneductaed teenager and made a right **** of it). I've since fiddled about and got it back to a more sensible set up but it isnt ideal by any means. The sadles on the bridge are corroding. I have fiddled with the saddle height to try and get rid of buzz as I have put it into the rather silly tuning of B (bottom E is a B and the rest is tuned accordingly). STring buzz has been an issue but I have managed to largely do away with this. The pacifica is a good starter guitar but it appears from the links on ultimate guitar you provided that it isnt well suited to silly tunings. Definitely need to replace my humbucker as there is rust on the poles (that surely cant be good for sound).

I know its stupid, but until now I hadnt really looked at the guitar as a potential cause of the issue. Its my guitar and I have had it for around 17 years - I stopped noticing its features really. Im still not clear what kind of effect the rust and corrosion would have on the sound - I doubt it can be good. 

Cheers

---

### Post by CrocoDuck on 2012-10-22
> **Sylos said:**
> 

My soundcard is the Maudio Delta 66 with the OMNI breakout box  


I was thinking that maybe impedance matching could be the cause of signal corruption... but actually this setup should work good.

---

### Post by Sylos on 2012-10-23
> **CrocoDuck said:**
> I was thinking that maybe impedance matching could be the cause of signal corruption... but actually this setup should work good.

Yeah I would think the only possible impedance issue would be if my mic lead was a speaker lead. I dont think it is but it did come with the mic second hand, so I cant garuantee it. Its XLR to XLR so I would say unlikely its a speaker lead but I suppose possible. I may have a rummage around and see if I can find another lead to test with.

Looking at it objectively, it does seem there are enough other failure points in the system (starting with the guitar) that could be the issue, so I suppose I start at the beginning and work through as sgx recomended.

Cheers

---

### Post by sgx on 2012-10-23
The pad button on the Omni should be 'out' to avoid
losing 20db gain, might experiment with the various pickup
position choices and the button settings. Setup the input gain
so a thundering power-chord just lights up the clipping LEDs,
then back off just a little. (or more, if you are getting system
noise-floor hum from the combined hardware, and let the software
add some gain.*

A stomp pedal with a bypass, can be used to boost input
gain, try getting a full clean input, like a garden hose
full of water, with no room for air in the hose, so you can use
all the software tricks available, to the max. Such a pre-amped
signal could be tried in the analog inputs, in case there is an
issue with the instrument level jacks/buttons

Some pickups sound better with volume and tone knobs at 10,
some better at lower levels.

*If wineasio is on your system, the free CamelCrusher plugin,
can be daisychained, its a nifty compressor/distortion unit
from

[http://www.camelaudio.com/](http://www.camelaudio.com/) (it is also re-packaged as the CM Fuzz
on the CM magazine dvd)

Cheers

---

### Post by jejeman on 2012-10-23
Sylos, can you give us an example of this bad sounding guitar? Can you record it and post it somewhere?
I didn't see any links to some examples.
We can talk about it, but it's better to be heard.

---

### Post by Sylos on 2012-10-23
> **sgx said:**
> The pad button on the Omni should be 'out' to avoid
losing 20db gain, might experiment with the various pickup
position choices and the button settings. Setup the input gain
so a thundering power-chord just lights up the clipping LEDs,
then back off just a little. (or more, if you are getting system
noise-floor hum from the combined hardware, and let the software
add some gain.*

A stomp pedal with a bypass, can be used to boost input
gain, try getting a full clean input, like a garden hose
full of water, with no room for air in the hose, so you can use
all the software tricks available, to the max. Such a pre-amped
signal could be tried in the analog inputs, in case there is an
issue with the instrument level jacks/buttons

Some pickups sound better with volume and tone knobs at 10,
some better at lower levels.

*If wineasio is on your system, the free CamelCrusher plugin,
can be daisychained, its a nifty compressor/distortion unit
from

[http://www.camelaudio.com/](http://www.camelaudio.com/) (it is also re-packaged as the CM Fuzz
on the CM magazine dvd)

Cheers


sgx - cheers for the ideas. I have (at least) got the box inputs set right (no clipping, reasonably high to avoid the noise floor).

I always thought stomp boxes were bad for recording as they generate a lot of background noise that you dont want on a recording. I was under the impression that the only effects units that were any good for recording were those that cost the big bucks (I heard the Boss GT6 was just good enough for recording on the noise front). Maybe Im wrong on this?

As for wineasio - never been able to get it running on any of my systems (incompetence is likely the cause). For now Im thinking I'll leave it alone as Im prone to having too many things on the go at once and never getting any of them sorted.

> Sylos, can you give us an example of this bad sounding guitar? Can you record it and post it somewhere?
I didn't see any links to some examples.
We can talk about it, but it's better to be heard.

Will string her up with fresh steel and give it a shot tonight or tomorrow and post the results. I had a quick go earlier at moving the mic to head on to the speaker and fiddling with the amp settings (took some volume off and bossted it on the preamp instaed, took a little gain off, a little more mid etc etc) but it still sounds mad whack (to use the parlance of the youth of today).

Cheers to all

---

### Post by CrocoDuck on 2012-10-23
> **Sylos said:**
> 
I always thought stomp boxes were bad for recording as they generate a lot of background noise that you dont want on a recording. I was under the impression that the only effects units that were any good for recording were those that cost the big bucks (I heard the Boss GT6 was just good enough for recording on the noise front). Maybe Im wrong on this?


Unwanted distortion, noise and other source of signal loss and corruptions depends, refering to stompboxes type (digital, with the quality of their AD -DA converters, or analog; true bypass or buffered with the quality of these two kinds of circuits) strongly on how many stompboxes you use, how you connect them to each other and on how they are powered (it may introduce ground loop with it's caracteristic noise or caracteristic noise of active circuital components if powered with low batteries). Avoid too much long stompboxes chains if you don't want issues. Probably the best way to link a **lot** of stompboxes is to using an analogic switching matrix (for example a switchblade). As always, do not forget impedances.

---

### Post by Sylos on 2012-10-23
So.....

I restrung the beast and recorded a quick couple of riffs for test purposes:

[http://soundcloud.com/undecided404/test](http://soundcloud.com/undecided404/test)

All misplayed but the point is the tone - its horrible in all the ways I dont want.

Any ideas other than hanging myself by the old strings? ;)

EDIT: should mention the recording method: mic on axis of speaker, directly into ardour. Exported to WAV and then converted to mp3 using Audacity. No effects other than the distortion on the amp.

Cheers

---

### Post by jejeman on 2012-10-23
I don't hear technicaly nothing wrong with the recording. Even the noise is not that high. So, I guess you don't like the colour of it.
Is there a difference beetween the sound you listen from the amp, and the recorded one? Are you satisfied by the sound of the amp?

Post a link to the example of what you want to achive.

---

### Post by sgx on 2012-10-23
I played the Test.mp3 into two rakarrack, using presets from bank 1

Ballada Solo, and D-Flange. While a bit over the top, it should
give you an idea of the potentials.

I also used Test.mp3 with CM Fuzz in Reaper, with good results,
then sent that output to the rakarracks. Lots of building blocks.

Most of the outcomes I liked just added a lot of highs,
and some mids, with some ambience, which you can also do
at the amp knobs, and software.

Maybe cobble a 30 minute test file, or a loop, and spend a few
evenings with rakarrack, I think you'll find some jewels.
:guitar:

---

### Post by Sylos on 2012-10-24
> I don't hear technicaly nothing wrong with the recording. Even the noise is not that high. So, I guess you don't like the colour of it.

Very well put I suppose. When I hear my sound it frustrates the hell out of me. It lacks clarity and sounds so confused - the definition of the notes seems to get lost. But I think rather than a signal path problem it is more just about the "colour" of the sound to me.

Due to noise issues I normally play my electric guitar unplugged to practice (I also thought it would make me better because I couldnt hide mistakes with distortion and fuzz). But now when I hear it through the amp its like Im hearing me with broken fingers play it.

It kind of looks like the major part of my problem may just be how poor I am at playing. Maybe Im back to the "poor musician, good gear" scenario - it wont make me sound any better!.

Well, ofr interets, heres an example of what I would like:

[http://www.youtube.com/watch?v=Cb9C1u8HsR8](http://www.youtube.com/watch?v=Cb9C1u8HsR8)

In my aspiration I try to ignore the fact that I will never be as good as these guys - I just try to aim for their guitar tone and clarity. Perhaps its unattainable without the level of skill they have.

sgx - interesting to hear you managed to get a passable sound by adding to it with rackarrack. Will be giving that a shot later to see what I can achieve.

Cheers

---

### Post by CrocoDuck on 2012-10-24
I was usually play unplugged too while practicing (when it was possible to clearly listen to metronomes, tracks and guitar togheter). I was usually acting like this because lazy ... but I found that acting like so you listen directly to the string while playing and it is very useful for the developing of the touch. Getting a clear and defined sound is difficult with distortion, expecially with hight gains, because the compression introduced by the distortion. I suggest to use a multiband distortion, in order to define gain for some frequency band that composes the spectrum. You shoud be able to define for every configurable band the right ammount of gain (and/or other parameters) in order to prevent too much compression, that implies less defined sound (as fundamentals levels becomes close to harmonics levels, non-harmonics partials levels and overtones introduced by the distortion kind, and notes are recognized by brain with fundamentals). You can find these tools in Guitarix. Some distortion stompboxes also have those kind of parameters or have some kind of useful equalizer, like the Boss Metal Zone or the cheaper Behringer Ultra Metal.

---

### Post by jejeman on 2012-10-24
Sylos, you are not that far from the result you want. Just spend some time with guitarix, rakarrack and with the amp it self, I guess the mic is transfering truely the sound from it.

---

### Post by CrocoDuck on 2012-10-24
> **jejeman said:**
> Sylos, you are not that far from the result you want. Just spend some time with guitarix, rakarrack and with the amp it self, I guess the mic is transfering truely the sound from it.

Yeah! We found that the hardware is basically ok. Those programs and the amplifier parameters will help you. If you find some LinuxDSP useful you know what to do! Don't be too severe with yourself and trust your ears: be carefull adding gain, constantly "keep a ear" on spectrum ends (bass and treeble ends). The sound is just around the corner.

---

