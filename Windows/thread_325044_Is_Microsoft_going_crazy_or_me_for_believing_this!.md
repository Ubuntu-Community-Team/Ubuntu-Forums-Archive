---
title: "Is Microsoft going crazy or me for believing this??!"
date: 2006-12-24
forum: Windows
---

### Post by riven0 on 2006-12-24
I don't know whether to take this seriously or not. :confused: 

Can somebody read this and tell me if I'm going crazy or Microsoft really going to do this???!!

> The Vista Content Protection specification could very well constitute the
longest suicide note in history.

Some "features" of Vista:

> Indirect Disabling of Functionality
-----------------------------------

As well as overt disabling of functionality, there's also covert disabling of
functionality.  For example PC voice communications rely on automatic echo
cancellation (AEC) in order to work.  AEC requires feeding back a sample of
the audio mix into the echo cancellation subsystem, but with Vista's content
protection this isn't permitted any more because this might allow access to
premium content.  What is permitted is a highly-degraded form of feedback that
might possibly still sort-of be enough for some sort of minimal echo
cancellation purposes.

> Decreased Playback Quality
--------------------------

Alongside the all-or-nothing approach of disabling output, Vista requires that
any interface that provides high-quality output degrade the signal quality
that passes through it.  This is done through a "constrictor" that downgrades
the signal to a much lower-quality one, then up-scales it again back to the
original spec, but with a significant loss in quality.  So if you're using an
expensive new LCD display fed from a high-quality DVI signal on your video
card and there's protected content present, the picture you're going to see
will be, as the spec puts it, "slightly fuzzy", a bit like a 10-year-old CRT
monitor that you picked up for $2 at a yard sale. 

> Denial-of-Service via Driver Revocation
---------------------------------------

Once a weakness is found in a particular driver or device, that driver will
have its signature revoked by Microsoft, which means that it will cease to
function (details on this are a bit vague here, presumably some minimum
functionality like generic 640x480 VGA support will still be available in
order for the system to boot).  This means that a report of a compromise of a
particular driver or device will cause all support for that device worldwide
to be turned off until a fix can be found.  Again, details are sketchy, but if
it's a device problem then presumably the device turns into a paperweight once
it's revoked.  If it's an older device for which the vendor isn't interested
in rewriting their drivers (and in the fast-moving hardware market most
devices enter "legacy" status within a year of two of their replacement models
becoming available), all devices of that type worldwide become permanently
unusable.

Whole report [here]("http://www.cs.auckland.ac.nz/~pgut001/pubs/vista_cost.txt"). Or read about it on [Digg]("http://digg.com/tech_news/Vista_security_spec_longest_suicide_note_in_history").

---

### Post by pay on 2006-12-25
Well with Microsoft, you defintely don't get what you pay for. Limiting lisence agreements, virus..etc. I'm glad that I'm never going back to Windows.:)

---

### Post by cilynx on 2006-12-25
Sadly, many of us still have to support the unwashed masses who will always buy the next chunk to come out of Microsoft.  I don't feel bad pirating Vista as I have a pile of Windows licenses that I paid for against my will when I bought my laptops and have never used.

---

### Post by BoyOfDestiny on 2006-12-25
> **riven0 said:**
> I don't know whether to take this seriously or not. :confused: 

Can somebody read this and tell me if I'm going crazy or Microsoft really going to do this???!!




I posted the same link in a thread  here. :)

Maybe our threads should be merged?
[http://ubuntuforums.org/showthread.php?t=324483](http://ubuntuforums.org/showthread.php?t=324483)

Anyway, sadly, all true. It's been planned for quite a while...

Google: 
tcpa
palladium MS
trusted computing

Although MS isn't alone in this, OSX features DRM in regard to where you can install the OS and iTunes type stuff... 
I find MS's application of DRM ridiculously intrusive, and as the article illustrates, more damaging for all Personal Computer users...

---

### Post by riven0 on 2006-12-25
> **BoyOfDestiny said:**
> I posted the same link in a thread  here. :)

