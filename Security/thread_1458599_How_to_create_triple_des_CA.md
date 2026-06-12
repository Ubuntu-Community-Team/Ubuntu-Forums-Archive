---
title: "How to create triple des CA"
date: 2010-04-20
forum: Security
---

### Post by weather15 on 2010-04-20
I am currently setting up a web server with SSL and I have recently realized the new 4096 bit certificate type that is triple des. I am interested in creating my own certificate authority with triple des 4096 bit CA and a 4096 server cert. I am also interested in using client certificates requiring that a certificate be on the client to negotiate a connection to the server. How could I do this?

---

### Post by HermanAB on 2010-04-20
Uhmmm, are you sure?  AFAIK triple DES is obsolete and no longer secure.

---

### Post by uRock on 2010-04-20
I recently read that some banks are still using it for PIN numbers, but I think most sites are using the x.509 for CAs.

---

### Post by weather15 on 2010-04-28
I am trying to create a CA that uses the strongest encryption type possible.

---

### Post by movieman on 2010-04-29
> **HermanAB said:**
> Uhmmm, are you sure?  AFAIK triple DES is obsolete and no longer secure.

Triple-DES is still pretty secure, though more modern encryption algorithms are preferred. Single-DES is hopelessly insecure.

I'm not sure how it relates to the CA, though: I don't think the certificate specifies the algorithms the server can use, just the key?

---

### Post by rookcifer on 2010-04-29
> **HermanAB said:**
> Uhmmm, are you sure?  AFAIK triple DES is obsolete and no longer secure.

Not true.  The old original DES (which used the original Lucifer cipher, I believe) is insecure but triple DES is not.  

The story behind Lucifer is rather interesting because it was originally released with a default 128 bit key length.  It was submitted to the NSA as the candidate for "DES" in the 70's.  The NSA "analyzed" it and later said they recommend the key be shortened to 56 bits.  Most people at the time thought (probably correctly) that the NSA could not break it, so they shortened it to make brute forcing easier.  There was actually a bit of controversy about it and a lot of private sector crypto experts were furious.

At any rate, triple DES is still considered secure.

---

