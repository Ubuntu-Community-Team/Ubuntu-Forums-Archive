---
title: "Securing Apache Webserver"
date: 2008-07-09
forum: Security
---

### Post by chrislynch8 on 2008-07-09
Hi,

What is the best and most secure method of setting up my Apache website to be accessed over https.

Is there a simple step by step guide to securing Apache?

Rgds
Chris

---

### Post by cdenley on 2008-07-09
This depends on whether you want to buy an SSL certificate signed by a certificate authority, or if you would settle for a self-signed certificate.

---

### Post by chrislynch8 on 2008-07-09
As it will only be our staff that will access this site a self signed cert would be sufficient assuming I still have control over the encryption bit length etc.

---

### Post by cdenley on 2008-07-09
[https://help.ubuntu.com/community/forum/server/apache2/SSL](https://help.ubuntu.com/community/forum/server/apache2/SSL)

---

### Post by chrislynch8 on 2008-07-09
Thanks for that.

All the googling I never entered + Ubuntu. :oops:

Rgds
Chris

---

### Post by Dr Small on 2008-07-09
Yeah, you probably just want a self-signed certificate for the encryption. That's what I do. Phewy with authorized certificates.

---

### Post by chrislynch8 on 2008-07-09
Ok,

I have that working now.

Just a quick question is there any guideline to the bit encryption to use before security really affects connectivity?

Rgds
Chris

---

### Post by chrislynch8 on 2008-07-09
> **Dr Small said:**
> Yeah, you probably just want a self-signed certificate for the encryption. That's what I do. Phewy with authorized certificates.

I feel the same way - but I created a cert and key using 2056 bit key with AES-256bit encryption, I think this might be overkill and will affect the response time of the site (which will be a CRM).

---

