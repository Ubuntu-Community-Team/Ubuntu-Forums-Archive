---
title: "When do I need to use &quot;0x&quot; prefix for GnuPG keys?"
date: 2012-03-31
forum: Security
---

### Post by chazinams on 2012-03-31
I often see GnuPg keys showing a "0x" before the short key (eg, 0xABCD1234). 

I noticed that commands still work without the 0x, like gpg --fingerprint ABCD1234 as opposed to gpg --fingerprint 0xABCD1234.

Is 0x a totally OPTIONAL thing? Or should I always use it? Why is it used but appears to not be needed for Terminal commands?

---

### Post by haqking on 2012-03-31
> **chazinams said:**
> I often see GnuPg keys showing a "0x" before the short key (eg, 0xABCD1234). 

I noticed that commands still work without the 0x, like gpg --fingerprint ABCD1234 as opposed to gpg --fingerprint 0xABCD1234.

Is 0x a totally OPTIONAL thing? Or should I always use it? Why is it used but appears to not be needed for Terminal commands?

0x signifies hexadecimal.

Safest to use it,

For example 9 is 9 in decimal and 9 in hexadecimal, but 0x9 is only 9 in hexadecimal

---

### Post by chazinams on 2012-03-31
Thanks!

---

