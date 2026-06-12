---
title: "Virus trojans going across networks"
date: 2007-11-17
forum: Server Platforms
---

### Post by fedex1993 on 2007-11-17
in it possible that trojans or malware on my laptop which is linux can it be passed onto my dekstop threw our network?

---

### Post by HermanAB on 2007-11-17
Of course.  Here you go:
$ scp evilvirus dumbuser@server:~/.
Password: dumbuserpassword

Cheers,

Herman

---

### Post by fedex1993 on 2007-11-17
but can they be transmitted from my laptop to my dektop even thoe i wont connect or anything

---

### Post by HermanAB on 2007-11-17
It is rather unlikely that a Linux PC will cause viruses to spread.  It would require human intervention, so it would need to be a deliberate act.

The exception is when you run a Linux machine as a mail server for a large number of windows clients.  In that case, it will pass whatever mail it receives on, unless you run SpamAssassin and ClamAV to remove the junk.  The Linux machine itself is however impervious to Windows viruses and therefore are very popular for use as mail servers.

Cheers,

Herman

---

