---
title: "How can i convert a ssh-keygen generate keypair to putty format using puttygen"
date: 2008-04-16
forum: Security Discussions
---

### Post by sefs on 2008-04-16
Hi all 

I've generate a key pair with ssh-gen but the private key is not recognised in putty.

I think i have to convert it to a putty format but I am not sure how to do this with puttygen under ubuntu, can someone point me in the right direction??

Thanks.

---

### Post by Dr Small on 2008-04-16
Create the keyset in puttygen.

---

### Post by sefs on 2008-04-17
Thanks for that.

It turns out also that once putty-tools are installed you can use puttygen on ubuntu to actually do the conversion to putty format with the following command...

```

puttygen /path/to/ssh-gen-privatekeyfile -O private -o /path/to/putty-formatted-privatekeyfile

```

---

### Post by Dr Small on 2008-04-17
Geesh. I wish I would have known that :p
I downloaded PuTTYGen as a windows binary and ran it with wine, just to generate a portable ssh key to be used with putty! :D

Glad you got the problem solved.

Dr Small

---

