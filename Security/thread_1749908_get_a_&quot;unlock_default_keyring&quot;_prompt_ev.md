---
title: "get a &quot;unlock default keyring&quot; prompt every time i login"
date: 2011-05-05
forum: Security
---

### Post by Trimatrix on 2011-05-05
I always get this prompt in Ubuntu and the option to auto login is grayed out so i cant choose it .  :(
Its not a serious issue but does anybody know how to unlock it when i sign in on Ubuntu 11.4?

---

### Post by madvinegar on 2011-05-05
Same problem here. Anyone has a solution?

---

### Post by CandidMan on 2011-05-05
I think this problem can be fixed with Seahorse, Open it up and under the passwords tab, select 'default' keyring and change the password to match the login password. 

My fresh install of Natty only has the Login keyring so everything is unlocked, but basically you want the Login keyring to be able to unlock the Default keyring.

Failing that try going to 'About Me' in the top right corner and 'changing' your password to the login password

---

### Post by Trimatrix on 2011-05-05
yup that didn't work :-/

---

### Post by CandidMan on 2011-05-06
Could you post on here what keyrings you have under the passwords. Not the actual contents, unless 'default' is under your 'login' keyring.
Otherwise you could try deleting the keyrings and entering all of your passwords again.
Ah, I think the answer may be here [http://ubuntuforums.org/showthread.php?t=1690460](http://ubuntuforums.org/showthread.php?t=1690460)
Had the same problem

---

