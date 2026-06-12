---
title: "Dovecot posting information in header"
date: 2007-07-30
forum: Server Platforms
---

### Post by pivotter on 2007-07-30
Hi,
My Dovecot header output:

IMAP 143/TCP

Unknown services banners
An unknown server is running on this port.
Type=spontaneous
0x00: 2A 20 4F 4B 20 4C 69 76 69 61 0D 0A * OK Dovecot Ready.

And if I enable, login_greeting_capability = yes

* OK [CAPABILITY IMAP4rev1 SASL-IR SORT THREAD=REFERENCES MULTIAPPEND UNSELECT LITERAL+ IDLE CHILDREN NAMESPACE LOGIN-REFERRALS STARTTLS AUTH=PLAIN AUTH=LOGIN AUTH=DIGEST-MD5 AUTH=CRAM-MD5] Dovecot ready.

7.04 Feisty 
Dovecot 1:1.0.0-1 

So, i disabled  login_greeting_capability,
but i can't get rid of the 0x00: 2A 20 4F 4B 20 4C 69 76 69 61 0D 0A *

Question: is this a normal and safe output for a IMAP header ? 

Cheers

Pivotter

---

