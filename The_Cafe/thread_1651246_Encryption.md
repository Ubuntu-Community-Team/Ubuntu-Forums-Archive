---
title: "Encryption"
date: 2010-12-22
forum: The Cafe
---

### Post by ki4jgt on 2010-12-22
I have an encryption algorithm Actually, it's a program which encrypts archives of files created with the program. I don't know what to tell my users when they ask how many bits encryption it is. Basically the longer the password is, the more encrypted the file becomes. After the encryption, the program rearranges the encrypted data in a random pattern decided by the password. Both the encryption and the rearangement of data can be MAJORLY influenced by slight differences such as "Battle" and "battle"

---

### Post by jerenept on 2010-12-22
Sounds interesting.

---

### Post by ve4cib on 2010-12-22
Could you change your algorithm so that the password is simply a seed used to generate an n-byte key?  That's basically how AES works; password + some initial (fixed) value ==> encryption key.  That way you could definitively say that your algorithm is n-bytes encryption.  You might even be able to just recycle AES' key expansion to suit your purposes.

---

### Post by ki4jgt on 2010-12-23
I really don't want to change it though, I've been using it to keep my secrets for years. Mainly in notebooks and things but it's still cool :-) Isn't there some kind of math formula which can tell how many bits it is? LOL sorry :-) just curious.

---

### Post by ve4cib on 2010-12-23
If the length of the password defines the strength of the encryption (i.e. longer password = "more encrypted") then it's a "variable-bit cipher."

Something like AES on the other hand, uses a nice big function to generate a fixed-length key from a password.  The entropy of the key should be about the same, regardless of the length of the password, so from an algorithmic perspective there's no real difference between a single-character password and a 10-million character password.  Obviously one is easier to guess than the other in terms of brute-force, but if you were to work backwards to extract the password based on a known plaintext and a known ciphertext the length of the inital password doesn't make any difference at all.

---

### Post by cammin on 2010-12-23
[http://en.wikipedia.org/wiki/Password_strength](http://en.wikipedia.org/wiki/Password_strength)

There's a section about calculating both the entrophy bits of randomly generated and human generated passwords.

---

### Post by Grenage on 2010-12-23
Is it not likely that, however esoteric it may be, a personal algorithm would take mere minutes or hours to crack, compared with a standardised encryption algorithm such as Twofish?

---

### Post by ve4cib on 2010-12-23
It really depends.  Someone could implement an exceptionally robust encryption algorithm on their own.  PGP started off as a little private encryption algorithm back in the 90s after all.

That said it's probably much more likely that this particular algorithm is pretty weak when compared to peer-reviewed algorithms like AES, TwoFish, and the like.

---

### Post by ki4jgt on 2010-12-24
I'm actually going to setup a $20 dollar reward for anyone who can crack it once I get it built. (Provided they can show me how they did it! - and not using Brute force. I have a few more additions I want to add to it than what has been posted here.

EDIT: I'll be using a 100 character password.

---

### Post by Grenage on 2010-12-24
Good call; people love a challenge, and you'd be able to put your encryption to the test. :)

---

