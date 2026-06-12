---
title: "Analogue/Digital Interface Reccomended Hardware"
date: 2008-06-18
forum: Ubuntu Studio
---

### Post by jenny_thinkpad_t61p on 2008-06-18
Hello,

I'm looking for a reasonable quality analogue/digital converter for my Thinkpad T61p Laptop running Ubuntu HH 8.04.

I am considering the Focusrite Sapphire (firewire) (£250) or Edirol FA-66(firewire) (£190) or RME Cardbus interface (£550).

The focusrite and Edirol both support high quality conversion and seem to supported by linux though in the case of the Focusrite this seems to be specifically the Sapphire LE (£200) and not the Sapphire Pro, though they seem to be ostensibly the same unit for the drivers this is an assumption.

The RME Cardbus seems to be supported but I would like conformation of this, though this is a little expensive for me.

Does anyone have any experience of this I wish to have high quality mic samples taken into my machine, I will run the rt kernel for this application, probably UbuntuStudio 8.04.

As a final question, do I need to disable the Thinkpad built in soundcard somehow to use a different audio interface.

Thankyou

---

### Post by Stochastic on 2008-06-18
No disabling of your internal soundcard will be needed, just tell Jack to use the big one and that's what he'll do.

Focusrite's Saffire LE and Saffire Pro are both well supported from what I remember (if the Pro isn't working under freebob, then it's for sure supported well under ffado).  The downside of those cards is that the onboard DSP processing that you pay so much extra for is not supported in linux.  Also, freebob doesn't have mixer support (ffado does, but it's a bit of work to get running on 8.04 - but doable), so you're forced to have a stereo output (the 8 output channels turn into 4 stereo output pairs, all playing the same thing).  Overall, they're good cards though - but keep in mind the preamps aren't the ones focusrite are famous for.

The Edirol is also one I've heard good things about, but I haven't have the pleasure of working with it or hearing the results.

I use a Presonus Firepod (now sold as an FP10) and really do like the bang-for-the-buck that it offers.  The preamps are a little flatter/cleaner than the Focusrite's.

I've never seen/heard anything about the RME so I can't comment on that one.

Let us know what you end up doing.  And good luck.

---

### Post by jukingeo on 2008-07-19
> **Stochastic said:**
> No disabling of your internal soundcard will be needed, just tell Jack to use the big one and that's what he'll do.

Focusrite's Saffire LE and Saffire Pro are both well supported from what I remember (if the Pro isn't working under freebob, then it's for sure supported well under ffado).  The downside of those cards is that the onboard DSP processing that you pay so much extra for is not supported in linux.  Also, freebob doesn't have mixer support (ffado does, but it's a bit of work to get running on 8.04 - but doable), so you're forced to have a stereo output (the 8 output channels turn into 4 stereo output pairs, all playing the same thing).  Overall, they're good cards though - but keep in mind the preamps aren't the ones focusrite are famous for.

The Edirol is also one I've heard good things about, but I haven't have the pleasure of working with it or hearing the results.

I use a Presonus Firepod (now sold as an FP10) and really do like the bang-for-the-buck that it offers.  The preamps are a little flatter/cleaner than the Focusrite's.

I've never seen/heard anything about the RME so I can't comment on that one.

Let us know what you end up doing.  And good luck.

Hello Stochastic,

Good thing I found this thread.  Anyway, I do want to do something similar.  

A couple of days ago I was working on partitioning a USB drive and an unfortunate "accident" in that process had me wiping my Windows XP partition to kingdom come.  Since I know I had a hard time setting up my SoundBlaster X-Fi BOTH here in Ubuntu AND Windows, I feel it is time to bid it adieu.

So the past two days I been searching for a good replacement.  As you may recall I do have Ubuntu Studio and I DO want to use Linux for audio editing and mastering.

Keeping costs to a minimum I alloted a $300 budget for a new audio device.  So I started to look for a direct PCI solution and the closest I came was the Echo Gina 3G ($279).   This card has 2 in's and 6 outs, but it does have both kinds of digital I/O and it has Midi.

However, if I were to go the firewire route, I could enter myself into the Focusrite Saffire series which is regarded has a high end piece.  There are two models in my price range and that is the Saffire and the newer Saffire LE.

I am torn between these two units as the original Saffire offers the DSP effects on board and also 192khz capability.  It has 2 analog ins / 8 analog outs, SPDIF Digital I/O and Midi.   The Saffire LE differs in that it only has 96khz capabilty and it is lacking the DSP, but the analog input/output is 4 x 6.  The digital and midi are the same.  The price difference between the two is $299 (saffire) and $249 (Saffire LE).

So I am having trouble making up my mind.  I do like the idea of the DSP AND the 192khz capability of the original Saffire.  However, as you answered above, more then likely I wouldn't be able to use the DSP in Linux. Sure I am still going to have Windows and can use it there.  But it would be paying for something I only use half the time.  The only saving grace then for the original Saffire is the 192khz capability.  While I do want this capability I would only need to go that far IF there is a night and day difference from recording 192k vs 96k.  Because all said and done, I prefer the 4in 6 out configuration of the LE over the 2in 8out configuration of the original Saffire.

Now the next question would be this:

Since both Saffire's are firewire devices, they will only work through Jack via FreeBob.  That poses a problem because I don't know of a way to route system sounds, MP3 player sounds, internet audio and all regular sound devices (that don't use Jack), to use Jack.

So my proposal would be to take out the X-Fi card and put back in the old SoundBlaster Live that came with my computer (as we know the Soundblaster Live IS Linux compliant).  All my system and regular applications would go through this card.  Then I assume that I could route the output (internally) of the Saffire through Jack to the SoundBlaster Live.  I do intend on using two different speaker sets.  One is a surround subwoofer system where the SB Live would be hooked up to and I have a pair of KRK monitors which would be hooked up to the Saffire.  BUT I know that there will be many a day I want to process something through the Saffire and output it with my sound through the computer.

Would you think this is possible?  I would think so, but I am not sure.  I don't want to spend close to $300 on a audio interface to not have the proposed situation work.

Finally, I am not sure how knowledgeable you may be in this area, but how well is 192khz recording frequency supported in Linux?  I looked through some of the programs in Ubuntu Studio and only a handful do support this frequency.  Jack, however, can support BEYOND this frequency.  Thank fully Ardour seems to support it.  Most seem to be hovering in the 96k support with a few that can only go to 48k <sticking finger down throat>.

Anyway I would appreciate any opinions or suggestions you may have.

Thank You,

Geo

---

