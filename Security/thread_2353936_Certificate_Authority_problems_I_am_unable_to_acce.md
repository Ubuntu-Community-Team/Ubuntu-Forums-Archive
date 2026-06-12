---
title: "Certificate Authority problems: I am unable to access the ./demoCA/newcerts directory"
date: 2017-02-26
forum: Security
---

### Post by imnewuser1111 on 2017-02-26
Hello there, I am a new user here and currently taking a computer security course in my university. I would like to get some help because I was kind of giving up of finding a solution to my problem. I also tried googling it up on Google but I still cannot manage getting the right answer. I am not here asking for anyone to do my homework, rather give me a piece of advice on how to do the task 3.2 step 3 properly.

this is the question file: [http://www.cis.syr.edu/~wedu/seed/Labs/Crypto/Crypto_PublicKey/Crypto_PublicKey.pdf](http://www.cis.syr.edu/~wedu/seed/Labs/Crypto/Crypto_PublicKey/Crypto_PublicKey.pdf)

I keep on getting this message all over again. 
[INDENT][B]I am unable to access the ./demoCA/newcerts directory
[/B]
[B]./demoCA/newcerts: No such file or directory
[/B]
[/INDENT]


Creating /demoCA/demoCA/(files), changing the policy from match to anything, changing its case from upper to lower, etc. But I still receive the same message.

Does anyone here encounter this before? Would you mind telling me the steps to get the answer?

---

### Post by joebeasley on 2017-03-13
Page 2 at the top. You must create the directories manually.

mkdir ./demoCA
mkdir ./demoCA/newcerts
mkdir ./demoCA/certs
mkdir ./demoCA/crl
mkdir ./demoCA/serial

---

