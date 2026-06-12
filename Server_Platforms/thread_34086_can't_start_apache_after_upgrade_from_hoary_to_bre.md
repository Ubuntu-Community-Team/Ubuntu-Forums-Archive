---
title: "can't start apache after upgrade from hoary to breezy"
date: 2005-05-13
forum: Server Platforms
---

### Post by freeflying on 2005-05-13
```
[Fri May 13 21:02:10 2005] [error] Can't locate Apache2.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.4 /usr/local/share/perl/5.8.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl . /etc/apache2) at (eval 2) line 3.\n
[Fri May 13 21:02:10 2005] [error] Can't load Perl module Apache2 for server localhost.localdomain:0, exiting...
[Fri May 13 21:02:15 2005] [error] Can't locate Apache2.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.4 /usr/local/share/perl/5.8.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl . /etc/apache2) at (eval 2) line 3.\n
[Fri May 13 21:02:15 2005] [error] Can't load Perl module Apache2 for server localhost.localdomain:0, exiting...
[Fri May 13 22:03:24 2005] [error] Can't locate Apache2.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.4 /usr/local/share/perl/5.8.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl . /etc/apache2) at (eval 2) line 3.\n
[Fri May 13 22:03:24 2005] [error] Can't load Perl module Apache2 for server localhost.localdomain:0, exiting...
```

but in fact I have installed the perl ,and all run  well before my upgrading .

---

### Post by defkewl on 2005-06-08
Did you install mod_perl ?

---

