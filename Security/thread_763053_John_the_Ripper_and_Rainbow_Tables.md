---
title: "John the Ripper and Rainbow Tables"
date: 2008-04-22
forum: Security
---

### Post by DenKain on 2008-04-22
My question is simply can JTR use a Rainbow Table and is there a RBT generator that I can use in Ubuntu? I ask because I thought that RBTs only applied to NT and LM hashes but I have seen some MD5 RBTs as of late.

I have searched google.com and everything I find is just comparing JTR to a program that uses a RBT.

---

### Post by wirelessmonkey on 2008-04-22
Use john to create your dictionary file, then CowPatty to generate your rainbow tables.

---

### Post by stmurray on 2008-04-25
I'm not sure how CowPatty works, but the problem with Unix passwords and rainbow tables is salt.  Salt is a (random) string that is mixed in with the password before the password is hashed.  The salt value gets stored with the password hash.  So to create rainbow tables for Unix (Windows doesn't use salt), you have to not only hash (and store) all the potential passwords , but you have to hash each potential password and each salt value for that password .  If the salt range is large enough, the rainbow tables become to huge to be of value and you go back to real-time password brute-force methods (once you know the salt of the password you are trying to crack).

for a great explanation on this (and "why you should never create your own password authentication method", thrown in for free) see;

[http://www.matasano.com/log/958/enough-with-the-rainbow-tables-what-you-need-to-know-about-secure-password-schemes/](http://www.matasano.com/log/958/enough-with-the-rainbow-tables-what-you-need-to-know-about-secure-password-schemes/)

---

### Post by Monicker on 2008-04-25
WPA PSK uses the ssid to salt the passphrase.  So, you need to create tables for each ssid which you want to run them against.  There are some precomputed tables which you can download.  I have one such set; its almost 8gb in size and covers some of the most common ssid, and only about 1 million passwords.

A strong WPA PSK is not going to be found by a dictionary attack.

---

