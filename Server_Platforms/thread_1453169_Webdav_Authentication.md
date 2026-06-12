---
title: "Webdav Authentication"
date: 2010-04-12
forum: Server Platforms
---

### Post by whitbacon on 2010-04-12
I am trying to use webdav with apache2.  I would like authentication to be for users on the machine.  In other words i don't want to use an htpsswrd file or other such business.  I would like to add a user to the machine and automatically have webdav credentials given.

thanks in advance.

---

### Post by dmovad on 2010-12-14
If you found a tutorial to doing this I'd sure appreciate a pointer to the solution...

Thanks in advance!

---

### Post by SeijiSensei on 2010-12-14
[http://code.google.com/p/mod-auth-external/](http://code.google.com/p/mod-auth-external/)

along with

[http://code.google.com/p/pwauth/](http://code.google.com/p/pwauth/)

provide mechanisms for Apache to query the Unix system password database.

---

### Post by dmovad on 2010-12-15
Thank you very much!

---

