---
title: "Apache::Registry errors"
date: 2005-08-22
forum: Server Platforms
---

### Post by watje on 2005-08-22
Hi,

Everytime I open 127.0.0.1/perl/ I get this error in error.log:
```
[Mon Aug 22 12:48:34 2005] [error] [client 127.0.0.1] Can't locate object method "boot" via package "mod_perl" at /usr/lib/perl5/Apache/Constants.pm line 8.\nCompilation failed in require at /usr/lib/perl5/Apache.pm line 6.\nBEGIN failed--compilation aborted at /usr/lib/perl5/Apache.pm line 6.\nCompilation failed in require at /usr/lib/perl5/Apache/Registry.pm line 2.\nBEGIN failed--compilation aborted at /usr/lib/perl5/Apache/Registry.pm line 2.\nCompilation failed in require at (eval 3) line 3.\n
``` 
My apache2.conf:
```
<IfModule mod_perl.c>
  <IfModule mod_alias.c>
   Alias /perl/ /var/www/perl/
  </IfModule>
  <Location /perl>
    SetHandler perl-script
    PerlHandler Apache::Registry
    Options +ExecCGI
  </Location>
</IfModule>
``` 
And in my browser I get a 500 Internal Server Error
Thnx in advance

-Richard

---

### Post by relix42 on 2005-08-22
What is the value of @INC during a perl script run?

---

### Post by watje on 2005-08-22
[QUOTE=relix42]What is the value of @INC during a perl script run?[/QUOTE]
watje@dionyxus:~$ perl -e 'print join("\n",@INC) '
/etc/perl
/usr/local/lib/perl/5.8.4
/usr/local/share/perl/5.8.4
/usr/lib/perl5
/usr/share/perl5
/usr/lib/perl/5.8
/usr/share/perl/5.8
/usr/local/lib/site_per

---

