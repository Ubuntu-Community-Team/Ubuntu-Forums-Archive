---
title: "Can't get PGP get to work to open file"
date: 2008-11-29
forum: Security
---

### Post by rodrigolautaro on 2008-11-29
Hi folks

On one of my computers I got a file encrypted using a pgp key of my own(the file was like file.pgp). I had to export it to anoher computer, so I exported the pgp key to an .asc file, wich I copied to that pc and import it. Then I signed the key. Now when I righ-click the file and select uncrypt file, an error appears saying something like "The file could not be uncrypted. The uncrypting failed. Probably you don't have the uncrypting key". Thanks and sorry for my english, because my ubuntu it's in spanish.


Rodrigo

Dell Inspiron 1525
Ubuntu 8.04

---

### Post by Dr Small on 2008-11-30
Did you export the private key and import it also?
If not, you need to do that, in order to decrypt the file.

---

### Post by rodrigolautaro on 2008-11-30
How can I do that? Please tell me.

Thanks

---

### Post by rodrigolautaro on 2008-11-30
I've found the solution

 gpg --export-secret-key -a > secret.key


Then I copy the secret.key file to the other pc and double click on it.

Thanks

---

