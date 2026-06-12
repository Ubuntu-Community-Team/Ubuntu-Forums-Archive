---
title: "M-audio Audiophile 2496 vs. Delta 1010-LT or Delta 66"
date: 2008-10-01
forum: Ubuntu Studio
---

### Post by whistlingtony on 2008-10-01
Hey all,

I've recently obtained an interest in recording my own stuff. I have a nice, simple, quiet little computer ready to go. I need an audio interface and I'm hoping you all can help me pick one.

I am planning on hooking up a mixer, so I don't need a lot of inputs. Mixers are just more intuitive for many folks. 

I was thinking of either the M-Audio Audiophile 2496, the M-Audio Delta 1010-LT, or the Delta 66. 

Will the Delta 66's breakout box be a good or annoying thing?

I did my reading. They look to be supported. I'm wanting actual user experiences. Has anyone had problems with these cards? Money isn't really an issue here. I just want to know if one of these is going to be a pain in my ****. 

Does anyone have a different recommendation? 

Thanks all!

-Tony

---

### Post by Stochastic on 2008-10-02
my first thought is: if money is no object, why buy such poor quality cards?  (this is a relative qualification, but still, relatively truthful)

My next thought is that a breakout box is usually a good thing as it takes the audio signal away from the internal noise interference of the computer - but unfortunately some breakout boxes are merely for the convenience of plugging/unplugging easily and don't do any conversions.  Do your own research on this (phoning the manufacturers is a good way to learn about this).

My next though was, why limit your recordings to being a capture of a mixdown?  The power of digital audio is the ability to infinetly tweak a mix to perfection.  Even a simple acoustic guitar and vocal track should be kept as separate channels until you're 100% (I'd say 110%, but that's just not my style) satisfied with the FINAL result.  This is still up to you, the owner/operator of the equipment to determine in the end, but that's just how I see things.

My last thought, which happens to be the most important of the points I'm raising, is: which one has the best audio quality?  Read the specs, buy a better precision clock, noise floor, etc... particularly if price is not an issue for you.  (go get a hammerfall card)

---

### Post by jukingeo on 2008-10-02
> **whistlingtony said:**
> Hey all,

I've recently obtained an interest in recording my own stuff. I have a nice, simple, quiet little computer ready to go. I need an audio interface and I'm hoping you all can help me pick one.

I am planning on hooking up a mixer, so I don't need a lot of inputs. Mixers are just more intuitive for many folks. 

I was thinking of either the M-Audio Audiophile 2496, the M-Audio Delta 1010-LT, or the Delta 66. 

Will the Delta 66's breakout box be a good or annoying thing?

I did my reading. They look to be supported. I'm wanting actual user experiences. Has anyone had problems with these cards? Money isn't really an issue here. I just want to know if one of these is going to be a pain in my ****. 

Does anyone have a different recommendation? 

Thanks all!

-Tony

I ended up buying a Delta 44 and received it yesterday, so far it is working great and the best part was that it was automagically recognized by Linux...that is in ALL of my Linux distributions (I am up to three right now; Ubuntu Studio, Puppy, and Dynebolic).

However, I will say that cost WAS a factor in my purchase and if "money is no object" as you are saying then I would agree 100% with Stochastic...get an RME Hammerfall card.   The Hammerfall cards, like M-Audio is supported fully in Linux and I believe they too should be automatically recognized.   I do have to warn you though...we are talking extreme ends of the spectrum.  Hammerfall cards start at around $500 and go up from there.  But that is the way to go for a serious pro system.   For me I just wanted something to create a decent quality mix with (48k, 96k) and play around with all the cool programs within Linux.

I would personally stick with either M-Audio or Hammerfall because while other cards MAY run with ALSA drivers, it is usually a pain in the neck to get it going.   I went through 3 audio devices prior to getting the M-Audio Delta 44...all were not fully supported in Linux.  I purposely bought an Echo product (because I know they are good) based on research that it is supported via an ALSA driver. Iksnay, I couldn't get it to work AND I spoke to the ALSA developer for the driver of my specific device.  He barely returned my emails and was seemingly not interested in helping me out with my problem, so out the card went (it is on Ebay now) and I bought a Delta 44.   If I would have known I would have so much trouble with sound in Linux ahead of time, I would have made this card my FIRST choice.  But then again, hindsight is 20/20.

Now as Stochastic says, you want to lay your tracks into the digital realm as soon as possible. Once you are in "digital land" and you are using a higher sample rate such as 88k or 96k, you should be good to go.  You do your mixdown within a mixing program suited for the task.  In Linux, Ardour is the Grand Pubah, but there are others out there you can try.

Just do your research on an audio device.

Here is the information for the M-Audio Delta Line:

