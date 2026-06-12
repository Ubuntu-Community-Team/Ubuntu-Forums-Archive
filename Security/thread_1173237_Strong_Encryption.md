---
title: "Strong Encryption"
date: 2009-05-29
forum: Security
---

### Post by CitizenOne on 2009-05-29
I want to encrypt a file, and then use on the fly decryption and mount it on the filesystem. I know True Crypt can do this, but what about the Key Size. TrueCrypt, to my knowledge, uses 256-bit AES. Can you use larger keys for stronger encryption?

---

### Post by tubbygweilo on 2009-05-29
CitizenOne, 
Does truecrypt [cascading keys]("http://www.truecrypt.org/docs/cascades") encryption meet your requirements?

---

### Post by rookcifer on 2009-05-29
Why would you need anything stronger than 256 bit AES?  It would take millions of times longer than the age of the universe to even begin to brute force it.

Key size is the least of your worries.  More important is to pick a strong pass phrase, and a strong hash (SHA-256).  Your encryption is only as strong as the weakest link, and AES 256 is definitely NOT the weakest link.

---

### Post by Chayak on 2009-05-30
I think you may be confused on key strenghts CitizenOne.  You see 2048 and 4096 bit keys with RSA and only 256 bit with AES.  They're two different types of ciphers.  RSA being a stream cipher that goes bit by bit which is good for things such as streaming data.  AES works as a block cipher which encrypts 128 bit blocks data.  The method is much stronger cryptographically hence they key size is smaller.  The exact reasons behind it would take quite a while to explain and it's easier to just tell to you buy a copy of Applied Cryptography and find out yourself.

In the end the weakest link is likely going to be your passphrase.

---

### Post by statistic on 2009-05-31
Chayak is right. I'm in the middle of reading Bruce Scheier's Applied Cryptography, if you read [http://everything2.com/title/Thermodynamics%2520limits%2520on%2520cryptanalysis](http://everything2.com/title/Thermodynamics%2520limits%2520on%2520cryptanalysis) you'll find some text from the book that basically explains why it'll be a *long long* time before anyone human develops the means to defeat a key of that strength for symmetric encryption.

---

