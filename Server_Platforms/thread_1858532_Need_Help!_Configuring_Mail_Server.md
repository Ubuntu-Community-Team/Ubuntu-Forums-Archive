---
title: "Need Help! Configuring Mail Server"
date: 2011-10-12
forum: Server Platforms
---

### Post by deltacomp on 2011-10-12
Helllo, I am trying to setup an email server to work with my website I running from home with Apache2. I have followed this [tutorial ]("http://http://flurdy.com/docs/postfix/")to get it setup. I substituted the majority of localhost with my external ip address with the exception of MySQL config (I changed it and found I could not log in to MySQL or PHPmyadmin...). I wonder if it would work if I added phpmyadmin to the end of my domain name? [www.mydomain.com/phpmyadmin]("http://www.mydomain.com/phpmyadmin") :o

After installing squirrelmail, I receive an error "** ERROR: Connection dropped by IMAP server."  **when trying to log in.

I am able to telnet to the external ip address and port 993, so I think everything is working as far as the IP connection?

This is the contents of mail.log:
Oct 12 10:06:00 server postfix/cleanup[4384]: fatal: /etc/postfix/mysql_alias.cf: bad string length 0 < 1: select_field = 
Oct 12 10:06:01 server postfix/master[1760]: warning: process /usr/lib/postfix/cleanup pid 4384 exit status 1
Oct 12 10:06:01 server postfix/master[1760]: warning: /usr/lib/postfix/cleanup: bad command startup -- throttling
Oct 12 10:07:01 server postfix/cleanup[4410]: fatal: /etc/postfix/mysql_alias.cf: bad string length 0 < 1: select_field = 
Oct 12 10:07:02 server postfix/master[1760]: warning: process /usr/lib/postfix/cleanup pid 4410 exit status 1
Oct 12 10:07:02 server postfix/master[1760]: warning: /usr/lib/postfix/cleanup: bad command startup -- throttling
Oct 12 10:08:02 server postfix/cleanup[4414]: fatal: /etc/postfix/mysql_alias.cf: bad string length 0 < 1: select_field = 
Oct 12 10:08:03 server postfix/master[1760]: warning: process /usr/lib/postfix/cleanup pid 4414 exit status 1
Oct 12 10:08:03 server postfix/master[1760]: warning: /usr/lib/postfix/cleanup: bad command startup -- throttling
Oct 12 10:09:03 server postfix/cleanup[4514]: fatal: /etc/postfix/mysql_alias.cf: bad string length 0 < 1: select_field = 
Oct 12 10:09:04 server postfix/master[1760]: warning: process /usr/lib/postfix/cleanup pid 4514 exit status 1
Oct 12 10:09:04 server postfix/master[1760]: warning: /usr/lib/postfix/cleanup: bad command startup -- throttling
Oct 12 10:10:04 server postfix/cleanup[4516]: fatal: /etc/postfix/mysql_alias.cf: bad string length 0 < 1: select_field = 
Oct 12 10:10:05 server postfix/master[1760]: warning: process /usr/lib/postfix/cleanup pid 4516 exit status 1
Oct 12 10:10:05 server postfix/master[1760]: warning: /usr/lib/postfix/cleanup: bad command startup -- throttling
Oct 12 10:11:05 server postfix/cleanup[4524]: fatal: /etc/postfix/mysql_alias.cf: bad string length 0 < 1: select_field = 
Oct 12 10:11:06 server postfix/master[1760]: warning: process /usr/lib/postfix/cleanup pid 4524 exit status 1
Oct 12 10:11:06 server postfix/master[1760]: warning: /usr/lib/postfix/cleanup: bad command startup -- throttling
 
I can't figure out what any of it means...

I have a couple of questions, since this email server will hopefully send and receive email outside of the LAN, was I correct to change the IP addresses in the tutorial above from localhost to my external ip address? Or should they all be localhost?

Also since I am hosting a webpage with apache2 with the domain address of [www.mydomain.com]("http://www.mydomain.com"), should the postfix config file reflect the domain name [www.mydomain.com?]("http://www.mydomain.com?") or the name of computer hosting the domain name, i ask because I have tried both...

I have also setup a external DNS which I believe will route all email to my external IP address, since I have set this up already, and I have changed the localhost to my external ip address, will that mean that there is a loop?

I have been working on this for over 48 hours, and I don't mean two days, I mean I have literally devoted over 48 hours of work to this, its been nearly a week. Needless to say, my brain is fried and out of fresh ideas, I think I have tried almost everything. 

Any new ideas/directions will be much appreciated!

---

### Post by deltacomp on 2011-10-12
Update:

I decided to reinstall everything on a seperate computer, for several reasons, mainly to see if I can get it to work at all. As I was going through the tutorial again I realized that  /etc/courier/authmysqlrc was not present at install, that I had accidentally created it... I copied it from the new install to the broken system. It still doesn't work... :confused:

I have changed so many configurations at this point I am beginning to think it may be better to just start from scratch. 

If its any conciliation, I can not get the other computer to run the mail server either ](*,)](*,)](*,)](*,)

---

