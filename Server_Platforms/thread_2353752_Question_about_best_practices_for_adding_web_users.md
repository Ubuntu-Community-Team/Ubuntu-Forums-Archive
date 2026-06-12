---
title: "Question about best practices for adding web users."
date: 2017-02-24
forum: Server Platforms
---

### Post by rlischer on 2017-02-24
When adding users to Ubuntu that you want to allow to create their own website, should you put public_html in their /home/username/public_html folder?  Be default apache2 uses /var/www which is not very handy considering users already have a home folder elsewhere.

Thanks!

---

### Post by TheFu on 2017-02-24
a) I've never run public websites that anyone untrusted could edit.
b) I have used shared hosting and they used the public_html under the HOME method.

There are many, many, many, different ways, each depends on your specific requirements.  Flexibility is the great thing about Unix systems and the terrible thing.  So many choices. So many options.  Your needs aren't the same as most other people's needs since we all have different levels of skill and expertise.  Only you can decide which is "the best" way.

For example, if you don't allow ssh access to the server, the answers might be different.
If you don't allow FTP (and you shouldn't), the answers might be different.
If you put user logins into a SQL DB, the answers might be different.
If you put user logins into an LDAP DB, the answers might be different.
Will a DBMS be used with the websites?  Will that be on the same machine or not? Will each user have a different DB?

Redhat often has best practices for trivial setups. Complex setups usually require different answers.

[https://www.howtoforge.com/tutorial/perfect-server-ubuntu-16.04-with-apache-php-myqsl-pureftpd-bind-postfix-doveot-and-ispconfig/](https://www.howtoforge.com/tutorial/perfect-server-ubuntu-16.04-with-apache-php-myqsl-pureftpd-bind-postfix-doveot-and-ispconfig/) might be of help.  I wouldn't load all those things on a single system. I wouldn't use plain FTP ... er ... ever and I'd outsource DNS to a professional team ( been hacked through DNS before). I'd use mariaDB, not mysql.

---

### Post by SeijiSensei on 2017-02-24
If you go this route, I'd certainly limit other users to plain-vanilla HTML and CSS.  No scripts, no PHP, nothing that might be exploited.

Yes, the "standard" from many years back is to enable /home/user/public_html making those pages accessible as [http://www.yourdomain.com/~username](http://www.yourdomain.com/~username).

You may need to enable the "userdir" module for this:
```

sudo a2enmod userdir

```
then restart Apache or reboot.  On my 14.04 system, though, it was already enabled.  See /etc/apache2/mods-enabled.

---

### Post by rlischer on 2017-02-24
Thanks for the info.  I am a huge fan of ispconfig 3 and have used it for years.  I am now trying to learn everything ispconfig does from the terminal, just so I know what goes on behind the curtain.  I am done with ftp and will only use sftp but it seems keeping public_html in the home folder and using sftd at the same time breaks Apache when trying to limit the sftp user to their home folder.  

Thanks for pointing me in the right direction.

---

### Post by SeijiSensei on 2017-02-25
I don't see how using SFTP can "break" Apache.  If you connect as user@server, you'll see the whole directory tree, but your rights will be just as limited as if you logged into the server as "user" or connected directly with SSH.  By default you should have full access to /home/user and no access anywhere else other than /tmp.  

Yes, some FTP implementations have a "chroot" function which locks the FTP user to a specific directory.  That's possible with SFTP as well: [http://askubuntu.com/questions/134425/how-can-i-chroot-sftp-only-ssh-users-into-their-homes](http://askubuntu.com/questions/134425/how-can-i-chroot-sftp-only-ssh-users-into-their-homes)

---

### Post by rlischer on 2017-02-26
Thanks!

---

