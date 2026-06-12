---
title: "how to recover OpenPGP key?"
date: 2010-11-17
forum: Security
---

### Post by lordamit on 2010-11-17
Hi.
Long story short, I formatted my lucid, installed maverick, and want to recover the openPGP key I made when creating an account in launchpad.

I have these information from when I made it.


---------------------------------
pub   2048R/1F488295 2010-09-11
uid <MyName_here> <my_email@address.com>
sub   2048R/<edited_for_security purposes)> 2010-09-11



The fingerprint
The passphrase

The mail details sent to/received from launchpad. 

I thought if I export the key, I only have to import it in new installed Ubuntu.
The exported key is in .asc extension.

problem is, I can not verify it.

What do I do?

---

### Post by CharlesA on 2010-11-17
If you don't have the private key, you'll have to recreate the keypair and upload it to the key server.

---

### Post by bodhi.zazen on 2010-11-17
> **lordamit said:**
> Hi.
Long story short, I formatted my lucid, installed maverick, and want to recover the openPGP key I made when creating an account in launchpad.

I have these information from when I made it.


---------------------------------
pub   2048R/1F488295 2010-09-11
uid <MyName_here> <my_email@address.com>
sub   2048R/<edited_for_security purposes)> 2010-09-11



The fingerprint
The passphrase

The mail details sent to/received from launchpad. 

I thought if I export the key, I only have to import it in new installed Ubuntu.
The exported key is in .asc extension.

problem is, I can not verify it.

What do I do?

See :

[https://help.ubuntu.com/community/GnuPrivacyGuardHowto#Backing%20up%20and%20restoring%20your%20key%20pair](https://help.ubuntu.com/community/GnuPrivacyGuardHowto#Backing%20up%20and%20restoring%20your%20key%20pair)

[http://www.debuntu.org/how-to-import-export-gpg-key-pair](http://www.debuntu.org/how-to-import-export-gpg-key-pair)

---

