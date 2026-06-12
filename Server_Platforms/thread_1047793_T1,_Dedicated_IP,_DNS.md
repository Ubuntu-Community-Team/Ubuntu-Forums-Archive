---
title: "T1, Dedicated IP, DNS"
date: 2009-01-22
forum: Server Platforms
---

### Post by irishdunn on 2009-01-22
I have an ubuntu server sitting on my T1 connection. Right now I am just doing an a-record for each of my domain names to one of my T1's static IP's.

I would like to know if there is a guide or walkthrough on how to set up DNS to bind to my nameservers for my T1 company, and then I can stop using a-records for my domains.

Thanks!

---

### Post by geforce123 on 2009-01-24
Pardon me, but that was a strange sentence formulation ??

I don't really understand what you are trying to do ?

Record a certain DNS server for a domain ?



Phil

---

### Post by olivesandtrees on 2009-01-25
Your domains' nameservers should be controlled at your domains' registrar.  The nameservers listed on your registrar are the DNS servers where the actual active DNS record (whether it be A, MX, or the like) for your domain should be stored.

You should contact your ISP and ask them if they have managed DNS, and since you have a T1 connection this should be a resounding yes (I don't really know of any large companies that don't provide this service with a business level connection).  At this point let them know what DNS records you need then change over your registrar's nameserver entries to point at your ISP's nameservers.

Now, you will have no real need for a DNS server other than for internal resolution (I am guessing you are using NAT with you internal network).  The now internal DNS server should be setup to make any unknown request to be forwarded to DNS servers like OpenDNS @ 208.67.222.222 and 208.67.220.220

---

