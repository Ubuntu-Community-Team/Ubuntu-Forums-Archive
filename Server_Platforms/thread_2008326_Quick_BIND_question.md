---
title: "Quick BIND question"
date: 2012-06-22
forum: Server Platforms
---

### Post by linuxmunky on 2012-06-22
Just curious - is BIND set to forward requests by default?  I set up my server last night as a primary master only for my network (home.lan) and it started up no problems, but when I ran some nslookups and pings, I was able to reach google.com and yahoo.com.  I thought those requests would fail without me setting up caching / forwarders?

Thanks in advance - happy Friday all!

---

### Post by SeijiSensei on 2012-06-23
No, your server will resolve all names with or without forwarding enabled.

If there's no forwarding, requests are sent to one of the root servers authoritative for the top-level domain like ".com" or ".uk".  The root tells your server the identity of the nameserver authoritative for the specified domain, e.g., "example.com".  Your server then directs queries to that server in order to resolve "www.example.com" or to identify the MX servers that accept mail for the "example.com" domain.  Your server also builds a local cache of resolved queries that expire depending on the expiry settings in the domain's SOA record.

A forwarder simply sends all requests to another server for resolution then caches the results its receives to improve performance.

Is that clear enough?

Do you want to block your server from making external queries and have it be authoritative for only your local domain?  That's possible, but I doubt that's what you want to do.

---

### Post by linuxmunky on 2012-06-23
Thank you so much, that's crystal clear!  Is there a recommended or "best practice" approach to root servers vs. forwarding?  I know I could forward to OpenDNS (my ISP's DNS servers are iffy), but would like to know which approach is best.  And you're right, I don't want to block external queries, I was just curious how it all worked.

---

### Post by SeijiSensei on 2012-06-23
If you're on a slow connection, it might make sense to use the ISP's servers.  I never use forwarders except in a few unusual cases.  I have clients with in-house nameservers that provide a view of their internal networks.  I also have OpenVPN virtual networks established with them so I am connected directly and can query these internal DNS servers.  On my office DNS server I maintain zone files for these clients' domains, including any reverse in-addr.arpa domains, that forward all queries to my clients' nameservers.  Otherwise I just ask the roots.  

One reason not to use forwarding is if you need to refresh your view of the DNS after updating a domain's records.  Because DNS changes don't propagate immediately, an upstream forwarder may not recognize any changes you make to your public records for as long as 48 hours in practice.  I can avoid this problem by maintaining a local DNS server that talks to the roots directly,  If I restart bind9 and clear its cache, the server will start using the updated records when asked to resolve hostnames like "www.example.com".  If I used forwarders I'd have to wait until their cached records expired.

---

### Post by linuxmunky on 2012-06-23
Great points - I agree with you completely.  Thanks again Seiji.

---

