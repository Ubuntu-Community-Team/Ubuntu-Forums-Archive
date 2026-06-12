---
title: "How would you solve this? [Data server]"
date: 2012-04-12
forum: Server Platforms
---

### Post by Dracheschreck on 2012-04-12
This is not a specific ubuntu question, but I do plan to use ubuntu to solve this, I hope someone with expertise in a similar situation can give some tips:

I have a ton of data (video, ~30TB) in (~15) external USB HDD's. This data has been collected for research for some period of time.

Now we need to set up a server so that people can have access to this data if they need it.

My original plan is to set up a Ubuntu computer, plug in all of the hdd's at the same time, mount them all in the same path and share this via FTP.

People would also be able to ssh in and work with the data directly in the server.

So.. I have no specific questions, but if you read this and you cringe for one reason or another, please let me know before I fail! One of the things I dislike is plugging a lot of USB drives. Maybe I should remove the cases from those drives and use them internally, or set up a RAID... 

what do you think? thanks in advance for any tips!

---

### Post by rubylaser on 2012-04-12
Do you have any form of backup / redundancy?  If anyone of these disks failed, you're going to lose everything on the disk otherwise. Is this shared on the LAN and not on a WAN?  I ask, because USB drives are not exactly the speediest transfer mechanism.

Personally, I would build a server for this data with redundancy (but that would be costly for a server and a matching set of disks), and use the USB drives as backups to get you started.  If the users are on the LAN, I'd have them mount the share(s) via NFS.

Converting to RAID would require wiping these disks out first if you wanted to use them in the array, so that's not really an option unless you want to buy new disks.

---

### Post by Dracheschreck on 2012-04-12
Having redundancy is an important thing for us. We have some budget to do stuff.

We could buy HDD's for 30TB, copy everything there, share from there, keep the USB disks as backup, in case something fails.

Having real, online redundancy would be doubling the budget of HDD's, I don't think we could afford that.

Still, what options are available to connect so many HDD's (~15) to a single motherboard? Do you have any experience on this?

Thanks for the tips. Mounting the shares looks like a better solution than FTP, since we could work with the data from any program.

---

### Post by Jonathan L on 2012-04-12
Hi Dracheschreck

Given what you've said, I'm guessing:

[LIST]
[*]If you've been collecting them for some time they are probably valuable in some way.
[*]it's a low demand service: a few other people might access a video periodically
[*]Budget is tight
[/LIST]

There's nothing wrong with what you've said, really, if you've got some simle requirement to make the data available for occasional transfer.  The main thing is that a pile of USB disks in a drawer will last indefinitely.  If you have them plugged in and switched on, the life expectancy is probably a year or three.

