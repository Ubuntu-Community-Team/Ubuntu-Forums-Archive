---
title: "TLS not available due to local problem"
date: 2010-11-01
forum: Server Platforms
---

### Post by defaria on 2010-11-01
I'm trying to configure my server (Ubuntu 10.04) to use TLS when communicating over SMTP. I got a lot configured however when I try to STARTTLS I get "TLS not available due to local problem". 

How can I resolve this?

---

### Post by defaria on 2010-11-04
Regenerated my keys as per [https://help.ubuntu.com/community/OpenSSL#SSL](https://help.ubuntu.com/community/OpenSSL#SSL) Certificates and got it working. However...

I'm using Thunderbird on my 64 bit 10.04 desktop and tried configuring it to use STARTTLS does not work. On my cell phone (Android based) I can set the outgoing SMTP to use my server with TLS (There's settings for None, SSL and TLS) and I got a warning that the cert wasn't properly signed (I think - some kind of cert error - but was able to OK it and contiue. With my desktop however, Thunderbird just complains "An error occurred during a connection to <server>:465. Peer's certificate has an invalid signature. (Error code: sec_error_bad_signature)". Note that Thunderbird only has settings for "None", "STARTTLS" and "SSL/TLS".

Is there a fix for this?

---

### Post by ffree on 2011-03-06
I had this prob in Rails 3 on Ubuntu 10, and got into admin spiral pretty quick.
My fastest fix: apt-get install sendmail
after that, all was immediately well. postfix was not work worth the new hassles.

---

