---
title: "Home folder permissions"
date: 2011-06-08
forum: Security
---

### Post by erotavlas on 2011-06-08
Hi,

I have installed Ubuntu 11.04 and I have two users. One is the root/sudo user while the other is a standard user.
The root/sudo user can access to the home folder of standard user. Is it sufficient to protect it by chmod 700 /home/username. In this case can the root read the file inside the home folder? If not is there a way to protect it?

Thank you

---

### Post by jaacko on 2011-06-08
Hi!

I don't think anything can be completely hidden from the root user. Only solution I can come up with is to create an encrypted volume (using Truecrypt for example) and storing files you don't want the root to see in there. The root user can still see the encrypted volume file, though.

---

### Post by mikewhatever on 2011-06-08
What's the point of having the root user on the system if you want to 'protect' some files from it?

---

### Post by bodhi.zazen on 2011-06-08
> **erotavlas said:**
> Hi,

I have installed Ubuntu 11.04 and I have two users. One is the root/sudo user while the other is a standard user.
The root/sudo user can access to the home folder of standard user. Is it sufficient to protect it by chmod 700 /home/username. In this case can the root read the file inside the home folder? If not is there a way to protect it?

Thank you

The only "protection" you have from the root user, or physical access, is encryption.

Ubuntu offer the option to encrypt your home directory as a part of the installation or you can do so post install.

Alternately you can use Cryptkeeper, LUKS, or Truecrypt.

---

