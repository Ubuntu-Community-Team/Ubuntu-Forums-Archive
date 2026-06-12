---
title: "What is the best option to add 4 SATA ports?"
date: 2009-04-06
forum: Server Platforms
---

### Post by TomB19 on 2009-04-06
I need 4 SATA ports.  I have one free PCIe x1 slot, one PCI slot, and two free PCIe x8 slots.

What is the best option to add 4 ports?  Port multiplier?  4 port PCI card?

I want to run 4 x 1.5TB drives so I'm a little worried about the 4 port PCI option.

I have a spare eSATA port.  I could connect a port multiplier to the eSATA connector and have just as much bandwidth as a PCI solution.

Whatever I do, it has to work with Ubuntu 8.10.

---

### Post by TomB19 on 2009-04-07
I just ordered an Sil3114 based 4 port PCI card.  Some people have reported success with this card while others report failure.

[http://www.ncix.com/products/?sku=19892&vpn=SY-SA3114-4R&manufacture=Syba](http://www.ncix.com/products/?sku=19892&vpn=SY-SA3114-4R&manufacture=Syba)

I'm hoping the card will support 4 x 1.5TB drives.  I'll certainly flash the firmware on the card before giving up.  I also need it to support hot-swap.  It looks like the Sil3114 chip can do what I need.

I don't care too much about performance and I don't care about firmware RAID.  I just want to see the drives with Kubuntu 8.10 (kernel 2.6.27-11-generic) and assemble them with mdadm.

I'll report back so we have this information in the forums.

---

### Post by fjgaude on 2009-04-08
Well, with a PCI card you will be limited to a thru-put of about 110MB/sec. With four of late-model drives in raid5 you could have a thru-put of over 250MB/sec, but with that slow bus of PCI you are hosed! Go with PCI-E.

---

### Post by TomB19 on 2009-04-11
I'd love to use a PCIe controller but could not find a 4 (or more) port PCIe SATA host adapter that was checked out with Linux.

Any recommendations?

---

### Post by Beef on 2009-04-12
Have a look at a perc 5i, you can pick them up on ebay for around $120. Will give you 8 sata ports.

---

### Post by ghettofreeryder on 2009-04-13
My home servers have an Adaptec 2410SA in one, and a 31605 in the other, both work no problem

---

