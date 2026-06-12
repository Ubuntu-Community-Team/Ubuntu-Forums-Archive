---
title: "free ssl certificate?"
date: 2011-09-07
forum: Server Platforms
---

### Post by micdhack on 2011-09-07
I finally managed to set the ssl for apache2 but when i broswer with firefox i get a warning!
For the certificate i used [https://www.cacert.org](https://www.cacert.org) but apparently it is not recognized by firefox.

Do you know any free websites that give valid ssl certificates?

---

### Post by Grenage on 2011-09-07
No, I'm not aware of any.  Places such as godaddy (never used them) provide some of the better prices, apparently.

---

### Post by rubylaser on 2011-09-07
A recognized Certificate Authority is always going to cost money.  You can self sign your certs, and then add your cert in Firefox in Advanced > Encryption > View Certificates.

The "Servers" tab will let you add exceptions or import certificates. The "Authorities" tab will let you add new authorities.

But, if this is for a public site, you'll want to spend the ~ $70/yr (GoDaddy) and get a signed cert so your visitors aren't confused / scared away by invalid SSL Certificate warnings.

---

### Post by HermanAB on 2011-09-08
You can get free certs from Startcom.

---

### Post by BkkBonanza on 2011-09-08
Yes, [startssl.com]("http://startssl.com") is good and free too. Recognized by browsers and I've used in the past without problems.

(startssl.com same as startcom)

They're the only CA that offers what I consider to be reasonable pricing. If you buy a commercial cert from them then you can get unlimited (as many as you need) with any domain you control for the one price. And that includes wildcard domains except for the Extended Validation certs, and even those aren't a ridiculous $1500 price tag like that other well known brand.

---

### Post by rubylaser on 2011-09-08
> **HermanAB said:**
> You can get free certs from Startcom.

Thanks for sharing.  I learn something new everyday.

---

