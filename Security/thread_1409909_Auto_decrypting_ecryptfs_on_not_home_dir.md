---
title: "Auto decrypting ecryptfs on not home dir"
date: 2010-02-18
forum: Security
---

### Post by bulislaw on 2010-02-18
Ive tried to encrypt some "random" dir eg other disk wih ecryptfs -> ok it works fine but i dont want to manually decrypt it (file with plain text passphrase is not an option!) 

So i want to bind it to user login like default home dir, but i cant find any serious docs etc only sevral howto encrypt home dir ...

Please help

---

### Post by giammy on 2010-02-18
> **bulislaw said:**
> Ive tried to encrypt some "random" dir eg other disk wih ecryptfs -> ok it works fine but i dont want to manually decrypt it (file with plain text passphrase is not an option!) 

So i want to bind it to user login like default home dir, but i cant find any serious docs etc only sevral howto encrypt home dir ...

Please help

Hi,

you could give a try to libPAM: the module pammount can execute actions at login,
using login password, and mount a encrypted device.

bye
giammy

---

### Post by bulislaw on 2010-02-18
ok, but i need strong pass (or key file) to encrypted data and kind of more usable to the system (10-15 chr) 

iam trying to follow ubuntu at this one and use wrapped pass (i know i can use pammount and use second loop-based encrypted "drive" key only and then use it to decrypt the rest -> but this is the secondbest solution) 

i hope some one would know how to use only ecryptfs and the pamecrypfs (or something like this)

---

