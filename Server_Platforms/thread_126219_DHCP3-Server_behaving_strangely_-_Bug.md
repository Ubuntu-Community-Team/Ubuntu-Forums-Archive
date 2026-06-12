---
title: "DHCP3-Server behaving strangely - Bug?"
date: 2006-02-06
forum: Server Platforms
---

### Post by nverhaar on 2006-02-06
Hi all,

I have been running DHCP3-SERVER on ubuntu hoary 5.04 for the last 6 months without any problems, and I have recently moved it to a newer server running ubuntu breezy 5.10. I copied the dhcpd.conf and dhcpd.leases files exactly as they were on the old server, however I am noticed VERY strange behaviour.

Clients can connect fine and obtain an IP address, Dynamic DNS tied in to BIND9 appears to be working flawlessly as well. However, rather than renewing the existing lease upon restart of client machines, they are obtaining a completely new lease and new IP address.

In all the time I have used DHCP3-SERVER it has never done this to me until moving to it over to Breezy, and has become extremely annoying.

I have set min, max, and default lease times to 30 days, and still I see clients are given a new IP within minutes of obtaining a lease.

Does anyone have any ideas or solutions, or is DHCP3-SERVER known to be buggy on Breezy?!

---

### Post by ::DoGG:: on 2006-02-06
You are using EXACT the same version of server softwar eYou were using before ???

---

### Post by nverhaar on 2006-02-06
I was previously doing DHCP on 5.04 Hoary, but have now moved it to a newer servering running 5.10 Breezy. These are the software versions:

5.04 Hoary
dhcpd3-server - Internet Systems Consortium DHCP Server V3.0.1

5.10 Breezy
dhcpd3-server - Internet Systems Consortium DHCP Server V3.0.2

I have tried everything I can think of but it is still assigning new leases every time, rather than renewing existing leases. Im tearing my hair out over here, can anyone help me?!

---

### Post by nverhaar on 2006-02-07
Oh come on, dont tell me NOBODY here uses DHCP?!

Someone must have this problem!!

---

### Post by nverhaar on 2006-02-12
Bump!@

---

### Post by Glut on 2006-02-13
Why does the recycling of IP addresses concern you? Should you be using static leases?

---

