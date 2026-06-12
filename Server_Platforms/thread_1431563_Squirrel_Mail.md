---
title: "Squirrel Mail"
date: 2010-03-16
forum: Server Platforms
---

### Post by bluedrakonis on 2010-03-16
I followed this guide completely 

[http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3)

what do i now, how do i set this to be an email domain for example: 

[email]admin@mywebite.com[/email]

thanks for any and all help

---

### Post by KB1JWQ on 2010-03-16
Oh dear.

Squirrelmail is kind of the last piece to a working mail solution.  I've had lackluster results in following tutorials-- specifically, they teach you how to do ONE THING, ONE WAY, with no understanding about why you're doing what you're doing.  As a result, you wind up in your current situation; trying to make a change and not understanding how.

If you're using virtual users with a mysql backend, look into postfixadmin as a management tool; it automates this.  Be sure to use squirrelmail's vlogin plugin as well.

---

### Post by kewlrichie on 2010-03-17
- The Perfect Server - Ubuntu 9.10 [ISPConfig 3] [http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3)

This is a full setup for a web hosting style control panel and there wouldn't be any reason to install all the stuff that goes along with this but you could just single out the mail part and complete that. This is a local mail system with real system users

- Virtual Users And Domains With Postfix, Courier, MySQL And SquirrelMail (Ubuntu 9.10) [http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu-9.10](http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu-9.10)

"The advantage of such a "virtual" setup (virtual users and domains in a  MySQL database) is that it is far more performant than a setup that is  based on "real" system users. With this virtual setup your mail server  can handle thousands of domains and users. Besides, it is easier to  administrate because you only have to deal with the MySQL database when  you add new users/domains or edit existing ones. No more postmap  commands to create db files, no more reloading of Postfix, etc. For the  administration of the MySQL database you can use web based tools like  phpMyAdmin which will also be installed in this howto. The third  advantage is that users have an email address as user name (instead of a  user name + an email address) which is easier to understand and keep in  mind."

- Postfix Virtual Hosting With LDAP Backend And With Dovecot As IMAP/POP3 Server On Ubuntu Kamic Koala 9.10 [http://www.howtoforge.com/postfix-virtual-hosting-with-ldap-backend-and-with-dovecot-as-imap-pop3-server-on-ubuntu-karmic-koala-9.10](http://www.howtoforge.com/postfix-virtual-hosting-with-ldap-backend-and-with-dovecot-as-imap-pop3-server-on-ubuntu-karmic-koala-9.10)

Now this is what i use at work. It is sort of the same concept as the above MYSQL method but using openldap as a backend for users and authentications. Using a web interface called Phamm to add users and domains (very easy to use). This new guide for ubuntu 9.10 uses Roundcube as a webmail solution. I haven't tried it but it looks very nice. When i did the install I used a the older 9.04 guide and followed that through and I also used pieces of the MYSQL guide to add in the Amavisd-New, Clam-AV, Spamassassin and squirrelmail parts.

- iRedMail 0.5.1: Full-Featured Mail Server With LDAP Postfix RoundCube/SquirrelMail iRedAdmin On Ubuntu 9.04 [http://www.howtoforge.com/iredmail-0.5.1-full-featured-mail-server-with-ldap-postfix-roundcube-squirrelmail-iredadmin-on-ubuntu-9.04](http://www.howtoforge.com/iredmail-0.5.1-full-featured-mail-server-with-ldap-postfix-roundcube-squirrelmail-iredadmin-on-ubuntu-9.04)

Now this is a new script based method of setting everything up and looks very good and seems to sets things up in a few screens. It uses IRedAdmin as the web interface for adding domains and users much like Phamm does. This also seems like a great choice and it looks like you can have a mail server up and running in a few mins. Also seems full featured has a choice of ldap or mysql for a backend, few choices of different webmail clients, web management interface and awstats for mail statistics. If i had to rebuild my current mail server i might consider using this setup it looks very easy and straight forward.



Anyways that was just some hints on where to look. I personally prefer virtual based setups like the mysql and ldap backends I think there are much easier to manage and I can add as many domains as I like and I don't like to make real system users. Also if you don't know already you would need have a hosted MX record with a hosting provider so your domain (mywebsite.com) knows where to resolve to your new mail server. Also your ISP has to not have port 25 blocked or you wont be able to receive mail. If your doing this at home there is work arounds for ISPs that block 25 port, just do a quick search on the forums or google and there are services like no-ip.com has a service called mail reflector [http://www.no-ip.com/services/managed_mail/inbound_port_25_unblock.html](http://www.no-ip.com/services/managed_mail/inbound_port_25_unblock.html)

---

### Post by bluedrakonis on 2010-04-05
thanks ill give that a try

---

### Post by bluedrakonis on 2010-04-07
i followed the one guide but am hung up on a gnarwl issue

[http://ubuntuforums.org/showthread.php?p=9088069#post9088069](http://ubuntuforums.org/showthread.php?p=9088069#post9088069)

---

