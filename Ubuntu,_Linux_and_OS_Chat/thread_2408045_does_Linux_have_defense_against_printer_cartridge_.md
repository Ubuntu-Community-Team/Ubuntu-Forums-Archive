---
title: "does Linux have defense against printer cartridge scams?"
date: 2018-12-12
forum: Ubuntu, Linux and OS Chat
---

### Post by ardouronerous on 2018-12-12
Just watched this video: [https://www.youtube.com/watch?v=AHX6tHdQGiQ](https://www.youtube.com/watch?v=AHX6tHdQGiQ)

Apparently, some printer manufacturers have included a chip inside their ink cartridges that tricks the user into thinking their ink is running low when in fact it isn't.

Let's say the Linux kernel has open-source drivers for the printer, can this defend against ink cartridges scams?

---

### Post by freemedia2018 on 2018-12-12
It depends on where the chip works. If the driver has to implement the feature, then perhaps it could work around it. 

If the chip causes the printer to report it is low on ink and there's no way to distinguish that from actually being low on ink, the printer could refuse to work regardless of the driver.

It's good to avoid scam-like brands either way, but it would be nice if software could help thwart the scam. I would classify such a chip as an example of malware in hardware. There aren't many of those, but there will be more of them in the future.

---

### Post by oldrocker99 on 2018-12-13
I know that Epson reinking kits, at least in the past, had a device that would reset the chip.

---

### Post by SagaciousKJB on 2018-12-14
> **freemedia2018 said:**
> It depends on where the chip works. If the driver has to implement the feature, then perhaps it could work around it. 

If the chip causes the printer to report it is low on ink and there's no way to distinguish that from actually being low on ink, the printer could refuse to work regardless of the driver.

It's good to avoid scam-like brands either way, but it would be nice if software could help thwart the scam. I would classify such a chip as an example of malware in hardware. There aren't many of those, but there will be more of them in the future.

I mean, define "scam-like" brands.  I bought an HP printer, and on Windows it would tell me the ink was too low to print anything.  I installed an open-source driver for it on Ubuntu, and it printed a faded page.  Granted it wasn't lying the ink level was low, but couldn't this be seen as a way to get users to buy more ink?  Kind of holds you hostage to go buy another cartridge if you can't even print one simple page of paper, faded or not.

---

### Post by freemedia2018 on 2018-12-14
I mean I would at least try to avoid any brand that does such things to their customers.

Really intended as a subjective placeholder, you decide what threshold of abuse you're willing to tolerate. We are talking about printers, after all. Inkjets at that. I figured they were invented to encourage people to lose all faith in humanity.

I get inspecific when I think the valid answers are diverse enough to justify it.

---

### Post by QIII on 2018-12-14
Just about all printers these days are little more than a gimmick to get you to buy expensive ink.  They are actually a loss leader to hook ink sales.

---

### Post by QIII on 2018-12-15
Nothing there that isn't simple business practice in any number of industries.  Businesses exist to make money.  Up-selling is a standard practice.  Selling something for the best price you can get on the eve of a sale is just good business.  A wary buyer watches for sales anyway.  Selling a commodity that is in high demand for a premium price is how business works.
 
Your car runs on gas and can be filled with fuel as often as it runs out.  Your printer is connected to a common electrical grid and gets as much "fuel" as it needs.  Ink is NOT the fuel your printer runs on.

But you can void the warranty on your car by using the wrong brand of oil and you can void the warranty on your printer by using aftermarket/refilled ink cartridges.

One might has well march and wave signs protesting the exact force of gravity as band together to bring down businesses that don't give away the milk.

The printer is a loss leader to drive ink sales.  That's the nature of the industry.  If you find a printer manufacturer who sells you a printer for a reasonable price and gives you the ink for free for the life of the printer, don't rush to buy stock in that company.  It'll go bankrupt -- and you won't get any customer support any longer.

There are far more meaningful things going on in the world over which to get your bowels in an uproar.

---

### Post by SagaciousKJB on 2018-12-15
> **QIII said:**
> Nothing there that isn't simple business practice in any number of industries.  Businesses exist to make money.  Up-selling is a standard practice.  Selling something for the best price you can get on the eve of a sale is just good business.  A wary buyer watches for sales anyway.  Selling a commodity that is in high demand for a premium price is how business works.
 
Your car runs on gas and can be filled with fuel as often as it runs out.  Your printer is connected to a common electrical grid and gets as much "fuel" as it needs.  Ink is NOT the fuel your printer runs on.

But you can void the warranty on your car by using the wrong brand of oil and you can void the warranty on your printer by using aftermarket/refilled ink cartridges.

One might has well march and wave signs protesting the exact force of gravity as band together to bring down businesses that don't give away the milk.

The printer is a loss leader to drive ink sales.  That's the nature of the industry.  If you find a printer manufacturer who sells you a printer for a reasonable price and gives you the ink for free for the life of the printer, don't rush to buy stock in that company.  It'll go bankrupt -- and you won't get any customer support any longer.

There are far more meaningful things going on in the world over which to get your bowels in an uproar.

I think that's probably more the case for consumer-level printers.  It's honestly less trouble just to toss those ones when they start having problems.  I mean, I'm pretty technically proficient; I can install linux on my toaster and debug C programs with my swiss army knife.  But I will  NOT troubleshoot a family member's printer.  Here's my deskjet trouble shooting guide: Is it broken? Buy a new one.  I'm just glad I've never had to wrestle with one of those enterprise level ones.  Scenes from Office Space come to mind.

But yeah I notice the industry has adapted.  You can get a nice printer-scanner combo for about 50 bucks on sale at any given time at Wally World, and it comes with a pack of ink.  What's that old phrase though, 'The first time's free.'  Well, I've literally been able to buy a brand new printer with ink for less money than it would cost to buy fresh new ink cartridges for my older printer.  I feel like THAT is getting a little ridiculous.

I use to watch The Screen Savers on TechTV a lot, and they compared it to Gillette.  They can make a razor that lasts 100 years, but then they'd go out of business.

---

