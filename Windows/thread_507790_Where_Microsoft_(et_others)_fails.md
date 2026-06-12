---
title: "Where Microsoft (et others) fails"
date: 2007-07-23
forum: Windows
---

### Post by vrangforestillinger on 2007-07-23
My father was trying to watch a DVD on his new LCD-tv the other day with his laptop. He could not get it to work, and asked me to look at it. He was using Windows Media Player, and it said that it was unable to play the DVD because it could not activate the analog copy protection on that screen (the LCD-tv). (However that works)

Typical scenario: NN wants to protect copyrights. NN implements system with the purpose to hinder pirates to copy the copyrighted material. Pirate cracks the code, normal user is stuck not being able to use the material the way he wants, even thought his usage is not violating the copyright.

My father was quite irritated, as he felt that MS was treating him as if he was trying to violate the copyright.

I said I did not know how to solve it, but that I did know that I would never encounter such problems in Ubuntu.  (Right?)

My father fixed it by using some other DVD-player for Windows.

---

### Post by kamaboko on 2007-07-24
The more "likely" scenario was that the other video player he installed had the codec he needed.  So if I'm able to watch a DVD on Linux with one video player and not another it must be due to Linux imposing copy right protection?

---

### Post by dca on 2007-07-24
Was the DVD protected by Macrovision?

---

### Post by vrangforestillinger on 2007-07-24
> **kamaboko said:**
> The more "likely" scenario was that the other video player he installed had the codec he needed.  So if I'm able to watch a DVD on Linux with one video player and not another it must be due to Linux imposing copy right protection?

Uhm, no. According to Windows Media Player, the problem was not that it missed some codec. If it did, my experience is that it tries to download the missing codec. The error message said that MP was "unable to activate analog copy protection".

Furthermore, he was able to play the DVD as long as he did not plug in the external TV-screen. Doesnt sound like a codec problem to me. 

He also tried to update his drivers, but it seems Windows Media Player is unable to play this DVD on the external screen due to some copy protection system.

> **dca said:**
> Was the DVD protected by Macrovision?

It did not have any labels about that. Don't know.

---

### Post by kamaboko on 2007-07-24
> **vrangforestillinger said:**
> Uhm, no. According to Windows Media Player, the problem was not that it missed some codec. If it did, my experience is that it tries to download the missing codec. The error message said that MP was "unable to activate analog copy protection".

Furthermore, he was able to play the DVD as long as he did not plug in the external TV-screen. Doesnt sound like a codec problem to me. 

He also tried to update his drivers, but it seems Windows Media Player is unable to play this DVD on the external screen due to some copy protection system.



It did not have any labels about that. Don't know.

I currently have XP and Vista Ultimate feeding to HD LCD TV's.  I play DVD's on both of them and have never seen that code before.

---

### Post by BoyOfDestiny on 2007-07-24
> **vrangforestillinger said:**
> Uhm, no. According to Windows Media Player, the problem was not that it missed some codec. If it did, my experience is that it tries to download the missing codec. The error message said that MP was "unable to activate analog copy protection".

Furthermore, he was able to play the DVD as long as he did not plug in the external TV-screen. Doesnt sound like a codec problem to me. 

He also tried to update his drivers, but it seems Windows Media Player is unable to play this DVD on the external screen due to some copy protection system.



It did not have any labels about that. Don't know.

Sounds like DRM to me.

"Vista's content protection mechanism only allows protected content to be sent over interfaces that also have content-protection facilities built in."
...
"Similarly, component (YPbPr) video will be disabled by Vista's content protection, so the same applies to a high-end video setup fed from component video."
[http://www.cs.auckland.ac.nz/~pgut001/pubs/vista_cost.html](http://www.cs.auckland.ac.nz/~pgut001/pubs/vista_cost.html)

You could always experiment and tell him to buy a new tv out card, and possibly a new tv (with hdcp support...) ;) Sounds fair right? :(

---

### Post by smoker on 2007-07-24
>  You could always experiment and tell him to buy a new tv out card, and possibly a new tv (with hdcp support...) :wink: Sounds fair right? :sad:

darn it, seems i would have to look for a 'vista capable' tv if i was using it, lol, i think i will stick to linux :-)

