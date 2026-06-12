---
title: "where is password file in ubuntu?"
date: 2010-01-07
forum: Security
---

### Post by vksingh on 2010-01-07
Hi,

Can somebody tell me in which file in Ubuntu , the login passwords of all users is stored.

Thanks,

Vivek

---

### Post by lisati on 2010-01-07
Why?

---

### Post by __p1n__ on 2010-01-07
In an ubuntu installation login password values are not stored in any file.

---

### Post by FuturePilot on 2010-01-07
> **__p1n__ said:**
> In an ubuntu installation login password values are not stored in any file.

Yes they are. How does it authenticate you then?

---

### Post by __p1n__ on 2010-01-07
> **FuturePilot said:**
> Yes they are. How does it authenticate you then?

Carefully reread my post.

---

### Post by FuturePilot on 2010-01-07
> **__p1n__ said:**
> Carefully reread my post.

Oh, you mean the plain text value?

---

### Post by __p1n__ on 2010-01-07
> **FuturePilot said:**
> Oh, you mean the plain text value?

Which is what the OP asked for.

---

### Post by undecim on 2010-01-07
Well, if you plan on trying to find out someone else's password, you are out of luck, because all the passwords are encrypted.

The encrypted passwords are stored in /etc/shadow, but you should never have to mess with it. 

What exactly are you doing that you need the passwords? There are several tools built into Ubuntu for manipulating the password and shadow files.

---

### Post by FuturePilot on 2010-01-07
> **__p1n__ said:**
> Which is what the OP asked for.

Yes, now I understand.

---

### Post by doas777 on 2010-01-07
traditionally they are stored in /etc/passwd, but that file has not contained passwords for a very long time. more recently the passwords were stored in a file called /etc/shadow that was encrypted for security. there is no good way to find a users password in cleartext on a modern system.

---

### Post by doas777 on 2010-01-07
> **FuturePilot said:**
> Yes they are. How does it authenticate you then?
hash comparison. passwords are required to use non-reversible hashing, so that they cannot be broken (deciphered in plaintext).

so on password create, hash the passwd by a given mechanism, and store the hash.
when you put in your password, it is hashed against the same mechanism, and if it matches, you are ready to go, and the system does not need to know your actual password. 

the only problem with this system is that you have to ensure that the incoming vector actually hashed the password, rather than just supplying an already compromised hash (pass-the-hash attacks).

---

### Post by running_rabbit07 on 2010-01-07
> **doas777 said:**
> hash comparison. passwords are required to use non-reversible hashing, so that they cannot be broken (deciphered in plaintext).

so on password create, hash the passwd by a given mechanism, and store the hash.
when you put in your password, it is hashed against the same mechanism, and if it matches, you are ready to go, and the system does not need to know your actual password. 

the only problem with this system is that you have to ensure that the incoming vector actually hashed the password, rather than just supplying an already compromised hash (pass-the-hash attacks).

All this talk about hash can't be good.:P Isn't technology grand?

---

### Post by __p1n__ on 2010-01-07
> **running_rabbit07 said:**
> All this talk about hash can't be good.:P Isn't technology grand?

I don't do it often but when I do do it I love smoking hashes - the windows LM variety particularly.

---

### Post by doas777 on 2010-01-07
lolz

---

### Post by vksingh on 2010-01-08
Hi,

Can anybody tell me, how to decrypt the password available in /etc/shadow file?

Thanks,

Vivek

---

### Post by vksingh on 2010-01-08
Hi,

Can anybody tell me how to decrypt the password of users available in /etc/shadow file in Ubuntu?

Thanks,

Vivek

---

### Post by Agent ME on 2010-01-08
It was already said above: It's not possible.

---

### Post by bodhi.zazen on 2010-01-08
> **vksingh said:**
> Hi,

Can anybody tell me how to decrypt the password of users available in /etc/shadow file in Ubuntu?

Thanks,

Vivek

It is possible, however, decrypting another person's password is not supported in these forums.

---

