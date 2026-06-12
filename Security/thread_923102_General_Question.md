---
title: "General Question"
date: 2008-09-18
forum: Security
---

### Post by mdlefave on 2008-09-18
Because the linux kernel is open source, what stops people from looking at the code, seeing what the encryption on user passwords is, and cracking anyone they want (anyone using the linux kernel of course). Someone want to fill me in?

---

### Post by ntbutler on 2008-09-18
> **mdlefave said:**
> Because the linux kernel is open source, what stops people from looking at the code, seeing what the encryption on user passwords is, and cracking anyone they want (anyone using the linux kernel of course). Someone want to fill me in?

From what i am aware, generally the encryption functions are 1-way functions. I suppose people could if they can be bothered, but from what others have told me the functions are designed so that cracking them is a big hassle, so the only real way is brute force. I did hear once that someone re-wrote a kernel that used a really simple 2-way hash function for the passwords and then distributed it to some un-wary noobs...
Admittedly, i haven't looked at how ubuntu handles this, but i have studied some other versions like minix and, yeah i guess it's a bit of a danger, but no more than windows...

---

### Post by cariboo on 2008-09-18
IF you get your kernel from trusted sources, in the case of Ubuntu, the repositories, you have nothing to worry about, unless someone has physical access to your computer, then all bets are off. Just as an aside I let john (the butcher) try to brute force my password, I shut down the program after 8 hours as it hadn't cracked my password yet. John is available in the rpeositories.

Jim

---

### Post by The Cog on 2008-09-18
Just to simplify nbutlers answer: the password encryption is a one-way hash, meaning it is essentially impossible to un-encrypt the stored passwords again. The way Linux checks your password as you log in is to scramble the password you enter in the same way, and check that you get the same mess as is stored on disk. That way, even if someone gets access to the password file, it won't really help.

---

### Post by hyper_ch on 2008-09-18
it is not impossible.

If an attacker can get hold of your encrypted password he can then use rainbow tables to find a collission - meaning another string that encrypts to the same hash. With that they won't need to know your original one but they can use the collission one.

---

### Post by cdenley on 2008-09-18
> **hyper_ch said:**
> it is not impossible.

If an attacker can get hold of your encrypted password he can then use rainbow tables to find a collission - meaning another string that encrypts to the same hash. With that they won't need to know your original one but they can use the collission one.

That would apply to any OS. Is there any OS that uses a password hashing function which is actually a secret. I've easily cracked Vista passwords using rainbow tables. Even if it's not open-source, you can't keep encryption methods a secret for long. If anyone besides an admin gets hashed passwords for any system, it should be considered a security problem.

Doesn't linux use salting to make cracking with rainbow tables exponentially more difficult. Or maybe I don't fully understand the concept of rainbow tables.

By the way, I think encryption refers to data which can be decrypted. Hashing is a computed representation of data which typically cannot be reversed. You can, however, compute hashes of random passwords until you find a matching hash.

---

### Post by hyper_ch on 2008-09-18
both is encryption but they serve differnet uses...

generally if you input a password it undergoes a function and then it will be compared to what is stored. If the stored entity is equal with the one undergone the function the you are granted access.

So what you do with rainbow tables is just to start encrypting random data and store both, the unencrypted and the other one. At some point you will get collissions where two passwords are being encrypted to the same string. In that case you can use either one to unlock. This means if you have a rainbow table of many, many encrypted passwords then you'll just look if you can find a collission and then you know another password that you can use to gain access.

---

### Post by cdenley on 2008-09-18
> **hyper_ch said:**
> both is encryption but they serve differnet uses...

generally if you input a password it undergoes a function and then it will be compared to what is stored. If the stored entity is equal with the one undergone the function the you are granted access.

So what you do with rainbow tables is just to start encrypting random data and store both, the unencrypted and the other one. At some point you will get collissions where two passwords are being encrypted to the same string. In that case you can use either one to unlock. This means if you have a rainbow table of many, many encrypted passwords then you'll just look if you can find a collission and then you know another password that you can use to gain access.

Then it sounds like I do understand. Ubuntu uses MD5 hashing for passwords. It uses an 8 character salt. The MD5 hash was generated by using the actual password in addition to the salt. The rainbow tables would have to be computed using the salt for the given password, or every possible salt value for any given password. This would be pointless, and you're better off computing hashes on the fly when you have the correct salt. Or do I not understand correctly?

---

### Post by mdlefave on 2008-09-19
Does Ubuntu use salts?

---

### Post by cdenley on 2008-09-19
> **mdlefave said:**
> Does Ubuntu use salts?

Yes. MD5 uses an 8 character salt. I think DES was a 2 or character salt. Ubuntu uses MD5.

---

### Post by ds[de] on 2008-09-19
> **cdenley said:**
> The rainbow tables would have to be computed using the salt for the given password, or every possible salt value for any given password. This would be pointless, and you're better off computing hashes on the fly when you have the correct salt. Or do I not understand correctly?

No, that is correct.


Regards,
ds[de]

---

### Post by kevdog on 2008-09-28
Can you change from md5 to lets say whirlpool hashes or sha512 or sha256 hashes.  I had the md5 algorithm!!

---

### Post by cdenley on 2008-09-28
> **kevdog said:**
> Can you change from md5 to lets say whirlpool hashes or sha512 or sha256 hashes.  I had the md5 algorithm!!

You will be able to use sha512 in intrepid.
[https://bugs.launchpad.net/ubuntu/+source/pam/+bug/245786](https://bugs.launchpad.net/ubuntu/+source/pam/+bug/245786)

For hardy, probably the best you could use is blowfish.
[http://ubuntuforums.org/showthread.php?t=300208](http://ubuntuforums.org/showthread.php?t=300208)

---

