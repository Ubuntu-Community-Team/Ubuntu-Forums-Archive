---
title: "postfix security certificates  -  how to change ?"
date: 2009-08-20
forum: Server Platforms
---

### Post by cbear on 2009-08-20
I am getting errors from thunderbird every time I access my mailer server because the domain name I am connecting to does not match the domain name of the linux server.  How do I change the security certificate on the linux server (postfix I assume) ?

---

### Post by giggins on 2009-08-20
By far, the simplest way to fix it is to connect to the server using the domain you setup in the certificate.

If that doesn't work (maybe the domain is invalid), you can create a new certificate. You will still have issues if that certificate is signed by a CA that your machine does not trust (such as a self-signed certificate). [This page]("https://help.ubuntu.com/community/Postfix#Configuration") (under the configuration section) shows you how to create a new, self-signed certificate, and how to use in with Postfix.

If you want to generate a CSR that can be signed by a third-party CA (such as Thawte or Verisign), you can use the following to generate the csr and key:

```
openssl req -new -nodes -keyout smtpd.key -out smtpd.csr -days 365
```Use the contents of smtpd.csr to get a signed cert, and use smtpd.key as the keyfile (note: its NOT ENCRYPTED, so keep it somewhere safe).

---

### Post by cbear on 2009-08-23
problem is, the domain in the certificate is no longer valid.  Seems to have been auto-generated a long time ago and contains the domain of an ISP I don't even use anymore.  The domain in the signiture is listed as:

LINUX03.hsd1.comcast.ca.net

my machine is now on a static IP thru AT&T and my mail clients map straight to it at:  [www.boxb29.com](www.boxb29.com)

So, changing the client to point to LINUX03...blah blah...won't work since that is a bogus address these days.

---

### Post by giggins on 2009-08-24
Did the other options I mentioned (creating a self-signed cert or a CSR) help?

---