[http://www.m-audio.com/index.php?do=products.list&ID=pciinterfaces](http://www.m-audio.com/index.php?do=products.list&ID=pciinterfaces)

Here is the information on the RME Hammerfall line:

[http://www.rme-audio.de/en_sitemap.php](http://www.rme-audio.de/en_sitemap.php)

---

### Post by aeiah on 2008-10-02
i use a delta 44. that line of stuff (the 66 and 10 10 too) do the conversion in the breakout box. it works fine in linux although it can be a bit fiddly to start with. once set up you shouldnt have any problems.

id suggest going for the delta range and if you find you need something better then you can just sell it and get a pro card. you'll be wanting to spend a lot of money on a fancy array of studio monitors and soundproofing anyway if you want to take advantage of what a pro card has to offer so the loss of selling the delta second hand would be a drop in the ocean.

---

### Post by jtappin on 2008-10-02
> **whistlingtony said:**
> I was thinking of either the M-Audio Audiophile 2496, the M-Audio Delta 1010-LT, or the Delta 66. 

Will the Delta 66's breakout box be a good or annoying thing?

I did my reading. They look to be supported. I'm wanting actual user experiences. Has anyone had problems with these cards? Money isn't really an issue here. I just want to know if one of these is going to be a pain in my ****. 

I have an Audiophile 2496, which I use for digitizing 78s and LPs. For that purpose it is fine, the noise from the card inside the PC is less than 1bit in 16bit recording and much less than that from the deck and amplifier. Also since most audio component systems have RCA connectors, it's easy to hook up without having to find heterogeneous cables.

As far as Linux support goes there were a few lockups with the very early ALSA 0.9 series (which was the latest version around the time I got the card), but I was able to locate where they happened and the ALSA team were able to fix them.

I've never used a breakout box so I can't comment on that.

---

### Post by whistlingtony on 2008-10-02
Sweet! Thanks all! 

Heh, when I said "Money is no object" I meant between $100 and $200 didn't matter. Thank you for the Hammerfall recommendation though. I'll look at them, but I'm just at a hobby level. No need to spend quite that much dough. I'll buy nice microphones instead.

"why limit your recordings to being a capture of a mixdown?" Hmm... that's good advice. Thanks Stochastic!

Jukingeo, Jtappin, Aeiah  thanks for the personal references! I trust a personal experience more than marketing drivel.

---

### Post by jukingeo on 2008-10-02
> **whistlingtony said:**
> Sweet! Thanks all! 

Heh, when I said "Money is no object" I meant between $100 and $200 didn't matter. 

LOL, yeah...some of the really high end cards can get expensive.  Some of the RME stuff can approach $1500.   Supposedly they have excellent digital converters that even rivals the Pro-Tools stuff.

---

### Post by paulg on 2008-10-03
I use a 1010-LT. It has more features and inputs than the 1010 or 66. I didn't need a breakout box and I couldn't afford or need pro quality.

The advantage of a breakout box (aside from potentially having processing outside of the computer) is that when you need to make many connections in a short period of time it's easier to make the connections above the desk and to troubleshoot routing problems. The 1010 & 66 breakout boxes also accept balanced TRS connections which is a big deal if you are using long cable runs. 

If you are using a mixer then the connection advantage of a breakout box can be overcome. Another advantage of using a mixer is preamps which are really to important to have with mics. A mixer is generally an affordable way to get a bunch of them. You can buy really good ones separately but then we're talking about pro gear again. If you do use a mixer you really want to go 1:1 with your connections. Anything going into the mixer will need it's own output/input to your soundcard.

---

### Post by jukingeo on 2008-10-04
> **paulg said:**
> I use a 1010-LT. It has more features and inputs than the 1010 or 66. I didn't need a breakout box and I couldn't afford or need pro quality.


Yes, I found it weird that the 1010-LT DOES have XLR balanced pre-amped inputs.  The standard 1010 doesn't have XLR's nor pre-amps.  Yet, the 1010-LT is by far cheaper.  

My concern was that I do hook up mixers and outside line sources to my computer.  So I was worried about line/connection inconsistencies and the introduction of noise.  

I guess one way around the problem with the 1010lt is to run very short connections to a patch bay and do the XLR/TRS conversions there.  This way essentially you would have a nice breakout box/patch point.

Surprisingly in my dealings with audio equipment repair, I find the traditional RCA connection as second in reliability next to the XLR connection.  1/4" connections are next in line.  They do get 'dirty', but are easily cleaned up. 1/8" connections are the worst.  I have trouble with them all the time on computer/tv/ipod sound systems. They get really dirty after about a year or so of use and because of the small size, they break easy.  I have the most trouble with this connection.

So if you are not going to make many changes to your system (during use...meaning you have pretty much one type of setup), you keep your connections short, and you don't intend to move your system around a lot then I would say, yeah, you are much better off with the 1010lt.

In my case, I know I am going to patch in mixers, video units, etc so I do like the convenience of a breakout box and I sure don't want to crawl around to the back of the computer every time I have to "repatch".

I might look into the 1010lt / patchbay approach I mentioned above, but for right now I just want to really see what I can do in Linux.  So it looks like finally I can attain that goal.

I must say though that even though M-Audio may not be the best product on the market, the company itself seems to be first rate.  They are offering a lifetime warranty on the items, they are providing Linux support top to bottom for their products and best of all, it is automagically recognized in most Linux distributions.   So in one night all my audio problems were put to bed once and for all (at least so far), so I am much thankful for that alone.

Geo

---

### Post by Stochastic on 2008-10-04
> **jukingeo said:**
> they are providing Linux support top to bottom for their products and best of all, it is automagically recognized in most Linux distributions.

That's just simply not true.  They have yet to provide any info for the ffado developers on their firewire line.  Take a look: [http://www.ffado.org/?q=devicesupport%2Flist&filter0=M-Audio&filter1=&op2=OR](http://www.ffado.org/?q=devicesupport%2Flist&filter0=M-Audio&filter1=&op2=OR)

Their PCI cards have been around a long time, so they're very well supported in ALSA, but their newer cards simply aren't supported.  It's only a matter of time before they discontinue those older lines, or change their architecture.  As far as I can tell the policy change was probably implemented during the Avid (the guys who design protools stuff) takeover of M-Audio (read more about it here: [http://www.maudio.co.uk/news/en_gb-352.html](http://www.maudio.co.uk/news/en_gb-352.html)).  This really is a shame because their earlier linux support policy was top notch - they even attempted to release their own GPL linux drivers at one point (if my memory serves correct).  My assumption is that Avid doesn't want the Ardour world to impinge on their semi-pro DAW market stranglehold.

---

### Post by whistlingtony on 2008-10-06
Hmm...

Ok, I'm going for the 1010lt. 

Now, if I'm just dorking around by myself, I can use the two XLR connectors for my voice and my guitar. Great!

Heh, I've been doing a lot of reading. TweakHeadz is a good site! 

If I want friends... I'm going to need a mixer with enough outputs... and some 1/4" to RCA adaptors? 

Might I use a Multichannel Mic Preamp with said adaptors to get the same effect?  Err... something like....

[http://pro-audio.musiciansfriend.com/product/SMPro-Audio-PR8E-Multichannel-Microphone-Preamplifier?sku=187700](http://pro-audio.musiciansfriend.com/product/SMPro-Audio-PR8E-Multichannel-Microphone-Preamplifier?sku=187700)

Thanks guys!

-Tony

---

### Post by thorgal on 2008-10-06
... I wouldn't use my guitar on one of the XLR input of the 1010LT, it's meant for MIC levels, not line level.

---

### Post by jukingeo on 2008-10-06
> **Stochastic said:**
> That's just simply not true.  They have yet to provide any info for the ffado developers on their firewire line.  Take a look: [http://www.ffado.org/?q=devicesupport%2Flist&filter0=M-Audio&filter1=&op2=OR](http://www.ffado.org/?q=devicesupport%2Flist&filter0=M-Audio&filter1=&op2=OR)

I wasn't referring to anything OUTSIDE of the Delta Line.  The firewire line is a different animal and I am not going anywhere near firewire with Linux for a while.  At least not until FFADO is under full release AND comes standard with Jack.

> Their PCI cards have been around a long time, so they're very well supported in ALSA, but their newer cards simply aren't supported.  It's only a matter of time before they discontinue those older lines, or change their architecture.

I was referring to the Delta PCI card line only.   Yes, I did notice that from the documentation that I received with my Delta 44 that it does appear to be a very old line.  The documentation covers older operating systems back to Windows 98 on up to Windows 2000.  There is no mention of ME or newer OS's, but the website does have XP drivers for it.

That will suck if they do discontinue the Delta line after all this time.  So far my Delta 44 works VERY well with Linux and I have not found a single hickup as of yet.

>  As far as I can tell the policy change was probably implemented during the Avid (the guys who design protools stuff) takeover of M-Audio (read more about it here: [http://www.maudio.co.uk/news/en_gb-352.html](http://www.maudio.co.uk/news/en_gb-352.html)).  This really is a shame because their earlier linux support policy was top notch - they even attempted to release their own GPL linux drivers at one point (if my memory serves correct).

They DO have a Linux driver listed on their site.  Linux is among the choices for driver downloads.  That was one of the deciding factors governing the purchase of the Delta 44.  It seemed to be well supported.  However, it didn't even come to that.  I just plugged the card into my machine and it was good to go.


>  My assumption is that Avid doesn't want the Ardour world to impinge on their semi-pro DAW market stranglehold.

Well, if there isn't going to be support for M-Audio sound devices in the future, that will suck big time.  It is very bad as it is to fine pro (or semi-pro) audio cards that will work in Linux.   If M-Audio will not support the newer lines, then that will only leave Hammerfall, and those cards are way too expensive for those that have home project studios.

So, Avid is scared of Ardour, huh?  I guess Ardour is THAT good then.   I am just starting to play with it now, so I really don't know my way around the program.   It is all new to me.  Granted I been with Linux for 4 months now, but up to now that four months was spent struggling to get proper audio on my system.

I am thinking I should pick up another Delta card for my "future" Linux machine.  May as well get it before they axe the Delta line.

Geo

---

### Post by jukingeo on 2008-10-06
> **whistlingtony said:**
> Hmm...

Ok, I'm going for the 1010lt. 

Now, if I'm just dorking around by myself, I can use the two XLR connectors for my voice and my guitar. Great!

Heh, I've been doing a lot of reading. TweakHeadz is a good site! 

If I want friends... I'm going to need a mixer with enough outputs... and some 1/4" to RCA adaptors? 

Might I use a Multichannel Mic Preamp with said adaptors to get the same effect?  Err... something like....

[http://pro-audio.musiciansfriend.com/product/SMPro-Audio-PR8E-Multichannel-Microphone-Preamplifier?sku=187700](http://pro-audio.musiciansfriend.com/product/SMPro-Audio-PR8E-Multichannel-Microphone-Preamplifier?sku=187700)

Thanks guys!

-Tony

You can't use a mic XLR input directly with a guitar.  That is an impedance mis-match.  Mic impedances are in the low to midrange (600ohms to 10k). A guitar's impedance is VERY high (1meg), so you are going to need a high impedance pre-amp or a dedicated guitar preamp to use with a 1010LT.

It was a shame that I couldn't get the Echo Mona to work, because it DID have switchable pre-amps in which it could switch from line level, to mic level, and guitar.

I don't know if the 1010lt has something that can switch the impedance of the mic inputs.  I doubt it since the inputs are XLR.  At any rate, you are probably better off with a guitar pre-amp box anyway.  Perhaps something with a vacuum tube in it to 'warm up' your guitar sound.

As for going RCA to 1/4", you could use a patchbay.  I remember that (years ago) Tascam had a patch bay that had RCA inputs on the back and 1/4" inputs on the front.   It will still be unbalanced, but it will give you up front 1/4" patch points. Could be the model PB-32P or PB-32R...something like that.

Geo

---

### Post by paulg on 2008-10-07
> **jukingeo said:**
> 
I don't know if the 1010lt has something that can switch the impedance of the mic inputs.  I doubt it since the inputs are XLR.  At any rate, you are probably better off with a guitar pre-amp box anyway.  Perhaps something with a vacuum tube in it to 'warm up' your guitar sound.
Geo

It does in fact! I know there are a couple different line level impedances for consumer/pro gear and there are a couple variations available by jumper settings. See page 7 of the manual - warning, it's a PDF:
[http://www.m-audio.com/images/global/manuals/Delta1010LT-Manual.pdf](http://www.m-audio.com/images/global/manuals/Delta1010LT-Manual.pdf)

I believe the delta line itself is about 10 years old. Would be nice to see someone come out with a newer card (PCI-e?) that's as affordable, as well supported and as long lasting as the Delta series. I don't care if it's M-Audio or not. The support has as much to do with the chipset by VIA as it does M-Audio. It's starting to become somewhat dated but there's still a lot of bang-for-your buck there.

The breakout box of the 1010 does in fact have balanced inputs. They are all TS/TRS unbalanced/balanced type 1/4" inputs. You'd likely want XLR->TRS converters to use standard XLR type patch cords. Not sure what the impedance of the inputs but you'll still probably want some mic preamps if you are plugging in a mic.

A friend of mine actually built a breakout box for his 1010LT. I think in all he spent as much money buying all the connectors and stuff as he would have spent on just getting the 1010 upfront.

---

### Post by jukingeo on 2008-10-08
> **paulg said:**
> It does in fact! I know there are a couple different line level impedances for consumer/pro gear and there are a couple variations available by jumper settings. See page 7 of the manual - warning, it's a PDF:
[http://www.m-audio.com/images/global/manuals/Delta1010LT-Manual.pdf](http://www.m-audio.com/images/global/manuals/Delta1010LT-Manual.pdf)

Oh, so it does have switchable pre-amps?  That is good then.  Then for guitar you would set it to around 1meg (or higher).

> I believe the delta line itself is about 10 years old. Would be nice to see someone come out with a newer card (PCI-e?) that's as affordable, as well supported and as long lasting as the Delta series. I don't care if it's M-Audio or not. The support has as much to do with the chipset by VIA as it does M-Audio. It's starting to become somewhat dated but there's still a lot of bang-for-your buck there.

Yeah, the Delta line seems to be dated, but it WORKS!   I been noticing this as a pattern with Linux support.  It seems like they can easily support items that are 5 to 10 years old.  But anything that is 4 years old or newer (with some exceptions, of course), seems to be a problem.   Overall I am getting the gist that Linux as a whole is pretty much behind the times in comparison to both Windows and the Mac.   While it would be nice to have more 'newer' items supported, the advantage to being somewhat behind is that you can breath new life into older gear.  Moreover, you could put a Linux system together for a fraction of the cost of a new PC or Mac and yet still have a fairly fast machine.

I have streamlined my Windows XP and as of now it is running almost as fast as Ubuntu.  But thus far (in my experience) nothing can touch Puppy Linux.  That sucker is really fast!

...getting back on track...

> The breakout box of the 1010 does in fact have balanced inputs. They are all TS/TRS unbalanced/balanced type 1/4" inputs. You'd likely want XLR->TRS converters to use standard XLR type patch cords. Not sure what the impedance of the inputs but you'll still probably want some mic preamps if you are plugging in a mic.

That I am well aware of.  Because there are no pre-amps on the standard 1010 it is probably set at line level impedances.  More then likely 10k. 

> A friend of mine actually built a breakout box for his 1010LT. I think in all he spent as much money buying all the connectors and stuff as he would have spent on just getting the 1010 upfront.

Yes, that would be correct.  Unless you have access to surplus, making your own breakout box is ludicrous.  You CAN modify a patch bay and that would be cheaper.  But I think it would be better to by a standard 1010 and then buy a pre-amp for it.  This way you can decide what inputs you want, if you want SS or tube based technology.

I think what I am going to do is buy a couple of tube based condenser microphones and use them when I need a mic in a pinch.  For more elaborate work, I have my Mackie 1402 mixer that I can use.

For the most part, I want to hang a condenser mic over my desk for doing voice overs on videos and perhaps for video-phone conferencing (Skype) and streaming live work.

One thing I did notice about the M-Audio Delta Line is that they are linkable (at least in Windows).  You can have up to 4 cards running in Windows. 

I did think about the idea of also getting the 1010LT and using it WITH the Delta 44 I just got.  This way I would have some choice over balanced/unbalanced connections.  However, I have heard it is a fiasco to get more than one card running with Linux.

A fellow friend of mine had much trouble to get a multi-channel virtual pipe organ to work with 2 Creative Audigy cards.  However, since that time has passed, I told him about the Delta 1010 already.  With a 1010 he just needs the one device.

At any rate I think I want to get a couple more of the M-Audio Delta cards because once they do change the line (as Stochastic says), it may be hard to find something on a semi-pro or pro level that will work in Linux.  Sure there is still the Hammerfall line, but that is too expensive for most people.  But one day I do want to get a Hammerfall card, when I set up my "pro" machine.

Geo

---

### Post by vinyldavid on 2008-10-20
Hey guys, I cannot seem to find how to run my 1010LT in Linux....what do you guys use?  I am looking at making my old desktop an audio recording machine.


What drivers/software are needed?

---

### Post by jukingeo on 2008-10-20
> **vinyldavid said:**
> Hey guys, I cannot seem to find how to run my 1010LT in Linux....what do you guys use?  I am looking at making my old desktop an audio recording machine.


What drivers/software are needed?

I didn't use anything.  I just plugged my Delta 44 in and it was automatically detected.   The 1010LT is part of the Delta series and it should be the same.

At any rate, what you should check out is your mixer levels.  A big problem is that they are initially set all the way down.  Go into your terminal and type "alsamixer".  An application will launch.  Make sure all your digital levels are up. I set all my Alsamixer PCM out controls up to the first red marker for each digital output (playback) option.

The mouse will not work in alsamixer...you need to use the keyboard only.

Once you get the levels up, open up something in You Tube (such as a music video) and raise and lower You Tube's volume.  You should hear something.

Once you get some kind of sound out of an application, you may want to use a gui application for controlling volumes.  In Ubuntu that application would be Envy24Control.   Most "other" gui Alsa Mixers do not seem to work.  If having a gui application for volume control isn't mandadory, you can always go back to the terminal and use Alsamixer.  That always seems to work.

Hope that helps!

Geo

---

### Post by vinyldavid on 2008-10-21
> **jukingeo said:**
> I didn't use anything.  I just plugged my Delta 44 in and it was automatically detected.   The 1010LT is part of the Delta series and it should be the same.

At any rate, what you should check out is your mixer levels.  A big problem is that they are initially set all the way down.  Go into your terminal and type "alsamixer".  An application will launch.  Make sure all your digital levels are up. I set all my Alsamixer PCM out controls up to the first red marker for each digital output (playback) option.

The mouse will not work in alsamixer...you need to use the keyboard only.

Once you get the levels up, open up something in You Tube (such as a music video) and raise and lower You Tube's volume.  You should hear something.

Once you get some kind of sound out of an application, you may want to use a gui application for controlling volumes.  In Ubuntu that application would be Envy24Control.   Most "other" gui Alsa Mixers do not seem to work.  If having a gui application for volume control isn't mandadory, you can always go back to the terminal and use Alsamixer.  That always seems to work..
Hope that helps!

Geo

Does Alsomixer support multiple input channels?  I am not worried about playback, as I will be exporting the stuff to my hard drive for editing on my Mac in Bias Deck and Bias Peak.

---

### Post by jukingeo on 2008-10-21
> **vinyldavid said:**
> Does Alsomixer support multiple input channels?  I am not worried about playback, as I will be exporting the stuff to my hard drive for editing on my Mac in Bias Deck and Bias Peak.

It should.  As of now I been mostly playing with outputs and my multiple outputs ARE labeled in Alsamixer, but they use obtuse labeling and you have to play with it to find out what it is.

The Envy24Control application was specifically meant for multiple in/out cards such as the Delta series.  It has a bit of a learning curve, but once you get it set, it is cool and you don't have to deal with the text based Alsamixer anymore.

---

### Post by nemo1945 on 2008-11-13
Well , actually the Delta1010lt does not seems to work with U.Studio 8.10 amd:confused:I think it was working with 8.04 i will try.
Yes , after testing , [COLOR="Red"]it works fine with 8.04 studi[/COLOR]o the problem then is on the side of my Graphic Card ATI X1250(no dual screen)

---

### Post by jukingeo on 2008-11-13
> **nemo1945 said:**
> Well , actually the Delta1010lt does not seems to work with U.Studio 8.10 amd:confused:I think it was working with 8.04 i will try.

Really?  That is a new one on me.  And not a pleasant one either. However, I AM still on 8.04.  I very rarely jump on the bandwagon when a new release comes out, I wait a while first.  I remember the problems I had initially with Hardy.  Now I finally got everything working right.  

I am surprised that it wouldn't work as the Delta line from M-Audio is usually pretty good with Linux in general.

As it is, there are very few sound options that work out of the box with Linux.  Sure hate to hear that the M-Audio Delta line has problems now.

So far I been having good luck with my Delta 44 on Hardy.  I probably will eventually upgrade to Intrepid, but I want to wait and see first how good it runs.  So far from your report about the 1010lt, it isn't reassuring.

Anyway, should you do find a way to get your card working, please post your findings back here.

Geo

---

### Post by nemo1945 on 2008-11-13
The level input is selectable and adjustable in the control panel!Thats an answer to a post telling that we cant connect a guitar to the unbalanced/balanced input1-2 of the Delta1010lt , i personally use it to record Electric Bass and it works fine

---

### Post by nemo1945 on 2008-11-13
[COLOR="Blue"]I very rarely jump on the bandwagon when a new release comes out, I wait a while first.[/COLOR]  That's Wisdom!But i was so happy to see my dual screen fonctionning

 So actually i am back to 8.04 i have other things to test , particularily Reaper under Wine and Wineasio:guitar:

---

### Post by jukingeo on 2008-11-14
> **nemo1945 said:**
> The level input is selectable and adjustable in the control panel!Thats an answer to a post telling that we cant connect a guitar to the unbalanced/balanced input1-2 of the Delta1010lt , i personally use it to record Electric Bass and it works fine

Do you have it set up with Envy24Control? 

Also did you go into the terminal and activate ALSAMIXER to make sure all the level controls are up?

If the answer to either or both is "No" then that could explain why you only have partial sound.

---

### Post by jukingeo on 2008-11-14
> **nemo1945 said:**
> [COLOR="Blue"]I very rarely jump on the bandwagon when a new release comes out, I wait a while first.[/COLOR]  That's Wisdom!But i was so happy to see my dual screen fonctionning

 So actually i am back to 8.04 i have other things to test , particularily Reaper under Wine and Wineasio:guitar:

Wow!  So the new version DOES cause problems, huh?  Another fellow was having problems with his Midisport...a device I also have.  I spent many hours to get the Midisport to be automatically recognized on start up.

I have battled close to 5 months trying to get sound to work in Linux in general.  So far things are finally coming together with Ubuntu Hardy.  At first I was starting to despise this version of Ubuntu, but once I bought the M-Audio Delta 44 and it worked right out of the box, I decided to stick it through.  I did the necessary updates to Hardy and I finally got the Midisport to work.  Everything is on ALSA and I am happy to say that I have FULL sound now in Hardy.  All my sound works.  Now of course this is 6 months later and Intrepid has been released.  But I think I am going to wait about 4 months or so before I decide to upgrade.  My main goal was to try out all the nice applications that Ubuntu Studio has to offer and I only recently began to do that.  So I am not going to jeopardize my set up just to have "the latest" update.

I think if you are working on Hardy, stick with it for a few months longer.  By then most of the issues would be straightened out and there will be fixes for them.

Overall I think it is better to be one version behind (unless the update has a feature you absolutely can't live without).

While Hardy did have it's problems, most of them were resolved by the 4th month of the release.

So I would still use Hardy if I were you, but keep Intrepid on your system.  Check back here often and watch for fixes.  Once you get things fully functional in Intrepid, then move on up to it.

I am right now using Ubuntu Studio Hardy, Puppy Linux 4.0, and Windows XP on a triple boot system.

---

### Post by nemo1945 on 2008-11-15
When i type alsamixer in the terminal , something appear , but does not look like a mixer...When i make a test in the system/sound/device select , it gives an error message.:(
It works well with 8.04 , but i'll quit for a while because i was not able to run any music application in Ubuntu , Ubuntu studio , specially with wineasio , was not able to install it, there is always something missing , or compilation error.To get something working i have to pass several hours finding a solution , for now i prefer to play music...
BTW , Jukingeo ,what's "Intrepid"?
Processor :Athlon 64X2 4000+
Mobo:Gigabyte GA-MA69GM-S2H
Sound:M-Audio delta 1010LT PCI not functioning
Graphic:Radeon Ati X1250 build in only 1024x768

---

### Post by jukingeo on 2008-11-15
> **nemo1945 said:**
> When i type alsamixer in the terminal , something appear , but does not look like a mixer...

I don't know how long you been on computers but if you know of DOS or text based operating systems, ALSAMIXER will have a DOS-Like look and feel.  It will NOT operate with the mouse.  It will only operate from the keyboard.  In simpler terms, you should get something that looks like this:

[http://www.flickr.com/photos/betacontinua/2464351490/](http://www.flickr.com/photos/betacontinua/2464351490/)

If you don't get something that somewhat looks like that, there is something seriously wrong.[/QUOTE]

> When i make a test in the system/sound/device select , it gives an error message.:(

I am not familiar with that kind of test.

> It works well with 8.04 , but i'll quit for a while because i was not able to run any music application in Ubuntu , Ubuntu studio , specially with wineasio , was not able to install it, there is always something missing , or compilation error.To get something working i have to pass several hours finding a solution , for now i prefer to play music...

Are you also having any kind of problems in 8.04? Are you using anything other than ALSA?  I have an ALSA only set up.  No OSS, No Pulse, no anything kind of layering going on with my system.  I am able to play back MP3's, play games, listen to streaming audio (Internet:YouTube, etc).

However, I have noticed that some of the Ubuntu Studio applications are picky and many do not like or cooperate well with ALSA.  However, those same applications allow the use of Jack.  I HIGHLY recommend getting Jack to work with your sound device FIRST.  THEN most of the Ubuntu Studio applications can be set up and routed via Jack.  Since you have the 1010lt, that has vastly more I/O options than my card which is only 4in/4out analog.  If I were in your shoes, learning to set up and use Jack is a MUST.  Once you get the ALSA driver working with Jack everything pretty much falls into place.  You launch your Ubuntu Studio applications...but make sure you set everything (including Jack) to the same sample frequency.  Then you go into Jack's "Connections" and you use it like a patch bay and connect your applications to and fro each other.  Jack does the rest and outputs everything via ALSA to your sound device.

Jack isn't the easiest to use for a newbie, but there isn't much to it and once you learn it, it will just provide a huge leap forward in learning Linux audio based applications. 

I will say that I don't have everything going through Jack, just the "pro-audio" apps and Wine.  Streaming internet, my MP3 player, & games go to ALSA directly.

> BTW , Jukingeo ,what's "Intrepid"?

Ubuntu versions go by means of identification:  1) numercial 2) an actual name.

You already know the number variants, but you will find that many refer to them by name.  These are the names as far as I remember back

6.04  Dapper Drake
6.10  Edgy Eft
7.04  Feisty Fawn
7.10  Gutsy Gibbon
8.04  Hardy Herron
8.10  Intrepid Ibex

You will notice a pattern in the names.  All are two worded adjective-animal associations. They are also in alphabetical order.

Just in case you don't know, a Drake is a duck, an Eft is a salamander, a Gibbon is a monkey, a Herron is a bird, and an Ibex is a type of mountain goat.

However, many that refer to the Ubuntu versions by name instead of number, cut the animal part of the name off and just refer to the version by the adjective part alone.

So version 8.10 will be referred to as just "Intredpid", Version 8.04 will be referred to as just "Hardy", Version 7.10 will be referred to as just Gutsy.  You probably will no longer hear much talk of versions beyond Gutsy.  The Ubuntu forums usually drop support for 2nd oldest version upon a new version's release...thus Gutsy is now officially no longer supported.  However, lately since there were major problems with Hardy (8.04) when it first was released, there are still many people using Gutsy (7.10).  I still even see some people using versions as old as 6.10.

When I started with Linux, my first version was 6.10.  At that time version 8.04 was just released and I was told to upgrade as soon as possible.  So I did so.  Shortly after I was experiencing many problems with version 8.04 and I ALMOST went back to version 7.10 as I was told that that 7.10 was much more stable.  However, Ubuntu Studio was the version I was after and back then it didn't have as many features as it does with version 8.04.  So I hung in there and finally solutions did become available.  Granted, it took me over 5 months alone to get everything finally working.  The biggest help for me was the purchase of the M-Audio Delta 44 audio device.  That solved many of my audio problems in one swift swoop!

So all in all, I really do not want to rock my boat of my NOW working version 8.04.  So Intrepid is going to wait for a while.  Although I do admit, the Intrepid Ibex background screen is AWESOME!  The Ubuntu backdrops are WAY better than anything that came with Windows.

> 
Processor :Athlon 64X2 4000+
Mobo:Gigabyte GA-MA69GM-S2H
Sound:M-Audio delta 1010LT PCI not functioning
Graphic:Radeon Ati X1250 build in only 1024x768

Hmmm, I am not familiar with AMD processors as I been all my computer life with Intel.  I did aquire an old AMD K6-2/400 though and I am going to use that for a Linux based MAME project.  One thing though, I did notice "64" in that processor name.  64 bit machines inheritly have more problems with setup than their 32 bit counterparts.  So you do have to make absolutely sure that your programs you set up are made for a 64 bit machine.  That also includes the OS itself.

I never had a 64 bit machine, but I have heard of the setup nightmares for Linux.  I am sure though as the Ubuntu versions go on, 64 bit support will get better and better.

BTW, did you ever try 64Studio?  It is a Debian based OS that was initially designed specifically for 64 bit machines.  I personally tried the 32 bit version for my machine, though, and I didn't like it.  Audio application wise it is a good program, but it is horrible with regular housekeeping tasks.  Navigating was a bit awkward for me.  So I ended up coming back here to Ubuntu.  Ubuntu also has the best support base and a HUGE community following.  Ubuntu is truly the beginners Linux distribution.  So you are in the right place if you are a beginner.  I still consider myself a beginner even though I been 6 months on the operating system.   As I pointed out earlier, I am bouncing around between Linux distributions and for a good portion of my work, I am still using Windows XP.  But all of my internet surfing, emails, letter writing, picture editing, classic console game playing...that I all do now in Ubuntu Studio.

Anyway, I have to run now, this post become somewhat of a "novel".

Have a good day and I do hope that you get your issue solved.

Geo

---

### Post by jukingeo on 2008-11-15
Deleted-Bum post

---

### Post by Reeman on 2009-03-04
The behringer copies of the akg studio condenser cost about 120 bucks and are great. I use two of them through a mackie 1202 and find the s/n ratio is simply as good as any commercial stuff that costs 1000 bucks! As far as the M-audio cards go the 24/96 is great in so much as you can gang them and do 4 track at full 24/96. Sure they do not have a mic pre-amp but that is a positive. They are easy to use and the alsa support is fool proof. 

To get mikes as good as the cheapo behringer condensers you would need to spend plenty and to get something better than the audiophile 24/96 cards would also cost a lot more.

---

### Post by milkmachine on 2009-12-07
I just installed Ubuntu Studio 9.10 and had a little trouble getting my Delta 1010 to be recognized by pulseaudio. After a few hours of searching around, and finally getting it, I thought I'd throw up a little tutorial for people who like the step-by-step approach.

How to get your Delta 1010 to work with Ubuntu 9.10 through pulseaudio:
[http://www.milkmachine.org/delta1010.html](http://www.milkmachine.org/delta1010.html)

---

### Post by thoti73 on 2010-02-28
-.öl> **milkmachine said:**
> I just installed Ubuntu Studio 9.10 and had a little trouble getting my Delta 1010 to be recognized by pulseaudio. After a few hours of searching around, and finally getting it, I thought I'd throw up a little tutorial for people who like the step-by-step approach.

How to get your Delta 1010 to work with Ubuntu 9.10 through pulseaudio:
[http://www.milkmachine.org/delta1010.html](http://www.milkmachine.org/delta1010.html)

Dude, I've been looking for a solution for days now! Thanks for sharing!

---