---

### Post by Dr. C on 2007-07-24
> **BoyOfDestiny said:**
> Sounds like DRM to me.

"Vista's content protection mechanism only allows protected content to be sent over interfaces that also have content-protection facilities built in."
...
"Similarly, component (YPbPr) video will be disabled by Vista's content protection, so the same applies to a high-end video setup fed from component video."
[http://www.cs.auckland.ac.nz/~pgut001/pubs/vista_cost.html](http://www.cs.auckland.ac.nz/~pgut001/pubs/vista_cost.html)

You could always experiment and tell him to buy a new tv out card, and possibly a new tv (with hdcp support...) ;) Sounds fair right? :(

This definitely looks like a Vista DRM issue to me. Basically if the display and a host of other components are not HDCP compliant Vista will block the output from many a DVD that will work perfectly fine in Ubuntu or for that matter Windows XP.

There are a few solutions to this situation as far as I can see. 
1) Get an new display, TV etc and many a new component. This involves spending thousands of dollars to replace perfectly good electronics, and add to global warming in the process. Presumably the solution Microsoft will recommend.
2) Get rid of Windows Vista and its DRM, and replace it with Ubuntu, another GNU / Linux distribution. or possibly another free OS
3) Get rid of Windows Vista and its DRM, and replace it with Windows XP, Windows 2003 or Windows 2000. This will only work for a while until Microsoft ends support for Windows XP and Windows 2003 and Windows 2000.

---

### Post by kamaboko on 2007-07-24
> **FineE said:**
> This definitely looks like a Vista DRM issue to me. 

Then how do you explain it working for me?  My HD LCD TV's are not HDCP compliant.  Neither Vista nor XP have a problem playing DVD's to those TV's.

---

### Post by darksong on 2007-07-25
I have played downloaded, copied, officail and other DVD's which bend the law on Vista Home premium. DRM has never come into play or stopped me from watching DVD's, videos or Music. I read somewhere that DRM is only to be implemented on Blue Ray technology - don't know if this is true though.

---

### Post by loyeyoung on 2007-07-28
This thread is yet another expression of why everyone should switch to Linux. Proprietary software is unavoidably in conflict with users because it must simultaneously provide usability for its users and police violations of its license. Open source software resolves that conflict.

Install Ubuntu on the computer and then install support for Restricted Formats (i.e., libdvdcss2). In the US, if the user is merely trying to play a DVD for the user's private, non-commercial use, installing and using libdvdcss2 presents no copyright issues. 

