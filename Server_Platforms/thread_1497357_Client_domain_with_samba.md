---
title: "Client domain with samba"
date: 2010-05-30
forum: Server Platforms
---

### Post by pgun90 on 2010-05-30
Hi

I have Ubuntu server 9.04 with samba domain. I have managed to add XP in the domain. But when I try on Ubuntu desktop 9.04, I get errors. 

I use likewise-open. Use this command for adding it,

sudo domainjoin-cli join <domain> <user>

Then I get this message:
Error: Unable to resolve DC name [code 0x80080026]

Can someone help me, want to join ubuntu client to the system.

-Pgun90

---

### Post by fubarcristi on 2010-05-30
try the like wise  gui and user the how to from likewise site

---

### Post by pgun90 on 2010-05-30
> **fubarcristi said:**
> try the like wise  gui and user the how to from likewise site

Tried this. Get the same error with that....

---

### Post by Vegan on 2010-05-30
likewise does not work with SAMBA 3.3 so that is not a solution

what is your domain controller topology?

---

### Post by pgun90 on 2010-05-31
> **Vegan said:**
> likewise does not work with SAMBA 3.3 so that is not a solution

what is your domain controller topology?

Okey, I only want my ubuntu client, to join the samba domain.
Is this possible at all? If so, how?

-Pgun90

---

### Post by pgun90 on 2010-06-07
> **Vegan said:**
> likewise does not work with SAMBA 3.3 so that is not a solution

what is your domain controller topology?

Can I use likewise in Ubuntu 10.04. If i use, the server and desktop 10.04?
What is the best way to add it to a domain, and login with a user?

Thx, for all help.

pgun90

---

