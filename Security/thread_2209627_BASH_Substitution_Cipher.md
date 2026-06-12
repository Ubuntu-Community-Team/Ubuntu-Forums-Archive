---
title: "BASH Substitution Cipher"
date: 2014-03-06
forum: Security
---

### Post by CosmicFlux on 2014-03-06
Hi,

I've written a small bash script to implement basic encryption, utilizing **sed** to read a file and substitute plain text letters for substitution symbols (~¬|_#@ etc.), for ASCII files I have in my home directory. How could I ascertain how secure this is? 

I'm aware that Ubuntu supports GPG and ENCFS, and that those are better tools for encryption (I, in fact, use both of these on my system, as well as accessing the Web through a VPN) but I was just playing around with Bash and wondered if this basic type of encryption is is any way useful?


Regards,

Flux

---

### Post by steeldriver on 2014-03-06
Well it's not really my field, but any monoalphabetic substitution cipher is insecure against [frequency analysis]("http://en.wikipedia.org/wiki/Frequency_analysis") if the plaintext is in just about any known natural language

---

