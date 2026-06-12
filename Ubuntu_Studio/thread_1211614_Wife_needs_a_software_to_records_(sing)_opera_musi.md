---
title: "Wife needs a software to records (sing) opera music"
date: 2009-07-12
forum: Ubuntu Studio
---

### Post by jocampo on 2009-07-12
Hello People

Well...my question is ... what are the alternatives that I have in order to create a modest recording studio for my wife. She is a former opera singer and would like to record music to maybe sell the audio material later. I've heard a lot about Ubuntu Studio...is that a good choice? also ... what hardware (systems or barebones) do you recommend me for that, which brand ... how's the compatibility issue when getting mics and music stuff...

Thanks in advance,

---

### Post by ghostborg on 2009-07-12
I'm no expert but what first comes to mind is Audacity.
[http://audacity.sourceforge.net/]("http://audacity.sourceforge.net/")
Which should be installed by default in the Studio version of Ubuntu.
I loaded Studio once and it seemed to have much of what you would need.

I would look into a sound card with a good Signal to noise ratio.
SNR. Creative Labs cards seem to be good. Motherboard sound cards tend to be a bit noisy.

You might look for advice from a sound engineer.
Veronica Belmont at the podcast Tekzilla at [www.revision3.com](www.revision3.com) mentioned her audio background on the show.

You will probably get confused by all the recommendations people give but just check out people comments/reviews on products before buying them.

Good Luck.

---

### Post by RedSingularity on 2009-07-12
I would say audacity as well.

---

### Post by tgalati4 on 2009-07-12
m-audio delta 44 or 66 cards are decent.  M-audio also makes usb preamps that are decent.  $1,000 studio microphone will record more vocal nuances than a $200 mic.  Check craigslist.org.

---

### Post by raboofje on 2009-07-13
Audacity is a good, simple start. If you start requiring more (more serious multitracking, effects, etc), look into Ardour.

---

### Post by russo.mic on 2009-07-13
Hey Guys!  Audio Recording Engineer here!

So,  my advice for best mileage per dollar is to get an old PreSonus Firepod.  They can be fetched off of E-bay for pretty cheap.  Something in the order of $150.  

The advantages?  Well, the delta 44 cards and such don't come with microphone preamps, which you really do need.  The Firepod has 8 right in the front of it that can also function as line-level inputs (like you'd use for a cd player or a bass D.I. or something).

Disadvantage?  You'll have to look up how to compile the FreeBob driver for the thing.  not to much of a task however.  Anyway, once you do that, you'll have the ability to record 8 channels at one time.  And, if you want to expand, you can get a 2nd and 3rd firepod and daisy chain up them, giving you 24 tracks at the same time.  

Let me also as you this, your wife, is she recording this opera music on stage?  as it's being preformed?  or does she want to do it at home?  The methods you'd go about recording this change based on the answer.  Mainly, mic placement and Microphone selection.  

If she is recording it on her own, in your house kind of thing, then you'd probably want to pick up a good vocal mic.  Some cheap one's I recommend are the Audio Technica 4040 or 4050, the Shure KSM series.  

If she is recording this on stage, then Rode makes a microphone that you'd want to pickup, the Rode NT4.  The main advantage being that it's a very natural stereo mic, kind of designed to pick up sound as our ears do, to put it simply.  You could just put that somewhere in front of a stage, or hung up from a truss, point that at stage, and take a feed from the 2 inputs.

As far as software goes, I'd like to give a +1 to Ardour.  I think it's the best editor in my opinion.  Also, I just read in linux journal that the next version will support VST/VSTi plugins, and have MIDI capiblity as well. This can all be found in a download of Ubuntu Studio.  Also, I hear a program called reaper has done some great stuff, but I haven't yet had the chance to try it.

Sorry for the long post, but I just love recording!  Don't hesitate asking any more questions about gear or whatever.  I love talking about it.

Russo

---

### Post by jocampo on 2009-07-13
Hello Russo and Team, 1st ... thanks all you guys for taking the time and read/reply my post! ;-) ...I really appreciate it.

Gotta work and take a shower now, will read everything with more calm from my office, but really quick ...

-She wants to record and sign at home
-I'm assuming she will use a baseline track/music for her voice
-Main idea is selling or recording CDs with her voice

So, so far, is these what I need?

1.A good computer/barebone
2.Ubuntu Studio
3.A decent audio card
4.A decent mic
5. Do I need like a mixer or external console?

