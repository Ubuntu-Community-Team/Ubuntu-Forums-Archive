---
title: "Advice on a SATA PCI Card. Is there many compatibility issues?"
date: 2008-06-02
forum: Server Platforms
---

### Post by garethsimpsonuk on 2008-06-02
I am just about to buy this pci card ( VIA VT6421A ) from ebay
I have searched the forums and google and haven't found much which is surprising as it's an entry level chipset and I'm sure a lot of ppl have picked this as there first card.
Can anyone confirm if this has been fixed for Hardy? I am waiting to buy right now as I've just bought a SATA drive ( my 4 IDE ones seem to all have packed in )and would like them to arrive together but I'm worried about the issues there was a bug filed on Launchpad for Gutsy, I'm just gonna have a look now to see if it was fixed.

edit: should I just find the next expensive chipset just to save any problems?

Cheers guys,

I cant wait to get my server up & running now. I've had to start another project while I'm waiting which has been buying a load of old xboxes, softmodding them & installing XBMC on them.
This software is brilliant and will fit perfectly into my home network, I plan to have 1 in each of the main rooms in my house. They're perfect for a cheap media controller and even have some integration with MythTV, highly recommended, you can get them for 20 quid each.
__________________

---

### Post by garethsimpsonuk on 2008-06-03
bump, bump....bump,bump it up!

---

### Post by amites on 2008-06-03
See if you can find the chipset,

I have one with the Initio chip and it's been giving me a headache,

though it can see it so it is doable with just about any, just a question of how much you want to troubleshoot

---


reread your post:

if I were looking to be buying another SATA controller I would be spending a few extra dollars to save myself a few hours

---

### Post by windependence on 2008-06-04
I'm not sure about that one but I know we have been using 3Ware cards without any issues with various distros.

-Tim

---

### Post by garethsimpsonuk on 2008-06-04
cheers 4 the replies. yea that's the main problem it seems amite. The chipset listed above is probably the cheapest on ebay that doesn't come fromchina. there's also these to choose from:

1. ( this guys doesn't know what a chipset is so he gave me this. i guess it's the Sil1311.. bit ) 

Silicon Image, SATALink, Sil3112ACT144, QC7122.1-3, 0550, 1.21 - I'm pretty sure this maufacturer is linux friendly

2. Promise FastTrak S150TX2

3. This 1 hasn't listed the actual chipset but said this -  

"This product use SATALink Chip, Not VIA Chipset which are selling by other eBay Sellers at very cheap price."

4. This 1 is the most common and cheapest but I know there was issues going from 7.04 to 7.10 - 

VIA VT6421A

That's about all of them really. Now a couple more qusetions..

Is a SATA to IDE converter not as effective as a pci card? I only have 2 pci slots and my nic takes 1. I would like a USB 2.0 card aswell as i only have 1.1.

I've found a pci card with usb 2.0 and ( only 1 ) SATA channel. I may have  USB drives on there will the SATA and USB drives be competing?

If I have a  2 SATA drives and 3 IDE drives am I seriously overlioading my lil box? Will he die sooner? What if I upgrade the PSU?

I seem to buy everything but my smokes off ebay and thats only cos they don't sell them. Will i get superior products at the same price by going to a mainstream seller?

Thanks guys, I've already bought the SATA drive so need to get a card soon!

---

### Post by garethsimpsonuk on 2008-06-04
if no1 can help me is there an in/compatibility list?

---

### Post by amites on 2008-06-06
yup, one of the cheapest there is on ebay

the advantage of a PCI card is speed, the converters are rather slow

haven't heard of a compatibility list for 8.04, would be nice as I'm thinking of replacing the one I have

might be better to start another topic for discussions on the rest of it

(about your lilbox maybe - dunno the specs though if it only has USB 1.1 it's probably fairly old and seeing it's last couple upgrades before it gets unusable, might even want to back it down to an oder version, probably won't kill your box any sooner in a sense that will matter much)

---

### Post by Jesus-Ninja on 2008-06-25
Hello garethsimpsonuk!

Did you ever buy a SATA card for your linux box? I'm also running Hardy, and looking at one of these VIA VT6421A ebay cards so that I can add a 1TB disk.

Would really love to know what your findings are

---

### Post by garethsimpsonuk on 2008-06-26
I've replied to your PM m8. It works great but you can't boot from it ( on my mobo n e way ). Move all your critical partitions to he SATA and just keep them root partition on the IDE / PATA drive. That way you have as much as possible on the faster drive. I still believe it's possible to have the MBR on the IDE drive and to point to the kernel on the SATA ( maybe supergrub could do this? )

Hope this helps and feel free to ask more.

Gareth

---

