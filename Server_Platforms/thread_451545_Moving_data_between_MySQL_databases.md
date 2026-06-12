---
title: "Moving data between MySQL databases"
date: 2007-05-22
forum: Server Platforms
---

### Post by TheGameAh on 2007-05-22
Hey guys.  Perhaps an easy question, not sure yet.

Setup a test MySQL database for a PHP site.  Have a simple table, usernames and passwords.  The passwords are encrypted.  How can I move those passwords betweens servers?  When I moved them to the other server, they all change.

---

### Post by Brazen on 2007-05-22
How are you moving them?  If you are doing a dump  and restore of the database, I would assume it would work fine, since it (should be) is just a hashed value that should transfer just like text.

---

### Post by TheGameAh on 2007-05-23
Yeah I was just using PHPMyAdmin to do a dump/restore of the database (using a .sql file).  But when I look at the password value on the new server, it's a longer character string and completely different.

---

### Post by Brazen on 2007-05-23
You could try shutting down the mysql daemon and copying the database files under /var/lib/mysql over to the other machine.

---

### Post by TheGameAh on 2007-05-23
Just checked, and even the password fields for the users under the MySQL table itself is different (even though I made them the same when creating the servers).  This makes me think that MySQL itself is doing it, when the web app I use create the users, it must use a different password-creating scheme.

---

### Post by Wim Sturkenboom on 2007-05-24
You might be running two different versions of MySQL. I know that there was a change, but not sure in which version that happend. As far as I know, it happened somewhere in the 4 series (4.0.23a is still old).

The trick is in the password function that generates an 8-byte hash on older MySQL versions and an 24-byte
hash in the newer versions (more secure). Therefor copying of passwords will not work; they need to be regenerated and that can only be done 'manually'.

Can you give us the content of the relevant lines in the sql-file ?

---

### Post by TheGameAh on 2007-05-24
Indeed the MySQL versions are different, but I don't think that different.  I used Edgy desktop for one version, Feisty server for the other, but used the same install methods on both.

The Edgy version is 5.0.24a and the Feisty is 5.0.38.

One password on the Edgy box is 5e8d3a041cb2e5cd.

The same password on the Feisty is *BB9498715E9D585BC6D3C4A4A33E0F22047D1918.


I'm hoping I don't have to tell 80 users they have to recreate their passwords.  I would imagine you could do this password transfer somehow.  What do you guys think?

---

### Post by Wim Sturkenboom on 2007-05-24
I'm quite sure that what I described earlier is the problem. There might be a setting in the config to force it to use the old password format; I'm however not sure about this.

Ah, found it in the manual (I hope)

> 
**Tell the server to use the older password hashing algorithm: **

Start mysqld with the --old-passwords option. 

Assign an old-format password to each account that has had its password updated to the longer 4.1 format. You can identify these accounts with the following query: 

mysql> SELECT Host, User, Password FROM mysql.user
    -> WHERE LENGTH(Password) > 16;

For each account record displayed by the query, use the Host and User values and assign a password using the OLD_PASSWORD() function and either SET PASSWORD or UPDATE, as described earlier. 

So on your edgy system, that is probably how it is started and on your Feisty it's different. My info comes from the reference manual for versions 3.23, 4.0 and 4.1 (the option mght no longer exist; check the manuals that apply to your version).

---

### Post by TheGameAh on 2007-05-25
Yeah looks like you were right.  I modded the PHP app I was using to insert "old_password" in stead of just password, and it made it exactly how it is on the test server.

Now the fun part I guess. Converting passwords.  Is there a way to unhash or decrypt the passwords on the old server, then run it through the new MySQL to generate longer passwords?

---

### Post by melancholeric on 2007-05-25
What function did you use for encrypting the passwords? If it was md5 or SHA1 there's no way to decrypt them.

[http://dev.mysql.com/doc/refman/5.0/en/encryption-functions.html](http://dev.mysql.com/doc/refman/5.0/en/encryption-functions.html)

[http://dev.mysql.com/doc/refman/5.0/en/password-hashing.html](http://dev.mysql.com/doc/refman/5.0/en/password-hashing.html)

It looks like it's SHA1. No way to decrypt.

---

