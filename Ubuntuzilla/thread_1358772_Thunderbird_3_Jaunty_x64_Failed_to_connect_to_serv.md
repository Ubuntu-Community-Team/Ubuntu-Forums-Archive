---
title: "Thunderbird 3 Jaunty x64: Failed to connect to server"
date: 2009-12-18
forum: Ubuntuzilla
---

### Post by dbc001 on 2009-12-18
I just installed Ubuntuzilla to get Thunderbird 3.0. It seems to have installed fine, but when I run Thunderbird it simply says "Failed to connect to server mail.xxx.com".

If I uninstall TB3, Thunderbird 2 works just fine.  I'm using Dreamhost for my mail, using IMAP.  Anyone else experiencing this issue?

Thanks in advance,
dbc001

---

### Post by nanotube on 2009-12-19
Hi

Hmm, well, could be the same issue that seems to crop up with 64bit users with firefox.

try going to the detailed config editor (edit -> preferences -> advanced -> general -> config editor button), and set "network.dns.disableIPv6" to true, and see if that helps.

---

### Post by dbc001 on 2009-12-20
That worked perfectly, thanks!

---

### Post by nanotube on 2009-12-20
> **dbc001 said:**
> That worked perfectly, thanks!

cool :)

---

### Post by DeMus on 2009-12-31
> **nanotube said:**
> Hi

Hmm, well, could be the same issue that seems to crop up with 64bit users with firefox.

try going to the detailed config editor (edit -> preferences -> advanced -> general -> config editor button), and set "network.dns.disableIPv6" to true, and see if that helps.

Thanks, I really thought I had to go back to T'bird 2. Still 64 bits is a problem for many problems. When will this finally be fixed? I mean 64-bit processors are so old already and still the software is not ready for it.
Well, thanks again, it now works.

---

