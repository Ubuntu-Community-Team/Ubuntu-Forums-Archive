---
title: "Root password"
date: 2009-12-24
forum: Security
---

### Post by neotifa on 2009-12-24
Is there anyway how to at least secure root passwords?
I know there is a way how to reset the password, so im asking how to protect it best way i can

---

### Post by ajgreeny on 2009-12-24
If you follow the default, there is no root password in ubuntu, so this is not needed.

---

### Post by noway2 on 2009-12-24
Ajgreeny is correct, but to answer the question that may have been the intent...assuming the OP meant the default user password that is utilized with sudo....

Generally speaking, it is a good idea to keep this password strong and secure.  If someone were to hack your system, either remotely or to gain physical access to it, with this password they could do a tremendous amount of damage.  There is plenty information available regarding 'strong' passwords that should get you started.

---

### Post by HermanAB on 2009-12-25
In Ubuntu, the default is to have the root password locked.  If you unlocked it, then you can lock it again with:
$ passwd -l root

Always use looooong passwords for everything - at least 9 characters (since common dictionaries go up to 8 characters, but there are longer ones too). I use 12 or 16 character semi-pronounceable and never get hacked.

---

