---
title: "how to use fakeshell"
date: 2012-06-25
forum: Security
---

### Post by erodri07 on 2012-06-25
Dears all, 

 I'm working on ubuntu natty.  I'm trying to use fakeshell setting FAKE_SHELL /bin/fakeshell in /etc/login.defs.
 
 I have not receiving argument like comments say in login.defs,  the shell script at /etc/passwd is not passed to fakeshell script in my testing. 

 how is supposed it could be used ?. Is it possible to get a complete /etc/passwd entry for user trying to log in ?

 
 Regards,
  eduardo.

---

### Post by erodri07 on 2012-06-25
I realized that environment for user trying to log in had been setting while testing fakeshell script. That's great, so seems to be working something like this at fakeshell content script :

  env $SHELL

  Regards,
   eduardo.

---

