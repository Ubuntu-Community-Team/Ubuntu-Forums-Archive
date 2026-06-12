---
title: "Internal HSDPA for Thinkpad T42? Mini PCI or Hack?"
date: 2008-07-05
forum: The Cafe
---

### Post by animaniac on 2008-07-05
I cant find any HSDPA adapters for mini PCI, they only seem to be available for Mini PCI-E which my laptop doesn't have.

Dose anybody know of either a mini-PCI option i might not have seen or a not too advanced hack(read: i have soldering iron, but am lacking in skill) that would work with my laptop, and Ubuntu.

As for PC-Card options, they tend to stick-out too much, a reason why im not too keen on the USB alternatives either.

---

### Post by animaniac on 2008-07-06
Thousands of people on-line and no suggestions as how to accomplish this?

---

### Post by mips on 2008-07-06
There are no mPCI mobile cards available that I know of. There are also no mPCIe to mPCI adapters available and I do not thinh the two standards are interchangeable.

I know the mPCIe supports both USB2.0 and mPCI busses so it *might* be possible to hack it to connect directly to the internal USB bus of your laptop. This is all wild speculation on my part so take it with a pinch of salt but worth looking into though.

[http://www.pcisig.com/home](http://www.pcisig.com/home)
[http://www.pcisig.com/specifications/conventional/mini_pci/](http://www.pcisig.com/specifications/conventional/mini_pci/)
[http://en.wikipedia.org/wiki/PCI_Express_Mini_Card](http://en.wikipedia.org/wiki/PCI_Express_Mini_Card)

Going this route seems a bit radical and complicated if not impossible.

> As for PC-Card options, they tend to stick-out too much, a reason why im not too keen on the USB alternatives either.

What if the card had no external portrusion? Zadago has a card with a light external antennal which *looks* detachable and even if it wasn't I'm sure you could remove it. If you could remove it then one could drill a small hole in the laptop casing and route a flexible wire antenna (similair to wireless ethernet) into the laptop and up into the screen as they do with WLAN. The model I'm referring to is the Aircard 850, [http://www.zadako.sk/product_info.php?products_id=366](http://www.zadako.sk/product_info.php?products_id=366)

EDIT: The antenna is completely removable.

EDIT2: The card dimensions are 86mmx54mmx5mm so it will definately not portrude.
[http://www.business.orange.co.uk/servlet/Satellite?blobcol=urldata&blobheader=image%2Fgif&blobkey=id&blobtable=MungoBlobs&blobwhere=1213962141770&cachecontrol=0%3A0%3A0+*%2F*%2F*&ssbinary=true](http://www.business.orange.co.uk/servlet/Satellite?blobcol=urldata&blobheader=image%2Fgif&blobkey=id&blobtable=MungoBlobs&blobwhere=1213962141770&cachecontrol=0%3A0%3A0+*%2F*%2F*&ssbinary=true)

Also have a look at their PC-300 & Aircard 875 models as they have external pertrusions but it really does not protrude by much and might be a viable option for you. I suspect they will be linux compatible (depending on the card chipset) as I have see them mentioned in conjunction with linux.
[http://www.zadako.sk/information.php?info_id=12](http://www.zadako.sk/information.php?info_id=12) I see linux drivers specified here.

[http://www.zadako.sk/redirect.php?action=url&goto=www.sierrawireless.com](http://www.zadako.sk/redirect.php?action=url&goto=www.sierrawireless.com)

Hope this is of some help.

---

### Post by animaniac on 2008-07-06
thanks, I'll look into the PC-card alternatives, they do look quite a bit more compact than the last one i saw. 

although the question now is should i go with something that sticks out more for higher speed (my operator supports 7.2, and 14.4 is planned for Q4) or live with lower speed, i gonna take that bucket of häagen-dazs from the icebox to help my decision.

---

### Post by mikeh on 2008-07-19
The usual approach is to use a Bluetooth connection to a mobile phone.

I suppose you could get the pinout for the docking connector, trace the leads, and use one of the USB ports from that.
  Has anybody done this?

---

### Post by mips on 2008-07-20
> **mikeh said:**
> The usual approach is to use a Bluetooth connection to a mobile phone.


That means he will have to go and buy a HSDPA enabled phone.

---

### Post by mikeh on 2008-07-20
> **mips said:**
> That means he will have to go and buy a HSDPA enabled phone.

Well, he has to buy something. Phones are sold in much bigger quantities and may not cost much more. e.g. Nokia 6120/6121 .

I'm sure you could fit a USB modem (minus case) inside the T42, as people have done with the EeePC.

---

### Post by mips on 2008-07-21
> **mikeh said:**
> 
I'm sure you could fit a USB modem (minus case) inside the T42, as people have done with the EeePC.

It should be possible if space permits. Never opened one of those USB device so I have no idea how big the PCB is.

EDIT:
Did some googling:
[http://forum.eeeuser.com/viewtopic.php?id=22284](http://forum.eeeuser.com/viewtopic.php?id=22284)
The [E172]("http://www.huawei.com/news/view.do?id=5402&cid=42") is really small and should fit just about anywhere in a laptop.

---

