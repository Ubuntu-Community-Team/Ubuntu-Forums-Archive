---
title: "DNS addreses changing automatically"
date: 2010-08-09
forum: Ubuntu Studio
---

### Post by mavapor on 2010-08-09
Hi!

I having problems with my DNS severs.

I can change the adresses to Google DNS numbers, but the system automatically change them back every time!

How can i fix this?

Thanks

Sorry the bad English.

---

### Post by ghostborg on 2010-08-09
I'm assuming it changes back to Auto ETH0 when you reboot.
You can right click on the Network Icon and select edit connections.
Choose the connection to edit and click on the Edit button and check the box Connect automatically and click apply.
Inspect your other connections to make sure the Connect automatically boxes are unchecked.

One thing is that I am unable to connect to other computers on my Home network when anything but Auto eth0 is used for DNS.

So I leave mine as Auto eth0 by default and simply left click on the Network Icon and select the DNS server to use.
Some people just setup there router to do this so all machines use it. OpenDNS is free check them out too. OpenDNS.com .

---

