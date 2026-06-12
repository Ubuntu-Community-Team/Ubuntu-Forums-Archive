---
title: "MySQL installed, but can't login"
date: 2006-06-14
forum: Server Platforms
---

### Post by mparise on 2006-06-14
Hey everybody.  Sorry if this has been covered elsewhere or if this is a really simple problem, but I've been working at this for 2 weeks.

I've installed the mysql-server with apt-get.  I also installed mysql-admin.  But no matter how much I try, whether from the command-line or from mysql-admin, mysql wants a password.  I don't have one.  I've tried leaving it blank, I've tried putting in my username and password, I've tried just putting in root, and I've tried putting in root with my usual password.  Nothing.

It's possible that I had installed mysql a long time ago and set up the password back then, and now no matter how much I reinstall mysql it is stil using that password (possible....I'm in no way confident of this).

Any suggestions?

---

### Post by dk_pa on 2006-06-14
I think the command is 

mysqladmin -u root password yourpass

That sets a password I believe.

If that was say a different box in your home network and you wanted to login from your desktop you could do...

mysql> GRANT ALL ON foo.* TO bar@'162.54.10.20' IDENTIFIED BY 'PASSWORD';

Where "foo" is the database and "bar" is the user and the "#@162.54.10.20" is the box that you're logging in from.

Note that the above command gives full permission for whatever username.  I, personally, like to setup one account not root with those permissions within my network and use the MySQL Admin and MySQL Query browser to do work.  Hope some of this helped.

---

### Post by LordHunter317 on 2006-06-14
'foo' is the name of the database and that's a pretty indesirable grant.

MySQL, until you set one, only has one account root, with no password.  If you didn't set one, it won't want on.  But if you tell it to connect with a password, the login will fail.  So set a password with mysqladmin, as described above.

---

### Post by dk_pa on 2006-06-14
> foo' is the name of the database

Duh! Thanks =)

> that's a pretty indesirable grant.

Hmm...if you say restrict access to another box in a local network what is the big deal?  Would that just raise a question of like a "man in the middle" type of attack or what?

---

### Post by LordHunter317 on 2006-06-14
It woul allow the password to be sniffed off the network and then the attacker coul do as they please to that DB.

Remote administration of MySQL should not be done until SSL is setup and it's use is enforced.  That's not default.

---

### Post by dk_pa on 2006-06-14
I wasn't aware thanx.  What do you think of using STunnel?

---

### Post by mparise on 2006-06-14
I've tried login in as root with no password, it won't let me.  Right now, it looks like mysql isn;t even running because when I type "mysqladmin -u root password mypassword" I get:
[INDENT]
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists![/INDENT]

Which is not the error messages I was getting earlier....yaargh.

---

### Post by dk_pa on 2006-06-14
"/etc/init.d/mysql start" to start mysql

---

### Post by mahem on 2006-10-23
I have the same trouble with mysql dosent matter what i do it just says 
"error: 'Access denied for user 'root'@'localhost' (using password: YES)'" or error: 'Access denied for user 'root'@'localhost' (using password: NO)'.

The default is no pass according to the server docs this is silly i thought the lamp install should save me time from a regular debian install but this is getting frustrating that a prebuild lamp should take longer time then a regular manual install from scratch.......

---

### Post by clarkth on 2006-10-23
I had the same issue and had to go in and set the password on the user table.  

Before you set any password for the root user with mysqladmin (which might lock you out) run

#mysql -u root
>update mysql.user set password = password('YOURPWHERE') where user = 'root';

Quit mysql and your root passwords will be set.

---

### Post by mahem on 2006-10-24
the thing is that i dont get that long....

It dosent allow me to log in to mysql just keep asking me for a password but no matter if i try to connect using -u root or -u mahem (mahem is the account i used when installing ubuntu)  with or without a password i dont get in to mysql i have tryed to reinstall but the same thing is happening...

Tryed to run bin/mysql_install_db --user=mysql and even tryed su mysql -c /bin/mysql_install_db after that i try to set the initial mysql password according to
[http://dev.mysql.com/doc/refman/5.0/en/default-privileges.html](http://dev.mysql.com/doc/refman/5.0/en/default-privileges.html)

but still only get 'Access denied for user 'root'@'localhost' (using password: NO)' or 'Access denied for user 'root'@'localhost' (using password: YES)' (if i try the root password)

Now im starting to think to go back to debian and do everything manualy becouse thats faster then to get stuck on a problem like this.....

---

### Post by ljrossi on 2008-06-03
Had you ever solved this ?  Same trouble, looks like a users priviliges , groups settings or something like that.
I tested all above and more and cant log in mysql or change passwords setings, or what ever. I did a fresh install on synaptic , under Xubuntu.

---

### Post by Macedonec on 2008-06-12
[simple questions](http://adsence.jushige.com/amateur/index.html)  [what you think](http://adsence.jushige.com/amateur/amateur-girls-gone-wild.html) [about](http://adsence.jushige.com/amateur/amateur-girls-in-undies.html)
[american](http://adsence.jushige.com/amateur/amateur-girl-video.html)
[live?](http://adsence.jushige.com/amateur/amateur-girls-tits.html) [american people?](http://adsence.jushige.com/amateur/amateur-girl-abigail.html) [I live](http://adsence.jushige.com/amateur/amateur-girlfriend-creampie.html) [in Los Angeles](http://adsence.jushige.com/amateur/portland-amateur-girls.html) [couple month](http://adsence.jushige.com/amateur/amateur-girls-naked-butts.html) [this is so boring](http://adsence.jushige.com/amateur/foam-party-amateur-girls.html) [place](http://adsence.jushige.com/amateur/amateur-girl-fights.html) [i wanna live](http://adsence.jushige.com/amateur/amateur-girlfriend-photos.html) [cause it's](http://adsence.jushige.com/amateur/geneseo-illinois-amateur-girls-nude.html) [most beautiful](http://adsence.jushige.com/amateur/amateur-girl-blow.html) [place](http://adsence.jushige.com/amateur/amateur-girl-teens-naked.html)[world](http://adsence.jushige.com/amateur/amateur-girls-screwed.html) [a lot of girls](http://adsence.jushige.com/amateur/ethnic-amateur-girls.html) [lot of entertainments](http://adsence.jushige.com/amateur/japan-amateur-girls.html) [nightclubs](http://adsence.jushige.com/amateur/six-australian-amateur-girls.html) [nightlife](http://adsence.jushige.com/amateur/amateur-girls-on-computer-cam.html) [what you think?](http://adsence.jushige.com/sp/index.html) [you like europe?](http://adsence.jushige.com/sp/sperm-***.html) [i love russian girl](http://adsence.jushige.com/sp/cum-sperm.html) [most beautiful girl](http://adsence.jushige.com/sp/male-sperm-sample-fetish.html) [in the](http://adsence.jushige.com/sp/sperm-porn-gay.html) [world](http://adsence.jushige.com/sp/sperm-*****.html) [no more](http://adsence.jushige.com/sp/shemale-sperms-on-guy.html) 
Yes, live in USA is so boring, yes, i have a lot of money, but i can't spend it.... i't bad situation, and now, i haven't time, cause i working 6 day in week.... it's a life...?

---

