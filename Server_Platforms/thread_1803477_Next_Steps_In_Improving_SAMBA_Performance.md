---
title: "Next Steps In Improving SAMBA Performance"
date: 2011-07-13
forum: Server Platforms
---

### Post by ThePol1 on 2011-07-13
I built my own file server based on the Intel Atom 525 and Ubuntu 11.04 (amd64):
[http://www.intel.com/products/desktop/motherboards/db-D525MW/D525MW-overview.htm](http://www.intel.com/products/desktop/motherboards/db-D525MW/D525MW-overview.htm)

It has 2 2TB Western Digital Green drives connected via SATA.

Internal file transfers (disk-to-disk) using Nautilus zip along at 80 Mb/sec. Over SAMBA, however, I'm getting 35 Mb/sec. Other than creating the shares, I haven't modified smb.conf.

I have a gigabit network. I've run atop on the receiving computer and it isn't being taxed. At 35 Mb/sec the file server is also not being taxed.

Should I be focusing on testing the onboard NIC (RealTek 8111E) in the file server or looking at SAMBA? Any suggestions on the next steps for how to improve SAMBA performance?

---

### Post by brighty22 on 2011-07-13
Transfers inside a machine are always faster than network, not just because SATAII is theoretically 3 times faster than gigabit ethernet. 35MB/s is a very reasonable rate on its own.. to speed it up further I would look at the interfaces on the computer and server, as well as any switches in between. Samba could be tweaked as well, although don't expect anywhere near 80MB/s.

---

### Post by ThePol1 on 2011-07-13
> **brighty22 said:**
> Transfers inside a machine are always faster than network, not just because SATAII is theoretically 3 times faster than gigabit ethernet. 35MB/s is a very reasonable rate on its own.. to speed it up further I would look at the interfaces on the computer and server, as well as any switches in between. Samba could be tweaked as well, although don't expect anywhere near 80MB/s.

I have 2 TrendNet Gigabit switches between the machines with CAT5e cable. [http://www.amazon.com/TRENDnet-Unmanaged-Auto-Negotiation-Auto-MDIX-TEG-S80G/dp/B001QUA6RA/ref=sr_1_1?ie=UTF8&qid=1310567106&sr=8-1](http://www.amazon.com/TRENDnet-Unmanaged-Auto-Negotiation-Auto-MDIX-TEG-S80G/dp/B001QUA6RA/ref=sr_1_1?ie=UTF8&qid=1310567106&sr=8-1)

How would I go about looking at the interfaces between the machines?

---

### Post by brighty22 on 2011-07-13
That switch isn't smart or managed, so nothing can be done there. Consider buying a dedicated gigabit NIC; onboard chips aren't always the greatest (although some are very good), but as I said in my last post, it will make little if any difference.

---

