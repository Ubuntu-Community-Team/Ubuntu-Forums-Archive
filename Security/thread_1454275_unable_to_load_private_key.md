---
title: "unable to load private key"
date: 2010-04-14
forum: Security
---

### Post by methodtwo on 2010-04-14
Hi there
I've copied and pasted a private key that i need to use with openssl.It was copied from a simple text file.It is an rsa private key. However when ever i try to use the key,for example to try and sign a textfile, as in:
```
openssl rsautl -sign -in textfile -inkey privatekey -out result
```
Then i get the message: unable to load private key
I think the key needs formatting but i don't know and can't find how to do it
Any help would be great
regards methodtwo

---

