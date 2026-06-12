---
title: "VIA NAS 7800 - Tiny motherbaord with 8 SATA-2 ports"
date: 2008-12-20
forum: Server Platforms
---

### Post by handy on 2008-12-20
Has anyone had any experience with one of these [***_VIA NAS 7800_***]("http://www.via.com.tw/en/products/mainboards/motherboards.jsp?motherboard_id=610") motherboards?

***[Edit:]** Doh! I spelled motherboard wrong! :lolflag:*

---

### Post by windependence on 2008-12-21
I am not running that specific board but I run a mini ITX board from Intel and it's fine. You may want to take a look at this one also since it has better specs. It's an Intel D945GCLF With   Integrated Atom 230 Processor. 1.6 GHz instead of 1.5, it can take 2 GB memory instead of 1, and the VIA chrome video chip does not play well with some Linux distros. Also, the Atom is a dual core processor.

I don't know what you are paying for that board but I am a reseller and can get you the Intel board for $84.95 and I'll throw in free shipping if you are in the states. Here is some info on the board and the Atom processor:

[http://www.intel.com/products/desktop/motherboards/D945GCLF/D945GCLF-overview.htm](http://www.intel.com/products/desktop/motherboards/D945GCLF/D945GCLF-overview.htm)

[http://ark.intel.com/cpu.aspx?groupId=35635](http://ark.intel.com/cpu.aspx?groupId=35635)

Oh and the processor uses just 4 watts of power. 

If you are going to build a NAS check out FreeNAS [http://www.freenas.org/](http://www.freenas.org/). Absolutely rock solid (as with most FreeBSD stuff) and 5 minute install from ISO CD.

-Tim

---

### Post by handy on 2008-12-21
Thanks for your reply windependence :-)

I live in Oz, downunder.  So I expect to pay the freight.

I will read your links & get back to you.

Again, thanks for the offer.

---

### Post by windependence on 2008-12-21
No problem, I can ship to Oz. Do it all the time.

-Tim

---

### Post by handy on 2008-12-21
windependence I'll PM you & we can continue this discussion.

---

### Post by windependence on 2008-12-21
No problem thanks.

-Tim

---

### Post by tyn on 2010-01-30
Hi,
The dual core atom boards sound interesting.  I followed your link to the Intel site but none of the boards I looked at had more than 2 SATA ports.  I need at least 8 and gigabit ethernet for my NAS (preferably with hardware that works with ubuntu).

Do the atom boards run all the ubuntu software?  I really only need mediatomb and samba though.

Thanks,
Ty

---

### Post by volkswagner on 2010-01-30
> **windependence said:**
> I am not running that specific board but I run a mini ITX board from Intel and it's fine. You may want to take a look at this one also since it has better specs. It's an Intel D945GCLF With   Integrated Atom 230 Processor. 1.6 GHz instead of 1.5, it can take 2 GB memory instead of 1, and the VIA chrome video chip does not play well with some Linux distros. Also, the Atom is a dual core processor.

I don't know what you are paying for that board but I am a reseller and can get you the Intel board for $84.95 and I'll throw in free shipping if you are in the states. Here is some info on the board and the Atom processor:

[http://www.intel.com/products/desktop/motherboards/D945GCLF/D945GCLF-overview.htm](http://www.intel.com/products/desktop/motherboards/D945GCLF/D945GCLF-overview.htm)

[http://ark.intel.com/cpu.aspx?groupId=35635](http://ark.intel.com/cpu.aspx?groupId=35635)

Oh and the processor uses just 4 watts of power. 

If you are going to build a NAS check out FreeNAS [http://www.freenas.org/](http://www.freenas.org/). Absolutely rock solid (as with most FreeBSD stuff) and 5 minute install from ISO CD.

-Tim


Isn't the Atom 230 single core.  I thought the 330 was the dual core model.

Although the cpu uses 4watts the GPU 945 chipset is the power hog here, requiring the large heatsink and/or fan.

I still love the Atom platform, but am anxious to see a low end/low power GPU paired with it.

I am running the BOXD945GCLF2 with Ubuntu Server 8.04.1, flawlessly, which has the gigabit onboard LAN.

I recall reading that the dual core shares the FSB so it actually divides the buss speed, possibly reducing performance in single threaded processes.

---

### Post by tyn on 2010-01-30
Yes it is the 330 (or the D510) that are dual core; not the 230.  On the Intel site there is a summary page  [http://www.intel.com/products/desktop/motherboard/index.htm]("http://www.intel.com/products/desktop/motherboard/index.htm") that has all the boards they make; several have embedded atom CPU's.

I didn't realise the 945 was such a problem.  I guess that leaves the Nvidia Ion chipset or the Intel NM10.  I haven't seen any of these with more than 4 SATA-2 ports.  It seems a little odd; I would have guessed that NAS devices would be a big market for these embedded motherboards.

---

### Post by tlsarles on 2010-01-30
windependence,

I am interested in putting together a low cost NAS too. That Intel board doesn't look to bad, altho I plan to run opensolaris/zfs with all the bells as an iSCSI target, so I expect I will want the dual core Atom. Would likely want dual gig Ethernet, and as many sata ports as is available. 6/8 would be cool, more would be awesome.

For extra credit, if you could put in a rack case(any # of U's) that will support the same number of 3.5in drives(With Trays), with PSU, and 2gb RAM. I'd be curious to get a shipped price (USA). Maybe a very small SSD for the boot/swap partition too, like 16gb, if its cheap enough.

On an extreme budget, so I want bottom of the barrel parts, other than the PSU, since I don't want it to die.

---

### Post by BkkBonanza on 2010-01-31
I just got a D510 board for $86 US inc. Fedex shpg in US. I'm about to set it up with Ubuntu server as a home use router/server. It doesn't have enough SATA ports for full NAS use (only 2). You would have to go with one of the higher end boards like the Gigabyte or MSI Socket P mini-itx boards, or add in a PCI SATA card. 

Problem with any of these mini-itx systems is usually you want to build in a small enclosure that limits the ability to use PCI cards. I'm trying out a PCI extender cable with a Intel Dual Port GigE card but I'm not sure this will work reliably. I need the extra LAN ports but not more SATA.

The main attraction to the Intel Atom boards is low cost. The newer versions have miniPCIe slots which are great for adding wifi (and I think there is some SATA miniPCIe around too) but otherwise the limitation is expandability.

@tlsarles,
If you're talking extreme budget then SSD isn't going to fit. Your best bet is using a USB flash on an internal port. I've found recent flash drives that are faster than CF cards and easier to add-on. The new intel boards don't have IDE so the only way to add CF is with a SATA converter. I have a Tuff'n'Tiny Kingston 8GB flash stick that gets 28MB/s read which I'll be testing for this. It only cost $12 whereas an SSD is going to cost more a lot, lot more. Intel has these new internal usb SSD modules (forget the name) but even they cost $50+ for 4GB. 

If you really need speed you'd be better off adding RAM because it will be used as disk cache to speed up any slow flash access.

---

