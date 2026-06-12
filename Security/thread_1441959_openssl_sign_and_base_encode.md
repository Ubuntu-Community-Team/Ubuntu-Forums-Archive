---
title: "openssl sign and base encode"
date: 2010-03-29
forum: Security
---

### Post by methodtwo on 2010-03-29
Hi there
i need to know more about openssl.In particular i'm having problems with some basic coammand-line stuff to do with signing and base64 encoding.You'll have to excuse me but i'm a security n00b.
What is the command for signing some text file with a given private key and then after that base64 encoding the same file.Can this be done with a single command?
what's wrong with:
```
openssl rsautl -sign -in textfile -inkey privatekey.pem enc -base64 -in textfile
```
or should that be:
```
openssl rsautl -sign -in textfile -inkey privatekey.pem | openssl enc -base64 -
```??
Any help to get me to understand these complex commands would be great
methodtwo

---

### Post by noway2 on 2010-03-30
Perhaps this will help: [http://www.madboa.com/geek/openssl/#encrypt-base64](http://www.madboa.com/geek/openssl/#encrypt-base64)

---

