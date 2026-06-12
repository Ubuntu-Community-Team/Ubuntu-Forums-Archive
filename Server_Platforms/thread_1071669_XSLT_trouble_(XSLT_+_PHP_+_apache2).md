---
title: "XSLT trouble (XSLT + PHP + apache2)"
date: 2009-02-16
forum: Server Platforms
---

### Post by bunker6 on 2009-02-16
Hi everyone.

I have installed apache2 with all the necessary modules for php and XSLT parsing.
phpinfo(); tells me everything is OK. Have a look:
```

xsl
XSL enabled
libxslt Version 1.1.24
libxslt compiled against libxml Version 2.6.32
EXSLT enabled
libexslt Version 1.1.24 
```

However when I try to xslt_create(); in the next line I get an undefined function fatal error. Makes me feel a bit crazy.

I did restart apache sure.

Is there something I can do to fix that?

---

### Post by balagosa on 2009-07-02
mind telling me how you got the **libxslt1.1.24**

I am trying to compile a certain program that requires that library (yes, that exact version)

---

### Post by ullazusman on 2009-08-30
> **balagosa said:**
> mind telling me how you got the **libxslt1.1.24**

I am trying to compile a certain program that requires that library (yes, that exact version)


Hiya, check this link on how to install xslt!

[http://www.techsww.com/tutorials/libraries/libxslt/installation/installing_libxslt_on_ubuntu_linux.php](http://www.techsww.com/tutorials/libraries/libxslt/installation/installing_libxslt_on_ubuntu_linux.php)

cheers mate!

---

