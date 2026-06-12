---
title: "RSA Prime Numbers"
date: 2008-02-17
forum: Security Discussions
---

### Post by Ryan H on 2008-02-17
Okay I'm reading into RSA encryption and I know I have to have two large random prime numbers to generate the keys. I've read the numbers need to be between 100 and 200 digits, I want to know how I generate numbers this big? All I've found on the internet is a lot of complicated mathmatical methods, random programs like mprime, which I can't seem to actually output any numbers form, and very large lists of prime numbers on the internet.

Can anyone point me to a program/resource to do this?

Thanks!

-Ryan H

---

### Post by kevdog on 2008-02-17
Is this for gpg encryption or by some other method?

---

### Post by Ryan H on 2008-02-17
I'm not sure? I plan on using it for a digital signature...
I think its just plain RSA.

---

### Post by kevdog on 2008-02-17
An RSA based signature for emails -- like a GnuPG signing key?  Again, usually the RSA algorithm is implemented into another program and the functionality taken from there.  Unless you are a programmer (which you very well might be), what exactly do you want to use RSA for?

---

### Post by Ryan H on 2008-02-17
Yes, I am a programmer. My program regularly checks for updates from a central server and then downloads the updates from the server. I planned on signing the updates with a digital signature to verify their contents. The language I'm using is PHP. There isn't currently a purely PHP implementation of GnuPG, while there is for RSA.

As I understand it you generate a public key and a private key from the prime numbers. I'd then distribute the public key with my program, and keep the digitally sign the updates with the private key. And I would encrypt and decrypt with RSA.

Correct?

-Ryan H

---

### Post by kevdog on 2008-02-17
Hmm, yes that is the way it works however Ive never programmed trying to do this.  Sounds definitely interesting as far as using php.

---

### Post by Ryan H on 2008-02-18
Ah, thanks anyways.

Does anyone know how to generate large prime numbers?

-Ryan H

---

### Post by kevdog on 2008-02-18
Not to bother you any farther, but why don't you post on the gnupg mailing list.  I know this has nothing to do with gnupg, however they have had to incorporate this method in their program.  The programers themselves often post to this list so I am sure they can either give you a method or a reference:

[http://www.gnupg.org/documentation/mailing-lists.en.html](http://www.gnupg.org/documentation/mailing-lists.en.html)

---

### Post by euler_fan on 2008-02-18
> **Ryan H said:**
> Ah, thanks anyways.

Does anyone know how to generate large prime numbers?

-Ryan H

Generate large number, test from primality.

The first is simple--just make a large random integer. The second requires various tests. One you might look at is Lucas-Lehmer. It was used to test some of the Mersenne primes (which get very large very fast). Just google for tests for prime numbers or some such.

This is the only way to generate primes known.

On another point it takes all of 30 seconds to generate a signature for a file using GPG. I suspect you are not generating the update on your server, merely distributing it via the server. In this case, why not make a script to take a given update (which you can point the script at), have it then generate the signature and upload both to the server for you? This avoids the whole problem of coding signatures and also minimizes the risk of potentially exposing your secret key through the Internet as it will not be on the server at all.

---

