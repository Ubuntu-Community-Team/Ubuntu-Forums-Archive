---
title: "Can I choose the encryption algorithm passwd uses?"
date: 2009-10-01
forum: Security
---

### Post by currupipi on 2009-10-01
Hi,all!While I was trying John the Ripper on my ubuntu 9.04, I discovered by accident that my passwords were encripted in sha-512, or at least I think so.(the hash started with $6$,which corresponds to that one,correct me if I'm wrong).Since when is this algorithm used on ubuntu?I can't find the information anywhere. Am I able to choose which alogrithm to use? How? Can I use AES,for example? Would that be advisable?
Thank you for the attention.

---

### Post by kevdog on 2009-10-01
sha512 -- this is not the encryption cipher -- it is the hash of the password.  Cipher algorithm vs hash algorithm -- two totally different things we are talking about!

---

### Post by Lars Noodén on 2009-10-02
/etc/login.defs gives several options for password hashes, but AES is not listed.

---

### Post by cdenley on 2009-10-02
SHA-512 is the best password hashing algorithm available with PAM, and I believe it was implemented starting with 8.10. Before that, MD5 was used. If neither of those are configured in /etc/pam.d/common-password, then it falls back to the default DES, which is very weak. I believe AES is an ecryption algorithm, not a hashing algorithm, so you wouldn't want to protect your passwords with it even if it were possible.

It is also possible to use blowfish, but I think SHA-512 is better.
```

sudo apt-get install libpam-unix2
cat /usr/share/doc/libpam-unix2/README.Debian

```

---

### Post by cdenley on 2009-10-02
> **Lars Noodén said:**
> /etc/login.defs gives several options for password hashes, but AES is not listed.

I believe /etc/login.defs only changes the algorithm used by System>Administration>Users and Groups to change passwords. Command-line tools like "passwd" will use the algorithm configured in /etc/pam.d/common-password.

---

### Post by currupipi on 2009-10-02
All right!thank you all!

---

### Post by kevdog on 2009-10-02
DES and Blowfish are ciphers, not hash types.

---

### Post by cdenley on 2009-10-02
> **kevdog said:**
> DES and Blowfish are ciphers, not hash types.

I don't think their PAM implementations would qualify as ciphers, but I could be wrong.

---

