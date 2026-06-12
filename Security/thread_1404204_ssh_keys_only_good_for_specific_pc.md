---
title: "ssh keys only good for specific pc?"
date: 2010-02-11
forum: Security
---

### Post by siva_ on 2010-02-11
I have enabled ssh key based logins for one of my servers and disabled normal password based logins.

It just occurred to me that the public key which I generated on my pc, and uploaded to the servers authorized_keys, may in fact only apply to my local PC / user account.

So basically if my system crashes I would have no way to login to the server...? Is it not possible to "share" public keys so other people (PCs / accounts) can use them?

Thanks for your help.

---

### Post by noway2 on 2010-02-11
What is important is the public - private key pair.  Anyone with the private key can gain access.  You upload the public key to the server and keep the private key on the client.  If you were to put the private key on multiple PCs, it should authenticate each of them.

The downside to this is twofold: 1 - multiple copies of the private key increases the likelihood of it becoming compromised.  2 - if it does become compromised, it is more work to replace all of them.

---

### Post by ushills on 2010-02-11
Why not carry your ssh key on a usb stick with a strong passphrase.

---

### Post by FlaHAM on 2010-02-11
SSH dual key access ONLY effects your remote log on. I use dual key access with the password access option disabled.
It does not impair your ability to log on at the local console.

FlaHAM

---

