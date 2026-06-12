---
title: "[postfix] need a help with postmap:warning on mail server postfix with ubuntu 10.04"
date: 2011-04-08
forum: Server Platforms
---

### Post by venol on 2011-04-08
I follow this  tutorial > [http://serion.co.nz/content/howto-setup-mailserver-using-postfix-mysql-dovecot-postfixadmin-amavis-new](http://serion.co.nz/content/howto-setup-mailserver-using-postfix-mysql-dovecot-postfixadmin-amavis-new) and I can add one virtual domain with two virtual user with  postfixadmin, so I have domain example.com with users [EMAIL="user1@example.com"]user1@example.com[/EMAIL]  and [EMAIL="user2@example.com"]user2@example.com[/EMAIL]. But, when I test to send message to another  address. Example, [EMAIL="user1@example.com"]user1@example.com[/EMAIL] to [EMAIL="user2@example.com"]user2@example.com[/EMAIL] it's doesn't  work. This is the log for the error.

> postfix/trivial-rewrite[5230]:  fatal:  mysql:/etc/postfix/mysql_virtual_mailbox_domains.cf(0,lock|fold_fix):  table lookup problemand, when I check with manual command on  terminal "postmap -q example.com  mysql:/etc/postfix/mysql_virtual_mailbox_domains.cf" and this is the  result
> postmap: warning: connect to mysql server 127.0.0.1: Access  denied for user 'postfixadmin'@'localhost' (using password: YES)
I have user on mysql and ther user(postfixadmin) can login and select database. But, what is  the problem?

this is file mysql_virtual_mailbox_domains.cf
> 
hosts = 127.0.0.1
user = postfixadmin
password = adminpostfix   #replace with the password you set above
dbname = postfixadmin
query = SELECT domain FROM domain WHERE domain='%s' and backupmx = 0 and active = 1


---

### Post by venol on 2011-04-09
need  help  .. . :(

---

### Post by venol on 2011-04-10
helep.  . .
:(

---

### Post by eskuge on 2011-04-10
Check that your password is the same in all the mysql_virtual_* files. 
Also try to change the password for the postfixadmin user. Remeber to change the password in all the files also then.

---

### Post by venol on 2011-04-10
> **eskuge said:**
> Check that your password is the same in all the mysql_virtual_* files. 
Also try to change the password for the postfixadmin user. Remeber to change the password in all the files also then.
  
thanks for the reply. you right, I must ensure all configuration mysql_virtual_* file correct. Thanks

):P

---

