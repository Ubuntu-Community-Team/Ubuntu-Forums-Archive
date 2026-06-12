---
title: "Courier Dependencies Missing?"
date: 2012-08-25
forum: Server Platforms
---

### Post by 1-Up on 2012-08-25
I've been working on setting up an email server based on this guide: [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

I have postfix working with send and receive mail.

Courier, however, is not working.  When trying 'telnet localhost 143' it instantly closes the connection after connecting.

The mail.log gives this error: "/usr/lib/courier/courier/imaplogin error while loading shared libraries libcourierauth.so: cannot open shared object file: no such file or directory."

How can I go about correcting this?

---

### Post by 1-Up on 2012-08-26
I messed something up with courier.

I fixed this problem by doing a apt-get --purge remove courier-authlib, then reinstalling all courier packages.

---

