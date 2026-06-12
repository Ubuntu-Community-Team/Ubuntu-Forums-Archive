---
title: "Self Signed Cert in Postfix"
date: 2009-06-27
forum: Server Platforms
---

### Post by drhiii on 2009-06-27
How can I disable the self signed certificate in Postfix.  There is a small group of people using a postfix mail server and everyone is having to click to accept the self signed cert EVERY TIME they check for email.  I had always seen in the past, accepting the certificate, and it goes away.  But this is asking every Check Mail, for everything.

How can I either disable this (I tried disabling TLS, I know I know, but it is a small group... but that did not work).  Am trying to figure out how to just use a plain text login, but have not been able to get that working.  Driving me a bit nuts.

I could go out and get an authoritative cert which may be the thing, but for such a short list, kinda am avoiding that.  

Help anyone.

---

### Post by drhiii on 2009-06-28
I've been able to obtain an Outlook installation and it indeed queries EACH time Outlook looks at the unsigned certificate, giving the security warning, to check for mail on this Postfix installation.

How in the world can I get rid of this certificate warning?  Having it pop up each time is like, nuts.  But I have not been able to figure out a way around it.  

Help.

---

### Post by drhiii on 2009-06-28
No one?

---

