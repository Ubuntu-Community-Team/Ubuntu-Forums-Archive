---
title: "openssl privatekey formatting"
date: 2010-04-13
forum: Security
---

### Post by methodtwo on 2010-04-13
Hi there
I have a private key base64 encoded.The trouble is that because it's base64 encoded it has a maximum line length of 64 chars.How do i formatt the base64 encoded private key so that the maximum line length of 64 chars doesn't matter and i can then use the private key to sign textfiles etc?
regards methodtwo

---

### Post by methodtwo on 2010-04-13
By the way.The way that this problem is showing itself is that when i do:
```
#openssl rsautl -sign -in textfile -inkey privatekey.pem -out answer
```
i get: unable to load private key
So i believe that if i knew how to format this private key properly it will work, right?
regards methodtwo

---

### Post by methodtwo on 2010-04-13
By the way this private key was origionally just copied and pasted text.Not imported from a key server

---

