---
title: "Other uses for internal notebook wireless card?"
date: 2007-12-08
forum: The Cafe
---

### Post by Tanjer1588 on 2007-12-08
So i have an older but pritty powerful laptop its a 2002 sony vio and the poor little guy up and died on my... the screen dont work and the keys are messed up pritty good but the guts are all in working order so im in the prosesses of salvaging parts from it to attach to my desk top ... kinda like a Frankenstein machine type thing, So i have got converters for both its hard drive and dvd/cd -+r/rw drive cus i really could use that on my desk top, it allso has a built in wireless card that i would like to salvage some how but i cant seem to find any thing on the internet about how to turn it into a usb device or attach it to my desk top. Im really into wireless crap and do a lot of wardriveing and i have another home made USB Cantenna but i would like to use this wire less card in the same way...

So pritty much i just wanna know if any one out there knows what i could do with this wireless card? can i pull it out of there and some how make it unaversal? its a pritty good card

so ya... and if you know anything els i could absorb from the laptop let me know

Thanks all.  
                                                                                          Ubuntu Freak, T

---

### Post by zachtib on 2007-12-08
> **Tanjer1588 said:**
> So i have an older but pritty powerful laptop its a 2002 sony vio and the poor little guy up and died on my... the screen dont work and the keys are messed up pritty good but the guts are all in working order so im in the prosesses of salvaging parts from it to attach to my desk top ... kinda like a Frankenstein machine type thing, So i have got converters for both its hard drive and dvd/cd -+r/rw drive cus i really could use that on my desk top, it allso has a built in wireless card that i would like to salvage some how but i cant seem to find any thing on the internet about how to turn it into a usb device or attach it to my desk top. Im really into wireless crap and do a lot of wardriveing and i have another home made USB Cantenna but i would like to use this wire less card in the same way...

So pritty much i just wanna know if any one out there knows what i could do with this wireless card? can i pull it out of there and some how make it unaversal? its a pritty good card

so ya... and if you know anything els i could absorb from the laptop let me know

Thanks all.  
                                                                                          Ubuntu Freak, T

what chipset is the card?

if it's atheros, you could have some fun with it and BSD...

---

### Post by reidbold on 2007-12-08
If it's built in, the control chips are on the board. It would be ridiculous to salvage it in that case. Unless you are looking for fun with electronic components. 

If it's a plug in card, you can get PCMCIA adapters.

---

### Post by n3tfury on 2007-12-08
if you only used it once i wouldn't have said anything.  it's ***PRETTY***

---

### Post by Tanjer1588 on 2007-12-09
> **zachtib said:**
> what chipset is the card?

if it's atheros, you could have some fun with it and BSD...

how do i find out what kind of chip set it has on it?

---

### Post by mips on 2007-12-09
Can you give us the exact laptop model please ?

I suspect your laptop has a miniPCI wireless card as you said it is INTERNAL but I could be wrong.

