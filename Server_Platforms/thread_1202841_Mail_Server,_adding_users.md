---
title: "Mail Server, adding users"
date: 2009-07-02
forum: Server Platforms
---

### Post by oiboy on 2009-07-02
Sorry for the redunant question I'm sure, however I haven't found the answer I needed.

I recently upgraded to a fresh install of 9.04 server edition on my server.

I installed both LAMP and Mail Server from the list of items to install during the server installation. 

My LAMP server is running with no issue on [http://www.moosechan.org](http://www.moosechan.org). 

The email server is running without any issue on my default admin account (oiboy@moosechan.org), I can send and receive mail without issue. 

My question is this: How do I add other users to the system to send and receive? 

I added a test user with adduser via ssh and on the test account I can SEND only, I am unable to receive mail. Is there a group, or something else I am missing that a user must belong to, or have done in order to have full send / receive ability?

Thanks in advance,

Oi!

---

### Post by kustomjs on 2009-07-02
well how do you got your email server setup? on mysql+postfix+dovecot? or is it on LDAP?  we need little bit more information before anybody can help you.

---

### Post by oiboy on 2009-07-02
Uhm... whatever Ubuntu 9.04 Server Edition installs by default during the server installation when you select "Mail Server" to install.

I don't know, I didn't make any choices on what packages to install, just chose LAMP, SSH, and Mail Server from the package selection screen during my server install.

---

### Post by kustomjs on 2009-07-02
well by default its postfix (correct me if im wrong) but you still didnt tell us anything else about your email server. are you using dovecot or courier? and are you using LDAP or Mysql?

---

### Post by oiboy on 2009-07-02
> **oiboy said:**
> Uhm... whatever Ubuntu 9.04 Server Edition installs by default during the server installation when you select "Mail Server" to install.

I don't know, I didn't make any choices on what packages to install, just chose LAMP, SSH, and Mail Server from the package selection screen during my server install.

AGAIN no idea, whatever the 9.04 server installs by default. I installed NOTHING other than OpenSSH, LAMP, and Mail Server from the selection list. I then installed UnrealIRCD and Anope Services, Make, ccg, and MySQL.

---

### Post by kustomjs on 2009-07-02
again there is not going to be much help anybody can give you.

---

### Post by oiboy on 2009-07-02
Fair enough, guess ubuntu's documentation is poor then as it doesn't tell you anywhere what gets installed by default.

Thanks, time for a new distro then.

---

### Post by oiboy on 2009-07-02
Ok think I figured it out:


**Turn-key mail servers**

  The dovecot-postfix package in Ubuntu 9.04 provides an easy-to-deploy mail server stack, with support for SMTP, POP3, and IMAP with TLS and SASL.  
  dovecot-postfix was packaged by Ante Karamati&#263;.


So Postfix and Dovecot with MySQL

---

### Post by kustomjs on 2009-07-02
if your using Postfix+Dovecot+Mysql here is how you insert users on mysql database: 

To add new mailboxes just run a simple sql query in mysql:

insert into users (`email`, `password`, `quota`) values ('EMAIL@yourdomain.com', encrypt('PASSWORD'), 1024);

---

### Post by oiboy on 2009-07-02
Doesn't appear to work, no users table =\

I did notice that in my admin home folder I have /home/oiboy/mail/inbox where inbox is an empty document.

Anywho, here's the output from mysql:

```
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 361
Server version: 5.0.75-0ubuntu10.2 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| information_schema | 
| moosechan          | 
| mysql              | 
+--------------------+
3 rows in set (0.00 sec)

mysql> insert into users (`email`, `password`, `quota`) values ('test@moosechan.org', encrypt('test'), 1024);
ERROR 1046 (3D000): No database selected
mysql> 
```And here is the directory structure of my admin account

```

oiboy@moosechan:~$ ls
anope-1.8.0  mail  Unreal3.2
oiboy@moosechan:~$ cd mail
oiboy@moosechan:~/mail$ ls
inbox
oiboy@moosechan:~/mail$ 

```I'm sorry for the trouble, I'm new to the email side of things, I'm fairly flawless on my LAMP, IRC and such that I run for my users. There's been a demand for email otherwise I wouldn't give this the time of day lol. But like I said, it's weird cuz [email]oiboy@moosechan.org[/email] works without any issue to both send and receive.

---

