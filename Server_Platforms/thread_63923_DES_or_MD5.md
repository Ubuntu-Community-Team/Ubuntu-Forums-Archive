---
title: "DES or MD5"
date: 2005-09-09
forum: Server Platforms
---

### Post by Radi0ShacK on 2005-09-09
hi all,
i was just wondering how to know if my system "or any system" whether it is using DES or MD5 hash algorithm for encrypting users acconuts passwords in /etc/shadow. Also which one is frequently used or is there another one "another encryption technique which i dont know?"
thanks alot

---

### Post by LordHunter317 on 2005-09-09
On Linux, salted MD5 is normally used for storing passwords.

---

### Post by Radi0ShacK on 2005-09-10
thanks alot :) do u know how to get more technical information about this salted MD5 ?? "man page info ...etc"

---

### Post by LordHunter317 on 2005-09-10
What specifically do you want to know?

I can't find anything authortative about exactly how the algorithm is performed on my system, looking at the glibc sourcecode may be your best bet.

---

### Post by Radi0ShacK on 2005-09-11
i just want to know how to disable/enable null passwords and how the salted md5 algorithm performed and does all linux machines use thee same method or not "may be the same salt ...etc"

---

### Post by Dax0r on 2005-09-14
Blowfish.

---

### Post by Radi0ShacK on 2005-09-14
THANKS, but i think ubuntu is using MD5 hash encryption how can i chane it to use Blowfish?
second is there any library that i can use to implement blowfish algorithm like crypt(3) for DES/MD5 ??
thanks alot again :)

---

