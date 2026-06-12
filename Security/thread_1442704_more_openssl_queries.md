---
title: "more openssl queries"
date: 2010-03-30
forum: Security
---

### Post by methodtwo on 2010-03-30
Hi there
when i do:
```
openssl rsautl -sign -in textfile.txt -inkey myprivatekey.pem
```
i get:
```
unable to load Private Key
```
I have copied and pasted the myprivatekey.pem from the source that issued it.It was not imported from a key server.
So why can't the private key be loaded?.What should i do in order to get it to work?
all i need to do is sign the textfile with my given private key!

---

