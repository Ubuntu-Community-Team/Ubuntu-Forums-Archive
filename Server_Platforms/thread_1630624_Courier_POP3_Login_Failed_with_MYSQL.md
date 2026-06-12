---
title: "Courier POP3 Login Failed with MYSQL"
date: 2010-11-25
forum: Server Platforms
---

### Post by asmahan on 2010-11-25
Hello,

I am a newbie and doing a schoolproject of setting up a mailserver with Ubuntu.

I have so far: installed and configured postfix, installed courier, installed MySQL and SASL. mostly following a guide on Howtoforge.com ([http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-10.10](http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-10.10))

When I want to login via POP3 with a user from the MySQL database, authentication fails.

The mail.log file contains the followiung error:
Nov 25 18:47:55 asmahan pop3d: Disconnected, ip=[::ffff:10.11.39.33]
Nov 25 18:48:05 asmahan pop3d: Connection, ip=[::ffff:10.11.39.33]
Nov 25 18:48:16 asmahan pop3d: LOGIN FAILED, user=john, ip=[::ffff:10.11.39.33]

The problem only occurs when I try to login via POP3. I can send emails via SMTP using the same account without any problems.

Thanks for any help,
Asmahan

---

### Post by JMLM70 on 2010-11-29
I had a problem with my pop3 accounts and solved it by putting the port on front of the pop server, like: "pop.server.domain:123". Just google for your e-mail accounts ports and give it a try...

---

