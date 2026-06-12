---
title: "Please help me understand my security certificates in Firefox."
date: 2012-06-29
forum: Security
---

### Post by zozza on 2012-06-29
I was looking at Firefox Preferences / Encryption / Certificate Manager / Authorities.

This seems to contain a list of all certificates that Firefox deems secure.

However, in Certificate Manager / Servers there are also some more certificates.

These are:

DigiNotar (DigiNotar Cyber CA / DigiNotar Root CA / DigiNotar Services 1024 CA) - "explicitly distrust DigiNotar CA" (presumably due to the well-publicized security breach).
Entrust.net (DigiSign Server ID - (Enrich)) - "explicitly distrusted Malaysian Digicert Sdn. Bhd. (en)" (because of [http://www.digicert.com.my/](http://www.digicert.com.my/) - clarification statement).
GTE Corporation (DigiSign Server ID (Enrich)) - "explicitly distrusted Malaysian Digicert Sdn. Bhd. (cyb)"

I don't understand the difference between these invalidations.  The DigiNotar CA was invalidated.  However, I don't see what has been invalidated with Entrust and GTE.  It's not the CA is it?  Also, if, in both cases, Enrich was invalidated then why are there two entries (one for Entrust and one for GTE)?

Thanks!

---

