---
title: "Ease of upgrading processors and effect upon warranty?"
date: 2007-03-24
forum: System76 Support
---

### Post by sbergman27 on 2007-03-24
I am basically sick of futzing with my Compaq v2552us with its components made by manufacturers who don't care about their customers. (In particular, Broadcom) and would like to show support for System76.  However, I'm limited on funds right now and can't really buy the machine that I want.  I  was thinking about either the Darter or Gazelle Value, but with the minimum processor.

How difficult is it to upgrade the processor in these machines later and how might it affect the warranty?

In any case, I will be purchasing 2 Gazelle Values for a customer of mine early next week.

After looking over the System76 site, I'm really excited.

I have been using Microtel units from Walmart and Amazon for cheap point of sale stations.  The Ratel looks like a great replacement.  A little more expensive, but I would leave the Ubuntu on it rather than replace the Linspire with CentOS, so they would actually be about the same price to my customers.

---

### Post by crichell on 2007-03-26
> How difficult is it to upgrade the processor in these machines later and how might it affect the warranty?

It's easy to upgrade the processor - it's accessible from a panel on the bottom of the computer.  We'll still honor our warranty with you - we just wouldn't warranty the new processor.

---

### Post by AusIV4 on 2007-04-25
Sorry to revive a dead thread but...
I purchased a Gazelle Value in February. I got minimum specs because I thought I'd just be using it to take notes in class. Now I've decided that it could easily replace my primary laptop, but I'd like to up the processing power (and maybe the RAM) a little bit first. The way I understand it, I could open a panel on the back of the Gazelle, pop out the Celeron M, and put a Core 2 Duo in it's place. Is this correct? A Core 2 duo is a bit pricey if I'm not going to be absolutely certain it will work in my system.

---

### Post by thomasaaron on 2007-04-25
Yep. Remove the battery (and adapter :lolflag: ), the back panel, and the heat sync over the processor. There is, I think, a little white tab that locks the CPU into the socket. Unlock it and replace the processor. (Then do all of this in reverse to put it back together :) )

You can replace it with any of these:
Core 2 Duo T5500 1.66GHz 2MB 667FSB
Core 2 Duo T5600 1.83GHz 2MB 667FSB
Core 2 Duo T7200 2.0GHz 4MB 667FSB
Core 2 Duo T7400 2.16GHz 4MB 667FSB
Core 2 Duo T7600 2.33GHz 4MB 667FSB

You may have to re-image it, though. Not exactly sure.
If so, you'd need to back up your files.

---

### Post by AusIV4 on 2007-04-25
> **thomasaaron said:**
> You may have to re-image it, though. Not exactly sure.
If so, you'd need to back up your files.

I assumed I'd have to reinstall the OS, I just wanted to make sure I wasn't going to have any hardware problems.

Thanks.

---

### Post by BroncoInCalifornia on 2007-04-26
I upgraded to a T7200 on a Pangolin ( an Asus S96F).  I changed to the dual core processor and it just worked.  I did not have to change any settings or reinstall any software.

---

### Post by TheMono on 2007-04-26
The generic kernel should be fine with a new processor. Sure, back up first, but I'm pretty sure it should just 'plug and play' processor.

---

### Post by AusIV4 on 2007-04-26
Can anyone tell me where I might be able to buy one of those processors? I've looked around online and I haven't found anyone selling the mobile core 2 duos without laptops accompanying them. Even intel's site only lists the desktop processors as available boxed. Is it possible to buy one through System76?

---

### Post by Alvinius on 2007-04-26
Well here are a few [http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2+50001157+40000343+1389627504&name=Mobile](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2+50001157+40000343+1389627504&name=Mobile)

---

### Post by g14 on 2007-05-13
> **AusIV4 said:**
> I assumed I'd have to reinstall the OS, I just wanted to make sure I wasn't going to have any hardware problems.

Thanks.

No, you will *not* have to re-install any Linux operating system after replacing things such as ram or the processor. The processor speed or amount of ram is not hard coded and as a matter of fact, Linux supports hotplugging cpus AND ram if the underlying motherboard does also.

Note that these motherboards don't support hotplugging ram or cpu and I wouldn't advise you try doing it.

---

