---
title: "How to generate TPM 2.0 keys?"
date: 2016-06-14
forum: Security
---

### Post by ckotichas on 2016-06-14
[COLOR=#3D3D3D]Sorry if this has been posted already, but so far we have been unable to find any information or tutorials on TPM 2.0 key generation anywhere. 

We have had tons of success generating TPM 1.2 keys in Trusty Tahr (14.04 LTS). Unfortunately we've been unable to figure out how to do this in Xenial Xerus (16.04 LTS), partly because the key generation process has changed in TPM 2.0. 
[/COLOR]
Supposedly we can do this with tpm2-tools:
```
[COLOR=#3D3D3D]apt-get install tpm2-tools[/COLOR]
```[COLOR=#3D3D3D]
Then we can issue commands with:
```
[COLOR=#3D3D3D]resourcemgr[/COLOR]
```[/COLOR]
If our understanding is correct, the process is as follows:
 [COLOR=#3D3D3D]1. Take ownership of the module
2. Create a primary key
3. Create a signing key[/COLOR]

Our questions are:
1. Are we approaching this process correctly? Are we missing an important step?
2. Would there happen to be a TPM 2.0 key generation tutorial?

Thank you for your help.

---

