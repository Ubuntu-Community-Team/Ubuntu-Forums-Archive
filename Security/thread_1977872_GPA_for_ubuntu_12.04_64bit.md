---
title: "GPA for ubuntu 12.04 64bit"
date: 2012-05-10
forum: Security
---

### Post by sefs on 2012-05-10
Hi all,

I used to love using GPA the privacy assistant.  Now i have gone 64-bit it is not in the repos.  Any one found out how to get it back?

Thanks.

---

### Post by DanR01 on 2012-05-12
I have installed GPA 0.70 on 12.04 64 bit Ubuntu without any issues from

[HTML]http://packages.debian.org/lenny/amd64/gpa/download[/HTML]

I was unable to get the newer version to work correctly - it failed to display keys. I tried the deb package and compiling from source without luck. I used GDebi to install the package. 

It would be great if the newer version could be packaged for Ubuntu. Seahorse is a very poor replacement IMHO.

Best wishes

---

### Post by sefs on 2012-05-12
Bless you my son. Thanks for that.  Seahorse is ok but, it does not have the file manager feature that gpa has or the clipboard encryption/decryption (That I know about) which I wanted.  GPA is indeed great.

They are up to gpa_0.9.0-1.1_amd64.deb now.
[http://ftp.ca.debian.org/debian/pool/main/g/gpa/](http://ftp.ca.debian.org/debian/pool/main/g/gpa/)

---

### Post by ottosykora on 2012-05-12
Q: will the GPA work with gpg1.4 or will it work only with gpg2?

---

### Post by sefs on 2012-05-12
> **ottosykora said:**
> Q: will the GPA work with gpg1.4 or will it work only with gpg2?

I read somewhere that it requires gpg2.  I would have to try and find where I saw that.

---

### Post by ottosykora on 2012-05-13
OK , I tried the GPA, but I have to say it does not work at all properly. I can make key managemet with it half way, but this is about all.

Encryption works, but then it is not able to decrypt what it did encrypt and it is not able to verify sig it has created.

Hmm, rather junk.

I know I have it under windows running too, it has there the same problems, never works really.

---