So, you might considered getting new disks at the highest density you can.
Or have it all working and configured, but only plug in the particular disks on demand (if that's not patently ridiculous)
Depending on application, you might even consider having everything plugged in, but only switch on a given disk on demand, with some relays etc. (if not even more ridiciulous!)

If the individual files are large (over 100 Gbyte, say) you'll get benefit from RAID simply for packing size.  (That is, you won't have lots of disks with 90 Gbyte wasted space, because it's aggregated across the RAID set.) But in general I'm not a huge recommender of RAID unless you get a specific benefit you need: in your case, RAID0 gives you simplicity of setup but might be tricky when you outgrow it (no redundancy, just makes a big logical filesystem from smaller disks).  Higher RAID levels will increase the required amount of raw disk space, and are probably not what you want.

Have you considered the file layout and whether the mounts are read only?  I'm guessing you might get mileage out of a scheme like this:
```
 /disk/1/video1.mpg
 /disk/1/video2.mpg
 ...
 /disk/15/video900.mpg

Then a big box of symlinks:
 /disk/data/video1.mpg -> ../1/video1.mpg
 ...
 /disk/data/video900.mpg -> ../15/video900.mpg

```If you organise the files in a sensible way, you'll give yourself a lot of space for when you need to move the physical parts around.  I've organised some file servers of this scale like that and it works surprisingly well, once you get your helper scripts sorted out.

On the subject of access, are you sure you want FTP?  Have you  considered ssh (if you need authentication) or just old http (if you  don't).  I was so happy when I stopped having to lock up FTP servers.  You say people will log in over ssh (so you'll have that already) ... what kind of work will they do?  My line of thinking is this: 30TB of data online, how do we deal with accidental deletion, corruption etc.

Hope that's of some use.  Tell us a bit more about your parameters and let us know your current thinking.

Kind regards,
Jonathan.

---

### Post by CharlesA on 2012-04-12
> **Dracheschreck said:**
> Having redundancy is an important thing for us. We have some budget to do stuff.

We could buy HDD's for 30TB, copy everything there, share from there, keep the USB disks as backup, in case something fails.

This would be the best way to do it imho. If you do decide to go with RAID, go with RAID6 so it can handle the failure of two disks.

When I originally had my home "server" I was running off an XP box and sharing a USB drive. It was slow as hell and quite a pain. Now I've got everything on an internal RAID array and backing it up to USB drives.

Sidenote: It might be a good idea to go with 2TB drives, but you would still need 17 drives in order to get around 30TB of space. 15 drives for the array and 2 drives for parity to recover data in case a drive goes out.

EDIT: You might be better off with 3TB drives, as you would only need 12 drives total.

See here too:
[http://www.raid-calculator.com/Default.aspx](http://www.raid-calculator.com/Default.aspx)

---

### Post by Dracheschreck on 2012-04-12
Thanks for taking the time to reply!

You are right in the 3 assumptions, this data is valuable, access will be only once in a while, and we are on a tight budget.

Files are not too big, so RAID would only complicate things IMO.

I still have a big doubt: the actual hardware problems:

- A nice case to fit everything?
- How to plug in so many SATA drives?

---

### Post by Jonathan L on 2012-04-12
Hi Dracheschreck

I've commited various crimes with "loose disks" on rack shelving and I don't really recommend it.  A quick browse found 4-bay SATA drive docks which look good (says tried with four 4TB disks) in the US $200 range:

[http://intrl.startech.com/HDD/Docking/4-Bay-eSATA-USB-3-to-SATA-Hard-Drive-Docking-Station-for-25-35-HDD~SATDOCK4U3E]("http://intrl.startech.com/HDD/Docking/4-Bay-eSATA-USB-3-to-SATA-Hard-Drive-Docking-Station-for-25-35-HDD%7ESATDOCK4U3E")

I like the idea of buy just the raw disks and plugging them in.  It certainly solves the problem of a dozen USBs.  I'd do it with a nice 1-U server and some of these sitting on top of it, but depends on your physical environment.   That company seems to make various convenient disk chasses, I'm sure you'll find something from them or a competitor which will suit you.

I think the best part about this is you'd be able to spend only a few hundred and test everything out before investing in the real disks and the time to copy everything around.

Not tried these, mind, nor have any association with them.

Kind regards,
Jonathan.

---

### Post by CharlesA on 2012-04-12
I've seen some nice tower cases that are able to handle 10-15 drives.

Enterprise grade stuff should be able to handle that but it would be expensive.

As for finding enough SATA ports, have you thought of getting a PCI-e SATA card?

This all depends on if you are going to be using RAID or just sticking with using USB.

---

### Post by CharlesA on 2012-04-12
I've seen some nice tower cases that are able to handle 10-15 drives.

Enterprise grade stuff should be able to handle that but it would be expensive.

As for finding enough SATA ports, have you thought of getting a PCI-e SATA card?

This all depends on if you are going to be using RAID or just sticking with using USB.

---

### Post by SeijiSensei on 2012-04-12
For comparison purposes, here's what a Linux-based commercial 30 TB NAS solution would look like:

[http://www.aberdeeninc.com/abcatg/NAS854LX.htm](http://www.aberdeeninc.com/abcatg/NAS854LX.htm)

It costs about $16K.

---

### Post by CharlesA on 2012-04-12
Cripes! I thought the 6TB NAS I've got at work was impressive.

---

### Post by rubylaser on 2012-04-12
If you want a case capable of holding a lot of hard drives, it's pretty difficult to beat the  [Norco 4220]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811219021").  If you just want to run the disks as JBOD, then you'll still need some HBA's.  I'd suggest 3 [IBM m1015]("http://www.ebay.com/sch/i.html?_from=R40&_trksid=p5197.m570.l1313&_nkw=m1015&_sacat=See-All-Categories")'s as they'll support ( 8 ) hard drives over 2TB each.

Then, you'll need a motherboard with (3) PCI-Express x8 slots to accomodate the cards.  These [Supermicro boards]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813182253") are great coupled with a Xeon E3-1230 and 16GB of RAM.

I'd still be building this solution on top of a redundant setup (RAID6 as CharlesA suggested), unless having a large chunk of your data down for hours in the case of a failed drive is not an issue.

---

### Post by CharlesA on 2012-04-12
> **rubylaser said:**
> If you want a case capable of holding a lot of hard drives, it's pretty difficult to beat the  [Norco 4220]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811219021").

*whistles* I think the best part of that one is this:

"Smooth border prevent lacerating your skin" :KS

> I'd still be building this solution on top of a redundant setup (RAID6 as CharlesA suggested), unless having a large chunk of your data down for hours in the case of a failed drive is not an issue.

Aye. When you get into arrays that large, it'll take a long time for the array to rebuild. I'd rather go with the RAID-6 + backups solution myself, but that is not taking a budget into account.

---

### Post by Jonathan L on 2012-04-13
Hi Dracheschreck

It's a big and pretty complex topic, but the RAID or not question is one of the first to sort out.  My experience of the matter is that is really depends on how much downtime hurts you.  My assumption from the description of the problem is that downtime is not very problematic (they haven't had this video online before anyways) and "some video unavailable" would be acceptable.

Let's say you have a (pretty bad) replacement rate of 10% pa: one disk per year, including growth.

Then choose which of the following two tasks you want to do:

1.  Buy a new disk, format it, mount it on /dev/disk/nnn, copy a read-only USB disk to it, and run a script to make symlinks
2.  Buy a new disk, join to a RAID set, and rebuild a live RAID set of 10s of TB.

If you do these things frequently and are familiar with the equipment, number 2 is definitely easier.  If you only do it once a year, 1 is trivial, 2 requires thinking and time.  Number 1 is a fantastically ordinary process, amongst the most tested of all the functions of the operating system; number 2 is a relatively rare process with software written by who exactly?  Was it Adaptec or JetStore, whose whole business is things like this, or someone else?  Frankly, the provenance of firmware can be frightening, even for large companies.

Just my experience of managing people running multi-terabyte RAID systems: they worried about those rebuild processes and took a lot of care and time getting them right.  The screens for "initialise whole raid set" are often shockingly close to "initialise drive and rebuild whole raid set".  Additionally, the management of the RAID sets in multiples of 5 (or whatever) matched-size disks is much bigger grain size than it looks, and they spent a lot of time juggling when drive capacities changed (eg 250GB -> 500 -> 1TByte and so on.)

So, in this case, I'd seriously consider running without RAID, with a file layout like I suggested earlier.

Data about disk failure rates in the field:  [http://static.usenix.org/events/fast07/tech/schroeder.html](http://static.usenix.org/events/fast07/tech/schroeder.html) which says "in the field, annual disk replacement rates typically exceed 1%, with 2-4% common and up to 13% observed on some systems. This suggests that field re-placement is a fairly different process than one might predict based on datasheet MTTF".

Hope that's of some help thinking about your preferred solution.

Kind regards,
Jonathan.


PS.  Interesting article about building something like this with FreeNAS software, which made me think of a semi-networked solution by aggregating a pile of NASes through a single Ubuntu server.  Not what I'd do for 30Tbyte, maybe what I'd do for 100.  [http://www.bit-tech.net/hardware/storage/2010/07/23/how-to-build-a-nas-box/1](http://www.bit-tech.net/hardware/storage/2010/07/23/how-to-build-a-nas-box/1)

---

### Post by Dracheschreck on 2012-04-17
Thank you VERY much for your replies! :KS

The case looks like a great deal! 

I've certainly decided on not using a RAID, specially since I'll probably not be in charge for this system a couple of months from now, it should be easy to administrate. Having the files in separate disks but using symlinks will be great for the users and little effort for the administrators.

I have some more questions:
Is it worth it using a Xeon instead of a desktop i7 CPU & mobo?

Any tips for the PSU? I don't need a redundant PSU (downtime is irrelevant). Should I just go for a powerful desktop PSU or is that not going to fit in a 4U case?

As for the connection to the hard disks: Any brand recommendations for the PCI-E cards I'll need to get to plug them all in?
Edit: Those IBM m1015 cards seem RAID cards, right? I Believe I just need more SATA ports, which should be cheaper. Please let me know if I'm wrong.
EDIT: [3x of this card seem like a good choice.]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815121009")
EDIT2: The OS compatibility seems a bit strict, I planned to use Ubuntu for the server, but I guess that is not too important.

Thanks again!

PS: [Parts list]("https://docs.google.com/spreadsheet/pub?key=0AisioMl_rX7VdG4xU2xka2lxUjYzY1djWmducGJnSnc&output=html")

---

### Post by Dracheschreck on 2012-04-17
Ew, turns out that PCI-X doesn't stand for PCI-express!
Guess I'll need to find another card for more SATA ports.

---

### Post by rubylaser on 2012-04-17
> **Dracheschreck said:**
> Thank you VERY much for your replies! :KS

The case looks like a great deal! 

I've certainly decided on not using a RAID, specially since I'll probably not be in charge for this system a couple of months from now, it should be easy to administrate. Having the files in separate disks but using symlinks will be great for the users and little effort for the administrators.

I have some more questions:
Is it worth it using a Xeon instead of a desktop i7 CPU & mobo?

Any tips for the PSU? I don't need a redundant PSU (downtime is irrelevant). Should I just go for a powerful desktop PSU or is that not going to fit in a 4U case?

As for the connection to the hard disks: Any brand recommendations for the PCI-E cards I'll need to get to plug them all in?
Edit: Those IBM m1015 cards seem RAID cards, right? I Believe I just need more SATA ports, which should be cheaper. Please let me know if I'm wrong.
EDIT: [3x of this card seem like a good choice.]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815121009")
EDIT2: The OS compatibility seems a bit strict, I planned to use Ubuntu for the server, but I guess that is not too important.

Thanks again!

PS: [Parts list]("https://docs.google.com/spreadsheet/pub?key=0AisioMl_rX7VdG4xU2xka2lxUjYzY1djWmducGJnSnc&output=html")

The IBM m1015 cards support RAID0/1 out of the box, but it is a very popular thing to flash them with [LSI IT firmware]("http://www.servethehome.com/ibm-serveraid-m1015-part-4/") to just use them as HBA's that support SATAIII drives and drives over 2TB in size.  This is what I've done with mine at home. These can be had on eBay from [60-80 bucks each]("http://www.ebay.com/itm/IBM-ServeRAID-M1015-SAS-RAID-Controller-FRU-46M0861-LSI-PN-SAS9220-8i-/190667696948?pt=COMP_EN_Networking_Components&hash=item2c64ae2b34").

The [IBM BR10i]("http://www.ebay.com/itm/IBM-ServeRAID-BR10i-SAS-RAID-Controller-44E8690-44E8689-LSI-PN-SAS3082E-R-B-/310388908024?pt=COMP_EN_Networking_Components&hash=item48449edff8")'s can be flashed as well and are around 30 dollars each on eBay and still support up to 8 hard drives, but they're just SATAII and support hard drives up to 2TB in size.

I have one of those Supermicro PCI-X cards in my old fileserver, but that's definitely not what you're looking for here, plus it's more expensive than either of the two IBM cards I mentioned.

---

### Post by rubylaser on 2012-04-17
If you go with the Norco case, do yourself a favor and get the [120mm fan bracket]("http://www.ipcdirect.net/servlet/Detail?no=258") if you have that server anywhere near people as it's 80mm fans are REALLY loud (You'd need to get 3 120mm along with this bracket). [This]("http://www.servethehome.com/120mm-fan-partition-norco-rpc4220-rpc4020/") demonstrates what I'm talking about.

In regards to a PSU, you'd just want a unit that supports around 60A on one rail.  Something like [this ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817139011&nm_mc=AFC-C8Junction&cm_mmc=AFC-C8Junction-_-na-_-na-_-na&AID=10440897&PID=3891137&SID=rewrite")would be great.

Hope that helps.  If you have any more questions, fire away :)

---

### Post by MakOwner on 2012-04-18
I'm using three of these things right now - up to 8 hot swap SATA disks in an eSATA enclosure, and you can do JBOD or software raid.

They have SAS models available now, but I'm using the 3 and 6 GB eSATA enclosures.

With the latest models of the enclosures they started shipping Highpoint controller cards which is a real disappointment, but you can get a 4 port PCIe eSATA card compatible with port multipliers for less than $200 these days.

[http://www.sansdigital.com/towerraid/index.php](http://www.sansdigital.com/towerraid/index.php)

I have one attached to a Dell PE 2950 with 2TB Seagate drives - I just stuck the generic SIL chipset card that came with the enclosure into the PCIe slot and with 10.04 LTS minimal install and mdadm I have it set up in RAID5.
Another one is attached to a Dell PE 850 with 1.5 TB drives.

Third one is being prepped to go alongside the one attached to the PE 850.


If you go JBOD and just mount the disks individually, as everyone else here has said be careful about disk failures.  A previously formatted drive that will mount on linux via USB will easily mount in one of these - I have done that.  

If you elect to use software raid, do be careful of a couple of things - rebuild time on a failed 2TB drive can be ... well, I keep spares on the shelf.  I would have gone RAID 6 but I needed the space.  I'm currently running with less than 2TB free on the enclosure with the 2TB disks.
Also, the default installation of mdadm will configure an array consistency check on th first Sunday of the month.Watch for it the first time and you can adjust your behavior accordingly.

disclaimer - I'm not connected with the company in any way.  The performance is not going to win you any awards, but for the cost it easily satisfies low demand applications.

---

### Post by Gyokuro on 2012-04-18
Looking at the amount of data you have to keep stored I think maybe you should look at some equipment from EMC ([http://www.emc.com/backup-and-recovery/data-domain/data-domain.htm#!hardware](http://www.emc.com/backup-and-recovery/data-domain/data-domain.htm#!hardware)), EMC Data Domain DD160, depends whether your are on tight budget or not. Otherwise Netapp gear should be fine too or storage solutions from HP.

---

### Post by Jonathan L on 2012-04-18
Hi again Dracheschreck

> PS: [Parts list]("https://docs.google.com/spreadsheet/pub?key=0AisioMl_rX7VdG4xU2xka2lxUjYzY1djWmducGJnSnc&output=html")

You're getting an awful lot of bang for those bucks!  Please keep us filled in with progress.

Kind regards,
Jonathan.

---

### Post by Dracheschreck on 2012-04-18
I'm definitely going the frugal way, so my setup is going to be all internal (no external towers)

_**Controller cards:**_

The m1015's look like a solid bet, with a good pricetag for the capabilities/brand.

Probably I would only need two of them, since the mobo has 6 sata ports. (15 disks + 2 OS disks < 2*8 + 6)

--They seem very tailored for IBM servers, **Are the m1015's going to be a pain to install in that mobo, with a normal OS?**

--What do you think about [this card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816117157")? It's cheaper than the m1015 (retail price), **is there any reason to stick to the m1015 instead of the SASUC8I ?**


**To rubylaser** (or any other who has used the NORCO RPC-4020):
 How do you connect the hard disks to the controllers? Do the backplanes of the case have a SAS connector which then goes to 4 drives each, or do i need to breakout SAS->SATA myself with a cable? How about power to the disks? is it also individual or is there a power rail in the case?

Thanks!!!

---

### Post by rubylaser on 2012-04-18
> **Dracheschreck said:**
> I'm definitely going the frugal way, so my setup is going to be all internal (no external towers)

_**Controller cards:**_

The m1015's look like a solid bet, with a good pricetag for the capabilities/brand.

Probably I would only need two of them, since the mobo has 6 sata ports. (15 disks + 2 OS disks < 2*8 + 6)

--They seem very tailored for IBM servers, **Are the m1015's going to be a pain to install in that mobo, with a normal OS?**

--What do you think about [this card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816117157")? It's cheaper than the m1015 (retail price), **is there any reason to stick to the m1015 instead of the SASUC8I ?**


**To rubylaser** (or any other who has used the NORCO RPC-4020):
 How do you connect the hard disks to the controllers? Do the backplanes of the case have a SAS connector which then goes to 4 drives each, or do i need to breakout SAS->SATA myself with a cable? How about power to the disks? is it also individual or is there a power rail in the case?

Thanks!!!

I can't get Newegg to load for me right now, so I'm not sure what card you linked to.  But, I'd still buy the IBM m1015 off of eBay.  They're almost all new pulls from IBM servers that people are upgrading to fancier hardware RAID cards.  If you flash them with the IT firmware that I linked to earlier, they work great in Windows, Linux, or Solaris without a problem.  It will be recognized as an LSI card in Linux, and work great out of the box.  Here's how mine looks in my fileserver. 

```
root@fileserver:~# lspci | grep LSI
01:00.0 Serial Attached SCSI controller: LSI Logic / Symbios Logic SAS2008 PCI-Express Fusion-MPT SAS-2 [Falcon] (rev 03)
```

The Norco 4220 has 5 backplanes that control 4 drives each.  Each backplane has a single SF8087 Mini SAS connector and 2 ea. molex 4-pin power connectors (redundant).  If you bought 2 IBM m1015's you'd need to connect them to the Norco backplane with a [Norco C-SFF8087-D SFF-8087 to SFF-8087 Multilane SAS Cable]("http://www.tkqlhce.com/click-3891137-10440897?SID=rewrite&url=http%3A%2F%2Fwww.newegg.com%2FProduct%2FProduct.aspx%3FItem%3DN82E16816133034").

Each SFF-8087 port in the Norco 4220 or 4224 cases's storage backplane provides a data connection for 4 hard drives each. The Norco 4220 and 4224 have 5 and 6 SFF-8087 ports respectively which means 20 and 24 drives respectively. So you would need 6 of those SFF-8087 to SFF-8087 cables to connect all 24 drives. Personally, I'd get (3) IBM m1015 cards and not fiddle with your onboard SATA ports, but that's just me. Or, you could go with 1 IBM m1015 plus an [HP SAS expander]("http://www.amazon.com/gp/product/B0025ZQ16K?ie=UTF8&tag=servecom-20&linkCode=as2&camp=1789&creative=390957&creativeASIN=B0025ZQ16K"). This would be more expensive than the (3) eBay m1015's, but it is another option if you don't like the idea of (3) cards.

---

### Post by rubylaser on 2012-04-18
Newegg finally loaded for me.  The Intel SASUC8I is the more expensive version of the [IBM BR10i]("http://www.servethehome.com/ibm-serveraid-br10i-lsi-sas3082e-r-pciexpress-sas-raid-controller/") that I posted earlier.  I'd personally buy the m1015 first and the BR10i second based on their availability and cost via eBay.

---

### Post by CharlesA on 2012-04-18
They linked to:

Intel RAID Controller Card SATA/SAS PCI-E x8 8internal ports (SASUC8iI)

EDIT: Ignore me. ;)

---

### Post by vpadro on 2012-04-19
Try to use Dell Perc 5/i or 6/i they're pretty cheap this days and are very compatible/fuctional under every linux distro including Ubuntu.

[http://bit.ly/I1vV9h](http://bit.ly/I1vV9h)
[http://bit.ly/I1wm3k](http://bit.ly/I1wm3k)

cables(my guess):
[http://bit.ly/I1wwb5](http://bit.ly/I1wwb5)

Right now we're using a couple 5/i on RAID5 for a year without any downtime or loss.

Good luck.

---

### Post by rubylaser on 2012-04-19
> **vpadro said:**
> Try to use Dell Perc 5/i or 6/i they're pretty cheap this days and are very compatible/fuctional under every linux distro including Ubuntu.

[http://bit.ly/I1vV9h](http://bit.ly/I1vV9h)
[http://bit.ly/I1wm3k](http://bit.ly/I1wm3k)

cables(my guess):
[http://bit.ly/I1wwb5](http://bit.ly/I1wwb5)

Right now we're using a couple 5/i on RAID5 for a year without any downtime or loss.

Good luck.

The OP mentioned that he doesn't want to do RAID so this rules out the Perc 5i or 6i. To use either of these as JBOD disks you have to configure each drive as a single-disk RAID 0.  This is not as transparent as passing the disks directly through like a card running in IT mode.

Plus, even the newer Perc 6i doesn't support drives larger than 2TB, so moving to larger disks in the future won't work with these controllers.  Also, they need a fan on them (or a bigger heatsink) or they will overheat.  They are good cards, but I don't see them as a great fit for this use case.

---

### Post by vpadro on 2012-04-19
> **rubylaser said:**
> The OP mentioned that he doesn't want to do RAID so this rules out the Perc 5i or 6i. To use either of these as JBOD disks you have to configure each drive as a single-disk RAID 0.  This is not as transparent as passing the disks directly through like a card running in IT mode.

Plus, even the newer Perc 6i doesn't support drives larger than 2TB, so moving to larger disks in the future won't work with these controllers.  Also, they need a fan on them (or a bigger heatsink) or they will overheat.  They are good cards, but I don't see them as a great fit for this use case.

The question will be, is this Data valuable or not? If is not, well disregard this and my last reply, if it is then the OP needs any kind of RAID I've seen many but many JBODs and RAID0 gone in less than a beagle bark so I hope he can reconsider planning this again, like I said if it's valuable Data.

About the Perc 6/i I'm sorry, but you might be mistaken Dell Percs do support 2TB Disks(SAMSUNG EcoGreen F4 HD204UI - what the OP mentioned in this [list]("https://docs.google.com/spreadsheet/pub?key=0AisioMl_rX7VdG4xU2xka2lxUjYzY1djWmducGJnSnc&output=html")) what I've only seen is that you have to create RAID Volumes under 2TB in VMware ESXi but this is not that scenario so if you are talking about 3TB drives, which is not the case because the OP disregarded them AFAIK, well your right. :) 

That NORCO has plenty airflow for what I've seen is very similar to Dell's R905 and if you are going to use a couple of Perc 6's controllers well they're going to be at home.

Also I would reconsider buying a smaller HD for the OS beacause it's just a waste of space(500GB) if it's only going to be deployed as a File Server: [http://bit.ly/HUgIWo](http://bit.ly/HUgIWo)

Why not use [FreeNAS]("http://bit.ly/J9OdXW") or [Openmedia Vault]("http://bit.ly/J9N9U4") and use a USB Key to load any of them?

If I'm not going to take care of that in the near future I'd leave the Backup server' SW as easy as can be and FreeNAS and Openmedia Vault are easy to deploy. But that's just me a cranky nerdy guy who don't like to lost data and to be yelled by the long suits.


Best of luck!

---

### Post by rubylaser on 2012-04-19
> **vpadro said:**
> The question will be, is this Data valuable or not? If is not, well disregard this and my last reply, if it is then the OP needs any kind of RAID I've seen many but many JBODs and RAID0 gone in less than a beagle bark so I hope he can reconsider planning this again, like I said if it's valuable Data.

About the Perc 6/i I'm sorry, but you might be mistaken Dell Percs do support 2TB Disks(SAMSUNG EcoGreen F4 HD204UI - what the OP mentioned in this [list]("https://docs.google.com/spreadsheet/pub?key=0AisioMl_rX7VdG4xU2xka2lxUjYzY1djWmducGJnSnc&output=html")) what I've only seen is that you have to create RAID Volumes under 2TB in VMware ESXi but this is not that scenario so if you are talking about 3TB drives, which is not the case because the OP disregarded them AFAIK, well your right. :) 

That NORCO has plenty airflow for what I've seen is very similar to Dell's R905 and if you are going to use a couple of Perc 6's controllers well they're going to be at home.

Also I would reconsider buying a smaller HD for the OS beacause it's just a waste of space(500GB) if it's only going to be deployed as a File Server: [http://bit.ly/HUgIWo](http://bit.ly/HUgIWo)

Why not use [FreeNAS]("http://bit.ly/J9OdXW") or [Openmedia Vault]("http://bit.ly/J9N9U4") and use a USB Key to load any of them?

If I'm not going to take care of that in the near future I'd leave the Backup server' SW as easy as can be and FreeNAS and Openmedia Vault are easy to deploy. But that's just me a cranky nerdy guy who don't like to lost data and to be yelled by the long suits.


Best of luck!

I said disks greater than 2TB if he ever wanted to expand in the future. Many users including me had suggested building a RAID array, but the OP has stated many times that there will be a backup and he does not want RAID in any way.

Personally, I'd be building this with Openindiana and ZFS as it's checksumming and COW really protect my data.  With the hardware mentioned in this thread, it could be VERY fast with two 12 disk raidz2 vdevs.

---

### Post by CharlesA on 2012-04-19
> **rubylaser said:**
> I said disks greater than 2TB if he ever wanted to expand in the future. Many users including me had suggested building a RAID array, but the OP has stated many times that there will be a backup and he does not want RAID in any way.

Personally, I'd be building this with Openindiana and ZFS as it's checksumming and COW really protect my data.  With the hardware mentioned in this thread, it could be VERY fast with two 12 disk raidz2 vdevs.
I don't have any experience with Openindiana or ZFS, but I know ZFS is really good for massive amounts of data.

I still think RAID would be way better then running JBOD and hoping it's ok.

---

### Post by rubylaser on 2012-04-19
> **CharlesA said:**
> I don't have any experience with Openindiana or ZFS, but I know ZFS is really good for massive amounts of data.

I still think RAID would be way better then running JBOD and hoping it's ok.

RAID would be a better solution (both in terms of fault tolerance and throughput).

A hardware RAID card (Perc 6i as suggested) with a SAS expander would also be another good solution if you wanted a cheaper hardware RAID solution. But, I'm always leery with more than 10-12 disks with only 2 parity disks.  A 24 disk RAID6 array would scare the crap out of me during a rebuild :)  That's why I mentioned the two 12 disk raidz2 (like RAID6) vdevs or an even more fault tolerant option with greater IOPS would be three 8 disk raidz2 vdevs.

---

### Post by CharlesA on 2012-04-19
So basically you would have two 12 disk raidz2 arrays instead of one 24 disk array?

---

### Post by rubylaser on 2012-04-19
> **CharlesA said:**
> So basically you would have two 12 disk raidz2 arrays instead of one 24 disk array?

No, but I like your question :) ZFS is different that traditional raid with their separate filesystems. [This is]("http://hub.opensolaris.org/bin/download/Community+Group+zfs/docs/zfslast.pdf") a quick, interesting read if you've never looked into ZFS compared with traditional RAID + filesystem.  A ZFS volume is called a pool.  Pools are made up of any number of vdevs (virtual devices).  These vdevs can contain single disks, mirrors, or groups of disks in raidz(1/2/3).

These vdevs are striped together, so in the example I provided, you'd have 1 pool that you'd interact with made up of 24 disks. 4 of those disks would be used for parity in that example.  You can add as many vdevs to a pool as you'd like, but it's a good practice to make the vdevs that you add be a similar arrangement, so that each of your vdevs perform that same and have the same fault tolerance, so you don't have a weak link in you're setup.  Here's a good [explanation]("http://constantin.glez.de/blog/2010/06/closer-look-zfs-vdevs-and-performance") of vdevs if I failed explaining well enough.

---

### Post by CharlesA on 2012-04-20
Wow, that is pretty damn cool.

Thanks for the info!

---

### Post by Jonathan L on 2012-04-20
Hi All

Re RAID, again:

[QUOTE=CharlesA]RAID would be way better then running JBOD and hoping it's ok.[/QUOTE]

The alternative to RAID is not "and hope", the alternative is "know what to do when the failure happens."  

Categorically, _RAID does not prevent disk failures_;  it protects uptime by automating the reaction to the failed disk, at the cost of addition complexity and frankly very challenging testing procedures.  

As such, you are making a bet about what kinds of failures you're likely to have, and organising your system's response to those (ie, by choosing how many parity disks etc.)  Typically, for large data sets, the input disks are simply regarded as transport media, and as full backups are very expensive to make,  frequently they don't exist.  Thus the data is sitting on disks which are powered up and spinning, in a single computer with a single OS and operators.  The entirety of the data is therefore simultaneously vulnerable to, for example, PSU overspike destruction, OS bugs, operator oops.   Obviously some of those risks are pretty low; operator error and OS (including firmware) bugs are non-trivial though.

The alternative is JBOD, with the original disks powered down in a drawer, preferably off-site.  When the disk failure happens, you buy another, possibly different sized one, and rebuild that section.  With good planning this is a simple task, bounded by the size of the unit.  A 1 TByte disk copy is a lunch break, a 10 TByte array rebuild is something you monitor over quite a while, typically fretfully, and juggling RAID sets over a long time period can be extremely time-consuming.

Obviously you could do both: build a big RAID box, fill it, and still keep the original disks in a drawer.  But then you've done all this work of building the RAID system for how much benefit?

Just to speak about RAID testing for a moment.  You get the box, you build the RAID sets and then you experiment.  You pull something out hot or mark something as broken, and then watch it rebuild, slowly.  You tell yourself you're satisfied with the testing.  In three years time when your data has doubled in size and you are growing the sets, will you do this again with the hot data?  Or will you make a full backup and then do the experiments?  Or will, somehow, the testing become less rigorous when the time involved becomes apparent and immediate?

May I suggest that those who are trying to convince Dracheschreck to change his mind about RAID, despite him being clear about it: 1) advocate a specific kind of RAID level and organisation, 2) describe the actual benefits and 3) address the points about the work of the rebuild and the complexity of the setup.

My point, simply, is that when proposing RAID (for redunancy) we have to think about the net cost/benefit in time, configuration, testing as well as the simple benefit in performance and uptime, both of which have been explicity discounted by Dracheschreck.  Merely repeating that you need it is unhelpful.

I write as someone who has seen enormous data loss, both with and without RAID.  The single distinguishing characteristic that makes your data survive is organisation, a plan, and testing.

Kind regards to all.
Jonathan.

PS.  Of course we're speaking about the RAID levels which redundancy, not the simple performance and size levels.

---

### Post by rubylaser on 2012-04-20
> **Jonathan L said:**
> Hi All

Re RAID, again:



The alternative to RAID is not "and hope", the alternative is "know what to do when the failure happens."  

Categorically, _RAID does not prevent disk failures_;  it protects uptime by automating the reaction to the failed disk, at the cost of addition complexity and frankly very challenging testing procedures.  

As such, you are making a bet about what kinds of failures you're likely to have, and organising your system's response to those (ie, by choosing how many parity disks etc.)  Typically, for large data sets, the input disks are simply regarded as transport media, and as full backups are very expensive to make,  frequently they don't exist.  Thus the data is sitting on disks which are powered up and spinning, in a single computer with a single OS and operators.  The entirety of the data is therefore simultaneously vulnerable to, for example, PSU overspike destruction, OS bugs, operator oops.   Obviously some of those risks are pretty low; operator error and OS (including firmware) bugs are non-trivial though.

The alternative is JBOD, with the original disks powered down in a drawer, preferably off-site.  When the disk failure happens, you buy another, possibly different sized one, and rebuild that section.  With good planning this is a simple task, bounded by the size of the unit.  A 1 TByte disk copy is a lunch break, a 10 TByte array rebuild is something you monitor over quite a while, typically fretfully, and juggling RAID sets over a long time period can be extremely time-consuming.

Obviously you could do both: build a big RAID box, fill it, and still keep the original disks in a drawer.  But then you've done all this work of building the RAID system for how much benefit?

Just to speak about RAID testing for a moment.  You get the box, you build the RAID sets and then you experiment.  You pull something out hot or mark something as broken, and then watch it rebuild, slowly.  You tell yourself you're satisfied with the testing.  In three years time when your data has doubled in size and you are growing the sets, will you do this again with the hot data?  Or will you make a full backup and then do the experiments?  Or will, somehow, the testing become less rigorous when the time involved becomes apparent and immediate?

May I suggest that those who are trying to convince Dracheschreck to change his mind about RAID, despite him being clear about it: 1) advocate a specific kind of RAID level and organisation, 2) describe the actual benefits and 3) address the points about the work of the rebuild and the complexity of the setup.

My point, simply, is that when proposing RAID (for redunancy) we have to think about the net cost/benefit in time, configuration, testing as well as the simple benefit in performance and uptime, both of which have been explicity discounted by Dracheschreck.  Merely repeating that you need it is unhelpful.

I write as someone who has seen enormous data loss, both with and without RAID.  The single distinguishing characteristic that makes your data survive is organisation, a plan, and testing.

Kind regards to all.
Jonathan.

PS.  Of course we're speaking about the RAID levels which redundancy, not the simple performance and size levels.

These are well thought out points. Unfortunately, downtime for most organizations is something they would just not accept as a foregone conclusion.  Obviously, when doing DR planning you have to weigh the cost vs. benefit of a particular solution. In everyday practice,  just running a single disk and waiting for it's eventual failure or hoping that SMART data will alert you of a potential failure before it happens seems a little counter intuitive.  In my company, if we were to lose a huge chunk of our data due to a failed disk in the middle of responding to a proposal we could potentially miss out on multi-million dollar jobs.  Even just the 1 hour restore time you mentioned could potentially cause us to miss that window.  So, RAID + both onsite disk-to-disk and offsite backups helps to mitigate that risk for us. 

The OP really doesn't want traditional RAID and is willing to settle with having to restore a failed disk and the downtime associated with it.  I'd suggest that he buys a license for [UNRAID]("http://lime-technology.com/technology").  I won't explain it here because it's likely you've seen it before, but if you haven't, it has all of the benefits of JBOD that you mentioned above plus one parity disk.  This has the added benefit of a simple web GUI to manage the disks, your shares, etc.

Solaris/Openindiana + the napp-it web GUI as I mentioned before also makes it very easy to manage all aspects of a ZFS array + sharing + snapshots to aid in the case of accidental deletion / user error + checksumming your data for bit level accuracy + the side benefit of eliminating almost all of the bugs you mentioned without a steep learning curve. It makes for a pretty robust system.  Replacing a failed disk is as simple on either of these two setups as removing the failed disk and adding a new disk to the system and adding it the the array via the web interface.  It literally takes about 5 minutes, and once the new disk is in place, it will resync automatically.

I've suggested raid levels that I would use, as well as structure of vdevs, and explained both the increased fault tolerance and massive throughput gains that could be had by using that setup in previous posts, so I won't do that again.  At this point the OP has made his decision and we're just debating amongst ourselves, so we might as well move along to helping other people. Thank you very much for taking the time to explain your thoughts :)

---

### Post by Jonathan L on 2012-04-20
... nice post, rubylaser.


Dracheschreck ... do please keep up to date with your progress.

Kind regards all.

Jonathan.

---

### Post by jocatoth on 2012-04-20
thanks and kudos to rubylazer and jonathan l for well a considered and written high level discussion concerning what RAID actually does and does not do. i think this proves again that one of the best features of UBUNTU is this forum.

---

### Post by Dracheschreck on 2012-04-23
Guys, thanks for the info again!

I've been re-reading this whole thread, this is my current idea:

[LIST]
[*]3 x m1015 cards, to support up to 24 drives over 2TB when flashed.
[*]Expand to the Norco RPC-4224 with 24 Bays
[*]Run as a JBOD.
[/LIST]

One of you suggested to just use a flash drive to run the OS, for example FreeNAS. Using a specific OS for data servers seems like a good idea, however, I was thinking that this server could be used to run experiments on the data directly as well, which would require a general purpose OS.

Any other opinions on running from a flash drive instead of a hard disk? (Or on choosing an application specific OS instead of Ubuntu?)

Apparently there are no DDR3 Unbuffered ECC sticks larger than 4GB so that limits the computer to 16GB.

[Detailed parts list is here as usual. Tips and recommendations are very much suggested!]("https://docs.google.com/spreadsheet/pub?key=0AisioMl_rX7VdG4xU2xka2lxUjYzY1djWmducGJnSnc&output=html")

EDIT: 
Maybe I should change the setup to a Desktop CPU & MOBO, which would allow for more RAM (Useful if we want to run experiments on the server). Thoughts on that?

---

### Post by rubylaser on 2012-04-23
> **Dracheschreck said:**
> Guys, thanks for the info again!

I've been re-reading this whole thread, this is my current idea:

[LIST]
[*]3 x m1015 cards, to support up to 24 drives over 2TB when flashed.
[*]Expand to the Norco RPC-4224 with 24 Bays
[*]Run as a JBOD.
[/LIST]

One of you suggested to just use a flash drive to run the OS, for example FreeNAS. Using a specific OS for data servers seems like a good idea, however, I was thinking that this server could be used to run experiments on the data directly as well, which would require a general purpose OS.

Any other opinions on running from a flash drive instead of a hard disk? (Or on choosing an application specific OS instead of Ubuntu?)

Apparently there are no DDR3 Unbuffered ECC sticks larger than 4GB so that limits the computer to 16GB.

[Detailed parts list is here as usual. Tips and recommendations are very much suggested!]("https://docs.google.com/spreadsheet/pub?key=0AisioMl_rX7VdG4xU2xka2lxUjYzY1djWmducGJnSnc&output=html")

EDIT: 
Maybe I should change the setup to a Desktop CPU & MOBO, which would allow for more RAM (Useful if we want to run experiments on the server). Thoughts on that?

If you wanted to virtualize, you could go with the [ESXi all-in-one]("http://www.napp-it.org/doc/downloads/all-in-one.pdf") and run an Openindiana VM with HBA passthrough of the m1015 cards and then run Ubuntu in another VM.

EDIT: Here are 8GB sticks that should work with the Supermicro board if you want to get to 32GB.
[Option 1]("http://www.provantage.com/kingston-technology-kvr1333d3e9sk2-16g~7KIN91M7.htm")
[Option 2]("http://www.provantage.com/crucial-technology-memory-ct2kit102472ba160b~7CIAL6R5.htm")

You could also look at the 2011 platform for more RAM.  Here's different setup, although more pricey, this is a newer platform and has 32GB of RAM (non-ECC memory).
[MOBO] [ASUS P9X79 WS]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131798")
[CPU] [Intel Core i7-3820 Sandy Bridge-E 3.6GHz]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819115229")
[RAM] [G.SKILL Ripjaws X Series 16GB (4 x 4GB)]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820231429&nm_mc=AFC-C8Junction&cm_mmc=AFC-C8Junction-_-Memory%20(Desktop%20Memory)-_-G.SKILL-_-20231429&AID=10440897&PID=3967465&SID=") x2 for 32GB

---

### Post by rubylaser on 2012-04-23
This is funny, I just went on Servethehome's website to view their motherboard suggestions, and got looking at their builds and realized that their "Decked Out" build is almost exactly the same parts as what you've ended up at.

[http://www.servethehome.com/midrange-diy-storage-server-buyers-guide-october-2011/]("http://www.servethehome.com/midrange-diy-storage-server-buyers-guide-october-2011/")

---

### Post by Dracheschreck on 2012-04-24
> **rubylaser said:**
> This is funny, I just went on Servethehome's website to view their motherboard suggestions, and got looking at their builds and realized that their "Decked Out" build is almost exactly the same parts as what you've ended up at.

[http://www.servethehome.com/midrange-diy-storage-server-buyers-guide-october-2011/]("http://www.servethehome.com/midrange-diy-storage-server-buyers-guide-october-2011/")

:guitar: great!

---

### Post by Jonathan L on 2012-04-24
Hi Dracheschreck

> just use a flash drive to run the OS, for example FreeNAS. Using a specific OS for data servers seems like a good idea, however, I was thinking that this server could be used to run experiments on the data directly as well, which would require a general purpose OS.

Any other opinions on running from a flash drive instead of a hard disk? (Or on choosing an application specific OS instead of Ubuntu?)
I've had a lot of mileage running from flash, both loading up ramdisks and with RO-mounted unions (just like the Live CD).  The best, in my opinion, was running from ramdisks: really fast to do anything (exept boot!).

Although the server-specific OS are great, I'd probably suggest using whatever you had the most experience of.  It can be very irritating learning all the different flags (for ps, ls, ifconfig and so on) if you move from one unix-like to another.  And if you get a real incompatibility it will be difficult to find.  If you've already got lots of different things running and have already addressed those issues, then maybe it's a good idea.  I've had lots of experience of other Unixes, and I can heartily commend FreeBSD for disk servers.  All in all, I'd recommend harmonising if you can -- indeed, that's why I use Ubuntu for most things now, as the harmony between servers, desktops, and AWS-cloud servers really saves a lot of effort.

Running programs on your file server?  I wouldn't recommend it.  For this kind of thing I quite like diskless compute servers, booted PXE from the file server, NFS mount everything, and run any applications on that.  A project I've completed recently is like that: a small, RAID file server and a stack of diskless compute servers, switched on and off by the master machine (to save power during low demand.)

Yours is turning into a great project!

Kind regards,
Jonathan.

---

### Post by Dracheschreck on 2012-04-24
Hi again, I was going over the current parts list, and noticed that the [motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813182253") doesn't have 3 PCIEx8 slots, which will be needed for the 3 M1015 cards.

After googling a bit, it seems that the M1015's will work fine on these slots, since they are physically identical to 8x though they will only have the bandwith of 4x. This should be no problem since my disks won't even be in RAID so all their throughput together shouldn't be bottlenecked by the 4x PCIE bus.

Just typing my thoughts here in case I'm wrong :P

---

### Post by rubylaser on 2012-04-24
> **Dracheschreck said:**
> Hi again, I was going over the current parts list, and noticed that the [motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813182253") doesn't have 3 PCIEx8 slots, which will be needed for the 3 M1015 cards.

After googling a bit, it seems that the M1015's will work fine on these slots, since they are physically identical to 8x though they will only have the bandwith of 4x. This should be no problem since my disks won't even be in RAID so all their throughput together shouldn't be bottlenecked by the 4x PCIE bus.

Just typing my thoughts here in case I'm wrong :P

Nope, you are correct, and even at PCI-e x4, the bandwidth is still 1.6GBps, so ( 8 ) spinning disks won't come close to saturating that bus.

---

### Post by Dracheschreck on 2012-04-24
> **Jonathan L said:**
> Running programs on your file server?  I wouldn't recommend it.  For this kind of thing I quite like diskless compute servers, booted PXE from the file server, NFS mount everything, and run any applications on that.  A project I've completed recently is like that: a small, RAID file server and a stack of diskless compute servers, switched on and off by the master machine (to save power during low demand.)

Hmm. In our working situation, probably only 1-2 people will work on this data (read-only) at any given time. Could you elaborate why you dislike working on the server?

My idea would be to set up Ubuntu, people could SSH in and execute their programs directly on the server, saving a lot of time (no transferring of data back and forth)

---

### Post by Jonathan L on 2012-04-24
Hi Dracheschreck

> Hmm. In our working situation, probably only 1-2 people will work on this data (read-only) at any given time. Could you elaborate why you dislike working on the server?

My idea would be to set up Ubuntu, people could SSH in and execute their programs directly on the server, saving a lot of time (no transferring of data back and forth)My recommendation against letting people work on the server directly isn't really to do with their load, it's to do with the software installation.  I try to organise things so that I can replace them, quickly, with replacement hardware, and reinstall things, from cold if required.  I accept that this Easy-To-Rebuild approach isn't common, as most people prefer Complete-Restore-From-Backup, but I find that this can restrict you in lots of ways that a well-organised rebuild won't have.  So, in your case, it isn't that the people will use CPU, it's that they will (require) software to be installed.  This might change frequently, depending on what they're doing, and might lead you into runaway upgrades.

My general disposition is that a file server's job is imply one thing: providing files.  And an attached compute server does other things.  Suppose you have your 30Tbyte FS and a compute server C1.  When you need to experiment with the compute environment, you borrow something and try a C2.  Because this is just a compute server with programs and no data, it's quick to deal with.  As you've said, not copying data back and forth is a _huge_ advantage, whether locally on the FS or over NFS.

On the other hand perhaps that's too much complexity for your situation, or that NFS speeds would be too slow between FS and C1.  Then you do exactly what you said: make the data read-only, and away you go.  It all depends on the software (and the money!).   Especially if you've only got a user at a time.  Or the programs are very well behaved.

My earlier argument in favour of "normal" Ubuntu on your file server was incidentally partially to do with this: you _can_ run programs if you want to.  Either the users directly, or you install them via cron or whatever.  I might easily be accused of wanting it both ways: but it was about making choices available.

A lot also depends on the user base.  Sounds like you have a small number of rather collaborative people.  In which case sure, let them use the server.  (If they had the potential to hack in and mess things up it would be a different matter.)  If it goes too slowly or causes problems, get a compute server and stick it on top.

Hope that's some use.

Kind regards,
Jonathan.

---

### Post by rubylaser on 2012-04-24
Personally, with the hardware that's mentioned in this thread, if you're not using this as a virtualization host, you're wasting a bunch of capability (you could run less expensive mobo, ram, cpu).  I'd run ESXi on this and pass through all of the m1015 cards to Openindiana and use that as my SAN.  Then, I'd setup an Ubuntu instance to access the data.  Since these are both on the same machine and don't have to go over the physical network, this VM would have access speeds greater than gigabit ethernet. Even virtualized, both of these machines will be very fast and the SAN will still have great throughput.  Just my 2 cents :)

---

### Post by CharlesA on 2012-04-24
> **rubylaser said:**
> Personally, with the hardware that's mentioned in this thread, if you're not using this as a virtualization host, you're wasting a bunch of capability (you could run less expensive mobo, ram, cpu).  I'd run ESXi on this and pass through all of the m1015 cards to Openindiana and use that as my SAN.  Then, I'd setup an Ubuntu instance to access the data.  Since these are both on the same machine and don't have to go over the physical network, this VM would have access speeds greater exceeded gigabit ethernet. Even virtualized, both of these machines will be very fast and the SAN will still have great throughput.  Just my 2 cents :)
Huge +1

---

### Post by Dracheschreck on 2012-04-24
Virtualizing was not at all my purpose. Pardon me if I didn't explain the environment correctly, but, as Jonathan L correctly inferred, we are indeed a small group of very collaborative people. 

This is why I didn't think about virtualizing and the reason why I want to keep everything really simple, physical access to the server is easy (next building).

Also, it is the first time I heard of IPMI. Didn't know you could to KVM without having the computer on, it's very cool! However, it is certainly not a need of this system, so maybe you are right and server-quality hardware is not needed.

I'll check the prices and try to come up with an i7-based solution and see what you guys think about it.

Thanks for the comments, this is a very nice thread ):P

---

### Post by Dracheschreck on 2012-04-25
Ok, what do you think about this?

My only doubt is if the full ATX mobo is going to fit in the NORCO case.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16820231507](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231507)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819115070](http://www.newegg.com/Product/Product.aspx?Item=N82E16819115070)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813128545](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128545)

---

### Post by Jonathan L on 2012-04-25
> **Dracheschreck said:**
> Ok, what do you think about this?

My only doubt is if the full ATX mobo is going to fit in the NORCO case.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16820231507](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231507)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819115070](http://www.newegg.com/Product/Product.aspx?Item=N82E16819115070)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813128545](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128545)

Hi again

Norco case says "Motherboard Compatibility: Support EEB (12"x13"), CEB(12"x10.5"), [COLOR=Red]ATX (12"x9.6")[/COLOR], Micro ATX (9.6" x 9.6")", so you wouldn't even be the biggest board it could take.

I don't follow CPUs and motherboards closely, but as a generalisation I like to steer away from boards with lots of different sized slots.  But most of all I'd suggest getting one someone like rubylaser has actually used, as there are so many available places for surprises!   I tend for my projects to be very conservative and use mostly Intel motherboards, mostly because of the quality of the documentation.  (I expect withering comments from the brethren!)

Looks like you'll have plenty of CPU spare for your users, by the way.

Re server vs desktop motherboards.  Server versions tend to have a bit more "remote control" available, if you care for it; desktop ones tend to have a bit too much video.  I've used both for server functions, and have not had issues.  (Server vs desktop software, mounting hardware, power supplies, on the other hand.)

Kind regards,
Jonathan.

---

### Post by rubylaser on 2012-04-25
> **Dracheschreck said:**
> Ok, what do you think about this?

My only doubt is if the full ATX mobo is going to fit in the NORCO case.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16820231507](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231507)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819115070](http://www.newegg.com/Product/Product.aspx?Item=N82E16819115070)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813128545](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128545)

These parts are more expensive than the e3-1230 + Supermicro solution I suggested earlier, so I'd suggest you stick with the server hardware and ECC memory.  Also, if you're not going to virtualize on this box, 16GB of RAM is MORE than enough :)

If you really still want 32GB, you can get 8GB dimms.  You just need to get two of these kits KVR1333D3E9SK2/16G for 32GB of RAM on the Supermicro board.

---

### Post by Dracheschreck on 2012-05-07
Ok, so I'm almost ready, will stick to the server-quality hardware instead of the i7.

I'm trying to find a bracket to mount the OS hdd inside the box (I thought somebody mentioned such a device in this thread but I couldn't find it :confused:). Do you know any alternatives to [this]("http://www.atechfabrication.com/products/drive_mounting_kits.htm")? 

Also, cheap m1015's don't seem to be available right now on Ebay. Do you think I should wait to see if cheaper ones show up?

Thanks for all the help, can't wait for the parts :popcorn:

---

### Post by CharlesA on 2012-05-07
I haven't seen any brackets like that used before.

You just wanted something to hold the drive that isn't an external enclosure, right?

---

### Post by Dracheschreck on 2012-05-07
> **CharlesA said:**
> You just wanted something to hold the drive that isn't an external enclosure, right?

Yup, I wouldn't want to waste one of the external slots for the OS drive.

---

### Post by CharlesA on 2012-05-07
> **Dracheschreck said:**
> Yup, I wouldn't want to waste one of the external slots for the OS drive.
Gotcha. That should work, but I've never used them, so I can't give you a review on how good/bad they are.

---

### Post by Morrighu on 2012-05-07
I know that you don't really want a back up, but in my experience, research data is often invaluable when it comes time for peer review for the article, thesis defense, etc.  Telling your thesis committee that you lost the data never goes well....  Just sayin'....

Get yourself one or more old junk servers.  Most IT shops have a few laying around.  They can be as old and slow as you like. Shove enough disks in it to cover at least one folder of your research data.  In short, create JBOD's.  

Set up rsync between them and your production server and let it copy at its own pace.  Heck for the cost of small switch and few patch cables (which most IT shops also have laying around), you could even put it on a private network.

Skip the --delete option in the rsync config and even if someone deletes by accident, you will still have a copy.

---

### Post by CharlesA on 2012-05-07
> **Morrighu said:**
> I know that you don't really want a back up, but in my experience, research data is often invaluable when it comes time for peer review for the article, thesis defense, etc.  Telling your thesis committee that you lost the data never goes well....  Just sayin'....

Indeed. Don't forget about data corruption either.

---

### Post by Jonathan L on 2012-05-07
Hi Dracheschreck

> a bracket to mount the OS hdd inside the boxIt seems your motherboard is 9.6" x 9.6" (MicroATX) and the chassis says it holds up tp 12"x13".  Looks to me like you'll have 3.4" extra width.

So how about just make some holes in the left-hand wall (looking from front) and mount with screws?  Or on the "mezzanine" above the disks, where the CD-ROM goes?  What are the two aluminium plates with circular holes?  The look like they might just be fixed-drive mounting plates.  Or perhaps you could attach some stock things like this [http://intrl.startech.com/HDD/Brackets/Bracket-for-35-Inch-Floppy-with-Bezel~BRACKETFDBK]("http://intrl.startech.com/HDD/Brackets/Bracket-for-35-Inch-Floppy-with-Bezel%7EBRACKETFDBK") to that mezzanine.

[http://www.norcotek.com/product_images/flyer/rpc4220_5.jpg](http://www.norcotek.com/product_images/flyer/rpc4220_5.jpg)


All best,
Jonathan.

---

### Post by rubylaser on 2012-05-07
> **CharlesA said:**
> Indeed. Don't forget about data corruption either.

If the OP uses ZFS and ECC RAM corruption is basically non existent as long as you scrub periodically.

And, I'd wait for cheaper m1015's.  I got mine for $60 each.

---

### Post by CharlesA on 2012-05-07
> **rubylaser said:**
> If the OP uses ZFS and ECC RAM corruption is basically non existent as long as you scrub periodically.

And, I'd wait for cheaper m1015's.  I got mine for $60 each.
Gotcha. That's pretty handy. :)

---

