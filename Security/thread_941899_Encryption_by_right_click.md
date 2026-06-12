---
title: "Encryption by right click?"
date: 2008-10-08
forum: Security
---

### Post by Line on 2008-10-08
Hi
On the desktop I can right click and select "encrypt". Then "Choose recipients" pops up with no alternatives to select. 
Can I make my own keys here?
Is there a users manual for this function somwere?
Thanks

---

### Post by slowth5 on 2008-10-08
Hi Line, you first need to create a public key.

For Hardy:

Applications > Accessories > Passwords and Encryption Keys

Click the "New" button across from 'Generate a new key of your own.'

Select PGP key, then fill out the information and create a new key. The default key uses strong encryption, so just pick a strong password and you're good to go. Now you can right-click and select your key to encrypt.

---

### Post by lovinglinux on 2008-10-08
> **slowth5 said:**
> Hi Line, you first need to create a public key.

For Hardy:

Applications > Accessories > Passwords and Encryption Keys

Click the "New" button across from 'Generate a new key of your own.'

Select PGP key, then fill out the information and create a new key. The default key uses strong encryption, so just pick a strong password and you're good to go. Now you can right-click and select your key to encrypt.

What does public key means? It will be listed somewhere with public access?

What happens if I loose the key somehow?

---

### Post by slowth5 on 2008-10-08
Public-key cryptography, also known as asymmetric cryptography, is a form of cryptography in which the key used to encrypt a message differs from the key used to decrypt it. In public key cryptography, a user has a pair of cryptographic keys&#8212;a public key and a private key. **The private key is kept secret, while the public key may be widely distributed.** Incoming messages would have been encrypted with the recipient's public key and can only be decrypted with his corresponding private key. The keys are related mathematically, but the private key cannot be practically derived from the public key.

You can backup your public key. If you lose the only copy, then you're in trouble.

---

### Post by lovinglinux on 2008-10-08
> **slowth5 said:**
> **The private key is kept secret, while the public key may be widely distributed.**

So, when you create a new key in the "My Personal Keys" option they are not automatically made public right? The keys are generated locally and to distribute the public key I have to "Export Public Key" and upload it somewhere right? 

I'm asking these questions because I never used this feature, so I don't want to mess things and put myself on a position of security risk, thinking that I'm secure.

---

### Post by slowth5 on 2008-10-09
Hi lovinglinux, you're exactly right.  I only recently sorted out public key cryptography, since it can be confusing.  

It's commonly used for secure email exchange. You and a friend each create private keys, then you export and exchange public keys. You then import your friends public key and sign their public key with your private key. Now when exchanging email, you encrypt your message with your friend's public key, so that only your friend can decrypt the message with their private key.

---

### Post by lovinglinux on 2008-10-09
> **slowth5 said:**
> Hi lovinglinux, you're exactly right.  I only recently sorted out public key cryptography, since it can be confusing.  

It's commonly used for secure email exchange. You and a friend each create private keys, then you export and exchange public keys. You then import your friends public key and sign their public key with your private key. Now when exchanging email, you encrypt your message with your friend's public key, so that only your friend can decrypt the message with their private key.

Thanks. It is a little bit confusing, but it's clear now. I imagine how this would work in the real world. I guess my friends would stop sending me e-mails if I send them a pgp key to decrypt the message :)

Now I remember trying to use pgp with Windows a long time ago, but didn't worked very well. Ubuntu makes it really easy to use.

---

