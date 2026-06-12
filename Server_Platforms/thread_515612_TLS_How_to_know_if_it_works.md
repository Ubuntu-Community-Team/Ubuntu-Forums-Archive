---
title: "TLS How to know if it works?"
date: 2007-08-02
forum: Server Platforms
---

### Post by guilly on 2007-08-02
Hi guy's,

I installed TLS last night on my ftp server by following the how to guide on here with proftpd. Anywayas i was able to successfully connect but i would like to know how to find out if TLS is actually working? I'm using gftp to connect and i could not find an option in there to disable encryption, and i also looked into the /var/proftpd/tls.log to see if i could find some type of log entry after i had connected but was also unsuccessful at finding anything? does it only log unsuccessful attempts?

thanks

---

### Post by guilly on 2007-08-02
54 hits an nobody knows???

---

### Post by Mr. C. on 2007-08-03
Run tcpdump on the interface that is listening, and watch the packets. If you can read the contents, the connection is not TLS.  If it is encrypted, you won't be able to read it.

MrC

---