Loye Young
[http://www.iycc.biz](http://www.iycc.biz)
Laredo, Texas

---

### Post by kamaboko on 2007-07-28
Don't blame MS for your problems.  Other entertainment giants have been moving toward DRM for quite a while.  Here's an interesting article worth reading.  

[http://www.nxtbook.com/nxtbooks/questex/hom070807/index.php?startpage=10](http://www.nxtbook.com/nxtbooks/questex/hom070807/index.php?startpage=10)

---

### Post by marx2k on 2007-07-31
Best quote of that ridiculous article - " BD+ [...] won't likely be breached for 10 years"

When is the last time you've heard of any Sony licensed/crippled product seeing long term success of any kind? Beta anyone? Minidisc? 

Sony is betting a LOT on the Blu-Ray format.

---

### Post by Lord Illidan on 2007-07-31
> When is the last time you've heard of any Sony licensed/crippled product seeing long term success of any kind? Beta anyone? Minidisc?

Playstation? Walkman?

---

### Post by marx2k on 2007-07-31
> **Lord Illidan said:**
> Playstation? Walkman?

Heh, have you seen the sales figures for PS3? Ever look into why more exclusive games aren't being produced for it? (Hint: cost and complexity of development SDK software)

The Walkman was just a trademark name for the portable tapeplayer - every company under the sun had a version and did not have to pay patent proceeds to Sony for that.

Sony is notorious for failed licensing schemes- and I hate it. (Especially since I own 2 Minidisc recorders that, because of Sony, refuse to work with Linux and are forced to be populated with music under Sony's awful SonicStage)

A little followup from WikiPedia - I was a bit incorrect in what the "Walkman" is - "Walkman is a very popular Sony brand used to market its portable audio players, and is synonymously used to refer to the original Walkman portable personal stereo player and as a generic term for similar devices from other manufacturers.  The names "Walkman", "Pressman", "Watchman", "Scoopman", "Discman", and "Talkman" are trademarks of Sony, and have been applied to a wide range of portable entertainment devices manufactured by the company. Sony continues to use the "Walkman" brand name for most of their portable audio devices, after the "Discman" name for CD players was dropped in the late 1990s. According to Sony, the plural form is "Walkman Personal Stereos", rather than "Walkmans" or "Walkmen" (presumably to preserve their trademark on "Walkman")"
([http://en.wikipedia.org/wiki/Walkman](http://en.wikipedia.org/wiki/Walkman))


So, basically, the Walkman is just a trademarked name that had nothing to do with Sony's success in technology licensing :)

Final edit, I promise:  Read this.. it's actually pretty interesting! :) [http://en.wikipedia.org/wiki/Stereobelt](http://en.wikipedia.org/wiki/Stereobelt)

---

### Post by kamaboko on 2007-07-31
> **marx2k said:**
> Best quote of that ridiculous article - " BD+ [...] won't likely be breached for 10 years"
.

The point of posting that article was to demonstrate that MS is not the flagship of DRM.  People on this board behave as though it were a MS creation.  It's not.  So in the future when people can't play DRM enforced media on their Linux boxes, who will they turn to to blame next?

---

### Post by pjkoczan on 2007-07-31
> **kamaboko said:**
> The point of posting that article was to demonstrate that MS is not the flagship of DRM.  People on this board behave as though it were a MS creation.  It's not.  So in the future when people can't play DRM enforced media on their Linux boxes, who will they turn to to blame next?

You're right, DRM is not a Microsoft creation, as Apple has its hands in the DRM cookie jar, and it is the media who are really pushing it. What is Microsoft's fault (and Apple's to a lesser extent) is that they kowtowed so readily to the desires of the studios. Microsoft has a near 90% desktop market share, so if you think that studios could afford to miss out on that great of a user base, you're kidding yourself.

MS (and Apple) could have made more customer-centric demands or told the studios to do something anatomically impossible regarding DRM. The studios would have had to follow or go find another platform (Linux? yeah right, not enough desktop market share to be appealing, and the GPL people would have laughed them out of their offices), abandon online music entirely (very unprofitable, and mp3 ripping/sharing would still exist), or simply swallowed the bitter pill and accept that they weren't getting their way. A specific media needs a venue more than a venue needs that specific media.

MS and Apple could have had the studios begging at their feet, but instead they're the ones on their knees.

> Playstation? Walkman?

Marx2k said it very well, so I'll just add on what I feel I should. These weren't Sony-licensed technologies. These products were Sony slapping a name on devices to play cheap, widely-available, and *open* formats (CDs, cassettes, and DVDs are all open formats...I mention DVDs for the PS2 and the myriad selection of DVD players). This is where Sony achieved its market dominance, especially in the video game market, as they could produce games and hardware very cheaply, while Nintendo and Sega were charging huge licensing fees for cartridges and specially sized discs. True, Sony's games did have copy protection, but at the heart of it all was the CD, the nice cheap open format.

Speaking of beta, the you can read up on it at [http://en.wikipedia.org/wiki/Betamax](http://en.wikipedia.org/wiki/Betamax) and from the other side at [http://en.wikipedia.org/wiki/VHS](http://en.wikipedia.org/wiki/VHS). There was also an interesting documentary on media formats on the History Channel a few months back, but I can't remember its name.

---

