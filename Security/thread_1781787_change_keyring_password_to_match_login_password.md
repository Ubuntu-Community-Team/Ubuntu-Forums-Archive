---
title: "change keyring password to match login password"
date: 2011-06-14
forum: Security
---

### Post by litspliff on 2011-06-14
everytime i try to vnc to my box, it pops up the keyring authentication, which is obviously a huge problem when logging in remotely.

how do i change my keyring password to match my login password?

---

### Post by litspliff on 2011-06-20
really? nobody knows?

---

### Post by Dave_L on 2011-06-20
Applications >> Accessories >> Passwords and Encryption Keys

Or from the shell, "seahorse".

Right-click on "Passwords: login" and select "Change Password".

---

### Post by litspliff on 2011-06-20
hey! thanks a lot.

i found that a few days ago, but i thought it would change my login password.
thanks for clearing that up!:guitar:

---

### Post by Dave_L on 2011-06-21
Yes, the terminology is confusing.  "Passwords: login" refers to a container of passwords for logging in to "other" places.

"seahorse" seems to be a front-end for "gpg". If that's correct, I'd like to know how to change the login keyring password from the shell, using only the "gpg" command. I'd looked at "man gpg", but it's very complex.

---

### Post by white.noise on 2012-06-13
Hi,

Thanks for that. I have never bothered trying to change it before now.

---

