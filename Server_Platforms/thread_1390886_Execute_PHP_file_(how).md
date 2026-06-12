---
title: "Execute PHP file (how?)"
date: 2010-01-26
forum: Server Platforms
---

### Post by julifos on 2010-01-26
Hi all!

Some time ago I installed LAMP in my server, but now I need to execute .php files from the command-line (in order to execute some manteinance scripts for mediawiki).

Seems that the PHP files running in the server are run thru some kind of "module" in apache2.

Can I tell apache2 to run a .php file in command-line mode using that php module?

Or should I install a fresh copy of php-5? Won't that interfere with apache or mangle the system?

Thanks in advance for any hints!

---

### Post by Ryan Dwyer on 2010-01-26
You can't run a single PHP file with Apache's PHP module unless you make a HTTP request and have Apache serve that file. I don't remember if LAMP includes a PHP binary for CLI. I'd look around in LAMP's folder and see if there's a "php" or "php-cli" binary (in the bin folder).

If you can't find it, you can sudo apt-get install php5-cli and it shouldn't interfere with LAMP.

---

### Post by computer13137 on 2010-01-26
Just in case the above explanation is confusing to you (I kind of had to do a double take on it, and I'm very familiar with this stuff), I'm going to try to condense it for you.  This will also enable me to subscribe to this thread so I can follow up if you're still having issues.  :P 

What you're asking isn't too hard. ;)

To execute a PHP script, all you have to do is use "php" to run it.  For instance:
**php test.php**
or
**php /home/username/test.php**

If this fails, you probably don't have php5-cli installed.  This is easy to remedy:
**apt-get install php5-cli**
Then try it again.


If you have any further questions please don't hesitate to reply to this thread. :)

-Kirk

---

### Post by Vegan on 2010-01-27
> **julifos said:**
> Hi all!

Some time ago I installed LAMP in my server, but now I need to execute .php files from the command-line (in order to execute some manteinance scripts for mediawiki).

Seems that the PHP files running in the server are run thru some kind of "module" in apache2.

Can I tell apache2 to run a .php file in command-line mode using that php module?

Or should I install a fresh copy of php-5? Won't that interfere with apache or mangle the system?

Thanks in advance for any hints!

```
sudo tasksel LAMP
```

will install anything needed for the standard LAMP stack.

---

### Post by julifos on 2010-01-27
Then, if php-cli doesn't interfere with the server, I will install it!

Thanks for your answers!

---

