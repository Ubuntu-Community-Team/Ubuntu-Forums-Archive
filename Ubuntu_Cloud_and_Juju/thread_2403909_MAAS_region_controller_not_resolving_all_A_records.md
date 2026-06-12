---
title: "MAAS region controller not resolving all A records in zone it created and manages"
date: 2018-10-17
forum: Ubuntu Cloud and Juju
---

### Post by bigtexun on 2018-10-17
I have been working with MAAS successfully for a couple years.  I implemented a new cloud stack from scratch 3 weeks ago, and everything worked correctly right out of the box.  I racked up servers over a 3 day period, due to not having all of the parts do do it all on the same day.  So as a result the stack grew over a several day period.

After being up for around 2 weeks, my region controller started dropping machines out of DNS.  It seems to be dropping them in the order they were added, and I think it started dropping them around 2 weeks after they were comissioned.

Using the web UI to view the DNS zone, I see that all of my A records that were automatically created are still in the zone.  However the only record that resolves is the A record for the region controller itself.

The first time I implemented MAAS, DNS didn't seem to work at all, so I managed DNS outside of MAAS.  However there were many disadvantages to that approach, so when I installed this new stack, I created a zone just for the MAAS stack, and was very happy that it worked perfectly.

I don't know if the timing was exactly 2 weeks, but the order the machines started failing does appear to be the same order they were comissioned, so it feels like some sort of timeout is involved.  It feels like what happens when you have a caching DNS server that continues resolving a zone for a DNS server that is down until the TTL expires.  The problem of course this is not a caching server resolving a remote zone, this is a local server dropping local entries that still appear in the zone file.

I'm running a fresh MAAS version 2.4.2 (**7034-g2f5deb8b8-0ubuntu1), running on a fresh Ubuntu 18.04.1 LTS, and I have applied updates since this problem started, in case there was a fix in an update.**

How can I get MAAS to reload the records that show in the webUI?  How can I make them persistent?  I'm sure this is a bug, and they are supposed to already be persistent, but I would expect other people to be experiencing the issue.  The default TTL is only 1000, so I don't think it is a TTL issue, I think it just feels like TTL issues I have seen in the past.

---

### Post by bigtexun on 2018-10-17
Upon deeper inspection, I see that the bind zone files look good, and are loaded with the expected data.

/etc/resolv.conf  is pointed at 127.0.0.53 which is not answering.  When I point it at  the local ethernet IP address, suddenly I can resolve things that are in  the zone file on the local system (region controller).  So part of the  problem is it is not answering the local queries.  Not sure why that  works, but it doesn't work from the rest of the corporate nameservers  yet.  

It feels like I have two different problems...  Bind is  not answering on 127.0.0.53, and on the ethernet IP it is not answering  for the corporate nameservers.

---

### Post by sunnywty on 2018-10-29
Try to restart bind9.service and then observe its status. Remember to configure the DNS forwarder and disable DNSSEC validation of upstream zones. I have stuck on the DNS issue for three days and finally make it fully working.

---

