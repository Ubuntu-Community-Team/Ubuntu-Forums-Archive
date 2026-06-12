---
title: "15k RPMs of MADNESS!! argh!"
date: 2009-04-06
forum: The Cafe
---

### Post by gtfourdreams on 2009-04-06
I recently picked up a Proliant DL380 G3 to replace a couple older dual p3 servers. holy mother of goodness, this server is LOUD!! i tried to silence it by pulling out two fans which helped a little bit, but geeze the high pitch whine of the 15k 36gb HP drives are intolerable. the whole rackmount is about 3 feet away and i am considering getting a set of full-time ear plugs to kill the noise.

anybody have any tips to silence the drives? it's running on the compaq array 5i plus so hdparm and sdparm won't do anything to it. if I can't quiet these things down, i might downgrade to my old 9.1gb u160 10k rpm drives. those were so much quieter (but still louder than anything else i have around)

maybe someone knows of a cheap way to get my sata drives to work inside this DL380 G3? an adapter perhaps?

---

### Post by mips on 2009-04-06
Put the server in a different location. Store room, garage etc.

---

### Post by gn2 on 2009-04-06
The mose effective means of silencing hard drives that I know of is mechanical de-coupling.
Either use a novibes cage or build your own with bungee cord, or just lay the hard drive on some soft foam.

But as suggested by mips, moving it into a different space where the noise is inaudible is the best bet.

---

### Post by gtfourdreams on 2009-04-06
i was considering moving it. but i really can't. i already drilled holes and ran wires to this location. (wireless will be too slow for the frequent data transfers) it's the most ideal location because it's the most central to my computers and tv/media center.

i dont think there is a no-vibes cage that will work with the Proliant DL380. the drives have to stay in the hot swap tray

[img]http://www.scsi4me.com/images/HP-Tray2.jpg[/img]

maybe its time for the ear plugs.

do you guys think this will work?: [http://www.microcenter.com/single_product_results.phtml?product_id=0266514](http://www.microcenter.com/single_product_results.phtml?product_id=0266514)

---

### Post by blastus on 2009-04-06
This is why I build my PCs for silence. Everything in them is geared towards silence. There's nothing like an annoying noisy computer.

---

### Post by toupeiro on 2009-04-07
lol...

You do realize a DL380 G3 is a rack-mount enterprise server, most commonly to be installed in a data center, or a room typically not occupied for long periods of time by human beings?  Quietness is not what it was designed for...

you can find slower drives, but you are likely not going to get away from the expensive SCSI interface without spending even more money.  You didn't really buy a "put it under your desk" server...  Try selling it and applying it to something quieter..

EDIT: Or.. Sell the drives on Ebay (Ultra320SCSI 15K drives should be able to produce a pretty penny still) with the Smart Array controller and pick yourself up a PCI-X or PCI-E (depending on your backplane) SATA-II controller and a solid state disk or two with the money, you'll probably break even or even still have some money left over.  You obviously don't need the I/O of the 15K drives, so even go with Sata HDD rather than SSD and save yourself even more money.

---

### Post by InfinityCircuit on 2009-04-07
And I thought you were talking about RPM hell...

---

### Post by gn2 on 2009-04-07
> **gtfourdreams said:**
> the drives have to stay in the hot swap tray

Not if they connect with standard connections.
Just get [24" cables]("http://www.ebuyer.com/product/151962") and place them outside the case in a novibes cage, or rest them on foam.

Have you looked at [homeplug powerline network adapters]("http://www.amazon.co.uk/Max-Value-200Mbps-Home-Double/dp/B001AIKBB4/ref=pd_cp_ce_1?pf_rd_p=136153791&pf_rd_s=center-41&pf_rd_t=201&pf_rd_i=B000TV7FJ4&pf_rd_m=A3P5ROKL5A1OLE&pf_rd_r=03HEY5GPTMDATYR9HXRE") to help with relocating it into a loft or a cellar?

Another option might be to use lower rpm bigger capacity drives.

---

### Post by mips on 2009-04-07
Those drives are noisy, period. You will probably get a bit of relief using silicone grommets & a antivibration cage but it won't be much so it's still going to be noisy.

Run new cables and move the server (why does it have to be by your desk? There is no reason) or sell it and get something quieter.

---

### Post by gtfourdreams on 2009-04-07
> **toupeiro said:**
> 
You do realize a DL380 G3 is a rack-mount enterprise server, most commonly to be installed in a data center, or a room typically not occupied for long periods of time by human beings?  Quietness is not what it was designed for...


It really didn't cross my mind. :) You know the story, it was a really good deal and I did a quick research to see if Ubuntu installed on it without hiccups. It was all fine. I didn't think of searching for "Proliant INSANELY loud fans and drives". :lolflag:

> 
EDIT: Or.. Sell the drives on Ebay (Ultra320SCSI 15K drives should be able to produce a pretty penny still) with the Smart Array controller and pick yourself up a PCI-X or PCI-E (depending on your backplane) SATA-II controller and a solid state disk or two with the money, you'll probably break even or even still have some money left over.  You obviously don't need the I/O of the 15K drives, so even go with Sata HDD rather than SSD and save yourself even more money.

i have a couple 500gb sata drives so i am considering that. (using a pci/pci-x sata card and without the hot swap scsi backplane.) the server isn't impossible to get to and i don't think that i would be moving the drives around too often.

> **gn2 said:**
> Not if they connect with standard connections.
Just get [24" cables]("http://www.ebuyer.com/product/151962") and place them outside the case in a novibes cage, or rest them on foam.


my server rack is too pretty to have drives sitting outside. hehe. old pictures here: [img]http://ubuntuforums.org/attachment.php?attachmentid=107534&d=1237945131[/img]
[img]http://ubuntuforums.org/attachment.php?attachmentid=107535&d=1237945162[/img]
That's before the Proliant DL380

I think moving it is out of the question. It's already in the basement and I have no attic or storage room. The laundry room is prone to backing up. (it's an old house) The garage gets -20 in the winter and 100+ in the summer. 

Thanks for all the ideas though. Keep them coming :D

---

### Post by insane_alien on 2009-04-07
so... why don't you move out of the basement? or make a soundproof box around the rack?

---

### Post by gn2 on 2009-04-07
You could suspend the drives inside that big cabinet.
It's no surprise it's loud with the drives bolted into such a big soundbox.

---

### Post by simtaalo on 2009-04-07
> **insane_alien said:**
> make a soundproof box around the rack?

if you can't move it, this is the best idea.

---

### Post by mips on 2009-04-07
> **simtaalo said:**
> if you can't move it, this is the best idea.

I would second that.

---

### Post by gtfourdreams on 2009-04-07
> **insane_alien said:**
> so... why don't you move out of the basement? or make a soundproof box around the rack?

The basement is my home office. Living room, bedrooms and kitchen is above. The basement is fairly clean, nobody really comes down here to bother me, etc. 

How would you guys suggest making a soudproof box? Wouldn't that restrict air flow? Or should I block the front door off and just let the rear bring in the air?

---

### Post by Mehall on 2009-04-07
I'd say there's enough room in the bottom of it you could suspend the HDD's in a novibe-cage inside the rack.

---

