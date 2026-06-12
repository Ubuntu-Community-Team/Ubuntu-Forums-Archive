---
title: "Legacy PCI NIC OK for WAN NAT Interface?"
date: 2011-10-09
forum: Server Platforms
---

### Post by mattlach on 2011-10-09
Hey all,

I recently got a fantastic deal on an open box [micro ATX AMD E-350 board](http://www.asus.com/Motherboards/AMD_CPU_on_Board/E35M1M_PRO/), and figured I'd use it for my new server, as its low power use is perfect for a machine that stays on 24/7.

The server is going to serve as my NAT and NAS, as running a few other light weight daemons.

I have been told that the on-board gigabit Ethernet (Realtek 8111E) while fine for casual browsing, is not sufficient for server use.

[img]http://www.asus.com/Motherboards/AMD_CPU_on_Board/E35M1M_PRO/websites/Global/products/qSoDxhM5mAk1F607/VBChTnIckoHlDyrT_500.jpg[/img]


So it seems I find myself in a slight expansion bind.

As can be seen above, the slots are as follows:

1.) PCI Express 16x (4x mode)
2.) PCI Express 1x
3.) Legacy PCI
4.) Legacy PCI

Slot 1 will need to be reserved for my planned SATA controller as it is a 4x board.  This SATA controller will complement the 5 on board SATA ports for use with FlexRaid.

I'll need slot 2 for a gigabit ethernet card for the LAN.  (I have opted to go with a Broadcom NetXtreme card).  This will see transfer speeds at full gigabit speeds due to the NAS.  I chose this slot for the LAN as legacy PCI is limited to 133MB/s.  This is fast enough for gigabit in one direction, but not full duplex.

My plan is currently to use legacy PCI slot 3 or 4 for a ethernet card for the WAN. (I have found a marvell based NIC I like). My internet connection is 35Mbit down and 30mbit up, so the PCI bus should have more than sufficient bandwidth for even a saturated internet connection going full bore up and down.

Are there any other issues I should know about using the PCI bus for the WAN Ethernet card.   Could this increase latencies over a PCIe card due to the PCIe-PCI bridge?  I have some avid gamers in the household who would NOT be pleased if this were the case.

As an alternative I have been looking at some server dual port Broadcom NetXtreme NIC cards - which would allow me to have both WAN and LAN on the same PCIe 1x slot, but these are expensive and usually used pulls from old servers, so I'd rather not go that route if I don't have to.

I appreciate any input!

Thanks,
Matt

---

### Post by Bachstelze on 2011-10-10
> **mattlach said:**
> 
I have been told that the on-board gigabit Ethernet (Realtek 8111E) while fine for casual browsing, is not sufficient for server use.

Whoever told you that was probably referring to high-load servers for entreprise applications, where you have 1Gbps flowing almost constantly. I would be willing to bet you won't see any difference, be it only because your ISP probably doesn't give you anything near 1Gbps. You could probably use a 10-year-old 100Mbps NIC with no problem on your WAN interface.

---

### Post by volkswagner on 2011-10-10
I'd be very surprised if the OnBoard LAN did not exceed your needs for the WAN interface.

---

### Post by mattlach on 2011-10-10
> **Bachstelze said:**
> Whoever told you that was probably referring to high-load servers for entreprise applications, where you have 1Gbps flowing almost constantly. I would be willing to bet you won't see any difference, be it only because your ISP probably doesn't give you anything near 1Gbps. You could probably use a 10-year-old 100Mbps NIC with no problem on your WAN interface.

Well, the load on the WAN interface will not be inconsequential.

In our house we have 4 very connected people.   At any given time there may be 2 PC's and an XBOX 360 playing video games, with multiple automatic OS patch upgrades downloading, and someone streaming a netflix film on the tv, while browsing the web on their phone, and the NAS server downloading the latest linux distribution via bit torrent.

All this traffic is going to be going through the WAN port at the same time.

