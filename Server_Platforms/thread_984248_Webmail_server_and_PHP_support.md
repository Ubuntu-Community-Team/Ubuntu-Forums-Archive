---
title: "Webmail server and PHP support"
date: 2008-11-16
forum: Server Platforms
---

### Post by bandito40 on 2008-11-16
Hi,

I am looking for a way to receive emails to a PHP script.  Anyone know how this can be done?

Thanks,


Bandito

---

### Post by CrucifiedEgo on 2008-11-16
The short answer is no, the long answer is still no.  What you'll want to do is recieve mail normally and then check that mailbox with a php script.  Make sure you have php-imap installed.

---

### Post by bandito40 on 2008-11-16
That's the conclusion I was coming too.  So what is the best webmail server to install on Ubuntu.  I am installing Courier right.  Any suggestions.

Thanks,


Bandito

---

### Post by Philio on 2008-11-17
You can receive emails to a PHP script using a pipe!

For example on our email servers we use OSTicket and have the following pipe setup:

[email]support@domain.com[/email] -> |/usr/bin/php -q /home/domain.com/support/www/api/pipe.php

This is using exim MTA.

---

### Post by Philio on 2008-11-17
> **bandito40 said:**
> That's the conclusion I was coming too.  So what is the best webmail server to install on Ubuntu.  I am installing Courier right.  Any suggestions.

Thanks,


Bandito

Roundcube is a nice free one: [http://roundcube.net/](http://roundcube.net/)

---

