---
title: "php-cli missing imap"
date: 2008-11-10
forum: Server Platforms
---

### Post by jamstooks on 2008-11-10
I'm running into a very weird problem. I can't seem to get to use the imap module when running php from the command line. When I list the modules [PHP]php -m[/PHP] it doesn't show up.

However, when I run [PHP]phpinfo()[/PHP] using apache, imap shows up in the list of installed modules.

Both versions line up so I know that apache isn't using php4 while the command line is php5...

PHP 5.2.3-1ubuntu6.4

Any thoughts would be very much appreciated...

-Ben

---

### Post by CrucifiedEgo on 2008-11-10
The apache module for php and the cli php use different php.ini's.  Compare /etc/php5/apache2/php.ini and /etc/php5/cli/php.ini -- you should be able to find the difference.

---

### Post by jamstooks on 2008-11-10
Thanks! That did the trick!
I just had to add the following to /etc/php5/cli/php.ini

extension=imap.so

---

