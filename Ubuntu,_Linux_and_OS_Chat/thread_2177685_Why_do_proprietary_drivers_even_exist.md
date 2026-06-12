---
title: "Why do proprietary drivers even exist?"
date: 2013-09-29
forum: Ubuntu, Linux and OS Chat
---

### Post by WinterMadness on 2013-09-29
I must be lacking some kind of information. Aren't hardware manufacturers typically in the business of selling hardware? Wouldn't having open source drivers for everything they sell make more sense because it would allow the community to maintain the HW's usefulness (longevity and compatibility) thus increasing sales?

Imagine if a bug was found in a graphics card driver, and an open source coder found it and fixed it, it wouldnt take as long for them to simply investigate the given code and to implement it as opposed to trying to recreate the problem and to pinpoint it etc.

It would also allow them to sell older cards for very low prices since open source coders would probably make sure it works on modern systems.

Fill me in.

---

### Post by deadflowr on 2013-09-29
Lawyers

---

### Post by 1clue on 2013-09-29
Do you remember WinModems?

There are all sorts of reasons why companies want to control the drivers for their hardware.  Some of them are pretty good, some are pretty bad.

Some hardware manufacturers not only create proprietary drivers but also cooperate fully with Open Source or even make the driver themselves and open source it afterwards.  Other hardware manufacturers block Open Source any way they can, for a variety of reasons.

One of those reasons is illustrated very well by the WinModem of a decade or more back.  People came out with a WinModem, it was super cheap.  Turns out there was barely enough hardware to make it work, and a lot was done in software.  The companies who made them did not cooperate with Open Source at all, because they didn't want the world to know what a piece of crap they'd made.

Another example:  IBM ported Linux to their mainframes.  They Open Sourced everything except the driver for their network card, which would have revealed critical information about the card itself.  Free to use (of course not valuable unless you have one of their mainframes) but not free to tinker with.

---

### Post by pqwoerituytrueiwoq on 2013-09-29
> **1clue said:**
> One of those reasons is illustrated very well by the WinModem of a decade or more back.  People came out with a WinModem, it was super cheap.  Turns out there was barely enough hardware to make it work, and a lot was done in software.  The companies who made them did not cooperate with Open Source at all, because they didn't want the world to know what a piece of crap they'd made.wouldn't this be easy to tell by dissecting one?

---

### Post by Copper Bezel on 2013-09-30
Yeah, without reading about this and based on what's stated above, that sounds a lot more like, "the sticker price reflected the development cost of software, and keeping it proprietary prevented others from selling the same product at a much lower cost," which is, you know, kinda why *any* proprietary software exists.

---

### Post by 1clue on 2013-09-30
> **pqwoerituytrueiwoq said:**
> wouldn't this be easy to tell by dissecting one?

I suppose so, if you're a hardware type.  I wouldn't have any idea looking under the covers.  WinModems were half the cost of the next cheapest thing, and they were shipped with a lot of systems.

You can have whatever opinion of motives for proprietary software you want.  There are some scenarios which don't seem to work well with an Open Source model, or at least which haven't yet shown any signs of working well that way.  As well, programmers have every bit as much right to choose a commercial model as other programmers have to choose an Open Source model.

---

### Post by bcschmerker on 2013-09-30
Some hardware manufacturers have trade secrets to protect in the newest generation of microprocessor chips.  Whereas my "Hot Rod gPC™," an Advanced Micro Devices®-equipped custom-build shoehorned into an Everex® TC2502 case, is fully FOSS-supported (xserver-xorg-video-radeon is fully functional on the integrated ATi® R600 GPU in the AMD® 780G/SB710 chipset), that's not the case with the brand-new AMD® Northern Islands GPU's in the Radeon® HD™ 7000 Series, which have massive hardware changes compared to the R6xx GPU's. 

And some hardware manufacturers don't play at all nice with the open-source community; the LinUX Kernel Group had to reverse-engineer drivers for pre-2000 versions of Microsoft® Windows® NT™ for sufficient information on the registers of the nVIDIA® MCP-series chipsets in order to get said chipsets to work at all in LinUX, as I encountered during my all-too-delayed efforts to get an eMachines®/Acer® EL1210-09 (Advanced Micro Devices® Athlon 64® LE-1620, nVIDIA® MCP78S chipset; augmented with nVIDIA® GT218 in an Asus® EN210/DI/512MD3(LP) video adapter) ready for projector duty.  And I *still* needed GeForce® Software Version 319 (ppa:ubuntu-x-swat/x-updates; nvidia-319, nvidia-settings-319) for dual-display operation, with xserver-xorg-video-nouveau unusable for either GPU (viz., no FOSS net).

