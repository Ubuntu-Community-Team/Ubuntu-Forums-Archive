---
title: "Can this be done over HTTPS?"
date: 2011-07-17
forum: Security
---

### Post by TimeDistort12 on 2011-07-17
Is it possible to provide encryption over HTTPS without a certificate?

I can't afford a certificate from a CA, but I do want to provide encryption with my website... without a self-signed certificate because I hate that screen popping up on the clients computer on first visits.

Is there another way it can be done?

---

### Post by bodhi.zazen on 2011-07-17
A self-signed certificate is the best option. Some sites offer free certificates, but I always use a self signed certificate. The only place a self signed certificate would be inappropriate would be financial transactions, and in that event purchase a certificate, they are not *that* expensive.

---

### Post by HermanAB on 2011-07-17
Use StartSSL.  It is just as bad as any other:
[http://www.startssl.com/](http://www.startssl.com/)

---

### Post by Dave_L on 2011-07-17
What about this:

How do I create a real SSL Certificate?
[http://httpd.apache.org/docs/2.0/ssl/ssl_faq.html#realcert](http://httpd.apache.org/docs/2.0/ssl/ssl_faq.html#realcert)

How do I create and use my own Certificate Authority (CA)?
[http://httpd.apache.org/docs/2.0/ssl/ssl_faq.html#ownca](http://httpd.apache.org/docs/2.0/ssl/ssl_faq.html#ownca)

---

### Post by HermanAB on 2011-07-18
The users will still get a warning the first time, because your CA is not in the browser already, unless you spoof an existing CA.

---

### Post by Dave_L on 2011-07-18
Yes, I would expect that. I was merely asking whether the apache.org article was correct.

---

