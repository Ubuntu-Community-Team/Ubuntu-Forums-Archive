---
title: "Changing user passwords hash type"
date: 2008-11-27
forum: Server Platforms
---

### Post by martien on 2008-11-27
Hello. I have my Ubuntu running for few mounts and i want to change users password types - i mean that now in /etc/shadow passwords are stored in with hash, but i want that hash to be md5, not the default one. How can i change the type? Thank you very much in advance

---

### Post by RealPSL on 2008-11-27
You should be able to do this by changing the variable MD5_CRYPT_ENAB to yes in the /etc/login.defs file. New passwords should then be encrypted with md5

---

### Post by martien on 2008-11-28
> **RealPSL said:**
> You should be able to do this by changing the variable MD5_CRYPT_ENAB to yes in the /etc/login.defs file. New passwords should then be encrypted with md5
Well, i did that, then i passwd <user> again and then i did open /etc/shadow to see whats my crypt method, but it was still $1klslsda...., then i rebooted and tried passwd <user> again and its the same. No difference in the method. Any suggestions?

---

### Post by RealPSL on 2008-11-28
It appears that is no longer the setting and it has been moved to /etc/pam.d/common-password. According to that file in hardy the default setting is to use md5 not crypt so you should be okay already.

---

### Post by martien on 2008-11-29
> **RealPSL said:**
> It appears that is no longer the setting and it has been moved to /etc/pam.d/common-password. According to that file in hardy the default setting is to use md5 not crypt so you should be okay already.
Well in /etc/pam.d/common-password i have the following line:
> password   requisite   pam_unix.so obscure md5
and still when i try to change someone's password it appears in /etc/shadow like unix crypt.

---

### Post by RealPSL on 2008-11-29
Martien,

Hashes that start with the "$1$" are md5 hashes

---

