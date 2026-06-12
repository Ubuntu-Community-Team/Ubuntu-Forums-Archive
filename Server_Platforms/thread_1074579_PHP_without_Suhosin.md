---
title: "PHP without Suhosin"
date: 2009-02-19
forum: Server Platforms
---

### Post by alfonso.caponi on 2009-02-19
Hi forum,

I'm using Ubuntu 8.10 (i386) with Apache and PHP installed via apt.
Now, without re-compiling sources etc.. how can I disable Suhosin patch? Or, exists a PHP packages without Suhosin patch? Or, can I disable any Suhosin settings in php.ini or similar?

Thank you very much, I don't found useful informations with google...

AL

---

### Post by alfonso.caponi on 2009-02-19
> **alfonso.caponi said:**
> Hi forum,

I'm using Ubuntu 8.10 (i386) with Apache and PHP installed via apt.
Now, without re-compiling sources etc.. how can I disable Suhosin patch? Or, exists a PHP packages without Suhosin patch? Or, can I disable any Suhosin settings in php.ini or similar?

Thank you very much, I don't found useful informations with google...

AL

Ops.. missing php5-suhosin...

---

### Post by possnfiffer on 2011-04-10
What's the big secret with Suhosin? nobody is willing to spill the beans and its just something i need to install Skadate (requires it to be disabled as well as
Apache Server 1.3 or higher
ModRewrite installed
PHP 5.2.4 (server module and system binary, as Apache module) or higher

    suexec must be disabled
    suPHP, suApache, Suhosin must be disabled
    cURL support
    register_globals off
    safe_mode off

MySQL 5.0.3 or higher
GD Library 2 with FreeType support
Mail server (SendMail, Exim or other)
Cron

---

### Post by possnfiffer on 2011-04-10
> **alfonso.caponi said:**
> Hi forum,

I'm using Ubuntu 8.10 (i386) with Apache and PHP installed via apt.
Now, without re-compiling sources etc.. how can I disable Suhosin patch? Or, exists a PHP packages without Suhosin patch? Or, can I disable any Suhosin settings in php.ini or similar?

Thank you very much, I don't found useful informations with google...

AL

Found it, The solution
Suhosin for a domain can be disabled by 2 methods.
1) Using php.ini
2) Using .htaccess.
Following are the steps in order to
A. Disable suhosin using php.ini.
1) Login to the server as root
2) Copy the servers customized php.ini file to the document root odf the domain.
[root@server]# php -i | grep php.ini
Configuration File (php.ini) Path => /usr/local/lib
Loaded Configuration File => /usr/local/lib/php.ini
[root@server]# cp /usr/local/lib/php.ini /home/username/public_html
3) Open the php.ini file and add the following code to the file:
[suhosin]
; Misc Options
suhosin.simulation = On
[On indicates disabled, Off indicates enabled]
4) Save and quit the file. Restart apache.  That’s it. Suhosin for a domain will now be disabled.

B. Disable SUHOSIN via .htaccess
1) Go to the document root for the domain and open the .htaccess file for the domain.
2)Now enter the following code in the file.
php_flag suhosin.simulation On
3) If the server is configured to use suphp try entering following code in .htaccess.
<Files “.ht*”>
deny from all
</Files>
suPHP_ConfigPath /home/username
4)Save and quit the file. Restart apache.  That’s it. Suhosin for a domain will now be disabled.

---

### Post by pgowling on 2011-08-18
I have tried both the php.ini and .htaccess methods on Ubuntu 10.04 LTS but with no success, phpinfo() still shows:

> This server is protected with the Suhosin Patch 0.9.9.1
Copyright (c) 2006-2007 [Hardened-PHP Project]("http://www.hardened-php.net/") Copyright (c) 2007-2009 [SektionEins GmbH]("http://www.sektioneins.de/")

Does anyone have any other suggestions on how to disable Suhosin without having to recompile PHP from source please?

---

### Post by jsilveronnelly on 2012-10-04
> **pgowling said:**
> ...Does anyone have any other suggestions on how to disable Suhosin without having to recompile PHP from source please?

Pretty sure you can't, on Ubuntu >= 10.04.

I have searched and searched, and tried everything recommended, with no success.

---

