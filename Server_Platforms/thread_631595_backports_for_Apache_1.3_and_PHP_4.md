---
title: "backports for Apache 1.3 and PHP 4"
date: 2007-12-04
forum: Server Platforms
---

### Post by Pitt Stains on 2007-12-04
Hello,

I need to set up a test server running Apache 1.3 and PHP 4.  I'd prefer not to compile anything from source and use managed packages.  Is there a backport or something from which I can apt-get these packages?  I was planning on running Ubuntu 7.10...

Thanks,
Pitt

---

### Post by Pitt Stains on 2007-12-27
Bump.

It's really the PHP4 part that's important to me.  Which version of Apache is used doesn't matter so much.

Surely this is just a matter of enabling the right repository?  Does anyone know which one?

Thanks!

---

### Post by jtc on 2007-12-27
Actually I'm pretty sure Ubuntu 7.10 won't give you PHP4, since that is a version of PHP which is to be abandoned by the end of this year. If you really want to use PHP4, which you in most cases shouldn't, and you don't want to compile it yourself it might be an idea to install Ubuntu 6.06 LTS.

Regarding PHP4, this is what [php.net]("http://www.php.net/") has to say.

>  Today it is exactly three years ago since PHP 5 has been released. In those three years it has seen many improvements over PHP 4. PHP 5 is fast, stable & production-ready and as PHP 6 is on the way, PHP 4 will be discontinued.

The PHP development team hereby announces that support for PHP 4 will continue until the end of this year only. After 2007-12-31 there will be no more releases of PHP 4.4. We will continue to make critical security fixes available on a case-by-case basis until 2008-08-08. Please use the rest of this year to make your application suitable to run on PHP 5.

For documentation on migration for PHP 4 to PHP 5, we would like to point you to our [migration guide]("http://www.php.net/manual/en/migration5.php"). There is additional information available in the [PHP 5.0 to PHP 5.1]("http://www.php.net/manual/en/migration51.php") and [PHP 5.1 to PHP 5.2]("http://www.php.net/manual/en/migration52.php") migration guides as well. 

---

### Post by Pitt Stains on 2008-01-07
Thanks.  You're right.  I actually **don't** want to run PHP4.  Unfortunately, I don't have any control over the live hosting environment, and it's running PHP4... so if I'm going to be running a representative testing/dev server, it should be running PHP4 too.

The LTS disk is a good idea.  Thanks.

In the end, I think I'll run PHP5 on my testing server anyway.  Maybe I can leverage that.  ("Well, this won't work on the live server... maybe we should upgrade to PHP5.") :-p

---

