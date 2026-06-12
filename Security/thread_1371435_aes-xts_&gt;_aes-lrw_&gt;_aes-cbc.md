---
title: "aes-xts &gt; aes-lrw &gt; aes-cbc ?"
date: 2010-01-03
forum: Security
---

### Post by jf/ on 2010-01-03
I'm just wondering - what is the best way to set up your encrypted volumes with dm_crypt and LUKS?

My understanding was that aes-lrw ws better than aes-cbc - and then I stumble upon [http://en.wikipedia.org/wiki/Disk_encryption_theory#LRW](http://en.wikipedia.org/wiki/Disk_encryption_theory#LRW) which says that LRW has some problems, and XTS is better? I dont know enough about encryption theory to be able to say anything, so i'm hoping some folks more enlightened will be able to say something here.

I was previously using aes-lrw-benbi to set up a volume. If xts is truly better - should i be using '-c aes-xts-benbi' then?

---

### Post by jf/ on 2010-01-03
and btw, a cat of /proc/crypto does not show me support for aes-lrw, even though cryptsetup has managed to work with that cipher. How do i check to see which ciphers are truly supported?

---

### Post by __p1n__ on 2010-01-03
Presumably LRW was dropped by the SISWG because this encryption mode assumes that the plaintext and the tweak key are independent.  Practically speaking, it was Microsoft's refusal to adopt it that did it in.

XTS is the identified long-term narrowblock encryption mode for AES so in the absence of any particular techno-aesthetic consideration you could do worse than to adopt it.

---

### Post by rookcifer on 2010-01-03
Use aes-cbc-essiv.  XTS is still fairly new and hasn't underwent nearly the scrutiny that cbc has.  And the watermarking attacks are mitigated by using essiv.

---

### Post by HermanAB on 2010-01-04
Military desktop systems commonly use AES256, CBC, ESSIV, SHA256

---

