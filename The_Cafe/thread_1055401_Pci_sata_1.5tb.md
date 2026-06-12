---
title: "Pci sata 1.5tb"
date: 2009-01-30
forum: The Cafe
---

### Post by bonfire89 on 2009-01-30
Hello all,

I'm looking for a SATA PCI card that will work with the 1.5TB drives.

I know that I am going to get only the slower transfer speed but that is fine. This is just for my ubuntu file server.

I need some recommendations.. One that will actually work! I have been having a hell of a time with one that I bought online from tigerdirect.ca .. I have had a terrible experience with them and never plan to go back. They are very stingy... (annnyyywayyss)

I purchased [http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?Sku=M501-1086](http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?Sku=M501-1086) and only the one port works, the other goes very very slow. I convinced one of the stores into exchanging it for me (not technically allowed since I bought it online) and the replacement behaved the same way.

I am using a abit ic7 or abit ic7g motherboard. I can't remember which, and I am reading conflicting information on the board and such.

IC7 [http://www.abit.com.tw/page/en/motherboard/motherboard_detail.php?DEFTITLE=Y&fMTYPE=Socket%20478&pMODEL_NAME=IC7](http://www.abit.com.tw/page/en/motherboard/motherboard_detail.php?DEFTITLE=Y&fMTYPE=Socket%20478&pMODEL_NAME=IC7)

IC7g [http://www.abit.com.tw/page/en/motherboard/motherboard_detail.php?DEFTITLE=Y&fMTYPE=Socket%20478&pMODEL_NAME=IC7-G](http://www.abit.com.tw/page/en/motherboard/motherboard_detail.php?DEFTITLE=Y&fMTYPE=Socket%20478&pMODEL_NAME=IC7-G)

Buying from a store that has returns is pretty important since I have been have such a terrible time getting this to work. I'm located in Toronto, Canada. (incase there are other Torontonians on here). I have heard good things about newegg.ca in regards to this.


Thanks

---

### Post by Frak on 2009-01-30
It'd be very slow over a PCI port. I'd say get a PCI-X version of it to facilitate the bandwidth needs, but I don't think that's an option.

I just wanted to put that out there.

---

### Post by Skripka on 2009-01-30
> **Frak said:**
> It'd be very slow over a PCI port. I'd say get a PCI-X version of it to facilitate the bandwidth needs, but I don't think that's an option.

I just wanted to put that out there.

Yep...this is why there are server main boards....

---

### Post by Frak on 2009-01-30
> **Skripka said:**
> Yep...this is why there are server main boards....
Mac's have been using PCI-X instead of PCI for as long as the G4 series, IIRC.

^^^^^^^
bit off topic

---

### Post by bonfire89 on 2009-01-30
it took over 10 hours to install ubuntu server slow....

installing form floppy disks would probably be faster. PCI isn't THAT slow.

---

### Post by Redache on 2009-01-30
> Mac's have been using PCI-X instead of PCI for as long as the G4 series, IIRC.

^^^^^^^
bit off topic

I think what he was pointing out is that PCI-X is different to PCI-Express, which is probably what you actually meant, since no consumer Mobo will have a PCI-X port.

PCI-E is the correct way to shorthand PCI Express.

Anyway:

I'd say try and find a PCI-E card as the bus bandwidth is much higher and should therefore be faster. 

The reason the second port was slow is probably because the first chewed up all the PCI bandwidth.

---

### Post by Frak on 2009-01-30
> **Redache said:**
> I think what he was pointing out is that PCI-X is different to PCI-Express, which is probably what you actually meant, since no consumer Mobo will have a PCI-X port.

PCI-E is the correct way to shorthand PCI Express.

Anyway:

I'd say try and find a PCI-E card as the bus bandwidth is much higher and should therefore be faster. 

The reason the second port was slow is probably because the first chewed up all the PCI bandwidth.
No, I really meant PCI-X. PCI-X is much more suited for driver controllers than PCIe, since PCI-X slots have dedicated buses, while PCIe and regular PCI share a bus. PCI is just inefficient, not due to other devices on the bus.

I've been using PCI-X SCSI's for a long while now.

---

### Post by Skripka on 2009-01-30
> **Frak said:**
> Mac's have been using PCI-X instead of PCI for as long as the G4 series, IIRC.

^^^^^^^
bit off topic

Not too surprised on the desktop side-the G5s and Mac Pros are built on server boards.  What better way to get a (perhaps ridiculously) powerful machine than to take a setup designed for server level throughput-and use it as a desktop ;)

I've actually though about it as a project from time to time.

---

### Post by Frak on 2009-01-30
> **Skripka said:**
> Not too surprised on the desktop side-the G5s and Mac Pros are built on server boards.  What better way to get a (perhaps ridiculously) powerful machine than to take a setup designed for server level throughput-and use it as a desktop ;)

I've actually though about it as a project from time to time.
Random thought, but since Teslas are starting to hit the scene, and Server boards are starting to look like Workstation boards, we may have multi-processor, multi-core, SLi capable server boards that support SCSI/SAS and plus when they come out with SCSI capable SSD's.

I can see it. Two Core i7's, two 280's in SLi, 32GB of FB-DIMM (Fully Buffered RAM).

Future is amoung us :).

---

### Post by Skripka on 2009-01-30
> **Frak said:**
> Random thought, but since Teslas are starting to hit the scene, and Server boards are starting to look like Workstation boards, we may have multi-processor, multi-core, SLi capable server boards that support SCSI/SAS and plus when they come out with SCSI capable SSD's.

I can see it. Two Core i7's, two 280's in SLi, 32GB of FB-DIMM (Fully Buffered RAM).

Future is amoung us :).

Let's see, this would need at least a full size tower, and a 2kW PSU to drive it...it would help to live north here-and put it outside and use Mother Nature as a heat dump.  Hmmmmmm....

---

### Post by Frak on 2009-01-30
> **Skripka said:**
> Let's see, this would need at least a full size tower, and a 2kW PSU to drive it...it would help to live north here-and put it outside and use Mother Nature as a heat dump.  Hmmmmmm....
Worth it.

---

### Post by andrewpmk on 2009-01-30
Go to College & Spadina, there's about two dozen computer stores there so you should be able to find what you are looking for.

---

### Post by dmizer on 2009-01-31
> **Skripka said:**
> [snip]it would help to live north here-and put it outside and use Mother Nature as a heat dump.  Hmmmmmm....

Or this? [http://www.newscientist.com/article/dn16512-thermal-computing-is-heating-up.html](http://www.newscientist.com/article/dn16512-thermal-computing-is-heating-up.html)

---

### Post by bonfire89 on 2009-02-04
> **andrewpmk said:**
> Go to College & Spadina, there's about two dozen computer stores there so you should be able to find what you are looking for.

hehe, yeah, that was my first place I looked. Though, I only really looked at Canada Computers because they are the only people around there that I feel I could return the card to if it didn't work. But they were out of them at the time. I suppose I will inquire about when they will get more in.

All the other places are too sketchy to have returns from what I have seen thus far at least.

Thanks for the reply.

---

### Post by handy on 2009-02-04
A PATA -> SATA adapter that plugs into one of your motherboard's IDE sockets wouldn't do the job for you?

---

### Post by bonfire89 on 2009-02-13
I didn't know such thing existed. VERY interesting!

buut, I do need to extend the number of slots.

---

