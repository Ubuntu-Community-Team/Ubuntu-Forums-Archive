---
title: "Help with Gadmin-proftpd"
date: 2010-10-08
forum: Server Platforms
---

### Post by JD32 on 2010-10-08
I'm trying to set up a home server with gamin and i've configured the server and added a user but when i activate i get this message (below). I've tried to restore th config files but i still get the same message.

Please help???


```
 - Fatal: TLSRSACertificateFile: '/etc/gadmin-proftpd/certs/cert.pem' does not exist on line 56 of '/etc/proftpd/proftpd.conf'


```

---

### Post by JD32 on 2010-10-10
bump

---

### Post by ganjan on 2011-05-07
bump !@@@@@@@@

---

### Post by xXOtherPeoplesWasteXx on 2011-05-10
Configure a 'Signing Certificate' from the 'Servers" setup section.

---

### Post by geidorei on 2011-05-25
Hi - just had same issue, thsi is what to do:

sudo gedit /etc/proftpd/proftpd.conf

And remove following (or comment them out by placing a # at the front of each line), all will be aok then, it worked for me:
TLSRSACertificateFile /etc/gadmin-proftpd/certs/cert.pem
TLSRSACertificateKeyFile /etc/gadmin-proftpd/certs/key.pem
TLSCACertificateFile /etc/gadmin-proftpd/certs/cacert.pem

Karl

---