Maybe our threads should be merged?
[http://ubuntuforums.org/showthread.php?t=324483](http://ubuntuforums.org/showthread.php?t=324483)



Hey, I didn't see that! :D 

Yeah, these threads should be merged.

---

### Post by 3rdalbum on 2006-12-26
Denial-of-service for drivers is probably not going to be used. Microsoft doesn't care about 3rd-party security. And besides, I thought drivers were going to run in user-space in Vista?

What really annoys me is the "all-or-nothing" content disabler. I work at an electrical store, where all the plasma and LCD TVs are not compatible with the DRM. My boss and I are dreading the day when people start complaining that their new TVs aren't working with hi-definition content.

Apparantly, Blu-ray discs will contain the same sort of thing as the driver denial. If an encryption key is stolen from a Blu-ray DVD player and distributed online, it will be possible for the studios to implement a "kill-switch" for that model of DVD player, and include it on every new Blu-ray disc. Scary stuff.

---

### Post by kevinf311 on 2006-12-26
Did you hear? The ration of chocolate was increased to 20 grammes today. :-| 

Anyone else seeing some parallels here? Since when did Macrosoft (and Sony for that matter) gain the power to render hardware useless? I don't know how they can expect people to swallow software *they* paid for making hardware they *own* worthless (on said software). How is this not illegal? If I put a script in some hypothetical program I wrote that accessed third party drivers and commented out all of the useful bits, I'd be sued for all I was worth inside a month. 

I'm sure ms thinks that they are being noble and creating a more elite world of hardware/software compatibility by forcing others to comply with their white list. "Pay us $X for the OS, pay $X more to have only the premium hardware specs, then if we feel like a hardware provider isn't keeping up we'll axe them and force you to pay $X over again to maintain your system." They completely skipped Monopoly and went straight to Tyranny. :mad: 

I'm all for protection of content. Not everything can be free. People need money. Pirating music/video doesn't go into that persons (creator) house and start breaking crap. What happens to the people like me that follow the "Rule of 3" or something similar where one downloads up to three songs from an artist and upon reaching three songs decides they like the artist enough to buy an album or two (or more in a lot of cases)?

Putting performance degrading code into an OS only fans the flames under the people most eager to crack and disarm it.
 </rant> :rolleyes: Sorry for the vent.

---

### Post by BoyOfDestiny on 2006-12-26
> **kevinf311 said:**
> Did you hear? The ration of chocolate was increased to 20 grammes today. :-| 

Anyone else seeing some parallels here? Since when did Macrosoft (and Sony for that matter) gain the power to render hardware useless? I don't know how they can expect people to swallow software *they* paid for making hardware they *own* worthless (on said software). How is this not illegal? If I put a script in some hypothetical program I wrote that accessed third party drivers and commented out all of the useful bits, I'd be sued for all I was worth inside a month. 

I'm sure ms thinks that they are being noble and creating a more elite world of hardware/software compatibility by forcing others to comply with their white list. "Pay us $X for the OS, pay $X more to have only the premium hardware specs, then if we feel like a hardware provider isn't keeping up we'll axe them and force you to pay $X over again to maintain your system." They completely skipped Monopoly and went straight to Tyranny. :mad: 

I'm all for protection of content. Not everything can be free. People need money. Pirating music/video doesn't go into that persons (creator) house and start breaking crap. What happens to the people like me that follow the "Rule of 3" or something similar where one downloads up to three songs from an artist and upon reaching three songs decides they like the artist enough to buy an album or two (or more in a lot of cases)?

Putting performance degrading code into an OS only fans the flames under the people most eager to crack and disarm it.
 </rant> :rolleyes: Sorry for the vent.

++

If I downloaded a song from an artist I like, I pick up an album (I'm not an RIAA fan so I find the CD used in that case :) then rip to flac/ogg )

Bonus points for the 1984 reference. :) Orwell definitely had foresight.

---

### Post by smoker on 2006-12-26
> 
Quote:
The Vista Content Protection specification could very well constitute the
longest suicide note in history.


> They completely skipped Monopoly and went straight to Tyranny.  

if you think this is piracy and drm protection, wait until a little while down the road, after, crack, fix, - ms updates! crack, fix, - msupdates with even more severe restrictions.

why anyone would want to try vista, never mind paying for it is beyond a simple guy like me.

ms suicide note - well, no empire lasts forever!

---

### Post by blitze on 2006-12-26
This goes far beyond DRM and content protection.  This is controlling content distribution which has been a goal for MS for a long time.

I also think this will tie inwith their 3rd party hardware projects like X-Box and Zune.

I hope they pay royally for this and the Digital World is a better place for their stuffup.

---

### Post by 3rdalbum on 2006-12-27
I bought a DVD recorder/VCR combo today. Unfortunately, I've now found that it's full of DRM - it won't let you record a copy-protected video onto DVD.

That's the horrible thing about DRM. Like Soviet Russia, it assumes you are guilty and does not allow you to prove your innocence.

---

### Post by steven8 on 2006-12-27
What I read on the one site made me wonder a bit.  It said that MS was attempting to prove to film companies that their products were safe from piracy on a computer.  I will NOT own Vista, and I hate what Microsoft is doing, but I wonder how much of this is the product of outside pressuring for anti-piracy.

---

### Post by adewale on 2006-12-27
this may sound like a dumb question but i came across an article about vista demanding that any hardware that would work on vista its specs must be closed and mustn't write any open source drivers.i can't remember where i saw the article.

---

### Post by bobbybobington on 2006-12-28
If this continues the next windows after vista will be called windows riaa/mpaa edition 

The scariest part of this is most people don't know or care about this.

---

### Post by smoker on 2006-12-28
> **bobbybobington said:**
> If this continues the next windows after vista will be called windows riaa/mpaa edition 


i think vista is RC1 of this:mad:

---

