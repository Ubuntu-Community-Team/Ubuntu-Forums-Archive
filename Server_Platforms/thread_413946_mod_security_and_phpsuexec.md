---
title: "mod_security and phpsuexec"
date: 2007-04-19
forum: Server Platforms
---

### Post by lukemack on 2007-04-19
hi,

i am running ubuntu 6.10 with the lamp server package installed (and upgraded to 5.2.1 using the dotdeb repository.

can anyone tell me how i can ascertain whether i am running phpsuexec and mod_security?

someone suggested httpd -l but i get 'command not found'

many thanks,

<L>

---

### Post by Czar on 2007-05-13
> **lukemack said:**
> can anyone tell me how i can ascertain whether i am running phpsuexec and mod_security?

Good question.   What is the best way to force php to run as the user who holds the content?  phpsuexec i assume?  What's the easiest way to implement this?

**EDIT**

Nvm.  

> $ sudo aptitude search suphp
p   libapache-mod-suphp                          - Apache module to run php scripts with the owner permis
p   libapache2-mod-suphp                         - Apache2 module to run php scripts with the owner permi
p   suphp-common                                 - Common files for mod suphp           

---

