---
title: "Which graphics card?"
date: 2012-09-27
forum: The Cafe
---

### Post by Statia on 2012-09-27
(Not sure if this shouldn't go in "Hardware and laptops", but as that is more about problems getting hardware to work, I'll post here)

Currently my machine has an Asus ENGT430 graphics card (so basically Nvidia GT430). I am not (yet?) much of a gamer, so for now this works just fine. Should I want to upgrade to something with a bit more oomph, what would you recommend?

Constraints: 

- price: I know I could go out and buy a €500 card, but let's say I don't want to spend more than €100 (that would mean $100 for hardware on sale in the US).

- power: I have a 300W PSU and don't want to replace it just to accomodate a graphics card.

- brand: considering Linux support, it should have a Nvidia chipset.

---

### Post by mips on 2012-09-27
For $100 maybe a GTS450.

Keep in mind that the second digit in the model number is the performance indicator while the first digit indicates the series, so a 450 would more than likely be faster than a newer 640.

Heres a site wher you can do a quick rough comparison purely based on specs [http://www.gpureview.com/show_cards.php](http://www.gpureview.com/show_cards.php) alternatively look up one of the many sites with benchmark listings.

---

### Post by kaldor on 2012-09-27
> **mips said:**
> For $100 maybe a GTS450.

Recently upgraded to this card. Slightly old, but definitely a great choice. I can't complain :)

Edit: noticed your PSU. The GTS 450 would be too high for 300W. I'd really recommend you upgrade to a 450W or 500W PSU from a good brand like Corsair or Antec so you have much more room for upgrades. The PSU is something you don't want to skip on.

---

### Post by pqwoerituytrueiwoq on 2012-09-27
amd's does provide linux support for there drivers
what brand is your 300w psu? some lie about there wattage
since you are looking for a upgrade for a gt 340 you should consider a better psu
corsair/seasonic/antec/ocz/pc power cooling are some good brands
when i upgraded from my gt 430 i went to a 550 ti (67.99 after rebate last black friday)
here is a psu calculator
[http://extreme.outervision.com/psucalculatorlite.jsp](http://extreme.outervision.com/psucalculatorlite.jsp)

---

### Post by yeehi on 2012-09-27
Consider using integrated graphics instead of a dedicated video card, since you are not much of a gamer.

The 3D graphics on Intel Ivy Bridge chips, HD Graphics 4000, has come a long way and does quite well at a lot of [games]("http://www.notebookcheck.net/Intel-HD-Graphics-4000-Benchmarked.73567.0.html").

---

### Post by QIII on 2012-09-27
It's good to see that the "ATI is no good on Linux" thing persists.

Don't get me wrong.  I like NVIDIA products.  But the myth that ATI graphics are more problematic than NVIDIA is just that.  A myth.

AMD bought ATI quite a while ago.  Before AMD bought ATI and turned it around, ATI's reputation was well deserved.  But that colors everyone's opinions to this day.  It's not the old ATI.  It's AMD/ATI.

What I would suggest is this:  rather than ask in a forum where you might get a brand-loyalty flame war, go to Phoronix or another website and read reviews of cards in your price range.  Pick the one that looks like it best serves your needs.  Don't worry about the manufacturer.  They are both good.  Worry about features and price.

And yes, a better PSU is a must.

---

### Post by Primefalcon on 2012-09-28
> **QIII said:**
> It's good to see that the "ATI is no good on Linux" thing persists.

Don't get me wrong.  I like NVIDIA products.  But the myth that ATI graphics are more problematic than NVIDIA is just that.  A myth.

AMD bought ATI quite a while ago.  Before AMD bought ATI and turned it around, ATI's reputation was well deserved.  But that colors everyone's opinions to this day.  It's not the old ATI.  It's AMD/ATI.

What I would suggest is this:  rather than ask in a forum where you might get a brand-loyalty flame war, go to Phoronix or another website and read reviews of cards in your price range.  Pick the one that looks like it best serves your needs.  Don't worry about the manufacturer.  They are both good.  Worry about features and price.

And yes, a better PSU is a must.
+1, I am actually using an ATI GPU atm, and I have not had any issues with it!

---

### Post by Statia on 2012-09-28
> **yeehi said:**
> Consider using integrated graphics instead of a dedicated video card, since you are not much of a gamer.

The 3D graphics on Intel Ivy Bridge chips, HD Graphics 4000, has come a long way and does quite well at a lot of [games]("http://www.notebookcheck.net/Intel-HD-Graphics-4000-Benchmarked.73567.0.html").

My system (i3-2120, H61) has HD-2000 built-in graphics, I don't think that performs better than my current video card, but I might be mistaken.

---

### Post by Statia on 2012-09-28
> **pqwoerituytrueiwoq said:**
> amd's does provide linux support for there drivers
what brand is your 300w psu? some lie about there wattage


Thanks for the link.
My PSU is Asus (or at least included by Asus):

[http://www.asus.com/Barebone_PC/V_Series_2530L/V6P8H61ELX/#specifications]("http://www.asus.com/Barebone_PC/V_Series_2530L/V6P8H61ELX/#specifications")

I see now it is 350 Watts peak.

---

### Post by mips on 2012-09-28
> **Statia said:**
> 
I see now it is 350 Watts peak.

You might just squeeze it in with a 350W psu but it would be very close, 500W is recommended, [http://www.guru3d.com/articles_pages/geforce_gts_450_review_roundup,15.html](http://www.guru3d.com/articles_pages/geforce_gts_450_review_roundup,15.html)

---

### Post by rai4shu2 on 2012-09-28
> **QIII said:**
> It's good to see that the "ATI is no good on Linux" thing persists.

Don't get me wrong.  I like NVIDIA products.  But the myth that ATI graphics are more problematic than NVIDIA is just that.  A myth.

Well, VDPAU isn't a myth. Does ATI do hardware acceleration for MPEG4 video (in Linux, that is)?

---

### Post by QIII on 2012-10-01
VDPAU was proprietary to  NVIDIA for a long time, although it is now open source.

ATI gains video acceleration through VAAPI and the XvBA backend, as you know.  That doesn't provide as rich a set of acceleration options just yet.  MPEG-2 VLD and MPEG-4 Part 2 are actually implemented in the driver, but are not yet exposed.  AMD's anticipated XvBA SDK is expected to address that.

That is a red herring, anyway.   Notice that I wrote "problematic".  ATI GPUs are no more problematic than NVIDIA's.

---

### Post by MdMax on 2012-10-01
> **Statia said:**
> Currently my machine has an Asus ENGT430 graphics card (so basically Nvidia GT430). I am not (yet?) much of a gamer, so for now this works just fine. Should I want to upgrade to something with a bit more oomph, what would you recommend?

It's hard for me to recommend a graphics card. I'm using the GeForce 8800GT. If you need very good OpenGL support, I think you'll probably get the best results with proprietary Nvidia drivers. I don't know if Ati managed to improve their drivers.

If you select a high-end GPU, be careful with your PSU. 300W is too low for most cards.

As a GNU/Linux and [_X-Plane_]("http://www.x-plane.com/")/[_FlightGear_]("http://www.flightgear.org/") user, I'm recommending Nvidia.

[[img]http://ggka.online.fr/xp/xp10-63-th.jpg[/img]]("http://ggka.online.fr/xp/xp10-63.jpg") [[img]http://ggka.online.fr/xp/xp10-70-th.jpg[/img]]("http://ggka.online.fr/xp/xp10-70.jpg") [[img]http://ggka.online.fr/xp/xp10-72-th.jpg[/img]]("http://ggka.online.fr/xp/xp10-72.jpg") [[img]http://ggka.online.fr/xp/B777-005-th.jpg[/img]]("http://ggka.online.fr/xp/B777-005.jpg")

---

### Post by rai4shu2 on 2012-10-01
> **QIII said:**
> That is a red herring, anyway.   Notice that I wrote "problematic".  ATI GPUs are no more problematic than NVIDIA's.

Are you sure that's what you meant? Maybe you should be even more pedantic about that word "problematic." :P

Meanwhile, some of us don't care about hardware (or semantics). In fact, I'll flat out admit it. ATI makes better hardware. But who cares? I suppose if you expected the driver to one day actually support the features you wanted, then ATI is the way to go. If you actually want 1080p right now in Linux. Guess what? ATI would be a mistake.

---

### Post by Statia on 2012-10-02
> **QIII said:**
> 
ATI gains video acceleration through VAAPI and the XvBA backend, as you know.  That doesn't provide as rich a set of acceleration options just yet.  MPEG-2 VLD and MPEG-4 Part 2 are actually implemented in the driver, but are not yet exposed.  AMD's anticipated XvBA SDK is expected to address that.


No 'foo' "just yet".
'Bar' "not yet exposed".
Wait for 'baz' "to address that"

So how is that supposed to be just as good as Nvidia's drivers?
Like I said: I'd like to go with Nvidia.

---

### Post by Grenage on 2012-10-02
In the last couple of years I've had a few machines with AMD graphics cards, and for various reasons, they all got replaced with Nvidia models.  There are few reasons to *buy* one for Linux, over an Nvidia alternative.

My usage in the above cases, was for an HTPC, gaming machine, and general workstation.

---

### Post by QIII on 2012-10-02
I'm still trying to find the post where I said "as good as".  Call me pedantic, I guess.

Strangely, if one were to look at the ATI wiki in my signature under "Enabling Video Hardware Acceleration", I specifically say that it is not as full featured as other OEMs.

I also said to pick what has the features you want rather than getting embroiled in a flame war - which is what this seems to have become.

---

### Post by Statia on 2012-10-02
> **QIII said:**
> I'm still trying to find the post where I said "as good as". 

You said "Worry about features" in your first post. In your second post you actually mention a number of features that don't work (yet) with ATI.

I really believe you when you say the ATI cards are good hardware, but why would I buy a piece of hardware when I can't use all or most of its features?
If I have the choice between a €100 Nvidia card of which the drivers allow me to use 90% of the features (as compared to Windows drivers) or a €100 ATI card whose drivers
support 70% of the features, then my money goes to Nvidia. ATI wants my money? They can have it when their drivers don't lag so far behind the Windows drivers. I know better than to think Nvidia is doing a great job at this, but at least they do the less (least? lest?) worst job in the industry.

---

### Post by QIII on 2012-10-02
I hear you and I agree with that line of reasoning.

But there is often an undertone in such discussions that ATI doesn't care about Linux or that their drivers are hard to install or they don't work, etc.

I think that is myth that is a carry-over from before AMD bought ATI and ATI support for Linux really did suck.

AMD does care about Linux, but with ATI they started not just from behind, but going the wrong direction.  They have worked pretty darn hard to turn that around.  You should buy what works.  But make it a features/cost decision rather than an ATI is horrid decision.

That they have gotten what they have into the driver, even if it is not yet exposed indicates that they are interested in putting effort and resources into Linux.  It even goes so far as the fact that they have such a tight relationship with Canonical that every fourth and tenth month they make sure that they have a good driver to put in the Canonical repo even before it is available to the general Linux community.

NVIDIA has a longer history of Linux support.  It's not that ATI can't get it together.  They started with a lesser hand.

By the way, even though ATI has done a better job of working with open source developers, I think Linus' comment about NVIDIA was a little over the top.

---

### Post by sidzen on 2012-10-02
AnandTech article *NVIDIA's GeForce 600M Series: Mobile Kepler and Fermi Die Shrinks*, says,
 
. . . "At the same time, it wouldn't be unreasonable to expect a cut down GK104 to materialize as the GTX 680M; the desktop GTX 680 only has a TDP of 195 watts, and some careful binning and pruning of clocks (keep in mind that the desktop card is running the GPU at 1GHz and the power-hungry GDDR5 at a staggering 6GHz) could theoretically produce a competitive top-end notebook GPU. It wouldn't be unheard of; NVIDIA's crammed cut down GF100/GF110 Fermi chips into notebooks with a 100W TDP, and the GTX 680 is already very close to that level. Give NVIDIA some time to make a bunch of money selling all the GTX 680 cards they can to early adopters and then we're likely to start seeing trickle down parts, including our presumed GTX 680M."

SOURCE -- [http://www.anandtech.com/show/5697/nvidias-geforce-600m-series-keplers-and-fermis-and-die-shrinks-oh-my/3](http://www.anandtech.com/show/5697/nvidias-geforce-600m-series-keplers-and-fermis-and-die-shrinks-oh-my/3)
Article by Dustin Sklavos & Jarred Walton on 3/22/2012 8:59:00 AM

Also see [http://www.compuvest.com/Desc.jsp?iid=1771500](http://www.compuvest.com/Desc.jsp?iid=1771500) -- not an M suffix, but this is where I buy graphics cards as they become available.

---

### Post by DogMatix on 2012-10-02
Wow! whilst you lot are pulling Graphic Card wheelies. I'm tootling along on my NVIDEA GT210 Moped quite happily. It runs Unity (12.04) fine and my PSU is less than 300W (Although this is less than recommended & I keep meaning to swap it for a 500W I have sitting on a shelf). 

I feel inadequate now!

---

### Post by viperdvman on 2012-10-02
I myself am looking to upgrade to an NVidia GTX 560, maybe even the Ti model if I want to push it. Very fast cards, not too expensive, and still fairly new and will last me a good long while :D

---

### Post by Statia on 2012-10-03
> **QIII said:**
> 
AMD does care about Linux, but with ATI they started not just from behind, but going the wrong direction.  They have worked pretty darn hard to turn that around.  You should buy what works.  But make it a features/cost decision rather than an ATI is horrid decision.


By the time I am going to upgrade (and that might be a while) I will research the current situation of driver support. Maybe I'll swap out my PSU as well, we'll see.

I was having a look at Oil Rush, almost bought it, but their recommended card is a GTX 460 or Radeon HD4850. I'll just wait playing it until I upgrade.

---

### Post by QIII on 2012-10-03
Don't buy the 4800 series.  ATI is moving the driver to a legacy branch, which means it probably won't work with the next version of X Server.

This will be ATI's second legacy branch.  NVIDIA has three.  They both like to push for us to buy new widgets.  Now *that *gets my blood pressure up.

---

### Post by Statia on 2012-10-03
I just enabled controlling my GPU fan speed, by GUI or with a script.
Do ATI drivers allow this kind of control?

---

### Post by QIII on 2012-10-03
Yes, you can control the fan speed.

There is no GUI for Overdrive in Linux, but it exists.

Just for giggles, it might be fun to write a GUI, now that you mention it.

---

### Post by litiform on 2012-10-12
I would just get Intel Integrated. Performance has never been better and Linux support is the best.

I'd stay away from NVIDIA and AMD. I dislike NVIDIA. I like AMD, but drivers seem more problem than integrated.

---

### Post by Statia on 2012-10-27
I am thinking about the GT640 2GB now.
It retails for exactly one cent under my &#8364;100 limit and demands a 350W power supply.
Now I just have to wait until I can justify spending a hundred Euros.
Like after landing a job....

EDIT: Thanks everybody for your input!

---

### Post by kaldor on 2012-10-27
> **Statia said:**
> I am thinking about the GT640 2GB now.
It retails for exactly one cent under my €100 limit and demands a 350W power supply.
Now I just have to wait until I can justify spending a hundred Euros.
Like after landing a job....

EDIT: Thanks everybody for your input!

The GT 640 won't be *that* much more powerful than your current card. Also, with lower-end cards, the memory is pretty much irrelevant. I'd at least get a GTX 650. Better yet, see if you can find the GTX 650 Ti for a decent price.

If you're not willing to replace the power supply then I'd wait longer and save up until you can get exactly what you want- what's the point in spending 100 euros and then realizing you were looking for something faster? ;)

---

### Post by vanquishedangel on 2012-10-27
> **QIII said:**
> It's good to see that the "ATI is no good on Linux" thing persists.

Don't get me wrong.  I like NVIDIA products.  But the myth that ATI graphics are more problematic than NVIDIA is just that.  A myth.

AMD bought ATI quite a while ago.  Before AMD bought ATI and turned it around, ATI's reputation was well deserved.  But that colors everyone's opinions to this day.  It's not the old ATI.  It's AMD/ATI.

What I would suggest is this:  rather than ask in a forum where you might get a brand-loyalty flame war, go to Phoronix or another website and read reviews of cards in your price range.  Pick the one that looks like it best serves your needs.  Don't worry about the manufacturer.  They are both good.  Worry about features and price.

And yes, a better PSU is a must.

Actually it was true til a certain point, but then ati got way better and I have sworn by ati for years. I game on linux and only use ati, their support is way better than it was and I have little to no issue with ati.

That myth come from a time way back when you needed to compile your driver from scratch, when tools like the software center and jockey were non exist-ant so rejoice all of you who don't know that pain!

I would say the psu as well, but you could also check into Lubuntu, that uses less wattage and resources (graphics as well) leaving more for your applications and games.

---

### Post by madoshwa on 2012-10-27
Im running the nvidia geforce 9800gt. the linux nvidia app is pretty good. it gives me the functionality that i need for it (dual dvi and single s-video input). for windows it is a pretty good card even. can run games like borderlands on max. not sure how much it is retail, but i picked mine up from a friend for 20$ with a loud fan. a can of air fixed that up :P

---

### Post by mips on 2012-10-28
> **kaldor said:**
> The GT 640 won't be *that* much more powerful than your current card.

+1

You would be wasting a 100 euros.

---

### Post by Statia on 2012-10-29
> **kaldor said:**
> The GT 640 won't be *that* much more powerful than your current card. Also, with lower-end cards, the memory is pretty much irrelevant. I'd at least get a GTX 650. Better yet, see if you can find the GTX 650 Ti for a decent price.

  

Thanks, duly noted!

---

### Post by SkyHighClaw on 2012-10-29
I'm rolling with a gtx 550 Ti. I'm totally digging this card right now. once i get enough cash together im gonna invest in a new motherboard and rig 2 of em up via sli.

---

### Post by Statia on 2012-11-08
> **kaldor said:**
> The GT 640 won't be *that* much more powerful than your current card. Also, with lower-end cards, the memory is pretty much irrelevant. I'd at least get a GTX 650. Better yet, see if you can find the GTX 650 Ti for a decent price.


And how about now that the R310 driver is available? It should double the performance of 600 series cards. It is also supposed to improve the performance of other cards, but not as much.

---

### Post by Statia on 2013-04-29
> **kaldor said:**
> The GT 640 won't be *that* much more powerful than your current card. Also, with lower-end cards, the memory is pretty much irrelevant. I'd at least get a GTX 650. Better yet, see if you can find the GTX 650 Ti for a decent price.

If you're not willing to replace the power supply then I'd wait longer and save up until you can get exactly what you want- what's the point in spending 100 euros and then realizing you were looking for something faster? ;)

Well, last weekend I finally had both the money and the time (especially the latter was the limiting factor) to go out and buy and install a new card. I bought a MSI GTX 650Ti Power Edition, for €129.
The cooler on that thing is HUGE!
According to this site: [http://www.extreme.outervision.com/psucalculatorlite.jsp](http://www.extreme.outervision.com/psucalculatorlite.jsp)
a 350 Watt PSU would just do, but I wanted to be sure, so also got a Corsair CX 500W PSU.

It's all running fine now, thanks all for your input here.

---

### Post by mips on 2013-04-29
Cool, took you some time though :)

---

### Post by Statia on 2013-04-29
> **mips said:**
> Cool, took you some time though :)

All work and no play ;-)

---

