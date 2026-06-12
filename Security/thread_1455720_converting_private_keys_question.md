---
title: "converting private keys question"
date: 2010-04-16
forum: Security
---

### Post by methodtwo on 2010-04-16
Hi there
I have a private key to use with openssl.It's in PEM format.That is it is: ASN.1 + DER + base64.The problem is that i can't use it with openssl.I origionally just copied and pasted the key from a simple text file.When i do:
```
openssl rsautl -sign -in textfile -inkey privatekey.pem -out result
```
i get: unable to load key
The problem is that base64 only allows a limited line length.But i don't know how to alter the private key so that it will work.
Thank you for your time
regards methodtwo

---

### Post by methodtwo on 2010-04-16
I'm not sure whether the problem is the line length of the base64 encoded private key.I've checked the number of characters per line in the key and it is 64.Does this mean that the problem is the base64 encoded key and line length or not?.I don't know what the problem is but when ever i run an openssl command that includes the private key i get: unable to load private key.
Even if i run:
openssl rsa -in privatekey.pem -text 
i still get: unable to load private key
So i don't know what the problem is. As i mentioned earlier i copied and pasted the key from a text file. 
Thankyou for your time
regards methodtwo

---

