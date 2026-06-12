---
title: "6 channel audio anyone? revised!"
date: 2009-02-19
forum: Ubuntu Studio
---

### Post by Reeman on 2009-02-19
Well it came down to having a SoundDisaster card installed along with a real M-Audio card. The SB audigy ca0106 chip just does not cut the mustard at higher bit rates. 

I tried multitrack 24/96 (just 4 channel for now) and the SB card started to drop bits all over the place at high bit rate. **_HOWEVER_** the alc883 worked fine. Surprise surprise....an onboard dsp that really rocks! Guess it is the quality of the circuits on the asus board helping with the bus to the amd 64 processor. Well lucky for me a local music store retailer had another M-audio Audiophile 24/96 for 70 bucks. 

So here is a shot of all three devices in use at low bit rate. I will slowly start recording at progressively higher rates and see what happens.

Because I can world clock twin the M-audio cards there will be no jitter with 4 tracks from these cards, seeing that I already had good results with one M-Audio and the ALC883 azalia, there might be no trouble with ganged Audiophiles and the onboard Realtek chip.[-o<

---

### Post by Stochastic on 2009-02-20
Nice to see that you've managed to do all that configuration.  

IMHO it's easier (less configuration after every new Ubuntu version), produces better audio, gives more features (preamps/phantomPWR), and only costs a touch more to buy one single firewire card with multiple outs.  And with FFADO on its way into the repositories...

---

### Post by Reeman on 2009-02-20
> **Stochastic said:**
> Nice to see that you've managed to do all that configuration.  

IMHO it's easier (less configuration after every new Ubuntu version), produces better audio, gives more features (preamps/phantomPWR), and only costs a touch more to buy one single firewire card with multiple outs.  And with FFADO on its way into the repositories...

Yes it would be easier to use external a/d. But the whole purpose of this is to put together a true semi portable multitrack that will accept atleast four analogue line level ins for pure a to d work! If I can get 6 channel working at cd quality I will be satisfied. But good stable four channel at 24/96 is my first priority. 

I want to do hall recording of classical ensembles with a mobile set up. Because I will be using nothing but good condenser mikes to two stereo out mixer boards (mackie 1212s) and no external digital effects I need clean quiet a to d. 

One example is Bachs' cantatas and ensemble works. The ideal setup is four carefully placed mics for the orchestral section and four really carefully set up mics for the vocal work. Mixed separately to control room sounds.

With this setup I could send a stereo mixed house out to the Conductor and my monitor.

I am looking to become a hired gun that can do stuff that would cost a fortune through a production studio. The whole idea is to get some of the really wonderful stuff produced that gets missed by the overpriced and bloated entertainment industry. 

The fact is that classical music performance recording is dying from neglect and companies that control the industry (SONY) are just recycling old stuff that was mostly done when companies like (COLUMBIA)(DGG)etc, etc actually had real classical recording going on!:-({|=

As an aside the reason why four carefully placed mics for the sections is important is SATB and the ability and knowledge level to be able to place the mics at distances which do not copy exact wave lengths. If you place a mike at a distance that copies the exact wave length of a certain frequency your recording will have wolf notes that stick out like a sore thumb. Classical recording is an art and as such requires real science!

---

### Post by Stochastic on 2009-02-20
Yes, a clean quiet A/D is exactly what I was suggesting (no DSP was mentioned).

I do extremely similar work (though I prefer post-Xenakis style 'classical' to the more traditional stuff - though Bach always has a place in my heart *glen gould is good for doing taxes to*).  My setup includes some nice mics (Josephsons) plugged straight into my Presonus Firepod (nice clean preamps on that soundcard).  Ardour has no troubles capturing all 8 channels.

This setup is much cheaper than all the soundcards & mixers you're suggesting using, and is much more portable too.

Oh, and I hardly believe that SONY controls the classical music racket - Universal Music Group has a much more influential classical branch (Deutsche Grammophon) and Warner's Nonesuch is quite influential too.

But I really don't want to argue, I'm just trying to suggest something easier for you to work with.

---

### Post by Reeman on 2009-02-21
> **Stochastic said:**
> Yes, a clean quiet A/D is exactly what I was suggesting (no DSP was mentioned).

I do extremely similar work (though I prefer post-Xenakis style 'classical' to the more traditional stuff - though Bach always has a place in my heart *glen gould is good for doing taxes to*).  My setup includes some nice mics (Josephsons) plugged straight into my Presonus Firepod (nice clean preamps on that soundcard).  Ardour has no troubles capturing all 8 channels.

This setup is much cheaper than all the soundcards & mixers you're suggesting using, and is much more portable too.

Oh, and I hardly believe that SONY controls the classical music racket - Universal Music Group has a much more influential classical branch (Deutsche Grammophon) and Warner's Nonesuch is quite influential too.

But I really don't want to argue, I'm just trying to suggest something easier for you to work with.

No arguments about the hats in the recording industry! 

I have considered using firewire audio but if that were the case I would fork out the bucks and go all mac like the rest of the majority. But I like to build my own stuff. 

From what I am reading [_[COLOR="RoyalBlue"]Vista or XP64[/COLOR]_]("http://forums.presonus.com/showthread.php?t=7514") is a dog for audio. I do not want to do WDM based XML/DirectX gamer crap. The last thing I need or desire is to have DRM tags dumped into my bit streams. I run with emphasis off on Linux so my files are open and I never have to sweat running them anywhere I choose. 

I have found that the biggest hurdle to good clock timing performance on the pc has been stable power! Now there is a company [[COLOR="Blue"](FSP)[/COLOR]]("http://www.fsp-group.com/english/1_product/2_detail.asp?mainid=1&fid=123&proid=137") that build high spec fanless atx power supplies. I am using one and find that it really is making a huge difference with audio!
Their power fluctuation specs are really good.... as good as the circuits designed for high end digital audio amps.

If I can build a setup that goes directly from the small mic pre amps to the line ins then in theory Ardour can do all the mixing functions necessary as I will be running things flat using hall acoustics, mic placement and level control to eq the show.

Stable power and an Asus board with good caps and circuit design goes a long way to maximize the capabilities of the onboard and pci sound devices. I might experiment with inline small tube emulated mic pre amps that send phantom and run on 9v batteries. The original clean hall acoustics is what I crave...not digitally created add ons.

  
No arguments about the companies that are still releasing classical productions. It is just that they are so bloated and non competitive that all they seem to be doing is resting on the past glory of greats like Karl Bohm, George Szell and Leonard Bernstein.

---

### Post by markbuntu on 2009-02-22
A few orchestras like the BSO and the Philharmonic are starting to release and sell their own live recordings over the internet and the Met is broadcasting Opera to movie theatres. Big changes are happening with classical music....and we really need more examples of modern works that the big distributors will just not get into. You guys are on the right track..high quality recordings for small audiences, low production costs to make that possible.

---

### Post by Stochastic on 2009-02-23
I see no reason why you'd want to have a Mac setup if you're going to buy a firewire card, and I still believe a firewire card is much simpler, cheaper, more portable, and higher quality than the setup you've described (the M-Audio 24/96 is a really poor soundcard IMHO).

Furthermore, you're recent edit, which described Wolf Tones, seems out of left field.  Wolf tones are created acoustically by acoustic instruments and their resonating bodies, it has nothing to do with mic placement; see: [http://en.wikipedia.org/wiki/Wolf_tone](http://en.wikipedia.org/wiki/Wolf_tone)
Your explanation of 'exact wavelengths' makes no sense either as a basic string quartet can easily have wavelengths anywhere from 35feet to 7inches as their base fundamental pitch wavelength.  The technique you're describing seems to require that every single note in that range be taken into consideration, and no placement that is an exact multiple of any of those wavelengths is acceptable.  This completely ignores the fact that every harmonic has a wavelength of half the previous harmonic (i.e. the third harmonic of the 7inch or 2000hz note would have a wavelength of 1.75 inches).  Crunching the numbers in my head I can easily see that finding the perfect location where no length is a multiple of an equal-tempered scale note (or it's harmonics), is literally physically impossible.  Furthermore, this simple rendition of the problem assumes a single point source emanation, which is the farthest thing from the truth (never mind how you would attempt to measure your exact perfect distance).  However, all this, in theory, might be somehow magically possible to setup in lab settings...
...but that's just not how soundwave propagation physics works. ;)

The closest phenomenon that exists is the standing wave phenomenon, but that is determined by the architecture of the hall you're in (you know that one that you're trying to capture as flat as possible).  And has little to do with mic placement (particularly when you start considering all the modes).  The best solution to the standing wave issue is to record in a well designed hall - lucky you.

I would highly recommend taking a read through [The Master Handbook of Acoustics by Frederick Alton Everest]("http://www.google.ca/search?hl=en&q=master+acoustics+handbook") before taking on any recording gigs.  And, it'd be advisable that you do a quick apprenticeship with a small recording studio before you start walking around claiming you can do what they do (particularly if you're packing M-Audio 24/96 cards and trying to make that claim).  I don't mean to be a wet blanket, and maybe I'm being too much of one (after all I don't know your expertise), but I do know that recording is a science that many think they have mastered before they even get their first gig.

---

### Post by Reeman on 2009-02-23
OK I used wolf tones out of context. And should have just pontificated on pure hall recording techniques. My bad.   

Being a classical guitarist I understand how wolf tones are created and why 880hrz can wolf if the Luthier does not tune the sound board to the box of the guitar. Hence the infamous 220 boom that close in mic placement suffers from when recording acoustic guitar.

The [[COLOR="Blue"]Physics of Sound[/COLOR]]("http://www.amazon.com/Physics-Sound-2nd-Richard-Berg/dp/0131830473") was my old text book back when I first got into recording. Now the book is like gold good luck finding it cheap!

 
What I was getting at by mentioning SATB mike placement is that by doing really carefull sound checks prior to performance you can  move your mikes around to avoid either dead spots or worse still sweet spots that can unbalance your sections in any venue regardless of acoustics. Today this seems to be a dying art because of the lack of hall recording specialists and the almighty studios!

If you have multitrac high bit rate firewire experience with linux I am all ears. 
  

Do you really think pushing multitrack through firewire is a better solution? I have looked into [[COLOR="Blue"]Linux[/COLOR]]("http://www.echoaudio.com/Products/FireWire/") compatable firewire devices and agree that their devices are interesting, just I have no experience with their linux drivers and using external a/d. I have seen some boasting that they can get 8channel 24/96 working through firewire...but I am a little concerned about the limits of firewire. If you do not have a record buffer working before the transfer how do you pipe that much data to your recording and mixing software? If you do have a record buffer then you will have to monitor things source only because your converted stuff will not be in realtime.

  

My only other device is an old 4track adat that is starting to have record head trouble and is impossible to fix. I got rid of my 4 channel r to r Sony tape that I have had since 1976 ...maybe I should have kept it.   

As to the M-audio cards ... I know they are "prosumer" but I have had really good results. Because they are rated at over 100db they seem to handle hot signals quite well. I have found them really quiet and their drivers seem to be rock solid even under Linux!

---

