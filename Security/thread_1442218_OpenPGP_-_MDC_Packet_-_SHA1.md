---
title: "OpenPGP - MDC Packet - SHA1"
date: 2010-03-29
forum: Security
---

### Post by tomehb on 2010-03-29
OpenPGP Standard RFC 4880, not really a Linux Question, but as may be using GnuPG on Linux I thought I would ask here:) 

The Modification Detection Code Packet is defined to use SHA-1, even though it does state in section 13.11. that this can be altered, and gives example methods. However this would cause interoperability, [SIZE="3"]**(q1)**[/SIZE]so I assume there is no standard method of doing this??

[SIZE="3"]**(q2)**[/SIZE]How much of a threat do you believe this to be? Even though the SHA-1 hash is encrypted within the symmetrically encrypted integrity protected data packet. 


Cheers

Thomas

---

### Post by Agent ME on 2010-03-29
Are you asking if the modification detection code packet is a threat? I think you are completely misunderstanding it. The mdc just makes sure that the message hasn't been tampered with.

---

### Post by tomehb on 2010-03-29
> **Agent ME said:**
> Are you asking if the modification detection code packet is a threat? I think you are completely misunderstanding it. The mdc just makes sure that the message hasn't been tampered with.

If the message has been altered would this not be a threat? Slightly Confused...

---

### Post by Agent ME on 2010-03-29
Are you asking whether it's a threat when the MDC is altered and incorrect, or whether there's a threat changing the MDC to use a different hashing system?

In the first case, if you get an error that a message's MDC is incorrect, the message was either corrupted or tampered with. You probably shouldn't trust it.

In the second case, I think you can change what hashing system is used to make the MDC, but people using older software might have trouble decrypting your messages. On linux mailing lists, etc, this probably isn't very likely as most are using a recent version of GPG, but in some corporate contexts where older versions of PGP may be in use, others may run into some trouble.

---

### Post by tomehb on 2010-03-29
> **Agent ME said:**
> Are you asking whether it's a threat when the MDC is altered and incorrect, or whether there's a threat changing the MDC to use a different hashing system?

In the first case, if you get an error that a message's MDC is incorrect, the message was either corrupted or tampered with. You probably shouldn't trust it.

In the second case, I think you can change what hashing system is used to make the MDC, but people using older software might have trouble decrypting your messages. On linux mailing lists, etc, this probably isn't very likely as most are using a recent version of GPG, but in some corporate contexts where older versions of PGP may be in use, others may run into some trouble.

The latter and also found some info on it....


[http://www.aigarius.com/blog/2009/05/06/re-howto-prep-for-migration-off-of-sha-1-in-openpgp/](http://www.aigarius.com/blog/2009/05/06/re-howto-prep-for-migration-off-of-sha-1-in-openpgp/) :)
> "Brian: SHA-1’s collision-resistance has been compromised, but it is not clear that its one-wayness has been compromised. As Daniel A. Nagy points out, for fingerprints and MDC, collision resistance is unimportant, and only one-wayness matters."

Cheers

---

