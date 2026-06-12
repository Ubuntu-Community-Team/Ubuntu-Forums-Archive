---
title: "DNSSEC support"
date: 2012-07-17
forum: Security
---

### Post by old n grumpy on 2012-07-17
Hi there,

Could anyone tell me if the default (stub?) DNS resolver in Ubuntu (I suppose in Linux generally) is aware DNSSEC and to what extent?

Or more generally where the FOSS community stands in supporting DNSSEC from an end-user perspective. As far as I know there is a Firefox plugin...

I´ve heard rumors that Windows 8 will have DNSSEC (details?) support built in.

:confused:

---

### Post by fudoreaper on 2012-12-11
Hi,

I was looking for an answer to the same question, and using a 12.10 system.

I can tell you the following:

The system stub resolver doesn't ask for DNSSEC when sending a query to the nameserver. Therefore, the nameserver returns a result even when DNSSEC validity fails.

I can set the edns0 bit on outbound queries by adding "options edns0" to /etc/resolv.conf. I can't believe that's not default, by this time--the standard was published in 1999, as RFC 2671.

I am not aware of any option to turn on DNSSEC checking in the system stub resolver, but I am still looking.

So far, very disappointing to see the state of the system stub resolver is barely better than 1996.  It does support IPv6 nameservers, so that's one thing that it's not in the dark ages about.

I don't know who makes these decisions, but it would be interesting to have a conversation about this with whoever that group is.

---

### Post by samiux on 2012-12-11
DNSSEC will amplify the DDoS attack.  For details, please read [this article]("http://www.securiteam.com/securityreviews/5GP0L00I0W.html").

Samiux

---

