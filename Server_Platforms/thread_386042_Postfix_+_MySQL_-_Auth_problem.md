---
title: "Postfix + MySQL - Auth problem"
date: 2007-03-16
forum: Server Platforms
---

### Post by cfyves on 2007-03-16
Hi all,

I've recently installed Ubuntu 6.06 as a complete reinstall on an existing server.

One thing That I'm a bit tripped on is Postfix + MySQL.

I used these pages as reference:
[PostfixCompleteVirtualMailSystemHowto]("https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto")
[PostfixBasicSetupHowto]("https://help.ubuntu.com/community/PostfixBasicSetupHowto")
[PostfixAmavisNewClamAVSpamAssassin]("https://help.ubuntu.com/community/PostfixAmavisNewClamAVSpamAssassin")

I also installed Postfix Admin
[http://high5.net/page9.html]("http://high5.net/page9.html")

I set up a domain, and created an email.
I can receive email with no problems.

I've used courier and in the logs, I see authdaemond.mysql, spamd, amavis start up with no problems when this server starts up.

When I attempt to log in via Outlook I get the following:
In mail.log
> 
Mar 16 14:20:06 ubuntu postfix/smtpd[5760]: connect from unknown[10.1.1.1]
Mar 16 14:20:08 ubuntu postfix/smtpd[5760]: warning: unknown[10.1.1.1]: SASL LOGIN authentication failed


in auth.log
> 
Mar 16 14:20:06 ubuntu saslauthd[5227]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=  user=yves
Mar 16 14:20:08 ubuntu saslauthd[5227]: DEBUG: auth_pam: pam_authenticate failed: Authentication failure
Mar 16 14:20:08 ubuntu saslauthd[5227]: do_auth         : auth failure: [user=yves] [service=smtp] [realm=jeflipe.ca] [mech=pam] [reason=PAM auth error]


Any ideas on what I can check?

I have been googling for a while.

Thanks,

Yves

---

### Post by Nikron on 2007-03-16
Can you post your /etc/courier/authdaemonrc

I have my postfix set up in a similiar way, and had to change this in that file

authmodulelist="authmysql"

---

### Post by cfyves on 2007-03-16
This are the uncommented options in the authdaemonrc file:
> 
authmodulelist="authmysql"

authmodulelistorig="authcustom authcram authuserdb authldap authpgsql authmysql authpam"

daemons=5

version=""

authdaemonvar=/var/run/courier/authdaemon


Thanks for the reply,

Yves

---

### Post by astrogazer on 2007-03-16
authdaemonrc looks ok

How does your authmysqlrc look like?

Can you succesfully login via Courier?

---

### Post by cfyves on 2007-03-16
This is the uncommented options in authmysqlrc:
> 
MYSQL_SERVER		127.0.0.1
MYSQL_USERNAME		user
MYSQL_PASSWORD		password
MYSQL_PORT		3306
MYSQL_OPT		0
MYSQL_DATABASE		database
MYSQL_USER_TABLE	passwd
MYSQL_CRYPT_PWFIELD	crypt
MYSQL_UID_FIELD		112
MYSQL_GID_FIELD		119
MYSQL_LOGIN_FIELD	id
MYSQL_HOME_FIELD	home
MYSQL_NAME_FIELD	name


username, password and database were modified to post on the forum.

When I telnet pop3, and attempt to login with the email and password, I get 
-ERR login failed

And, when I telnet imap I get "NO Error in IMAP command received by server" when I try to login.

---

### Post by astrogazer on 2007-03-16
At a first glance authmysqlrc looks ok.

Do you see anything in your mysql.log when you try to login?
There should be a few new queries on each attempt.

---

### Post by Nikron on 2007-03-16
Also, you might want to check out:  /etc/pam.d/imap

---

### Post by cfyves on 2007-03-17
The MySQL logs don't show anything.

in the /etc/pam.d/imap file:

> 
@include common-auth
@include common-account
@include common-session


I've checked these 3 files....

> 
common-auth :
auth	required	pam_unix.so nullok_secure


> 
common-account:
account	required	pam_unix.so


> 
common-session:
session	required	pam_unix.so
session	optional	pam_foreground.so


I'm assuming I should have something like the following in once of these files:
> 
auth sufficient pam_mysql.so user=mail passwd=secret host=localhost db=mail table=accountuser usercolumn=username passwdcolumn=password crypt=1 logtable=log logmsgcolumn=msg logusercolumn=user loghostcolumn=host logpidcolumn=pid logtimecolumn=time

account required pam_mysql.so user=mail passwd=secret host=localhost db=mail table=accountuser usercolumn=username passwdcolumn=password crypt=1 logtable=log logmsgcolumn=msg logusercolumn=user loghostcolumn=host logpidcolumn=pid logtimecolumn=time


Thanks,

Yves

---

### Post by astrogazer on 2007-03-19
If nothing shows up in the mysql queries log then you have a problem with
your your MySQL connection settings.

Having absolutely nothing in the log files means that Courier is not even
'trying' to connect to MySQL. Even if it tried but failed there should be  a message.

---

### Post by cfyves on 2007-03-19
Ok.

I now have the mysql logs. They were commented out, not sure if this is from a default install. I didn't comment them.

Now in my mysql.log I have these 2 types of login requests:
> 
070319 10:54:47	      8 Connect     dbuser@localhost on 
		      8 Init DB     postfixdb
		      8 Query       SELECT id, crypt, "", 112, 119, home, "", "", name, "" FROM passwd WHERE id = "emailuser@domain.com"
		      9 Quit

And
> 
070319 10:59:57	     10 Connect     dbuser@localhost on postfixdb
		     10 Init DB     postfixdb
		     10 Query       SELECT password FROM mailbox WHERE  = 'emailuser'
		     10 Quit   "



Over in my auth.log file I have
> 
Mar 19 11:04:54 ubuntu saslauthd[5235]: pam_mysql - MySQL error(You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '= 'emailuser'' at line 1)
Mar 19 11:04:54 ubuntu saslauthd[5235]: DEBUG: auth_pam: pam_authenticate failed: Error in service module
Mar 19 11:04:54 ubuntu saslauthd[5235]: do_auth         : auth failure: [user=emailuser] [service=smtp] [realm=domain.com] [mech=pam] [reason=PAM auth error]


---

### Post by cfyves on 2007-03-19
Ok, I'm not sure If I'm getting closer...

When trying to retrieve email with Outlook express I have the following in the mysql.log.

> 
61 Connect     postfixuser@localhost on 
61 Init DB     postfixdb
61 Query       SELECT id, crypt, "", 112, 119, home, "", "", name, "" FROM passwd WHERE id = "user@domain.com"
61 Quit  


So, it would seem as though the postfix user is trying to authenticate my log in attempt.

But, I'm not sure where that query would come from. I was under the impression that it would use the settings in my mysql_virtual_alias_maps.cf (or other conf files), and there is no directive to a table named "passwd" in those files.

Am I way off???

Or maybe getting closer?

---

### Post by astrogazer on 2007-03-19
There are multiple errors in the SQL statements.

Other than that I cannot make much sense. I would go ahead and re-edit all the config files
because the settings in each one are different.

auth sufficient pam_mysql.so user=mail passwd=secret host=localhost db=mail table=accountuser usercolumn=username

MYSQL_DATABASE database

All parameters should be the same in all these conf files

---

### Post by cfyves on 2007-03-19
> **astrogazer said:**
> There are multiple errors in the SQL statements.

Other than that I cannot make much sense. I would go ahead and re-edit all the config files
because the settings in each one are different.

auth sufficient pam_mysql.so user=mail passwd=secret host=localhost db=mail table=accountuser usercolumn=username

MYSQL_DATABASE database

All parameters should be the same in all these conf files

Ok.... just to make sure I understand...
In the /etc/pam.d/pop3 , imap and smtp I should have this data.

I'd like a little clarification on the data because at this point I'm getting a little confused. I've been googling and have found quite a few examples that confuse me a little.

In the auth sufficient string, I should enter the user and password with which to access the database... at the moment this is what I have in the config files:
auth sufficient pam_mysql.so user=dbuser passwd=dbpassword host=localhost db=postfixdbname table=mailbox usercolumn=username passwdcolumn=password

I have this in the :
/etc/pam.d/pop3
/etc/pam.d/imap
/etc/pam.d/smtp
files....

I found the location of the SQL code that causing the login attempt in my mysql.log file.
This was coming from the settings in the /etc/courier/authmysqlrc file.

---

### Post by astrogazer on 2007-03-20
The problem is that you have not entered the correct parameters in the .conf files.
For example in authmysqlrc you declare

MYSQL_DATABASE database

which means that the name of the database which holds credentias etc. is database

but then in another .conf file you have this:
auth sufficient pam_mysql.so user=mail passwd=secret host=localhost db=mail table=accountuser usercolumn=username

In this one you declare the name of the database as mail!

Then in the mysql query log you get:
61 Connect postfixuser@localhost on
61 Init DB postfixdb

meaning you are trying to connect as postfixuser to database postfixdb


Probably the best thing to do is start from scratch using the following tutorial:

[http://postfix.wiki.xs4all.nl/index.php?title=Virtual_Users_and_Domains_with_Courier-IMAP_and_MySQL](http://postfix.wiki.xs4all.nl/index.php?title=Virtual_Users_and_Domains_with_Courier-IMAP_and_MySQL)

Try to do one step at a time, and make sure you understand what you are doing and that it works.
If this is a production server and not something you are just practicing on I would strongly advise
you to take it offline because apparently there are some major security holes.

There are some really nice books on Postfix out there. Just get one and read it thoroughly.

Hope this helps a little bit more.

---

### Post by cfyves on 2007-03-20
Hi there...

All the db info in the configs still look the same... but I think it might be just as quick to start over.

I've also found this page on setting up a virtual mail system like this:
[http://flurdy.com/docs/postfix/]("http://http://flurdy.com/docs/postfix/")

I'm gonna go through them and attempt to reinstall.

Thanks for your assistance.

I will post again.

Thanks,

Yves

---

