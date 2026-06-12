---
title: "how do you change the hash used by yppasswd?"
date: 2011-05-25
forum: Security
---

### Post by robmc2049 on 2011-05-25
Does anyone know how to change the hash used by yppasswd in ubuntu?  The default is DES.  I would like to at least use MD5. Changing pam_unix2.conf doesn't seem to be doing anything.

thanks

---

### Post by robmc2049 on 2011-05-25
Figured it out... add nis to the end of the line 

password	[success=1 default=ignore]	pam_unix.so obscure sha512

in /etc/pam.d/common-password

Also, there seems to be a bug where it asks for your password twice when you use sha512.  Could be related to other configuration.  If you change it to MD5, no problems.

---

### Post by Joe of loath on 2011-05-25
MD5 has been broken, don't use it.

---

### Post by robmc2049 on 2011-05-26
Bug was related to the way I was including the unix2 pam module for blowfish support. I have since fixed that and switched back to sha512.  Either way, hashing passwords regardless of the algorithm or salting isn't ideal.  Our security model around here is admittedly not that strong.

---

