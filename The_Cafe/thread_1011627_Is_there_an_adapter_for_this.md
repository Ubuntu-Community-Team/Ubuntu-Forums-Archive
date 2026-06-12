---
title: "Is there an adapter for this?"
date: 2008-12-15
forum: The Cafe
---

### Post by zmjjmz on 2008-12-15
[http://xs.to/xs.php?h=xs134&d=08511&f=img_1150920.jpg](http://xs.to/xs.php?h=xs134&d=08511&f=img_1150920.jpg)
So yeah, I'm trying to install a PCI ethernet card in a 486.
Is this hopeless?

---

### Post by Mr. Picklesworth on 2008-12-15
> ...a 486...Give up now and get a modern computer. You can pick a used one up for pennies!

As far as I am aware, there are rarely - if ever - adapters between these buses. Once you get down to the hardware stuff at this level the slightest change can render the interface quite meaningless.

Err, good luck though ;)

---

### Post by zmjjmz on 2008-12-15
> **Mr. Picklesworth said:**
> Give up now and get a modern computer. You can pick a used one up for pennies.

But I love my 486 :(
It turns out I need an ISA adapter. I guess I'll buy that along with an IDE to CF adapter.

---

### Post by MikeTheC on 2008-12-15
> **Mr. Picklesworth said:**
> Give up now and get a modern computer. You can pick a used one up for pennies!

As far as I am aware, there are rarely - if ever - adapters for these buses. They are different shapes for many reasons, and once you get down to the hardware stuff at this level the slightest change can render the entire interface meaningless.

Err, good luck though ;)
Pretty much agree here. Considering what a new system can cost these days, there's so little point in putting any money into old equipment.

---

### Post by zmjjmz on 2008-12-15
[http://www.amazon.com/gp/offer-listing/B00004XRD1/sr=/qid=/ref=olp_tab_new?ie=UTF8&coliid=&me=&qid=&sr=&seller=&colid=&condition=new](http://www.amazon.com/gp/offer-listing/B00004XRD1/sr=/qid=/ref=olp_tab_new?ie=UTF8&coliid=&me=&qid=&sr=&seller=&colid=&condition=new) 
This looks like what I want.

---

### Post by MikeTheC on 2008-12-15
> **zmjjmz said:**
> [http://www.amazon.com/gp/offer-listing/B00004XRD1/sr=/qid=/ref=olp_tab_new?ie=UTF8&coliid=&me=&qid=&sr=&seller=&colid=&condition=new](http://www.amazon.com/gp/offer-listing/B00004XRD1/sr=/qid=/ref=olp_tab_new?ie=UTF8&coliid=&me=&qid=&sr=&seller=&colid=&condition=new) 
This looks like what I want.

Sure, it'll work. It's only 10bT, but what the heck, you probably shouldn't expect that much more out of the system, given the capabilities of the bus.

---

### Post by zmjjmz on 2008-12-15
> **MikeTheC said:**
> Sure, it'll work. It's only 10bT, but what the heck, you probably shouldn't expect that much more out of the system, given the capabilities of the bus.

Dude, it's a 486. I barely expect it to work (most 486's I've worked with had a freaked out CMOS battery).

---

### Post by Rhubarb on 2008-12-15
You should be able to pick up a 2nd hand ISA network adapter from a computer market.

With ISA cards, you'll need to set the IRQ and the DMA jumpers on it.

---

### Post by Dr. C on 2008-12-15
It depends on the motherboard. Some 486 motherboards supported VESA (an extended ISA bus) or pci, Otherwise an ISA ethernet card likely 10baseT is what you need.

---

