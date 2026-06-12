---
title: "raid systems?"
date: 2009-08-16
forum: Server Platforms
---

### Post by hockey97 on 2009-08-16
Hi, I would like to know more about raid systems.

I want to know if I put  a raid card in my system do I have limits on how many hard drives can connect to that one single card? 

what would I need to get to be able to lets say store about 5,000 hard drives in a cabinet that have like 5 shelfs?

---

### Post by scorp123 on 2009-08-16
> **hockey97 said:**
>  Hi, I would like to know more about raid systems. [http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://en.wikipedia.org/wiki/RAID#Standard_levels](http://en.wikipedia.org/wiki/RAID#Standard_levels)
[http://en.wikipedia.org/wiki/Non-standard_RAID_levels](http://en.wikipedia.org/wiki/Non-standard_RAID_levels)

> **hockey97 said:**
>  I want to know if I put a raid card in my system do I have limits on how many hard drives can connect to that one single card?  I guess that totally depends on the card you buy. A cheapo SATA/RAID controller will probably only support 4 disks max. and at maximum offer various combinations of RAID0, RAID1, RAID0+1 with those four disks.

Professional cards (which usually cost 1000.-- dollars and beyond) can do e.g. RAID5 or RAID6 with 6 disks and more ... But as a home user you're not very likely to find such equipment. You'd be better off with a nice "NAS" solution that you can buy in any smalltown computer shop.

> **hockey97 said:**
>   what would I need to get to be able to lets say store about 5,000 hard drives in a cabinet that have like 5 shelfs? You'd need about 104 pieces of this server:

Sun Fire X4540:
[http://www.sun.com/servers/x64/x4540/index.xml](http://www.sun.com/servers/x64/x4540/index.xml)

[IMG]http://www.sun.com/images/k3/k3_sunfire-x4540_4.jpg[/IMG]

Each X4540 can be equipped with up to 48 disks. In this configuration (48 x 1 TB) each server costs at least 48'000.-- US dollars per piece. So 104 pieces of those would cost you around 5 million dollars.

And as each server consumes between 1200W and 1800W of electrical power you'd probably also need your own small electrical power plant to power them.

And you better have good air conditioning, because 100+ servers will definitely generate a lot of heat :D  (probably you will need a second power plant just to power the air conditioners ...)

---

### Post by hockey97 on 2009-08-16
well, right now I am starting a small company. I just want to know just in case if we grow and grow how to handle the growth. 

If I use a NAS how many can I plug at a time? Just wondering. 

I thought you can simply just stack hard drives on shelfs and connect them someway to the computer. How do huge websites handle extreme data storage?

---

### Post by windependence on 2009-08-17
They use SCSI drives and RAID cabinets. I have a cabinet that holds 12 drives if you need one. I am willing to sell it cheap. 

Very large companies use SANs and they are very expensive. I have run many of these over my career. You would need much other equipment and lots of juice as has been mentioned, but I can't imagine that you would get that big. I run tons of commercial web sites on just one or two arrays. Most sites don't take much space unless you are streaming media.

-Tim

---

### Post by scorp123 on 2009-08-17
> **hockey97 said:**
>  well, right now I am starting a small company. And what would a small company use 5000 harddisks for? Seriously: that sounds like wasting a lot of energy and money on the wrong item.

> **hockey97 said:**
>  I just want to know just in case if we grow and grow how to handle the growth.  Well, as discussed in your other thread: You can use "cloud computing" and buy storage on-line if you need or want to. Especially for start-ups this might be more affordable than running your own infrastructure.

> **hockey97 said:**
>  If I use a NAS how many can I plug at a time? Just wondering.  I have seen NAS drives with (almost) professional features, e.g. they can have up to six disks, they support SAMBA, NFS, FTP and what not, they're basically like small storage servers. But such NAS systems also cost (almost) as much as a good server, e.g. 1000.-- dollars and beyond. But that's still cheaper than 20'000.-- dollars and more that you'd have to pay for a storage server.

> **hockey97 said:**
>  I thought you can simply just stack hard drives on shelfs  Not directly. You still need some kind of casing, e.g. SAN, Fibre Channel, SAS or some other form of storage cabinet that can take loads of harddisks. And then you still need a server somehow with the right adapter cards (SAS, Fibre Channel, Host Bus, ... whatever) to control and coordinate all those disks. As someone already mentioned: Such stuff costs a lot.

> **hockey97 said:**
>  How do huge websites handle extreme data storage? They buy storage servers like the one I already mentioned above. That server offers an excellent "number of harddisks per RU" ratio (e.g. how many disks can you stack in so and so little space) and it's quite "popular" in certain circles. But it is by no means the only storage system out there and certainly not the biggest. HP springs to mind. They have a storage system which fills entire 19" racks from bottom to top with disks, disks and more disks. 
[http://h18000.www1.hp.com/products/storageworks/xp24000/index.html](http://h18000.www1.hp.com/products/storageworks/xp24000/index.html)

But those things are seriously very pricey and only really interesting to large enterprises.

---

### Post by koenn on 2009-08-17
Planning ahead and choosing a scalable solution is a good idea, but in the time it takes  you grow from 'small company' to 'company that needs 5000 harddisks', the stuff you buy now will be obsoleted by new storage technology. 

The way yo do it is to get something today that's extensible enough to cover your needs for the next 5 years, and organize things so that migrations become easy (or at last: manageable) by the time you need upgrading to something larger.

It's probably also a good idea to express your storage needs in (multiples of) bytes, in stead of "number of disks".

---

