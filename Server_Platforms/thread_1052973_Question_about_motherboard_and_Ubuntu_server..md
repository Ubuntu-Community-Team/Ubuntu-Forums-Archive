---
title: "Question about motherboard and Ubuntu server."
date: 2009-01-28
forum: Server Platforms
---

### Post by _sAm_ on 2009-01-28
Hi

For a simple "home server" with Ubuntu Server as OS will this motherboard be good enough: [http://www.intel.com/products/desktop/motherboards/D945gclf2/D945gclf2-overview.htm](http://www.intel.com/products/desktop/motherboards/D945gclf2/D945gclf2-overview.htm) 

I want a homeserver that use as little power as possible.

It will do filesharing(samba, nfs, ssh, sftp), rtorrent, printserver, UPnP, and perhaps gallery2, backup via rsync, and not more then 5 users.

The motherboard has only 2 sata ports, but I will add 4 more via pci to sata.

Thanks for any answers

---

### Post by windependence on 2009-01-28
This board works fine with Ubuntu, and draws only about 30 watts. I run a desktop machine on it without issues.

-Tim

---

### Post by electrogeist on 2009-01-28
Should be good.

Couple things I don't like about it:  only 1 memory slot, only 1 PCI slot, and CPU soldered on board.  But then again it is small and may be cheaper than buying board + CPU seperately.  Odd that they used a Realtek NIC instead of an Intel NIC...

---

### Post by windependence on 2009-01-29
> **electrogeist said:**
> Should be good.

Couple things I don't like about it:  only 1 memory slot, only 1 PCI slot, and CPU soldered on board.  But then again it is small and may be cheaper than buying board + CPU seperately.  Odd that they used a Realtek NIC instead of an Intel NIC...

You have to remember, this board is not really intended to be a desktop board. It is intended for "appliance" type machines and things like kiosks.

If you put 2 GB in the mem slot (the max) it runs just great for almost any application. CPU is permanent as it's not intended to be upgraded. If you think about it, by the time you are ready to upgrade your boards, the memory has usually changed along with things like PCIe or other interface changes. I think this is a great idea myself. The board/CPU is ridiculously cheap for what you get. It's a frickin dual core proce for God's sake.

-Tim

---

### Post by electrogeist on 2009-01-30
True. I was just pointing out that expandability is not its strong point  ;) 

Another point, and while it doesn't matter for server use, is that the GMA 500 video currently has no accelerated drivers right?

---

### Post by cariboo on 2009-01-30
I use the same board for a media center, I only have 1Gb ram, and it runs quite well.

Jim

---

### Post by _sAm_ on 2009-02-11
Thank you all for your help:-) 

I was about to order this MB then I found this: [http://www.tomshardware.com/reviews/intel-atom-efficiency,2069-2.html](http://www.tomshardware.com/reviews/intel-atom-efficiency,2069-2.html) And now I think this "new" solution looks better for a home server; same price all in all, same low power usage, better performance. Hmmm 

Thanks again

---

