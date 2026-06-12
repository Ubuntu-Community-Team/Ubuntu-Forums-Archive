---
title: "What are the dangers of using hand rolled site certificates??"
date: 2008-12-12
forum: Security
---

### Post by mozkill on 2008-12-12
I can't find any specific information on the internet and so I thought I would ask this question.  What are the dangers of using hand rolled site certificates??

If a company were to use hand rolled certificates rather than certificates issued by a recognized and insured certificate issuer, what kinds of things might go wrong?

---

### Post by Dr Small on 2008-12-12
"hand rolled" as in "Self-Signed certificates"?
The dangers? Well, it's just not authorized by a verified legitimate company, is all. It in no way signifies that the information is *not* encrypted to the host.

I don't worry about self-signed certificates myself, since I have my own. Alot of folks just use them for the added comfort of encryption to the server for their users, and most are legitimate sites.

---

### Post by lykwydchykyn on 2008-12-12
Well, for one thing, visitors to your site will get a big ugly security warning telling them you're using and unverified security certificate and might not be who you claim to be.  Not very reasurring if you're doing something like eCommerce.

Otherwise, you make yourself vulnerable to a man-in-the-middle attack. [http://en.wikipedia.org/wiki/Man-in-the-middle_attack](http://en.wikipedia.org/wiki/Man-in-the-middle_attack)

---

### Post by bodhi.zazen on 2008-12-13
Well I always figured the biggest draw back to a self-signed cert was spoofing.

---

