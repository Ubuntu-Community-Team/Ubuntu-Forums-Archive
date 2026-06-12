---
title: "Cheap Thin Clients?"
date: 2012-04-18
forum: The Cafe
---

### Post by NexusSloth on 2012-04-18
Anyone know where I can get some cheap thin clients?

Everywhere I go, people want upwards of 200 bucks a piece. I thought thin clients were supposed to save money.

I need like, 30 of them, used or new, don't matter, they just need to be able to PXE boot.

...and yes, i tried amazon and ebay. no dice there, they don't sell 30 of the same unit.

---

### Post by lykwydchykyn on 2012-04-18
Went through the same thing about a year ago; the cheapest solution I could find was the zotac zbox, which is actually a mini computer rather than a thin client.  It will PXE boot, though, which was all I needed.  If you need an onboard OS you'll want something else.

Of course, a zbox with the necessary RAM ended up being around $215 - $240 each.  I know what you mean, you'd think a thin client could be had for under $200 but AFAIK they just aren't out there (new, anyway).

---

### Post by KiwiNZ on 2012-04-18
What is the price and availability of Wyse products in your locale?

---

### Post by Jamis32 on 2012-04-23
[http://www.thinmanager.com/hardware/tk3550.php](http://www.thinmanager.com/hardware/tk3550.php)

$200 out the door.  

As long as you are not adding them into a hazardous industrial environment, they will serve you well.  The reason they get so expensive is when you get into those industrial applications where the box can not have venting or fans.

But these work fine and are PXE boot ready.

---

### Post by lykwydchykyn on 2012-04-23
If you're booting to LTSP or some other Linux-based environment, make sure you get one first for testing.  Some geode drivers were dropped from the kernel a while back, and some of the Wyse clients I tested had a VIA chipset that only worked with a proprietary driver that I had to download from an obscure website and manually hack into the client image.

You don't want to end up with 30 doorstops...

---

### Post by Roasted on 2012-04-23
Avoid VIA like the plague. They're just not reliable chipsets with Linux. LTSP is pretty much amazing, though. I set up some LTSP servers on some old P4 boxes that had terrible HDD controllers. The controller was so slow, XP would just draggggggg on it. By setting them to PXE boot and dropping an Ubuntu LTSP + DHCP server on the VLAN, we bypassed the terrible HDD controllers and they were insanely fast. World of difference.

We were also testing some Intel Atom based ASUS Nettop boxes for future LTSP deployments.

This one in particular was on the radar:

[http://www.google.com/products/catalog?ix=aca&q=asus+nettop&um=1&ie=UTF-8&tbm=shop&cid=13304281670019459150&sa=X&ei=nmuVT9XzO6aI6QGRwt21BA&ved=0CIQBEPMCMAU](http://www.google.com/products/catalog?ix=aca&q=asus+nettop&um=1&ie=UTF-8&tbm=shop&cid=13304281670019459150&sa=X&ei=nmuVT9XzO6aI6QGRwt21BA&ved=0CIQBEPMCMAU)

That was over a year ago, though. There likely may be other products out that are cheaper.

EDIT: Here's one that's about 20-30 bucks cheaper. I don't see a NIC on it but it's listed as having gigabit ethernet. Just a thought:

[http://www.buy.com/pr/product.aspx?sku=223031572&sellerid=14387982](http://www.buy.com/pr/product.aspx?sku=223031572&sellerid=14387982)

---

