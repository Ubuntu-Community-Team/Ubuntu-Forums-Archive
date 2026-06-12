---
title: "Tripwire installation error"
date: 2015-08-14
forum: Security
---

### Post by priya_bandhavi on 2015-08-14
Hi,

I am getting the following issue in-spite of many times uninstalling and reinstalling the tripwire.
priya@challenger:~$ tripwire --check

  Error: Keyfile Read/Write error. 
##/etc/tripwire/site.key
 ##Exiting...  Any help would be appreciated . 

I wanted to prevent the default display of Integrity check reports on the screen during an integrity check. I tried modifying the code but was not successful.
 Any leads on this would also be helpful.

 
Thank You

---

### Post by CharlesA on 2015-08-14
Have you tried running it with sudo?

It probably needs write access to the key and only root would have that level of access.

---

### Post by priya_bandhavi on 2015-08-16
Thanks! It worked:D

---

