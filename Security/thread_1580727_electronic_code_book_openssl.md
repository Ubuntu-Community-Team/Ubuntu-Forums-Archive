---
title: "electronic code book openssl"
date: 2010-09-23
forum: Security
---

### Post by koba101 on 2010-09-23
don't know if anyone has ever tried this before.  But I'm trying to demonstrate the weakness of electronic code book block encryption by using using openssl.  There is an option in openssl in openssl to select dec-ecb.  So  I gave it a shot.

So I fed the following into the terminal

openssl des-ecb -kfile deskty -in test.txt -out someEncryptedFile


However, everytime, I get a different output.

Is there any parameter i need to set in openssl to get the same outpu?

---

### Post by anomie on 2010-09-23
You mean you're using openssl's enc(1) program? 

Try using the **-nosalt** option. (I'm not sure what the default is on Ubuntu systems.)

---

### Post by koba101 on 2010-09-23
Thanks

---