? Am I right? ...I know about systems, ;-D but nothing about recording, and she's good singing but not very techie, lol ... 

Thank you guys!

---

### Post by HavocXphere on 2009-07-13
It sound like you're dealing with just one channel, so you'd probably won't need a mixer.

You will however need an equalizer somewhere in the system imo. Even the best voices need some help. ;)

I'd be more worried about the acoustics of where you are recording. Confined spaces without padding are less than ideal for audio.

One thing missing from your list is a set of quality headphones (Mid range sennheisers). Without them you'd be relying on speakers/monitors and that introduces a bunch of problems associated with feedback & feedback destroyers.

Never heard of the Audio Technica mics that russo recommend, but the Shure mics he mentioned are definitely good. Do spare some thoughts though as to how you will connect them cause they usually don't come with mini jack connections.;)

Also watch the distance between the person and the mic. e.g. if its too short (like the rappers who shove the microphone 1/2 down their throats) then the lower frequencies get an unnatural boost that is pretty much impossible to fix w/ an equalizer. You'll also want to mount the mic in some way cause holding it by hand invariably results in added noise.

Not sure on the sound card front, especially w/ linux.

As for the system, make sure that its got a decently sized harddrive since you'll probably want the audio streams in an uncompressed format.

And finally, pay some attention to how the entire system is earthed. It can introduce noise into the audio stream if earthing is inadequate.:redface:

---

### Post by tgalati4 on 2009-07-13
Delta cards have an optional  I\O module with 2 decent preamps..  I've used one to record stereo church concerts on a PII 350 MHz computer running dynebolic.  2-hour  continuous recordings without a hiccup.  Envy24conntrol provides full linux support. 

 Firepod is good if you need 8 channels.

---

### Post by russo.mic on 2009-07-20
You shouldn't need a mixer with the Firepod, as it has the pre-amps you need.  If anything, I recommend a better pre-amp in front of it.  The pre-amps that come with it are pretty okay, but there is a company, FMR Audio.  They make the RMP (Really Nice Preamp), and it sounds awesome and is pretty cheap.  I use it in front of my $1000 pres sometimes for foley.

Also,  A pair of good headphones is nice, Grado Labs stuff is what I recommend.  Check them out.  Even there $100 pair I'll put ahead of the sony or Shenhiser sets that cost more anyday.

But really, a pair of good monitors will beat headphones out anyday.  Think the new Mackie Actives.  Great for the buck.  Also, Tapco made some good stuff a few years ago that can be fetched off e-bay for not to much.  

As far as mic placment goes, have some fun!  try different stuff!  I feel like for opera I would focus on getting a good space, then try seeing how far away you can place the mic.  The further away you place it, the more room you get.  If the room is good, then stellar.  If the room however is less than desirable, well, hmmm....Get closer and get some digital reverb plugins.  I remind you that Ardor supports VST, and there are plenty of great VST plugins out there for free.

The delta cards are great, but what's the point?  By the time you get done buying that, the cost is about what the firepod costs, and the firepod has some pretty great advantages.  For one thing, 8 channels.  For another thing, expansion.  And lastly, MUCH more portable.  You can use that thing with a laptop.  In fact, all my live gigs get done with ubuntu and 3 firepods on my Macbook.

Havoc, with the firepod, or most pres I know of, you would'nt need a 1/8th connector, just an XLR cable.  In fact, any condenser mic won't work with an 1/8 because that won't supply phantom power.  Also, I do put the Audio Technica Mics slightly ahead of the Shure stuff.  The 4050 has a great top end, great for female vocal actually.  I sometimes throw it up over my U89 or U87, both of which are WAY costly mics.

---

### Post by kayosiii on 2009-07-21
For opera style vocals I would favour a large diaphram condensor mic. You can get good options for a good deal less than 1000 dollars. Behringer and MXL are two manufacturers that spring to mind. Microphones all colour the sound going through them to some extent - a microphone may work well for one singer and badly for another. If you have a chance to try a mic before you buy it then do so. Professional studios have a collection of Mic's and usually audition a few to find the one that will work best for an individual performer. A flatter mic will be more versatile than one that is highly coloured.

I can also attest for the Firebox/Firepod being a good option for recording under linux. AFAIK you shouldn't have to recompile anything in the latest Ubuntu (using the ffado drivers -  I could be mistaken though - I am using Karmic at the moment).

