---
title: "Expanion slot availability"
date: 2009-11-08
forum: System76 Support
---

### Post by echo314 on 2009-11-08
The [Wildebeest Performance ]("http://system76.com/product_info.php?cPath=27&products_id=98") has listed 

Expansion Slots: 1 x PCI Express X16 slot

1. Does this mean, in addition to the slot already being used by the graphics card, there is an additional open slot, or is this the slot being used by the card? 

2. I know CPUs can become quickly obsolete as far as upgrading an existing mobo goes because of socket changes of the CPU and whatnot. Will the graphics card slot, the x16, work with something like a GTS 250 if I wanted to upgrade in the future, which certainly looks like a very capable card?

[SOLVED thanks to insight from jbelmonte]
3. (Unrelated) Here are some of the RAM options
4 GB - 2 x 2 GB - DDR3 - 1333 MHz ( +$89.00 )
8 GB - 4 x 2 GB - DDR3 - 1333 MHz ( +$210.00 )

So 2 sticks cost 89, but 4 cost 210 (instead of 178 ). I understand in other cases that denser memory modules cost more, but since these are the same presumably why is there an extra $32 for 4 sticks? Maybe it was meant to be 2x4GB, so thats 2 4GB sticks which makes sense it would be pricier.

As always, I appreciate your support Thomas!

(another edit) 4. I thought the i7 8xx did not have QPI, instead having DMI. Yet the site says 
Intel Core i7-870 2.93 GHz L2 8 MB **QPI** 2.5 GTs. 

I'm basing this of a few sites, here is what Wikipedia has to say 
"Lynnfield is the second processor sold under the Core i7 brand, while at the same time being sold as Core i5. Unlike Bloomfield, it does not have a QPI interface but directly connects to a southbridge and other devices using a 2.5 GT/s Direct Media Interface and PCI Express links in its Socket 1156."

and because I have enough random questions already...
5. On a single core system I would not question that going from 2.8GHZ to 2.93 for several hundred dollars more would not be worth it, for the 133MHz gain. I guess with the quad though, the gain would be more like 4x133MHz (from the i7 860 to 870), which is a little more then .5GHz gain overall. That looks a little more respectable. But noticeable, not sure.. Ok no question, just my thoughts...jeeze I should just take my thoughts to a blog already. :)

---

### Post by jbelmonte on 2009-11-08
I think I can answer number 3. You are not taking into account the 1GB stick that is in the base configuration. When upgrading from 1GB to 4GB, the upgrade price is NOT for the full 4GB, it is for the full 4GB LESS the 1GB stick they are removing. When upgrading from 4GB to 8GB, they are just adding 4GB, so the upgrade price is for the full 4GB. The 1GB stick costs about $35, which is the upgrade price from 1GB to 2GB.

---

### Post by thomasaaron on 2009-11-09
> 1. Does this mean, in addition to the slot already being used by the graphics card, there is an additional open slot, or is this the slot being used by the card?

Yes.

> 2. I know CPUs can become quickly obsolete as far as upgrading an existing mobo goes because of socket changes of the CPU and whatnot. Will the graphics card slot, the x16, work with something like a GTS 250 if I wanted to upgrade in the future, which certainly looks like a very capable card?

It should.

> [SOLVED thanks to insight from jbelmonte]
3. (Unrelated) Here are some of the RAM options
4 GB - 2 x 2 GB - DDR3 - 1333 MHz ( +$89.00 )
8 GB - 4 x 2 GB - DDR3 - 1333 MHz ( +$210.00 )

So 2 sticks cost 89, but 4 cost 210 (instead of 178 ). I understand in other cases that denser memory modules cost more, but since these are the same presumably why is there an extra $32 for 4 sticks? Maybe it was meant to be 2x4GB, so thats 2 4GB sticks which makes sense it would be pricier.

I think it has something to do with the original stick of memory that is figured into the base price costs about $35. But I'm having trouble getting my mind around the math this early in the morning. I'm not really in the inner circle when it comes to the hows and whys of pricing..

> (another edit) 4. I thought the i7 8xx did not have QPI, instead having DMI. Yet the site says
Intel Core i7-870 2.93 GHz L2 8 MB QPI 2.5 GTs.

I'm basing this of a few sites, here is what Wikipedia has to say
"Lynnfield is the second processor sold under the Core i7 brand, while at the same time being sold as Core i5. Unlike Bloomfield, it does not have a QPI interface but directly connects to a southbridge and other devices using a 2.5 GT/s Direct Media Interface and PCI Express links in its Socket 1156."

Yes, it uses DMI, not QPI.

> 5. On a single core system I would not question that going from 2.8GHZ to 2.93 for several hundred dollars more would not be worth it, for the 133MHz gain. I guess with the quad though, the gain would be more like 4x133MHz (from the i7 860 to 870), which is a little more then .5GHz gain overall. That looks a little more respectable. But noticeable, not sure.. Ok no question, just my thoughts...jeeze I should just take my thoughts to a blog already. 

It probably would depend on what you were doing with the machine. I imagine if you were compiling kernels, the increased performance would be more noticeable.

---

