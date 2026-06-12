---
title: "Installing ISPConfig"
date: 2010-01-27
forum: Server Platforms
---

### Post by terrapin893 on 2010-01-27
So Ive gone through all the steps to configure my server to accept and work well with ISPConfig.  I figured that would be the hard part.  But alas, no.  I cant seem to find the right repository to add to my sources.list file.  

Ive found the svn repository but I am hesitant to use that.  How do I go about installing ISPConfig now that I have fully configured my server to accept it?

---

### Post by dalitso on 2010-01-27
Which version of ubuntu are you using? And which ispconfig version are you trying to install?

This link might help [http://www.ispconfig.org/documentation.htm](http://www.ispconfig.org/documentation.htm)

---

### Post by terrapin893 on 2010-01-27
Karmic and ISPConfig 2

[quote=From the link]
Installation

Hint: With the system installation, some system files are replaced where adjustments were made.
This can lead to loss of entries in named.conf as well as in the Sendmail/Postfix configuration.

Important: ISPConfig is meant to be installed on new Linux installations with no web sites, so if you run a server with hundreds of web sites and need a control panel that can take care of those existing web sites, then ISPConfig is not for you!

Make sure you have the c and c++ compilers installed on your server (gcc and cpp). 

Log in to your shell as root.
Unpack the ISPConfig-archive

tar xvfz ISPConfig*.tar.gz
[/quote]

Maybe I totally missed something but I cant get past that last step.  

```

root@champion1:/home/paul# tar xvfz ISPConfig*.tar.gz
tar: ISPConfig*.tar.gz:  Cannot open: No such file or directory 

```

---

### Post by terrapin893 on 2010-01-27
You know what, I just installed webmin in like 3 minutes so Im just gonna roll with that.

---

### Post by dalitso on 2010-01-28
If u want just an interface for configuring your ubuntu server then webmin is the best choice, but if you want a web hosting control panel then you still have to consider ISPconfig.

Of course you can install virtualmin on webmin. Virtualmin is a web hosting control panel for webmin, I have used it before but still ISPconfig is the best.

---

### Post by terrapin893 on 2010-01-28
How did you install ISPConfig?

---

### Post by dalitso on 2010-01-28
The below steps were taken from [http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3-p5](http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3-p5)

Assuming you installed and configured everything as shown in the previous pages of this guide;

To install ISPConfig 3 from the latest released version, do this: 

```
cd /tmp
wget http://downloads.sourceforge.net/ispconfig/ISPConfig-3.0.1.6.tar.gz?use_mirror=
tar xvfz ISPConfig-3.0.1.6.tar.gz
cd ispconfig3_install/install/
```

(Replace ISPConfig-3.0.1.6.tar.gz with the latest version.)
The next step is to run 
```
php -q install.php
```

This will start the ISPConfig 3 installer:

root@server1:/tmp/ispconfig3_install/install# php -q install.php


--------------------------------------------------------------------------------
 _____ ___________   _____              __ _
|_   _/  ___| ___ \ /  __ \            / _(_)
  | | \ `--.| |_/ / | /  \/ ___  _ __ | |_ _  __ _
  | |  `--. \  __/  | |    / _ \| '_ \|  _| |/ _` |
 _| |_/\__/ / |     | \__/\ (_) | | | | | | | (_| |
 \___/\____/\_|      \____/\___/|_| |_|_| |_|\__, |
                                              __/ |
                                             |___/
--------------------------------------------------------------------------------


>> Initial configuration

Operating System: Debian or compatible, unknown version.

    Following will be a few questions for primary configuration so be careful.
    Default values are in [brackets] and can be accepted with <ENTER>.
    Tap in "quit" (without the quotes) to stop the installer.


Select language (en,de) [en]: <-- ENTER

Installation mode (standard,expert) [standard]: <-- ENTER

Full qualified hostname (FQDN) of the server, eg server1.domain.tld  [server1.example.com]: <-- ENTER

MySQL server hostname [localhost]: <-- ENTER

MySQL root username [root]: <-- ENTER

MySQL root password []: <-- yourrootsqlpassword

MySQL database to create [dbispconfig]: <-- ENTER

MySQL charset [utf8]: <-- ENTER

Generating a 2048 bit RSA private key
.......+++
...+++
writing new private key to 'smtpd.key'
-----
You are about to be asked to enter information that will be incorporated
into your certificate request.
What you are about to enter is what is called a Distinguished Name or a DN.
There are quite a few fields but you can leave some blank
For some fields there will be a default value,
If you enter '.', the field will be left blank.
-----
Country Name (2 letter code) [AU]: <-- ENTER
State or Province Name (full name) [Some-State]: <-- ENTER
Locality Name (eg, city) []: <-- ENTER
Organization Name (eg, company) [Internet Widgits Pty Ltd]: <-- ENTER
Organizational Unit Name (eg, section) []: <-- ENTER
Common Name (eg, YOUR name) []: <-- ENTER
Email Address []: <-- ENTER
Configuring Jailkit
Configuring SASL
Configuring PAM
Configuring Courier
Configuring Spamassassin
Configuring Amavisd
Configuring Getmail
Configuring Pureftpd
Configuring MyDNS
Configuring Apache
Configuring vlogger
Configuring Firewall
Installing ISPConfig
ISPConfig Port [8080]: <-- ENTER

Configuring DBServer
Installing Crontab
no crontab for root
no crontab for getmail
Restarting services ...
 * Stopping MySQL database server mysqld
   ...done.
 * Starting MySQL database server mysqld
   ...done.
 * Checking for corrupt, not cleanly closed and upgrade needing tables.
 * Stopping Postfix Mail Transport Agent postfix
   ...done.
 * Starting Postfix Mail Transport Agent postfix
   ...done.
 * Stopping SASL Authentication Daemon saslauthd
   ...done.
 * Starting SASL Authentication Daemon saslauthd
   ...done.
Stopping amavisd: amavisd-new.
Starting amavisd: amavisd-new.
 * Stopping ClamAV daemon clamd
   ...done.
 * Starting ClamAV daemon clamd
LibClamAV Warning: ***********************************************************
LibClamAV Warning: ***  This version of the ClamAV engine is outdated.     ***
LibClamAV Warning: *** DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq) ***
LibClamAV Warning: ***********************************************************
   ...done.
 * Stopping Courier authentication services authdaemond
   ...done.
 * Starting Courier authentication services authdaemond
   ...done.
 * Stopping Courier IMAP server...
   ...done.
 * Starting Courier IMAP server...
   ...done.
 * Stopping Courier IMAP-SSL server...
   ...done.
 * Starting Courier IMAP-SSL server...
   ...done.
 * Stopping Courier POP3 server...
   ...done.
 * Starting Courier POP3 server...
   ...done.
 * Stopping Courier POP3-SSL server...
   ...done.
 * Starting Courier POP3-SSL server...
   ...done.
 * Restarting web server apache2
 ... waiting    ...done.
Restarting ftp server: Running: /usr/sbin/pure-ftpd-mysql-virtualchroot -l mysql:/etc/pure-ftpd/db/mysql.conf -l pam -A -b -O clf:/var/log/pure-ftpd/transfer.log -8 UTF-8 -u 1000 -E -B
Installation completed.
root@server1:/tmp/ispconfig3_install/install#

The installer automatically configures all underlying services, so no manual configuration is needed.

Afterwards you can access ISPConfig 3 under [http://server1.example.com:8080/](http://server1.example.com:8080/) or [http://192.168.0.100:8080/](http://192.168.0.100:8080/). Log in with the username admin and the password admin (you should change the default password after your first login):

---

### Post by terrapin893 on 2010-01-28
ah, thats the missing command, 'wget' . . . . thats perfect.  Thanks so much!

Like seriously for so long I was trying to find a repository to add to my sources.list its not even funny.  I never thought about the 'wget' command.

---

