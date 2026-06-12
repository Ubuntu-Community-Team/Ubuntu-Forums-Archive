---
title: "Desktop computer"
date: 2019-05-30
forum: Ubuntu, Linux and OS Chat
---

### Post by wheelsmith on 2019-05-30
Who makes a good Linux Desktop computer?

---

### Post by Frogs Hair on 2019-05-30
Not a support request, moved to *Ubuntu Linux & OS Chat*.

---

### Post by LwIh%*7 on 2019-05-30
That depends, companies vary, I for one go for the Novatech company and buy a computer without and operating system installed so that I can have Linux on it. You can have many other companies doing the same like for example PC Specialists, Origin PC etc.

---

### Post by rbmorse on 2019-05-30
Linux support for desktops isn't the big adventure that it can be for laptops.  For the most part, it just works. Support for CPUs and PCHs is excellent and generally available when new products hit the store shelves (we'll see how well AMD prepared for the Ryzen 3000/x570 motherboards in just about six weeks.).  

Intel and Nvidia graphics subsystems are generally well-supported. AMD/ATI graphics too, although historically it may take a a full release cycle before your chosen distribution makes the driver sets that deliver satisfactory performance and reliability available for a brand new chipset.  A very, very few AMD desktop chipsets have proven to be particularly touchy about working with Linux...these are generally integrated CPU/GPU (known as APUs) like the 2200 series. 

If there are going to be issues it will be with support for peripherals like network adapters or audio subsystems, or "features" that are strictly cosmetic, like support for inside the case LED lighting. You can blame the motherboard manufacturers as they don't provide Linux compatible versions of their software utilities. 

The best advice I can offer is to do your shopping, pick a specific product and then post another question asking people to relate their experience with that specific product.

---

### Post by Autodave on 2019-05-30
One bit of advice: make sure that you are actually buying a desktop and not a desktop with a laptop motherboard in it!  I know that sounds crazy, but I have run into 2 such machines lately.  The telltale thing is to look at the power cord: if it is a brick (like what you get with a laptop) do NOT buy it!

Both of these machines were in a standard desktop case, but both had tiny little MBs in them.  No way to upgrade anything except adding some memory. No slots for GPUs, sound cards, etc.

---

### Post by oldos2er on 2019-05-30
I've had good luck with Dell desktops,  for general home use. The XPS series has been reliable. I upgrade the video hardware though.

---

### Post by rbmorse on 2019-05-30
I know some HP laptops are hard to convert off Windows because of some non-standard UEFI elements.   I have no experience with recent HP desktops.

---

### Post by TheFu on 2019-05-30
Putting the parts into a computer is easier than building a Lego tie fighter. The parts are all key'd so they only fit one direction these days.  The manual explains the order to do it and if you watch one youtube video on putting the parts into a case, it is pretty easy.

If you have a screwdriver and 45 minutes, you can get excellent, specific, components and almost always reuse existing parts to save 50% on a new desktop.  There have been some freakin' amazing deals on AMD Ryzen and motherboards the last few months.  $130 MB+CPU combos for a Ryzen 1600 are still going on now. Add 8-16G of DDR4 RAM for $50-$100 and you have a smokin system for under $250.  Reuse the case, PSU, keyboard, mouse, monitor, GPU, HDD(s), SSD(s), speakers, webcam ... whatever else you have.  About 6 months ago, I build a little faster machine for over $400, which was a crazy deal at the time.  RAM prices have dropped about 50% in the last 6 months.

Most of my cases in use today are from early 2000 timeframes. It is just a case. They don't wear out.

CPUs that come with a fan (like the Ryzen 5 line) will have the thermal paste pre-applied, so even that part is already handled perfectly. As others have stated above, the only real concern is using Ryzen-based APUs, like the 2200g, 2400g and newer 3xxxg lines coming out next month.

What better reputation do you need when you can pick the exact motherboard, which is the most important component for any OS compatibility.  

