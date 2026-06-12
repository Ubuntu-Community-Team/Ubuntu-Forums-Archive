---
title: "Postfix+Courier+pam_mysql Problems"
date: 2011-02-10
forum: Server Platforms
---

### Post by philistion on 2011-02-10
Hi,

I am trying to configure my mailserver for half a week now and before I go completely nuts, I want to ask in the forum, maybe one of you guys is able to help me..

My setup is a Ubuntu Server 10.10 , x86_64 and I began with this tutorial: [https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto](https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto)

All software versions are the default ones from maverick.

Due to the reason that I was not able to send emails, I did various modifications on the configs, but with no real success.

Now I put my configs to pastebin (sensitive data as passwords and domain name was changed):

[LIST]
[*]/etc/postfix/master.cf: [http://pastebin.com/NtT6Ffcn](http://pastebin.com/NtT6Ffcn)
[*]/etc/postfix/main.cf: [http://pastebin.com/mMuQf5EA](http://pastebin.com/mMuQf5EA)
[*]/etc/sasl2/smtpd.conf: [http://pastebin.com/3D8dHNtn](http://pastebin.com/3D8dHNtn)
[*]/etc/pam.d/smtp and /etc/pam.d/imap: [http://pastebin.com/NhZ60jJg](http://pastebin.com/NhZ60jJg)
[*]/etc/pam_mysql.conf: [http://pastebin.com/Sxfi8SBN](http://pastebin.com/Sxfi8SBN)
[*]/etc/default/saslauthd: [http://pastebin.com/k1HgA5zj](http://pastebin.com/k1HgA5zj)
[*]/etc/courier/authdaemonrc: [http://pastebin.com/8fpBusmJ](http://pastebin.com/8fpBusmJ)
[*]/etc/courier/authmysqlrc: [http://pastebin.com/UPep1pdY](http://pastebin.com/UPep1pdY)
[*]/etc/courier/imapd: [http://pastebin.com/JqvngzsG](http://pastebin.com/JqvngzsG)
[*]/etc/courier/imapd-ssl: [http://pastebin.com/6exw3KKH](http://pastebin.com/6exw3KKH)
[/LIST]
The MySQL Setup is exactly the same as in the tutorial, so no need to post it here, I guess.

_ And now the log files:_

In my /var/log/mail.info I have > Feb 10 10:43:35 mydomain imapd-ssl: LOGIN FAILED, user=mymailuser@mydomain.com, ip=[::ffff::80.110.174.199]
Feb 10 10:43:35 mydomain imapd-ssl: authentication error: Input/output errorwhen I try to access imap.

And when I want to send a mail I get:> Feb 10 10:47:19 pqgruber postfix/smtpd[5865]: warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: No such file or directory
Feb 10 10:47:19 mydomain postfix/smtpd[5865]: last message repeated 3 times
Feb 10 10:47:19 mydomain postfix/smtpd[5865]: warning: SASL authentication failure: Password verification failed
Feb 10 10:47:19 mydomain postfix/smtpd[5865]: warning: 80.110.174.199: SASL PLAIN authentication failed: authentication failure
Feb 10 10:47:21 mydomain postfix/smtpd[5865]: disconnect from 80.110.174.199But why has there to be a /etc/sasldb2 when I use the mysql database?

and the following from /var/log/auth.log
> Feb 10 11:14:20 mydomain postfix/smtpd[6147]: **sql_select option missing**
Feb 10 11:14:20 mydomain postfix/smtpd[6147]: **auxpropfunc error no mechanism available**
Feb 10 11:14:20 mydomain postfix/smtpd[6147]: **_sasl_plugin_load failed on sasl_auxprop_plug_init for plugin: sql**But, the most interesting part is that the following command returns "**OK: Success**":
> sudo **testsaslauthdb -u myuser -p mypass**It's also very strange that I get no MySQL log file, although I have enabled *general_log_file = /var/log/mysql/mysql.log* and *general_log = 1* in /etc/mysql/my.cnf

One other thing, I use the email address as "username", so everybody should login with his email and his password. That shouldn't be a problem at all, should it?
              [CENTER]                 [IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] **Posting Quick Reply - Please Wait**             [/CENTER]
         
                                                                
    [CENTER]         **«**             [Previous Thread]("http://ubuntuforums.org/showthread.php?t=1685096&goto=nextoldest")             |             [Next Thread]("http://ubuntuforums.org/showthread.php?t=1685096&goto=nextnewest")         **»**     [/CENTER]
        
It seems that there are several errors combined and therefore it is very hard for me to get this system up and running. Maybe the errors, reported in the log files, aren't even the  most important ones, so please have a look at my config files and if you see something unusual, please tell me!

I would be very grateful for any tips and corrections!


I am also open for easier alternatives, the most important requirement is the ability to manage virtual users and to be able to import old emails from courier, so I preferred Postfix+Courier+SASL+PAM+MySQL.
What other (less painful) ways are there to have a working SSL/TLS Mail setup with virtual users, the ability to manage them online and [if you suggest not using courier] at least the possibility to import old mails from courier..?


Thanks in advance!

philistion

---

### Post by elico on 2011-02-10
Courier is a nice choice but i'm using dovecot and very happy about it.
did you tried to install the server as a stand alone? not virtual?
this tutorial in ubuntu tutorials is nice but not the one that I used cause i found another one.
i recommend to you use first the simple mail setup to understand the concept using this tutorial
[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

and after that you can either use this courier great tutorial for openBSD (everything is the same except that you will need to use apt-get to install the packages)
[http://www.kernel-panic.it/openbsd/mail/](http://www.kernel-panic.it/openbsd/mail/)
(ho and skip the antvirus part.)
i have used these tutorials and it took me a whole day to read them and understand what is important and what needed for the server to work.
[http://workaround.org/ispmail/lenny](http://workaround.org/ispmail/lenny)
in this^^ (ispmail) link you cant copy and paste code cause it's curropted and missing one line for the server to actually work.

i am using postfixadmin to manage the sql database and it is very very usefull.

it seems likie your sasl thing is not working properly or you didnt installed one of the plugins required for mysql.

---

### Post by philistion on 2011-02-11
Thanks for the links, I am just reading through the tutorial at workaround.org. It seems that there were various parts of the I did not understand correctly, I think I get the "big picture" now :)

But, what alternatives are there instead of Pam , SASL and MySQL?

LDAP may be even more complicated. But there should be alternatives..?

If I get PAM+SASL+MySQL up and running, I'll stick with that setup, but If I can't solve the problem it would be fine to know at least one other alternative, instead of having to create normal unix user accounts, which is extremely uncomfortable in large companies.

---

### Post by elico on 2011-02-11
no company that is big and using postifx+dovecot\courier is using the PAM accounts(local machine one)
they are using openLDAP or mysql such DB.
i am using dovecot as the sasl "agent"
the mysql working perfect from dovecot just adding the basic settings file.
SASL is just an auth option and mySQL\PAM are users and passwords databases.
instead of the standard SASL you can use dovecot as "SASL" that will do everything you need.
i will post here my full working settings later so you can understand it.

---

### Post by philistion on 2011-02-12
The tutorial on workaround.org is great, thanks man!

Hm, so LDAP would be preferred if the number of users is increasing fast.

There is one thing left that bothers me: My users want to change their password from the intranet via web browser.
Postfixadmin is not suitable for the layout on workaround.org, I could adjust the queries, but I do not want to do this if there's another fine configuration tool.
Or should I rather stick with OpenLDAP from the beginning? 

What are the chances that I have to code my own "Configuration" tool, isn't this a commond "need" for mail hosts with virtual users?
The admins naturally won't set the passwords manually for each user.

Abroad from our mail setup we have a Subversion server with apache2+WebDAV and a web interface (with Basic Authentication) with Trac for viewing our SVN-Repositories and do some project management.
How can these different aspects be reconciled, so that only one account database, directory or whatever exists but is used for all the services we offer?

---

### Post by elico on 2011-02-12
well in this case you it will be much more simple to use openLDAP but you will need to code the password change web-page by yourself.
if you do ask me postfixadmin is great.
with postfixadmin you wont need to touch the database by yourself they have a prepared sql files to buid the database very well.
to change the users passwords on postfixadmin you have specific page just for that and every user can do it by himself using his own username and password.

if you do have an option to build the management scripts for such a system many people will be happy to get it.

---

