---
title: "Complete ISP server"
date: 2005-11-13
forum: Server Platforms
---

### Post by steffen on 2005-11-13
I have an old ISP server running RedHat9 and Directadmin virtual hosting panel. ([www.directadmin.com)](www.directadmin.com)). However, I need to upgrade, and since I've become totally in love with Ubuntu, and I'm obviously setting my server up on Ubuntu. Furthermore, I want to scrap Directadmin, because its an overkill for my purpose.

What I need is a webserver with ability to have multiple virtual domain names, domain name aliases and email users under each account/domain. I also want a DNS server (bind),Apache, PHP, MySQL, an email server, an FTP server, webmail, phpmyadmin, spamassassin, clamav, etc.

I have tried out VHCS and ISPConfig. VHCS looked very good at first impression, but the only thing I would use it for would be to set up new virtual accounts. And the end users would only have two levels of access - one for setting up additional email accounts, and one for reading email and changing password. So it's a bit overkill for the end users, while not having all the features I would prefer for the admin. The main purpose of this server is to serve email, and serve web pages through different Drupal sites.

After having looked at available open source software, I'm proposing the following config for my ISP server:

- Web server: Apache2
- Email: postfix and nmap with Hula ([www.hula-project.org](www.hula-project.org))
- proFTPD
- MySQL 4
- PHP 4
- Clamav and spamassassin (configured through Hula)
- Bind9
- Webmin and Virtualmin

I have searched around a lot for howtos on running a virtual domain based ISP server with Hula installed, but I haven't really found anything. Hula will be my end user's cornerstone, with access to their webmail. An administrator for each account will have access to add accounts through Hula WebAdmin.

The cornerstone for the administrator (myself) will be webmin and virtualmin. Webmin will give me a web based server panel, which would do for my own purpose. It is feature rich and modular. In addition, I'm hoping that Virtualmin will take care of adding all domain names and accounts.

Does anyone have any experience, or know of any posting somewhere of somebody who has set up an ISP server with this config - Webmin, Virtualmin and Hula? If so, any warnings or notes are appreciated! It's the combination of Virtualmin and Hula I'm in particular interested in.

Thanks!

---

### Post by coza on 2005-12-19
[http://www.howtoforge.com/perfect_setup_ubuntu_5.10](http://www.howtoforge.com/perfect_setup_ubuntu_5.10)

This link is a complete how-to doing just what you need. 

It uses ispconfig, which is just like cpanel.

It looks great.

---

### Post by WebDev90 on 2005-12-27
You can check also VHCS.

[http://vhcs.net]("http://vhcs.net")

---

### Post by LordHunter317 on 2005-12-27
[QUOTE=steffen]What I need is a webserver with ability to have multiple virtual domain names, domain name aliases and email users under each account/domain. I also want a DNS server (bind),Apache, PHP, MySQL, an email server, an FTP server, webmail, phpmyadmin, spamassassin, clamav, etc.[/quote]If this is a serious service, then all of this shouldn't be hosted on a single box.  Mail should be seperate.  DNS should be seperate, and as redundant as possible (likely hosted by someone else unless you have the capacity).

If you have any database load whatsoever, it should be a seperate box.

> - MySQL 4There is no reason to not use 5, unless you have stuff that's totally locked to that platform.

> - Clamav and spamassassin (configured through Hula)I'd highly recommend Mailscanner or Amavis instead.  It'll be faster.  Also, use SQL Bayes and AWL.

---

