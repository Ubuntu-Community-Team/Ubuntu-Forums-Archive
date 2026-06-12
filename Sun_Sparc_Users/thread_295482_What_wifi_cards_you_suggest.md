---
title: "What wifi cards you suggest?"
date: 2006-11-08
forum: Sun Sparc Users
---

### Post by mahy on 2006-11-08
Hi y'all,

another question from a complete Sparc noob. I'm about to buy some PCI wifi card for my Ultra 5. As we all know, not all cards work in Linux, and i guess even less work on a Sparc. Moreover, ndiswrapper is unavailable here, which doesn't leave me with many choices. I hope some of you use wireless internet connection and i'd like to receive some suggestions/recommendations from you. I'd like to buy something with good native support in the kernel. Please help me choose wisely. TIA.

Mahy

---

### Post by mahy on 2006-11-08
Well, i found some old TI card with acx111 chipset. I tried it on Athlon XP, where it was a matter of some symlinking and 'modprobe acx'. Then i removed the card to Ultra 5, and guess what? Not even the acx module was found, probably because the driver doesn't work on a Sparc, so it didn't get included into the kernel. Then i tried a card with Ralink chipset (also reported to be working allright), without success. That looks like a real bummer. I can't rely on "this works in Linux" testimonials, coz everything was only tested on x86. ](*,) I'm not saying it's Sparc's fault, i know my Ultra is 64bit, RISC and on top of that big-endian; kinda hard to port drivers from x68. :) What i need is just some advice what to buy.

---

### Post by netztier on 2006-11-08
> **mahy said:**
> What i need is just some advice what to buy.

"Classic" Sun Hardware has never supported WiFi adapters, so why should Linux kernel and module hackers go that long road to port drivers for some WiFi chipset that probably won't even run in a Sun machine?

So why not buy something that does not require a driver? 

Look for "gaming adapters", such as [Linksys WGA-54G ]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1115416826619&pagename=Linksys%2FCommon%2FVisitorWrapper")or [Netgear WGE111]("http://www.netgear.com/Products/Adapters/GWirelessAdapters/WGE111.aspx"). These can be used to hook up non-Wireless-aware devices to your WLAN. However the Linksys part does not (yet?) support anything better than WEP128 encryption, so you're stuck with that...

I have a handful of WGA-54G, but I haven't tried them on my SPARCs. Basically, there's no reason why they should not - they worked flawlessly with Ubuntu 6.06 and 6.10 on my HP Compaq nc6000 laptop.

Be careful though: if I remember correctly, the WGA-54G comes without external power supply, but with a special USB-to-5V cable that draws 5 Volts from a nearby USB port. This is a *very* neat idea for your common Xbox or laptop, but it fails miserably when there's no USB ports on your box... 

regards

Marc

---

### Post by mahy on 2006-11-08
Wow, this kinda shocked me. Should i assume you guys ain't using wifi at all? Well, ok, i'll have to find some other solution. The USB is not a problem for me. I bought a USB expansion card and it 'just works' (NEC chipset); but WEP as a max is a blocker in my case. However, the biggest problem for me is where to find such things. Here in Slovakia, shops are bursting with USB ADSL modems and Bluetooth gadgets, but this kind of hw is hard to come by.

---

### Post by netztier on 2006-11-09
> **mahy said:**
> Wow, this kinda shocked me. Should i assume you guys ain't using wifi at all? 

Not with the SPARC machines, anyway. The older machines don't have PCI slots anyway, and if at all, they're being used as servers that sit in a corner or a fortgotten shelf in the closet. That's what they're good at and for that they don't need WiFi at all. Desktop performance is generations behind what you can get out of a commodity PC today.

> **mahy said:**
> Well, ok, i'll have to find some other solution. The USB is not a problem for me. I bought a USB expansion card and it 'just works' (NEC chipset); but WEP as a max is a blocker in my case. 

This restriction only applies to the Linksys Gaming Adapter - others might be better here, although I just checked - the Netgear unit has the same restriction. D-Link's [DGL-3420]("http://games.dlink.com/products/?pid=383&#DGL-3420") for instance also supports WPA-PSK. Also [ZyXEL's G-570S]("http://www.zyxel.cz/product/model.php?indexcate=1134532190&indexcate1=1085450343&indexFlagvalue=1021876859") Access Point can be used in "Single PC bridge mode" (WPA, WPA2 etc included). It's a cool and very versatile product anyway, I have tested (admittedly not with Linux) and recommended that one before. Someone even built a wireless hotspot for an open air festival with planar antennas with a handful of these.

> **mahy said:**
> 
However, the biggest problem for me is where to find such things. Here in Slovakia, shops are bursting with USB ADSL modems and Bluetooth gadgets, but this kind of hw is hard to come by.

Well, ZyXEL at least has a HQ in the Czech Republic (see link above) - they at least should be able to help finding out where to buy.

regards

Marc

---

### Post by mahy on 2006-11-09
I'll have to buy some wifi AP able to operate in bridge or client mode. Thanks a lot.

---

