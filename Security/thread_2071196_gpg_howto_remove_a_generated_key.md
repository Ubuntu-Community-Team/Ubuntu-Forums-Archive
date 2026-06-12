---
title: "gpg howto: remove a generated key"
date: 2012-10-14
forum: Security
---

### Post by emonti on 2012-10-14
Hi,

I was experimenting with GPG during the installation of Truecrypt ([http://ubuntuforums.org/showthread.php?t=1970947](http://ubuntuforums.org/showthread.php?t=1970947)) and had a maintenance/housekeeping question. 

I created a key using:

```
gpg --gen-key
```I later forgot my passphrase and so I wanted to start over. I figured that since I hadn't at that stage used my private key to sign anything, it should be a simple case of deleting my key and recreating it.

First question is: Is this correct? 

Second question is: How do I go about deleting and recreating? Could simply remove it from my public and secret key rings and repeat the creation process using '--gen-key'?

And finally, the third question is: do I have to explicitly revoke my signature from any external servers at this early stage? I got as far as a failed attempt to sign the Truecrypt public key.

Thanks for any advice.

---

### Post by chadk5utc on 2012-10-14
yes as long as its not really needed/useful delete it. a quick search on google found: [https://weblion.psu.edu/trac/weblion/wiki/DeleteGpgKey](https://weblion.psu.edu/trac/weblion/wiki/DeleteGpgKey)
I would remove old/unused keys and start again...

---

