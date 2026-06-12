---
title: "Panda AV and firewall"
date: 2006-05-15
forum: Server Platforms
---

### Post by slimdog360 on 2006-05-15
On the panda software site
[http://www.pandasoftware.com/download/beta/particulares/?sitepanda=particulares](http://www.pandasoftware.com/download/beta/particulares/?sitepanda=particulares)
they have an AV and firewall for free. Although I havent used it yet it looks pretty good, though its still in beta. Im planning on giving it a try out on the weekend. the download's about 90MB
I just thought id post this up here in case anyone was interested.

---

### Post by localzuk on 2006-05-15
May I ask why you want a memory hogging, cpu hogging active scanning anti virus scanner on your computer? Why not use clamav? It is open source.

Also, on the firewall front, why not just use the built in firewall capability of the Linux kernel via iptables? (All you have to do is install a front end for it).

---

### Post by RavenOfOdin on 2006-05-15
Panda AV is crap, for the reasons stated above.

---

### Post by slimdog360 on 2006-05-16
[QUOTE=localzuk]May I ask why you want a memory hogging, cpu hogging active scanning anti virus scanner on your computer? Why not use clamav? It is open source.

Also, on the firewall front, why not just use the built in firewall capability of the Linux kernel via iptables? (All you have to do is install a front end for it).[/QUOTE]
Settle down buddy, I was just trying to give some choice.

---

### Post by localzuk on 2006-05-16
Heh, I am perfectly calm :) I am just asking why people would choose to use a closed source product with many problems over an open source product (which is included in Ubuntu by default)?

---

### Post by az on 2006-05-16
Under what licence is this application?  On the bottom of the page it says:

Free software
Panda DesktopSecure for Linux includes or may include software programs that are licensed to the user under General Public License (GPL) or other similar free software license, which require that the source code is made available to the licensee. The licensee may access the source code of this software from the following link.

I would be interested in knowing of what is running what is proprietary and what is free-libre.  Is it possible to remove all proprietary bits from this and still use it?  


Not that most people running Ubuntu need an antivirus, just those who happen to operate a mail server on it.  And that, to protect others from harm.

---

### Post by Lord Illidan on 2006-05-16
I wouldn't try Panda. It sucked even in Windows, just imagine in Linux.

Clam AV is said to be pretty good. There is also kapersky.

As for firewalls, Linux already has some good firewall in the form of IPtables.

---

### Post by localzuk on 2006-05-16
It appears that it contains 4 GPL libraries and app:

libesmtp
libzzip
mailutils
snort

So I would guess that, no, it won't work without the proprietory tools. But you could craft your own using those libs, clamav, iptables and firestarter (or similar iptables frontend)...

---

### Post by missmoondog on 2006-08-05
i just had this show up as new in synaptic. debated on getting it, but thought i'd see what there might be in the forums about it. not much, but enough to tell me i don't need it.

---

