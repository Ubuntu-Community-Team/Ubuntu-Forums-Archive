---
title: "File encryption"
date: 2008-06-21
forum: Security
---

### Post by thabo on 2008-06-21
Any opinions on what is the best program for file encryption ie GPG, Truecrypt etc. I want to use it for my online backups and backup on an external harddrive.
Thanks.

---

### Post by Dr Small on 2008-06-21
Truecrypt for an entire drive / partition, or simply GPG if you only plan to do a single file.

---

### Post by thabo on 2008-06-21
> **Dr Small said:**
> Truecrypt for an entire drive / partition, or simply GPG if you only plan to do a single file.

Thanks. I assume then that they are both equally easy to use/secure and that there are no other programs? They seem to the only ones I found.

---

### Post by hyper_ch on 2008-06-21
problem is that there is also parts of the file stored in swap, in tmp, and other locations as ext3 is journaled... so you have to know what you want to encode

You know the GPCode virus currently running on windows? It encrypts data with rsa key to 1024 bit (I think) and the advice so far is using tools like photorec to reconstruct the original, unencrypted file that was deleted...

Besides, you can fully encrypt your system with luks/dm-crypt

---

### Post by kevdog on 2008-06-21
There are other encryption programs, however many share the same features in that they seem all to make use of common encryption ciphers such as Rijndael (AES), TwoFish, Blowfish, Serpent, etc.  The US government encryption standard is AES128.  This seems currently to be the most tested (meaning its been time tested against hackability).  Both GnuPG and Truecrypt for example employ these ciphers.  Other programs may use different ciphers, however I would  always check what ciphers they use down below.  The American Encryption Standard Competition held in 2000, is a very good place to start: [http://en.wikipedia.org/wiki/Advanced_Encryption_Standard_process](http://en.wikipedia.org/wiki/Advanced_Encryption_Standard_process)

I'm no cryptographic expert however I would ensure whatever program you choose makes use of at least one of the five cipher finalists:
MARS, RC6, Rijndael, Serpent, and/or Twofish.

An emerging cipher particularly in Eastern Asia is known as Camellia.  Rather than Rijndael being the AES=American Encryption Standard, the Japanese Government has chosen Camellia as their Encryption Standard.  I don't know Camellia competes against the other 5 finalists since it wasn't an entrant in the AES competition.  It is in the process however of being ratified into the OpenGPG standard, so I'm assuming it must have a baseline level of credibility.

---

### Post by thabo on 2008-06-21
Thanks guys.
I think I will give Truecrypt a go.:)

---