---

### Post by mastablasta on 2013-09-30
also releaseing GPU drivers and hardware would give competition advantage. since thery would know how it works etc.  so i kind fo understand them why they keep some thing proprietary. but i do not know why they still have drivers for old chips that are basically not sold anymore locked.

---

### Post by alexan on 2013-09-30
The "official" reason is what mastablasta said... the true reason is that if they release all specification for opensource drivers (keep in mind: no one is asking them to release the OSS of their driver... all we need it's the just the SPECS to make own drivers) they fear they will sell less. Basically because a successful hardware model can be supported unlimited with community's bugfix and other improvements.
Thus, they think, there will be lot of less people willing to buy the new version/model of the same product (mostly videographics boards).


All they want it's the "iPhone effect": want lot of people to constantly buy the +1 version of the same stuff they already own.

---

### Post by ssam on 2013-09-30
Open drivers/firmware can allow additional features that the make does not want used. If a new feature can be enabled by updating software, then people won't buy a new model. High end models may only differ in software ( [http://www.argyllcms.com/doc/instruments.html#i1p2](http://www.argyllcms.com/doc/instruments.html#i1p2) ). Another good example is [http://www.magiclantern.fm/](http://www.magiclantern.fm/) which adds lots of features to digital cameras.

Wireless cards are only allowed to use certain frequencies in certain countries, an open diver could use the additional frequencies or increase power levels. (actually the linux kernel has code to make sure it obeys local RF laws).

---

### Post by buzzingrobot on 2013-09-30
> **WinterMadness said:**
> Aren't hardware manufacturers typically in the business of selling hardware? Wouldn't having open source drivers for everything they sell make more sense because it would allow the community to maintain the HW's usefulness (longevity and compatibility) thus increasing sales?



The decision is not as simple as "Make open source drivers for Linux and sell cards to Linux users". 

AMD and Nvidia, like all businesses, make decisions about where to allocate their resources -- money, people -- in order to *maximize* the money they can make.  A choice to be more serious about open source drivers means moving resources away from supporting other products. That would be a rational choice if the company believed overall profit would increase.  If they thought putting the same increase in resources into their existing Microsoft/Apple lines would create even more profit, they'd do that.

The thing to remember is that the goal is revenue and profit.  Making video cards is the means to that end.  Their support for *any* market -- Window, Linux, Apple, etc. -- is only as strong as the revenue it provides.

Rightly or wrongly, the Linux community has a reputation for not spending money, for wanting things to be gratis. That does not encourage people to sell to that market.

AMD and Nvidia's interest in selling "old" cards is probably in direct relation to the contribution those sales make to their bottom lines.  A card's "longevity" does not make them any money.  They want people to buy new cards on a regular basis, not buy one card and keep it for years and years.  That's why they release a steady stream of new cards with modest capability increases:  It's an incentive to buy.

AMD and Nvidia will never release enough info about their cards to allow someone else to manufacture cut-rate functional duplicates.  Because they would.

---

### Post by 1clue on 2013-09-30
> **alexan said:**
> The "official" reason is what mastablasta said... the true reason is that if they release all specification for opensource drivers (keep in mind: no one is asking them to release the OSS of their driver... all we need it's the just the SPECS to make own drivers) they fear they will sell less. Basically because a successful hardware model can be supported unlimited with community's bugfix and other improvements.
Thus, they think, there will be lot of less people willing to buy the new version/model of the same product (mostly videographics boards).


All they want it's the "iPhone effect": want lot of people to constantly buy the +1 version of the same stuff they already own.

That's exactly what they're trying to protect.  An API and a description of how to use it gives a lot of insight into what's on the other side of the API.

Companies who make good, solid middle-of-the-road hardware with no surprises don't have a lot to fear, and many of those companies are glad to work with Open Source.

Companies who make extreme hardware for the latest greatest DO have something to fear, even from releasing an API.

---

### Post by grahammechanical on 2013-09-30
I built my own machine because I did not want to pay for an OS that I never intended to use. At the time I was not a Linux/Ubuntu user. I am sure that other Linux users feel the same way. So, I think that component manufacturers would sell more if they provided Linux drivers. They do not need to provide technical details of the products to open source developers. They just need to provide Linux drivers.

How many combination printers and scanners on the market work on Linux? Completely? Wireless, as well? The printer maker that provides a product that is fully functional because they provided a Linux driver as well as a Windows driver would get my vote and maybe my money. But these business men lack the imagination to see it.

Last year I might have brought a Kodak printer/scanner because the prices were being reduced due to a decline in their business. I found that Kodak was not well supported in Linux. That is not the fault of the open source developers but it is due to the lack of imagination of the Kodak management who were not supplying Linux drivers. Result? A lost sale.

Regards.

---

### Post by 1clue on 2013-09-30
> **grahammechanical said:**
> I built my own machine because I did not want to pay for an OS that I never intended to use. At the time I was not a Linux/Ubuntu user. I am sure that other Linux users feel the same way.


Me too.  Every PC based system I've ever bought was bought from parts and assembled, excluding 2 laptops.  Been doing it since the mid 90s.

> 
So, I think that component manufacturers would sell more if they provided Linux drivers. They do not need to provide technical details of the products to open source developers. They just need to provide Linux drivers.


That's not how it works.  I've written a driver.  By releasing open source drivers, you're giving away just about everything the competition needs to know to reproduce your card.  They can buy a card, dissect it, look at your driver code and they have it.

> 
How many combination printers and scanners on the market work on Linux? Completely? Wireless, as well? The printer maker that provides a product that is fully functional because they provided a Linux driver as well as a Windows driver would get my vote and maybe my money. But these business men lack the imagination to see it.


I have a Canon MF8050 color laser all-in-one.  It works fine.  The company released a Linux driver, which is Open Sourced under the GPL.  Works on the network, but since it doesn't have a wireless card you need to wire it to your router, and if you have wireless attached to that then it's wireless.  Comes with a fax driver, which IMO is useless because I never send or receive faxes.  All the functions I use work fine.

However, as far as I can tell there are no Linux distros which include it in their package list.  Same driver for pretty much every color laser all-in-one, and nobody sees fit to include it.

I have a thread for Canon all-in-one laser drivers as a problem solving resource, it's been going for years now and still gets posts.

> 
Last year I might have brought a Kodak printer/scanner because the prices were being reduced due to a decline in their business. I found that Kodak was not well supported in Linux. That is not the fault of the open source developers but it is due to the lack of imagination of the Kodak management who were not supplying Linux drivers. Result? A lost sale.

Regards.

Linux is a tiny fraction of the business they get.  Some of these companies don't even supply Mac drivers, and that's a lot more business and a lot more mainstream.

This is the way Linux works.  Somebody gets a piece of hardware and finds out there's no driver for it, and out of frustration goes about finding or making one.  Welcome to Open Source!

---

### Post by buzzingrobot on 2013-09-30
I've built every machine I've used for the last 15 years, that wasn't a laptop.  While it's fun, I'm not sure that not paying for a preinstalled OS I wouldn't use actually produced a net savings.  I tend to build with hardware that's about a year behind the bleeding edge, and I don't build for games.  When I've checked prices on comparable readymade systems versus my costs, there hasn't been much difference.  When I buy a part for a new machine, I pay retail price.  Dell/HP/etc do not.

If I ran a peripheral business, before I committed to selling into the Linux market, I'd want to know if the return on the cost of entering that market is going to be greater, dollar per dollar, than spending the same amount to ramp up design, production, advertising, etc., in the Windows market. Those are the numbers I'd pay attention to.  Telling me a lose sales if I don't sell to Linux doesn't mean anything.  Tell me how I can make *more* money by spending *more* money on Linux products than on Windows products.

In the end, AMD and Nvidia will provide better Linux drivers, and be more amenable to working with FOSS, as Linux use increases.  We've just seen it:  Steam makes noise with Linux, Nvidia loosens its grip just a bit, just to keep a toe in what may become a profitable part of their game market.

---

### Post by 1clue on 2013-09-30
@buzzingrobot,

You're not quite going far enough on cost of machines IMO.  I haven't built a machine with a 3-digit price tag in 15 years.  That's not the whole story though, because I wind up with better hardware.  Inevitably a pre-built machine either goes too far for something I don't want or goes not nearly far enough on something I want.  If I build my own, the only time I don't get something exactly right is when I didn't do my homework.  Nonetheless, I always wind up spending some four digit number of US dollars.

I don't think Linux drivers are cost effective for businesses, just from the perspective of customer sales.

In the long run, I suspect there's a different reason why some companies provide Linux drivers:  They use Linux internally, and somebody on the driver team went ahead and ported it to Linux.  If you're already building drivers anyway, I doubt something like a printer would be all that much different from the Windows version.  I suspect some of these are handled from the management side of things, meaning they see a need internally and write the check.  Other times probably it's a guy who stays up late a week or two.

---

### Post by WinterMadness on 2013-09-30
I was just thinking that maybe if they simply developed the drivers for windows, and made it open source, then perhaps they could not be pestered with developing drivers for other platforms, as they could just leave it to the community.

---

### Post by RichardET on 2013-10-03
> **alexan said:**
> The "official" reason is what mastablasta said... the true reason is that if they release all specification for opensource drivers (keep in mind: no one is asking them to release the OSS of their driver... all we need it's the just the SPECS to make own drivers) they fear they will sell less. Basically because a successful hardware model can be supported unlimited with community's bugfix and other improvements.
Thus, they think, there will be lot of less people willing to buy the new version/model of the same product (mostly videographics boards).


All they want it's the "iPhone effect": want lot of people to constantly buy the +1 version of the same stuff they already own.


I think that you are correct.  Why would a hardware maker ever want to make it easier for a buyer to never buy the new version of the hardware?!
But hardware is so cheap now that it would be easier I would think for a new laptop to be made from 100% new parts, which are also open source new designs of existing
products, essentially licensing to designs the way processors are being produced.

---

### Post by kurt18947 on 2013-10-03
> **grahammechanical said:**
> I built my own machine because I did not want to pay for an OS that I never intended to use. At the time I was not a Linux/Ubuntu user. I am sure that other Linux users feel the same way. So, I think that component manufacturers would sell more if they provided Linux drivers. They do not need to provide technical details of the products to open source developers. They just need to provide Linux drivers.

How many combination printers and scanners on the market work on Linux? Completely? Wireless, as well? The printer maker that provides a product that is fully functional because they provided a Linux driver as well as a Windows driver would get my vote and maybe my money. But these business men lack the imagination to see it.

Last year I might have brought a Kodak printer/scanner because the prices were being reduced due to a decline in their business. I found that Kodak was not well supported in Linux. That is not the fault of the open source developers but it is due to the lack of imagination of the Kodak management who were not supplying Linux drivers. Result? A lost sale.  

Regards.

If I were in the tech business, I'm not sure I'd ape Kodak's business practices unless I too wanted to go bankrupt.  When I shop for a new piece of gear, linux compatibility is at the top of the list.  No linux support, no $ from me.  And if I'm in a crotchety mood, I may write to the benighted company's  CEO and tell him/her why I bought his/her competitor's product instead.

---

### Post by SeijiSensei on 2013-10-03
No hardware manufacturer is going to "go bankrupt" by not writing drivers for Linux.  For most manufacturers, the value of Linux drivers and sales to the Linux marketplace is, to use the attorneys' word for it, *de minimis*.

---

### Post by Prime624 on 2013-10-03
Because they're stupid.

---

### Post by RichardET on 2013-10-04
I think the issues over driver support are more complex than what seems to be the prevailing mood on this board.
Major tech companies place a value on their proprietary technologies and naturally do not want to give out too
much information and they also see valuing some proprietary platforms over others, such as MS Windows over GNU/Linux, to be an important
aspect of their overall business value.  I think companies such as Red Hat & canonical should invest in their own graphics, sound, BIOS,
technologies and then Linux will truly be a third wave OS choice.

---

### Post by buzzingrobot on 2013-10-04
You mean go into the hardware business?

---

### Post by ssam on 2013-10-16
Good example of a closed driver limiting functionality 
[https://lwn.net/Articles/569854/](https://lwn.net/Articles/569854/)

---

### Post by 1clue on 2013-10-16
If that were some special cable needed to provide extra functionality that's not in a standard cable I wouldn't have a problem with it.  But it looks like they just wanted to sell you their probably-overpriced cable.

Apple's doing that with their new iPhones too.  Proprietary connector wasn't enough, the cheap knockoffs were biting into their profit so they put a chip in the cable so they can charge $25 for a stupid USB cable.

---

### Post by w-andre on 2013-10-17
I remember WinModems quite vividly as I used to have to fix connection problems with them when I worked as tech support for a gigantic Internet company. A 56k modem in 1999 cost 40$ if I remember correctly whereas hardware modems were at least 90$. The difference was that one worked and the other didn't. Guess which one that was.

---

