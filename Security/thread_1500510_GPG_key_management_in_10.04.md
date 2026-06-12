---
title: "GPG key management in 10.04"
date: 2010-06-03
forum: Security
---

### Post by ushills on 2010-06-03
Hi

I have a fresh upgrade of 10.04 with my existing /home directory.  I cannot get seahorse to import my existing private gpg key that is held as both an asc file and a private block.

What app is best to use for the management of GPG keys in 10.04, I would use enigmail but it is not compatible with the latest 64bit thunderbird in the repos and therefore have to use evolution.

---

### Post by rookcifer on 2010-06-03
> **ushills said:**
> Hi

I have a fresh upgrade of 10.04 with my existing /home directory.  I cannot get seahorse to import my existing private gpg key that is held as both an asc file and a private block.

Seahorse should automatically recognize the key if it's in the ~/.gnupg directory.  If not, I suppose you could try using the command line

```
gpg --allow-secret-key-import --import private.key
```

> What app is best to use for the management of GPG keys in 10.04, I would use enigmail but it is not compatible with the latest 64bit thunderbird in the repos and therefore have to use evolution.

Hmm.  I use Enigmail with Thunderbird all the time, and I am on 64 bit Lucid (I am assuming the versions in the repos are 64 bit).

---

### Post by ushills on 2010-06-04
> **rookcifer said:**
> 
Hmm.  I use Enigmail with Thunderbird all the time, and I am on 64 bit Lucid (I am assuming the versions in the repos are 64 bit).


For some reason I cannot install enigmail from the repos as it says incompatible x64 version and the xpi although it installs does nothing.

---

