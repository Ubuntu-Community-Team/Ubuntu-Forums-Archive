---
title: "[SOLVED] hardy apache+mysql authentication password help"
date: 2008-06-13
forum: Server Platforms
---

### Post by straightOuttaCompton on 2008-06-13
Hello Everyone out there in Ubuntu land,

I'm having problems getting apache+mysql authentication to work.
I'm trying to password protect some directories using passwords in a mysql db.
The passwords in the db were created by mediawiki 1.7.1.
I had this working for an older version of apache+mysql and fedora.

I've followed the directions posted in this bug report:
[https://bugs.launchpad.net/ubuntu/+source/libapache-mod-auth-mysql/+bug/150649](https://bugs.launchpad.net/ubuntu/+source/libapache-mod-auth-mysql/+bug/150649)

Specifically, how to manually compile mod_auth_mysql:
[https://bugs.launchpad.net/ubuntu/+source/libapache-mod-auth-mysql/+bug/150649/comments/6](https://bugs.launchpad.net/ubuntu/+source/libapache-mod-auth-mysql/+bug/150649/comments/6)

I *almost* got this working, except apache always complains that the passwords do not match.

In my apache error.log, I get:
[Fri Jun 13 09:23:30 2008] [error] user MRUSER: password mismatch:/downloads


I'm using mysql and apache available from the ubuntu repository.
Here are the versions of the software I'm using now:
apache 2.2.8-1ubuntu0.2
mysql 14.12 Distrib 5.0.51a
ubuntu 8.04

Here's what I have for my configuration

 <Directory /var/www/downloads>

            AuthName "test"
            AuthType Basic
            AuthUserFile /dev/null
            AuthBasicAuthoritative Off

            AuthMySQLEnable On
            AuthMySQLAuthoritative On
            AuthMySQLDB dbname
            AuthMySQLUser user
            AuthMySQLPassword pass
            AuthMySQLUserTable user
            AuthMySQLNameField user_name
            AuthMySQLPasswordField user_password

            AuthMySQLPwEncryption md5

            require valid-user

 </Directory>



I think it has something to do with the way the password in the database is being decrypted.  The funny thing is, when I change the

AuthMySQLPwEncryption md5

to

AuthMySQLPwEncryption none

and copy+paste in the encrypted password exactly how it is in the database, I am able to authenticate ok and get to the directory I want.

Out of desperation, I went ahead and tried all of the configuration options:

AuthMySQLPwEncryption crypt | scrambled | md5 | aes | sha1

and none of them worked.

And, yes, I'm sure I'm entering the correct password in the username/password popup. :)

Help! Any ideas??

---

### Post by straightOuttaCompton on 2008-06-13
I was able to get the old passwords to work.

It turns out apache was not using a salt, but a simple md5 hash.

It could authenticate with an old set of passwords that werent made with a salt.

---

