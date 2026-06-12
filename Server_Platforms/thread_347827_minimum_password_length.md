---
title: "minimum password length?"
date: 2007-01-27
forum: Server Platforms
---

### Post by JimTDI on 2007-01-27
I've mostly run Ubuntu with Gnome - now I'm playing around with 6.06LTS server at the command prompt (no GUI).

Is there a minimum length for user passwords?  What is the default, and how do I set/change the allowed password length.  Any help would be greatly appreciated!

---

### Post by Koybe on 2007-01-28
Hello,

Everything regarding to authentication in linux is deeply configured in PAM (Pluggable Authentication Module). Every configurations files are in /etc/pam.d/ directory.

You have 4 main files for configuraing basic authentication for all the commands :
- /etc/pam.d/common-account 
- /etc/pam.d/common-auth
- /etc/pam.d/common-password
- /etc/pam.d/common-session

I think the names are self-explanatory. Pay attention if you are modifying PAM because any error could prevent you from logging to your system. I suggest keeping a root session open... just in case.

In /etc/pam.d/common-password, you should find something like this :
```
password     required     pam_unix.so nullok obscure min=4 max=8 md5
```Which means you have a 4<=length<=8 and a md5 crypted password.

I don't know if there is another simplier way.

Good luck. ;)

---

### Post by JimTDI on 2007-01-28
> **Koybe said:**
> Hello,

Everything regarding to authentication in linux is deeply configured in PAM (Pluggable Authentication Module). Every configurations files are in /etc/pam.d/ directory.

I don't know if there is another simplier way.

Good luck. ;)

Thank you for the information!  Does a default install of Ubuntu Server use PAM??

---

### Post by Koybe on 2007-01-28
Of course yes.

---

### Post by JimTDI on 2007-01-28
> **Koybe said:**
> Of course yes.

Thanks Koybe!

---

