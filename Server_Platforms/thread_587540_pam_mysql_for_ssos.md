---
title: "pam_mysql for ssos"
date: 2007-10-22
forum: Server Platforms
---

### Post by lee_connell on 2007-10-22
Hi all,

I have pam-mysql, libnss-mysql configured and working properly, mysql users can login etc...

My problem is when I issue the "passwd" command against a mysql user, it tells me permission denied, but the real problem is.

----------------------- [/var/log/auth.log]
pam_mysql - MySQL error (You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'FROM user WHERE user.user_name = 'testuser'' at line 1) 
--------------------------------------------

-----------------------[/var/log/mysql/mysql.log
071021 22:09:24 17 Connect nss@localhost on nss-mysql 
17 Init DB nss-mysql 
17 Quit  
18 Connect nss@localhost on nss-mysql 
18 Init DB nss-mysql 
18 Query SELECT 0, FROM user WHERE user.user_name = 'testuser' 
----------------------------------------------------

Now I had this problem earlier in configuration when I was trying to get authentication working, but the problem was i needed to explicitly define the "passwdcolumn" and "statcolumn" in my pam files.

-----------------------[/etc/pam.d/common-auth] etc...
password sufficient pam_unix.so nullok obscure min=4 max=8 md5 
password required pam_mysql.so nullok user=myuser passwd=mypass host=localhost db=nss-mysql table=user usercolumn=user.user_name passwordcolumn=user.password statcolumn=user.status crypt=md5 
-------------------------------------------------------------

Obviously the sql is not right above, what is causing this and how do I fix it?  it only happens when I issue the "passwd" command against the mysql user.

Thanks!

I'm running [Gutsy 7.10]

---

### Post by Peter Riche on 2007-10-23
Hi,

Sorry but I think I won't really help (hoping I will!)
I've got that same MySQL error in auth.log but it's issued by smbd when I do an smbclient command.
The Ubuntu version here is 7.04 Feisty (desktop), and the context is SAMBA authentication through PAM with MySQL.

As your case, everything works like a charm : MySQL authentication, Samba (without authentication) reports my existing browsable shares, etc... etc... but when I want to authenticate to samba (through smbclient command with -U option), the error appear.

I can imagine somebody will say "it's because of samba" and I'm no kind of expert with it but with smbpasswd (instead of pam_mysql) it works well... And that error seem to be a wrong MySQL syntax when pam_mysql try to read data in order to authenticate. So it's probably not "because of samba" as it's probably not "because of passwd".

I've tried to play a little with the appropriate pam.d conf file (/etc/pam.d/samba) by replacing "tablename.username" to "username", and then with the database, changing table names and pam.d/samba files accordingly... but nothing better with that!

Maybe we missed something in pam configuration/installation?? I will post if I find something.

-- Excuse my english, I'm just a Frenchy ;) and it's late here

---

### Post by lee_connell on 2007-10-23
Hey Peter,

Thanks for response, did you look at my pam.d files above?  Are you using the fully qualified field names for everything?  passwordcolumn statcolumn usercolumn?

I was missing passwordcolumn and it would not authenticate any users and would throw that same mysql syntax error as above.  It has me confused!

BTW: I am going to look at using postgres for authentication.  I am a bit disapointed that I have posted my problem here and in pam-mysql as well as nss-mysql forums and no one has replied yet.

[http://pgfoundry.org/projects/sysauth](http://pgfoundry.org/projects/sysauth)

[http://blue-labs.org/software/pg_nss/index.php](http://blue-labs.org/software/pg_nss/index.php)

I might even look into LDAP.

---

### Post by Peter Riche on 2007-10-23
hey, when do you sleep?!? lol

Concerning your pam.d files, I read it when I made the first reply, and that's why I come with a second reply : do change passwordcolumn to passwdcolumn in all of your lines in your appropriate pam config file

I found that because the SQL query sent by pam was "SELECT  FROM users WHERE", you see, no value for select, so I imagined we missed to say pam_mysql where to look for the password

As for me, I'm reading SAMBA docs because now i've a LOGON_FAILURE ;) I Love errors lol

As for you, this should solve the problem, as the MySQL syntax error disappeared ;) Please indicate "SOLVED" if it's the case, as it is for me concerning pam_mysql

---

### Post by lee_connell on 2007-10-23
Peter,

I'm in EST, so it's only 9:00PM for me :)  

Thanks for proof reading my config files, that was definitely the problem! thank you!

As for your samba issue what have you found out so far?

---

