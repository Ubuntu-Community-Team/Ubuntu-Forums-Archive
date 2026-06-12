---
title: "computer peripherals connectors - why is their change neccesary?"
date: 2009-05-09
forum: The Cafe
---

### Post by KhaaL on 2009-05-09
So I was watching a short film called [story of stuff]("http://www.storyofstuff.com/") and that covers consumerism, and considering that capacity is doubled every 18 months. However, one thought struck me that I really didnt have a answer for... *why* do computer components have their connectors changed? in the case going from AGP to PCI-E the gain was very marginal, in the case of RAM memory I belive the gain was more noticable, and CPUs... well, AMD and Intel stubbornly have their own type connectors, and with every generation we get a different socket (which i admittedly havent dug into). Is there a legitimate reason/gain for those socket changes?

---

### Post by BuffaloX on 2009-05-09
Mostly yes sometimes no.

For instance new CPUs have more address pins, because they can access more RAM. Newer CPUs run on lower voltages than older ones, accidentally inserting a new CPU in an old socket, would burn the new CPU.

PCI was getting too slow for some tasks, so they made PCIE.
AGP was still good enough, but was near impossible to speed up further, and would soon be obsolete anyway. So instead of replacing PCI first and AGP later, they replaced both at the same time, and by using the same standard for both, saved some costs.

In earlier days incompatible sockets and connectors were often used to artificially segment the market, essentially selling the same technology at two different prices, to me it seems this is rarely the case today.

---

### Post by glotz on 2009-05-09
Sales.

---

### Post by 3rdalbum on 2009-05-09
I don't understand why USB connectors are different.

I mean, I agree that the device end should be different to the host end. But there are SO MANY device ends; there's the "B" end, and the "Mini-USB" end; and then there's five or six weird standard ends; and then there are a hundred proprietary ends. (iPod, anyone?)

Why does my phone use a tiny non-standard USB connector when there's enough room for a Mini-USB connector? For that matter, why do we need B-type and Mini-USB? Why not just always use Mini-USB, as it seems to work just as well as the B-type end?

And then there are unscrupulous companies that go around selling A-to-A (host-to-host) USB cables; I've even seen them free on the covers of PC magazines. I'm yet to encounter a device that actually has a host connector. I think those cables get sold entirely with the purpose that some poor schmuck will think "Hey, I can network two computers together with this!" and buy it, not realising that some USB cards can be destroyed by connecting them to another computer.

---

### Post by richg on 2009-05-09
So, change is inevitable. So, an option is struggle.

Rich

---

### Post by Skripka on 2009-05-09
CPU connectors are different to ensure that a user does not try to use incompatabile hardware.

On the Intel side for instance, Core i7 are made with DDR3 memory and only DDR3 memory in mind.  LGA775 is made with DDR2 and only DDR2 in mind.  This is why keyings are different.

Also over time the number of pins has gone up so as to increase bandwidth.

---

### Post by Skripka on 2009-05-09
> **3rdalbum said:**
> I don't understand why USB connectors are different.

I mean, I agree that the device end should be different to the host end. But there are SO MANY device ends; there's the "B" end, and the "Mini-USB" end; and then there's five or six weird standard ends; and then there are a hundred proprietary ends. (iPod, anyone?)

Why does my phone use a tiny non-standard USB connector when there's enough room for a Mini-USB connector? For that matter, why do we need B-type and Mini-USB? Why not just always use Mini-USB, as it seems to work just as well as the B-type end?

And then there are unscrupulous companies that go around selling A-to-A (host-to-host) USB cables; I've even seen them free on the covers of PC magazines. I'm yet to encounter a device that actually has a host connector. I think those cables get sold entirely with the purpose that some poor schmuck will think "Hey, I can network two computers together with this!" and buy it, not realising that some USB cards can be destroyed by connecting them to another computer.

On the phone end..I seem to recall the EU issuing an ultimatum to at least standardize power brick connectors.

---

