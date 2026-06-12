---
title: "Question about public key/private key encryption"
date: 2009-08-06
forum: Security
---

### Post by EM man on 2009-08-06
I have just started learning about this particular type of encryption.  I am more familiar with symmetric encryption, whereby the sender and receiver share a private key that was exchanged in some secure way (in person, via trusted couriers, etc.).  Why is it not possible to use the public key to decrypt the message, since said public key was used to encypt said message in the first place?

---

### Post by HermanAB on 2009-08-06
Try this:
5 * 11 = ?

55 OK?

Now, given 55, which two numbers were multiplied to get 55?

A more difficult problem right?

This is the kind of problem that public key encryption is typically based on, but remember that public keys are only used to exchange another symetric key which is really used to encrypt the data.

---

### Post by koenn on 2009-08-06
it's a mathematical thing, and there are several different algorithms 
wikipedia has an good explanation on RSA if you like to know  details on how that works

[http://en.wikipedia.org/wiki/RSA](http://en.wikipedia.org/wiki/RSA)

---

### Post by EM man on 2009-08-06
> **HermanAB said:**
> Try this:
5 * 11 = ?
 
55 OK?
 
Now, given 55, which two numbers were multiplied to get 55?
 
A more difficult problem right?
 
This is the kind of problem that public key encryption is typically based on, but remember that public keys are only used to exchange another symetric key which is really used to encrypt the data.
 
Ah okay, it's about prime numbers, thank you. :)
 
Do you mind if I ask you a question about encryption and Evolution?
 
P.S.  There are some instances where entire conversations are conducted with public key/private key cryptography, right?

---

### Post by hggdh on 2009-08-06
Asymmetric encryption allows one to exchange data with somebody else without having the problem of securely exchanging encryption keys (this is called the 'key distribution problem', and it is a very hard problem to tackle).

It also allows for a neat thing:

* what is encrypted with the private key can *only* be decrypted with the corresponding public key;
* what is encrypted with the public key can *only* be decrypted with the corresponding private key.e

Without entering in the details, here it is how it works: you generate a key pair (private, public). The private key you never give to anybody else; the public key you publish on your Facebook, you tweeter about it, in other words, you do *not* care who has it.

Now, if some one wants to send you something that *only* *you* will be able to read, the encrypt it with the *public* key. 

Note that if you want to send somebody something that only they can read, you *cannot* encrypt with your private key, since the whole world has your public key, and everybody would be able to decrypt it... so you would need to use this somebody else's *public* key to do that.

Good so far. Now you add in some special protocols (TLS/SSL comes to mind, being pretty common), and you can open encrypted (private) sessions *without* having to exchange an encryption key! Cool :-). Now, of course, there are a lot of other considerations, which I have taken out of here.

But.

asymmetric encryption usually has a high CPU cost, at about O(10^3) times more costly than symmetric encryption. So you do not want to have your *whole* session under asymmetric encryption. So you design a protocol that will allow an *initital*, asymmetrically encrypted session to be established; during this session, the partners will decide on a *symmetric* algorithm, an ephemeral encryption key for it, and then drop from Asymmetric encryption to symmetric encryption. Lo and behold, I have just described TLS/SSL!

I do not know of any commercial implementation that is fully performed under asymmetric encryption -- high CPU usage, etc.

The large composite number -- the product of two large primes -- is the most common implementation for asymmetric encryption, and relies on the fact that factoring very large numbers is a difficult task (meaning CPU/memory costly), and that the problem goes exponentially harder as the composite number grows. There are, still, no known algorithms to factor a large number in polinomial time, and this problem is usually considered to be a probable non-polinomial (NP) one. Also, *finding* primes seems to be a NP problem as well.

---

