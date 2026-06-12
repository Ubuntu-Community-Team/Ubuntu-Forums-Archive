---
title: "Question about PGP/GPG and OTR"
date: 2010-04-11
forum: Security
---

### Post by blueshiftoverwatch on 2010-04-11
I always thought that any kind of public key encryption meant that it was asymmetric. Which means that PGP/GPG and OTR are both examples of asymmetric encryption. But, I was reading their Wikipedia articles and:
> **PGP]PGP encryption uses a serial combination of hashing, data compression, **symmetric-key cryptography**, and, finally, public-key cryptography said:**
> 
[QUOTE=PGP; Early History]Phil Zimmermann created the first version of PGP encryption in 1991. The name, "Pretty Good Privacy", is humorously ironic and was inspired by the name of a grocery store, "Ralph's Pretty Good Grocery", featured in radio host Garrison Keillor's fictional town, Lake Wobegon. **This first version included a symmetric-key algorithm that Zimmermann had designed himself**, named BassOmatic after a Saturday Night Live skit.
[QUOTE=OTR]Off-the-Record Messaging, commonly referred to as OTR, is a cryptographic protocol that provides strong encryption for instant messaging conversations. OTR uses a combination of the **AES symmetric-key algorithm**, the Diffie-Hellman key exchange, and the SHA-1 hash function.[/QUOTE]
[QUOTE=Diffie-Hellman key exchange]Diffie&#8211;Hellman key exchange (D&#8211;H) is a cryptographic protocol that allows two parties that have no prior knowledge of each other to jointly establish a shared secret key over an insecure communications channel. This key can then be used to encrypt subsequent communications using a **symmetric key cipher**[/QUOTE]

I think I understand how OTR works, using the Diffie-Hellman key exchange it uses public keys (asymmetric) encryption to exchange symmetric (secret key encryption). But, OTR is a little different in that the keys are throw away and the entire system is designed so that the conversations can't be decrypted later, even if both parties in the conversation wanted to.

When using GPG I've always used the ElGamal encryption algorithm, which is asymmetric. But that still uses the Diffie-Hellman key exchange. Which "[is] used to encrypt subsequent communications using a symmetric key cipher". But with PGP/GPG the keys aren't throw away like in OTR. And, I don't see how any scheme can use symmetric encryption over the Internet and still be secure. Symmetric encryption keys are vulnerable to interception by a man in the middle.

I'm confused and reading other Wikipedia articles as well as the short section on encryption in one of my textbooks isn't helping either. It seems like all of the sources I've read either aren't telling me what I want to know, or are written in such a way that they assume you already know everything about the subject beforehand.

---

### Post by Agent ME on 2010-04-11
Assymetric (public-key) encryption algorithms are slow. PGP and many other systems will create a random key for a symmetric algorithm, encrypt it to the other person's public key, and then securely send the key over. Then the rest of the message is encrypted with that key in a symmetric algorithm.

---

### Post by blueshiftoverwatch on 2010-04-12
> **Agent ME said:**
> Assymetric (public-key) encryption algorithms are slow. PGP and many other systems will create a random key for a symmetric algorithm, encrypt it to the other person's public key, and then securely send the key over. Then the rest of the message is encrypted with that key in a symmetric algorithm.
So what your saying is: when Alice encrypts a message to send to Bob. She's doing more than just encrypting the message with Bob's public key to be decrypted by Bob's private key? When she selects Bob's key another third key is created that is a combination of one of Alice's keys and Bob's public key?

---

### Post by rookcifer on 2010-04-12
> **blueshiftoverwatch said:**
> So what your saying is: when Alice encrypts a message to send to Bob. She's doing more than just encrypting the message with Bob's public key to be decrypted by Bob's private key? When she selects Bob's key another third key is created that is a combination of one of Alice's keys and Bob's public key?

When Alice wants to send a message to Bob, this is what happens:

1) Her client (PGP/GPG) will create a one-time session key using a conventional (and fast) *symmetric* algorithm.  

2) That session key is used to encrypt the plaintext and turn it into ciphertext.

3) The session key is then encrypted with the recipient's public key and sent along with the already encrypted ciphertext. 

4) The recipient decrypts the session key and then uses the session key to decrypt the ciphertext.

So, basically, the public key is only used to encrypt another symmetric key.  The reason is that asymmetric ciphers are much slower than symmetric.  So, it's just an issue of speed.

[This website ]("http://www.pgpi.org/doc/pgpintro/#p10")explains it all.

---

### Post by blueshiftoverwatch on 2010-04-12
Thanks, that helped a lot.

---