Headphones are a useful tool for mixing but you should not rely on them alone. Ideally you would have a set of full studio monitors in an acoustically treated environment but that is likely to run well over your budget (it certainly does mine). A good set of midfield or nearfield monitors and some thought applied to the recording area will be a reasonable compromise. If you do this you will want to listen to your work in several different environments at least until you have an idea of what your speakers don't do and how to compensate for them. Like microphones one set of speakers does not work best in all conditions so audition the things before purchasing. What you want is a set of speakers that accurately reproduce what the computer is trying to play - this may not sound as good as less accurate speakers can reproduce.

Software wise I would look at Audacity if you are going to stick to fairly simple recordings and Ardour if you can see yourself getting more serious down the track.

Here is a checklist.
1) good accoustic space to record in
2) a good microphone. (I reccomend a large diaphram condensor)
3) a good preamp and analog to digital conversion unit (better known as soundcard).
4) Monitors & headphones for mixing with.
5) Either Ardour or Audacity for creating the mix.

---

### Post by thisllub on 2009-08-24
A distro with a real time kernel is pretty important.
64Studio is the best I have tried.
[http://www.64studio.com/](http://www.64studio.com/)

---

### Post by daniel_cello on 2009-08-25
If it's not too late I would like to offer another suggestion for a sound card. I have used the firepod and found it to be comparatively quite noisy. If you are able to fit it in your budget I would much rather recommend the small Saffire board by Focusrite, that I believe will also run linux under the ffado driver. I have the 19" saffire and the recording quality is like day and night compared to Firepod. (I have not tried the small Saffire - I am only assuming they use the same mic preamp as in the 19" version.)

---

### Post by jocampo on 2009-08-25
Not too late...in fact... still saving to pay all this cash and please wife :-)...

At work now, but will review all your advices at home or during lunch hour.

Thanks for the suggestions folks! ;-)

---

### Post by Stochastic on 2009-08-26
> **daniel_cello said:**
> If it's not too late I would like to offer another suggestion for a sound card. I have used the firepod and found it to be comparatively quite noisy. If you are able to fit it in your budget I would much rather recommend the small Saffire board by Focusrite, that I believe will also run linux under the ffado driver. I have the 19" saffire and the recording quality is like day and night compared to Firepod. (I have not tried the small Saffire - I am only assuming they use the same mic preamp as in the 19" version.)

