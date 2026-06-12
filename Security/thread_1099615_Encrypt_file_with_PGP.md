---
title: "Encrypt file with PGP"
date: 2009-03-18
forum: Security
---

### Post by e24ohm on 2009-03-18
Folks:
Is there a way to use PGP to encrypt a file. Understand you can use PGP for email, with Thunderbird, but I want to encrypt a file.

If PGP can not be used to do this, what is a good opensource/standard method to encrypt file/files on linux?

thanks 
E

---

### Post by Dr Small on 2009-03-18
Greetings there,
Please check out my guide for GnuPG encryption:
[http://ubuntuforums.org/showthread.php?t=680292](http://ubuntuforums.org/showthread.php?t=680292)

Regards,
Dr Small

---

### Post by e24ohm on 2009-03-18
> **Dr Small said:**
> Greetings there,
Please check out my guide for GnuPG encryption:
[http://ubuntuforums.org/showthread.php?t=680292](http://ubuntuforums.org/showthread.php?t=680292)

Regards,
Dr SmallMate this is great, thanks. Sorry if this is a stupid question, but is this compairable to say 128 bit, or something of the sort?

---

### Post by e24ohm on 2009-03-18
> **Dr Small said:**
> Greetings there,
Please check out my guide for GnuPG encryption:
[http://ubuntuforums.org/showthread.php?t=680292](http://ubuntuforums.org/showthread.php?t=680292)

Regards,
Dr SmallMate, i checked out your other sites, Happy birthday...cheers!!!

---

### Post by Dr Small on 2009-03-18
> **e24ohm said:**
> Mate this is great, thanks. Sorry if this is a stupid question, but is this compairable to say 128 bit, or something of the sort?
I'm not a cryptology expert; I just use it. But my friend kevdog has written a guide on "Advanced Key Generation", which you can find here.
[http://ubuntuforums.org/showthread.php?t=687173](http://ubuntuforums.org/showthread.php?t=687173)

> **e24ohm said:**
> Mate, i checked out your other sites, Happy birthday...cheers!!!
Thanks! Yes, I'll be turning 18 tomorrow. What sites did you find this from, if I may ask? :D My UF profile?

Best Regards,
Dr Small

---

### Post by unutbu on 2009-03-18
Happy birthday, Dr Small! 
Your knowledge sure outpaces your years. :popcorn:

---

### Post by Dr Small on 2009-03-18
> **unutbu said:**
> Happy birthday, Dr Small! 
Your knowledge sure outpaces your years. :popcorn:
Oh, I wouldn't say that. There is still quite alot of things I have never been able to comprehend or yet master, but I thank you just the same. It's really funny though, that people should start wishing me a happy birthday in a support thread! :D

---

### Post by e24ohm on 2009-03-18
> **Dr Small said:**
> Oh, I wouldn't say that. There is still quite alot of things I have never been able to comprehend or yet master, but I thank you just the same. It's really funny though, that people should start wishing me a happy birthday in a support thread! :DRespect for helping me mate...Cheers!!!

---

### Post by tornadof3 on 2009-03-18
You asked about whether it's comparable to 128bit security. There are two main types of cryptography techniques - symmetric key and public-private (asymmetric) key. GnuPG uses the asymmetric type (well, technically it also uses both but that's a different topic).

If you hear someone who uses eg TrueCrypt with a 128-bit AES key, a 128-bit ElGamal key used with GnuPG would not be as secure. In fact no where near as secure. Keys you generate with GnuPG will tend to be in the 2048 bits region. I personally use 4096 bits although that is majorly paranoid and unnecessarily large.

---

### Post by kevdog on 2009-03-20
Happy Birthday Dr. Small.  Hopefully all of your wishes if you had any came true.  I know mine never did, but at least hoping yours did!

---

