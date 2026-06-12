---
title: "How effective is the encryption software that comes with Ubuntu?"
date: 2010-10-10
forum: Security
---

### Post by BlackRoseBud on 2010-10-10
I'm interested in knowing how effective the encyption software that comes with Ubuntu is.  I'm refering to the software that allows you to encypt your home directy and if using the altnerative disk, the entire hard drive partition.  I realize ecryption effeciveness is largely determined by how complex the password or key is, but are there any backdoors or methods for hackers or government agencies to recover the key or bypass the encryption without brute force techniques?

---

### Post by rookcifer on 2010-10-10
> **BlackRoseBud said:**
>  I realize ecryption effeciveness is largely determined by how complex the password or key is, but are there any backdoors or methods for hackers or government agencies to recover the key or bypass the encryption without brute force techniques?

No.  Or at least if there is, no one has found them (the code is open-source).  Use a long key and you'll be as secure as is possible with any publicly known methods.  It's doubtful that anyone can break the crypto provided you use it correctly.

I must qualify this statement by saying that crypto is a tough subject because it requires so much expertise by those trained in the field.  Any old C coder probably will not be skilled enough to detect any funny business (even with open-source code) if it's done cleverly enough (this is evidenced by the Debian SSL debacle, where a code maintainer not trained in cryptography accidentally screwed up the RNG and made the whole system insecure.  He did this by changing only one line of code).  It will take an expert in the field (a la Bruce Schneier) as well as someone skilled in coding to detect something strange.  However, with the code open, it does provide a sense of comfort because anything strange will likely be detected in time.

---

### Post by BlackRoseBud on 2010-10-10
> **rookcifer said:**
> No.  Or at least if there is, no one has found them (the code is open-source).  Use a long key and you'll be as secure as is possible with any publicly known methods.  It's doubtful that anyone can break the crypto provided you use it correctly.

I must qualify this statement by saying that crypto is a tough subject because it requires so much expertise by those trained in the field.  Any old C coder probably will not be skilled enough to detect any funny business (even with open-source code) if it's done cleverly enough (this is evidenced by the Debian SSL debacle, where a code maintainer not trained in cryptography accidentally screwed up the RNG and made the whole system insecure.  He did this by changing only one line of code).  It will take an expert in the field (a la Bruce Schneier) as well as someone skilled in coding to detect something strange.  However, with the code open, it does provide a sense of comfort because anything strange will likely be detected in time.

Okay, thanks!  That's what I wanted to hear.  :-)

---

### Post by HermanAB on 2010-10-11
It is very effective.  Governments and military commonly use LUKS up to the level of Secret.  There are lots of Linux systems in government use - mostly Redhat, but I have seen Ubuntu as well.

---

