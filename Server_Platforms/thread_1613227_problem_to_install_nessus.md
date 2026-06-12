---
title: "problem to install nessus"
date: 2010-11-04
forum: Server Platforms
---

### Post by oren tal on 2010-11-04
I want to install nessus.
I run the following in the terminal:

sudo apt-get install nessus

I get a message that the package is not available and anther package replace it.
However I am interested in nessus  and not in openvas-client (the other package.

So how can I get the nessus package.

---

### Post by TSJason on 2010-11-04
oren,

A quick search of apt reveals that the package name for nessus is actually "harden-remoteaudit" - try installing that one.

```
jhamilton@C9H13NO3:~$ apt-cache search nessus
harden-remoteaudit - Audit your remote systems from this host
jhamilton@C9H13NO3:~
```

---

### Post by polyanskinn on 2011-08-29
[SIZE=4]Run Ubuntu Softwre Center, search[/SIZE][SIZE=4] harden-remoteaudit and install it:

Go to [http://www.nessus.org](http://www.nessus.org), click Downloads and register the program for Home users:

Then open your email and follow the steps to activate:

Thanks
[/SIZE]

---

### Post by Dangertux on 2011-08-29
Interesting side note...Does anyone here remember when Nesuss was free? I mean like completely free for commercial use?

I feel old :-(

---

### Post by raffen on 2011-09-08
> **Dangertux said:**
> Interesting side note...Does anyone here remember when Nesuss was free? I mean like completely free for commercial use?

Yes I do. Back in 2002 or something..

---

### Post by Lars Noodén on 2011-09-08
> **Dangertux said:**
> Interesting side note...Does anyone here remember when Nesuss was free? I mean like completely free for commercial use?

I feel old :-(

Yes.

IIRC, [OpenVAS](http://www.openvas.org/) was a fork of the last free and open source version of Nessus.  OpenVAS is in the Ubuntu repositories.

---