If the above is the case then you need a mPCI to PCI adapter card with antenna connectors, something like this:
[http://linitx.com/viewproduct.php?prodid=11082](http://linitx.com/viewproduct.php?prodid=11082)

If it is a card that slots into the PCMCIA/CardBus slot then you need a CardBus to PCI adapter, something like this:
[http://www.compusa.com/products/product_info.asp?product_code=50892079](http://www.compusa.com/products/product_info.asp?product_code=50892079)

Either way it is cheaper to just buy a Wireless PCI card than it is to get an adapter. The economics of going the adapter route just don't make sense.

You could always sell the internal wireless card. Can you give us a closeup picture/photo of the card, both sides ?

---

### Post by Tanjer1588 on 2007-12-09
> **mips said:**
> Can you give us the exact laptop model please ?

I suspect your laptop has a miniPCI wireless card as you said it is INTERNAL but I could be wrong.

If the above is the case then you need a mPCI to PCI adapter card with antenna connectors, something like this:
[http://linitx.com/viewproduct.php?prodid=11082](http://linitx.com/viewproduct.php?prodid=11082)

If it is a card that slots into the PCMCIA/CardBus slot then you need a CardBus to PCI adapter, something like this:
[http://www.compusa.com/products/product_info.asp?product_code=50892079](http://www.compusa.com/products/product_info.asp?product_code=50892079)

Either way it is cheaper to just buy a Wireless PCI card than it is to get an adapter. The economics of going the adapter route just don't make sense.

You could always sell the internal wireless card. Can you give us a closeup picture/photo of the card, both sides ?

The laptops a Sony Vio Model PCG-8M2L the wireless card dose not slide in, its built into the machine i dont know how to get it out :D but i can get a phto of it in there if you like.

---

### Post by mips on 2007-12-09
> **Tanjer1588 said:**
> The laptops a Sony Vio Model PCG-8M2L the wireless card dose not slide in, its built into the machine i dont know how to get it out :D but i can get a phto of it in there if you like.

Yes, please attached a photo of the front and back.

Google is not giving me much.

---

### Post by Tanjer1588 on 2007-12-09
[IMG]http://i15.photobucket.com/albums/a362/tanjer1588/DSC_0066.jpg[/IMG]

[IMG]http://i15.photobucket.com/albums/a362/tanjer1588/DSC_0063.jpg[/IMG]

Thats whats inside there, Mostly i just want to know what i can do with it since im tinkering with every thing from the laptop, i just removed the LCD screen from it, probly going to see what i can do to it, maybe hook it up to something :D

---

### Post by mips on 2007-12-09
Why not use it with a external keyboard/mouse & screen?

You could turn it into a server or a router or something like that. You could even transplant all the working components into a custom case.

If you would like to fix it, which is probably not worth it, [http://www.sparepartswarehouse.com/Sony,Vaio,PCG-GRT,PCG-GRT100,Laptop,Parts.aspx](http://www.sparepartswarehouse.com/Sony,Vaio,PCG-GRT,PCG-GRT100,Laptop,Parts.aspx)

---

### Post by D-EJ915 on 2007-12-09
that's a MiniPCI card

---

### Post by mips on 2007-12-09
> **Tanjer1588 said:**
> 
Thats whats inside there, 

That is a mPCI or Mini PCI card as I though.

I will tell you the chipset soon.

Edit: It is known as a LAN-Express AS IEEE 802.11g miniPCI Adapter or something like that and from what I can tell it uses the Prism chipset. It was made by Ambit Microsystems Corporation

If you plug the card back into the laptop and install a basic linux on it you can id the card 100% by typing **lspci -v** from the cli.

Just something I found, [http://pijulius.blogspot.com/2006/05/cleaning-sony-vaio-pcg-grt100-fan.html](http://pijulius.blogspot.com/2006/05/cleaning-sony-vaio-pcg-grt100-fan.html)

---

### Post by Tanjer1588 on 2007-12-09
ok thank you, ya so how would i move the working parts into there own box? i want to use what i can from it.

---

### Post by Whiffle on 2007-12-09
[http://cgi.ebay.co.uk/Mini-PCI-to-PCI-Adapter-Card-Motherboard-Desktop-PC_W0QQitemZ270194667068QQihZ017QQcategoryZ90719QQcmdZViewItem](http://cgi.ebay.co.uk/Mini-PCI-to-PCI-Adapter-Card-Motherboard-Desktop-PC_W0QQitemZ270194667068QQihZ017QQcategoryZ90719QQcmdZViewItem)

---

### Post by mips on 2007-12-09
> **Tanjer1588 said:**
> ok thank you, ya so how would i move the working parts into there own box? i want to use what i can from it.

Thats the hard part and it's will require some creative thinking on your part. There are sites on the net where people build their own boxes etc.

Just make sure you have 'offsets' for the motherboard so it does not short against anything.

Is the keyboard physically broken or does some keys just not work ? If they are not physically broken it might be worth looking at cleaning all contacts etc with pure alcohol (no you cant drink it as it will kill you) and trying it again. If you know someone thats into electronics they can check out the screen for you as it is usually just the power circuitry that  goes faulty on the panel and it might be repairable for cheap, else check all the connectors and clean them.

Let us know how you go

---

### Post by mips on 2007-12-09
[http://www.macbook-fr.com/ibook/bricolage/recyclage_ibook_dual_article13.html?page=1]("http://www.hardmac.com/news/2006-03-20/#5281")
[http://www.macbook-fr.com/ibook/bricolage/recyclage_ibook_dual_article13.html?page=2]("http://www.powerbook-fr.com/ibook/bricolage/recyclage_ibook_dual_article13.html?page=2l")

Is a example of a Mac transplant.

Best bet would probably be to use plexiglass. You could actually make something really nice if you have the plexiglass professionally cut & edges smoothed. Offsets for the motherboard and other components can be made with little plexiglass pieces with pilot holes for screws to mount things. Drill & dremel tool will allow for exact cutouts for connectors.

Here are some crazy ideas you might want to adapt for a laptop MB and parts,  [http://www.mini-itx.com/projects.asp](http://www.mini-itx.com/projects.asp)

---

### Post by Tanjer1588 on 2007-12-09
cool man thanks, and no none of the keys on the laptop are broken, the video card on it died and the bulb in the LCD screen died along with the dvd rw drive :D and since it was sold old i decided to take it appart. ill see what i can figure out tho, thanks

---