That's a lot for a budget netbook-style ethernet chipset to handle, even at a relatively low speed of 35mbit down, 30mbit up.

As I said above, I am not too concerned with absolute bandwidth.  The PCI bus's half duplex 133MB/s should be more than enough.   In fact, if I max out the internet speed, at 35mbit down and 30mbit up I will only be using ~6% of that bandwidth.  I am more concerned with any latency introduced by the PCI express to PCI bridge on the motherboard.   There will be a bridge that converts PCI Express signals (native to modern chipsets) to something that a PCI card can understand.   My concern is that this bridge is going to introduce latencies.   The gamers in the house would HATE this.

---

### Post by robvas on 2011-10-10
I think you are making mountains out of molehills. There should be no measurable difference between the setup you are talking about and a off-the-shelf home router. Don't forget that those things use some very low-end internals.

---

### Post by mattlach on 2011-10-10
> **robvas said:**
> I think you are making mountains out of molehills. There should be no measurable difference between the setup you are talking about and a off-the-shelf home router. Don't forget that those things use some very low-end internals.

This is kind of the response I was looking for.

I feel the same way, but never having done it before, I don't know for sure, and I was hoping to get input from someone who has :)

I know that dedicated routers use some pretty low end equipment, but its amazing how much you can do with really low end parts when they are designed specifically for the task at hand.

The very popular Broadcom MIPS chips - for instance - have (as I understand) everything integrated on the same chip, including the ethernet chips.

The 125mhz MIPS CPU may not be very highly powered, but there shouldn't be much in the way of latency to be heard of between the WAN and LAN side if they both reside on the same chip :p

---

### Post by svtguy88 on 2011-10-10
I agree with everyone that says that your onboard Ethernet is probably fast enough.  As mentioned, you're not going to see anywhere near gigabit speeds from your ISP, so even with multiple clients doing bandwidth intensive tasks should be fine.

That said, I'm in the process of configuring a Dell Poweredge 1800 that I picked up.  I purchased a 4 port PCI-X NIC for the LAN side of things, and am using the onboard Gigabit port for my ISP.  

You could likely pickup a card like I did for around $50, as that's about what I paid on eBay.  Just be careful to make sure the PCI-X card's slot design is one that works with your PCI slots.  PCI-X is backwards compatible with PCI, as long as it fits in the slot - it will just run at the slower speed that PCI is rated at, but if you want a multi port card, I noticed the PCI-X cards on eBay are about the cheapest you can get (at lest for a four port).

---

### Post by mattlach on 2011-10-10
> **pkmgarf said:**
> I agree with everyone that says that your onboard Ethernet is probably fast enough.  As mentioned, you're not going to see anywhere near gigabit speeds from your ISP, so even with multiple clients doing bandwidth intensive tasks should be fine.

That said, I'm in the process of configuring a Dell Poweredge 1800 that I picked up.  I purchased a 4 port PCI-X NIC for the LAN side of things, and am using the onboard Gigabit port for my ISP.  

You could likely pickup a card like I did for around $50, as that's about what I paid on eBay.  Just be careful to make sure the PCI-X card's slot design is one that works with your PCI slots.  PCI-X is backwards compatible with PCI, as long as it fits in the slot - it will just run at the slower speed that PCI is rated at, but if you want a multi port card, I noticed the PCI-X cards on eBay are about the cheapest you can get (at lest for a four port).

I would be concerned about running 4 gigabit ports on the same 32bit 33mhz PCI slot, considering the PCI bus at these speeds just barely has enough bandwidth for one gigabit port...  It will likely be OK on your poweredge has it probably has capable PCI-X slots.

As I ahve said before, I agree that the total 35mbit down and 30mbit up only results in about 6% utilization of the legacy PCI bus.  I am not concerned with the bandwidth.   I am more concerned with the latency introduced by the PCIe -> PCI bridge.  I am not sure if this is noticeable or not.

---

