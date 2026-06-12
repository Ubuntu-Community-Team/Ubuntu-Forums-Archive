---
title: "Possible to have home partition on NFS server?"
date: 2008-07-02
forum: The Cafe
---

### Post by markp1989 on 2008-07-02
I have the following computers.

Desktop:3.2ghz 2gb 80gb and 160gb
Laptop:1.5ghz 1gb 40gb Laptop 2 asus eee pc 4gb
torrentslave/nfs/daap server:1ghz athlon 1gb ram 160gb
Divxbox: 866mhz 128mb 1gb CF 

I was thinking of getting a cheap sata card for the torrent slave. and moving the 2 hard drives from my desktop pc to the torrent slave.

Then install ubuntu on  a 2gb CF card (root partition read only in squashfs) in the desktop PC, and have the home partition stored on the Torrent slave, being accessed using NFS.

a few questions:
how cheap can i get a PCI SATA (with 2 internal sata ports) card that works out of the box with linux? 

will i notice any lag if i have the home partition on a network share (100Mb Wired) I only use the home partiton to store settings , not larger files?



Thanks MarkP1989

---

### Post by LaRoza on 2008-07-02
> **markp1989 said:**
> 
how cheap can i get a PCI SATA (with 2 internal sata ports) card that works out of the box with linux? 

Well, as cheap as you can find. I don't think you'd have a problem using any of them, but you might want to check out the forum to see.

---

### Post by Lostincyberspace on 2008-07-03
I got mine for 30.

It is from Manhattan (the company not the city)
[http://www.manhattan-products.com/driver-mercury-ataraid.shtml](http://www.manhattan-products.com/driver-mercury-ataraid.shtml)
It is the raid card with the 2 internal ports.

Using it in windows is tricky though so if you dual boot be prepared to wait a while while you get every thing set up..

---

### Post by markp1989 on 2008-07-03
> **Lostincyberspace said:**
> I got mine for 30.

It is from Manhattan (the company not the city)
[http://www.manhattan-products.com/driver-mercury-ataraid.shtml](http://www.manhattan-products.com/driver-mercury-ataraid.shtml)
It is the raid card with the 2 internal ports.

Using it in windows is tricky though so if you dual boot be prepared to wait a while while you get every thing set up..

I dont want to set it up using raid, because the drive sizes don't match, if i get one that supports raid, will i be able to use it with out raid?


does any one know if this card will work using linux?
[http://cgi.ebay.co.uk/3-Port-SATA-1-Port-IDE-PCI-RAID-Controller-Card-B117_W0QQitemZ230265995791QQcmdZViewItem?hash=item230265995791&_trkparms=39%3A1%7C65%3A2&_trksid=p3286.c0.m14](http://cgi.ebay.co.uk/3-Port-SATA-1-Port-IDE-PCI-RAID-Controller-Card-B117_W0QQitemZ230265995791QQcmdZViewItem?hash=item230265995791&_trkparms=39%3A1%7C65%3A2&_trksid=p3286.c0.m14)

it has a Via-VT6421A chip,  dont know if that will work or not?

---

