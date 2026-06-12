---
title: "Password security"
date: 2010-01-15
forum: Security
---

### Post by J V on 2010-01-15
A few questions on password security

How are passwords stored? Standard MD5? Is it possible to add a salt?

Is there a way to secure the salt? The file housing the hashed passwords?

Is it even possible to keep someone with physical access to your system from getting in?

Could I set up a counter, so that after 5 wrong passwords it wipes the ecryptfs passphrase? (quick way to wipe the data)

Is it even possible to stop them from resetting that counter every 4 mistakes?

rainbow tables have put a dent in my faith in passwords as you can probably tell...

---

### Post by munky99999 on 2010-01-15
It's fairly trivial to get the passwords from unix/linux even the latest distros.

basically they will be /etc/passwd and /etc/shadow. You take both files in order to be able to brute force it. I think they went to sha1 for it, but that's not so much the security; it's that you basically need root access in order to gain access to the passwords.

Ubuntu uses seahorse as the front end and apparmor to enforce the root access only factor.

I think your questions are more worriesome as it kinda implies you are going to be having significant physical access problems.

If that's the case. Try to move the authentication off the box entirely and use LDAP or something similar.

---

### Post by J V on 2010-01-15
Well I would still like a salt they can't find :P

---

### Post by cdenley on 2010-01-15
Ubuntu started using PAM's SHA-512 implementation a few version back. Before that, MD5 was the default. You should note that the scheme used for password hashing in linux is not the same as the hashing scheme it was named after. Even with the password hash, cracking it would be no easy task. Both MD5 and SHA-512 use salts, which makes precomputed hashes impractical.
[http://people.redhat.com/drepper/SHA-crypt.txt](http://people.redhat.com/drepper/SHA-crypt.txt)
Every system has to store the password hashes somewhere in order to use password authentication. This includes Windows, Mac, and BSD's.

---

### Post by J V on 2010-01-15
not particularly, just encrypt the "startup code" which in turn would be different... in fact if the whole linux system could switch to ecryptfs...

---

### Post by cdenley on 2010-01-15
> **J V said:**
> not particularly, just encrypt the "startup code" which in turn would be different... in fact if the whole linux system could switch to ecryptfs...

Not sure what you mean "startup code", but you can encrypt your entire disk (except /boot) or simply /etc which contains your shadow file by using the alternate installer. Encryption is the only way to protect from physical access, but it is still possible to retrieve encryption keys from memory.

---

### Post by J V on 2010-01-15
no i meant like double encryption ala ecryptfs

---

### Post by cdenley on 2010-01-15
> **J V said:**
> no i meant like double encryption ala ecryptfs

Double encryption?

---

### Post by J V on 2010-01-15
everythings encrypted by a random value which is encrypted by the password, if the system worked like that it would be impossible to bruteforce the password, they would need to test one, test the second one, and then confirm weather the files were properly decrypted...

No more rainbow tables, much more difficult to do :P

---

### Post by cdenley on 2010-01-15
> **J V said:**
> everythings encrypted by a random value which is encrypted by the password, if the system worked like that it would be impossible to bruteforce the password, they would need to test one, test the second one, and then confirm weather the files were properly decrypted...

No more rainbow tables, much more difficult to do :P

As I already said, the password hashes are salted, so using precomputed hashes (rainbow tables) is impractical.

---

### Post by J V on 2010-01-15
Oh of course, duh xD

My bad, anyway, yeah, is the salt the same on every ubuntu? Someone might think of making rainbow tables just for ubuntu if it becomes so popular...

---

### Post by cdenley on 2010-01-15
> **J V said:**
> Oh of course, duh xD

My bad, anyway, yeah, is the salt the same on every ubuntu? Someone might think of making rainbow tables just for ubuntu if it becomes so popular...

No, the salt is completely random. Setting the same password twice results in a different salt which means a different hash.
```

cdenley@ubuntu:~$ mkpasswd -m SHA-512 test
$6$[COLOR="Red"]zA/7.93TdDuJ6BoV[/COLOR]$tqe5Yd43rC7cBL5ahOowJCc26SRy7GlI5gSTIpk6nQrCETJATvKJC6kAx9zczPfnO1GM2WPEdhpgUKg2zjwKU1
cdenley@ubuntu:~$ mkpasswd -m SHA-512 test
$6$[COLOR="Red"]8VWUeEZIwO9r04MV[/COLOR]$AdWDTUyElSlI8c2eaVwSa3OPqnJoPfbrFTI2VF1TdmW.u9GbgP43Qs64KEiXiLnNLRqKAfyl2ntPaTAynCQ7r1

```
The salts are in red.

---

### Post by Zimmer on 2010-01-15
> **J V said:**
> everythings encrypted by a random value which is encrypted by the password, if the system worked like that it would be impossible to bruteforce the password, they would need to test one, test the second one, and then confirm weather the files were properly decrypted...

No more rainbow tables, much more difficult to do :P

Unless you are thinking about encrypting your disks your data (Win or Linux) is open for anyone with a live CD and physical access to your machine..
Interesting piece here, though, but aimed at WI FI 
[https://www.grc.com/passwords.htm](https://www.grc.com/passwords.htm)

---

