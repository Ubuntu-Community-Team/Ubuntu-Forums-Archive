---
title: "Installing SSH2 into PHP"
date: 2010-03-23
forum: Server Platforms
---

### Post by IcyTexx on 2010-03-23
Hi...

Well, I want to install [http://pecl.php.net/package/ssh2](http://pecl.php.net/package/ssh2) extension into PHP, but it seems like it's only installed by pear, and for pear I need php-pear which wants to install php-cli.

I already have php-cgi with fcgi and Apache2 worker MPM.

Please, could anyone help me?

---

### Post by schloss2 on 2010-03-23
I would recommend using [phpseclib, a pure PHP SSH2 implementation]("http://phpseclib.sourceforge.net/").  The PECL extension has several problems.  Among others, it doesn't work on PHP 5.3:



[http://core.trac.wordpress.org/ticket/10348#comment:10](http://core.trac.wordpress.org/ticket/10348#comment:10)
 [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=569119](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=569119)
[http://pecl.php.net/bugs/bug.php?id=16727](http://pecl.php.net/bugs/bug.php?id=16727)
[URL="http://pecl.php.net/bugs/bug.php?id=16727"]
[/URL]
 And even on the versions it does work on it doesn't work very well:


 [https://bugs.launchpad.net/ubuntu/+source/php-ssh2/+bug/501959](https://bugs.launchpad.net/ubuntu/+source/php-ssh2/+bug/501959)


And on those few occasions it actually does work it's slow:

[http://kevin.vanzonneveld.net/techblog/article/make_ssh_connections_with_php/#comment_3759](http://kevin.vanzonneveld.net/techblog/article/make_ssh_connections_with_php/#comment_3759)

---

### Post by IcyTexx on 2010-03-24
Thank you very much!

---

