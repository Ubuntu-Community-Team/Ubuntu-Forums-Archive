---
title: "SquirrelMail login error - &quot;Preference database error (not found) Exiting abnormally&quot;"
date: 2008-11-11
forum: Server Platforms
---

### Post by rushhh on 2008-11-11
HI everyone.  I follow the guide from [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)
everything works, but I can't sign into SquirrelMail.

I get the login screen and after I enter the Name and Password, Press "login", next screen I get an error "Preference database error (not found). Exiting abnormally"

has any body seen this error message before?  

I'm using UBUNTU SERVER 8.04.  I'm able to send mail out and received using Postfixadmin.


-mail.log

Nov 11 01:36:51 mydomain imapd-ssl: Connection, ip=[::ffff:127.0.0.1]
Nov 11 01:36:51 mydomain authdaemond: received auth request, service=imap, authtype=login
Nov 11 01:36:51 mydomain authdaemond: authmysql: trying this module
Nov 11 01:36:51 mydomain authdaemond: SQL query: SELECT id, crypt, "", 5000, 5000, home, CONCAT(home,'/',maildir), "", name, "" FROM users WHERE id = "info@mydomain.com" AND (enabled=1)
Nov 11 01:36:51 mydomain authdaemond: password matches successfully
Nov 11 01:36:51 mydomain authdaemond: authmysql: sysusername=<null>, sysuserid=5000, sysgroupid=5000, homedir=/var/spool/mail/virtual, address=info@mydomain.com, fullname=info@mydomain.com, maildir=/var/spool/mail/virtual/blah/, quota=<null>, options=<null>
Nov 11 01:36:51 mydomain authdaemond: authmysql: clearpasswd=<null>, passwd=xPk1ieoqpwl7E
Nov 11 01:36:51 mydomain authdaemond: Authenticated: sysusername=<null>, sysuserid=5000, sysgroupid=5000, homedir=/var/spool/mail/virtual, address=info@mydomain.com, fullname=info@mydomain.com, maildir=/var/spool/mail/virtual/blah/, quota=<null>, options=<null>
Nov 11 01:36:51 mydomain authdaemond: Authenticated: clearpasswd=password, passwd=xPk1ieoqpwl7E
Nov 11 01:36:51 mydomain imapd-ssl: LOGIN, user=info@mydomain.com, ip=[::ffff:127.0.0.1], port=[33661], protocol=IMAP
Nov 11 01:36:51 mydomain imapd-ssl: LOGOUT, user=info@mydomain.com, ip=[::ffff:127.0.0.1], headers=0, body=0, rcvd=46, sent=347, time=0, starttls=1

is there any other logs I should be looking at?

thanks...

---

