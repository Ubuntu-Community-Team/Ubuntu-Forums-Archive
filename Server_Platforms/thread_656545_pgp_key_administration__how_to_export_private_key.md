---
title: "pgp key administration : how to export private key?"
date: 2008-01-02
forum: Server Platforms
---

### Post by mveltre on 2008-01-02
hi,

i've installed the PGP key administration tool and generated a new private and public key. All works perfectly.. but I like to use my keypair also on another PC, in another application. 

For this i need a simple ASCII export of my private and public key. It is easy to export the public one... but for the private one i can not find a way?

There is a possibility to back-up the keypair. But the outcome is a zipped pubring and secring.pgp which seems to be binary and not ASCII.

Any ideas?

Thanks!

Markus

---

### Post by icheyne on 2008-01-02
gpg --export-secret-keys --armor

or try:

sudo aptitude install kgpg (if you prefer KDE)

or

sudo aptitude install seahorse (if you prefer Gnome)

---

