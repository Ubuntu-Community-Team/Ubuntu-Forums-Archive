---
title: "ipv6 readiness"
date: 2011-01-13
forum: The Cafe
---

### Post by josephellengar on 2011-01-13
Hi. I failed the ipv6 readiness test. What exactly does this mean for me? Is it due to my ISP? If so, will I be unable to browse sites on World ipv6 Day?

---

### Post by Austin25 on 2011-01-13
I failed, too. It just means your isp isn't providing IPv6.

---

### Post by Phrea on 2011-01-13
Did you guys do this one: [http://areyou.v6ready.info/](http://areyou.v6ready.info/) ?
It says I'm not ready either.

---

### Post by josephellengar on 2011-01-13
> **Phrea said:**
> Did you guys do this one: [http://areyou.v6ready.info/](http://areyou.v6ready.info/) ?
It says I'm not ready either.

I originally used a different one, but that one says I'm not ready also. I guess there's not much to worry about if only 5% of people are ready.

---

### Post by RandomJoe on 2011-01-13
That test isn't necessarily true, in my opinion.  My home network is what I would consider "IPv6 ready" - I have v6 addresses, have radvd running internally, and can connect to v6-only sites.  (Via a 6to4 tunnel, ISP isn't ready yet.)

However, their test says you aren't v6-ready unless your browser prefers v6 over v4, which Firefox and OS X do not.  So it says I'm "not ready".  

Seems rather silly to me - I meet all their other requirements.  If they tried a domain that had ONLY a v6 address, it would work just fine.

Although I'm annoyed by the "prefer v4 by default" too.  IIRC I found how to change that on Firefox, but I can't change OSX' behavior as far as I know...

---

### Post by samalex on 2011-01-13
The site lists a few things it checks, so it'd be nice if it put tick marks next to the ones that passed and failed. I'd be curious to know what I need to do to become IPv6 compliant since I have LOTS of old stuff around my house yet I know IPv6 is coming someday.

Update: Here's a few more I found that give more feedback 
- [http://test-ipv6.com/](http://test-ipv6.com/)
- [http://ipv6-test.com/](http://ipv6-test.com/)

Test with IPv4 DNS record - ok (0.453s) using ipv4
Test with IPv6 DNS record - bad (0.183s)
Test if your ISP's DNS server uses IPv6 - bad (0.264s)
Test with Dual Stack DNS record - ok (0.426s) using ipv4
Test IPv4 without DNS - ok (0.273s) using ipv4
Test IPv6 without DNS - bad (0.061s)
Test IPv6 large packet - bad (0.084s)

I guess there's not much I can do if it says my ISP isn't compliant...

---

### Post by Phrea on 2011-01-13
```
Test with IPv4 DNS record	 	ok (0.460s) using ipv4
Test with IPv6 DNS record	 	ok (0.490s) using ipv4
Test if your ISP's DNS server uses IPv6	 	bad (0.497s)
Test with Dual Stack DNS record	 	ok (0.488s) using ipv4
Test IPv4 without DNS	 	ok (0.988s) using ipv4
Test IPv6 without DNS	 	bad (0.026s)
Test IPv6 large packet	 	ok (0.972s) using ipv4
```

Whatever above posted means. :D

---

### Post by lemming465 on 2011-04-18
> **Phrea said:**
> Test with IPv4 DNS record	 	ok (0.460s) using ipv4
DNS query for "A" record (IPv4 address) over IPv4 transport.
> Test with IPv6 DNS record	 	ok (0.490s) using ipv4
DNS query for "AAAA" record (IPv6 address) over IPv4 transport.
> Test if your ISP's DNS server uses IPv6	 	bad (0.497s)
Does your upstream DNS server have an AAAA (IPv6) address as well as an "A" (IPv4) address?
> Test with Dual Stack DNS record	 	ok (0.488s) using ipv4
Can you get back both "A" and "AAAA" records for a dual-stacked site from your DNS server?
> Test IPv4 without DNS	 	ok (0.988s) using ipv4
Make a direct IPv4 connection to an IPv4 address, without using DNS.  This tests IPv4 transport.
> Test IPv6 without DNS	 	bad (0.026s)
Make a direct IPv6 connection to an IPv6 address, without using DNS.  This tests IPv6 transport.  If it fails, you are v4-only.  If it works, you might be using tunneled v6 (OK, but not the best) or native v6 (best).
> Test IPv6 large packet	 	ok (0.972s) using ipv4
The minimum size an IPv6 network has to support is 1280 byte packets.  If you can't get packets that large through your ISP, v6 won't work.

---

