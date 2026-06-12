---
title: "OCI8 Support - Instant Client on 64bit Ubuntu Server"
date: 2012-09-03
forum: Server Platforms
---

### Post by b00mtastik on 2012-09-03
Hello to all Ubunters out there!

So, I've done ALL OF IT. No seriously, damn near close and this still isn't working. 

I've downloaded the Instant Client Basic, SDK, and ODBC and ran the RPMS via Alien and they installed. 

Installed OCI8 via PECL and it installed, $ORACLE_HOME directory was set up nicely and found were the OCI8.SO file was sitting and pointed the 'extension_dir' in 'php.ini' to it, and also pointing the LD_LIBARY_PATH to the correct Oracle location in "/usr/lib/oracle/11.2/client64/lib" (<-- by memory, but I know I had the problem where it was 'client64' not client since I've downloaded the 64 bit version.

Now...

PHPINFO is still not showing that OCI8 support has been enabled. Ubuntu Server 12.04 is still not showing it and I'm wondering if anyone else has had this problem and have figured out a way around it? I've been Googling and tutorialling for almost 4 days straight now and I figured it was about time to forum it up as well!

Now for a bit of background, I'm working on a php web application  via SilverStripe to connect to an Oracle DataBase to download the information needed to work with so then it can be mapped properly to the SilverStripe database and then used as seen fit. I managed to get this working perfectly on a Windows 7 64bit environment to test if it was possible and it did. Perfectly, I might add again. Ubuntu Server 12.04 was not so nice to me. But I'll show it...with a bit of help from you all! :)

-B00mer

---

### Post by oldos2er on 2012-09-04
Moved to Server Platforms.

---

### Post by SeijiSensei on 2012-09-04
First, have you checked /var/log/apache2/error.log?  Is there any indication that Apache/PHP is having trouble loading the module?  Does it even try?

PHP modules are loaded with the "extension" directive in php.ini.  On Ubuntu, "extra" PHP modules are activated by files in /etc/php5/apache2/conf.d/.  Try creating a file in that directory called oci8.ini with this content:

```

; configuration for php OCI8 module
extension=oci8.so

```

On my 12.04 installation, the referenced modules themselves are in /usr/lib/php5/20090626/.  See if you have a directory like that and put a copy of the oci8.so module there.

If that doesn't work, you might need to compile your own version of PHP from source using the [--with-oci8]("https://blogs.oracle.com/opal/entry/the_php_configure_withoci8_opt") setting in the configuration.

---

### Post by b00mtastik on 2012-09-12
> **SeijiSensei said:**
> First, have you checked /var/log/apache2/error.log?  Is there any indication that Apache/PHP is having trouble loading the module?  Does it even try?

PHP modules are loaded with the "extension" directive in php.ini.  On Ubuntu, "extra" PHP modules are activated by files in /etc/php5/apache2/conf.d/.  Try creating a file in that directory called oci8.ini with this content:

```

; configuration for php OCI8 module
extension=oci8.so

```

On my 12.04 installation, the referenced modules themselves are in /usr/lib/php5/20090626/.  See if you have a directory like that and put a copy of the oci8.so module there.

If that doesn't work, you might need to compile your own version of PHP from source using the [--with-oci8]("https://blogs.oracle.com/opal/entry/the_php_configure_withoci8_opt") setting in the configuration.

So, I think I am in love with you. Ok not really, but EXTREMELY thankful for sure. Storing the OCI8.ini file in /etc/php5/apache2/conf.d definitely worked. My location for the modules references were the in the same location you had, /usr/lib/php5/20090626 and so I thought that is all that would have been needed. But now OCI8 support definitely shows up in the phpinfo page. 

Again, thank you very much for your help.

-B00mer

---

