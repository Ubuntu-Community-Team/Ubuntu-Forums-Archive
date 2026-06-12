---
title: "Funniest eBay acquisition in years...or: Taking 12 hours to format 300 GB..."
date: 2015-09-27
forum: The Cafe
---

### Post by syntaxerror74 on 2015-09-27
Well, guys, sometimes there are these happy events in life, when you pay a minor sum, and get 10 times as much, just due to your basic knowledge of things...

To begin with, there was an eBay auction not long ago, where somebody sold a couple of HDDs (1TB each) as "For parts or not working" for a less than moderate price. He wrote in the description, that BIOS/UEFI does recognize all drives properly, and that there are neither any bad nor reallocated sectors on the drive (true, telling from SMART). He continued that he bought these himself almost new and he would only sell these drives because he was **not satisfied with their abnormally poor speed** (all drives had identical model).
He was sure that there must be a very specific defect in all of these drives which causes the slowdown.

Since I knew from basic knowledge, that a good SMART result will not affect the speed / throughput in any way, I bought the lot...and I'm telling you, this was a WINNER!!!

One drive was supposed to get an NTFS partition (to be able to access it in multiple OSes) and I started making an unformatted partition in gparted and used **mkntfs** to properly "deep"-format the drive. (I always do that with sensitive data)

Well, but this took plenty of time. **After 12 hours, mkntfs was at about 65%.** I quit this, and when I did a hdparm -I /dev/sdb, my eyeballs almost fell out:
```

# hdparm -I /dev/sdb
...
Commands/features:
        Enabled Supported:
           *    SMART feature set
                Security Mode feature set
           *    Power Management feature set
                Write cache
           *    Look-ahead
           *    Host Protected Area feature set
           *    WRITE_BUFFER command


```

Er...gimme a break!!!
*ALL* of these seemingly "slow" drives **had write-caching set to DISABLED!!**
ROFLMAO...:D :D 
(Must be a doggone hard thing to do trying to drive a mere 50 mph with the brakes on, heh...)
As I had better results with **sdparm** in making settings permanent, I hacked in the following:

```

# sdparm --set=WDC /dev/sdc

```

Incredibly enough, formatting the partition now completed in a few freakin' hours!!
So as you can see, lack of knowledge can easily lead to a totally ridiculous conclusion ("HDD is so painfully slow!").

Nevertheless: for me it was a great bargain ... and a great laugh.

---

### Post by uninvolved on 2015-09-27
I once bought a "neat looking box with pretty blue lights - powers up" for ten bucks with free shipping. I recognized it and figured I might as well buy it for the coming apocalypse. It was an inbound POTS call router. I tested it, dug out the required paperwork, and sold it back on eBay for several thousand dollars but I made the new owner pay for shipping. I did, however, include the printed help files from the PDF that I'd found and downloaded.

I used to drink, heavily, and eventually gave up on my eBay addiction. I made lots of great buys but had so many useless things and I don't think I ever used most of them more than once. These days I mostly collect new hardware that never gets used. Stupid NewEgg and Amazon sales... *sighs* The IT guy at the very small local elementary school loves me. So, there's that.

---

### Post by syntaxerror74 on 2015-09-27
> **uninvolved said:**
> It was an inbound POTS call router. I tested it (...) and sold it back on eBay for several thousand dollars
GRRRR. I hate you so much now. :P :evil:
Why aren't I ever so lucky? Selling that silly thing would have paid my rent by itself for half a year (or maybe even longer).
BTW, a router for several 1000 $$ ? It did not happen to be gold-plated, eh? :P

---

