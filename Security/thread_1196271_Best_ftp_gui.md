---
title: "Best ftp gui?"
date: 2009-06-24
forum: Security
---

### Post by ruipedroca on 2009-06-24
I've chosen to create this thread in Security because my question is VPN related.

So here it is:
Imagine x computers (clients), all ubuntu's, in x different cities, that communicate only with another computer (server), also ubuntu, at a different city, within an ipsec VPN configured at router level.
If you wanted to aloud users to exchange files within some predefined rules/folders, would you use ftp? In so, what gui ftp would you advise?

---

### Post by norman_ on 2009-06-24
you seem to be talking about a ftp client. If so, my favorite is filezilla. Much of the reason why hangs on the fact that it is cross-platform and quite intuitive.

---

### Post by HermanAB on 2009-06-25
You don't need a FTP GUI, since you already got one.  Open  the file manager Nautilus (your Home icon) and click File, Connect to Server.

La voila!

---

### Post by bodhi.zazen on 2009-06-25
I suggest gftp

---

### Post by ericab on 2009-06-25
filezilla for life

---

### Post by ZeldeR on 2009-06-25
filezilla :) or MC

---

### Post by ruipedroca on 2009-06-25
Sorry guys, but i was referring to the server version! :---)

---

### Post by bodhi.zazen on 2009-06-25
Server side I advise ssh (scp / winscp).

If your ftp is available only on your VPN you should be fine.

If you must use ftp , use a hardened version if you can , such as vsftp

---

### Post by HermanAB on 2009-06-26
BTW, Filezilla is both a Server and a Client.

---

