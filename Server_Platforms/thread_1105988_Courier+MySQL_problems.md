---
title: "Courier+MySQL problems"
date: 2009-03-25
forum: Server Platforms
---

### Post by fusa on 2009-03-25
I am having problems with setting up Courier.  I have followed this guide: [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/) but as far as I can tell the database doesn't seem to be correct since I get this in syslog: 

Mar 25 09:39:07 Server authdaemond: SQL query: SELECT id, crypt, "", uid, gid, home, concat(home,'/',maildir, "", name, "" FROM users WHERE id = 'username'  AND (enabled=1)
Mar 25 09:39:07 Server authdaemond: mysql_query failed, reconnecting: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'FROM users WHERE id = 'username'  AND (enabled=1)' at line 1
Mar 25 09:39:07 Server authdaemond: authmysqllib: connected. Versions: header 50051, client 50067, server 50067
Mar 25 09:39:07 Server authdaemond: mysql_query failed second time, giving up: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'FROM users WHERE id = 'username'  AND (enabled=1)' at line 1
Mar 25 09:39:07 Server authdaemond: authmysql: TEMPFAIL - no more modules will be tried

I receive the above after trying to login to courier by:

$ netcat server.com 110
+OK Hello there.
user username
+OK Password required.
pass password
-ERR Temporary problem, please try again later

I created the users table by:

CREATE TABLE `users` ( `id` varchar(128) NOT NULL default '', `name` varchar(128) NOT NULL default '', `uid` smallint(5) unsigned NOT NULL default '5000', `gid` smallint(5) unsigned NOT NULL default '5000', `home` varchar(255) NOT NULL default '/var/spool/mail/virtual', `maildir` varchar(255) NOT NULL default 'blah/', `enabled` tinyint(3) unsigned NOT NULL default '1', `change_password` tinyint(3) unsigned NOT NULL default '1', `clear` varchar(128) NOT NULL default 'ChangeMe', `crypt` varchar(128) NOT NULL default 'sdtrusfX0Jj66', `quota` varchar(255) NOT NULL default '', `procmailrc` varchar(128) NOT NULL default '', `spamassassinrc` varchar(128) NOT NULL default '', PRIMARY KEY (`id`), UNIQUE KEY `id` (`id`) ) ;


I added to the database:

INSERT INTO users (id,name,maildir,clear) VALUES ('username@server.com','username','/home/username/Maildir/', encrypt('password') );

I have checked other guides and they all seem to set up the database for users differently, but most seem to be 3-4 years older.  I am not sure which is correct.

---

### Post by BkkBonanza on 2009-03-25
That query,

SELECT id, crypt, "", uid, gid, home, concat(home,'/',maildir, "", name, "" FROM users WHERE id = 'username' AND (enabled=1)

Has "" several places in it. That generally means that a program variable was null when the query was generated. That would indicate that some config constant is likely not set correctly. Also a closing bracket is missing. So either there is some program errors or the missing variable is causing the screw ups.

So... double check any config values you need to set during install.

---

### Post by fusa on 2009-03-25
Thank you!
I found a missing ) in authmysqlrc.  Also the guides section where it shows how to add users was adding an encrypted password to the clear password field, leaving the encrypt field as default.

One more question about the directory structure. I assume I am suppose to create a dir in /var/spool/mail/virtual/ called Maildir/ I then needed to create a another directory in Maildir/ called cur/  

Should I use /var/spool/mail/virtual/Maildir and not /home/username/Maildir?
Is there any other directories I should have? Also what permissions and ownership should they have?

Also should the UID and GID match the users for Ubuntu (UID and GID are set to 5000, should I change it to 1000 to match my UID and GID in Ubuntu)?

---

### Post by fusa on 2009-03-25
I think I have it correctly configured now, I set home in MySQL to /home/username and maildir to Maildir/ and changed the UID and GID to 1000 to match the values in /etc/passwd

---

