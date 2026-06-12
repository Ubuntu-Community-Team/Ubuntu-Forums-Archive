---
title: "OpenSSL decryption"
date: 2009-01-16
forum: Security
---

### Post by alenis on 2009-01-16
Doing some experiments with OpenSSL command line utility to encrypt/decrypt files, I discovered a strange behaviour. I created a very simple text file named "a" containing this text:

```
prova
```  

I encrypted the file with the command

```
openssl aes-256-cbc -a -salt -in a -out a.enc 

```

using 

```
prova
```

as password.

The command

```
openssl aes-256-cbc -d -a -in a.enc -out a.dec -k prova
```

correctly decrypt a.enc.

Tryng to decrypt with "bimbo" as password, of course, doesn't work and OpenSSL exits with the following message

```
bad decrypt
7563:error:06065064:digital envelope routines:EVP_DecryptFinal_ex:bad decrypt:evp_enc.c:461:
```

However, using "alfiere" as password seems to decrypt the file correctly: the program exits withour error messages, but the decrypted file is unreadable.

If I encrypt the file again, with the same password, "alfiere" is no good anymore, that is to say, the program exits with an error; but other wrong passwords behave as it behaved before: OpenSSL exits without error messages but the decrypted file is no good.

My question is: is this behaviour intended or is it a bug? And how can I check if the decryption was successful without examining the file manually?

Thanks

---

### Post by Nostalos on 2009-01-16
Its working as intended.  OpenSSL assumes you know 2 things about the file you are handing it.  The password and the cipher.   OpenSSL can't do any backwards checks because there is nothing to check against.   It took your original text and did what you want it to.  It does not store any hashes or anything is. its just encrypted text.   And it assumes you know what you want and does it.  If you gave it the wrong cipher or password it is just going to reverse it.

OpenSSL works in a pinch for a quick file encryption.  If you want checks and such I recommend you use PGP or an archiver such as 7zip as they store CRC checksums and the like.

---

### Post by alenis on 2009-01-17
Thanks for the information.

---