### Post by MikeTheC on 2009-05-09
See, now here's the thing. I *was* going to write a post in part about how USB isn't all that complex a standard, but actually, you're right. It is.

[Take a look at just how convoluted it's become.](http://en.wikipedia.org/wiki/USB#Types_of_USB_connector)

In *general* things have been simplified down considerably from how they used to be, especially with regard to the PC platform. You had serial, parallel, SCSI and, frankly, a host of other quasi-standard and very proprietary standards used for all kinds of devices. That's not even getting to connectors used on the motherboard, which took some time for the industry to even standardize on, and then that's gone through quite a number of iterations. PCs used to use ISA, for instance, which was eventually upgraded to "enhanced" or E-ISA. That more-or-less became the standard on PCs, while at the same time Apple was using NuBus, which arguably was technologically superior (32 bit vs 8 bit). However, that battle was lost (not just for Apple, but through an overall computer industry transition) to PCI. I remember the introduction of PCI, and it went a loooooooooong way towards allowing the incorporation of self-configuring "plug-n-play" capabilities on the hardware end.

For those of you who weren't into the PC scene back in the 80s and early 90s, it was a mess of having to manually deal with IRQ, I/O Address and DMA settings with jumpers on the cards. There was little or no handling of any of this by the OS, and so it was very, very easy to run out of IRQs and then having to pick and choose which set of capabilities you wanted to use, like "do I want to use the modem, or do I want to hear sound?" and that sort of crap. (For what it's worth, Apple never subjected its Mac users to this. We used to laugh about it a lot.)

Some things have been brought out as a means of standardizing on one particular interface bus, like USB. Other interfaces have been introduced to supplant older ones for performance reasons, like SATA. Ultimately, you have to keep up or you will be left behind. With apologies to Heraclitus, the only constant in the computer world is change.

---

### Post by Kareeser on 2009-05-09
I believe that's what the initial aim of USB was... to standardize everything into one port... but in the end, USB ended up with several shortcomings which were not easily addressed. Namely in that a USB port can't power 7200RPM hard drives or CD-ROM drives.

As for the different proprietary connectors? That's just sales, I'm pretty sure.

---

### Post by MikeTheC on 2009-05-09
> **Kareeser said:**
> I believe that's what the initial aim of USB was... to standardize everything into one port... but in the end, USB ended up with several shortcomings which were not easily addressed. Namely in that a USB port can't power 7200RPM hard drives or CD-ROM drives.

As for the different proprietary connectors? That's just sales, I'm pretty sure.

Yes, however, thanks to both USB and FireWire, we have come to accept on-the-fly OS configuration and hot-plugging as standard features. You try that crap with IDE, Parallel or SCSI and tell me how well it works out for you.

---

### Post by KhaaL on 2009-05-09
> **MikeTheC said:**
> 
[...]
For those of you who weren't into the PC scene back in the 80s and early 90s, it was a mess of having to manually deal with IRQ, I/O Address and DMA settings with jumpers on the cards. There was little or no handling of any of this by the OS, and so it was very, very easy to run out of IRQs and then having to pick and choose which set of capabilities you wanted to use, like "do I want to use the modem, or do I want to hear sound?" and that sort of crap. (For what it's worth, Apple never subjected its Mac users to this. We used to laugh about it a lot.)

Haha, that brings back memories :mrgreen:

---

### Post by RandomJoe on 2009-05-09
> **3rdalbum said:**
> And then there are unscrupulous companies that go around selling A-to-A (host-to-host) USB cables; I've even seen them free on the covers of PC magazines. I'm yet to encounter a device that actually has a host connector. I think those cables get sold entirely with the purpose that some poor schmuck will think "Hey, I can network two computers together with this!" and buy it, not realising that some USB cards can be destroyed by connecting them to another computer.

I actually do have a device that uses an A-to-A cable!  It's an old Linksys USB  802.11b wireless network card.  (Can't be bothered to walk down the hall to see what the model number is...)  But other than that, no I haven't seen anything else that uses one either.

---