I have tried both the Firepod and a Saffire (though it was the smaller version, not the 19" version) and I found the Firepod's sound quality to be better.  The preamps are the same between the larger and smaller Saffires (as far as I know).  The main audio difference was tone of the preamps (Presonus had clearer pres, whereas Saffire's had a bit more style - I prefer clear).

Possibly you had a bad product in your Firepod.  I know many people who are very happy with the quality of theirs.

However, Presonus cards are not officially supported by ffado (because they haven't donated a card to the ffado team for testing).  Focusrite cards ARE officially supported by ffado.

Really though I'd recommend a smaller card like the Firebox or smaller Saffire for what you're doing (just vocals).

Oh, and Ubuntu Studio 9.10 (which will be released in October) will most likely have a very nice stable RT kernel. (but I don't want to jinx things)

Edit: oh, and you'll want to use Ardour to record with, it will give you the least number of errors in the recording.

---

### Post by dawiba on 2009-08-26
I'm joining in a bit late, but just to add my vote for the Focusrite. Nothing against the Firepod, but I use a Saffire LE and it works without a hitch and the sound quality is terrific for a unit this (relatively) cheap. Plus Focusrite support FFADO.

I also go along with the recommendation for Sennheiser headphones. I use the HD 25 SP headphones and find the sound quality (again for the price) is great. There is some sound leakage when you're recording with a mic, but it's negligible if you're careful.

For monitoring I use Alesis Monitor One Mk2 speakers with a Samson amp. These can be bought quite cheaply now but you would need to buy an amp as well. You can get active versions if you prefer not to use/buy a separate amp.

Oh and of course, UbuntuStudio :smile: (This also works fine until I start poking around :()

All of this stuff is fine for me as I just record at home. It's modest (what you want in your first post) but perfectly functional and I'm happy with the results.

---

### Post by daniel_cello on 2009-08-26
> **Stochastic said:**
> I have tried both the Firepod and a Saffire (though it was the smaller version, not the 19" version) and I found the Firepod's sound quality to be better. The preamps are the same between the larger and smaller Saffires (as far as I know). The main audio difference was tone of the preamps (Presonus had clearer pres, whereas Saffire's had a bit more style - I prefer clear).

I think maybe the noise isn't such a big issue if you are able to get the levels fairly good and to get close to the sound source with your mics, but it all depends on the dynamics of the music. I was recording a live concert with a chorus and small orchestra so I could not go close with my mics and since the music had some softer sections the signal level was between maybe -50 or less and -10 dB. For a recording like that it is very clear if there is noise and the firepod I have tried was clearly generating a lot more noise than my saffire cards. (I have bought two since I occasionally need more than 8 mic channels when I am recording.) If you record at a level above -20dB (with a compressor) then you can get away with a noisier soundcard.
 
Not sure about your budget but I have gotten very good results with studio projects microphones, I've used models B1 C3 and LSD2 (which is two C3 in one mic). If you have a chance to audition them it is well worth it. But of course mics are vast subject and nowadays there are many spectacular mics for quite little money.

---

### Post by Stochastic on 2009-08-26
Very interesting, I'm using a pair of Josephson CM42 mics and constantly recording soundscapes (easily into the -70db range on regular sustained sections).  No noise is evident.  A soundcard at this quality level shouldn't produce any audible noise ever (noise floor should be around -110db) unless you're greatly increasing the gain on you're recordings.

Two things: 1) I almost want to suggest your poor mics are to blame, possibly the fact you're using large diaphram mics so far away from the source (possibly focusrite preamps contain some noise adjustment/compression technology?).  Maybe I'm just being snobbish on that one.
2) I have found my laptop's power supply to be poorly grounded and if I record with it plugged in anywhere near my soundcard I get noise.  My solution has been either run on battery while recording, or plug into a different circuit.  This may very likely be the 'noise' you speak of - it's audible in the -50db range.

---

### Post by carusoswi on 2009-09-19
I'm a bit late to this thread and a bit surprised, also.  If I were the OP, I wouldn't buy anything much at this time.  You'll need a couple of mics, of course, and some means to get both of them into your sound card.  You might want to try one of those stereo mics at first.

I, personally would hold off on purchasing a bunch of expesnive equipment at this time.  Chances are, the sound card already installed in your computer will serve your present needs.

If you can record a silence quietly - no static or hum from the computer, itself, then, likely, the soundcard is ok for starters.

Then, I would download and install the software you want to use in order to make recordings - above suggestions should be just fine.

Make some test recordings and evaluate them before you go off spending a fortune to build the perfect system.

BTW, your objective confuses me.  Your wife wants to use opera tracks to make cd's with her voice added that she can sell?

Is that even legal?

I dunno.  But, whatever, good luck with your adventure.

We are all musicians in this house (current professional opera singers, string players, etc.) and have been able to advance our performing careers mightily by the vast array of devices available that allow one to make decent sample recordings on the cheap without investing in more gear than what the normal household with an interest in consumer electronics would have anyway.

I did invest in a pair of inexpensive mics (Sonys with good frequency response specs, but not expensive - the pair was not more than $100), and, because I could not tolerate the electrical hum that would occur when making even short runs with mic cords, I eventually invested in a mixer with balanced xlr mic inputs and lots of balanced mic cord so that I can go into a reasonably sized space (church or synagogue, for example), stretch my cords, and still get good, clean signal without the hum.

My sound card s a Creative labs Audigy 2, nothing special, and I can tell you that the results using equipment equally simple and inexpensive will be more than adequate.

Advice given by others contributing to this thread is sound, but overkill, IMO.

It appears you will be re-recording tracks played through a sound system (or at least copying the tracks electronically and then mixing in live recordings of your wife.

Your source (except for your wife) is a bit compromised from the beginning, so I don't think it makes sense to go out an purchased the most pristine sound card and worry about s/n ratio (of the equipment) as all of it, likely the cheapest of it, will more than exceed your needs.

But, don't bother taking my word for it (or that of anyone esle on this board).  Listen to our suggestions, then, (if I were you), pick up the most modest amount of equipment you need to begin, and use that low cost approach to gain some actual experience.

As your experience grows, you'll have a much more informed notion of the weak spots in your settup.  Then, go out and spend more money to fix up those weak spots.

I think you will be happier with the outcome if you take this approach.

BTW, to others here, will Ardor allow sound on sound recording?  Just curious.

This is one area of Linux I have not yet mastered (audio recording), although I have rather extensive experience in Windows with Sony's Vegas and Steinberg's Wavelab, both excellent (but proprietary and expensive) bits of software.

If anything I've stated smacks of condescension, please know that it was not intentional towards the OP or the respondents to his questions.

Good luck!

Caruso

---