Also, beware that small cases usually mean smaller size motherboards. There are 2 standards, ITX and microATX. These trade size for expansion. "Shuttle" is a brand that makes boot-box sized computers with good performance, good price, but limited expansion to fit into the cases which are about half the size of a mid-tower. These don't cost $120+ more than equivalent desktops like NUC versions do.  NUCs are as small as possible and effectively have zero way to upgrade anything inside the box.  The Shuttle brand computers generally support half length GPUs and (2) 3.5" hdds and come with multiple NICs, USB3, eSATA and optical connections.  I've run Ubuntu on Shuttles for family members since 2010. They liked the smallish size and that the cost wasn't out of line with normal systems.

Building isn't for everyone, but if you'd like to save $200+ on a new system, it is definitely worth considering.

---

### Post by DuckHook on 2019-05-30
> **TheFu said:**
> Putting the parts into a computer is easier than building a Lego tie fighter.
A Lego tie fighter may be easy for *you!* Not so much for *me*. :tongue:
> &#8230;if you'd like to save $200+ on a new system, it is definitely worth considering.
Not sure that one could save $200 these days. The thing about pre-assembled machines is that, even with the MS tax, the assembly-line nature of the build, the low third-world labour rates and the bulk-buy component discounts available to the OEM (but not to us) often make them more cost-effective than spinning your own box.

I build my own not because it's less expensive, but because I can dictate *exactly* what I want and thereby highly customize it. If one sticks to proven. mainstream components that are neither too old nor too new, Ubuntu installs like a champ.

---

### Post by Autodave on 2019-05-31
+1 with Duckhook.  I had purchased an RX590 8 gig video card.  Upon installing it, it evidently was defective and shorted out my motherboard wiping out the sound and replacing it with a loud static noise.  Reinstalling the old sound card did not repair my sound.  Further diag showed that the MB had been ruined.  The manufacturer of the card and seller of the card both said that it wasn't their fault and both refused to offer any assistance.

So, I considered upgrading that machine or building a new one.  I also looked for deals on pre-built systems.

My new machine cost about $15 more than what the parts would have cost *before* I added and shipping costs.  And, I still had to wonder what would happen if I got another bad part that would take out other new parts.  In the end, I purchased a complete unit and let the warranty fall on the supplier.

---

### Post by TheFu on 2019-05-31
But who doesn't have a case, PSU, HDD, keyboard, optical drive, NIC, mouse, monitor already?  All that adds up to about $200.
Every 5-10 yrs, I swap out my MB and CPU for about $200 total and reuse everything else I can.  This last upgrade forced DDR4 onto me, so it was $150 more.  But that was going to happen regardless.

The new system replaced 3 other machines here in performance.  Electricity use has dropped $10-$15/month.

I've been doing this since being totally screwed over by multiple "pre-built" desktop systems from well known vendors. One of my clients have me a high-end CAD workstation from a well-know vendor.  It was hot, noisy, and a dust magnet. It had a Raptor HDD, which was very noisy. Eventually, the GPU failed, which was fine, since I was using it to run about 15 virtual machines.  I remember the day I turned that machine over to one of my business partners.  The room wasn't as hot or noisy.

When you pick the components, you get to choose what's important to you, like being quiet. I don't go crazy and use liquid cooling. The stock Ryzen fans do fine.  Plus, there isn't a huge month of spending to get a $900 desktop.

I suppose we will agree to disagree on this and for completely non-technical people, buying is probably the best choice. If you have never changed the oil in your car-types of people.  OTOH, if you've installed a new HDD into a computer even once, then putting a MB+CPU+RAM+HDD inside a case really isn't any harder.  Just more connections, that's all.

---

### Post by SeijiSensei on 2019-05-31
I've installed Linux on a variety of desktop machines. In general I prefer Dells. I have an ASUS connected to my TV.  It had a stupid warranty that was broken as soon as I opened the case to install an NVIDIA card.  It works fine, but that warranty??

NewEgg has a lot of refurbished Dells if you're on a budget. These all have at least an i5: [https://www.newegg.com/p/pl?Submit=ENE&N=50010772%204814%208000%204016%20100019096%20601190701%20601190702&IsNodeId=1&d=dell%20desktop&bop=And&Order=PRICE&PageSize=36](https://www.newegg.com/p/pl?Submit=ENE&N=50010772%204814%208000%204016%20100019096%20601190701%20601190702&IsNodeId=1&d=dell%20desktop&bop=And&Order=PRICE&PageSize=36)

---

### Post by charlieg on 2019-06-02
Punch do in the UK.

---

