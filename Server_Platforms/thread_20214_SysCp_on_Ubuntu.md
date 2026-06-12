---
title: "SysCp on Ubuntu"
date: 2005-03-15
forum: Server Platforms
---

### Post by ejms07 on 2005-03-15
SysCP is a ISP Servers Control Panel for Debian (woody/sarge).  We use it for our customers Web and Mail servers.  I tried it in Warty, it installs with no errors but don't work so good.  Then, I tried in Hoary but it install Apache 1.3 and libraries of Apache 2.  Does any one knows about it?

---

### Post by alastair on 2005-03-15
Define "don't work so good".
Also - explain the 1.3 vs 2.0 apache problem.

---

### Post by ejms07 on 2005-03-16
In Warty, you can use SysCP web interface and configure your customer's domains and emails, but it does not create their respective folders in /var/customer/mail.

In Hoary when you install SysCP, it install apache 1.3 but it's dependencies are for apache 2 (e.g. libapache2-mod-XXXXXX).

---

### Post by alastair on 2005-03-16
OK - teh "/var/customer/mail" folder problem sounds like a permission issue (user/group problem). Probably not a show stopper.

As for the Hoary dependency issue - from their web site :

[http://www.syscp.de/wiki/EnInstall](http://www.syscp.de/wiki/EnInstall)

It looks like the s/w is Debian Woody (stable) or Sarge (Testing). Dependencies to Ubuntu might be problematic I guess.

You could always download and install from source.

---

### Post by az on 2005-03-16
...From the website:
Technical Background

At the moment SysCP supports the following daemons:

    * webserver: [Apache 1.3] with [PHP4]
    * mail transfer agent: [Postfix]
    * pop/imap server: [Courier]
    * ftp server: [ProFTPd]
    * database server: [MySQL]
    * nameserver: [Bind9]
    * traffic accounting and statistics: [Webalizer]

Postfix, Courier and ProFTPd will be configured to get their user information directly from the SysCP database. You don't need to add and maintain local users to get this daemons to work. Apache and Bind will be configured through two configuration files (/etc/apache/vhosts.conf and /etc/bind/syscp_bind.conf).

It does not support apache2.  So that would be problematic if you already have apache2 installed.

It is GPL, but I could not find the debian source packages.  I suppose they could be made available.  But they would be neccessary for backporting.  This package would be a good candidate for the Ubuntu Backports project.

If you want to do that, I can help you.  The first step would be to find the .dsc .diff and orig.tar.gz files for the latest version.  I looked at the site for only a few minutes.  Maybe you could investigate.


While looking, I just found:
1.6. Is it possible to use Apache 2.0.x instead of 1.3.x?

Yes. Although SysCP supports Debian stable packages by default, it has been proven that usage of Apache 2.0.x is possible without problems. However, we'd like to point out that you must use the tar.gz in that case.


Ah ha!
...Hope that helps.

---

### Post by ejms07 on 2005-03-17
I will install all the necessary packages from Ubuntu (Hoary) repositories, and then install SysCP from tar.gz, let see what happen...

If you or someone knows another aplication similar to SysCP in Ubuntu repositories please let me know.

Thanks anyway....you guys ROCK!

---

### Post by ejms07 on 2005-03-21
azz...

I installed the tar.gz version and works fine, I just installed all the new versions of it's required packages and made some editing work.

It will be nice to have SysCp on Ubuntu's repositories.

Thanks!

---

### Post by hmunoz on 2006-02-07
I am trying to install syscp on ubuntu 5.10 
I download de tar.gz on the server make all the configuration that syscp said 
when i tried to configure my pop3 account my incoming mail server works, i have a problem with my outgoing mail server said that cant connect

how can i check my postfix to see if is working?
btw I am missing postfix-tls is not on the repositories and i cant find a .deb

---

