---
title: "PAM issues"
date: 2007-08-07
forum: Server Platforms
---

### Post by smbm on 2007-08-07
Hi

I need some help with some PAM settings. I've been messing around with it for hours but have reached a brick wall!

I'm running Gutsy.

I'm trying to use pam_mount, pam_thinkfinger and pam_keyring (gnome_pam_keyring?) together to mount my encrypted ~ log me into my network with no password and preferably be able to do all this by swiping my finger over the print reader.

So far I've got as far as needing a swipe and then a password to get login and decryption done. I'm ok with this, it's not ideal but not really bad either.

I can't for the life of me figure out how to get the keyring to unlock with this combination!

Does anyone have any tips or guides to point me in the right direction?

Cheers

---

### Post by smbm on 2007-08-08
Anyone? I'm still trying but still haven't figured it out.

---

### Post by smbm on 2007-08-10
Does anyone know of a good PAM tutorial/guide even?

Most of the stuff I've found so far has been pretty cryptic!

---

### Post by redr00ster on 2007-12-20
Did you manage to find a fix for this?

I am having a similar issue, have got fingerprint working for logging in and unlocking screen etc. However now I am prompted to "pam_mount reenter password" to mount my encrypted /home partition after I have swiped.

It would be really nice if swiping the finger could log in and also authenticate the pam_mount operation.

---

