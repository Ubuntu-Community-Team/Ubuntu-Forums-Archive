---
title: "Howto: set up a mail server in Ubuntu"
date: 2006-06-01
forum: Tutorials
---

### Post by flurdy on 2006-06-01
A how to for a complete step by step guide to install, configure and run 
a mail server on a GNU / Linux system 

The server includes theses programs:
Ubuntu + Postfix + Courier IMAP + MySQL + Amavisd-new + SpamAssassin + ClamAV + SASL + TLS + SquirrelMail + Postgrey

[flurdy.com/docs/postfix]("http://flurdy.com/docs/postfix")

The how to is now beeing upgraded to support dapper since it was released today.
It is extensive and widely used.

You can use it as extension or alternative to the guides on the wiki, E.g.
[https://wiki.ubuntu.com/Postfix](https://wiki.ubuntu.com/Postfix)
[https://wiki.ubuntu.com/PostfixBasicSetupHowto](https://wiki.ubuntu.com/PostfixBasicSetupHowto)
[https://wiki.ubuntu.com/PostfixVirtualMailBoxClamSmtpHowto](https://wiki.ubuntu.com/PostfixVirtualMailBoxClamSmtpHowto)
[https://wiki.ubuntu.com/PostfixCompleteVirtualMailSystemHowto](https://wiki.ubuntu.com/PostfixCompleteVirtualMailSystemHowto)

Please discuss in this thread any issues or comments regarding this, the 5th edition for dapper.

**[COLOR="Red"]Staff note:[/COLOR]** The following links are very old; please note that they may not apply to recent versions of Ubuntu.
For other version please use these threadsL
[Breezy howto thread.]("/showthread.php?t=97600")
[Hoary howto thread.]("/showthread.php?t=40047")

---

### Post by flurdy on 2006-06-02
Forgot to include the url! :)
first post edited to include it.

[http://flurdy.com/docs/postfix](http://flurdy.com/docs/postfix)

---

### Post by mossholderm on 2006-06-04
FYI, its TLS (Transport Layer Security), not TSL :)

---

### Post by flurdy on 2006-06-05
Thanks. :) cant spell in any language

---

### Post by woot on 2006-06-05
woooah! can't wait to try this myself! Im on a laptop with dapper but my server at home, well server is a big word...call it a download pc :) is still running win2k but after the exams im planning to put dapper on it! looking forward to play around with the mail server thingy!

thnx for the howto

---

### Post by the_man_stephen on 2006-06-08
Hi,

After following the guidelines set out in [http://flurdy.com/docs/postfix](http://flurdy.com/docs/postfix) I get an error saying "Invalid Zone Type: Local"

Can anyone help me out as I can't seem to find the solution to the problem anywhere online?

Cheers

---

### Post by Aeudian on 2006-06-09
I am pretty far along in the guide, at the testing stage and i am having undeliverable mail.  I am using postfix to smtp relay to an exchange server,  i telnet into the device and am able to ehlo, mail from, rcpt to, and data, just fine and it queues up my mail message.  But at the point watching the exchange server the email never nor does my system connect to the server with the email. i put my exchange server under relayhost in the main.cf and also changed 127.0.0.1 for mynetworks to my external ip's network.

Any idea whats wrong or how to debug the postfix step by step.

---

### Post by makan on 2006-06-26
can i use postfixadmin ([http://high5.net/postfixadmin/](http://high5.net/postfixadmin/)) to manage my posfix if i use your howto? :-k

---

### Post by FedeKrum on 2006-06-27
Can´t get to [http://flurdy.com/docs/postfix](http://flurdy.com/docs/postfix) .
The page it is not viewable.

Any other place to get this howto?

THX

---

### Post by RShadow on 2006-06-30
SOLVED: I had an error in authmysqlrc .. now I just need to figure out how I can send mail to the outsideworld.  If I send mail to an address in my domain it works fine.. but If I try and send mail to say my gmail account the server denies the relay request.

sorry for teh double posting... didn't realize there was a dapper thread

anways..

---
I am running into a small problem.  Whenever I try to auth to check mail the login fails.  I have verified that the password that is being send and the password stored in the mysql database match, so I can't figure out why it is failing.

However I have noticed the following in my logs
```

Jun 30 07:24:52 zues imaplogin: Connection, ip=[::ffff:xxx.xxx.xxx.xxx]
Jun 30 07:24:52 zues imaplogin: LOGIN: DEBUG: ip=[::ffff:xxx.xxx.xxx.xxx], command=CAPABILITY
Jun 30 07:24:53 zues imaplogin: LOGIN: DEBUG: ip=[::ffff:xxx.xxx.xxx.xxx], command=LOGIN
Jun 30 07:24:53 zues imaplogin: LOGIN: DEBUG: ip=[::ffff:xxx.xxx.xxx.xxx], username=user@domain
Jun 30 07:24:53 zues imaplogin: LOGIN: DEBUG: ip=[::ffff:xxx.xxx.xxx.xxx], password=cleartextpass
Jun 30 07:24:53 zues imaplogin: authdaemon: starting client module
Jun 30 07:24:53 zues imaplogin: authdaemon: TEMPFAIL - no more modules will be tried
Jun 30 07:24:58 zues imaplogin: LOGIN FAILED, ip=[::ffff:xxx.xxx.xxx.xxx]

```
stripped IP's and acutal domains/passwords/users.. any ideas what is wrong with my setup?

---

### Post by RShadow on 2006-06-30
Well I have fixed my courier sasl problem, but now I am having a problem with smtpd sasl issues.

Whenever I am trying to send mail outside of my domain it is being rejected.  Here are a few log's

mysql log
```

 35 Connect     mail@localhost on maildb
                     35 Query       SELECT destination FROM aliases WHERE mail='mydomain' and enabled = 1
                     36 Connect     mail@localhost on maildb
                     36 Query       SELECT domain FROM domains WHERE domain='mydomain' and enabled = 1
060630 13:51:50      35 Query       SELECT destination FROM aliases WHERE mail='gmail.com' and enabled = 1
                     36 Query       SELECT domain FROM domains WHERE domain='gmail.com' and enabled = 1

```

What I find strange is that it is running a query looking for gmail.com which I know is failing... I can't possible list every domain that somebody might want to send mail too.. so I know something is arsed up in my cofigs somewhere.. I just can't seem to figure out where.

mail.log
```

Jun 30 13:51:50 zues postfix/smtpd[2787]: NOQUEUE: reject: RCPT from unknown[xxx.xxx.xxx.xxx]: 554 <theuser@gmail.com>: Relay access denied; from=<localuser@mydomain> to=<theuser@gmail.com> proto=ESMTP helo=<[192.168.2.2]>
Jun 30 13:51:51 zues postfix/smtpd[2787]: lost connection after RCPT from unknown[xxx.xxx.xxx.xxx]

```

main.cf (snippets of relevant stuff)
```

inet_interfaces = all
mynetworks_style = host

# requirements for teh sender details
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit

# requirements for the connectin server
smtpd_client_restrictions = reject_rbl_client relays.ordb.org, reject_rbl_client blackholes.easynet.n1, reject_rbl_client dnsb1.njab1.org

#adding the postgrey policy:
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unauth_destination, check_policy_service inet:127.0.0.1:60000, permit


smtpd_sasl_auth_enabled = yes
broken_sasl_auth_clients = yes
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
smtpd_sasl_security_options = nonanonymous
smtpd_sasl_local_domain =

smtpd_use_tls = yes
smtpd_tls_cert_file = /etc/postfix/postfix.cert
smtpd_tls_key_file = /etc/postfix/postfix.key
smtpd_data_restrictions = reject_unauth_pipelining

```

smtpd.conf
```

pwcheck_method: auxprop
auxprop_plugin: sql
mech_list: plain login cram-md5 digest-md5
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: mail
sql_passwd: myubersecurepassword
sql_database: maildb
sql_select: select clear from users where id='%u@%r' and enabled = 1

```

any help would be appreciated.

---

### Post by herald on 2006-06-30
[QUOTE=RShadow]SOLVED: I had an error in authmysqlrc .. now I just need to figure out how I can send mail to the outsideworld.[/QUOTE]

First, I'd like to apologize to Flurdy for posting my first request in the wrong thread...Didn't realize there was a whole other Dapper Drake thread!  Sorry!

I'm probably being an idiot here, but where did you find the authmysqlrc file for dapper drake?  I understand from the courier-authlibs information page that mysql support is integrated into that tarball, but after doing the "apt-cache search courier-authmysql", I can't seem to find the package, and therefore I have no authmysqlrc file...10 to 1 says that it has to be manually built from source code, but I'd like to have someone confirm or deny that.  Thanks!
BTW, this is a AMD-64 build, so the repositories may be different?

---

### Post by leetcharmer on 2006-07-01
the tutorial is too confusing for someone who is new.  Please make it more newbie friendly, k thx~ :D

example: write in commands to edit / create files 'sudo vim /etc/postfix/(whatever)'

Also, be more precise and confident with the content: I want what you're offering, not something similar.  Give me all the steps to make exactly what you have.

---

### Post by sebastian2 on 2006-07-01
[FONT="Courier New"]/var/log/mail.log[/FONT] says:

```
Jul  1 10:07:14 mail postfix/smtpd[10067]: connect from some.host.com[1.2.3.4]
Jul  1 10:07:14 mail postfix/smtpd[10067]: warning: SASL authentication failure: no secret in database
Jul  1 10:07:14 mail postfix/smtpd[10067]: warning: some.host.com[1.2.3.4]: SASL CRAM-MD5 authentication failed
Jul  1 10:07:14 mail postfix/smtpd[10067]: warning: SASL authentication failure: Password verification failed
Jul  1 10:07:14 mail postfix/smtpd[10067]: warning: some.host.com[1.2.3.4]: SASL PLAIN authentication failed
Jul  1 10:07:14 mail postfix/smtpd[10067]: warning: some.host.com[1.2.3.4]: SASL LOGIN authentication failed
Jul  1 10:07:19 mail postfix/smtpd[10067]: warning: SASL authentication failure: no secret in database
Jul  1 10:07:19 mail postfix/smtpd[10067]: warning: some.host.com[1.2.3.4]: SASL CRAM-MD5 authentication failed
Jul  1 10:07:20 mail postfix/smtpd[10067]: warning: SASL authentication failure: Password verification failed
Jul  1 10:07:20 mail postfix/smtpd[10067]: warning: some.host.com[1.2.3.4]: SASL PLAIN authentication failed
Jul  1 10:07:23 mail postfix/smtpd[10067]: warning: some.host.com[1.2.3.4]: SASL LOGIN authentication failed
Jul  1 10:07:27 mail postfix/smtpd[10067]: lost connection after AUTH from some.host.com[1.2.3.4]
Jul  1 10:07:27 mail postfix/smtpd[10067]: disconnect from some.host.com[1.2.3.4]
```

while [FONT="Courier New"]/var/log/mysql/mysql.log[/FONT] says nothing (it logs other queries, so logging itself seems to be ok)

[FONT="Courier New"]/etc/postfix/sasl/smtpd.conf[/FONT] is

```
pwcheck_method: auxprop
auxprop_plugin: sql
mech_list: plain login cram-md5 digest-md5
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: someuser
sql_passwd: somepass
sql_database: somedb
sql_select: select clear from users where id='%u@%r' and enabled = 1
```

someuser with somepass is allowed do connect to use somedb at localhost. So where is the problem? It seems that postfix/sasl does not even try to connect to the database

---

### Post by RShadow on 2006-07-01
Hmm.. no postfix gurus around?  Still have not been able to solve this one.

as for my authmysqlrc file.. I had to create it myself in /etc/courier

---

### Post by Kurdt on 2006-07-03
Well, i am having a problem described here, 

[http://www.ubuntuforums.org/showthread.php?t=206591](http://www.ubuntuforums.org/showthread.php?t=206591)
***(SASL per-process initialization failed)***

Maybe posting here gives me more luck to find the solution and maybe flurdy sees my question.

Thanks

---

### Post by willytk on 2006-07-03
Has anyone managed to get amavisd-new to work with mysql-white/blacklisting (wbl). I've roughly followed [http://www.ijs.si/software/amavisd/README.sql.txt](http://www.ijs.si/software/amavisd/README.sql.txt) and have managed to get amavisd to store the quarantined messages in a table...but I can not get it to look up the wbl table. There's no sign of the query in the mysql.log.

I've set **$sql_select_white_black_list** = 'SELECT wb FROM wblist,mailaddr WHERE (wblist.rid=?) AND (wblist.sid=mailaddr.id) AND (mailaddr.email IN (%k)) ORDER BY mailaddr.priority DESC' in the 50-user conf file amavis/conf.d

Anyone help me? Show me their amavis conf files? Thanks a lot!

Regards,
Willy T. Koch
Oslo, Norway

---

### Post by RShadow on 2006-07-04
I think I posted this somewhere else, but if you are having trouble going through flurdy's guide then I would suggest you give this howto a try

[http://workaround.org/articles/ispmail-sarge/](http://workaround.org/articles/ispmail-sarge/)

It worked perfectly for me, and it explains alot of what is going on as well. I guess it just made more sense to me, made me understand why I was doing what I was doing so when I did run into a few hitches (misspellings) I knew exactly where to look and was up and runnign with this guide in about 20 min.

---

### Post by the_idol on 2006-07-06
Has anyone including the author been sucessful in this installation?

The Idol

---

### Post by viniosity on 2006-07-06
[QUOTE=the_idol]Has anyone including the author been sucessful in this installation?
The Idol[/QUOTE]

I have not been.. I'm getting closer though.  A few typos here and there messed me up.  Right now I'm at the stage where I can access the courier imap via thunderbird but I can't send myself an email from anywhere (internal or external).  I keep getting this error:


```

Jul  7 09:43:04 mail2 postfix/smtpd[4816]: connect from unknown[50.59.29.10]
Jul  7 09:43:04 mail2 postfix/smtpd[4816]: NOQUEUE: reject: RCPT from unknown[207.59.239.130]: 554 <viniosity@foo.net>: Relay access denied; from=<testaccount@gmail.com> to=<viniosity@foo.net> proto=ESMTP helo=<mail.gmail.com>

```

I've done lots of searching on google for 554 relay access denied but the solutions I found don't seem to apply to this scenario where domains are kept in the dbase instead of /etc/postfix/virtual

Any ideas?

---

### Post by neufena on 2006-07-07
Hi,

Firstly thanks Flurdy for the howto, greetins from a fellow manc!

I've managed to get my server up and running really well, the only bit I can't seem to get sorted is the SASL for sending mail. By tailing the logs it appears that the auth is checking with the MySQL tables but not accepting my password as correct.

I've attached the relevent config files.  I hope someone can help me fix the problem.  let me know if you need any of the log files on any more info.

---

### Post by the_idol on 2006-07-08
I got mine working finally by using a combination of flurdy's howto  and this one mentioned earlier [http://workaround.org/articles/ispmail-sarge/]("http://workaround.org/articles/ispmail-sarge/")
Now that I've got it working I am now going work on making postfixadmin work with this setup and I'll be happy.

The Idol

---

### Post by viniosity on 2006-07-08
the_idol: Could you give us a few hints as to what modifications you made to the flurdy docs to get going?  I tried replacing my main.cf and master.cf files with the ones from neufena but am still getting the relay error when attempting to receive mail.  Any tips would be appreciated..

---

### Post by tbird469 on 2006-07-09
After much hair pulling with getting postfix/smtp/sasl/mysql working, it turned out that I had trailing spaces at the end of each line from the copy/paste in the /etc/postfix/sasl/smtpd.conf

After removing the spaces from the file and reloading postfix all was well.

I was getting errors in /var/log/auth.log like these until I removed the trailing spaces:

postfix/smtpd[27381]: SQL engine 'mysql ' not supported
postfix/smtpd[27381]: auxpropfunc error no mechanism available
postfix/smtpd[27381]: _sasl_plugin_load failed on sasl_auxprop_plug_init for plugin: sql

Other than that the howto was great.

---

### Post by caledfwlch on 2006-07-14
I'm in need of some help,

I can't seem to be able to login to SquirrelMail. I double checked my authmysqlrc file and all the fields are set properly, double checked my db and everything's fine. The squirrelmail config test goes well. The test on Furby's site went well. I have no idea what else could be wrong.

This is my mail.log below, any ideas?

[FONT="Courier New"][SIZE="2"]Jul 14 21:28:04 mail imaplogin: Connection, ip=[::ffff:127.0.0.1]
Jul 14 21:28:04 mail imaplogin: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], command=LOGIN
Jul 14 21:28:04 mail imaplogin: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], username=username@domain.tld
Jul 14 21:28:04 mail imaplogin: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], password=mypassword
Jul 14 21:28:04 mail imaplogin: authdaemon: starting client module
Jul 14 21:28:04 mail imaplogin: authdaemon: TEMPFAIL - no more modules will be tried
Jul 14 21:28:09 mail imaplogin: LOGIN FAILED, ip=[::ffff:127.0.0.1]
Jul 14 21:28:09 mail imaplogin: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], command=LOGOUT
Jul 14 21:28:09 mail imaplogin: LOGOUT, ip=[::ffff:127.0.0.1][/SIZE][/FONT]

SquirrelMail config test:

[FONT="Courier New"][SIZE="2"]SquirrelMail configtest

This script will try to check some aspects of your SquirrelMail configuration and point you to errors whereever it can find them. You need to go run conf.pl in the config/ directory first before you run this script.

SquirrelMail version:	1.4.6
Config file version:	1.4.0
Config file last modified:	14 July 2006 18:09:40
Checking PHP configuration...
    PHP version 4.4.2-1build1 OK.
    PHP extensions OK.
Checking paths...
    Data dir OK.
    Attachment dir OK.
    Plugins are not enabled in config.
    Themes OK.
    Default language OK.
    Base URL detected as: [http://192.168.1.122/squirrelmail/src](http://192.168.1.122/squirrelmail/src)
Checking outgoing mail service....
    SMTP server OK (220 mydomain.com ESMTP Postfix)
Checking IMAP service....
    IMAP server ready (* OK [CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA AUTH=CRAM-MD5 AUTH=CRAM-SHA1 IDLE ACL ACL2=UNION STARTTLS] Courier-IMAP ready. Copyright 1998-2004 Double Precision, Inc. See COPYING for distribution information.)
    Capabilities: * CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA AUTH=CRAM-MD5 AUTH=CRAM-SHA1 IDLE ACL ACL2=UNION STARTTLS
Checking internationalization (i18n) settings...
     gettext - Gettext functions are available. You must have appropriate system locales compiled.
     mbstring - Mbstring functions are available.
     recode - Recode functions are unavailable.
     iconv - Iconv functions are available.
     timezone - Webmail users can change their time zone settings.
Checking database functions...
     PHP Pear DB support is present.
    mysql database support present.
    preferences database connect successful.
    mysql database support present.
    addressbook database connect successful.
    mysql database support present.
    global addressbook database connect successful.

Congratulations, your SquirrelMail setup looks fine to me![/SIZE][/FONT]

---

### Post by caledfwlch on 2006-07-14
> **caledfwlch said:**
> I'm in need of some help,

I can't seem to be able to login to SquirrelMail. I double checked my authmysqlrc file and all the fields are set properly, double checked my db and everything's fine. The squirrelmail config test goes well. The test on Furby's site went well. I have no idea what else could be wrong.

This is my mail.log below, any ideas?

[FONT="Courier New"][SIZE="2"]Jul 14 21:28:04 mail imaplogin: Connection, ip=[::ffff:127.0.0.1]
Jul 14 21:28:04 mail imaplogin: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], command=LOGIN
Jul 14 21:28:04 mail imaplogin: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], username=username@domain.tld
Jul 14 21:28:04 mail imaplogin: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], password=mypassword
Jul 14 21:28:04 mail imaplogin: authdaemon: starting client module
Jul 14 21:28:04 mail imaplogin: authdaemon: TEMPFAIL - no more modules will be tried
Jul 14 21:28:09 mail imaplogin: LOGIN FAILED, ip=[::ffff:127.0.0.1]
Jul 14 21:28:09 mail imaplogin: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], command=LOGOUT
Jul 14 21:28:09 mail imaplogin: LOGOUT, ip=[::ffff:127.0.0.1][/SIZE][/FONT]

SquirrelMail config test:

[FONT="Courier New"][SIZE="2"]SquirrelMail configtest

This script will try to check some aspects of your SquirrelMail configuration and point you to errors whereever it can find them. You need to go run conf.pl in the config/ directory first before you run this script.

SquirrelMail version:	1.4.6
Config file version:	1.4.0
Config file last modified:	14 July 2006 18:09:40
Checking PHP configuration...
    PHP version 4.4.2-1build1 OK.
    PHP extensions OK.
Checking paths...
    Data dir OK.
    Attachment dir OK.
    Plugins are not enabled in config.
    Themes OK.
    Default language OK.
    Base URL detected as: [http://192.168.1.122/squirrelmail/src](http://192.168.1.122/squirrelmail/src)
Checking outgoing mail service....
    SMTP server OK (220 mydomain.com ESMTP Postfix)
Checking IMAP service....
    IMAP server ready (* OK [CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA AUTH=CRAM-MD5 AUTH=CRAM-SHA1 IDLE ACL ACL2=UNION STARTTLS] Courier-IMAP ready. Copyright 1998-2004 Double Precision, Inc. See COPYING for distribution information.)
    Capabilities: * CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA AUTH=CRAM-MD5 AUTH=CRAM-SHA1 IDLE ACL ACL2=UNION STARTTLS
Checking internationalization (i18n) settings...
     gettext - Gettext functions are available. You must have appropriate system locales compiled.
     mbstring - Mbstring functions are available.
     recode - Recode functions are unavailable.
     iconv - Iconv functions are available.
     timezone - Webmail users can change their time zone settings.
Checking database functions...
     PHP Pear DB support is present.
    mysql database support present.
    preferences database connect successful.
    mysql database support present.
    addressbook database connect successful.
    mysql database support present.
    global addressbook database connect successful.

Congratulations, your SquirrelMail setup looks fine to me![/SIZE][/FONT]

Edit: I changed the username/password fields in the log file here   to hide it, it is passing that info correctly.

Meant to edit the first post, not reply. ](*,)

---

### Post by caledfwlch on 2006-07-17
It might not be a problem with SquirrelMail afterall, when trying to connect to courier from telnet I get:

telnet localhost 143
A01 LOGIN [email]myuser@mydomain.com[/email] mypassword
A01 NO Login failed.

Would anyone have any clues? I'm at a real loss.

Edit:

Nevermind, was a typo in my authmysqlrc file... Two and a half days of debugging for a typo. Weee. Log files are now my best friend.

Edit The Second:

Just wanted to pass along a thank you to Flurdy, great tut! After haggling with a few minor issues that were entirely of my own doing, I've got a email server running, sending and receiveing without a hitch to the postmaster account. Cheers!

---

### Post by matko on 2006-07-20
hello. after i succesfully login with SquirrelMail version 1.4.4 i get error

```
Preference database error (no such field). Exiting abnormally
```

is it problem with postfix, squid or mysql?

than you

---

### Post by crilen007 on 2006-07-21
I went through the entire setup, but I can't seem to Telnet to my postfix server from localhost.

It starts up ok, and without error. Not sure what files one may need to help with this.

---

### Post by elvis on 2006-07-24
Another "thank you" to Flurdy for the great guide.  Your time and effort is greatly appreciated.

I've followed the guide and learned a LOT about postfix and courier (coming from a sendmail/cyrus background, and wanting to learn something different).  Mail seems to be arriving where it ought to, which is a good thing.

One problem I have however is I can't log into the Courier-IMAP server from mutt.  I don't know if this is a mutt problem, an SASL problem, or something else.

I open mutt, tell it to connect (press "c") and feed it imap://user:pass@servername .  It finds the TLS certificitate fine, tells me it's authenticating via CRAM-MD5, and then gives me a "SASL Authentication Failed" error.

My logfiles look like this:
```

Jul 25 10:19:46 localhost imaplogin: Connection, ip=[::ffff:127.0.0.1]
Jul 25 10:19:46 localhost imaplogin: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], command=CAPABILITY
Jul 25 10:19:46 localhost imaplogin: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], command=STARTTLS
Jul 25 10:19:47 localhost imaplogin: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], command=CAPABILITY
Jul 25 10:19:48 localhost imaplogin: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], command=AUTHENTICATE
Jul 25 10:19:51 localhost imaplogin: authdaemon: starting client module
Jul 25 10:19:51 localhost imaplogin: authdaemon: REJECT
Jul 25 10:19:56 localhost imaplogin: LOGIN FAILED, ip=[::ffff:127.0.0.1]
Jul 25 10:19:58 localhost imaplogin: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], command=LOGOUT

```

Now if I telnet it instead, I get the following:

```

# telnet localhost 143
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
* OK [CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA AUTH=CRAM-MD5 AUTH=CRAM-SHA1 IDLE ACL ACL2=UNION STARTTLS] Courier-IMAP ready. Copyright 1998-2004 Double Precision, Inc.  See COPYING for distribution information.
imap login user@servername pass
imap OK LOGIN Ok.
imap logout
* BYE Courier-IMAP server shutting down
imap OK LOGOUT completed
Connection closed by foreign host.

```

And the logs:
```

Jul 25 12:53:29 localhost imaplogin: Connection, ip=[::ffff:127.0.0.1]
Jul 25 12:53:47 localhost imaplogin: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], command=LOGIN
Jul 25 12:53:47 localhost imaplogin: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], username=user@servername
Jul 25 12:53:47 localhost imaplogin: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], password=pass
Jul 25 12:53:47 localhost imaplogin: authdaemon: starting client module
Jul 25 12:53:47 localhost imaplogin: authdaemon: ACCEPT, username user@servername
Jul 25 12:53:47 localhost imaplogin: LOGIN, user=user@servername, ip=[::ffff:127.0.0.1], protocol=IMAP
Jul 25 12:56:34 localhost imaplogin: LOGOUT, user=user@servername, ip=[::ffff:127.0.0.1], headers=0, body=0, time=167

```

Is someone able to shed some light on this?  The box is in another location, so I'm unable to test it locally with a GUI client like mozilla-thunderbird, etc.  I will try to get near it eventually and test with other clients.  Is mutt the problem?  Or did I break something?

[edit]
World's quickest edit!  The username is "user@servername".  When using mutt and telling it to connect to imap://user:pass@servername, the username is only "user".

Instead, I now tell mutt to connect to "imap://servername".  It prompts me for a username, which I enter as "user@servername" (ie: the complete entry from "id" column from the "users" table) and the correct password, and I am in.

Sometimes you just need to talk out your problem, and the solution becomes clear.

And once again, thanks heaps to Flurdy for the clear and concise guide.  Great software is nothing without people who take the time to explain/howto it.

---

### Post by wwinfrey on 2006-07-26
Great tutorial, thanks for the update for Dapper.

However, I'm wondering, how would I set up server-side mail filtering? I come from a qmail/vpopmail background, where I'm able to use .qmail files to pipe the incoming mail into a Perl script employing Mail::Audit that will sort my mail into different destination folders. Mail::Audit works just fine with Maildir directories so that's not an issue.

TIA

---

### Post by Criocaps on 2006-08-08
Hello,
 
I'have follow the first part of Flurdy tutorial (excluding the security part) and try to make it works (receive, send e-mail...)

I've the following problem : 

I can send e-mail with postfix from server to another adress
I can send e-mail from outside to the server and i see that it comes in because i see it in the queue and the aliases working well too...

But : 
I can connect to the server with a mail client to fetch the mails.
It prompt me for user/password and refuse it.

Any clue ?

Thanks a lot,

Didier.

---

### Post by NeoFax on 2006-08-09
Postfix is not delivering my email to the /var/spool/mail/virtual/user directory.  It is just dropping all of the email to /var/spool/mail/terry mbox file.  Where should I change my main.cf to make it deliver to the maildir folder?

---

### Post by jjtechno on 2006-08-09
Thanks you saved me a bunch of trouble.
regards

---

### Post by NeoFax on 2006-08-10
> **Criocaps said:**
> Hello,
 
I'have follow the first part of Flurdy tutorial (excluding the security part) and try to make it works (receive, send e-mail...)

I've the following problem : 

I can send e-mail with postfix from server to another adress
I can send e-mail from outside to the server and i see that it comes in because i see it in the queue and the aliases working well too...

But : 
I can connect to the server with a mail client to fetch the mails.
It prompt me for user/password and refuse it.

Any clue ?

Thanks a lot,

Didier.

For the username are you using user@domain?  I had problems until I did this.

---

### Post by Criocaps on 2006-08-18
I finally found and correct the problem...

1° Indeed i need to use user@domain as user in pop3 login, thanks Neofax !
2° I found also somes typos

But how can i use the real username in place of user@domain ?

---

### Post by crilen007 on 2006-08-23
I'm getting a Maildir invalud, no 'cur' directory error when trying to check mail

Any ideas on whats causing this or where I can create a cur directory?
Where I can see if one exists?

---

### Post by crilen007 on 2006-08-23
Well I fixed that (Ran makemaildir) and now pop3 and squirrelmail work ok.

However, I can't seem to send messages to the server.

it tells me the mailbox is unavailable.

I checked mysql and the entries are ok for maildir and home and all that.

I did chown to the maildir, and the users folder inside that folder with the virtual:virtual thing.

Any ideas? Do you need to see any file logs?

---

### Post by bonyari on 2006-08-25
How can I integrate procmail and spamassassin per virutal domain/users. I see that there was a procmailrc and spamassassinrc field added to the users table. Any pointer to documentation is appreciated.

Thanks

---

### Post by Kurdt on 2006-08-29
Hi, i made a question here [http://www.ubuntuforums.org/showthread.php?t=245165](http://www.ubuntuforums.org/showthread.php?t=245165) about a problem with foreign bounces and FQDN i am experiencing, maybe someone or **flurdy** can help me and that's why i post it also here.

Thanks!! ;)

---

### Post by elvis on 2006-08-29
> **Criocaps said:**
> I finally found and correct the problem...

1° Indeed i need to use user@domain as user in pop3 login, thanks Neofax !
2° I found also somes typos

But how can i use the real username in place of user@domain ?

Yeah, I had the same problem (see page 3 of this thread - it had the same solution).

To make the usernames not contain the domain name (ie: to make them "user" and not "user@domain"), you need to do the following:

1) In the table "users" the guide specifies that each 'id' feild is "user@domain".  Change this to just "user" and that will be the logon name for your mail client.

2) In the table "aliases" you have a pair of values 'mail' and 'destination'.  Change the 'destination' to match the 'id' field from the "users" table.

So for instance if I had the table "users" with an entry:

**id: elvis@mydomain.com**
name: elvis
uid: 5000
gid: 5000
home: /var/spool/mail/virtual
maildir: elvis/
enabled: 1
change_password: 1
clear: elvispass
etc...

and the table "aliases" with an entry:
pkid: 1
mail: elvis@mydomain.com
**destination: elvis@mydomain.com**

I would change these to:

table users:
**id: elvis**
name: elvis
uid: 5000
gid: 5000
home: /var/spool/mail/virtual
maildir: elvis/
enabled: 1
change_password: 1
clear: elvispass
etc...

table aliases:
pkid: 1
mail: elvis@mydomain.com
**destination: elvis**

Just make sure that for every user account there is an alias pointing to it, or your mail will not be delivered!  You can have aliases pointing to multiple accounts (say for instance a "staff@domain.com" alias that points to all user accounts "elvis,priscilla,lisa" - sort of an easy mailing list setup).  

You can also have multiple aliases for the same account (say alias "elvis@mydomain.com" pointing to account "elvis" as well as alias "elvis@someotherdomain.com" also pointing to the user account "elvis", and a third "thefatguy@mydomain.com" pointing there as well - this way all of those aliases land in the same inbox).

Hope that helps.

---

### Post by Truster on 2006-09-13
Hi.

I have set up an email server as descripted in the howto on Ubuntu server 6.0.6. Everything seems to be work fine, i can login via terminal, but when i try to login with squirrelmail, i always geht the folowing error: at the top: ERROR: Could not complete request.
Query: SELECT "INBOX"
Reason Given: Unable to open this mailbox.

At left side: ERROR: Connection dropped by IMAP server.
Query: SUBSCRIBE "INBOX.Sent"

no more Infos at syslog etc :(

---

### Post by elvis on 2006-09-13
I was wondering if anyone has a good autoreply guide that works with this setup.  I've tried a few, but they constantly fail.  I've made a new transport called "autoreply:", and I've told the system that any messages being sent to "autoreply.mydomain.com" is to be sent by that transport instead of the "virtual:" transport (as specified in the "domains" table).  

But I keep getting errors telling me that the user at that domain is not found, which looks like it's not using the correct transport and instead it's looking for a particular mailbox.

If anyone can offer any advice, I'm all ears.

---

### Post by elvis on 2006-09-14
This is twice in a row now where I've asked a question and answered it myself.  Maybe I should have a bit more patience before I post questions to the forums? :)

The problem was not defining the transport_maps which I've got sorted out now.

Anyways... I've set up autoreply / autoresponder / vactaion email notices (whatever you want to call it).  I did the following:

1) In /etc/postfix/main.cf was the following as per flurdy's guide:
```

# this is how to connect to the domains (all virtual, but the option is there) 
# not used yet 
# transport_maps = mysql:/etc/postfix/mysql_transport.cf

```

I uncommented the last line:
```

# this is how to connect to the domains (all virtual, but the option is there) 
# not used yet 
transport_maps = mysql:/etc/postfix/mysql_transport.cf

```

2) I created a /etc/postfix/mysql_transport.cf file which looked up the "transport" field of the "domains" table:
```

user=database_username
password=database_password
dbname=maildb
table=domains
select_field=transport
where_field=domain
hosts=127.0.0.1
additional_conditions = and enabled = 1

```

3) I added the transport type "autoreply" to /etc/postfix/master.cf:
```

autoreply unix  -       n       n       -       -       pipe
  flags= user=nobody argv=/etc/postfix/autoreply $sender $mailbox

```

4) I created an executable script /etc/postfix/autoreply :
```

mail -s"Fireworks Digital Autoreply From: <$2>"  $1 < /etc/postfix/autoreply_message

```
Make sure you chmod 755 the file to make it executable.

And with it, the text /etc/postfix/autoreply_message to go with it (make this whatever you want).

5) Into the table "domains" I added the row domain="autoreply.mydomain.com" transport="autoreply:" (note the trailing ":" - it is important).

Basically that's it.  Now autoreply is working. To enable a user to be set to autoreply, in the "aliases" table, add the destination "user@autoreply.mydomain.com".  What happens is the mail server looks up the domain "autoreply.mydomain.com", see's the transport is the unix pipe to the script /etc/postfix/autoreply, which in turn fires an email back at the original sender with the message attached!

And with that working, my client can now take holidays.  Wish I could too. :)

---

### Post by cdnwetzel on 2006-09-16
Aside from a few typos I seem to have done alright following the howto, I can send from squirrelmail, but I can't seem to receive mail.  From tail -f /var/log/mail.info, I get the following:


```
Jul 29 17:41:41 cwetzel postfix/qmgr[4859]: 2549D2BDF6: from=<cdnwetzel@comcast.net>, size=1216, nrcpt=1 (queue active)
Jul 29 17:41:41 cwetzel postfix/local[4936]: 2549D2BDF6: to=<chris@cwetzel.com>, relay=local, delay=1, status=sent (delivered to mailbox)
Jul 29 17:41:41 cwetzel postfix/qmgr[4859]: 2549D2BDF6: removed
Jul 29 17:41:42 cwetzel postfix/smtpd[4930]: disconnect from sccrmhc12.comcast.net[204.127.200.82]
```


So it seems to me that the message hits the incoming queue, is sent to my mailbox, but when I view squirrelmail there's no new mail.  I have tried sending from myself to myself, and from comcast.net and my work e-mail, and everytime the same result.  Any ideas what I might have missed?

---

### Post by cdnwetzel on 2006-09-17
> **NeoFax said:**
> Postfix is not delivering my email to the /var/spool/mail/virtual/user directory.  It is just dropping all of the email to /var/spool/mail/terry mbox file.  Where should I change my main.cf to make it deliver to the maildir folder?

NeoFax, did you find an answer to this?  I'm afraid I'm at the same point you got stuck at in this post.  Everything appears to work, except that I never see any e-mail in Squirrelmail and I found all my mail is showing up in the same /var/spool/mail/$USER mbox rather than /var/spool/mail/virtual/$USER  Any help would be great.  Thanks.

---

### Post by Truster on 2006-09-18
Suggestions about TLS/SSL:

When you create the Certificate as descripted in the howto, you can't use Outlook (Express) because you have no valid Certificate installed.

Here is a little Workaround to create Certificates with a self-signed root certificate.

i suggest to create a CA Certificate with the CA.pl script
e.g
```
/usr/lib/ssl/misc/CA.pl -newca
```
hit RETURN

Enter the required information

Example:
```
Making CA certificate ...
Generating a 1024 bit RSA private key
.................................++++++
...............++++++
writing new private key to './demoCA/private/cakey.pem'
Enter PEM pass phrase:
Verifying - Enter PEM pass phrase:
-----
You are about to be asked to enter information that will be incorporated
into your certificate request.
What you are about to enter is what is called a Distinguished Name or a DN.
There are quite a few fields but you can leave some blank
For some fields there will be a default value,
If you enter '.', the field will be left blank.
-----
Country Name (2 letter code) [AU]:AT
State or Province Name (full name) [Some-State]:AUSTRIA
Locality Name (eg, city) []:MYCITY
Organization Name (eg, company) [Internet Widgits Pty Ltd]:Rast + Ruh GmbH
Organizational Unit Name (eg, section) []:
Common Name (eg, YOUR name) []:Mailserver Root Certificate Authority
Email Address []:webmaster@mailserver.abc

Please enter the following 'extra' attributes
to be sent with your certificate request
A challenge password []:
An optional company name []:
Using configuration from /usr/lib/ssl/openssl.cnf
Enter pass phrase for ./demoCA/private/cakey.pem:
Check that the request matches the signature
Signature ok
Certificate Details:
        Serial Number:
            ab:c2:1e:02:cb:e0:eb:71
        Validity
            Not Before: Sep 15 12:16:49 2006 GMT
            Not After : Sep 12 12:16:49 2016 GMT
        Subject:
            countryName               = AT
            stateOrProvinceName       = AUSTRIA
            organizationName          = Rast + Ruh GmbH
            commonName                = Mailserver Root Certificate Authority
            emailAddress              = webmaster@mailserver.abc
        X509v3 extensions:
            X509v3 Basic Constraints: 
                CA:FALSE
            Netscape Comment: 
                OpenSSL Generated Certificate
            X509v3 Subject Key Identifier: 
                DF:33:B9:82:B0:26:3A:99:4C:B9:41:C3:09:45:CA:79:7D:4B:67:85
            X509v3 Authority Key Identifier: 
                keyid:DF:33:B9:82:B0:26:3A:99:4C:B9:41:C3:09:45:CA:79:7D:4B:67:85

Certificate is to be certified until Sep 12 12:16:49 2016 GMT (3650 days)

Write out database with 1 new entries
Data Base Updated

```

You have to remember the choosen phassphrase. you will need it later to sign the certificate

Now let's create the private key with:
```
/usr/lib/ssl/misc/CA.pl -newreq-nodes
```

Fill out the required field as you have it done before.
REMEMBER: The common name (CN) must be the server adress eg sv00.mydomain.at

```
Generating a 1024 bit RSA private key
.................++++++
.........++++++
writing new private key to 'newkey.pem'
-----
You are about to be asked to enter information that will be incorporated
into your certificate request.
What you are about to enter is what is called a Distinguished Name or a DN.
There are quite a few fields but you can leave some blank
For some fields there will be a default value,
If you enter '.', the field will be left blank.
-----
Country Name (2 letter code) [AU]:AT
State or Province Name (full name) [Some-State]:AUSTRIA
Locality Name (eg, city) []:MYCITY
Organization Name (eg, company) [Internet Widgits Pty Ltd]:Rast + Ruh GMBH
Organizational Unit Name (eg, section) []:
Common Name (eg, YOUR name) []:sv00.mydomain.at
Email Address []:

Please enter the following 'extra' attributes
to be sent with your certificate request
A challenge password []:
An optional company name []:
Request is in newreq.pem, private key is in newkey.pem

```

So we have the required certificate to self-sign our one with:
```
/usr/lib/ssl/misc/CA.pl -sign
```

This will self-sign our certificate with our own CA-Certificate

```
Using configuration from /usr/lib/ssl/openssl.cnf
Enter pass phrase for ./ChatfreakCA/private/cakey.pem:
Check that the request matches the signature
Signature ok
Certificate Details:
        Serial Number:
            ab:c2:1e:02:cb:e0:eb:72
        Validity
            Not Before: Sep 15 12:22:25 2006 GMT
            Not After : Sep 12 12:22:25 2016 GMT
        Subject:
            countryName               = AT
            stateOrProvinceName       = AUSTRIA
            localityName              = MYCITY
            organizationName          = Rast + Ruh GMBH
            commonName                = sv00.mydomain.at
        X509v3 extensions:
            X509v3 Basic Constraints: 
                CA:FALSE
            Netscape Comment: 
                OpenSSL Generated Certificate
            X509v3 Subject Key Identifier: 
                22:AA:9C:E1:9E:3C:B3:B4:A4:6C:7C:1E:76:54:D0:20:33:7C:0C:FA
            X509v3 Authority Key Identifier: 
                keyid:12:E2:B5:E0:E2:69:E3:F8:10:1D:82:F5:9D:B7:AE:3B:11:E2:FA:14

Certificate is to be certified until Sep 12 12:22:25 2016 GMT (3650 days)
Sign the certificate? [y/n]:y


1 out of 1 certificate requests certified, commit? [y/n]y
Write out database with 1 new entries
Data Base Updated
Signed certificate is in newcert.pem

```

now type ls and see, wat we have, it should look like this
```
demoCA  newcert.pem  newkey.pem  newreq.pem
```
You can copy newcert.pem and newkey.pem to your /etc/postfix directory and update the main.cf file

To use the certificate with courier, both (key and certificate) file must be in one file. You can do this with:
```
root@test:~# cat newkey.pem >> imapd.pem
root@test:~# cat newcert.pem >> imapd.pem
```

and copy the new file to /etc/courier/

now cd to demoCA

you'll find a file named cacert.pem

you can use this file to import it in Internet Explorer/Outlook/Entourage/

This will result in no nag of wrong root Certificate :)

Hint: you can edit the /usr/lib/ssl/misc/CA.pl and /usr/lib/ssl/openssl.cnf to adjust paths, date, and other settings

---

### Post by Truster on 2006-09-18
> **cdnwetzel said:**
> Aside from a few typos I seem to have done alright following the howto, I can send from squirrelmail, but I can't seem to receive mail.  From tail -f /var/log/mail.info, I get the following:


```
Jul 29 17:41:41 cwetzel postfix/qmgr[4859]: 2549D2BDF6: from=<cdnwetzel@comcast.net>, size=1216, nrcpt=1 (queue active)
Jul 29 17:41:41 cwetzel postfix/local[4936]: 2549D2BDF6: to=<chris@cwetzel.com>, relay=local, delay=1, status=sent (delivered to mailbox)
Jul 29 17:41:41 cwetzel postfix/qmgr[4859]: 2549D2BDF6: removed
Jul 29 17:41:42 cwetzel postfix/smtpd[4930]: disconnect from sccrmhc12.comcast.net[204.127.200.82]
```


So it seems to me that the message hits the incoming queue, is sent to my mailbox, but when I view squirrelmail there's no new mail.  I have tried sending from myself to myself, and from comcast.net and my work e-mail, and everytime the same result.  Any ideas what I might have missed?

as i can see, your reley is local. on my server it's virtual and dropped into the correct folder:

Sep 18 10:04:43 sv00 postfix/smtp[31797]: 723598BC47: to=<webmaster@example.at>, relay=127.0.0.1[127.0.0.1], delay=2, status=sent (250 2.6.0 Ok, id=31336-01, from MTA([127.0.0.1]:10025): 250 Ok: queued as CCBF48BC52)
Sep 18 10:04:43 sv00 postfix/qmgr[31787]: 723598BC47: removed
Sep 18 10:04:43 sv00 postfix/virtual[31803]: CCBF48BC52: to=<truster@example.at>, orig_to=<webmaster@example.at>, relay=virtual, delay=0, status=sent (delivered to maildir)

mabybe some configuration errors in: main.cf master.cf mysql_*.cf ?

---

### Post by Truster on 2006-09-18
/delete

---

### Post by cdnwetzel on 2006-09-18
```
Sep 18 23:27:26 cwetzel postfix/smtpd[10454]: connect from localhost[127.0.0.1]
Sep 18 23:27:26 cwetzel postfix/smtpd[10454]: 5C6342BF1D: client=localhost[127.0.0.1]
Sep 18 23:27:26 cwetzel postfix/cleanup[10456]: 5C6342BF1D: message-id=<1579.68.44.63.212.1158633922.squirrel@webmail.cwetzel.com>
Sep 18 23:27:26 cwetzel postfix/qmgr[10444]: 5C6342BF1D: from=<chris@cwetzel.com>, size=1144, nrcpt=1 (queue active)
Sep 18 23:27:26 cwetzel amavis[10318]: (10318-02) FWD via SMTP: <chris@cwetzel.com> -> <chris@cwetzel.com>, BODY=8BITMIME, 250 2.6.0 Ok, id=10318-02, from MTA([127.0.0.1]:10025): 250 Ok: queued as 5C6342BF1D
Sep 18 23:27:26 cwetzel amavis[10318]: (10318-02) Passed CLEAN, LOCAL [127.0.0.1] [68.44.63.212] <chris@cwetzel.com> -> <chris@cwetzel.com>, Message-ID: <1579.68.44.63.212.1158633922.squirrel@webmail.cwetzel.com>, mail_id: 6COCScsQNwwQ, Hits: -0.89, 2469 ms
Sep 18 23:27:26 cwetzel amavis[10318]: (10318-02) TIMING [total 2484 ms] - SMTP EHLO: 9 (0%)0, SMTP pre-MAIL: 4 (0%)1, mkdir tempdir: 1 (0%)1, create email.txt: 1 (0%)1, SMTP pre-DATA-flush: 7 (0%)1, SMTP DATA: 29 (1%)2, body_digest: 3 (0%)2, gen_mail_id: 1 (0%)2, mkdir parts: 2 (0%)2, mime_decode: 26 (1%)3, get-file-type1: 56 (2%)6, decompose_part: 21 (1%)6, parts_decode: 0 (0%)6, AV-scan-1: 1023 (41%)48, AV-scan-2: 1 (0%)48, spam-wb-list: 8 (0%)48, SA msg read: 2 (0%)48, SA parse: 8 (0%)48, SA check: 870 (35%)83, update_cache: 4 (0%)84, fwd-connect: 112 (5%)88, fwd-mail-from: 6 (0%)88, fwd-rcpt-to: 174 (7%)95, write-header: 5 (0%)96, fwd-data: 2 (0%)96, fwd-data-end: 53 (2%)98, fwd-rundown: 4 (0%)98, main_log_entry: 41 (2%)100, update_snmp: 5 (0%)100, unlink-1-files: 3 (0%)100, rundown: 1 (0%)100
Sep 18 23:27:26 cwetzel postfix/smtpd[10454]: disconnect from localhost[127.0.0.1]
Sep 18 23:27:26 cwetzel postfix/smtp[10450]: 8CCFE2BEA2: to=<chris@cwetzel.com>, relay=127.0.0.1[127.0.0.1], delay=2524, status=sent (250 2.6.0 Ok, id=10318-02, from MTA([127.0.0.1]:10025): 250 Ok: queued as 5C6342BF1D)
Sep 18 23:27:26 cwetzel postfix/qmgr[10444]: 8CCFE2BEA2: removed
Sep 18 23:27:26 cwetzel postfix/local[10449]: 5C6342BF1D: to=<chris@cwetzel.com>, relay=local, delay=0, status=sent (delivered to mailbox)
Sep 18 23:27:26 cwetzel postfix/qmgr[10444]: 5C6342BF1D: removed

```

Well, I went over those files... admittedly, I cound't find the issue, however, if you reference my newest post from my mail.info, it seems going over my master.cf/main.cf has accidently fixed something in terms of my content filtering, which now appears in the log entry. ](*,)  Attached are my master.cf, main.cf, mysql_mailbox.cf, and mail.info for anyone who can help review and see if there are typos.  If you need anything else, please ask.  Thanks for all the help! :D

---

### Post by Truster on 2006-09-19
@cdnwetzel: Read your Logs

It semms that your ClamAV Scanner is broken
> Sep 18 23:27:24 cwetzel amavis[10318]: (10318-02) ClamAV-clamd: Can't send to socket /var/run/clamav/clamd.ctl: Transport endpoint is not connected, retrying (1)

and it always says Transprot: local

Make sure, that postfix can access the mysql DB

tail -f the mysql log and send a mail to your account and see what's happen

and...... . holy shit, you have a fatal error in your master.cf

Example of your file:
smtp      inet  n       -       -       -       -       smtpd
        -o cleanup_service_name=pre-cleanup
You have two separated lines
-o blahblah is a new line in your config but it must belong to the line above
that means, you have to tab or space to the second line, DO NOT HIT ENTER

fix this issue in all lines, and try it again

Good Luck ;)

---

### Post by cdnwetzel on 2006-09-19
I'm going to continue going over those files and check spaces and tabs, I found loads of lines spaced in 5-6 times rather than tabbed, I'm attaching my mysql.log in case that might show something useful, it all seemed normal to me, no errors that is...

---

### Post by cdnwetzel on 2006-09-19
Thank you for all your help, I found the more I reviewed those files the more I found slight typos.  I had my mysql_domains.cf duplicating my aliases, rather than querying the right tables and fields.  I then found once I fixed that, I had put my domain name in mydestination also (hence the local relay), once I removed that line, everything works!  Mail now goes to my maildir, rather than an mbox!  Thanks for pushing me the right direction (the one that pointed the finger back at me, LOL).  :D

---

### Post by achra on 2006-09-24
Much thanks for this great howto.. I've learned a lot troubleshooting it, and I've finally got a working mailserver.

However, I can't send mail from outside my home network. If I'm outside the trusted network and attempt to send via my smtp server, I get greylisted.. Any ideas on how to do this? I understand why it's happening, but is there a way to not greylist a foreign host if I am logging in with a valid mail login?

Thanks,
 -Achra

---

### Post by artioli1984 on 2006-09-26
Hi all, i'm new to postfix, i try to install it with this tutorial, now it running, but when i test system it can't send messages
](*,) 
my telnet:

root@ubuntu:/home/davide# telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 ubuntu.d-one.info ESMTP Postfix (Ubuntu)
EHLO ubuntu
250-ubuntu.d-one.info
250-PIPELINING
250-SIZE 10240000
250-ETRN
250-STARTTLS
250 8BITMIME
MAIL FROM: <gianmarco.artioli@poste.it>
250 Ok
RCPT TO: <xandros@lala.com>
Connection closed by foreign host.

I force stop postfix because it loops on recipient.

root@ubuntu:/home/davide# tail -f /var/log/mail.log

root@ubuntu:/home/davide# tail -f /var/log/mail.log
Sep 26 09:49:01 ubuntu postfix/master[7504]: daemon started -- version 2.2.10, c onfiguration /etc/postfix
Sep 26 09:49:05 ubuntu postfix/smtpd[7509]: connect from localhost[127.0.0.1]
Sep 26 09:50:04 ubuntu postfix/smtpd[7509]: warning: connect #1 to subsystem public/cleanup: Connection refused
Sep 26 09:50:14 ubuntu postfix/smtpd[7509]: warning: connect #2 to subsystem public/cleanup: Connection refused
Sep 26 09:50:24 ubuntu postfix/smtpd[7509]: warning: connect #3 to subsystem public/cleanup: Connection refused
Sep 26 09:50:34 ubuntu postfix/smtpd[7509]: warning: connect #4 to subsystem public/cleanup: Connection refused
Sep 26 09:50:44 ubuntu postfix/smtpd[7509]: warning: connect #5 to subsystem public/cleanup: Connection refused
Sep 26 09:50:54 ubuntu postfix/smtpd[7509]: warning: connect #6 to subsystem public/cleanup: Connection refused
Sep 26 09:51:04 ubuntu postfix/smtpd[7509]: warning: connect #7 to subsystem public/cleanup: Connection refused
Sep 26 09:51:14 ubuntu postfix/smtpd[7509]: warning: connect #8 to subsystem public/cleanup: Connection refused
Sep 26 09:51:24 ubuntu postfix/smtpd[7509]: warning: connect #9 to subsystem public/cleanup: Connection refused

#######################################################ÀÀ



root@ubuntu:/etc/postfix# netstat -tap
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost:60000         *:*                     LISTEN     4141/postgrey.pid -
tcp        0      0 localhost:mysql         *:*                     LISTEN     7204/mysqld
tcp        0      0 *:10000                 *:*                     LISTEN     6017/perl
tcp        0      0 *:smtp                  *:*                     LISTEN     8923/master
tcp        0      0 192.168.0.170:36019     72.14.217.99:www        ESTABLISHED4962/firefox-bin
tcp6       0      0 *:imaps                 *:*                     LISTEN     4292/couriertcpd
tcp6       0      0 *:www                   *:*                     LISTEN     4756/apache2
tcp6       0      0 *:ssh                   *:*                     LISTEN     4656/sshd




############################################À

tail -f /var/log/mysql/mysql.log


060926 10:38:31      48 Connect     mail@localhost on maildb
                     48 Query       SELECT destination FROM aliases WHERE mail='poste.it' and enabled = 1
                     49 Connect     mail@localhost on maildb
                     49 Query       SELECT domain FROM domains WHERE domain='poste.it' and enabled = 1
060926 10:39:00      48 Query       SELECT destination FROM aliases WHERE mail='lala.com' and enabled = 1
                     49 Query       SELECT domain FROM domains WHERE domain='lala.com' and enabled = 1
060926 10:39:01      50 Connect     mail@localhost on maildb
                     50 Query       SELECT destination FROM aliases WHERE mail='xandros@lala.com' and enabled = 1
                     50 Query       SELECT destination FROM aliases WHERE mail='@lala.com' and enabled = 1
060926 10:40:00      49 Quit
                     48 Quit


########################################à


i think /etc/hosts.allow can create problems, so i write ALL : ALL, but not changed.


what can i do? plese help me!!!

---

### Post by pht3k on 2006-09-26
hi,

i installed postfix according to the howto and it works!  Thanks for this.  But i had to make some adjustments ....

1. amavis was not starting.  i found it was due to the missing operator in the mydomain line :
[INDENT]$mydomain 'yourdomain.com';[/INDENT]
[INDENT]should be[/INDENT]
[INDENT]$mydomain ='yourdomain.com';[/INDENT]

2. a permission error given me some troubles. To fix it:
[INDENT]cd /var/lib/amavis[/INDENT]
[INDENT]chown virtual:virtual db[/INDENT]

3. those packages should be in the neeeded packages list :
[INDENT]courier-pop courier-pop-ssl[/INDENT]

Otherwise, info is very precise.  But some like some other users said : it's maybe not a howto for newbie.

cya,
pht3k

---

### Post by oziemike on 2006-09-28
Hi guys, 

I would appreciate a litte help. Firtsly I have put a system together exactly as per Flurdy's HOWTO. Thanks you for all your time and effort. Something has gone wrong, probably my fault, but need a little guidance as to what I should look for.

The system is working fine and I have about 5 users. The problem has now come about when I try to add new users. I enter them into the database via phpmyadmin and it enters them OK. All looks fine with the entry.

But it doesn't go and create the mailboxes in /var/spool/mail/virtual

If I try and log in via Squirrelmail or use a pop client to a new user, it rejects it. Squirrelmail reports that the Imap has dropped the connection. Interestingly if I try a dud (non-existent) user, it reports doesn't know the user. So it seems it knows about my new user, but can't authenticate it, then drops it.

The mail log reports that there was no such dircetory for that person (as previously explained).

Couple of quetsions. At what stage does the system create the new mailbox??  Is it right at the time you create the entry in MySQL, or the first time somebody logs in??

Please let me know if you need any log outputs or to see any of the config files etc.

Hope someone can help. Thanks in advance. Mike.

---

### Post by pht3k on 2006-09-28
oziemike: the user need to receive mail before the dir get created.  so send him mail and check again.

---

### Post by oziemike on 2006-09-28
Thank you so much for that. I have been tearing my hair out for two days now trying to work out why the new accounts would not work and the answer was as simple as that.

Just got to get amavis and the aliases working now and it is all complete.

Thank you again for putting me out of my misery.

Mike

---

### Post by pht3k on 2006-09-28
hehe, me too I have been tearing my hair out for a couple of days before i found the answer!

---

### Post by oziemike on 2006-09-29
Amavis is going now too, just the same permissions you found.

Would you know if you can put multiple recipients into the alias list in the database or is it one only per alias?? I did try but only the fist recipent got the mail.

Mike

---

### Post by listerthrawn on 2006-10-09
Guide is great but I'm having problems.

I've got postfix receiving ok but can't get courier to access.  I keep getting a NO Login failed. when I try to log in.  I've checked the mysql log and it doesn't change at all when i try to do this.  It's not looking up the address.  I'll post my authmysqlrc file. (passwords changed)

Any ideas?  Anyone?

MYSQL_SERVER    localhost
MYSQL_USERNAME  mail
MYSQL_PASSWORD  apassword
MYSQL_PORT      0
MYSQL_OPT       0
MYSQL_DATABASE  maildb
MYSQL_USER_TABLE        users
MYSQL_CLEAR_PWFIELD     clear
MYSQL_UID_FIELD         uid
MYSQL_GID_FIELD         gid
MYSQL_LOGIN_FIELD       id
MYSQL_HOME_FIELD        home
MYSQL_NAME_FIELD        name
MYSQL_MAILDIR_FIELD     concat(home,'/',maildir)
MYSQL_WHERE_CLAUSE      enabled=1

---

### Post by badmojo on 2006-10-12
Has anyone setup the squirrelmail plugin "courrier_vacation" with this?
I have a system built around this guide and I am quite happy with it, but I would realy like to make this plugin work. Any help or advice is greatly appreciated!

---

### Post by xtek on 2006-10-15
I'm having a little problem with getting the server to work.  I think I have everything right but for some reason avamis will not work. I get this error in /var/log/mail.log.

```
Oct 15 00:16:59 localhost postfix/qmgr[14286]: warning: connect to transport amavis: No such file or directory
```

Any ideas?

Also has anyone tried to get fetchmail working with this setup? (It would be usefull to be able to pull emails from multiple accounts)

---

### Post by ngms27 on 2006-10-15
I've got most of this going but amavis wount start. I get 

Starting amavisd: /etc/init.d/amavis: line 64: /var/run/amavis: No such file or directory

I have tried creating a file and a directory and setting ownership to virtual:virtual but nothing works.

Could someone please post a working 50-user file for amavis etc?

Thanks

JonnyT

---

### Post by ngms27 on 2006-10-15
A copy of /var/run/amavis would also help!

---

### Post by shakyamuni on 2006-10-16
Dear friends,

Once created the account, I 'm not able to login via squirrelmail, giving an error : "ERROR Unknown user or password incorrect", so, since it's not working for squirrelmail, it won't work either for any email client.

Does anyone knows about this? is it an error in the email creation procedure ¨?

regards,

Carlos.

---

### Post by ngms27 on 2006-10-17
Try using [email]username@mydomain.org[/email]

Works for me

---

### Post by shakyamuni on 2006-10-17
It should work if you have that domain.... I don't have it so I still have the same issue.... thanks anyway ....does anyone knows any other possible solution?


thanks,in advance..

regards,
Carlos.

---

### Post by ngms27 on 2006-10-17
What is your domain?
What is your user id?

---

### Post by jmc1664 on 2006-10-17
I wondered if anyone could point me in the right direction. I have just carried out the install procedure while taking notes etc, and everything went nicely. Courier is allowing me to log in etc, but Postfix freezes every time I enter the "MAIL FROM: " telnet command. Looking at the mail.log, the relevant error would seem to be:

ubuntu postfix/trivial-rewrite[5697]: warning: connect to mysql server localhost: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

I have checked for obvious things like spacing, typos etc, but nothing so far. The only decisions I have taken outside following flurdy's guide are choosing "Internet Site" when installing postfix and choosing the "Create Directories" option when installing courier.

The only other thing to report is that the etc/postfix/main.cf file seemed to be missing a lot of the entries specified in the guide.

Any working solutions will be gratefully received and rewarded with cash prizes!

Thanks,

John

---

### Post by jmc1664 on 2006-10-17
> **jmc1664 said:**
> I wondered if anyone could point me in the right direction. I have just carried out the install procedure while taking notes etc, and everything went nicely. Courier is allowing me to log in etc, but Postfix freezes every time I enter the "MAIL FROM: " telnet command. Looking at the mail.log, the relevant error would seem to be:

ubuntu postfix/trivial-rewrite[5697]: warning: connect to mysql server localhost: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

I have checked for obvious things like spacing, typos etc, but nothing so far. The only decisions I have taken outside following flurdy's guide are choosing "Internet Site" when installing postfix and choosing the "Create Directories" option when installing courier.

The only other thing to report is that the etc/postfix/main.cf file seemed to be missing a lot of the entries specified in the guide.

Any working solutions will be gratefully received and rewarded with cash prizes!

Thanks,

John


The reason for the above error was that /etc/postfix/mysql_alias.cf was missing a line break. This resulted in completely breaking the mysql connection.

I'll post back once it either totally works or I break it again!

---

### Post by ngms27 on 2006-10-18
Right got this working and the AV and Spam filtering is working great but...

Where does amavis / spamassassin put my spam?

Thanks

JonnyT

---

### Post by shakyamuni on 2006-10-18
> **ngms27 said:**
> What is your domain?
What is your user id?

username:ccubillos
domain: stitchkin.cl


as far as I know... i already added domains and the account... but it's not working. The only piece I didn't set was the .htaccess file for the squirrelmail but I don't think that's problem...

any suggestions?

---

### Post by shakyamuni on 2006-10-18
> **shakyamuni said:**
> username:ccubillos
domain: stitchkin.cl


as far as I know... i already added domains and the account... but it's not working. The only piece I didn't set was the .htaccess file for the squirrelmail but I don't think that's problem...

any suggestions?

This is an additional post...
I have the same issue using root account

login : root@localhost
password: xxxxx

squirrelmail sent me an error message with username/password invalid.
...
Additionally, I've included a portion of the mail.err log file :
Oct 18 18:57:31 garuda amavis[3542]: TROUBLE in pre_loop_hook: db_home directory is not writable: /var/lib/amavis/db at /usr$
Oct 18 19:41:13 garuda imaplogin: LOGIN FAILED, ip=[::ffff:127.0.0.1]
seems like db folder has no rights to write.... 

any ideas?

thanks a lot in advance.

carlos.

---

### Post by giorg on 2006-10-19
Guys I get this warning in my mail.log:

Oct 19 10:38:10 mail amavis[1432]: (01432-01) WARN: DSPAM problem, exit 64, result=[1553] warn: Unknown option: s\n

but actually the anti-span is working... any idea?
Thx a lot
Andrea

---

### Post by giorg on 2006-10-19
By the way, any chance to avoid amavis running for localnetworks? This would save performances... And the last problem I have is to give **virus** whitelist to amavis; seems to be possible only for spam.
Thx

---

### Post by shakyamuni on 2006-10-19
Dear friends,

I've found another error connecting myself via telnet doing " sudo telnet -d 127.0.0.1 25"
I write a message as follows:
"mail from: <username@domain>
503 Error: send HELO/EHLO first" --> this is the issue ...
any ideas?
i'm running out of ideas...

thanks

Carlos.

---

### Post by sputicus on 2006-10-24
> **jmc1664 said:**
> I wondered if anyone could point me in the right direction. I have just carried out the install procedure while taking notes etc, and everything went nicely. Courier is allowing me to log in etc, but Postfix freezes every time I enter the "MAIL FROM: " telnet command. Looking at the mail.log, the relevant error would seem to be:

ubuntu postfix/trivial-rewrite[5697]: warning: connect to mysql server localhost: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)


I just solved this problem myself, it has to do with the unix socket not being available in the chrooted postfix environment. If you set your "hosts = 127.0.0.1" postfix will use TCP rather than the unix socket to communicate with mysql.

I also posted about this in the following thread:

[http://www.ubuntuforums.org/showthread.php?p=1656729#post1656729](http://www.ubuntuforums.org/showthread.php?p=1656729#post1656729)

---

### Post by willg on 2006-10-25
I was able to get most everything running after several attempts. However, two problems still remain

1. I have seen this post twice, but not seen a solution. Basically, mail is getting delivered to /var/spool/mail/virtual/willg/ but is not showing up in Squirrelmail (when it was working)..which brings me to my next problem

2. After following the Squirrelmail section about adding mysql://username:password@127.0.0.1/database in the  DSN for Address Book section and DSN for Preferences section I now get the following error when I try to login to Squirrelmail


Warning: main(DB.php): failed to open stream: No such file or directory in /usr/share/squirrelmail/functions/db_prefs.php on line 40

Warning: main(): Failed opening 'DB.php' for inclusion (include_path='.:/usr/share/pear') in /usr/share/squirrelmail/functions/db_prefs.php on line 40
ERROR:
Could not include PEAR database functions required for the database backend.
Is PEAR installed, and is the include path set correctly to find DB.php?
Please contact your system administrator and report this error.


Any help would be greatly appreciated. Thanks!

---

### Post by shakyamuni on 2006-10-25
> **willg said:**
> I was able to get most everything running after several attempts. However, two problems still remain

1. I have seen this post twice, but not seen a solution. Basically, mail is getting delivered to /var/spool/mail/virtual/willg/ but is not showing up in Squirrelmail (when it was working)..which brings me to my next problem

2. After following the Squirrelmail section about adding mysql://username:password@127.0.0.1/database in the  DSN for Address Book section and DSN for Preferences section I now get the following error when I try to login to Squirrelmail


Warning: main(DB.php): failed to open stream: No such file or directory in /usr/share/squirrelmail/functions/db_prefs.php on line 40

Warning: main(): Failed opening 'DB.php' for inclusion (include_path='.:/usr/share/pear') in /usr/share/squirrelmail/functions/db_prefs.php on line 40
ERROR:
Could not include PEAR database functions required for the database backend.
Is PEAR installed, and is the include path set correctly to find DB.php?
Please contact your system administrator and report this error.


Any help would be greatly appreciated. Thanks!


Is not so clear in the howto manual, but ...have you tried to replace username:password for your squirrel username and password created in mysql?

regards,
Carlos.

---

### Post by extasy on 2006-10-27
Nice and easy howto! just what I needed, but does this howto work for edgy to or is it changes? I also wondered if this install can handle multiple domains?

---

### Post by rofl0r on 2006-11-03
thanks for the great tutorial. it also works on debian 3.1 with some little differences (i.e. amavis uses one single config file instead of 50-user and so on) =D>

---

### Post by dninja on 2006-11-17
> **bonyari said:**
> How can I integrate procmail and spamassassin per virutal domain/users. I see that there was a procmailrc and spamassassinrc field added to the users table. Any pointer to documentation is appreciated.

Thanks

Hi
Has anyone got an answer to this? I initially put the procmailrc file in my users home directory but then realised that the mail account is a virtual one so that wouldn't help. The field in the database doesn't seem to be used for anything, no sql is pulling the info out.

Help, I'm missing my filtering.

---

### Post by lawkie on 2006-11-22
Hello,

I have come to the point that I have installed the mail server on Ubuntu (I am a complete novice, so I just followed the guide), now I want to start adding users to my domain. To do this with mysql queries each time is very tiresome. I heard there are ways to use web-based programs.

Can someone please tell me what a good program is and more inportant, how do I link it to the database used in this tutorial? How do I set up such a program to be able to talk to mysql and update my users table!? Anyone who has done this?

Help is very much appreciated!

Thanks,

Rens

---

### Post by gregd on 2006-11-24
I had exactly the same problem with "SASL authentication failure: no secret in database" error. It would be great if the guide had a warning about **trailing whitespace problem** inside sasl conf file. Thanks tbird469 for the solution.

---

### Post by hecchan on 2006-11-29
Hi forum,

First my public thanks to ***flurdy*** for this great [howto]("http://flurdy.com/docs/postfix/"), (and to all the people who wrote this free software we are using)

This is my first post, the mail server seems to work now, not too much testing yet. But i can connect from a client machine in my LAN with evolution and send emails to the internet and receive from my Netscape webmail. Also squirrelmail and phpmyadmin seems OK.
I didn't follow blindly the howto, i readed the docs for the most important programs. But unfortunately, i didn't find the link to this forum until i got it working. Shame on me, the most of the answers were here. Just read the posts.
I just will put together a few problems i found. 
My SO is Ubuntu dapper and i have did exactly as ***flurdy*** said except for the php, i have installed php5 and i didn't install the shorewall as my router includes one.

_**Postfix:**_
If your ISP relay host needs authentication, you have to set up the [COLOR="DarkGreen"]sasl_passwd(.db)[/COLOR] file
I changed 
```
mynetworks_style = host 
```
to 
```
mynetworks_style = subnet
```
 as i want my mail server accepts mail sent from inside the LAN

_**Amavis:**_
I mixed flurdy's with [wiki'sPostfixAmavisNew]("https://wiki.ubuntu.com/PostfixAmavisNew")
I had to set owner for /var/lib/amavis/db 
so i think change
-------------------------
# You may have to change this 
```
cd /var/lib/amavis 
mkdir tmp 
chown virtual:virtual tmp 
chown virtual:virtual virusmails
```
------------------------ by
```
chown -R virtual:virtual /var/lib/amavis/*
```
----------------------

**_Authentication:_**
******************** VERY IMPORTANT ****************************
**************** CHECK TRAILING SPACES IN /etc/postfix/sasl/smtpd.conf
****************************************************************
It drove me crazy, i was able to authenticate from squirrelmail but from evolution or kmail i
got an authentication error which gives little information in the logs

**_Encryption:_**
Evolution still doesn't like the certs i have created following forum user: trusted instructions

**_SquirrelMail:_**
I have installed php5, so i had to change [COLOR="DarkRed"]php4-pear[/COLOR] by [COLOR="DarkGreen"]php-pear[/COLOR] and [COLOR="DarkGreen"]php-db[/COLOR]
I did a symlink to /etc/squirrelmail/apache.conf to keep the squirrelmail config together
ATTENTION:-after you create a mail account with mysql or phpmyadmin 
YOU MUST SEND AN EMAIL TO THE NEW ACCOUNT for the directory to be created under 
/var/spool/mail/virtual/

**_phpMyAdmin:_**
Here i found the darkest point of this howto.
I'm a newbee to all this stuff, so please, this is a call to someone with a deeper knowledge on this subject to review what i will say, because it seems to me it can be an important security hole for the the people who follow the phpmyadmin instructions.
After read the docs for phpmyadmin in dapper about [COLOR="Blue"]/etc/phpmyadmin/config.inc.php[/COLOR]:
[PHP]$cfg['PmaAbsoluteUri']	[/PHP]
docs suggets to leave it blank (it's working for me like that)
[PHP]$cfg['Servers'][$i]['user'] = 'mail'; 
$cfg['Servers'][$i]['password'] = 'apassword';[/PHP]
******************** VERY IMPORTANT ****************************
**************** NEVER PUT USER AND PASSWORD IN /etc/phpmyadmin/config.inc.php
****************************************************************
this file can be readed for any person who can run cgi scripts on the server
In the docs there is a solution creating an user with low privileges
[PHP]$cfg['Servers'][$i]['controluser']   = 'pma';
$cfg['Servers'][$i]['controlpass']   = 'apasswordforpmauser';[/PHP] 
there is a sql script to create other usefull tables for mysql
********************** READ THE PHPMYADMIN DOCUMENTATION ********************************

Sorry for using so much upper case.

I belive this a really great howto. It leaded me to get an email server working, and that it's a lot of stuff.

A newbee lazy sugestion:
To make copy and paste the code easier, fix the line returns for Linux

All the best

---

### Post by akosh on 2006-12-10
First of all, thank you for the great howto!

I've configured a server using it and it works well, but I have a warning that I can not really fix.

The MX was set to my IP address two days ago, it pointed to the server of my ISP before. A backup MX is still pointig there.

Please if you know of any possible solution, I would very much appreciate.

It is some kind of loopback problem:


Dec 10 12:18:02 mail postfix/pickup[1235]: 9C13339831A: uid=105 from=<amavis>
Dec 10 12:18:02 mail postfix/cleanup[1367]: 9C13339831A: message-id=<20061210111802.9C13339831A@mail.xxxx.hu>
Dec 10 12:18:02 mail postfix/qmgr[27797]: 9C13339831A: from=<amavis@mail.xxxx.hu>, size=707, nrcpt=1 (queue active)
Dec 10 12:18:02 mail amavis[32272]:) ESMTP::10024 /var/lib/amavis/tmp/amavis-20061210T031802-32272: <amavis@mail.xxxx.hu> -> <amavis@mail.xxxx.hu> Received: SIZE=707 from mail.xxxx.hu ([127.0.0.1]) by localhost (mail.xxxx.hu [127.0.0.1]) (amavisd-new, port 10024) with ESMTP id for <amavis@mail.xxxx.hu>; Sun, 10 Dec:18:02 +0100 (CET)
Dec 10 12:18:02 mail amavis[32272]:) Checking: 2p5kb2-H+LM4 <amavis@mail.xxxx.hu> -> <amavis@mail.xxxx.hu>
Dec 10 12:18:02 mail amavis[32272]:) p001 1 Content-Type: text/plain, size: 172 B, name: 
Dec 10 12:18:02 mail postfix/smtpd[1373]: connect from localhost[127.0.0.1]
Dec 10 12:18:02 mail postfix/smtpd[1373]: EB6923982DC: client=localhost[127.0.0.1]
Dec 10 12:18:03 mail postfix/cleanup[1367]: EB6923982DC: message-id=<20061210111802.9C13339831A@mail.xxxx.hu>
Dec 10 12:18:03 mail postfix/qmgr[27797]: EB6923982DC: from=<amavis@mail.xxxx.hu>, size=1134, nrcpt=1 (queue active)
Dec 10 12:18:03 mail amavis[32272]:) FWD via SMTP: <amavis@mail.xxxx.hu> -> <amavis@mail.xxxx.hu>, 250 2.6.0 Ok, id=32272-08, from MTA([127.0.0.1]:10025): 250 Ok: queued as EB6923982DC
Dec 10 12:18:03 mail amavis[32272]:) Passed CLEAN, <amavis@mail.xxxx.hu> -> <amavis@mail.xxxx.hu>, Message-ID: <20061210111802.9C13339831A@mail.xxxx.hu>, mail_id: 2p5kb2-H+LM4, Hits: -0.001, 349 ms
Dec 10 12:18:03 mail amavis[32272]:) TIMING [total 353 ms] - SMTP EHLO: 3 (1%)1, SMTP pre-MAIL: 1 (0%)1, SMTP pre-DATA-flush: 2 (1%)2, SMTP DATA: 42 (12%)13, body_digest: 1 (0%)14, gen_mail_id: 0 (0%)14, mime_decode: 7 (2%)16, get-file-type1: 12 (3%)19, decompose_part: 1 (0%)19, parts_decode: 0 (0%)19, AV-scan-1: 4 (1%)21, spam-wb-list: 2 (1%)21, SA msg read: 0 (0%)21, SA parse: 1 (0%)22, SA check: 149 (42%)64, update_cache: 1 (0%)64, fwd-connect: 34 (10%)74, fwd-mail-from: 5 (2%)75, fwd-rcpt-to: 5 (2%)77, write-header: 1 (0%)77, fwd-data: 0 (0%)77, fwd-data-end: 67 (19%)96, fwd-rundown: 1 (0%)97, main_log_entry: 9 (3%)99, update_snmp: 1 (0%)100, unlink-1-files: 1 (0%)100, rundown: 0 (0%)100
Dec 10 12:18:03 mail amavis[32272]:) extra modules loaded: unicore/lib/gc_sc/Digit.pl, unicore/lib/gc_sc/SpacePer.pl
Dec 10 12:18:03 mail postfix/smtp[1370]: 9C13339831A: to=<amavis@mail.xxxx.hu>, orig_to=<amavis>, relay=127.0.0.1[127.0.0.1], delay=1, status=sent (250 2.6.0 Ok, id=32272-08, from MTA([127.0.0.1]:10025): 250 Ok: queued as EB6923982DC)
Dec 10 12:18:03 mail postfix/smtpd[1373]: disconnect from localhost[127.0.0.1]
Dec 10 12:18:03 mail postfix/qmgr[27797]: 9C13339831A: removed
Dec 10 12:18:03 mail postfix/smtpd[1378]: connect from host-xxx-xx.opticon.hu[85.90.xxx.xx]
Dec 10 12:18:03 mail postfix/smtp[1377]: warning: host mail.xxxx.hu[85.90.xxx.xx] greeted me with my own hostname mail.xxxx.hu
Dec 10 12:18:03 mail postfix/smtp[1377]: warning: host mail.xxxx.hu[85.90.xxx.xx] replied to HELO/EHLO with my own hostname mail.xxxx.hu
Dec 10 12:18:03 mail postfix/smtp[1377]: EB6923982DC: to=<amavis@mail.xxxx.hu>, relay=mail.xxxx.hu[85.90.xxx.xx], delay=1, status=bounced (mail for mail.xxxx.hu loops back to myself)
Dec 10 12:18:03 mail postfix/smtpd[1378]: disconnect from host-xxx-xx.opticon.hu[85.90.xxx.xx]
Dec 10 12:18:03 mail postfix/cleanup[1367]: 2371039831F: message-id=<20061210111803.2371039831F@mail.xxxx.hu>
Dec 10 12:18:03 mail postfix/qmgr[27797]: 2371039831F: from=<>, size=2775, nrcpt=1 (queue active)
Dec 10 12:18:03 mail postfix/qmgr[27797]: EB6923982DC: removed
Dec 10 12:18:03 mail postfix/smtpd[1378]: connect from host-xxx-xx.opticon.hu[85.90.xxx.xx]
Dec 10 12:18:03 mail postfix/smtp[1377]: warning: host mail.xxxx.hu[85.90.xxx.xx] _greeted me with my own hostname_ mail.xxxx.hu
Dec 10 12:18:03 mail postfix/smtp[1377]: warning: host mail.xxxx.hu[85.90.xxx.xx] replied to HELO/EHLO with my own hostname mail.xxxx.hu
Dec 10 12:18:03 mail postfix/smtp[1377]: 2371039831F: to=<amavis@mail.xxxx.hu>, relay=mail.xxxx.hu[85.90.xxx.xx], delay=0, status=bounced (mail for mail.xxxx.hu loops back to myself)
Dec 10 12:18:03 mail postfix/smtpd[1378]: disconnect from host-xxx-xx.opticon.hu[85.90.xxx.xx]
Dec 10 12:18:03 mail postfix/qmgr[27797]: 2371039831F: removed

---

### Post by neptune on 2006-12-10
Does this HowTo include instructions for collecting remote mail from your ISPs mail server and forward to / dump into one of the virtual accounts?

eg: you have your own @yourname.com domain, and you also have [email]emailaccount@yourisp.com[/email].

This document covers how to setup Ubuntu as mail server for @yourname.com, which is great. I also have emails coming to @yourisp.com which I'd like to collect and drop into one of the virtual mailboxes. 

Is that possible?

Thanks!

---

### Post by dninja on 2006-12-10
Install yourself fetchmail then create a file called .fetchmailrc like this on in your users home directory:

[PHP]
poll <isp server> proto pop3 nodns
        user <isp username> with password <password> is <the full local username> here
        forcecr keep[/PHP]

the last two statments are optional, look in the man pages to see what they do.

You can then run fetchmail manually to bring the mail down or run fetchmail -d <time> to put it in daemon mode.

---

### Post by patg51 on 2006-12-12
Loved the tutorial.  Various configuration files are modified at different times in the tutorial.  At the end my config files (/etc/postfix/main.cf and master.cf for example) are pretty hacked up.

I try to keep related stuff together and had a hard time doing that with the various updates to the same config file in different places in the tutorial.  

An additional link that would show the complete config files would be helpful (to me at least).

Have been playing with this for a while and cannot get past the amavisd-new tests.

I was successful in testing the mail server up to section Configure / IMAP (Courier).

The next step for the amavisd-new get a "connection refused" to port 10024.

I have no idea where to look.  Any suggestions?

---

### Post by mootpoint on 2006-12-29
I've been working through this setup howto. I'd strongly suggest that in the "data" section, you tell us which database to put the data into! I figured it out, but:

Current text:

So we got a fully set up mail server... Well no, there is no users, domains, no nothing! 

Okay, first you need add some default data, some which are required, some which make sense. 

Then we'll add your own users and domains.

Proposed text:

So we have a fully set up mail server ... Well, no, there are no users, domains, no anything!

OK, first we need to add some default data to maildb. Some is required, some just makes sense. Then we'll add your own users and domains.

First, open the maildb database as the mail user:

mysql -u mail -p maildb

Enter the password for the mail sql account when prompted. 

Then add the required domains for local email: <continue with current text>


Hope that proves useful ... and I imagine I'll have a question or two shortly.

mootpoint

---

### Post by dninja on 2006-12-29
Something telling how to use the procmail columns in the database as well would be good.

---

### Post by Sprinker on 2007-01-01
Hey can someone make this sticky?  I think its a terrific tutorial and should be used by anyone who is slightly new to Linux and setting up a mail server can be a daunting task, I know it was for me.  I would like to personally thank Flurdy for this contribution.

---

### Post by Acker on 2007-01-08
Hi!

At first thx for the great guide. My Server is up and running. But it seems that spamassassin doesnt work. I don't get any X-Spam header e.g. Virus scan with amavis works... 

Anyone got the same problem?

Acker

---

### Post by milwell on 2007-01-11
I encountered this error after following flurdy's tutorial.

Warning: include_once(DB.php) [function.include-once]: failed to open stream: No such file or directory in /usr/share/squirrelmail/functions/db_prefs.php on line 40

Warning: include_once() [function.include]: Failed opening 'DB.php' for inclusion (include_path='.:/usr/share/php:/usr/share/php/PEAR') in /usr/share/squirrelmail/functions/db_prefs.php on line 40

It turns out, php-pear does not install DB.php,  just enter:

pear install DB

and it will connect to database. :rolleyes: 

Thanks to flurdy for the great guide.

---

### Post by foxmulder on 2007-01-14
Hi Guys,

I think Flurdy's How-to is nice, but it would be a lot more useful if it was setup like this one: [http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

The reason for that is, that that one actually has all the commands spelled out as well, so the real n00b's (like myself) can just copy/paste most of it!

Especially the part with all the packages is rather time consuming! Now I have to go find out each time what I need to apt-get, because the guide just says:

"Now everything is installed it is time to configure each of the core applications used." Duh, I haven't installed anything yet! Because the guide does not tell me the package names!

Is there ANYONE out there that can actually turn Flurdy's how-to in something like that?

---

### Post by mrsym0r on 2007-01-15
Hello all,

I've followed this guide, and installed all the required packages, but when I try to create the first mysql table, i get:

ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ''ALIASES' (
`pkid` smallint(3) NOT NULL auto_increment,
`mail` varchar(120) NOT ' at line 1
mysql>

The mysql version installed was 5.0.22-Debian_0ubuntu6.06-log .

I'm guessing that since the guide was created, the syntax has changed. Is anyone able to point me in the right direction of what it would now be?

Thanks in advance to anyone who replies.

-Simon

---

### Post by dninja on 2007-01-15
I've tried this command on a matching mysql server and it worked fine. Make sure that  the cut and paste didn't get any extra characters or miss any.

---

### Post by shakyamuni on 2007-01-15
Hi Everyone.

I 've been through hard times setting the server. I made it and it worked for a while. I decided to mount another server with more capacity, and I copied all the config files (postfix main and master cf files + courier+ virtual tables) from the first server to the new one. Everything looked good but I detected a subtle error when sending email via smtp. In the first server I have a couple of mozilla thunderbird clients authenticated using username and password to send email. But I could make it with the second server using authentication with SMTP, so I had to set them as not authenticated.

Any ideas to workaround?

thanks alot in advance.

CARLOS.

---

### Post by Jonhoo on 2007-01-20
Great tutorial! 
Only thing is, do you know when you will release the guide for Edgy?

Looking forward to it :)

Jonhoo

---

### Post by mlcampbe on 2007-01-22
I've been reading over this thread and the flurdy howto preparing to upgrade my exisitng mail server. I currently have approx 30 email users and am not using mysql to store the user info. What is the advantage of putting everything into a database? Should I really consider mysql for just 30 users?

---

### Post by Juzz on 2007-01-22
For those who get errors like:

```
relay=none
```
and
```
Connection refused [10024]
```

try to start up Amavis while in the debug windows (the log windows).
That can give an indication of what could possibly be wrong (in my case wrong permissions on a dir that I could fix in an instant - while I had been staring me blind on it).

Now all I need to figure out is how I can import mails from my old SuSE sendmail/cyrus imap system...
If anyone has a clue to that please point me in the right direction :cool:

---

### Post by shakyamuni on 2007-01-23
> **elvis said:**
> This is twice in a row now where I've asked a question and answered it myself.  Maybe I should have a bit more patience before I post questions to the forums? :)

The problem was not defining the transport_maps which I've got sorted out now.

Anyways... I've set up autoreply / autoresponder / vactaion email notices (whatever you want to call it).  I did the following:

1) In /etc/postfix/main.cf was the following as per flurdy's guide:
```

# this is how to connect to the domains (all virtual, but the option is there) 
# not used yet 
# transport_maps = mysql:/etc/postfix/mysql_transport.cf

```

I uncommented the last line:
```

# this is how to connect to the domains (all virtual, but the option is there) 
# not used yet 
transport_maps = mysql:/etc/postfix/mysql_transport.cf

```

2) I created a /etc/postfix/mysql_transport.cf file which looked up the "transport" field of the "domains" table:
```

user=database_username
password=database_password
dbname=maildb
table=domains
select_field=transport
where_field=domain
hosts=127.0.0.1
additional_conditions = and enabled = 1

```

3) I added the transport type "autoreply" to /etc/postfix/master.cf:
```

autoreply unix  -       n       n       -       -       pipe
  flags= user=nobody argv=/etc/postfix/autoreply $sender $mailbox

```

4) I created an executable script /etc/postfix/autoreply :
```

mail -s"Fireworks Digital Autoreply From: <$2>"  $1 < /etc/postfix/autoreply_message

```
Make sure you chmod 755 the file to make it executable.

And with it, the text /etc/postfix/autoreply_message to go with it (make this whatever you want).

5) Into the table "domains" I added the row domain="autoreply.mydomain.com" transport="autoreply:" (note the trailing ":" - it is important).

Basically that's it.  Now autoreply is working. To enable a user to be set to autoreply, in the "aliases" table, add the destination "user@autoreply.mydomain.com".  What happens is the mail server looks up the domain "autoreply.mydomain.com", see's the transport is the unix pipe to the script /etc/postfix/autoreply, which in turn fires an email back at the original sender with the message attached!

And with that working, my client can now take holidays.  Wish I could too. :)


Hello Elvis and everybody,:KS 

I've configured this mini-how to to implement vacations on postfix, but when I'm trying to send an email to test the autoreply message, instead, I receive this kind of email :

This is the Postfix program at host mailman.stitchkin.cl.

I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to <postmaster>

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

			The Postfix program

<webmaster@autoreply.domain.com> (expanded from <webmaster@domain.com>):
    Command died with status 127: "/etc/postfix/autoreply". Command output:
    /etc/postfix/autoreply: line 1: mail: command not found


Any ideas?


thanks a lot in advance.

regards,
Carlos.

---

### Post by Jonhoo on 2007-01-28
Hmm.. 
Had the same problem, but I think all I did was:
sudo apt-get install mail

:P

BTW:
When will the guide be updated for Edgy? ^^

---

### Post by shakyamuni on 2007-01-28
> **Jonhoo said:**
> Hmm.. 
Had the same problem, but I think all I did was:
sudo apt-get install mail

:P

BTW:
When will the guide be updated for Edgy? ^^

install mail??? I'm sorry, but I don't think that fix the problem....how many coincidences with packages in the repositories could be with "mail"?

thank you anyway.....
I still have the same problem....
Does anyone knows what's happening with this issue?

thanks

Carlos.

---

### Post by Tspiritstorm on 2007-01-29
Great Guide!

I am having one issue that remains and I know it is me doing something stupid. Aliases are not working correctly. I can tell it is checking via the /etc/postfix/mysql_alias.cf and then checking the DB but for some reason it is not resolving that [email]myalias@mydomain.com[/email] should resolve to [email]myaccount@mydomain.com[/email]. 

I am getting an Unknown User error with the alias email account.

---

### Post by Lord_Pancake on 2007-02-16
I am trying to test my server setup now. I can send mail to my gmail account, and recieve it. But when I try to reply to it, I never recieve it on my machine, At least i don't think I am. But I don't recieve a mesg saing it failed.

Thank you,
-Lord_Pancake

---

### Post by ltk5 on 2007-02-16
have to try this mail-thingie. It looks really cute :)

---

### Post by DanteUseless on 2007-02-19
Hi there!
This is a great tutorial, but I'm missing some parts:
*Edgy.. (fixed after some work)
*Userspesific spamassasin and procmail (use the fields allready made in db) - anyone got tips about this?
*Teach spamassassin spam. Testing and debuging.
*Same goes for antivirus.

Btw, the tutorial is HUGE, should be split up to several pages :)

---

### Post by Juzz on 2007-03-13
For those who get errors when trying to send mails using TLS/SSL by entering login info and you get this error:

```
"no secret in database"
```

Then find this line in main.cf :

```
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
```

and replace with:

```
smtpd_sasl_path = smtpd
```

It got my system running and enabling users to put in their usernames when sending mails over TLS/SSL.

---

### Post by Juzz on 2007-03-14
Can anyone here help me?

I cannot get amavis/postfix to insert the header "X-Spam-Status:" - I have tried several things... I have followed flurdy's howto and mixed it up with the workaround.org and help.ubuntu.com PostfixAmavisNew - all to no avail :( 

Is it Thunderbird that thinks that the user shouldn't see that header - or is it just not getting inserted?

I am trying both the "Show All Headers" option in Thunderbird and pressing CTRL-U for viewing the source and neither reveals the header...

Has the header been removed from amavis and have they created a new method of marking spam?

---

### Post by Juzz on 2007-03-21
I figured out how to enable the spamheaders...

You have to activate some **bypass** settings!?! :-k

In one of the config files: "/etc/amavis/conf.d/15-content_filter_mode"

You have to uncomment the bypass variables...

I think that's a weird way of thinking... To activate a bypass setting to enable the scanners...

---

### Post by sirgeekalot on 2007-03-30
> **dninja said:**
> Hi
Has anyone got an answer to this? I initially put the procmailrc file in my users home directory but then realised that the mail account is a virtual one so that wouldn't help. The field in the database doesn't seem to be used for anything, no sql is pulling the info out.

Help, I'm missing my filtering.

Did anyone ever get any response to this question?? i would like to use procmail for filtering instead of amavis due to resource problems. (i.e. i dont have enough of them!!)

---

### Post by The Muttster on 2007-03-31
It don't work.

Now I've got that out of the way, I'll describe what's happening:

When I connect to port 110 and authenticate my username and password, I get

-ERR Temporary problem, please try again later
Connection closed by foreign host.

Obviously, that presents me with a problem as I'd like to read my mail. I can connect on port 25 and send an email but that's only half the job.

Sadly, this is where the guide is a bit lacking for noobs like myself. The question is, how do I go about investigating what's wrong and how do I fix it?

---

### Post by DanteUseless on 2007-04-01
> **sirgeekalot said:**
> Did anyone ever get any response to this question?? i would like to use procmail for filtering instead of amavis due to resource problems. (i.e. i dont have enough of them!!)

Hi there. I gave up using procmail and i found out a solution using maildrop.
Basicly postfix delivers the mail to maildrop (not virtual: ), and maildrop looks at DB for user-info (username, aliases, maildir, etc). But its still not using the sql-field for filter. I've goto make the filters by hand in files.

Another problem was that ubuntu's maildrop had to be recompiled with mysql-support.

---

### Post by kkevin on 2007-05-25
> **Juzz said:**
> For those who get errors when trying to send mails using TLS/SSL by entering login info and you get this error:

```
"no secret in database"
```

Then find this line in main.cf :

```
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
```

and replace with:

```
smtpd_sasl_path = smtpd
```

It got my system running and enabling users to put in their usernames when sending mails over TLS/SSL.

Hi Juzz,
just wanted to say thank you for posting this. It did fix my problem (that I've been researching for literally DAYS).

Does anyone know what the implication is here?  What is going on with this change?
Thanks.

---

### Post by badfeet on 2007-05-29
Hello, I just followed this guide and (most) everything went smoothly.  The only problem I have is that
the users are not being created in /var/mail/vitrual.  The first two I set up had the directories created,
but all the users I've added since won't create the directory, so they are unable to receive any mail
and can't log in via IMAP or squirrelmail.  Any assistance you can provide would be appreciated.

Thanks!

---

### Post by Pollywoggy on 2007-05-30
This is an excellent tutorial.  I am setting up Postfix on a second machine and using the information in the tutorial.  If it works out, I will do the same on the main machine.

I am confused about something.  In the section CREATE TABLE `users`:

CREATE TABLE `users` (
`id` varchar(128) NOT NULL default '',
`name` varchar(128) NOT NULL default '',
`uid` smallint(5) unsigned NOT NULL default '5000',
`gid` smallint(5) unsigned NOT NULL default '5000',
`home` varchar(255) NOT NULL default '/var/spool/mail/virtual',
`maildir` varchar(255) NOT NULL default 'blah/',
`enabled` tinyint(3) unsigned NOT NULL default '1',
`change_password` tinyint(3) unsigned NOT NULL default '1',
`clear` varchar(128) NOT NULL default 'ChangeMe',
`crypt` varchar(128) NOT NULL default 'sdtrusfX0Jj66',
`quota` varchar(255) NOT NULL default '',
`procmailrc` varchar(128) NOT NULL default '',
`spamassassinrc` varchar(128) NOT NULL default '',
PRIMARY KEY  (`id`),
UNIQUE KEY `id` (`id`)
) ;

What is the purpose of the line

`clear` varchar(128) NOT NULL default 'ChangeMe',
`crypt` varchar(128) NOT NULL default 'sdtrusfX0Jj66'

I suspect I should have put something other than 'ChangeMe' and 'sdtrusfX0Jj66' when I did it.  If that is the case, do I need to use md5crypt to generate them?  Can I use PHPMyadmin to change the entries so I do not need to remove the table and enter the table info again?

Thanks for the tutorial.

---

### Post by oziemike on 2007-07-16
Hi all

I have setup about 3 of these servers now and they all work well. Having a problem (or maybe it is supposed to be this way??) with email clients.

In Evolution every time I open evol I get a message about the certificates and have to accept them for each session. Much the same with Outlook Express in Windoze.

I am using SSL on port 995 for receiving and TLS on 587 for sending. 

Evolution always starts with "Failed to get a valid greeting from ....... (the server)"

Can anyone give me some pointers??

Thanks

Mike

---

### Post by evilmrrogers411 on 2007-07-25
Im just getting started on this howto guide and was looking at the part 
"""""""""
OS: Ubuntu
The most important setting, security wise, is to configure the firewall. This off course varies between firewalls, your usage. Shorewall main config _**files in /etc/shorewall that we are concerned with, are interfaces, hosts, zones, policy and rules.**_
Here is a typical basic zones file

#zone display comment 
loc Local Local network 
net Net Tinternet
"""""""""

I dont see these files (interfaces, hosts, zones, policy and rules) even when I have it showing hidden files.  Am I suppose to create these files and just copy and paste what he has written like above or did I do something wrong when I got the packages (The way I installed all the packages was using the synaptic package manager and just looking up and marking all the packages that was said along with their dependencies).

---

### Post by Verifier on 2007-08-08
I got the "no secret in database" problem. I've changed to "smtpd_sasl_path = smtpd" in main.cf and I do not have any trailing spaces in /etc/postfix/sasl/smtpd.con.

```
Aug  8 10:53:07 www postfix/smtpd[9470]: connect from unknown[192.168.1.100]
Aug  8 10:53:27 www postfix/smtpd[9470]: warning: SASL authentication failure: no secret in database
Aug  8 10:53:27 www postfix/smtpd[9470]: warning: unknown[192.168.1.100]: SASL CRAM-MD5 authentication failed
Aug  8 10:53:27 www postfix/smtpd[9470]: warning: SASL authentication failure: Password verification failed
Aug  8 10:53:27 www postfix/smtpd[9470]: warning: unknown[192.168.1.100]: SASL PLAIN authentication failed
Aug  8 10:53:27 www postfix/smtpd[9470]: warning: unknown[192.168.1.100]: SASL LOGIN authentication failed
Aug  8 10:54:28 www postfix/smtpd[9470]: lost connection after AUTH from unknown[192.168.1.100]
Aug  8 10:54:28 www postfix/smtpd[9470]: disconnect from unknown[192.168.1.100]

```

All suggestions are most welcome since this is driving me mad after a couple of days trying to fix it :/

---

### Post by dmeyer on 2007-08-14
I'm having a problem relaying to an Exchange server inside my domain.  The Ubuntu server is located in the DMZ.  In my initial postfix setup I had  the relay working properly, but now that I have virtual domains it isn't working.  I have two local domains and my third domain is a relay domain and that is the one I'm having trouble with.

I'm testing th SMTP connection manually and when I get to 

*RCPT TO: <****@relaydomain.tld>*  the server responds with "454 4.7.1 <****@relaydomain.tld> Relay access denied".

A few items from my main.cf:

[I]#blank for virtual domains:
local_recipient_map =
my_destination =

#so I don't lose any messages during testing:
soft_bounce = yes

#transport maps are tested and working
transport_maps = hash:/etc/postfix/transport

#domain to relay for is specified here:
relay_domains = [relaydomain.tld]

#there might be an issue with this section?
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:192.168.2.2:10023, permit
[/I]

I think the problem is either with the smtpd_recipient_restrictions statement or the problem is happening when it does a lookup in the domains table in mysql.  I think it might be overriding the transport_maps setting and looking up the domain in the domains table and then rejecting it.  Is there possibly a way to specify the transport_maps setting in the transport field of the domains table?

I know I'm very close, but I'm not sure where to go from here, so any suggestions would be greatly appreciated.

---

### Post by dmeyer on 2007-08-15
I got the relay problem working by adding in the line "mynetworks = 127.0.0.1, 192.168.2.0, etc... " to the postfix main.cf file.  I'm not sure why that wasn't included in the howto, but I guess it isn't necessary for all configurations.

---

### Post by kevin79 on 2007-08-17
> **crilen007 said:**
> I went through the entire setup, but I can't seem to Telnet to my postfix server from localhost.

It starts up ok, and without error. Not sure what files one may need to help with this.

I know this message is old but do you remember how your fixed this? I'm having the same problem.

---

### Post by flurdy on 2007-08-26
If the shorewall files arent there, then you should create them.
There are examples in /usr/share/shorewall

---

### Post by bobster_b on 2007-09-23
I've been working through this tutorial which seems to be rather good.  I'm having one problem so far, the courier-authmysql package cannot be found.  I'm fairly new to Ubuntu, so I'm not exactly sure on where to go next...

Thanks, Heath

---

### Post by evanleibovitch on 2007-10-17
Hello Ivar and everyone,

I appreciate the work that has gone into this system; it has worked very well and demonstrated what can be done with a combination of open source tools.

I now have an installation that has been running smoothly for some time, but the users have requested a vacation-reply system.

Is there one technique that is recommended? In this forum I have seen a number of approaches, including a Squirrel plugin and some methods that require adding database tables.

Since this method has become widely used, are there any preferred approaches?

Thanks for any suggestions!

- Evan

---

### Post by oziemike on 2007-12-25
I would just like to highlight to anyone the importance of setting the "smtpd_sasl_path = smtpd" as mentioned below in the quote.

I had a full setup running on 6.06 LTS which has been running well for about a year. I had been overseas for a few months and when I got back near the machine I did the full dist-upgrade. It upgraded kernel. mysql, sasl and lots of other packages and it seemed all had gone OK till I tried to send mail.

I was getting the same messages as below and the simple act of changing the above parameter from Flurdy's original line fixed it. This was after much hunting, reloading backups etc, but kit all came down to that and is going fine again all updated.

This is still one of the best mail servers I have used and is extremely reliable.

Mike 

> **Verifier said:**
> I got the "no secret in database" problem. I've changed to "smtpd_sasl_path = smtpd" in main.cf and I do not have any trailing spaces in /etc/postfix/sasl/smtpd.con.

```
Aug  8 10:53:07 www postfix/smtpd[9470]: connect from unknown[192.168.1.100]
Aug  8 10:53:27 www postfix/smtpd[9470]: warning: SASL authentication failure: no secret in database
Aug  8 10:53:27 www postfix/smtpd[9470]: warning: unknown[192.168.1.100]: SASL CRAM-MD5 authentication failed
Aug  8 10:53:27 www postfix/smtpd[9470]: warning: SASL authentication failure: Password verification failed
Aug  8 10:53:27 www postfix/smtpd[9470]: warning: unknown[192.168.1.100]: SASL PLAIN authentication failed
Aug  8 10:53:27 www postfix/smtpd[9470]: warning: unknown[192.168.1.100]: SASL LOGIN authentication failed
Aug  8 10:54:28 www postfix/smtpd[9470]: lost connection after AUTH from unknown[192.168.1.100]
Aug  8 10:54:28 www postfix/smtpd[9470]: disconnect from unknown[192.168.1.100]

```

All suggestions are most welcome since this is driving me mad after a couple of days trying to fix it :/

---

### Post by MarilenCorciovei on 2007-12-27
Here is[ my experience]("http://www.len.ro/work/tools/gutsy-on-a-ubuntu-server/qmail/view") installing qmail using the qmailrocks guide with some modifications.

---

### Post by breiko on 2008-03-26
Hi there,
 I tried to follow the how-to as careful as I could. Now I'm testing the system and I have this problem:

```
breiko@rory:~$ telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 mail.MYDOMAIN.com ESMTP Postfix (Ubuntu)
ehlo mail.MYDOMAIN.com
250-mail.MYDOMAIN.com
250-PIPELINING
250-SIZE 10240000
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
mail from:test@test.com
250 2.1.0 Ok
rcpt to:info@MYDOMAIN.com
554 5.7.1 Service unavailable; Client host [127.0.0.1] blocked using relays.ordb.org; ordb.org was shut down on December 18, 2006. Please remove from your mailserver.
quit
221 2.0.0 Bye
Connection closed by foreign host.

```

Service unavailable?? :confused:

---

### Post by breiko on 2008-03-26
> **breiko said:**
> Hi there,

Service unavailable?? :confused:

Solved.
Just removed all rbl entries in main.cf

---

### Post by lofgren on 2008-05-19
Hi all,

I've used this excellent howto to configure postfix/squirrelmail and mysql db's with the overall goal being a smarthost configuration.

My domain is registered with godaddy and I have configured a catch-all address there.

I can send internally and relay outbound, but sorting incoming mail is the problem.

[B]My question is - what's the best way to sort mail sucked down from the catch-all address?
Has anyone done this? Got some config files I can peek at to get an idea?[/B]

I am trying to do:  [ISP] -> fetch -> sort -> [MTA]

It doesn't have to be incredibly complicated. Probably a couple of filters to grab my wife's mail and the rest can go to my mailbox.

I have toyed with 'fetchmail' / 'getmail' into postfix.

From what I have seen/tried fetchmail is okay to dump mail into postfix for one mailbox. getmail wants to dump to mbox or maildir folders, or use an intermediate mta such as procmail/maildrop.

As per the getmail page ([http://pyropus.ca/software/getmail/configuration.html#conf-retriever-multidrop](http://pyropus.ca/software/getmail/configuration.html#conf-retriever-multidrop)), the godaddy config is not a "maildrop" or "domain mailbox" setup. 
It is missing the necessary headers to make it easy for me ;)

Thanks for any help (and for the awesome guide),
Lofgren

PS>
My system is ubuntu, upgraded from 7.04 -> 7.10 -> 8.04 then I've followed this guide, installed postfix/squirrelmail etc. 
It also runs mythtv and has had mysql from the start.

A couple of issues I found with the current guide are:
-Pear DB not installed. Needed to run: pear install db
-needed square brackets around the relayhost host in main.cf and to include a port for godaddy smtp.
-old hosts in rbl entries as mentioned by the previous poster eg: spamhaus.org

---

### Post by BlairKatu on 2008-05-27
SquirrelMail gives me the following error an a successful login

```
Connection dropped by IMAP server.

```

I have tested extensively and found little help, If anyone knows about this it would be appreciated

---

### Post by lofgren on 2008-05-31
> **BlairKatu said:**
> SquirrelMail gives me the following error an a successful login

```
Connection dropped by IMAP server.
```

I have tested extensively and found little help, If anyone knows about this it would be appreciated

It's been a couple of weeks now and I am swiftly forgetting.. but does the user you are trying to log in as have mail yet?

I found that to "enable" the user's mailbox, I had to send them mail from the command line (see the test section in the howto).
This creates their mail folders and seems to fulfill one of the requirements for squirrelmail and courier-imap.

Once I had sent mail to one mailbox, I could log in to squirrelmail and then send mail to the others.

There might have been other steps I had to do as well, but I do recall this was one of them.

good luck.

---

### Post by exactaperfecta on 2008-06-25
I am completely new to Ubuntu OS and I am trying to set up an email server for the first time.

I have installed all of the packages and now I am trying to configure Shorewall.

I am having trouble editing the config files in the Terminal.  I am unable to change the text without error messages coming up.  Also, I don't know how to save the edited file when I am done.

Please advise.

Thanks,
Ward

---

### Post by qrwe on 2008-07-03
Has anyone tried the flurdy guide together with Roundcube instead of Squirrelmail?

There are two major packages available through aptitude:
roundcube: Makes the major configurations for you, including creating the Roundcube database.
roundcube-webmail: No database is created. It's easier to follow [the official installation guide]("http://trac.roundcube.net/wiki/Howto_Install") with this one though.

---

### Post by qrwe on 2008-07-03
> **breiko said:**
> Hi there,
 I tried to follow the how-to as careful as I could. Now I'm testing the system and I have this problem:

```
breiko@rory:~$ telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 mail.MYDOMAIN.com ESMTP Postfix (Ubuntu)
ehlo mail.MYDOMAIN.com
250-mail.MYDOMAIN.com
250-PIPELINING
250-SIZE 10240000
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
mail from:test@test.com
250 2.1.0 Ok
rcpt to:info@MYDOMAIN.com
554 5.7.1 Service unavailable; Client host [127.0.0.1] blocked using relays.ordb.org; ordb.org was shut down on December 18, 2006. Please remove from your mailserver.
quit
221 2.0.0 Bye
Connection closed by foreign host.

```

Service unavailable?? :confused:

You're trying to use a blacklist which is not available anymore. Remove it from smtpd_client_restrictions in /etc/postfix/main.cf (and don't forget to postmap and reload afterwards).

***

Added later:
Sorry for the double post, missed the post right afterwards.

---

### Post by Temujin_12 on 2008-07-04
I've run through the guide, loaded data, and was able to test (ie: manually telnet'ing works).

After adding the extra services (auth, ssl, spamassasin, clamav, etc.) when I start courier-imap-ssl I get the following error:

```

 * Starting Courier IMAP-SSL server...
/etc/init.d/courier-imap-ssl: xmalloc: ../bash/make_cmd.c:99: cannot allocate 557 bytes (0 bytes allocated)

```

I've tried increasing IMAP_ULIMITD in /etc/courier/imapd as per [this forum thread posting]("http://isp-control.net/forum/howto-make-ispcp-more-secure-t-257-2.html#pid5676"), but to no avail.  I even tried setting it to unlimited but still get the same error.

Starting non SSL imap works just fine.

Any ideas as to what may be causing this?


EDIT: By the way this is on an Ubuntu 6.04 server following the [5th edition of the guide]("http://flurdy.com/docs/postfix/edition5.html").

---

### Post by fade2gray on 2008-07-06
At [[COLOR="Blue"]_Configuration > Content Checks (amivisd-new)_[/COLOR]]("http://flurdy.com/docs/postfix/#config-adv-content")```
cd /etc/amavis.d/conf.d
```
Should that read ```
cd /etc/amavis/conf.d
```:confused:

And```
vi /etc/spamassassin/local.rf
```
Should that read ```
vi /etc/spamassassin/local.**c**f
```:confused:

Also, there seems to be a conflict at [[COLOR="Blue"]_Configuration > Encryption (TLS)_[/COLOR]]("http://flurdy.com/docs/postfix/#config-secure-crypt") - You are advised to "Please refer to [[COLOR="Blue"]_previous edition_[/COLOR]]("http://flurdy.com/docs/postfix/edition5.html#conf_encryption")  for more detail", where you are told to enter into the master.cf file```
smtps inet n - n - - smtpd
```Returning to [[COLOR="Blue"]_Configuration > Encryption (TLS)_[/COLOR]]("http://flurdy.com/docs/postfix/#config-secure-crypt"), you are told to enter```
smtps inet n - - - - smtpd
```:confused:

Any advice please?

---

### Post by lofgren on 2008-07-07
First part should be "cd /etc/amavis/conf.d" according to my system.

The older tute asks you to edit "50User", but seems a little rushed in that section - I think it was also a quote from someone else's suggestion or something.

Anyway on my system, "50-User" was the actual file to be edited.


I cannot comment on spamassassin as I skipped that section.

I'm not 100% sure of the smtps line. From the comments in my file, I believe the second "n" will make the process run in a chroot jail. I vaguely recall reading some conflicting discussion on whis as to which was best and why.
Either way, mine is set without the second "n".

Hope that helps.

---

### Post by fade2gray on 2008-07-07
Thanks for the reply lofgren.

Also, I think 'vi /etc/courier/authmysql' should read 'vi /etc/courier/authmysql**rc**' (the latter already exists after install).
I this is true, should 'authmodulelist="authmysql"' read 'authmodulelist="authmysql**rc**"' within '/etc/courier/authdaemonrc'?

---

### Post by 448191 on 2008-07-17
> **tbird469 said:**
> After much hair pulling with getting postfix/smtp/sasl/mysql working, it turned out that I had trailing spaces at the end of each line from the copy/paste in the /etc/postfix/sasl/smtpd.conf

After removing the spaces from the file and reloading postfix all was well.

I was getting errors in /var/log/auth.log like these until I removed the trailing spaces:

postfix/smtpd[27381]: SQL engine 'mysql ' not supported
postfix/smtpd[27381]: auxpropfunc error no mechanism available
postfix/smtpd[27381]: _sasl_plugin_load failed on sasl_auxprop_plug_init for plugin: sql

Other than that the howto was great.

That was very helpful. I was pulling my GD hair out. Removed all trailing spaces and voila.

---

### Post by bucksquare on 2008-07-17
Hello,
I'm following : [https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto).

Where do i place - A Maildir is a directory (often named Maildir) with three subdirectories named tmp, new, and cur. The subdirectories should all reside on the same filesystem-this directory.

Thanks

Next.

I tried to use my domain mmail but the mx record does not exist. is this something the domain holder does or do I use dns server in the ubuntu server.

Thanks

---

### Post by pavel989 on 2008-07-18
Kool!, this'll be awesome if i ever do start a website. thnx!

---

### Post by cochones on 2008-07-19
Hi there,
after following a part of this tutorial my webserver (apache2) don't start. I have tried many things and have also googled the error. So i don't know what to do an I hope someone of you can help me!

When I try to start the webserver with this command:
/etc/init.d/apache2 start

I get this error:

```
Starting web server (apache2)...
(98)Address already in use: make_sock: could not bind to address [::]:443
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:443
no listening sockets available, shutting down
Unable to open logs
 failed!

```

I have already looked up if another application is running which is using port 443 or port 80. But there is nothing.

Hope to get help :-)

---

### Post by cochones on 2008-07-20
Hi there,
I have fixed the Problem. I don't exaktly know what the problem was, but know it works :D. If anyone wanna know the solution was...write here.

So far..stay tuned!

---

### Post by oink on 2008-08-04
Hi all,

I have a problem integrating getmail in the flurdy mailserver. For some users i fetch the mail from a pop3 box with getmail and give it to Postfix with the MDA_external = /usr/sbin/sendmail command.

```
[options]
#message_log = /var/log/getmaillog
delete = false

[retriever]
type = SimplePOP3SSLRetriever
server = pop.gmail.com
username = myname@gmail.com
password = mypasswd

[destination]
type = MDA_external
path = /usr/sbin/sendmail
arguments = ('-bm','myname@mydomail.com')
unixfrom = true

```

The problem is that amavis is bypassed if i fetch my mail with getmail.

Anyone any idea, i'am really stuck!!
Thanks!!!

---

### Post by RalphG1000 on 2008-08-06
I am running 
Ubuntu 6.06.2 LTS

After following this tutorial I can telnet to port 25 from another machine.
I can: ehlo abc.com
mail from:<mr@abc.com>
rcpt to:<mrs@def.co.uk> (A domain registered on the server)

but then it always cuts me off tating "connection lost"

The logs in /var/log/mail.* show...

"Aug  6 00:05:39 ubuntu postfix/smtpd[4182]: fatal: 127.0.0.1:: missing service information"

The full log is below:

root@ubuntu:/var/log# vi mail.info.0
Aug  5 23:59:07 ubuntu spamd[3604]: spamd: server pid: 3604
Aug  5 23:59:07 ubuntu spamd[3604]: spamd: server successfully spawned child process, pid 3642
Aug  5 23:59:07 ubuntu spamd[3604]: spamd: server successfully spawned child process, pid 3643
Aug  5 23:59:07 ubuntu spamd[3604]: prefork: child states: II
Aug  5 23:59:17 ubuntu authdaemond.plain: modules="authmysql", daemons=5
Aug  5 23:59:20 ubuntu postfix/master[3975]: daemon started -- version 2.2.10, configuration /etc/postfix
Aug  6 00:05:05 ubuntu postfix/smtpd[4182]: connect from unknown[192.168.0.3]
Aug  6 00:05:39 ubuntu postfix/smtpd[4182]: fatal: 127.0.0.1:: missing service information
Aug  6 00:05:40 ubuntu postfix/master[3975]: warning: process /usr/lib/postfix/smtpd pid 4182 exit status 1
Aug  6 00:05:40 ubuntu postfix/master[3975]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling

I have spent many hours trying to solve this one problem and would appreciate any suggestions.

Thanks in advance, Ralph.

---

### Post by RalphG1000 on 2008-08-06
Still can't narrow the problem down any further so built another server using "http://workaround.org/articles/ispmail-sarge/" and it ran like a dream first attempt.

Will play tutorials off against each other now have a working box to add postgrey etc.

Ralph : )

---

### Post by stony999 on 2008-08-08
I tried all ways,
[LIST]
[*]I removed trailing spaces.
[*]I tried smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
[*]I tried smtpd_sasl_path = smtpd
[*]I created /etc/sasldb2
[*]I copied /etc/sasldb2 to /var/spool/postfix/etc/sasldb2, changed acces rights
[*]I tried pwcheck_method: saslauthd with saslauthd  and smtpd_sasl_path = /var/run/saslauthd
[*]If I put PLAIN LOGIN into smtpd.conf the smtp-Dialog still offers
250-AUTH=NTLM LOGIN PLAIN DIGEST-MD5 CRAM-MD5
[*]I straced postfix but I found no entry for smtpd.conf
[*]I wrote a script which automatically starts strace on smtpd when it starts  but I found no entry for smtpd.conf. (Ok, I am of course missing the first part in the trace, as it takes time to detect that smtpd has started and to stat strace, so)
[*]I tried saslfinger -s and it always gives me "There is no smtpd.conf that defines what SASL should do for Postfix. SMTP AUTH can't work!
[/LIST]

I am pretty sure now that postfix does not try to load smtpd.conf in one of these paths. I have no clue where I shall put it. Even strace didn't help.

Also mysql.log does not show any entries, when trying to send mails. When sending mails it works though).

In auth.log I always get
```

Aug  8 06:01:57 mail postfix/smtpd[14122]: sql_select option missing
Aug  8 06:01:57 mail postfix/smtpd[14122]: auxpropfunc error no mechanism available
Aug  8 06:01:57 mail postfix/smtpd[14122]: _sasl_plugin_load failed on sasl_auxprop_plug_init for plugin: sql
```

Questions:
[LIST]
[*]Any idea where to look further?
[*]Anyone has it running on 8.04 and may post it's configuration? 
[/LIST]

I have 
[LIST]
[*]Ubuntu 8.04
[*]postfix 2.5.1-2ubuntu1
[*]postfix-mysql (2.5.1-2ubuntu1)
[*]ibntlm0_0.3.13-1 
[*]libgsasl7_0.2.21-1 
[*]libsasl2-modules-sql_2.1.22.dfsg1-18ubuntu2 
[*]libauthen-sasl-perl_2.10-1
[/LIST]

---

### Post by stony999 on 2008-08-08
After modifying saslfinger shell script in order to give some more output where he seeks the file, I found out that indeed the smtpd.conf contained a space at the end in it's filename

My entry in main.cf is now
```
smtpd_sasl_path = smtpd
```

And my /etc/postfix/sasl/smtpd.conf is now
```
pwcheck_method:auxprop
auxprop_plugin:sql
mech_list:plain login cram-md5 digest-md5
sql_engine:mysql
sql_hostnames:127.0.0.1
sql_user:user
sql_passwd:pass
sql_database:maildb
sql_select:select clear from users where id='%u@%r' and enabled = 1

```

---

### Post by qrwe on 2008-08-23
> **Pollywoggy said:**
> This is an excellent tutorial.  I am setting up Postfix on a second machine and using the information in the tutorial.  If it works out, I will do the same on the main machine.

I am confused about something.  In the section CREATE TABLE `users`:

CREATE TABLE `users` (
`id` varchar(128 ) NOT NULL default '',
`name` varchar(128) NOT NULL default '',
`uid` smallint(5) unsigned NOT NULL default '5000',
`gid` smallint(5) unsigned NOT NULL default '5000',
`home` varchar(255) NOT NULL default '/var/spool/mail/virtual',
`maildir` varchar(255) NOT NULL default 'blah/',
`enabled` tinyint(3) unsigned NOT NULL default '1',
`change_password` tinyint(3) unsigned NOT NULL default '1',
`clear` varchar(128) NOT NULL default 'ChangeMe',
`crypt` varchar(128) NOT NULL default 'sdtrusfX0Jj66',
`quota` varchar(255) NOT NULL default '',
`procmailrc` varchar(128) NOT NULL default '',
`spamassassinrc` varchar(128) NOT NULL default '',
PRIMARY KEY  (`id`),
UNIQUE KEY `id` (`id`)
) ;

What is the purpose of the line

`clear` varchar(128) NOT NULL default 'ChangeMe',
`crypt` varchar(128) NOT NULL default 'sdtrusfX0Jj66'

I suspect I should have put something other than 'ChangeMe' and 'sdtrusfX0Jj66' when I did it.  If that is the case, do I need to use md5crypt to generate them?  Can I use PHPMyadmin to change the entries so I do not need to remove the table and enter the table info again?

Thanks for the tutorial.

This was a typical post where smileys should be banned from the surface of Earth! :-) <- OK, nevermind..

My problem is similar to this. When I tell courier to look for the "crypt" table in the database, it says that the passwords doesn't match. I succeed to log in when using plaintext ("clear" table) though. I do not want to reveal my password in the logs though (yes, I can read it clearly there), so how do I tell courier to decrypt the passwords in the crypt table?

Thanks for your support!

---

### Post by noclue2008 on 2008-08-27
Hi im new to the ubuntu thing,
I need some help im receiving this error

* Stopping MySQL database server mysqld                                                                                                              [ OK ]
 * Starting MySQL database server mysqld                                                                                                              [ OK ]
 * Checking for corrupt, not cleanly closed and upgrade needing tables.

---

### Post by dumarjo on 2008-08-28
is it possible to use some gui web based interface to administer this setup ?

Dumarjo

---

### Post by wetjet43 on 2008-09-03
It seems that a LOT of people are having problems with this guide. Everything from small typos to commands that just aren't working. I'm stuck on creating a new certificate using the command:

openssl req -x509 -newkey rsa:1024 -keyout imapd.pem \ -out imapd.pem -nodes -days 999

It just won't work. :confused:

This guide needs to be updated so the people who want to setup an email server for their orginazation can do so without hiccups and problems. I'm trying to get the elementary school I work at away from M$ Xchange server, and I'm unable to because the instructions in the guide are not 100% correct. I'd love to ditch our current mail server and go with this one... but for not it's not possible.

One more thing... VI is horrible! I like nano instead. Much easier to use, and the commands are right there that tell you how to use it.

---

### Post by ewtrowbr on 2008-09-08
Flurdy,

I was able to get most of the stuff working with some fiddling... I had to take the time to read through and make sure you know what's up with individual apps instead of cut-paste-pray. 

All in all, an excellent guide. This server was used last weekend to host mail for various New Orleans Small businesses fleeing Gustav, including the St. Bernard Parish Government. Flurdy, I'll be looking for your tipjar/wishlist, if it exists.  

Never did manage to get the crypt passwords working, so I used plain in SQL. I had to reference an earlier version of the guide to help me do this.  

If you want pop, you have to 'sudo apt-get install courier-pop' and configure. 

I'll go back through this thread and see if I can help people. 

I am interested in making unique spam folders for my users to hold quarantined mail. I cannot figure out how to do this without user shell accounts. If somebody knows, they can save me some research time. ;)

Erich

---

### Post by ewtrowbr on 2008-09-08
> **noclue2008 said:**
> Hi im new to the ubuntu thing,
I need some help im receiving this error

* Stopping MySQL database server mysqld                                                                                                              [ OK ]
 * Starting MySQL database server mysqld                                                                                                              [ OK ]
 * Checking for corrupt, not cleanly closed and upgrade needing tables.

I don't believe that's an error, just a statement that the software is checking for jacked up tables. Mine does the same thing. You should be cool...

Erich

---

### Post by ewtrowbr on 2008-09-08
> **wetjet43 said:**
>  One more thing... VI is horrible! 

I tried using nano, but the 'esc:w' feature was broken, so I went back to vim. 

:lolflag:

Erich

---

### Post by issackelly on 2008-10-12
I'm having problems with SASL and SSL on SMTP.

Here are my logs from a connection request

```
postfix/smtpd[2699]: connect from (outside host)
postfix/smtpd[2699]: setting up TLS connection from (outside host)
postfix/smtpd[2699]: SSL_accept error from (outside host_: -1
postfix/smtpd[2699]: lost connection after STARTTLS from (outside  host)
postfix/smtpd[2699]: disconnect from (outside host)
postfix/smtpd[2714]: warning: xsasl_cyrus_server_get_mechanism_list: no applicable SASL mechanisms
postfix/smtpd[2714]: fatal: no SASL authentication mechanisms
postfix/master[1746]: warning: process /usr/lib/postfix/smtpd pid 2714 exit status 1
postfix/master[1746]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling

```

OK... and HERE is what happens when I don't use SSL

```

postfix/smtpd[2838]: connect from (outside host)
postfix/smtpd[2838]: warning: SASL authentication failure: no secret in database
postfix/smtpd[2838]: warning: (outside host): SASL CRAM-MD5 authentication failed: authentication failure
imapd-ssl: LOGIN, user=issac@servee.com, ip=[::ffff:(outside host)], port=[49997], protocol=IMAP

```

IMAP is connecting fine (over ssl) and SMTP still won't connect at all (using the same credentials on the same database)


And just before that bit in the logs is this (not sure if it's related)

```
 postfix/master[2811]: warning: process /usr/lib/postfix/smtpd pid 2822 exit status 1
 postfix/master[2811]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
 postfix/smtpd[2823]: fatal: unexpected command-line argument: reject
 postfix/master[2811]: warning: process /usr/lib/postfix/smtpd pid 2823 exit status 1
 postfix/master[2811]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling

```
it always fails.

---

### Post by zmaj_lee on 2008-10-15
I am stuck ](*,)with my problem and it is so frustrating. I am hoping that somebody knows answer to my problem. I already have postfix setup with spamassassin and it is relaying emails to my exchange, and it also have a nice set of rules configured where one of them is to block anybody from outside who tries to send email somewhere else using my servers which is awesome but now I am in the situation where I need to make an exception so this particular IP address can send e-mail on my behalf to other people thru my email servers. I have no idea how to get this working and I need this working like yesterday ofcourse :). I found something on postfix smtp auth but I am not so sure if I can do that on my existing setup or if that would actually help me. Please ubuntu/postfix guru's show me the way and I'll follow. :guitar:

---

### Post by obitori on 2008-10-21
I just installed the Ubuntu 8.10 beta (Ibex).  Some of the file names have changed.  php-myadmin is now phpmyadmin and libclamav3 is now libclamav5.

If you cut and paste the below, you'll get all the programs that Flurdy installs...

```
apt-get install mysql-client mysql-server postfix postfix-mysql libsasl2-modules-sql libgsasl7 libauthen-sasl-cyrus-perl courier-base courier-authdaemon courier-authlib-mysql courier-imap courier-imap-ssl courier-ssl amavisd-new spamassassin spamc clamav-base libclamav5 clamav-daemon clamav-freshclam postgrey squirrelmail squirrelmail-locales php-pear php5-cli phpmyadmin shorewall shorewall-doc vim mutt lynx 
```

Good luck!

---

### Post by obitori on 2008-10-23
I am a big fan of your HOWTO.  In Edition 7 of your HOWTO, you provided the following script to create the table "users".  My question is this:  

Why do you create a "home" directory for the account?  Wouldn't it make sense to use "id/", which should be unique, as the home?

maildir + / + id + / should create a unique home directory for each user's mail, correct?

```
CREATE TABLE `users` (
`id` varchar(128) NOT NULL default '',
`name` varchar(128) NOT NULL default '',
`uid` smallint(5) unsigned NOT NULL default '5000',
`gid` smallint(5) unsigned NOT NULL default '5000',
`home` varchar(255) NOT NULL default '/var/spool/mail/virtual',
`maildir` varchar(255) NOT NULL default 'blah/',
`enabled` tinyint(3) unsigned NOT NULL default '1',
`change_password` tinyint(3) unsigned NOT NULL default '1',
`clear` varchar(128) NOT NULL default 'ChangeMe',
`crypt` varchar(128) NOT NULL default 'sdtrusfX0Jj66',
`quota` varchar(255) NOT NULL default '',
`procmailrc` varchar(128) NOT NULL default '',
`spamassassinrc` varchar(128) NOT NULL default '',
PRIMARY KEY  (`id`),
UNIQUE KEY `id` (`id`)
) ;
```

> So what does each of these lines do? Well the domains are pretty straight forward. 

The users are as well, it requires four fields. ID is the email address of the user, and also its username when loggin in, described later on. NAME is optional description of the user. MAILDIR is the name of the folder inside /var/spool/mail/virtual. It must end in a /, otherwise it wont be used as a unix maildir format. CRYPT is the encrypted text password to use.

---

### Post by lukeb.vr on 2008-11-04
> **dumarjo said:**
> is it possible to use some gui web based interface to administer this setup ?

Dumarjo

I'm trying to get a webgui working on this system using postfixadmin, but it appears that Ill have to rework the entire mysql database to match the one expected in postfixadmin. Has anyone had any luck in doing this?

---

### Post by satimis on 2008-11-07
Hi folks,


I'm following this howto to build a mail server.  I prefer installing Roundcube as webmail dropping squirrelmail and squirrelmail-locales.  Any other packages I can forget.


Is Roundcube available on Ubuntu repo?  TIA



B.R.
satimis

---

### Post by dchurch24 on 2008-11-23
Hi, great guide. Followed it and everything seems to be looking good.

I can send mail if I telnet in on 25, but having installed Squirrelmail, I can't log in to see if I have received mails.

This is entirely on a local network and I have sent test mails to root@localhost, but if I try to login to squirrelmail with root@localhost and [password], I get the following:

"ERROR
Unknown user or password incorrect."

Anyone else had this, or can point me in the right direction?

I did set this up before on another (external) server, and after a little bit of a struggle got it all working. That was without any spam or virus protection though, hence I followed this guide.

Please help, I'm stuck ;-)

UPDATE: I've managed to log in (for one user at least), but when I do I get the "IMAP dropped etc..." message - usually this means that the user hasn't received a mail and therefore the mail dirs are not set up. I have sent a mail to user@localhost, but this doesn't seem to be getting delivered.

I have teleneted on 25 and sent mail to external addresses and they have received fine. I'm obviously doing something wrong, but I cannot work out what.

---

### Post by aparrish on 2008-11-23
dchurch24:

I just followed the directions today. I seem to have smtp sending via telnet on port 25 working as well.

I found that his instructions tell you to insert users into the user's table as [email]user@domain.com[/email] this causes a lookup failure when loggin in via squirrelmail. The users when logging in via squirrelmail are user instead of [email]user@domain.com[/email]. I just modified my entry in the user's table to be "user"

I also had to switch from crypt to clear in the /etc/courier/authmysqlrc file. I am now able to login with the text of the clear field in the database as my password. 

This is an undesireable situation but at least lets me test my setup. I need to get encrypted passwords working now :)

Please respond to PM if you want to discuss via some instant messaging client.

---

### Post by aparrish on 2008-11-23
Looks like you are getting something like this in /var/log/mail.log

Nov 23 18:50:22 sephiroth imapd-ssl: chdir /var/spool/mail/virtual/username/: No such file or directory


Fix it by creating your /var/spool/mail/virtual/username directory for the user you are working with. I also had to make sure to create the 5000 gid and uid and chown it to the virtual user.

Cheers!

---

### Post by dchurch24 on 2008-11-24
Hi, thanks for the reply (and the PM, have added you in AIM ;-) )

I had already created the user folders in the virtual directory and chowned them to the same user, but I still get the IMAP error in squirrelmail.

I think the problem is that the mail is just not arriving in the users inbox and thus not setting up something that it should to get it working.

I am getting the following in the /var/log/mail.log:

```

Nov 24 10:17:03 dave-desktop imapd-ssl: Connection, ip=[::ffff:127.0.0.1]
Nov 24 10:17:03 dave-desktop imapd-ssl: chdir Maildir: No such file or directory

```

So it implies that there is a folder called Maildir that is missing somewhere.

---

### Post by dchurch24 on 2008-11-24
Ok, created the folders /home/[user]/Maildir and subs /cur /tmp and new.

I can now log into the users mail using Squirrelmail.

However, there is no mail there waiting.

If I send a mail using Squirrelmail, it never arrives either, yet if I telnet to port 25 and send one manually, it arrives where is hould (just not in my [user]@localhost account).

Clearly I have set something up wrong, but I don't know what.

---

### Post by satimis on 2008-11-24
> **dchurch24 said:**
> Ok, created the folders /home/[user]/Maildir and subs /cur /tmp and new.

Hi dchurch24,

It's NOT necessary to create the subdirectories, /cur, /new and /tmp.  They will be automatically generated on the arrival of the 1st mail.

But you must manually create /var/spool/mail/virtual/Maildir and run;```

# chown -R virtual:virtaul /var/spool/mail/virtual/Maildir

```

Then you can send/read mails on SM

HTH


satimis

---

### Post by dchurch24 on 2008-11-24
Thanks for that.

I did the chown, but still no mail arrives (or can be sent) through Squirrelmail.

The user I have set up is 'dave', so I have sent mail to dave@localhost, but despite this user being in the db, the mail never arrives.

---

### Post by satimis on 2008-11-24
> **dchurch24 said:**
> Thanks for that.

I did the chown, but still no mail arrives (or can be sent) through Squirrelmail.

The user I have set up is 'dave', so I have sent mail to dave@localhost, but despite this user being in the db, the mail never arrives.
Ah dchurch24,


1)
Sorry I forgot to mention "virtual:virtual" works on my system.

/var/spool/mail/virtual/Maildir is owned by "virtual" and in the "virtual group" here.  I don't know whether it is the same on your system.  Otherwise you have to adjust them to suit your case.  If the same, please check /etc/group to see they are there.


2)
Did you send the mail to 'dave' from another PC via Internet.  Then you have to address the mail "dave@domain.com"


satimis

---

### Post by dchurch24 on 2008-11-24
Hi, thanks again.

I corrected the typo ;-) before I chown'ed.

I have looked in /etc/group and the last entry is 'virtual:x:5000:' - is that correct?

I am sending the mail from inside my network - on the same machine as the server in fact.

---

### Post by satimis on 2008-11-24
> **dchurch24 said:**
> Hi, thanks again.

I corrected the typo ;-) before I chown'ed.

I have looked in /etc/group and the last entry is 'virtual:x:5000:' - is that correct?

# grep virtual /etc/group```

virtual:x:5000:
```
It is the same here


> 
I am sending the mail from inside my network - on the same machine as the server in fact.
All servers here are headless.  I install/config server remotely.  I can't test it here.


My guess, please try;```

dave@127.0.0.1
```
to check whether it works.

satimis

---

### Post by dchurch24 on 2008-11-24
rcpt to: dave@127.0.0.1

returns:

501 5.1.3 Bad recipient address syntax

---

### Post by hctopcu on 2008-12-17
I'm a newbee. Your guide is extremely helpfull thank you.
I have a running apache server on my machine. I am afraid of messing up so I skipped setting up firewall for now.

I managed to set up Courier IMAP. I can log in through imap but when I try to send mails, I get:
```
Dec 17 13:09:13 mygitarapp postfix/smtpd[24035]: connect from unknown[88.235.53.100]
Dec 17 13:09:13 mygitarapp postfix/smtpd[24035]: NOQUEUE: reject_warning: RCPT from unknown[88.235.53.100]: 504 5.5.2 <ArGoNNB>: Helo command rejected: need fully-qualified hostname; from=<gunman@mygitar.com> to=<c@gri.in> proto=ESMTP helo=<ArGoNNB>
Dec 17 13:09:13 mygitarapp postfix/smtpd[24035]: NOQUEUE: reject: RCPT from unknown[88.235.53.100]: 554 5.7.1 <c@gri.in>: Relay access denied; from=<gunman@mygitar.com> to=<c@gri.in> proto=ESMTP helo=<ArGoNNB>
Dec 17 13:09:13 mygitarapp postfix/smtpd[24035]: NOQUEUE: reject_warning: RCPT from unknown[88.235.53.100]: 504 5.5.2 <ArGoNNB>: Helo command rejected: need fully-qualified hostname; from=<gunman@mygitar.com> to=<c@gri.in> proto=ESMTP helo=<ArGoNNB>
Dec 17 13:09:13 mygitarapp postfix/smtpd[24035]: NOQUEUE: reject: RCPT from unknown[88.235.53.100]: 554 5.7.1 <c@gri.in>: Relay access denied; from=<gunman@mygitar.com> to=<c@gri.in> proto=ESMTP helo=<ArGoNNB>
Dec 17 13:09:13 mygitarapp postfix/smtpd[24035]: NOQUEUE: reject_warning: RCPT from unknown[88.235.53.100]: 504 5.5.2 <ArGoNNB>: Helo command rejected: need fully-qualified hostname; from=<gunman@mygitar.com> to=<hctopcu@gmail.com> proto=ESMTP helo=<ArGoNNB>
Dec 17 13:09:13 mygitarapp postfix/smtpd[24035]: NOQUEUE: reject: RCPT from unknown[88.235.53.100]: 554 5.7.1 <hctopcu@gmail.com>: Relay access denied; from=<gunman@mygitar.com> to=<hctopcu@gmail.com> proto=ESMTP helo=<ArGoNNB>
Dec 17 13:09:14 mygitarapp postfix/smtpd[24035]: disconnect from unknown[88.235.53.100]
```
I can't understand why a client need to have a hostname. (As I said I'm a rookie)

---

### Post by hctopcu on 2008-12-17
I made it by editing /etc/hostname and giving a correct domain.
But I don't get it. My server was accepting other smptp connections form gmail etc. I only had problems with clients. The problem and solution conflicts in my mind. I don't get it. If the problem was in servers hostname, why the rest of the world does not get the same problem?

---

### Post by nomaam on 2008-12-17
Does any one know of an iso image download of a setup mail server for those of us who are not able to get this tutorial working? Possibly a Torrent download?

---

### Post by lukeyduke on 2008-12-22
I have recently installed a fantastic webmail client, Atmail. They are a commercial email server appliance and webmail provider, however they have recently released a free version of their software, called atmail open. The biggest advantage is that I can now access my emails from anywhere in the world from the same fantastic interface every time. I find it is a much faster, simpler, better looking interface than any other, such as hotmail and gmail.

You can find an tutorial for installing it on there website here, it worked first go for me without any hassles whatsoever --> [http://atmail.com/kb/2008/installing-atmail-open-webmail-client-on-ubuntu/]("http://atmail.com/kb/2008/installing-atmail-open-webmail-client-on-ubuntu/")

---

### Post by anwoke8204 on 2009-01-02
I too am having this issue, I have configured everything, but when I try to log in, I get the invalid user, or incorrect password.  when I check the log it says that password entered doesn't match the crypt password.  Anyone know how I can resolve this.  Many thanks.  I haven't set u TLS yet, because I wanted to get it up and running first then will get TLS going.  I am running ubuntu server 8.04.  many thanks
Andrew

---

### Post by anwoke8204 on 2009-01-02
Could this be becuse I haven't enabled TLS, I have also tried switching to clear on the auth instead of crypt, but get the same issue.  I have created the username and password using the add user script given on the site also given below

INSERT INTO users (id,name,maildir,clear) VALUES
('email@address','short description','foldername/',encrypt('password'));
INSERT INTO aliases (mail,destination) VALUES
('email@address','email@address');
but I put in the valid information and passwords.

I also have an issue with amavisd when it is enabled, postfix won't start, I have an issue finding out where the "pickup" transort part of the config file is where you are supposed to paste the following:

-o content_filter=
         -o receive_override_options=no_header_body_checks

when that is enabled, postfix fails to start.  could someone give me some advise.  TIA

---

### Post by proddy on 2009-01-02
On the topic of "**Unknown user, or invalid password**" I had similar problems and found out the encrypted passwords created by MySQL (using encrypt()) don't match the MD5 checks done in the authentication library. I used the below script to generate the encrypted passwords and then manually inserted them into MySQL using the phpMyAdmin web app.

[FONT="Courier New"]#!/usr/bin/perl

if( $#ARGV != 0 )
{
 print "usage: vcrypt password\n";
 exit 1;
}
    my $salt = join '', ('.', '/', 0..9,'A'..'Z', 'a'..'z')[rand 64, rand 64];
    print crypt($ARGV[0], $salt) ."\n";[/FONT]

---

### Post by proddy on 2009-01-02
and, on the topic from ***hctopcu ***on the _**rejected clients**_, I had the same problem with postfix rejecting my Windows MS Outlook client "relay denied etc". I fixed it by:

1. including my home network in the postfix main.cf, e.g. adding
[FONT="Courier New"]mynetworks = 10.0.0.0/24, 127.0.0.0/8[/FONT]

2. removing "[FONT="Courier New"]reject_non_fqdn_recipient[/FONT]" from the [FONT="Courier New"]smtpd_recipient_restrictions[/FONT] paramter also in the postfix main.cf

Hope that helps

Paul

---

### Post by proddy on 2009-01-02
One change perhaps for Edition 8 of this excellent guide is where you say

# then check if postfix is listening on 25 and mysql on 3306
netstat -tnp

on my Ubuntu 8.10 server it's **[FONT="Courier New"]netstat -tnpa[/FONT]** (or -tnpl) to show the sockets that are actively listening

---

### Post by anwoke8204 on 2009-01-02
for lhat script do I just use nano and copy it into there, and save it as filename.pl in an accessible directory from the webserver, or how do I use that script.  Many thanks

---

### Post by proddy on 2009-01-03
copy it to a file and call it vcrypt. chmod 755 it. Then to run it use ./vcrypt <clean password> and it will generate the crypt'd version.

---

### Post by chamal on 2009-01-04
Hi, I have a authentication problem in the basic configuration with the procedure of [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

the configuration that I check very times is the same as the web
I use Ubuntu 8.04 in a virtual machine and a client microsoft outlook 2007 to connect to imap server. I think that the problem is the crypt but I can not find anywhere the solution.

the syslog

Jan  4 16:18:10 ubmail authdaemond: received auth request, service=imap, authtype=login
Jan  4 16:18:10 ubmail authdaemond: authmysql: trying this module
Jan  4 16:18:10 ubmail authdaemond: SQL query: SELECT id, crypt, "", uid, gid, home, concat(home,'/',maildir), "", name, "" FROM users WHERE id = "prueba@chamalzone.com" AND (enabled=1)
Jan  4 16:18:10 ubmail authdaemond: supplied password 'prueba' does not match encrypted password 'sdtrusfX0Jj66'
Jan  4 16:18:10 ubmail authdaemond: authmysql: REJECT - try next module
Jan  4 16:18:10 ubmail authdaemond: FAIL, all modules rejected
Jan  4 16:18:10 ubmail imapd: LOGIN FAILED, user=prueba@chamalzone.com, ip=[::ffff:192.168.1.112]

Please, help me.

---

### Post by proddy on 2009-01-04
dude, scroll-up and look at post #183

[http://ubuntuforums.org/showpost.php?p=6482091&postcount=183](http://ubuntuforums.org/showpost.php?p=6482091&postcount=183)

---

### Post by chamal on 2009-01-04
Sorry because the question and thanks a lot. The scpript fix my problem

---

### Post by ttolliver on 2009-01-07
Good evening,

First off, let me start with kudos for an awesome tutorial.  Sure, there may be some rough edges for a lot of us working through it, but I'm an IT geek and appreciate the complexity of what we're pulling off here.  So bravo Flurdy!!!

Okay, now to where I met my personal Waterloo ;~)

I worked through all the install and config, then found a typo when starting services for the first time.  Right now I'm in the beginning of the testing on the step where you telnet to localhost to send an email manually.  I can telnet fine, but I get an "unknown user" error for both the sending and receiving users in /var/log/mail.log when trying to send any email (see below).

I started out trying to send an email from my normal ISP account, but was running into spamhaus related block messages.  So the test you see below is me just trying to email from one local user to another.

At this point I haven't processed a successful email, so I don't have the mail directories in /var/spool/mail/virtual yet.

I've read all of the posts I can find related to "unknown user" errors, but they all seem to be encountered by people much farther along in their testing -- usually around squirrelmail debug.  So those answers don't seem to be pointed at my problem.

Any ideas would be greatly appreciated!

Thanks,
Tom


```

Jan  7 20:47:42 lndwr postfix/cleanup[16770]: 3448D3E1A4: message-id=<20090108024736.3448D3E1A4@mail.sdj.com>
Jan  7 20:47:42 lndwr postfix/qmgr[16765]: 3448D3E1A4: from=<test1@sdj.com>, size=382, nrcpt=1 (queue active)
Jan  7 20:47:42 lndwr postfix/virtual[16776]: 3448D3E1A4: to=<test2@sdj.com>, relay=virtual, delay=15, delays=15/0.01/0/0.01, dsn=5.1.1, status=bounced (unknown user: "test2@sdj.com")
Jan  7 20:47:42 lndwr postfix/cleanup[16770]: DEEE63E1A6: message-id=<20090108024742.DEEE63E1A6@mail.sdj.com>
Jan  7 20:47:42 lndwr postfix/qmgr[16765]: DEEE63E1A6: from=<>, size=2215, nrcpt=1 (queue active)
Jan  7 20:47:42 lndwr postfix/bounce[16773]: 3448D3E1A4: sender non-delivery notification: DEEE63E1A6
Jan  7 20:47:42 lndwr postfix/qmgr[16765]: 3448D3E1A4: removed
Jan  7 20:47:42 lndwr postfix/virtual[16776]: DEEE63E1A6: to=<test1@sdj.com>, relay=virtual, delay=0.03, delays=0.02/0/0/0.01, dsn=5.1.1, status=bounced (unknown user: "test1@sdj.com")
Jan  7 20:47:42 lndwr postfix/qmgr[16765]: DEEE63E1A6: removed

```

---

### Post by ttolliver on 2009-01-07
Here's another question, probably not related to my last post (famous last words, hehehe).

I built my server with the server hostname of 'xxxxxx'.  My expectation is that hostname can (and should) be totally separate from the fact that I'm building this box to host my domain, 'www.yyyyyy.com'.  And as I build a mail server out of the same box, I feel like I should be able to have standard mail server naming conventions of 'smtp.yyyyyy.com' and 'pop.yyyyyy.com'.

Am I correct in those assumptions?

At some level, I understand completely that the 'www.yyyyyy.com', 'smtp.yyyyyy.com', and 'pop.yyyyyy.com' all hit my machine through the magic of DNS (DynDNS in my case) and a given port associated with the service.  But once the network connection is made to my machine, it shouldn't care what my server hostname is.  Right?

That being said, I'm willing to accept that my server hostname may be considered to have a full hostname of 'xxxxxx.yyyyyy.com' because it is a part of the established 'yyyyyy.com' domain.  That's not unreasonable.

Oh, and one last tidbit.  I wonder if there is an inconsistency in the v7 instructions.  There are a couple places where we configure a hostname as 'smtp.yyyyyy.com' and a couple where we configure 'mail.yyyyyy.com'.  I'm guessing we're supposed to use all one or all the other.

Thanks in advance for the education!

Tom

---

### Post by Peque on 2009-01-09
Hey guys. 

after and update of some perl packages UI'm, running into this error - Is there anything I can do about it ??? 

```
Jan  9 06:57:17 sif amavis[4791]: (04791-01-4) (!)PRESERVING EVIDENCE in /var/lib/amavis/tmp/amavis-20090109T065710-04791
Jan  9 06:57:17 sif postfix/smtp[4798]: B1EC415061E: to=<rita@xxxxxx.xxx>, relay=127.0.0.1[127.0.0.1]:10024, conn_use=4, delay=85072, delays=85019/47/0/6.2
, dsn=4.5.0, status=deferred (host 127.0.0.1[127.0.0.1] said: 451 4.5.0 Error in processing, id=04791-01-4, quar+notif FAILED: temporarily unable to quaranti
ne: 451 4.5.0 Local delivery(1) to /var/lib/amavis/virusmails/v/spam-vtVlZTj5ZmNU.gz failed: Can't call method "value" on an undefined value at /usr/share/pe
rl5/IO/Compress/RawDeflate.pm line 98., id=04791-01-4 at /usr/sbin/amavisd-new line 10371. (in reply to end of DATA command))
Jan  9 06:57:18 sif amavis[4801]: (04801-01-3) (!)451 4.5.0 Local delivery(1) to /var/lib/amavis/virusmails/w/spam-wF3wbVF51GVY.gz failed: Can't call method 
"value" on an undefined value at /usr/share/perl5/IO/Compress/RawDeflate.pm line 98.
Jan  9 06:57:18 sif amavis[4801]: (04801-01-3) (!!)TROUBLE in check_mail: quar+notif FAILED: temporarily unable to quarantine: 451 4.5.0 Local delivery(1) to
 /var/lib/amavis/virusmails/w/spam-wF3wbVF51GVY.gz failed: Can't call method "value" on an undefined value at /usr/share/perl5/IO/Compress/RawDeflate.pm line
 98., id=04801-01-3 at /usr/sbin/amavisd-new line 10371.
Jan  9 06:57:18 sif amavis[4801]: (04801-01-3) (!)PRESERVING EVIDENCE in /var/lib/amavis/tmp/amavis-20090109T065716-04801
Jan  9 06:57:18 sif postfix/smtp[4775]: BA82A150571: to=<rita@xxxxxx.xxx>, relay=127.0.0.1[127.0.0.1]:10024, conn_use=3, delay=145226, delays=145171/53/0/2.
1, dsn=4.5.0, status=deferred (host 127.0.0.1[127.0.0.1] said: 451 4.5.0 Error in processing, id=04801-01-3, quar+notif FAILED: temporarily unable to quarant
ine: 451 4.5.0 Local delivery(1) to /var/lib/amavis/virusmails/w/spam-wF3wbVF51GVY.gz failed: Can't call method "value" on an undefined value at /usr/share/p
erl5/IO/Compress/RawDeflate.pm line 98., id=04801-01-3 at /usr/sbin/amavisd-new line 10371. (in reply to end of DATA command))
Jan  9 06:57:19 sif amavis[4791]: (04791-01-5) (!)451 4.5.0 Local delivery(1) to /var/lib/amavis/virusmails/f/spam-fmQs5XfFlx+6.gz failed: Can't call method 
"value" on an undefined value at /usr/share/perl5/IO/Compress/RawDeflate.pm line 98.
Jan  9 06:57:19 sif amavis[4791]: (04791-01-5) (!!)TROUBLE in check_mail: quar+notif FAILED: temporarily unable to quarantine: 451 4.5.0 Local delivery(1) to
 /var/lib/amavis/virusmails/f/spam-fmQs5XfFlx+6.gz failed: Can't call method "value" on an undefined value at /usr/share/perl5/IO/Compress/RawDeflate.pm line
 98., id=04791-01-5 at /usr/sbin/amavisd-new line 10371.

```

---

### Post by NerdWorld on 2009-01-10
Has anybody seen this error?

warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: No such file or directory



I think I have the proper path variable to find smtpd.conf
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2



As far as I know, I'm not supposed to be using a the Berkely db.  Correct?

This is preventing me from logging in (although everything else works fine!)

TIA!

---

### Post by qrwe on 2009-01-12
> **NerdWorld said:**
> Has anybody seen this error?

warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: No such file or directory



I think I have the proper path variable to find smtpd.conf
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2



As far as I know, I'm not supposed to be using a the Berkely db.  Correct?

This is preventing me from logging in (although everything else works fine!)

TIA!

Found this URL: [[COLOR="Navy"]SMTP Authentication with Postfix using files or MySQL[/COLOR]]("http://enc.com.au/myscripts/postfixmysql.html").
Hope you'll find something there.

---

### Post by bluethundr on 2009-01-13
Hello Ubuntu linux guys,
 
Could really use your help with this one. 

Well, first off MUCH THANKS to flurdy for his brilliant tutorial which I followed to the best of my ability here:

[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

Truly excellent work and an excellent tutorial. 

Nevertheless I am having some problems that I can sure use some help on.

Let me state before going any further that I _need_ to mysqlize my postfix backend, any user limitations on my end be damned!

Currently, my postfix mail setup can send to the universe, but cannot receive.


Bear in mind that in the following config files you will see my domain obscured as mail. foo.com 

The space you see is not a type-o in the config. It's a slight bug in the perl script I used to scrub my config and log files of important information that could open me up to security breaches. Better safe than sorry as they say. In short disregard the space you see when you see mail. foo.com I assure you it's really mail.foo.com in the actual config.

Mail sent to my account gets this bounce message:

[http://paste.debian.net/25859/](http://paste.debian.net/25859/)

Mail sent to my domain apparently disappears into a black hole for 7 days as my mail system delays bouncing it. I'd love to know why.

In this and in all of my further pastebins I have sanitized vital information in order to protect my domain and accounts from abuse. But you should still be able to tell what's going on from the info presented.

Here's one thing I would like to note before we proceed. This is how my virtual_mailbox_base is set in main.cf:

virtual_mailbox_base = /var/spool/mail/virtual

Yet though I have accounts setup in my mysql database, when I cd to that location the directory is completely empty.

Also, another odd thing is that I keep seeing references to [email]user@foo.com[/email]. No where in my main.cf is foo.com mentioned so I am at a loss to understand this.

This you might not be able to help with though, because 'foo' is how I obscure my domain in posts to pastebin for security purposes.

Here's my logs (obscured of course using foo and other obfuscations including the nonsensical 666.666.666.666 representing my public IP).

[http://paste.debian.net/25861/](http://paste.debian.net/25861/)

As you can see, my logs are rife with errors that I am unclear on how to address.

Here is my my main.cf file (again obfuscated):

[http://paste.debian.net/25863/](http://paste.debian.net/25863/)

Here's my master.cf file for good measure (not sure if this helps or not):

[http://paste.debian.net/25864/](http://paste.debian.net/25864/)

This is my virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf

[http://paste.debian.net/25867/](http://paste.debian.net/25867/)

This is my virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf

[http://paste.debian.net/25869/](http://paste.debian.net/25869/)

This is my virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf

[http://paste.debian.net/25870/](http://paste.debian.net/25870/)

This is my virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf

[http://paste.debian.net/25871/](http://paste.debian.net/25871/)

And my final mysql interaction in my main.cf, 

virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf

[http://paste.debian.net/25872/](http://paste.debian.net/25872/)

This is how my mail database is setup:

[http://paste.debian.net/25873/](http://paste.debian.net/25873/)

This is my aliases table in mysql:

[http://paste.debian.net/25874/](http://paste.debian.net/25874/)

This is my domains table:

[http://paste.debian.net/25875/](http://paste.debian.net/25875/)

and finally this is my users table:

[http://paste.debian.net/25876/](http://paste.debian.net/25876/)


And lastly, POP and IMAP refuse to authenticate valid user data.

Here is my /etc/courier/authmysqlrc:

[http://paste.debian.net/25877/](http://paste.debian.net/25877/)

This is my /etc/courier/imapd:

[http://paste.debian.net/25879/](http://paste.debian.net/25879/)

And finally, finally here's my /etc/courier/pop3d

[http://paste.debian.net/25946/](http://paste.debian.net/25946/)


That's all I can think of for now, it's late and I'm heading to bed. 

ANY insight into my plight at all will save a poor sysadmin's sanity.

Thank you all very much.

---

### Post by qrwe on 2009-01-15
Hello bluethundr,

As I assume you've already checked those config files carefully, it's always intresting to look out for unwanted incidents in '/var/log/mail.log'. As there's problem *sending* mail, it's sounds like something with postfix or/and amavis.
Another tip is to check '/etc/postfix/master.cf', there maybe something you've missed (or added inaccuratly) there. Compare with the flurdy guide if you're unsure, documentation at [www.postfix.org](www.postfix.org) is also your friend. :-)
Good luck.

---

### Post by Rolihla on 2009-01-22
hi everybody,

I'm a french newbe, someone can say me how to download the EC2 Amis to simply do test?

---

### Post by skywatcher on 2009-01-22
If I install Mailman from Synaptic, do I still have to go through this very complicated procedure of setting it up?  Isn't there an easy-to-use mailing list program for Ubuntu?

---

### Post by walshie on 2009-02-07
Hi all.

I am trying to set up a web and mail server for my parents business. 
i have got the web server working although the web page is not yet complete.([www.gzone.com.au](www.gzone.com.au)).
now i am looking at the web server setup, and it looks very daunting, oh i forgot to mention i am still a newb with linux. i dont suppose there is an easier way? 
i doubt that there is! any advice or should i just go for it and hope for the best.

---

### Post by earth_walker on 2009-02-07
Thanks for this how-to - I set a server up 2 years ago using this and on the software side it was amazing - stable, reliable and lots of features. 

Unfortunately it was on old hardware and behind an unreliable connection, and finally the server has died and I've migrated the company's email to a professional service (fastmail.fm - so far I'm very impressed, and surprise surprise they use a similar setup).

However, here's my problem: Several of the users used squirrelmail only and want their old emails. I have full backups, but of course these emails are sitting in /var/mail/virtual/user folders in coded files that don't seem to be human readable, or at least I don't know how to access.

Can I quickly access these backed up emails in a human readable format, without setting up the whole mail server again? 

Is there a way to import them into an email program so that I can then export them to the current email service? Is it just a matter of installing and configuring squirrelmail and IMAP for a local host?

Thanks,
EW

---

### Post by artifex on 2009-02-10
Thanks for your brilliant howto!

I would like to setup maildrop for moving all spam to a different IMAP folder on Ibex. Is there any tutorial for that?

I have read a lot of different site and now it is working with maildrop instead of courier-maildrop (which does not include courier-authlib for unknown reason) + have to change /var/run/courier/authdaemon as world searchable but it is in very "hacked" state so I would like to clean up my setup a bit.

---

### Post by thelucster on 2009-02-18
Thanks for the guide, very useful, however I am having some issues setting up SMTP authentication. I have followed the instructions to a t, but am unable to authenticate.

In /var/log/auth.log I get:

```
Feb 18 14:28:06 stackednotion postfix/smtpd[3920]: sql_select option missing
Feb 18 14:28:06 stackednotion postfix/smtpd[3920]: auxpropfunc error no mechanism available 
Feb 18 14:28:06 stackednotion postfix/smtpd[3920]: _sasl_plugin_load failed on sasl_auxprop_plug_init for plugin: sql 

```

Here is my /etc/postfix/sasl/smtpd.conf:

```
pwcheck_method: auxprop
auxprop_plugin: sql
mech_list: plain login cram-md5 digest-md5
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: mail
sql_passwd: blah
sql_database: mail
sql_select: select clear from users where id='%u@%r' and enabled = 1
```

Any ideas, it sounds as if it can't find the SQL plugin, but it is definately installed:

```
# apt-get install libsasl2-modules-sql libgsasl7 libauthen-sasl-cyrus-perl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libsasl2-modules-sql is already the newest version.
libgsasl7 is already the newest version.
libauthen-sasl-cyrus-perl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I am running 64bit 8.04.

Regards,

Luca Spiller

---

### Post by vtk on 2009-02-20
Hello all.  I worked through several of the rough spots in the setup, but I'm still experiencing a challenge.

To put it succinctly, I had to manually create the users directory in /var/spool/mail/virtual/<user_dir>.  When I finally got a successful login, I am getting errors that there is no inbox.  I've been through the HOWTO several times over the past few hours, to no avail.  Any ideas?  

I'm trying keep this short, in case this is a 'DUH' situation, but would be more than willing to pastebin any config files.

Thanks much all.

Peace,
V

---

### Post by flurdy on 2009-02-24
> **vtk said:**
> Hello all.  I worked through several of the rough spots in the setup, but I'm still experiencing a challenge.

To put it succinctly, I had to manually create the users directory in /var/spool/mail/virtual/<user_dir>.  When I finally got a successful login, I am getting errors that there is no inbox.  I've been through the HOWTO several times over the past few hours, to no avail.  Any ideas?  

I'm trying keep this short, in case this is a 'DUH' situation, but would be more than willing to pastebin any config files.

Thanks much all.

Peace,
V

Did the users in ...../virtual/.... receive an email?

Remember the folders only gets created when they receive their first email.

---

### Post by IanHobson on 2009-02-24
Help!

Ubuntu newbie here - basic info please! :)

I've set things up according to version 7, and I can login to collect my email (or rather get a "No emails on server" result). 

But I cannot get authenticated when I send emails. 

Same username, same password, same "Use TLS if available" link. 

How do I start investigating this? 

Thanks

Ian

---

### Post by cory_ on 2009-03-13
Flurdy thanks for taking the time to make a howto on setting up an email server.

As usual nothing works the first time as you mentioned in your tutorial.  I was testing my set up and noticed while tailing mysql log that postfix is unable to connect to mysql server.  The error logged says that access is denied for 'mail'@'localhost' (using password: NO). I might add this happens automatically without me starting telnet localhost 25.  Even though this was happening I tried to telnet and it times out after a long while with no results.  I went through the tutorial twice and feel like I have everything set up the way you showed.  I am installing this email server using Ubuntu 8.04 Hardy Heron.

Any help would be greatly appreciated.

---

### Post by mariuxx on 2009-03-17
Hi everyone.

I just followed the excellent howto to set up a mail server. When I came to testing, I experienced some problems.
First of all, there are some differences regarding config files for the different modules. Also commands/program names are different than in the testing section which was written for Dapper more than two years ago. To make matters worse, I'm quite new to Linux configuration, so I don't have many clues about where to look if things don't work first time.
Well, here is where it all stopped...

First, the testing section says (that I'm to issue):
/etc/init.d/courier stop 

There is no /etc/init.d/courier on my system. I believe I installed courier with: 'sudo apt-get courier-base'.
Now I have 3 services running: courier-authdaemon, courier-imap and courier-imap-ssl (all are located in /etc/init.d/)

Well, I have tried to ignore what does not result in direct errors. I stopped the above services, and more or less followed the testing section as well as I could.

The config files for postfix (/etc/postfix/master.cf and main.cf) on my system are quite different from what is shown in the howto. Specifically, none of the files contain an entry about content_filter.

Then, when I try to telnet in on port 25, the connection attempt is refused. I can telnet without specifying port, or specifying 23. I suppose I can edit some settings to let it happen, but I don't know where. I even stopped the Shorewall to be sure it was not the problem.

So, for first I would just love it if somebody could give me a hint to the following questions:
-How do I allow/accept telnet on port 25?
-How do I configure content filter?

Thanx for reading this.

---

### Post by flurdy on 2009-03-17
> **cory_ said:**
> Flurdy thanks for taking the time to make a howto on setting up an email server.

As usual nothing works the first time as you mentioned in your tutorial.  I was testing my set up and noticed while tailing mysql log that postfix is unable to connect to mysql server.  The error logged says that access is denied for 'mail'@'localhost' (using password: NO). I might add this happens automatically without me starting telnet localhost 25.  Even though this was happening I tried to telnet and it times out after a long while with no results.  I went through the tutorial twice and feel like I have everything set up the way you showed.  I am installing this email server using Ubuntu 8.04 Hardy Heron.

Any help would be greatly appreciated.


(If only things would work straight away, then the estimations I do at work may be a bit more correct...)


Is the mail user correctly set up in mysql? e.g. can you log in as it via phpmyadmin or mysql command line?

Do the /etc/postfix/mysql_xxxx files have a password defined in them?

---

### Post by flurdy on 2009-03-17
> **mariuxx said:**
> Hi everyone.

I just followed the excellent howto to set up a mail server. When I came to testing, I experienced some problems.
First of all, there are some differences regarding config files for the different modules. Also commands/program names are different than in the testing section which was written for Dapper more than two years ago. To make matters worse, I'm quite new to Linux configuration, so I don't have many clues about where to look if things don't work first time.
Well, here is where it all stopped...

First, the testing section says (that I'm to issue):
/etc/init.d/courier stop 

There is no /etc/init.d/courier on my system. I believe I installed courier with: 'sudo apt-get courier-base'.
Now I have 3 services running: courier-authdaemon, courier-imap and courier-imap-ssl (all are located in /etc/init.d/)

Well, I have tried to ignore what does not result in direct errors. I stopped the above services, and more or less followed the testing section as well as I could.

The config files for postfix (/etc/postfix/master.cf and main.cf) on my system are quite different from what is shown in the howto. Specifically, none of the files contain an entry about content_filter.

Then, when I try to telnet in on port 25, the connection attempt is refused. I can telnet without specifying port, or specifying 23. I suppose I can edit some settings to let it happen, but I don't know where. I even stopped the Shorewall to be sure it was not the problem.

So, for first I would just love it if somebody could give me a hint to the following questions:
-How do I allow/accept telnet on port 25?
-How do I configure content filter?

Thanx for reading this.

Yes courier's init files have spawned into a few files, but stopping all of them is fine,(theorticaly not all is needed to be stopped, but easier)

Not sure what you mean when your files do not match the howto. The default postfix template config files are quite different to the ones described in this howto. 

If telnetting to the box from the same box then it should be okay. If shorewall is stopped, make sure shorewall's routestopped config file is set to allow external access when firewall is down.

Addin content filters are desribeded here [http://flurdy.com/docs/postfix/#config-adv-content](http://flurdy.com/docs/postfix/#config-adv-content)

---

### Post by flurdy on 2009-03-17
To answer ttoliver's posts from January in case he stills have the same issues, or if others face similar ones:


> **ttolliver said:**
> Here's another question, probably not related to my last post (famous last words, hehehe).

I built my server with the server hostname of 'xxxxxx'.  My expectation is that hostname can (and should) be totally separate from the fact that I'm building this box to host my domain, 'www.yyyyyy.com'.  And as I build a mail server out of the same box, I feel like I should be able to have standard mail server naming conventions of 'smtp.yyyyyy.com' and 'pop.yyyyyy.com'.

Am I correct in those assumptions?

At some level, I understand completely that the 'www.yyyyyy.com', 'smtp.yyyyyy.com', and 'pop.yyyyyy.com' all hit my machine through the magic of DNS (DynDNS in my case) and a given port associated with the service.  But once the network connection is made to my machine, it shouldn't care what my server hostname is.  Right?

That being said, I'm willing to accept that my server hostname may be considered to have a full hostname of 'xxxxxx.yyyyyy.com' because it is a part of the established 'yyyyyy.com' domain.  That's not unreasonable.

Oh, and one last tidbit.  I wonder if there is an inconsistency in the v7 instructions.  There are a couple places where we configure a hostname as 'smtp.yyyyyy.com' and a couple where we configure 'mail.yyyyyy.com'.  I'm guessing we're supposed to use all one or all the other.

Thanks in advance for the education!

Tom


Yes, the mail server does not have to be called the same as the actual server name. But it often is by default. 

So make sure either you hardcode in the mail server name in myshostname or point it to /etc/mailname and edit that file to the chosen mail server name.

And yes I should be a bit more consistant with the names, however the actual names are up to each person. Also you may want to think of smtp.xxx as postfix only while courier etc could be mail.xxx?

> **ttolliver said:**
> Good evening,

First off, let me start with kudos for an awesome tutorial.  Sure, there may be some rough edges for a lot of us working through it, but I'm an IT geek and appreciate the complexity of what we're pulling off here.  So bravo Flurdy!!!

Okay, now to where I met my personal Waterloo ;~)

I worked through all the install and config, then found a typo when starting services for the first time.  Right now I'm in the beginning of the testing on the step where you telnet to localhost to send an email manually.  I can telnet fine, but I get an "unknown user" error for both the sending and receiving users in /var/log/mail.log when trying to send any email (see below).

I started out trying to send an email from my normal ISP account, but was running into spamhaus related block messages.  So the test you see below is me just trying to email from one local user to another.

At this point I haven't processed a successful email, so I don't have the mail directories in /var/spool/mail/virtual yet.

I've read all of the posts I can find related to "unknown user" errors, but they all seem to be encountered by people much farther along in their testing -- usually around squirrelmail debug.  So those answers don't seem to be pointed at my problem.

Any ideas would be greatly appreciated!

Thanks,
Tom


```

Jan  7 20:47:42 lndwr postfix/cleanup[16770]: 3448D3E1A4: message-id=<20090108024736.3448D3E1A4@mail.sdj.com>
Jan  7 20:47:42 lndwr postfix/qmgr[16765]: 3448D3E1A4: from=<test1@sdj.com>, size=382, nrcpt=1 (queue active)
Jan  7 20:47:42 lndwr postfix/virtual[16776]: 3448D3E1A4: to=<test2@sdj.com>, relay=virtual, delay=15, delays=15/0.01/0/0.01, dsn=5.1.1, status=bounced (unknown user: "test2@sdj.com")
Jan  7 20:47:42 lndwr postfix/cleanup[16770]: DEEE63E1A6: message-id=<20090108024742.DEEE63E1A6@mail.sdj.com>
Jan  7 20:47:42 lndwr postfix/qmgr[16765]: DEEE63E1A6: from=<>, size=2215, nrcpt=1 (queue active)
Jan  7 20:47:42 lndwr postfix/bounce[16773]: 3448D3E1A4: sender non-delivery notification: DEEE63E1A6
Jan  7 20:47:42 lndwr postfix/qmgr[16765]: 3448D3E1A4: removed
Jan  7 20:47:42 lndwr postfix/virtual[16776]: DEEE63E1A6: to=<test1@sdj.com>, relay=virtual, delay=0.03, delays=0.02/0/0/0.01, dsn=5.1.1, status=bounced (unknown user: "test1@sdj.com")
Jan  7 20:47:42 lndwr postfix/qmgr[16765]: DEEE63E1A6: removed

```


Tailing the mysql log "may" be key here.

Either postfix is not talking to mysql at all, or the user is not defined correctly, or postfix mysql config is not correct.

maybe...

---

### Post by mariuxx on 2009-03-18
Hi again, and thanks for your answer, flurdy.
Now I suppose I should explain the following:
I don't have local access to my server. It's hosted by a company run by a friend of mine, he installed the Ubuntu as a VMWare vm, and I use ssh to access it for any purpose. Of course, now it also run Apache, and I can access it through http (if I don't block it with shorewall of course:)), but I don't have local access to the box.
So, if I telnet to localhost in my ssh session, that works fine, unless I specify a port number, in which case I get the message "Unable to connect to remote host: Connection refused". I tried with the actual ip address and localhost, same result.
I can not telnet in, on any port, from the same location I use ssh. Using putty, it never connects, the window just closes without any messages.
I suppose this is not really related to the forum topic, but rather about general telnet(d) setup. But my testing stops at this point until I fix it...

---

### Post by mariuxx on 2009-03-19
Hello again folks.

I have managed now to send emails to my server, and they get delivered in the right mailboxes. That's just fantastic!

But it seems that the clamav module isn't working as it should.
Anyone knows a remedy for this?


Mar 19 20:15:45 ubuntu amavis[14003]: (14003-04) ClamAV-clamd: Can't send to socket /var/run/clamav/clamd.ctl: 107, retrying (1)
Mar 19 20:15:46 ubuntu amavis[14003]: (14003-04) (!)ClamAV-clamd: Can't connect to UNIX socket /var/run/clamav/clamd.ctl: No such file or directory, retrying (2)
Mar 19 20:15:52 ubuntu amavis[14003]: (14003-04) (!!)ClamAV-clamd av-scanner FAILED: run_av error: Too many retries to talk to /var/run/clamav/clamd.ctl (Can't connect to UNIX socket /var/run/clamav/clamd.ctl: No such file or directory) at (eval 98) line 309.

Thanx in advance

M

---

### Post by CaptainMorgan on 2009-03-22
Flurdy, this is a superb tutorial- the amount of depth you go into is phenomenal.  Thank you for your hard work.

I had a similar issue as another fellow upon the basic setup portion and then the testing of it- I get "..connection refused." upon attempting to telnet to it, both locally and remotely.  Unless I missed something, is it possible my ISP is blocking the port completely?  I'll probably make a call to them on Monday but I wanted to try this tutorial out this weekend and hopefully get some replies and/or do more research... and besides, I thought relay_hosts would solve the blocked port issue... unless I have it confused.  Any thoughts?

EDIT 1
Also, it is wise to be doing this on a development/serving rig?  My server runs more than a few websites(virtually), but maybe because of load I'm thinking I should use a spare older system I have to be solely a mail server... google searching for "benefits of a mail server" and different variations turned up commercial avenues; not what I'm looking for...

EDIT 2
Ok, so I called Comcast and was told to use 587, so I opened up that port on the router and I still received "....connection refused."  Back to the drawing board I guess... unless anyone has any suggestions...

---

### Post by CommodoreTeach on 2009-03-25
Hi all!

I'm new(ish) to linux, but really new to linux servers.  I'm setting up the server mostly to be a mailman server, but originally it was going to be much more robust than that, so I started with and got to be comfortable with this guide.

I'm having a problem with SASL authentication, I think it has to do with the passwords not matching from the crypt command in MySQL.  I tried the script that Proddy suggested in post 183, but that didn't seem to help either.  However, there is the possibility that I am not doing something correctly.  I ran it using "./vcrypt <password>" (replacing all of <password> with the real password) and then copy/pasted the result into the MySQL database. I then tried to send a mail through it and I got:

```
postfix/smtpd[5508]: warning: computer.domain[IP]: SASL LOGIN authentication failed: authentication failure
```

The only thing that seems to allow me to authenticate is if I put the passwords in plain text in the mail database.  I don't really like that option, and so I was wondering what the alternatives were.  I've been stumped on this for the last few days, and I haven't found any solution that works while keeping the passwords in the database encrypted (and not having to manually add the users to the sasldb2).  I have included the saslfinger -s output below (or as much of it was in the buffer of the ssh program I use).  Thanks in advance for any help or critique of the setup! :-)

saslfinger -c output:
```

-- smtpd is linked to --
        libsasl2.so.2 => /usr/lib/libsasl2.so.2 (0xb7ced000)

-- active SMTP AUTH and TLS parameters for smtpd --
broken_sasl_auth_clients = yes
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = foo.domain.com
smtpd_sasl_path = smtpd
smtpd_sasl_security_options = noanonymous
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_loglevel = 2
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s


-- listing of /usr/lib/sasl2 --
total 864
drwxr-xr-x  2 root root  4096 2009-03-24 14:01 .
drwxr-xr-x 54 root root 20480 2009-03-17 09:11 ..
-rw-r--r--  1 root root 13860 2008-10-10 10:40 libanonymous.a
-rw-r--r--  1 root root   988 2008-10-10 10:39 libanonymous.la
-rw-r--r--  1 root root 13752 2008-10-10 10:40 libanonymous.so
-rw-r--r--  1 root root 13752 2008-10-10 10:40 libanonymous.so.2
-rw-r--r--  1 root root 13752 2008-10-10 10:40 libanonymous.so.2.0.22
-rw-r--r--  1 root root 16382 2008-10-10 10:40 libcrammd5.a
-rw-r--r--  1 root root   974 2008-10-10 10:39 libcrammd5.la
-rw-r--r--  1 root root 17848 2008-10-10 10:40 libcrammd5.so
-rw-r--r--  1 root root 17848 2008-10-10 10:40 libcrammd5.so.2
-rw-r--r--  1 root root 17848 2008-10-10 10:40 libcrammd5.so.2.0.22
-rw-r--r--  1 root root 47752 2008-10-10 10:40 libdigestmd5.a
-rw-r--r--  1 root root   997 2008-10-10 10:39 libdigestmd5.la
-rw-r--r--  1 root root 46828 2008-10-10 10:40 libdigestmd5.so
-rw-r--r--  1 root root 46828 2008-10-10 10:40 libdigestmd5.so.2
-rw-r--r--  1 root root 46828 2008-10-10 10:40 libdigestmd5.so.2.0.22
-rw-r--r--  1 root root 13902 2008-10-10 10:40 liblogin.a
-rw-r--r--  1 root root   968 2008-10-10 10:39 liblogin.la
-rw-r--r--  1 root root 13748 2008-10-10 10:40 liblogin.so
-rw-r--r--  1 root root 13748 2008-10-10 10:40 liblogin.so.2
-rw-r--r--  1 root root 13748 2008-10-10 10:40 liblogin.so.2.0.22
-rw-r--r--  1 root root 30316 2008-10-10 10:40 libntlm.a
-rw-r--r--  1 root root   962 2008-10-10 10:39 libntlm.la
-rw-r--r--  1 root root 30196 2008-10-10 10:40 libntlm.so
-rw-r--r--  1 root root 30196 2008-10-10 10:40 libntlm.so.2
-rw-r--r--  1 root root 30196 2008-10-10 10:40 libntlm.so.2.0.22
-rw-r--r--  1 root root 14222 2008-10-10 10:40 libplain.a
-rw-r--r--  1 root root   968 2008-10-10 10:39 libplain.la
-rw-r--r--  1 root root 17844 2008-10-10 10:40 libplain.so
-rw-r--r--  1 root root 17844 2008-10-10 10:40 libplain.so.2
-rw-r--r--  1 root root 17844 2008-10-10 10:40 libplain.so.2.0.22
-rw-r--r--  1 root root 22394 2008-10-10 10:40 libsasldb.a
-rw-r--r--  1 root root   999 2008-10-10 10:39 libsasldb.la
-rw-r--r--  1 root root 21804 2008-10-10 10:40 libsasldb.so
-rw-r--r--  1 root root 21804 2008-10-10 10:40 libsasldb.so.2
-rw-r--r--  1 root root 21804 2008-10-10 10:40 libsasldb.so.2.0.22
-rw-r--r--  1 root root 24156 2008-10-10 10:40 libsql.a
-rw-r--r--  1 root root  1097 2008-10-10 10:39 libsql.la
-rw-r--r--  1 root root 26064 2008-10-10 10:40 libsql.so
-rw-r--r--  1 root root 26064 2008-10-10 10:40 libsql.so.2
-rw-r--r--  1 root root 26064 2008-10-10 10:40 libsql.so.2.0.22
-rw-r--r--  1 root root   259 2009-03-24 14:44 smtpd.conf

-- listing of /etc/postfix/sasl --
total 12
drwxr-xr-x 2 root root 4096 2009-03-03 15:25 .
drwxr-xr-x 3 root root 4096 2009-03-03 17:17 ..
-rw-r--r-- 1 root root  259 2009-03-24 14:45 smtpd.conf




-- content of /usr/lib/sasl2/smtpd.conf --
pwcheck_method: auxprop
auxprop_plugin: sql
mech_list: plain login cram-md5 digest-md5
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: --- replaced ---
sql_passwd: --- replaced ---
sql_database: maildb
sql_select: select clear from users where id='%u@%r' and enabled = 1

-- content of /etc/postfix/sasl/smtpd.conf --
pwcheck_method: auxprop
auxprop_plugin: sql
mech_list: plain login cram-md5 digest-md5
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: --- replaced ---
sql_passwd: --- replaced ---
sql_database: maildb
sql_select: select clear from users where id='%u@%r' and enabled = 1

-- content of /etc/postfix/sasl/smtpd.conf --
pwcheck_method: auxprop
auxprop_plugin: sql
mech_list: plain login cram-md5 digest-md5
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: --- replaced ---
sql_passwd: --- replaced ---
sql_database: maildb
sql_select: select clear from users where id='%u@%r' and enabled = 1


-- active services in /etc/postfix/master.cf --
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
smtp      inet  n       -       n       -       -       smtpd
submission inet n       -       n       -       -       smtpd
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_tls_auth_only=yes
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject_unauth_destination,reject
  -o smtpd_sasl_security_options=noanonymous,noplaintext
  -o smtpd_sasl_tls_security_options=noanonymous
smtps     inet  n       -       n       -       -       smtpd -v
  -o smtpd_tls_wrappermode=yes
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_tls_auth_only=yes
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
  -o smtpd_sasl_security_options=noanonymous,noplaintext
  -o smtpd_sasl_tls_security_options=noanonymous
pickup    fifo  n       -       -       60      1       pickup
  -o content_filter=
  -o receive_override_options=no_header_body_checks
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
proxywrite unix -       -       n       -       1       proxymap
smtp      unix  -       -       -       -       -       smtp
relay     unix  -       -       -       -       -       smtp
        -o smtp_fallback_relay=
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix  -       n       n       -       2       pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list
  argv=/usr/lib/mailman/bin/postfix-to-mailman.py ${nexthop} ${user}
amavis    unix  -       -       -       -       2       smtp
  -o smtp_data_done_timeout=1200
  -o smtp_send_xforward_command=yes
  -o disable_dns_lookups=yes
  -o max_use=20
127.0.0.1:10025 inet n  -       -       -       -       smtpd
  -o content_filter=
  -o local_recipient_maps=
  -o relay_recipient_maps=
  -o smtpd_restriction_classes=
  -o smtpd_delay_reject=no
  -o smtpd_client_restrictions=permit_mynetworks,reject
  -o smtpd_helo_restrictions=
  -o smtpd_sender_restrictions=
  -o smtpd_recipient_restrictions=permit_mynetworks,reject
  -o smtpd_data_restrictions=reject_unauth_pipelining
  -o smtpd_end_of_data_restrictions=
  -o mynetworks=127.0.0.0/8
  -o smtpd_error_sleep_time=0
  -o smtpd_soft_error_limit=1001
  -o smtpd_hard_error_limit=1000
  -o smtpd_client_connection_count_limit=0
  -o smtpd_client_connection_rate_limit=0
  -o receive_override_options=no_header_body_checks,no_unknown_recipient_checks

-- mechanisms on localhost --
250-AUTH PLAIN CRAM-MD5 DIGEST-MD5 LOGIN
250-AUTH=PLAIN CRAM-MD5 DIGEST-MD5 LOGIN


-- end of saslfinger output --


```

---

### Post by fusa on 2009-03-25
In your example located at: [http://flurdy.com/docs/postfix/#data](http://flurdy.com/docs/postfix/#data) 

INSERT INTO users (id,name,maildir,clear) VALUES ('xandros@blobber.org','xandros','xandros/', encrypt('apassword') ), ('vivita@blobber.org','vivita','vivita/', encrypt('anotherpassword') );


should the maildir,clear)  actually be maildir,crypt)  It looks like your inserting the encrypted password into the clear text field.

---

### Post by Adriano1980 on 2009-04-04
Hello Forum,
This is a really grate tutorial  however is was wondering what the  fields `procmailrc` , `spamassassinrc`  are and how I can use them. ant the quota  field is it for courier and how i can use the quota ?
Thank you  for  clarification 
Adriano

---

### Post by sTo0z on 2009-04-28
flurdy,

I was wondering what you're advice would be on the best way to back this system up.  

I am not knowledgeable so the best solution I can think of is to maybe rsync each user's folder and then dump the mysql data... is that what you would do?

I'm sure there's something better out there, I just don't know what it is.. I don't really know how I would back up the whole thing.

Any and all help is appreciated, thank you!  

PS - Awesome guide, I followed your guide from 6.06 awhile back and the email server is still chugging along perfectly.  I was a hero at work thanks to you. ;)

---

### Post by Villu on 2009-05-12
This usually happens when the smtpd.conf file can not be found. If you're running Postfix 2.3, removing (commenting out) the smtpd_sasl_path in the main.cf file should fix the problem. This is because 2.3 has changed the way it looks for the file and now automatically prepends /etc/postfix/sasl/ and appends .conf, so smtpd could also be a valid value.

> **thelucster said:**
> Thanks for the guide, very useful, however I am having some issues setting up SMTP authentication. I have followed the instructions to a t, but am unable to authenticate.

In /var/log/auth.log I get:

```
Feb 18 14:28:06 stackednotion postfix/smtpd[3920]: sql_select option missing
Feb 18 14:28:06 stackednotion postfix/smtpd[3920]: auxpropfunc error no mechanism available 
Feb 18 14:28:06 stackednotion postfix/smtpd[3920]: _sasl_plugin_load failed on sasl_auxprop_plug_init for plugin: sql 

```Here is my /etc/postfix/sasl/smtpd.conf:

```
pwcheck_method: auxprop
auxprop_plugin: sql
mech_list: plain login cram-md5 digest-md5
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: mail
sql_passwd: blah
sql_database: mail
sql_select: select clear from users where id='%u@%r' and enabled = 1
```Any ideas, it sounds as if it can't find the SQL plugin, but it is definately installed:

```
# apt-get install libsasl2-modules-sql libgsasl7 libauthen-sasl-cyrus-perl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libsasl2-modules-sql is already the newest version.
libgsasl7 is already the newest version.
libauthen-sasl-cyrus-perl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```I am running 64bit 8.04.

Regards,

Luca Spiller

---

### Post by Villu on 2009-05-12
Try commenting out the line.

> **NerdWorld said:**
> Has anybody seen this error?

warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: No such file or directory



I think I have the proper path variable to find smtpd.conf
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2



As far as I know, I'm not supposed to be using a the Berkely db.  Correct?

This is preventing me from logging in (although everything else works fine!)

TIA!

---

### Post by slipstream180 on 2009-05-12
Flurdy: great tutorial! This is the most complete tutorial I've seen out there - thank you so much for putting the time and effort into this.

My issue has to do with getting bounced emails when using a relayhost. I've added this wrinkle to the Postfix config to circumvent the SPAM suppression my ISP (& which most good ones do) on port 25. Unfortunately, one side-effect of my attempt is that my configuration is auto-forwarding any incoming emails to my forwarding service. What am I doing wrong?

Here's the mail log output:
```

May 11 16:39:00 mail postfix/smtpd[25335]: connect from n54.bullet.mail.sp1.yahoo.com[98.136.44.32]
May 11 16:39:01 mail postfix/smtpd[25335]: 0E33218880A: client=n54.bullet.mail.sp1.yahoo.com[98.136.44.32]
May 11 16:39:01 mail postfix/cleanup[25330]: 0E33218880A: message-id=<783351.26703.qm@web45303.mail.sp1.yahoo.com>
May 11 16:39:01 mail postfix/qmgr[25118]: 0E33218880A: from=<user@yahoo.com>, size=2613, nrcpt=1 (queue active)
May 11 16:39:01 mail amavis[2631]: (02631-19) ESMTP::10024 /var/lib/amavis/tmp/amavis-20090506T093443-02631: <user@yahoo.com> -> <testuser@example.c> SIZE=2613 Received: from mail.example.com ([127.0.0.1]) by localhost (mail.example.com [127.0.0.1]) (amavisd-new, port 10024) with ESMTP for <testuser@example.c>; Mon, 11 May 2009 16:39:01 -0700 (PDT)
May 11 16:39:01 mail postfix/smtpd[25335]: disconnect from n54.bullet.mail.sp1.yahoo.com[98.136.44.32]
May 11 16:39:01 mail amavis[2631]: (02631-19) smtp connection cache, dt: 154.9, state: 0
May 11 16:39:01 mail amavis[2631]: (02631-19) dkim: VALID Author+Sender+MailFrom signature by i=@yahoo.com, From: <user@yahoo.com>, a=rsa-sha256, c=relaxed/relaxed, s=s1024, d=yahoo.com
May 11 16:39:01 mail amavis[2631]: (02631-19) dkim: VALID Author+Sender+MailFrom signature by i=user@yahoo.com, From: <user@yahoo.com>, a=rsa-sha1, c=nofws, s=s1024, d=yahoo.com
May 11 16:39:01 mail amavis[2631]: (02631-19) Checking: UNH1HEO39P8B [98.136.44.32] <user@yahoo.com> -> <testuser@example.c>
May 11 16:39:01 mail amavis[2631]: (02631-19) p003 1 Content-Type: multipart/alternative
May 11 16:39:01 mail amavis[2631]: (02631-19) p001 1/1 Content-Type: text/plain, size: 9 B, name: 
May 11 16:39:01 mail amavis[2631]: (02631-19) p002 1/2 Content-Type: text/html, size: 127 B, name: 
May 11 16:39:01 mail postfix/smtpd[25332]: connect from localhost[127.0.0.1]
May 11 16:39:01 mail postfix/smtpd[25332]: 5770B188810: client=localhost[127.0.0.1]
May 11 16:39:01 mail postfix/cleanup[25330]: 5770B188810: message-id=<783351.26703.qm@web45303.mail.sp1.yahoo.com>
May 11 16:39:01 mail postfix/qmgr[25118]: 5770B188810: from=<user@yahoo.com>, size=3239, nrcpt=1 (queue active)
May 11 16:39:01 mail postfix/smtpd[25332]: disconnect from localhost[127.0.0.1]
May 11 16:39:01 mail amavis[2631]: (02631-19) FWD via SMTP: <user@yahoo.com> -> <testuser@example.c>,BODY=7BIT 250 2.0.0 Ok, id=02631-19, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 5770B188810
May 11 16:39:01 mail amavis[2631]: (02631-19) Passed CLEAN, [98.136.44.32] [64.9.232.205] <user@yahoo.com> -> <testuser@example.c>, Message-ID: <783351.26703.qm@web45303.mail.sp1.yahoo.com>, mail_id: UNH1HEO39P8B, Hits: -, size: 2610, queued_as: 5770B188810, dkim_id=@yahoo.com,user@yahoo.com, 340 ms
May 11 16:39:01 mail postfix/smtp[25331]: 0E33218880A: to=<testuser@example.c>, orig_to=<testuser@example.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=0.79, delays=0.43/0/0.01/0.35, dsn=2.0.0, status=sent (250 2.0.0 Ok, id=02631-19, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 5770B188810)
May 11 16:39:01 mail postfix/qmgr[25118]: 0E33218880A: removed
May 11 16:39:01 mail amavis[2631]: (02631-19) TIMING [total 358 ms] - SMTP greeting: 3 (1%)1, SMTP EHLO: 2 (0%)1, SMTP pre-MAIL: 2 (1%)2, SMTP pre-DATA-flush: 4 (1%)3, SMTP DATA: 33 (9%)13, check_init: 2 (1%)13, digest_hdr: 62 (17%)30, digest_body_dkim: 4 (1%)32, gen_mail_id: 9 (3%)34, mime_decode: 33 (9%)43, get-file-type2: 21 (6%)49, parts_decode: 0 (0%)49, check_header: 5 (1%)51, update_cache: 3 (1%)52, decide_mail_destiny: 1 (0%)52, fwd-connect: 50 (14%)66, fwd-mail-pip: 6 (2%)67, fwd-rcpt-pip: 1 (0%)68, fwd-data-chkpnt: 0 (0%)68, write-header: 3 (1%)69, fwd-data-contents: 0 (0%)69, fwd-end-chkpnt: 41 (11%)80, prepare-dsn: 7 (2%)82, main_log_entry: 51 (14%)96, update_snmp: 5 (1%)98, SMTP pre-response: 1 (0%)98, SMTP response: 2 (0%)98, unlink-2-files: 1 (0%)99, rundown: 5 (1%)100
May 11 16:39:01 mail CRON[25337]: pam_unix(cron:session): session opened for user root by (uid=0)
May 11 16:39:01 mail dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.43" (uid=1000 pid=4498 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.760" (uid=0 pid=25337 comm="/USR/SBIN/CRON "))
May 11 16:39:01 mail /USR/SBIN/CRON[25344]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
May 11 16:39:01 mail CRON[25337]: pam_unix(cron:session): session closed for user root
May 11 16:39:02 mail postfix/smtp[25333]: 5770B188810: to=<testuser@example.c>, relay=outbound.mailhop.org[204.13.248.71]:2525, delay=0.88, delays=0.04/0/0.73/0.11, dsn=5.0.0, status=bounced (host outbound.mailhop.org[204.13.248.71] said: 550 testuser@example.c failed recipient verification (in reply to RCPT TO command))
May 11 16:39:02 mail postfix/cleanup[25330]: 502DE188811: message-id=<20090511233902.502DE188811@mail.example.com>
May 11 16:39:02 mail postfix/qmgr[25118]: 502DE188811: from=<>, size=5292, nrcpt=1 (queue active)
May 11 16:39:02 mail postfix/bounce[25334]: 5770B188810: sender non-delivery notification: 502DE188811
May 11 16:39:02 mail postfix/qmgr[25118]: 5770B188810: removed
May 11 16:39:03 mail postfix/smtp[25333]: 502DE188811: to=<user@yahoo.com>, relay=outbound.mailhop.org[204.13.248.71]:2525, delay=1.1, delays=0.01/0/0.7/0.41, dsn=2.0.0, status=sent (250 OK id=1M3f5L-0000uK-2h)
May 11 16:39:03 mail postfix/qmgr[25118]: 502DE188811: removed

```

Next the result of postconf -n:

```

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_at_myorigin = no
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
content_filter = amavis:[127.0.0.1]:10024
delay_warning_time = 4h
disable_vrfy_command = yes
inet_interfaces = all
local_recipient_maps = 
mailbox_size_limit = 0
masquerade_domains = example.com
masquerade_exceptions = root
maximal_backoff_time = 8000s
maximal_queue_lifetime = 3d
minimal_backoff_time = 1000s
mydestination = 
mydomain = example.com
myhostname = mail.example.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mynetworks_style = host
myorigin = $mydomain
readme_directory = no
recipient_delimiter = +
relayhost = outbound.mailhop.org:2525
smtp_helo_timeout = 60s
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_password
smtp_sasl_security_options = 
smtp_tls_CAfile = /etc/ssl/certs/Equifax_Secure_CA.pem
smtp_tls_note_starttls_offer = yes
smtp_tls_security_level = may
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsblnjabl.org
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_delay_reject = yes
smtpd_hard_error_limit = 12
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
smtpd_recipient_limit = 16
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, permit
smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_soft_error_limit = 3
smtpd_tls_cert_file = /etc/postfix/postfix.cert
smtpd_tls_key_file = /etc/postfix/postfix.key
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
tls_random_source = dev:/dev/urandom
unknown_local_recipient_reject_code = 450
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf

```

A few notes about my configuration/environment. I am using a home router w/ my own domain name (example.com). The mail server (mail.example.com) is running on Ubuntu 9.04 behind the home router. The router is set up to forward all of the relevant ports to the Ubuntu server. (Port 25 for SMTP and 143 for IMAP) 

Also, I've checked my router and DNS records against the documentation, and I think I've got the MX records set up properly. (not totally confident there...) I've tested the setup externally, using mxtools. ([http://www.mxtoolbox.com/](http://www.mxtoolbox.com/) a very helpful tool!) Everything there checks out, except its attempt to telnet into mail.example.com. Here's the result:

```
May 11 16:24:17 mail postfix/smtpd[25121]: connect from mxtb-pws1.mxtoolbox.com[64.20.227.131]
May 11 16:24:18 mail postfix/smtpd[25121]: NOQUEUE: reject: RCPT from mxtb-pws1.mxtoolbox.com[64.20.227.131]: 554 5.7.1 <test@mxtoolbox.com>: Relay access denied; from=<test@mxtoolbox.com> to=<test@mxtoolbox.com> proto=SMTP helo=<please-read-policy.mxtoolbox.com>
May 11 16:24:18 mail postfix/smtpd[25121]: disconnect from mxtb-pws1.mxtoolbox.com[64.20.227.131]
```

Not sure if this has anything to do w/ my issue, but maybe it will provide some clues...

Thanks for the help, in advance.

Cheers!

---

### Post by slipstream180 on 2009-05-13
OK. Problem solved.

As it turns out, this problem has nothing to do with the configuration files listed above. Instead, I had the [email]user@example.com[/email] account self-referenced in the MySQL aliases table like this:

```

pkid          mail                           destination                 enabled
1        user@example.com  user@example.com              1

```

So, the Postfix virtual mail delivery system was finding this erroneous entry in the 'aliases' table and then forwarding it on. 

Hope this helps someone in the future!

---

### Post by Villu on 2009-05-14
Thanks for a great tutorial, Flurdy!

I have managed to complement Flurdy's tutorial such that virtual transport is swapped for maildrop and spam is automatically delivered to a spam folder.

It is based on the excellent tutorial by Flurdy and complemented by parts of the tutorial found here: [http://daemonforums.org/showthread.php?t=193](http://daemonforums.org/showthread.php?t=193)

The latter tutorial also contains methods to implement vacation messaging.

If in doubt, check out the forementioned tutorial.

Here's what I did:

Complete Flurdy's tutorial and install maildrop

uncomment in main.cf:
```
transport_maps = mysql:/etc/postfix/mysql_transport.cf
```and add
```
maildrop_destination_recipient_limit = 1
```Master.cf file should contain the following line, change the user field to virtual:
```
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=virtual argv=/usr/bin/maildrop -d ${recipient}
```create mysql_transport.cf file and set the correct owner and permissions:
```
user=mail
password=changeme
dbname=maildb
table=domains
select_field=transport
where_field=domain
hosts=127.0.0.1
additional_conditions = and enabled = 1
```
create:
```
# cd /var/spool/mail/virtual/
# chmod +s /usr/bin/maildrop
# touch .mailfilter
# chmod 600 .mailfilter
# mkdir mailfilters
# chmod 700 mailfilters
# chown -R virtual:virtual .mailfilter mailfilters
```test maildrop and check logs:
```
echo "test" | maildrop -V 9 -d you@example.com
```Edit the ...virtual/.mailfilter file (haven't tested this bit):
```
# Deliver to Inbox or Spam box (create spam box if it does not exist)
if (/^X-Spam-Flag: YES/:h)
{
    `test -d $DEFAULT/.junkmail`
    if ($RETURNCODE == 1)
    {
        `/usr/bin/maildirmake -f junkmail $DEFAULT`
        `echo "junkmail" >> $DEFAULT/subscriptions`
    }
    exception {
        to "$DEFAULT/.junkmail"
    }
    # if all else fails, do regular delivery
    exception {
        to "$DEFAULT"
    }
}

```Now use phpmyadmin and change domain transport field from "virtual:" to "maildrop:"

Restart postfix, check log files and pray :)

Much of the code here is curtesy of hamba from daemonforums.org

Hope this helps!

Cheers, Villu

---

### Post by flurdy on 2009-05-28
> **fusa said:**
> In your example located at: [http://flurdy.com/docs/postfix/#data](http://flurdy.com/docs/postfix/#data) 

INSERT INTO users (id,name,maildir,clear) VALUES ('xandros@blobber.org','xandros','xandros/', encrypt('apassword') ), ('vivita@blobber.org','vivita','vivita/', encrypt('anotherpassword') );


should the maildir,clear)  actually be maildir,crypt)  It looks like your inserting the encrypted password into the clear text field.


Umm, yes good point. :)

---

### Post by flurdy on 2009-05-28
> **sTo0z said:**
> flurdy,

I was wondering what you're advice would be on the best way to back this system up.  

I am not knowledgeable so the best solution I can think of is to maybe rsync each user's folder and then dump the mysql data... is that what you would do?

I'm sure there's something better out there, I just don't know what it is.. I don't really know how I would back up the whole thing.

Any and all help is appreciated, thank you!  

PS - Awesome guide, I followed your guide from 6.06 awhile back and the email server is still chugging along perfectly.  I was a hero at work thanks to you. ;)


I (very briefly) do mention backing up in this section:
[http://flurdy.com/docs/postfix/index.html#ext_back](http://flurdy.com/docs/postfix/index.html#ext_back)
But there probably are other more elaborate solutions to this, and mine may have some integrety or security issue. But that is all I do, and it works.

Good to hear the server is still working, and you got some cred for it!

---

### Post by flurdy on 2009-05-28
> **mariuxx said:**
> Hi again, and thanks for your answer, flurdy.
Now I suppose I should explain the following:
I don't have local access to my server. It's hosted by a company run by a friend of mine, he installed the Ubuntu as a VMWare vm, and I use ssh to access it for any purpose. Of course, now it also run Apache, and I can access it through http (if I don't block it with shorewall of course:)), but I don't have local access to the box.
So, if I telnet to localhost in my ssh session, that works fine, unless I specify a port number, in which case I get the message "Unable to connect to remote host: Connection refused". I tried with the actual ip address and localhost, same result.
I can not telnet in, on any port, from the same location I use ssh. Using putty, it never connects, the window just closes without any messages.
I suppose this is not really related to the forum topic, but rather about general telnet(d) setup. But my testing stops at this point until I fix it...

I think you managed to solve most of these by your follow up post afterwards, but to clarify to others in the future:

Local physical access is not an issue, when I say locally I mean in a shell session on the mail server. Whether that is via SSH or login screen, is irrelevant to me.

Secondly when I mean telnetting it has nothing to do with telnetd. You are simple testing if the ports are open, and you can send SMTP/IMAP commands via telnet on those ports. 

And firstly when testing you need to do this locally. Then external ISP blocking and (usually) firewall issues are irrelevant. If no reply or connectio refused, then basically that service (postfix or whatever) is not running. 

Once local telneting responds okay to everything. Then you can start telnetting remotely. This will then test your firewall and any ISP blocking of ports.

---

### Post by flurdy on 2009-05-28
> **CaptainMorgan said:**
> Flurdy, this is a superb tutorial- the amount of depth you go into is phenomenal.  Thank you for your hard work.

I had a similar issue as another fellow upon the basic setup portion and then the testing of it- I get "..connection refused." upon attempting to telnet to it, both locally and remotely.  Unless I missed something, is it possible my ISP is blocking the port completely?  I'll probably make a call to them on Monday but I wanted to try this tutorial out this weekend and hopefully get some replies and/or do more research... and besides, I thought relay_hosts would solve the blocked port issue... unless I have it confused.  Any thoughts?

EDIT 1
Also, it is wise to be doing this on a development/serving rig?  My server runs more than a few websites(virtually), but maybe because of load I'm thinking I should use a spare older system I have to be solely a mail server... google searching for "benefits of a mail server" and different variations turned up commercial avenues; not what I'm looking for...

EDIT 2
Ok, so I called Comcast and was told to use 587, so I opened up that port on the router and I still received "....connection refused."  Back to the drawing board I guess... unless anyone has any suggestions...


Good to hear you find the howto usefull!

As mentioned in my previous post, regarding testing via telnet and ports: If it is rejected locally then it is you setup that is wrong, not the ISP. If works locally but not remotely, then either your firewall or the ISP is at fault.

Relay host does not solve blocked incomming port. It solves blocked outgoing ports, or use of backup mx for relaying/backup.


Regarding your 1st edit. How you split your servers up is down to your load, preferences and desire to have seperation of concerns.

Obviously it would be nice to have seperate machines/instance for each service. That way things are scalable and more secure. But usually it is not affordable.  You can try it on the same server and see if it is affected by performance. I would think you have to have quite a few hundreds/thousends of users before that becomes an issue.


.. right, think ive used by forum credits for this month... :)

---

### Post by p1nkrubb3rd1ld0 on 2009-06-01
:(

---

### Post by nilton84 on 2009-06-12
thanks to all people that contribute to this forum..

I have a simple question, sorry if Im not to much expert...

is this server configuration let me send email to off-sites? i mean server on internet gmail or hotmail?

thanks i really appreciate your help. my email is [EMAIL="niltonobando@gmail.com"]niltonobando@gmail.com[/EMAIL] if you want to writte.

---

### Post by elfstone2 on 2009-07-27
Hello.. I relly enjoyed doing that tutorial, since its well written, and working nearley perfect.
There is one little typo, it says to start /etc/init.d/shorewall start, and if it works, edit the /etc/shorewall to Startup yes. But it should be the other way round, shorewall wont start, if the Startupflag has not been set to Yes.

Also I really really like to know, how to use procmail with this setup, and i tried to google for it and add it on my own, but up to now i failed.. there are 7 or 8 requests in this thread on how to do this, but no answers.. so if someone could PLEASE answer this, it would help a lot of people.

Thx

---

### Post by rikksullenberger on 2009-08-02
Hi, excellent howto!

I am having a problem with smtp authentication 

I cant seem to get sasl to talk to mysql, I get the following error in the log file:

 warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: No such file or directory


any one have ideas?

Rikk

---

### Post by oziemike on 2009-08-07
As usual Flurdy, this has been a very reliable mail sever for me now for about 3 years!! Still running on Ubuntu 6.06 server with regular normal Ubuntu updates. 

Recently a new and rather dangerous problem cropped up. I went in via phpmyadmin to do some database work and found that phpmyadmin no longer had provision for logging on or off. It just went straight in there!! The login and logout icons were gone and this warning was on the main page:

"Cannot load mysqli extension. Please check your PHP configuration. - Documentation"

Some googling found that these extensions or something has changed with one of the MySQL or PHP updates and I cannot find how to fix it. Obviously anyone could go in and do damage to the db so I have disabled it till I can find some help. Any help would be seriously appreciated.

Mike

---

### Post by Grelf on 2009-08-27
First off, amazing HowTo! I used the original HowTo to run my email for the past number of years, and my machine finally gave up the ghost, so it was time to upgrade her. New hardware, latest ubuntu server OS. Fast like lightening.

I've re-setup the email, and everything except sending out email works. Anytime I try to send email out, it asks me for my password (Even though I'm logged in via imap to get my email), and then it won't let me send email.

Syslog is telling me: 

```
Aug 27 14:42:13 cthulu postfix/smtpd[12613]: warning: foo.net[my.ip]: SASL CRAM-MD5 authentication failed: generic failure
Aug 27 14:42:14 cthulu postfix/smtpd[12613]: warning: foo.net[my.ip]: SASL PLAIN authentication failed: authentication failure
Aug 27 14:42:16 cthulu postfix/smtpd[12613]: warning: foo.net[my.ip]: SASL LOGIN authentication failed: authentication failure

```

Any ideas?

---

### Post by wjase on 2009-09-03
Hi There,

I've got Postfix, POstfix Admin SASL and Courier Pop3 installed.

Having SASL authentication failures for SMTP (but pop works fine)

tried auxprop + sql and pam + sql but no joy either way.

Thought I might try and trace with strace but not sure how to insert the strace command into the execution stream so I can see where saslauthd is trying to run from...

Any advice on how to do this would be appreciated.

Thanks in advance,

Jase

---

### Post by kanngard on 2009-09-06
> **Grelf said:**
> 
I've re-setup the email, and everything except sending out email works. Anytime I try to send email out, it asks me for my password (Even though I'm logged in via imap to get my email), and then it won't let me send email.
Any ideas?
Logged into IMAP is not the same as submitting SMTP mail. You might have to login, depending on your setup. It might help us if you could add the part of your /etc/postfix/main.cf handling the smtpd, i.e. smtpd_recipient_restrictions. It should mention permit_sasl_authenticated.

---

### Post by kanngard on 2009-09-06
Thanks for your great HOWTO, Flurdy! Everything worked on my first try except some minor difficulties, that had nothing to do with your guide! Rather it was of the RTM kind of stuff...

I found some minor typos in the 8th edition, it might be interesting to fix in edition 9. My setup uses Ubuntu Server 9.04.

**Repositories (ClamAV)**
Clamav requires libclamav6 and not libclamav5:
```
sudo aptitude install clamav-base libclamav5 clamav-daemon clamav-freshclam
```
Should be:
```
sudo aptitude install clamav-base libclamav6 clamav-daemon clamav-freshclam
```

**Content Checks (Anti spam & anti virus)**
```
cd /etc/amavis.d/conf.d
```
Should be:
```
cd /etc/amavis/conf.d
```

```
less 05-domain-id
```
Should be:
```
less 05-domain_id
```

```
less 05-node-id
```
Should be:
```
less 05-node_id
```

**Webmail (Enable web access)**
Suggestion for a more complete HOWTO: add a section on how to enable SSL access for Squirrelmail:
```
sudo a2enmod ssl
sudo a2ensite default-ssl

```

---

### Post by wjase on 2009-09-06
Hi Folks,

I found I needed to er "adjust" my /etc/init.d/saslauthd script to set the permissions for the run directory created in the chroot for postfix to 750 (allow the sasl group to execute i believe).

I have the feeling that I need to take a shower as this seems like a slightly unclean thing to do...
But the mails are now coming in and out, and being authenticated as expected from my SQL maps...

---

### Post by ukripper on 2009-09-08
Thanks Flurdy for this howto 8th edition. 

I've successfully setup mail server using Postfix + courier + Squirrelmail (IMAP-SSL) port 993 + mysql following Flurdy's guide. However, i now wish to experiment with roundcube webmail instead of squirrelmail.

I am finding setting up roundcube bit difficult with my current setup. I wonder if anyone has already setup roundcube and can give some tips on how to  enable roundcube with Flurdy's setup? I am getting following database error with roundcube? thanks in advance for any help..
> [B]DATABASE ERROR: CONNECTION FAILED!

Unable to connect to the database!
Please contact your server-administrator.[/B]


---

### Post by ukripper on 2009-09-09
Looks like i have answered my own question!

After struggling for 3 days with roundcube I looked in /var/log/roundcube/errors for any errors and found plenty of below:
```
 DB Error: unable to find package 'MDB2_Driver_mysql' file 'MDB2/Driver/mysql.php' 
```

That means extra dependency needed to be installed to make roundcube work with mysql. So i installed that by ```
[B]sudo apt-get install php-mdb2-driver-mysql
[/B]
```
 and opened roundcube in the browser and voila!!!everything works. No more squirrelmail for me, time for AJAX based webmail.....ROUNDCUBE<<<--------

Thanks Flurdy for your work with setting up mailserver, in future roundcube would be good addition to your guide..keep up with the good work!:guitar:

---

### Post by ukripper on 2009-09-09
Anyone looking for nice roundcube theme and better than outlook 2007 webmail. - MVISION v2.2 [http://www.roundcubethemes.net/news.php?id=6]("http://www.roundcubethemes.net/news.php?id=6")

---

### Post by majstora on 2009-11-11
HI everybody,

I'm following this howto and I get an error:

**chdir Maildir: No such file or directory**

I think the line 
**MYSQL_MAILDIR_FIELD concat(home,'/',maildir)** is not working and courier is setting up the default Maildir which doesn't exists.
When I create a **user** in Mysql and I send an e-mail to it I get the maildir in /var/spool/mail/virtual/**user** with cur/ new/ and tmp/ folders, but when I try to access it with squirrelmail or outlook I get this error.

Is it possible to be a permissions issue?
Any other ideas?  thanks!

---

### Post by flurdy on 2009-11-12
> **oziemike said:**
> As usual Flurdy, this has been a very reliable mail sever for me now for about 3 years!! Still running on Ubuntu 6.06 server with regular normal Ubuntu updates. 

Recently a new and rather dangerous problem cropped up. I went in via phpmyadmin to do some database work and found that phpmyadmin no longer had provision for logging on or off. It just went straight in there!! The login and logout icons were gone and this warning was on the main page:

"Cannot load mysqli extension. Please check your PHP configuration. - Documentation"

Some googling found that these extensions or something has changed with one of the MySQL or PHP updates and I cannot find how to fix it. Obviously anyone could go in and do damage to the db so I have disabled it till I can find some help. Any help would be seriously appreciated.

Mike

So which user did it run against mysql as?

I am personally not comfortable with exposing phpmyadmin to the world either. So I usually restrict it with a .htaccess login, and even sometimes ip restrictions.

---

### Post by flurdy on 2009-11-12
> **ukripper said:**
> Looks like i have answered my own question!

After struggling for 3 days with roundcube I looked in /var/log/roundcube/errors for any errors and found plenty of below:
```
 DB Error: unable to find package 'MDB2_Driver_mysql' file 'MDB2/Driver/mysql.php' 
```

That means extra dependency needed to be installed to make roundcube work with mysql. So i installed that by ```
[B]sudo apt-get install php-mdb2-driver-mysql
[/B]
```
 and opened roundcube in the browser and voila!!!everything works. No more squirrelmail for me, time for AJAX based webmail.....ROUNDCUBE<<<--------

Thanks Flurdy for your work with setting up mailserver, in future roundcube would be good addition to your guide..keep up with the good work!:guitar:


If someone writes a roundcube howto extension to my postfix howto I would be happy to link to it. ;)

---

### Post by flurdy on 2009-11-12
> **kanngard said:**
> Thanks for your great HOWTO, Flurdy! Everything worked on my first try except some minor difficulties, that had nothing to do with your guide! Rather it was of the RTM kind of stuff...

I found some minor typos in the 8th edition, it might be interesting to fix in edition 9. My setup uses Ubuntu Server 9.04.

**Repositories (ClamAV)**
Clamav requires libclamav6 and not libclamav5:
```
sudo aptitude install clamav-base libclamav5 clamav-daemon clamav-freshclam
```
Should be:
```
sudo aptitude install clamav-base libclamav6 clamav-daemon clamav-freshclam
```

**Content Checks (Anti spam & anti virus)**
```
cd /etc/amavis.d/conf.d
```
Should be:
```
cd /etc/amavis/conf.d
```

```
less 05-domain-id
```
Should be:
```
less 05-domain_id
```

```
less 05-node-id
```
Should be:
```
less 05-node_id
```

**Webmail (Enable web access)**
Suggestion for a more complete HOWTO: add a section on how to enable SSL access for Squirrelmail:
```
sudo a2enmod ssl
sudo a2ensite default-ssl

```

Cheers!

Fixed the typos.

---

### Post by Incubusaurus on 2009-12-08
I've just finished going through the 9th edition of **How to set up a mail server on a GNU / Linux system** and thought I'd share a few things that I found.

First, it's a great tutorial, and I didn't have many problems.  Thanks Flurdy.  But there were some problems, and some things worth mentioning:

**Section MTA Postfix**

With this setting in *main.cf*

```
mynetworks_style = host
```I was unable to connect to the server from my email client, which is on another computer on the same subnet.  This setting restricts trusted clients to the server itself.  With this setting in place, if you attempt to use the server as your SMTP server from a client on the same subnet, you will probably receive this error in the logs:

[FONT=Courier New]554 5.7.1 <email address here>: Relay access denied;[/FONT]

Note also that if [FONT=Courier New]mynetworks[/FONT] is also set in *main.cf*, this will override [FONT=Courier New]mynetworks_style[/FONT]:

```
mynetworks = 192.168.1.0/24 # overrides mynetworks_style
mynetworks_style = host # overridden bt mynetworks
```To resolve the problem, either specify your subnet in [FONT=Courier New]mynetworks[/FONT], and comment out (or remove) [FONT=Courier New]mynetworks_style[/FONT]:

```
mynetworks = 192.168.1.0/24
#mynetworks_style = host
```Or, comment out (or remove) [FONT=Courier New]mynetworks[/FONT], and change [FONT=Courier New]mynetworks_style[/FONT] to [FONT=Courier New]subnet[/FONT]:

```
#mynetworks = 192.168.1.0/24
mynetworks_style = subnet
```For more information, see:
[http://www.postfix.org/postconf.5.html#mynetworks](http://www.postfix.org/postconf.5.html#mynetworks)
[http://www.postfix.org/postconf.5.html#mynetworks_style](http://www.postfix.org/postconf.5.html#mynetworks_style)

There is the following entry in *main.cf*:

```
maximal_queue_lifetime = 7d
```That's fine as it stands, but if you lower that value to less than the value of bounce_queue_lifetime (default 5d), then you will receive a warning in the log.  I changed mine to 3d, so had to insert bounce_queue_lifetime at 3d as well:

```
maximal_queue_lifetime = 3d
bounce_queue_lifetime = 3d

```

For more information, see:
[http://www.postfix.org/postconf.5.html#maximal_queue_lifetime](http://www.postfix.org/postconf.5.html#maximal_queue_lifetime)
[http://www.postfix.org/postconf.5.html#bounce_queue_lifetime](http://www.postfix.org/postconf.5.html#bounce_queue_lifetime)

**Section Anti Virus Postgrey**

In the section on enabling Postgrey, the port 10023 is shown.  It should be 60000.

Incorrect:

```
smtpd_recipient_restrictions =[INDENT]reject_unauth_pipelining, permit_mynetworks,
permit_sasl_authenticated, reject_non_fqdn_recipient,
reject_unknown_recipient_domain, reject_unauth_destination,
check_policy_service inet:127.0.0.1:10023, permit[/INDENT]
```Correct:

```
smtpd_recipient_restrictions =[INDENT]reject_unauth_pipelining, permit_mynetworks,
 permit_sasl_authenticated, reject_non_fqdn_recipient,
reject_unknown_recipient_domain, reject_unauth_destination,
check_policy_service inet:127.0.0.1:60000, permit[/INDENT]
```Alternatively, you can edit the value in */etc/default/postgrey*:

```
POSTGREY_OPTS="--inet=127.0.0.1:60000"
```**Testing**

Before starting the configuration of Amavis-new, I suggest reading the following document:

[http://www.ijs.si/software/amavisd/README.postfix](http://www.ijs.si/software/amavisd/README.postfix)

It contains more detialed information on configuring and testing Amavis-new, and helped me debug an issue that I encountered.

That's all for now.  I hope this helps someone.

---

### Post by flurdy on 2009-12-10
> **flurdy said:**
> If someone writes a roundcube howto extension to my postfix howto I would be happy to link to it. ;)

Ps. [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/) now includes roundcube section as ive started using roundcube myself....

---

### Post by ukripper on 2009-12-10
> **flurdy said:**
> Ps. [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/) now includes roundcube section as ive started using roundcube myself....

Welldone mate! good job

---

### Post by q.dinar on 2009-12-27
hello. i am going to install mail server to ubuntu 9.10 desktop. now i cannot install postfix without errors. when postfix is being installed this is in syslog:
Dec 27 17:59:18 dinar-desktop postfix/sendmail[13386]: fatal: execv /usr/sbin/postalias: No such file or directory
>22:51 utc+3 : solved , asked in #ubuntu to try install, one person said that it works, then i have tried to set one related apparmor profile to complain mode and there is other error now , #1 , was #75 as i remember.<
i check:
which execv
and it says nothing. i find in synaptic that it is in snoopy package.>21:33 utc+3 : i have been mistaken/i am mistaken, in snoopy is not that file. even may be execv is not file but function , so /usr/sbin/postalias does not exist? why ? as i know it is in postfix package. < if i check it to install i see:
depends on ld.so.preload-manager (>=0.1) but it is not installable.
why so? i have searched for it in web and have found:
[http://packages.ubuntu.com/dapper/all/ld.so.preload-manager/download](http://packages.ubuntu.com/dapper/all/ld.so.preload-manager/download)
[https://launchpad.net/ubuntu/+source/ld.so.preload-manager](https://launchpad.net/ubuntu/+source/ld.so.preload-manager)

also i have installed extra apparmor profiles and enabled postfix profiles and it blocked up some things on installation and uninstallation, but i have fixed profiles. added to /usr/sbin/sendmail profile:
```
/etc/mailname r,
```
>2009-12-28 17:50 utc+3 : and also this profile should be in complain mode during install and then also add:
```
/etc/__db.aliases.db wr,
/etc/aliases.db k,
```<
and to /usr/sbin/userdel :
```
@{PROC}/ r,
/etc/.pwd.lock rwk,
capability sys_ptrace,
#/usr/sbin/userdel ,
@{PROC}/[0-9]*/status r,
@{PROC}/[0-9]*/task/ r,
capability fsetid,
```

would(?) not you start new thread for ubuntu 9.10? i thought whether to start new thread about this my problem and installation of mail server in ubuntu 9.10 looking(?) at [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/) but as you still continue this thread and as i have just one this problem yet, i write here.

2009-12-28 17:51 utc+3 :
also add in /etc/apparmor.d/usr.lib.postfix.master :
```
#ub910
/etc/mailname r,
/var/spool/postfix/** k,
/var/lib/postfix/** wrk,
```
add in /etc/apparmor.d/usr.lib.postfix.qmgr and in /etc/apparmor.d/usr.lib.postfix.pickup :
```
/etc/mailname r,
```

---

### Post by q.dinar on 2009-12-28
hello.
what is this:

# may want to view the file to check if ok.
# especially that the final alias, eg root goes
# to a real person
sudo postalias /etc/postfix/aliases

this command has said nothing.

is my /etc/postfix/aliases file correct? :

# See man 5 aliases for format
postmaster:    root
clamav: root

you have written "especially that the final alias, eg root goes to a real person" so i should add:

root: dinar

? if so, after i add that, should i rerun sudo postalias /etc/postfix/aliases ?
now before you answer i do so i hope nothing bad if i do so...

2009-12-29 12:45 utc+3 : now i have root: dinar in root: dinar but do not have alias like that in maildb aliases table. should not it be?

---

### Post by q.dinar on 2009-12-28
"If you specify an ip in hosts, (as opposed to 'localhost') then it will communicate over tcp and not the mysql socket. (chroot restriction)."
so you make this so that this can be moved to chroot then?

GRANT SELECT,INSERT,UPDATE,DELETE,CREATE,DROP ON maildb.* TO 'mail'@'localhost' IDENTIFIED by 'mailPASSWORD';
GRANT SELECT,INSERT,UPDATE,DELETE,CREATE,DROP ON maildb.* TO 'mail'@'%' IDENTIFIED by 'mailPASSWORD'; exit;
why is 'mail'@'%' adding to 'mail'@'localhost' ? what does it mean? possiblity to connect from other computer?

18:48 utc+3 : hm should be mysql_alias.cf etc with "none" permission for "others"? because mysql password is in it. 18:51 utc+3: and what should be owner user and group of them?

21:07 utc+3 : 
INSERT INTO aliases (mail,destination) VALUES ('xandros@blobber.org','xandros@blobber.org'), ('vivita@blobber.org','vivita@blobber.org');
hm, to all users should be so ?

INSERT INTO aliases (mail,destination) VALUES ('@lala.com','@whupper.nu'), 
...
('postmaster@whopper.nu','postmaster@localhost'), ('abuse@whopper.nu','abuse@localhost'), 
...
('abuse@blobber.org','abuse@localhost');
then
 You want all mail for whooper.nu to go to xandros (catchall).
INSERT INTO aliases (mail,destination) VALUES ('@whopper.nu','xandros@blobber.org');

so mail to [email]postmaster@whopper.nu[/email] also will go to [email]xandros@blobber.org[/email] ?

21:24 utc+3 : a typo : "whupper.nu" .
21:31 utc+3 : probably to write "distribution" is better than "distrobution", because probably that is from old latin word...

---

### Post by q.dinar on 2009-12-29
hello
INSERT INTO users (id,name,maildir,crypt) VALUES ('xandros@blobber.org','xandros','xandros/', encrypt('apassword') );
/var/mail/virtual/xandros/ is created for that, is not it? why not something like /var/mail/virtual/blobber.org/xandros/ ? what to do if i want 2 separate maildirs for name in 2 domains ? just create user with such maildir in mysql query?

2009-12-30 18:22 utc+3 :
there are also 40-policy_banks and 21-ubuntu_defaults files in /etc/amavis/conf.d in ubuntu 9.10 .

2009-12-31 17:41 utc+3 :
flurdy, in previous edition you say to create postfix certificate myself in /etc/postfix/ , in the current edition you say to use /etc/ssl/certs/ssl-cert-snakeoil.pem  i have looked that directory , no such file there but many certificate files, i think, does not this mean that i should use one of them?

2010-01-01 14:58 utc+3 : i have made this yesterday. thank you. postgrey makes it to receive mail longer, i am going to disable it.

2010-01-01 20:51 utc+3 : one bug of this in ubuntu 9.10 is that "virtual" user has appeared on the login screen.

---

### Post by krak3n on 2009-12-31
Hi Guys

New to the forum :D

I've been following the 9th edition and got the basic setup done.

I am able to send and receive email through telnet, however I am having problems with getting a mail client (e.g Thunderbird) to send email via smtp.

Here is my /etc/postfix/main.cf

```

alias_database = hash:/etc/postfix/aliases
alias_maps = hash:/etc/postfix/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
delay_warning_time = 4h
disable_vrfy_command = yes
inet_interfaces = all
local_recipient_maps = 
mailbox_size_limit = 0
maximal_backoff_time = 8000s
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
mydestination = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mynetworks_style = host
myorigin = chris-reeves.com
readme_directory = no
recipient_delimiter = +
relayhost = 
smtp_helo_timeout = 60s
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, 	reject_rbl_client blackholes.easynet.nl, 	reject_rbl_client dnsbl.njabl.org
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_delay_reject = yes
smtpd_hard_error_limit = 12
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, 	reject_invalid_hostname, permit
smtpd_recipient_limit = 16
smtpd_recipient_restrictions = permit_mynetworks	permit_sasl_authenticated	reject_unauth_destination
smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, 	reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_soft_error_limit = 3
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
unknown_local_recipient_reject_code = 450
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf

```

The mail client is able to connect and receive emails via IMAP, but when it comes to SMTP sending it fails, this is what I get in the /var/log/mail.log

```

Dec 31 15:37:01 localhost postfix/smtpd[6393]: warning: 92.11.7.17: hostname host-92-11-7-17.as43234.net verification failed: Name or service not known
Dec 31 15:37:01 localhost postfix/smtpd[6393]: connect from unknown[92.11.7.17]
Dec 31 15:37:01 localhost postfix/smtpd[6393]: disconnect from unknown[92.11.7.17]

```

I've followed the guide to the letter, so I'm a little confused as to why it's not able to send emails via SMPT. :confused:

Any help guys?

Thanks

Chris

---

### Post by benjamin_888 on 2010-01-06
I have some question with the shorewall configuration part which is vi /etc/shorewall/rules

SSH/ACCEPT      net             $FW

I am confused with the entry above,the entry above should insert into which column?

After that,it said once the server is working, go back to vi /etc/shorewall/rules
how do i know the server is working or not? Anybody knows?

and the open business part is really confusing,
I have no idea how to insert the entries into it,can anybody shows me the screen shot or guidance so that i can understand?

tq.

---

### Post by q.dinar on 2010-01-08
hello. i have read shorewall manuals once, may be when reading this how-to, but i could not understand easily, (and i had not installed mail with this how-to that time), then iptables seemed easier to me, and now i use iptables and i left shorewall configuration part of this how-to.

---

### Post by Tube Shark on 2010-01-28
Need of a little help. I am setting up email server on ubuntu desktop 9.10 and following the tutorial (I think).  I didn't install shorewall cause i'm using the firewall in the router.  I can send no problem and when I try to telnet from the server from itself to receive an email I get "status=bounced (mail for domain.com loops back to myself) in the mail.log folder.  It seems to be getting rejected before the system can receive the email.  I'm not seeing any other errors, but they may come once the email gets through.

Please help running out of stuff to read.

Thanks

---

### Post by lisati on 2010-01-29
> **Tube Shark said:**
> Need of a little help. I am setting up email server on ubuntu desktop 9.10 and following the tutorial (I think).  I didn't install shorewall cause i'm using the firewall in the router.  I can send no problem and when I try to telnet from the server from itself to receive an email I get "status=bounced (mail for domain.com loops back to myself) in the mail.log folder.  It seems to be getting rejected before the system can receive the email.  I'm not seeing any other errors, but they may come once the email gets through.

Please help running out of stuff to read.

Thanks

Might be a good idea to start a new thread in the server section of the forum or ask the staff to move your query from the "outdated tutorials" section of the forum.

(No clue comes to mind why your telnet might be bouncing..... possibly a problem with your how your "hosts" information is configured)

---

### Post by Tube Shark on 2010-01-29
Thanks lisati I'll do that.

---

### Post by harry_bk on 2010-02-04
Hello everybody,
I am trying to set up a mail server on ubuntu 9.10 Server installed on VMware. In order to do that, I chose postfix and I followed the following tutorial ([http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)). But after I finished the setup, I am not able to run the basic server. The problem is that I have to setup the mail server for an entreprise where I'm doing my internship.  First I just wanted to test it locaally before being able to bind it to  a future Internet web site. I don't really know what's wrong with my basic setup. By the way I haven't set the DNS and I don't know if it's mandatory to do that even for local tests. Also, the machine is under dhcp. I'm also trying to install and set another mail server called Zimbra as someone advised me to, but as many people succeeded in installing and running Postfix, I really want to know what's wrong with my configuration. Below, you'll find some commands I typed and the results.

---

### Post by flurdy on 2010-02-04
> **harry_bk said:**
> Hello everybody,
I am trying to set up a mail server on ubuntu 9.10 Server installed on VMware. In order to do that, I chose postfix and I followed the following tutorial ([http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)). But after I finished the setup, I am not able to run the basic server. The problem is that I have to setup the mail server for an entreprise where I'm doing my internship.  First I just wanted to test it locaally before being able to bind it to  a future Internet web site. I don't really know what's wrong with my basic setup. By the way I haven't set the DNS and I don't know if it's mandatory to do that even for local tests. Also, the machine is under dhcp. I'm also trying to install and set another mail server called Zimbra as someone advised me to, but as many people succeeded in installing and running Postfix, I really want to know what's wrong with my configuration. Below, you'll find some commands I typed and the results.

in your attached screenshots it says: status:sent(delivered to mailbox)

So your postfix works.
(The rbl errors are due to dns but the server still works.)

---

### Post by harry_bk on 2010-02-05
Thanks a lot flurdy,Now it's ok I send and receive local messages. But when I tried to send messages to external domains like my gmail address it doesn't work as expected although I put the smtp address of my ISP in the relayhost case. What could be the problem??

---

### Post by lisati on 2010-02-05
> **harry_bk said:**
> Thanks a lot flurdy,Now it's ok I send and receive local messages. But when I tried to send messages to external domains like my gmail address it doesn't work as expected although I put the smtp address of my ISP in the relayhost case. What could be the problem??

Does your ISP block port 25?

---

### Post by harry_bk on 2010-02-05
I don't know if my ISP blocks port 25, but I'm going to check it right now

---

### Post by benjamin_888 on 2010-02-07
[SIZE=2]Hi Flurdy,

I am very confused in adding users and domains part.

First, is it I need to log in to mysql database using mysql -u root -p?

Then just follow whatever the instruction in that particular part?

Second, is it I only can test my email server after adding users and domains?

I have nearly finish my basic email server setup, just have a bit problem with firewall part.

Hope you can answer my question as soon as possible, so that i can solve my project faster. thank you very much.[/SIZE]
[FONT=&quot][/FONT]

---

### Post by flurdy on 2010-02-16
Ive updated the SASL section of [flurdy.com/docs/postfix/]("http://flurdy.com/docs/postfix/") to properly explain how to use password that are encrypted in the database.

---

### Post by flurdy on 2010-02-16
> **benjamin_888 said:**
> [size=2]hi flurdy,

i am very confused in adding users and domains part.

First, is it i need to log in to mysql database using mysql -u root -p?

Then just follow whatever the instruction in that particular part?

Second, is it i only can test my email server after adding users and domains?

I have nearly finish my basic email server setup, just have a bit problem with firewall part.

Hope you can answer my question as soon as possible, so that i can solve my project faster. Thank you very much.[/size]
[font=&quot][/font]

1)
Are you asking of you need to log in as root in the configuring the database or the add user section?

For the add domains and users section you log in as the *mail* user. But you can log in as root as well.

For adding domains and users you have to add the required ones.

Then modify the examples for normal users to suit your requirements.

2)
You can test your server without user etc. Especially not needed early on when you are simply testing if the server is up and can connect etc and not worried if the emails are rejected or not.

But eventually you will need domains and users otherwise testing will always reject your emails. So you need them quite early.

---

### Post by flurdy on 2010-02-16
Still no idea why my tutorial at some point was moved to the "outdated tutorial" forum, but nevermind.

---

### Post by mcfly1204 on 2010-02-16
I have gone through this tutorial and have just about everything working.  I can send/receive mail via postfix using telnet.  I can connect an email client, Thunderbird, from another system in the same network.  I can receive mail in the mail client.  However, I cannot send mail while using the mail client.  I receive the following error in /mail.log:
```

Feb 16 14:56:40 pg4 postfix/smtpd[4837]: connect from unknown[172.20.X.XXXX]
Feb 16 14:56:40 pg4 postfix/smtpd[4837]: setting up TLS connection from unknown[172.20.X.XXXX]
Feb 16 14:56:40 pg4 postfix/smtpd[4837]: TLS connection established from unknown[172.20.X.XXXX]: SSLv3 with cipher DHE-RSA-... (256/256 bits)
Feb 16 14:56:40 pg4 postfix/smtpd[4837]: warning: SASL authentication failure: no secret in database
Feb 16 14:56:40 pg4 postfix/smtpd[4837]: warning: unknown[172.20.X.XXXX]: SASL CRAM-MD5 authentication failed
Feb 16 14:56:43 pg4 postfix/smtpd[4837]: warning: SASL authentication failure: no secret in database
Feb 16 14:56:43 pg4 postfix/smtpd[4837]: warning: unknown[172.20.X.XXXX]: SASL CRAM-MD5 authentication failed
Feb 16 14:56:45 pg4 postfix/smtpd[4837]: disconnect from unknown[172.20.X.XXXX]
```

When I try to send a message in Thunderbird, I get a prompt telling me the password for the server is incorrect.  If I reenter what should be the correct password, I receive the prompt again.

Any thoughts?

---

### Post by flurdy on 2010-02-17
> **mcfly1204 said:**
> I have gone through this tutorial and have just about everything working.  I can send/receive mail via postfix using telnet.  I can connect an email client, Thunderbird, from another system in the same network.  I can receive mail in the mail client.  However, I cannot send mail while using the mail client.  I receive the following error in /mail.log:
```

Feb 16 14:56:40 pg4 postfix/smtpd[4837]: connect from unknown[172.20.X.XXXX]
Feb 16 14:56:40 pg4 postfix/smtpd[4837]: setting up TLS connection from unknown[172.20.X.XXXX]
Feb 16 14:56:40 pg4 postfix/smtpd[4837]: TLS connection established from unknown[172.20.X.XXXX]: SSLv3 with cipher DHE-RSA-... (256/256 bits)
Feb 16 14:56:40 pg4 postfix/smtpd[4837]: warning: SASL authentication failure: no secret in database
Feb 16 14:56:40 pg4 postfix/smtpd[4837]: warning: unknown[172.20.X.XXXX]: SASL CRAM-MD5 authentication failed
Feb 16 14:56:43 pg4 postfix/smtpd[4837]: warning: SASL authentication failure: no secret in database
Feb 16 14:56:43 pg4 postfix/smtpd[4837]: warning: unknown[172.20.X.XXXX]: SASL CRAM-MD5 authentication failed
Feb 16 14:56:45 pg4 postfix/smtpd[4837]: disconnect from unknown[172.20.X.XXXX]
```

When I try to send a message in Thunderbird, I get a prompt telling me the password for the server is incorrect.  If I reenter what should be the correct password, I receive the prompt again.

Any thoughts?

I updated the SASL authentication a few days ago.
Check if it solves your problem. Such as adding postfix to sasl user etc.

---

### Post by mcfly1204 on 2010-02-17
> **flurdy said:**
> I updated the SASL authentication a few days ago.
Check if it solves your problem. Such as adding postfix to sasl user etc.

I noticed that you updated the SASL portion and was eager to walk through it hoping it would resolve my issue... Unfortunately it did not.

---

### Post by three_jeeps on 2010-02-18
A general question:
Is there a version of the tutorial for 8.04 that describes how to set up an outgoing only mail server?  (Ideally for ppl who have comcast or verizon as their ISP?)

OR

A 'bare bones' version that does both outgoing and incoming?

Thanks for any help....
-John

---

### Post by nu_gen68 on 2010-02-19
First off, I'm kind of a noob with ubuntu, but I'll try my best to explain my problem.

I followed your tutorial and everything works great. 

My problem is that I am trying to add a plug-in for Squirrelmail, so that a user can change their password instead of changing it through SQL. So, I am trying to set up 'Change SQL Password' plugin from squirrelmail.org, I installed the compatibility plug-in as well. So far, I have the plug-in installed, but when squirrelmail accesses the SQL database it can't compare the old password properly to change it.

id: root@localhost
pw: 1234

The configuration file for Change SQL Password, the main lines:
accesses the SQL database: 
**$csp_dsn = 'mysl://mail:****@localhost/maildb';**
looks up password to compare: 
**$lookup_password_query = 'SELECT count(*) FROM users WHERE id = "%1" AND crypt = %4';**
encryption method: 
**$password_encryption = 'MYSQLENCRYPT';**
salt static and query are set to: nothing

MySQL Log:
210 Connect mail@localhost on
210 Init DB maildb
210 Init DB maildb
209 Query   SELECT count(*) FROM users WHERE id = "root@localhost" AND crypt = encrypt("1234")
209 Quit

Squirrelmail responds with "Your old password does not match". 

Thanks

---

### Post by benjamin_888 on 2010-02-21
> **flurdy said:**
> 1)
Are you asking of you need to log in as root in the configuring the database or the add user section?

For the add domains and users section you log in as the *mail* user. But you can log in as root as well.

For adding domains and users you have to add the required ones.

Then modify the examples for normal users to suit your requirements.

2)
You can test your server without user etc. Especially not needed early on when you are simply testing if the server is up and can connect etc and not worried if the emails are rejected or not.

But eventually you will need domains and users otherwise testing will always reject your emails. So you need them quite early.


thank you flurdy, how can i know my server is up or not?

---

### Post by oziemike on 2010-02-25
Have been running Flurdy's mail server for about 3 years based on Ubuntu 6.06 and thought it about time to get up to a newer version. So loaded up 9.10 server and followed it thru step by step. I am running it on the bench off the Interenet for testing purpose. Before the advanced setup it seemed to be sending and receiving OK. I had imported the old databases from 6.06 (MySQL)

With the advanced setup, the moment another mail server tries to connect or I even do a telnet localhost 25 I get:

Feb 26 01:15:46 mail postfix/smtpd[4219]: warning: SASL per-process initialization failed: generic failure
Feb 26 01:15:46 mail postfix/smtpd[4219]: fatal: SASL per-process initialization failed
Feb 26 01:15:47 mail postfix/master[4211]: warning: process /usr/lib/postfix/smtpd pid 4219 exit status 1
Feb 26 01:15:47 mail postfix/master[4211]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling

After that the server is locked up and starting and stopping it is the only way to get it back.

I have gone over and over the setup and still can't find any config problems. Can anyone point me in the right direct where I may have slipped up??

Mike

---

### Post by jvdl85 on 2010-02-28
Hi, 
I have used your site to setup a mail sever. but I have run in to some problems.
IMAP isnt working as it should. The mail log keeps giving me the error mail imapd: chdir Maildir: No such file or directory.
I have added data succesfuly and postfix and mysql seems seems to work fine.
I know this because I have tested via telnet and sended mails succesfully also the user directories were made.
Also the squirrelmail site says ERROR: ERROR: connection dropped by IMAP server.
Does anyone know what is configured maybe wrong?
I followed the documentation to the point.
 
 
```

This is from the mail.log
 
Feb 28 07:47:14 mail imapd: Connection, ip=[::ffff:192.168.2.15]
Feb 28 07:47:14 mail imapd: chdir Maildir: No such file or directory
Feb 28 07:47:14 mail imapd: jeroen: No such file or directory
Feb 28 07:47:48 mail imapd: Connection, ip=[::ffff:192.168.2.15]
Feb 28 07:47:48 mail imapd: chdir Maildir: No such file or directory
Feb 28 07:47:48 mail imapd: jeroen: No such file or directory

```
 
```

root@mail:/var/mail/virtual# pwd
/var/mail/virtual
root@mail:/var/mail/virtual# ls -ltra
total 20
drwxrwsr-x 3 root    mail    4096 2010-02-27 14:43 ..
drwx--S--- 5 virtual virtual 4096 2010-02-27 15:47 test
drwx--S--- 5 virtual virtual 4096 2010-02-27 15:49 jeroen
drwxr-sr-x 5 virtual virtual 4096 2010-02-28 03:19 .
drwx--S--- 5 virtual virtual 4096 2010-02-28 03:19 joyce
 
 
root@mail:/var/mail/virtual/jeroen# pwd
/var/mail/virtual/jeroen
root@mail:/var/mail/virtual/jeroen# ls -ltra
total 20
drwx--S--- 2 virtual virtual 4096 2010-02-27 15:49 cur
drwx--S--- 5 virtual virtual 4096 2010-02-27 15:49 .
drwx--S--- 2 virtual virtual 4096 2010-02-28 03:10 tmp
drwx--S--- 2 virtual virtual 4096 2010-02-28 03:10 new
drwxr-sr-x 5 virtual virtual 4096 2010-02-28 03:19 ..
 
 
root@mail:/var/mail/virtual/jeroen/new# pwd
/var/mail/virtual/jeroen/new
root@mail:/var/mail/virtual/jeroen/new# ls -ltra
total 20
-rw------- 1 virtual virtual  425 2010-02-27 15:49 
267282160.Vfc00I548fM177362.mail
drwx--S--- 5 virtual virtual 4096 2010-02-27 15:49 ..
-rw------- 1 virtual virtual 3298 2010-02-27 15:51 1267282314.Vfc00I54a0M170046.mail
-rw------- 1 virtual virtual 3831 2010-02-28 03:10 1267323030.Vfc00I54b2M855278.mail
drwx--S--- 2 virtual virtual 4096 2010-02-28 03:10 .

```
 
```

vi /etc/courier/authmysqlrc
 
MYSQL_HOME_FIELD        home
##NAME: MYSQL_NAME_FIELD:0
#
# The user's name (optional)
MYSQL_NAME_FIELD        name
##NAME: MYSQL_MAILDIR_FIELD:0
#
# This is an optional field, and can be used to specify an arbitrary
# location of the maildir for the account, which normally defaults to
# $HOME/Maildir (where $HOME is read from MYSQL_HOME_FIELD).
#
# You still need to provide a MYSQL_HOME_FIELD, even if you uncomment this
# out.
#
MYSQL_MAILDIR_FIELD concat(home,'/',maildir)

```
 
Iff more info is required then let me know, I'm really stuck. Also googled the problem but did'nt get any wiser.
 
from the FAQ section
**Squirrelmail does not allow me to log in**
 
This is due to many things. Most are due to skipping too fast forward, ignoring [test sections]("http://flurdy.com/docs/postfix/#test") etc. 
 

Answers: 
[LIST]
[*]**Does [postfix]("http://flurdy.com/docs/postfix/#config-simple-mta") work?**
No point trying to run before you can crawl. Send emails to recipients on your server, tail mail.log to see if everything is okay.
Often [mysql]("http://flurdy.com/docs/postfix/#config-simple-database") is not configured properly, [check the mysql logs]("http://flurdy.com/docs/postfix/#test") for activity.
[/LIST]Yes postfix works and i see activity in the mysql.log
Also the user dir's are made.

[LIST]
[*]**Have they ever received an email?**
If not they can not log into squirrelmail as the email folders will not yet exist. 
[/LIST]Yes as you can see above
[LIST]
[*]**Does [Courier]("http://flurdy.com/docs/postfix/#config-simple-imap") work?**
If it doesn't then you have still got some more setup to do.
[/LIST]Yes trying with telnet shows.
```

telnet localhost 143
Trying ::1...
Connected to localhost.
Escape character is '^]'.
* OK [CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE ACL ACL2=UNION] Courier-IMAP ready. Copyright 1998-2008 Double Precision, Inc.  See COPYING for distribution information.
 
 telnet localhost 10024
Trying ::1...
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 [127.0.0.1] ESMTP amavisd-new service ready
  
```
 
```

 ps -ef |grep courier
root     13243     1  0 Feb27 ?        00:00:00 /usr/sbin/courierlogger -pid=/var/run/courier/authdaemon/pid -start /usr/lib/courier/courier-authlib/authdaemond
root     13244 13243  0 Feb27 ?        00:00:00 /usr/lib/courier/courier-authlib/authdaemond
root     13254 13244  0 Feb27 ?        00:00:00 /usr/lib/courier/courier-authlib/authdaemond
root     13255 13244  0 Feb27 ?        00:00:00 /usr/lib/courier/courier-authlib/authdaemond
root     13256 13244  0 Feb27 ?        00:00:00 /usr/lib/courier/courier-authlib/authdaemond
root     13257 13244  0 Feb27 ?        00:00:00 /usr/lib/courier/courier-authlib/authdaemond
root     13258 13244  0 Feb27 ?        00:00:00 /usr/lib/courier/courier-authlib/authdaemond
root     13318     1  0 Feb27 ?        00:00:00 /usr/sbin/courierlogger -pid=/var/run/courier/imapd.pid -start -name=imapd /usr/sbin/couriertcpd -address=0 -maxprocs=40 -maxperip=20 -nodnslookup -noidentlookup 143 /usr/lib/courier/courier/imaplogin /usr/bin/imapd Maildir
root     13319 13318  0 Feb27 ?        00:00:00 /usr/sbin/couriertcpd -address=0 -maxprocs=40 -maxperip=20 -nodnslookup -noidentlookup 143 /usr/lib/courier/courier/imaplogin /usr/bin/imapd Maildir
root     13374     1  0 Feb27 ?        00:00:00 /usr/sbin/courierlogger -pid=/var/run/courier/imapd-ssl.pid -start -name=imapd-ssl /usr/sbin/couriertcpd -address=0 -maxprocs=40 -maxperip=20 -nodnslookup -noidentlookup 993 /usr/bin/couriertls -server -tcpd /usr/lib/courier/courier/imaplogin /usr/bin/imapd Maildir
root     13375 13374  0 Feb27 ?        00:00:00 /usr/sbin/couriertcpd -address=0 -maxprocs=40 -maxperip=20 -nodnslookup -noidentlookup 993 /usr/bin/couriertls -server -tcpd /usr/lib/courier/courier/imaplogin /usr/bin/imapd Maildir
root     30095 30074  0 08:34 pts/1    00:00:00 grep courier

```
 

[LIST]
[*]If all above is okay, then it may be a problem with your [Squirrelmail setup]("http://flurdy.com/docs/postfix/#config-extra-webmail").
Check empty spaces in squirrelmail mysql setup. More details in [test section]("http://flurdy.com/docs/postfix/#test"). 
[/LIST]**Email folders do not exist**
 
Mentioned many times in this guide and forums. 
 

Answers: 
[LIST]
[*]**Have they received an email?**
If not they you can not log into squirrelmail as the email folders will not yet exist. When receiving their first email, postfix will create all the neccessary folders. If it does not your postfix setup is broken. 
[/LIST]user dir's are made see above.
 
Greetz

---

### Post by flurdy on 2010-02-28
@jvdl85

Your setup certainly seems fine.
And the fact that the mail folders are created when receiving emails and that you can send indicates postfix is fine.

The courier bit also seems correct...


The only thing I would check is the sql logs. What happens there when you try to login read emails via imap?

---

### Post by q.dinar on 2010-03-01
i have question. i know that ssl works when i use squirrelmail. how can i know whether it works between mail servers when they send mail with smtp protocol. if i send message to a server that does not support ssl, do i see in log that mail is sent without ssl.
if target server does not trust my certificate, it can refuse mail or accept it anyway? can it ask to get it unciphered instead of getting it untrusted?

---

### Post by oziemike on 2010-03-02
Flurdy

I would certainly appreciate any pointers from my entry about 3 posts back, if you have the time??

Mike

---

### Post by fade2gray on 2010-03-02
I've been considering upgrading from 8.04 to 9.10.

Is this possible without breaking my mailserver?

I will be making a PING image of the system drive before attempting, but which files should I backup for an easy setup should I find it necessary to perform a clean install?

Thanks.

---

### Post by tiercel on 2010-03-02
< < < SOLVED!   ...well, at least working.  Feedback certainly appreciated, see below > > >

Okay... I'm going mad with a problem that crops up for me after the basic part of the setup.

I've worked through the tutorial up through Courier, and am testing the basic mail server.  I can successfully telnet localhost 25 to send a mail to a recipient on the machine.  When I attempt to telnet *mymachine* 25 from anywhere else, the telnet just hangs and eventually times out.

I can SSH into *mymachine* just fine from the outside world so it's presumably not some kind of DNS issue (I'm using ddclient + DynDNS to route to my DMZ'd machine behind a DSL router).

I figured maybe this was a firewall issue of some sort but if I use *mymachine* to surf to [www.canyouseeme.org](www.canyouseeme.org), it reports to *mymachine* that it can see port 25 just fine.  Furthermore, /var/log/syslog or mail.log cheerfully reports a SMTP port connection from [www.no-ip.com:](www.no-ip.com:)

```
postfix/smtpd[14144]: connect from www.no-ip.com[204.16.252.112]
postfix/smtpd[14144]: lost connection after CONNECT from www.no-ip.com[204.16.252.112]
postfix/smtpd[14144]: disconnect from www.no-ip.com[204.16.252.112]
```

Whatever they are doing is apparently able to connect just fine to the SMTP port, but telnet can't.  I tried deactivating shorewall altogether (and deactivating ufw as well, in case that was blocking anything) and got the same result.  (Needless to say, actually sending email to a user@*mymachine* results in said email vanishing into a black hole, unless I sent it from *mymachine* using telnet localhost.)

I'm really bamboozled.  This guide to setting up a mail server looks great, I just can't figure out what I've done wrong / haven't done that would result in an error like this.

Appreciate any help you can offer!  Thanks.

----------

< < < EDIT:  Solution > > > 

Gahhhh.  I guess this is what I get for trusting blindly in web-based port testers... it looks like it's just the "your ISP is blocking port 25 thing."  I changed the incoming port to 2525 and it seems to be accessible now.   I don't know if this is the cleanest way to solve this problem -- I've heard different chatter about using 587 or enforcing secure SMTP so I'm certainly still open to suggestions/criticism! 

What I did:

Open Shorewall port 2525:  edit /etc/shorewall/rules, add:

```
#Accept from anyone on the net
ACCEPT          net       $FW             tcp     2525
```

Get Postfix to listen on port 2525:   edit /etc/postfix/master.cf, change:

```
smtp      inet  n       -       -       -       -       smtpd
```to```
2525      inet  n       -       -       -       -       smtpd
```

Get DynDNS MailHop Relay to relay incoming mail to port 2525.

---

### Post by mcfly1204 on 2010-03-10
I was struggling to get SASL working, and then noticed that the following command would simply hang.
> telnet localhost 25
I proceeded to copy over my existing main.cf file with main.cf.debian, made all changes noted in the walkthrough, and the above command continues to hang.  I can view the following in mail.log.
> Mar 10 16:40:50 host4 postfix/smtpd[5030]: warning: SASL per-process initialization failed: generic failure
Mar 10 16:40:50 host4 postfix/smtpd[5030]: fatal: SASL per-process initialization failed
Mar 10 16:40:51 host4 postfix/master[4679]: warning: process /usr/lib/postfix/smtpd pid 5030 exit status 1
Mar 10 16:40:51 host4 postfix/master[4679]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling

**edit**
Added main.cf and master.cf for reference.

---

### Post by dcstar on 2010-03-12
> **three_jeeps said:**
> A general question:
Is there a version of the tutorial for 8.04 that describes how to set up an outgoing only mail server?  (Ideally for ppl who have comcast or verizon as their ISP?)


Ubuntu comes with an "outgoing" mail server installed by default - postfix.

All you may need to do is:
```
sudo dpkg-reconfigure postfix
```
and make sure it is set to "Internet", then edit the /etc/postfix/main.cf file with a relayhost (if you want your ISP's SMTP server to do the work).

Set you mail clients to use your system for outgoing mail and it should work. Can't get much simpler than that.

---

### Post by lisati on 2010-03-12
> **mcfly1204 said:**
> I was struggling to get SASL working, and then noticed that the following command would simply hang.

I proceeded to copy over my existing main.cf file with main.cf.debian, made all changes noted in the walkthrough, and the above command continues to hang.  I can view the following in mail.log.


**edit**
Added main.cf and master.cf for reference.

Is port 25 blocked from the machine you're running the telnet command on to your server?

---

### Post by mcfly1204 on 2010-03-12
> **lisati said:**
> Is port 25 blocked from the machine you're running the telnet command on to your server?

No, port 25 is not blocked.  I even ran iptables -F to flush all the rules.  I feel my issue has to be connected to the two files I posted given postfix is bound to 25.

---

### Post by q.dinar on 2010-03-16
i have got this error after i sent a mail:

host ***[***] said: 550 Access denied
    - Invalid HELO name (See RFC2821 4.1.1.1) (in reply to MAIL FROM command)

this is mail from MAILER-DAEMON@***(mydomain).

---

### Post by mcfly1204 on 2010-03-16
> **q.dinar said:**
> i have got this error after i sent a mail:

host ***[***] said: 550 Access denied
    - Invalid HELO name (See RFC2821 4.1.1.1) (in reply to MAIL FROM command)

this is mail from MAILER-DAEMON@***(mydomain).

Can you post a copy of your main.cf file?

---

### Post by q.dinar on 2010-03-16
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = dinar-desktop
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
#mydestination = kukmara.ru, dinar-desktop, localhost.localdomain, localhost
#As we will be using virtual domains, these need to be empty. http://flurdy.com/docs/postfix/
mydestination = 
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

# http://flurdy.com/docs/postfix/ :
# how long if undelivered before sending warning update to sender
delay_warning_time = 4h 
# will it be a permanent error or temporary
unknown_local_recipient_reject_code = 450 
# how long to keep message on queue before return as failed.
# some have 3 days, I have 16 days as I am backup server for some people
# whom go on holiday with their server switched off.
maximal_queue_lifetime = 7d 
# max and min time in seconds between retries if connection failed
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s 
# how long to wait when servers connect before receiving rest of data
smtp_helo_timeout = 60s 
# how many address can be used in one message.
# effective stopper to mass spammers, accidental copy in whole address list
# but may restrict intentional mail shots.
smtpd_recipient_limit = 16 
# how many error before back off.
smtpd_soft_error_limit = 3
# how many max errors before blocking it.
smtpd_hard_error_limit = 12
# Requirements for the HELO statement
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit 

# Requirements for the sender details
#smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, #reject_unauth_pipelining, permit 
#smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, #reject_unauth_pipelining, permit 
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit

# Requirements for the connecting server
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org 

# Requirement for the recipient address
#smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, reject_non_fqdn_recipient, #reject_unknown_recipient_domain, reject_unauth_destination, permit
#smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, #reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service #inet:127.0.0.1:10023, permit
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, permit

smtpd_data_restrictions = reject_unauth_pipelining
# require proper helo at connections
smtpd_helo_required = yes
# waste spammers time before rejecting them
smtpd_delay_reject = yes
disable_vrfy_command = yes
# not sure of the difference of the next two
# but they are needed for local aliasing
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
# this specifies where the virtual mailbox folders will be located
virtual_mailbox_base = /var/spool/mail/virtual
# this is for the mailbox location for each user
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
# and their user id
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf
# and group id
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
# and this is for aliases
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
# and this is for domain lookups
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
# this is how to connect to the domains (all virtual, but the option is there)
# not used yet
# transport_maps = mysql:/etc/postfix/mysql_transport.cf

#http://flurdy.com/docs/postfix/
content_filter = amavis:[127.0.0.1]:10024

#http://flurdy.com/docs/postfix/edition5.html
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
#smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = 

#http://flurdy.com/docs/postfix/edition5.html#conf_auth
#smtpd_use_tls = yes 
#smtpd_tls_cert_file = /etc/postfix/postfix.cert 
#smtpd_tls_key_file = /etc/postfix/postfix.key 
#smtpd_data_restrictions = reject_unauth_pipelining

#http://flurdy.com/docs/postfix/#config-secure-auth
# TLS parameters 
#smtp_use_tls = no 
smtp_tls_security_level = may 
#smtpd_use_tls=yes 
smtpd_tls_security_level = may 
#smtpd_tls_auth_only = no 
smtp_tls_note_starttls_offer = yes 
smtpd_tls_loglevel = 1 
smtpd_tls_received_header = yes 
smtpd_tls_session_cache_timeout = 3600s 
tls_random_source = dev:/dev/urandom 
#smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem 
#smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key 
smtpd_tls_cert_file = /etc/postfix/postfix.cert 
smtpd_tls_key_file = /etc/postfix/postfix.key 
#smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache 
#smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
```

---

### Post by lisati on 2010-03-16
> **q.dinar said:**
> i have got this error after i sent a mail:

host ***[***] said: 550 Access denied
    - Invalid HELO name (See RFC2821 4.1.1.1) (in reply to MAIL FROM command)

this is mail from MAILER-DAEMON@***(mydomain).

What this says to me is that the receiving system thinks that your system is introducing itself in a way that the receiving system doesn't like. I had a look at the main.cf file you posted, and suspect the following line *might* need to be changed (someone else might be able to confirm or correct):
> myhostname = dinar-desktop
On my system I have it set to reflect the name people would use in email addresses and when accessing my website.

---

### Post by steev182 on 2010-03-24
I'm unable to connect using IMAP, what could I have done wrong?

```
Mar 24 22:20:10 sweb00 authdaemond: received auth request, service=imap, authtype=login
Mar 24 22:20:10 sweb00 authdaemond: authmysql: trying this module
Mar 24 22:20:10 sweb00 authdaemond: authmysqllib: connected. Versions: header 50075, client 50083, server 50137
Mar 24 22:20:10 sweb00 authdaemond: SQL query: SELECT id, "", clear, uid, gid, home, concat(home,'/',maildir), "", name, "" FROM users WHERE id = 'steve'  AND (enabled=1)
Mar 24 22:20:10 sweb00 imapd: LOGIN FAILED, user=steve, ip=[my home ip]
Mar 24 22:20:10 sweb00 authdaemond: zero rows returned
Mar 24 22:20:10 sweb00 authdaemond: no password available to compare
Mar 24 22:20:10 sweb00 authdaemond: authmysql: REJECT - try next module
Mar 24 22:20:10 sweb00 authdaemond: FAIL, all modules rejected
Mar 24 22:20:15 sweb00 imapd: LOGOUT, ip=[my home ip], rcvd=63, sent=499

```

---

### Post by steev182 on 2010-03-25
I fixed one problem, logging in, I needed to change 'user' to 'name' in authdaemonrc. But now it looks like I can't send, so will look through the settings I added for SASL - AHHH

---

### Post by steev182 on 2010-03-25
My problem now:

Mar 25 13:55:53 sweb00 imapd-ssl: Failed to connect to socket /tmp/fam--
Mar 25 13:56:26 sweb00 imapd-ssl: last message repeated 3 times
Mar 25 13:56:26 sweb00 postfix/smtpd[27826]: warning: SASL per-process initialization failed: generic failure
Mar 25 13:56:26 sweb00 postfix/smtpd[27826]: fatal: SASL per-process initialization failed
Mar 25 13:56:27 sweb00 postfix/master[27666]: warning: process /usr/lib/postfix/smtpd pid 27826 exit status 1
Mar 25 13:56:27 sweb00 postfix/master[27666]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling

---

### Post by mcfly1204 on 2010-03-25
My current setup consists of Exchange 2003 processing email for domain A.  We have been sending/receiving for an additional domain, domain B, for a few years now, but the setup is clunky given I have distribution lists setup for the domain B email addresses.  

I have setup a postfix box on the same network as the Exchange server to host email for domain B.  My, I would love to say only, main issue is that I need to be able to send emails from domain A to (Exchange) to domain B (postfix).  How do I go about this?  Do I need appropriate DNS records for both boxes given the messages are not leaving the network?

---

### Post by steev182 on 2010-03-25
OK, Here are my config files, if another set of eyes can look and see what I've done wrong...

main.cf
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# SASL 
smtpd_sasl_auth_enable = yes
# If your potential clients use Outlook Express or other older clients
# this needs to be set to yes 
broken_sasl_auth_clients = no
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =

# TLS parameters
#smtp_use_tls = no 
smtp_tls_security_level = may
#smtpd_use_tls=yes
smtpd_tls_security_level = may
#smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
#smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
#smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.stevemulcahy.co.uk
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = stevemulcahy.co.uk
local_recipient_maps =
mydestination =
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mynetworks_style = host
# how long if undelivered before sending warning update to sender 
delay_warning_time = 4h 
# will it be a permanent error or temporary 
unknown_local_recipient_reject_code = 450 
# how long to keep message on queue before return as failed. 
# some have 3 days, I have 16 days as I am backup server for some people 
# whom go on holiday with their server switched off. 
maximal_queue_lifetime = 7d 
# max and min time in seconds between retries if connection failed 
minimal_backoff_time = 1000s 
maximal_backoff_time = 8000s 
# how long to wait when servers connect before receiving rest of data 
smtp_helo_timeout = 60s 
# how many address can be used in one message. 
# effective stopper to mass spammers, accidental copy in whole address list 
# but may restrict intentional mail shots. 
smtpd_recipient_limit = 16 
# how many error before back off. 
smtpd_soft_error_limit = 3 
# how many max errors before blocking it. 
smtpd_hard_error_limit = 12
# Requirements for the HELO statement 
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit 
# Requirements for the sender details 
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org 
# Requirement for the recipient address 
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:10023, permit
smtpd_helo_required = yes 
# waste spammers time before rejecting them 
smtpd_delay_reject = yes 
disable_vrfy_command = yes
# not sure of the difference of the next two 
# but they are needed for local aliasing 
alias_maps = hash:/etc/postfix/aliases 
alias_database = hash:/etc/postfix/aliases
# this specifies where the virtual mailbox folders will be located 
virtual_mailbox_base = /var/spool/mail/virtual 
# this is for the mailbox location for each user 
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
# and their user id 
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf 
# and group id 
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
# and this is for aliases 
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf 
# and this is for domain lookups 
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
# this is how to connect to the domains (all virtual, but the option is there) 
# not used yet 
# transport_maps = mysql:/etc/postfix/mysql_transport.cf
content_filter = amavis:[127.0.0.1]:10024    

```

master.cf:
```
#
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd
submission	inet 	n 	- 		n 		- 		-		smtpd
	-o smtpd_sasl_auth_enable=yes 
	# if you do not want to restrict it encryption only, comment out next line 
	#-o smtpd_tls_auth_only=yes
	# -o smtpd_tls_security_level=encrypt
	# -o header_checks=
	# -o body_checks=
	-o smtpd_client_restrictions=permit_sasl_authenticated,reject_unauth_destination,reject
	-o smtpd_sasl_security_options=noanonymous,noplaintext
	-o smtpd_sasl_tls_security_options=noanonymous
# -o milter_macro_daemon_name=ORIGINATING 
smtps 	inet 	n 		-		-		-		-		smtpd
	-o smtpd_tls_wrappermode=yes
	-o smtpd_sasl_auth_enable=yes
	-o smtpd_tls_auth_only=yes
	-o smtpd_client_restrictions=permit_sasl_authenticated,reject
	-o smtpd_sasl_security_options=noanonymous,noplaintext
	-o smtpd_sasl_tls_security_options=noanonymous
# -o milter_macro_daemon_name=ORIGINATING
#628      inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
   -o content_filter= 
	-o receive_override_options=no_header_body_checks
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       -       300     1       oqmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
proxywrite unix -       -       n       -       1       proxymap
smtp      unix  -       -       -       -       -       smtp
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay     unix  -       -       -       -       -       smtp
	-o smtp_fallback_relay=
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
#
# ====================================================================
# Interfaces to non-Postfix software. Be sure to examine the manual
# pages of the non-Postfix software to find out what options it wants.
#
# Many of the following services use the Postfix pipe(8) delivery
# agent.  See the pipe(8) man page for information about ${recipient}
# and other message envelope options.
# ====================================================================
#
# maildrop. See the Postfix MAILDROP_README file for details.
# Also specify in main.cf: maildrop_destination_recipient_limit=1
#
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
#
# See the Postfix UUCP_README file for configuration details.
#
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
#
# Other external delivery methods.
#
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix	-	n	n	-	2	pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}
amavis	unix	-	-	-	-	2	smtp 
	-o smtp_data_done_timeout=1200 
	-o smtp_send_xforward_command=yes 
	-o disable_dns_lookups=yes 
	-o max_use=20
127.0.0.1:10025	inet	n	-	-	-	-	smtpd 
	-o content_filter= 
	-o local_recipient_maps= 
	-o relay_recipient_maps= 
	-o smtpd_restriction_classes= 
	-o smtpd_delay_reject=no 
	-o smtpd_client_restrictions=permit_mynetworks,reject 
	-o smtpd_helo_restrictions= 
	-o smtpd_sender_restrictions= 
	-o smtpd_recipient_restrictions=permit_mynetworks,reject 
	-o smtpd_data_restrictions=reject_unauth_pipelining 
	-o smtpd_end_of_data_restrictions= 
	-o mynetworks=127.0.0.0/8 
	-o smtpd_error_sleep_time=0 
	-o smtpd_soft_error_limit=1001 
	-o smtpd_hard_error_limit=1000 
	-o smtpd_client_connection_count_limit=0 
	-o smtpd_client_connection_rate_limit=0 
	-o receive_override_options=no_header_body_checks,no_unknown_recipient_checks

```

smtpd.conf:
```
pwcheck_method: saslauthd 
mech_list: plain login cram-md5 digest-md5
log_level: 7
allow_plaintext: true
auxprop_plugin: mysql
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: mail
sql_passw : ------
sql_database: maildb
sql_select: select crypt from users where id='%u@%r' and enabled = 1
```

Any ideas?

---

### Post by fernandoch on 2010-03-25
Can this tutorial be used for a home mail server for testing? What do I need? Does it work with a static IP that I have at home?

I have a domain registered, but then what? Should I create this smtp.domain.name?

Can anyone give me answers to these questions?

Thank you.

---

### Post by q.dinar on 2010-03-26
yes, it work with static ip. your domain should have mx record pointing to your ip.
"smtp." subdomain is not needed if main domain points with "mx" to your ip. (main domain can point with "A" record to other ip or to your ip. also any subdomain can point to different ips with A and Mx , A to serve sites, MX to serve mail.)

---

### Post by q.dinar on 2010-03-28
another error when 10 mb mail sent to me:
```
Mar 28 15:02:59 dinar-desktop postfix/smtpd[7681]: connect from forward9.mail.yandex.net[77.88.61.48]
Mar 28 15:03:00 dinar-desktop postfix/smtpd[7681]: lost connection after EHLO from forward9.mail.yandex.net[77.88.61.48]
Mar 28 15:03:00 dinar-desktop postfix/smtpd[7681]: disconnect from forward9.mail.yandex.net[77.88.61.48]
Mar 28 15:06:20 dinar-desktop postfix/anvil[7684]: statistics: max connection rate 1/60s for (smtp:77.88.61.48) at Mar 28 15:02:59
Mar 28 15:06:20 dinar-desktop postfix/anvil[7684]: statistics: max connection count 1 for (smtp:77.88.61.48) at Mar 28 15:02:59
Mar 28 15:06:20 dinar-desktop postfix/anvil[7684]: statistics: max cache size 1 at Mar 28 15:02:59
Mar 28 15:16:15 dinar-desktop postfix/smtpd[7728]: connect from forward9.mail.yandex.net[77.88.61.48]
Mar 28 15:16:16 dinar-desktop postfix/smtpd[7728]: lost connection after EHLO from forward9.mail.yandex.net[77.88.61.48]
Mar 28 15:16:16 dinar-desktop postfix/smtpd[7728]: disconnect from forward9.mail.yandex.net[77.88.61.48]

```

---

### Post by harrysand on 2010-03-31
Im trying to follow this guide and ran into a problem when installing SASL. I was having trouble working with my repositories, could that be the problem?

Ran this.
```
:~$ sudo apt-get install libsasl2-modules libsasl2-modules-sql libgsasl7 \ libauthen-sasl-cyrus-perl sasl2-bin libpam-mysql
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libsasl2-modules is already the newest version.
E: Couldn't find package  libauthen-sasl-cyrus-perl

```

Here is my sources.list file.
```
# 
# deb cdrom:[Ubuntu-Server 9.10 _Karmic Koala_ - Release i386 (20091027.2)]/ karmic main restricted

#deb cdrom:[Ubuntu-Server 9.10 _Karmic Koala_ - Release i386 (20091027.2)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse

```

---

### Post by lucaspr on 2010-04-20
I'm going read the whole thread if this question is already asked.. If that is the case sorry I asked ;)

But is it possible to forget about local users and just deliver all scanned mail to an exchange 2003 server? If so.. How?

BTW, thanx for the GREAT HOwTO!!

---

### Post by candoyo on 2010-04-24
Hi Flurdy and everyone else!

Thanks a lot of writing this amazing guide. I really appreciate, it will make my life a lot easier :)

I have installed the AMI image into my AWS account. I have installed  flurdy-amis/ubuntu-mail-server-webmail.
I can access phpmyadmin via the internet. But, I am not sure what's the user name and password for phpmyadmin? I also logged into the server via ssh but was not able to run mysqladmin command. It said I didn't have enough privileges to access mysqladmin. But I am logged in as root... why cant I use mysqladmin?

Any help wold be highly appreciated. Thanks again for the great work :)

-Shaq

---

### Post by candoyo on 2010-04-24
Hi Flurdy and everyone else!

Thanks a lot of writing this amazing guide. I really appreciate, it will make my life a lot easier 

I have installed the AMI image into my AWS account. I have installed flurdy-amis/ubuntu-mail-server-webmail.
I can access phpmyadmin via the internet. But, I am not sure what's the user name and password for phpmyadmin? I also logged into the server via ssh but was not able to run mysqladmin command. It said I didn't have enough privileges to access mysqladmin. But I am logged in as root... why cant I use mysqladmin?

Any help wold be highly appreciated. Thanks again for the great work 

-Shaq

---

### Post by DonGonzo on 2010-05-03
**Update:**
This courier issue was resolved for me by editing /etc/courier/authmysqlrc
```

MYSQL_HOME_FIELD "/var/spool/mail/virtual"
...
MYSQL_MAILDIR_FIELD CONCAT(home,'/',maildir)

```

I seriously hope this helps someone else, it was driving me nuts.
**/Update**



Hello Flurdy et al,

I am having a problem identical to jvdl85. I have been stuck on it for a few hours now and haven't found a satisfactory answer... Postfix works, it created the directories, mail is in the directory &c &c.

The last I saw you mention to jvdl was to check mysql logs- 

```

# tail /var/log/mysql/mysql.log
                    149 Query       SHOW TABLES
                    149 Query       SHOW FULL FIELDS IN `Permission`
                    149 Query       SHOW COLLATION LIKE 'utf8_general_ci'
                    149 Query       SHOW FULL FIELDS IN `Member`
                    149 Query       SELECT `Member`.*, `Member`.ID, if(`Member`.ClassName,`Member`.ClassName,'Member') AS RecordClassName FROM `Member` WHERE (Member.ID = 1) ORDER BY Surname, FirstName LIMIT 1
                    149 Query       UPDATE Member SET LastVisited = NOW() WHERE ID = 1
                    149 Quit
100503  0:11:10     150 Connect     user@hostname on
                    150 Init DB     mail_database
                    150 Query       SELECT id, crypt, "", uid, gid, home, "", "", name, "" FROM users WHERE id = 'user@domain.ext'

```

```

#tail /var/log/mail.log
host authdaemond: received auth request, service=imap, authtype=login
host authdaemond: authmysql: trying this module
host authdaemond: SQL query: SELECT id, crypt, "", uid, gid, home, "", "", name, "" FROM users WHERE id = 'address@domain.ext'
host authdaemond: password matches successfully
host authdaemond: authmysql: sysusername=<null>, sysuserid=5000, sysgroupid=5000, homedir=/var/spool/mail/virtual, address=address@domain.ext, fullname=name, maildir=<null>, quota=<null>, options=<null>
host authdaemond: Authenticated: sysusername=<null>, sysuserid=5000, sysgroupid=5000, homedir=/var/spool/mail/virtual, address=address@domain.ext, fullname=name, maildir=<null>, quota=<null>, options=<null>
host imapd: chdir Maildir: No such file or directory

```

Any advice you can give me would be much appreciated! If any more information is needed, please let me know.


Thanks in advance,
Gonzo

---

### Post by kelrune on 2010-05-12
I have set up my apache2 server and my SquirrelMail. as well as the many things i have seen in the first post. but i am running into the issue when i try and view it through a web browser. i cant seam to set up my SSL mod to get it running. any thoughts?

---

### Post by flemmingbjerke on 2010-05-14
Works fine on debian. Two problems with SASL that should be relevant for ubuntu, too (at least 2):

1. The one problem is described here:
[http://isp-control.net/forum/thread-8381-post-65998.html#pid65998](http://isp-control.net/forum/thread-8381-post-65998.html#pid65998)
I had to remove:
check_policy_service inet:127.0.0.1:10023,
from:
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:10023, permit

2. There may no be blanks af the variables in:
/etc/postfix/sasl/smtpd.conf

Finally, it is not clear TLS-encryption of sending requires SASL? I have earlier sat up TLS, but then I could not receive mails from other mailservers that did not like TLS-authentication. As Ivar writes:

"For the encryption of reading emails, it is Courier you need to configure. For sending, and beetwen server encryption it is Postfix." 

It could be nice to have a description of how to set up encrypted sending without between server encryption.

But, thank you, for the nice howto!

---

### Post by flemmingbjerke on 2010-05-14
> **harrysand said:**
> ....
Ran this.
```
:~$ ....
E: Couldn't find package  libauthen-sasl-cyrus-perl

```
...

Yes, I had the same strange problem on debian. I ran:
aptitude search libauthen
and indeed the packet was in the repository. I copied the name of the package of from prompt in order to run
aptitude install libauthen-sasl-cyrus-perl
And: no problem! I think there must be some hidden code in the howto.

---

### Post by Mckormick on 2010-06-18
Hi - all.. Thanks for the great guide, I have everything working except SMTP/SASL.

I think I am getting the same problem as Mcfly1204 was a few posts back:

```
Jun 18 13:41:29 de1 postfix/smtpd[24493]: connect from xxx
Jun 18 13:41:29 de1 postfix/smtpd[24493]: warning: SASL authentication failure: no secret in database
Jun 18 13:41:29 de1 postfix/smtpd[24493]: warning: xxx: SASL CRAM-MD5 authentication failed: authentication failure
```

I've checked and double checked all config against the guide.  I think there may be a typo in the 10.04 version where in /etc/postfix/sasl/smtpd.conf

```
sql_passw: mailPASSWORD
```

should be

```
sql_passwd: mailPASSWORD
```

I've changed this but no luck.

Mcfly1204 - did you resolve this?  Sorry if I missed the fix.

Thanks!

---

### Post by flurdy on 2010-06-18
> **Mckormick said:**
> I think there may be a typo in the 10.04 version where in /etc/postfix/sasl/smtpd.conf

```
sql_passw: mailPASSWORD
```

should be

```
sql_passwd: mailPASSWORD
```



Hi,
**sql_passw** is the correct parameter, even if the other (**sql_passwd**) makes more sense. However I think both may even be supported now.

---

### Post by Mckormick on 2010-06-18
ah ok, I'd just seen it as sql_passwd on other guides so I guess both are supported.

I changed it back but have the same issue.  I can send email with no encrypted authentication but if I select encrypted in Thunderbird I cannot.  I have a tail on mysql.log which doesn't seem to get hit so I don't think it is getting that far.  My config is:


```
sudo adduser postfix sasl
The user `postfix' is already a member of `sasl'.
```

main.cf

```
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks,warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain,reject_unauth_pipelining, permit

smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination

...

# SASL
smtpd_sasl_auth_enable = yes
# If your potential clients use Outlook Express or other older clients
# this needs to be set to yes
broken_sasl_auth_clients = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =

# TLS parameters
#smtp_use_tls = no
smtp_tls_security_level = may
#smtpd_use_tls=yes
smtpd_tls_security_level = may
#smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
#smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
#smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

smtpd_sasl_authenticated_header = yes

```

master.cf
```
smtp      inet  n       -       -       -       -       smtpd
submission inet n       -       -       -       -       smtpd
#  -o smtpd_tls_security_level=encrypt
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject_unauth_destination,reject
  -o smtpd_sasl_security_options=noanonymous,noplaintext
  -o smtpd_sasl_tls_security_options=noanonymous
#  -o milter_macro_daemon_name=ORIGINATING
smtps     inet  n       -       -       -       -       smtpd
  -o smtpd_tls_wrappermode=yes
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
  -o smtpd_sasl_security_options=noanonymous,noplaintext
  -o smtpd_sasl_tls_security_options=noanonymous
#  -o milter_macro_daemon_name=ORIGINATING

```

/etc/default/saslauthd

```
DESC="SASL Authentication Daemon"
NAME="saslauthd"
MECHANISMS="pam"
MECH_OPTIONS=""pwcheck_method: saslauthd
mech_list: plain login cram-md5 digest-md5
log_level: 7
allow_plaintext: true
auxprop_plugin: mysql
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: mail
sql_passw: MY_MAIL_PASS
sql_database: maildb
sql_select: select crypt from users where id='%u@%r' and enabled = 1
THREADS=5
OPTIONS="-r -c -m /var/spool/postfix/var/run/saslauthd"

```

/etc/pam.d/smtp
```
auth required pam_mysql.so user=mail passwd=PASSWORD host=127.0.0.1 db=maildb table=users usercolumn=id passwdcolumn=crypt crypt=1
account sufficient pam_mysql.so user=mail passwd=PASSWORD host=127.0.0.1 db=maildb table=users usercolumn=id passwdcolumn=crypt crypt=1

```

A tail on auth.og only shows 

```
Jun 18 14:33:04 de1 postfix/smtpd[24787]: sql auxprop plugin using mysql engine
```

Again it doesn't get hit when I attempt to log on - the only change in the tailed logs is in mail.log


```
Jun 18 12:04:21 de1 postfix/smtpd[21601]: connect from xxx
Jun 18 12:04:21 de1 postfix/smtpd[21601]: warning: SASL authentication failure: no secret in database
Jun 18 12:04:21 de1 postfix/smtpd[21601]: warning: xxx: SASL CRAM-MD5 authentication failed: authentication failure
Jun 18 12:04:21 de1 postfix/smtpd[21601]: disconnect from xxx
```

Any help you can give would be great.  Thanks!

---

### Post by flurdy on 2010-06-18
Ps. You should mask you pw in the /etc/pam.d/smtp part of your post :)

And was your post of the /etc/default/saslauthd merged with /etc/postfix/sasl/smtpd.conf?

---

### Post by Mckormick on 2010-06-18
oops! :redface:

The /etc/default/saslauthd is actually

```
DESC="SASL Authentication Daemon"
NAME="saslauthd"
MECHANISMS="pam"
MECH_OPTIONS=""
mech_list: plain login cram-md5 digest-md5
log_level: 7
allow_plaintext: true
auxprop_plugin: mysql
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: mail
sql_passw: MY_MAIL_PASS
sql_database: maildb
sql_select: select crypt from users where id='%u@%r' and enabled = 1
THREADS=5
OPTIONS="-r -c -m /var/spool/postfix/var/run/saslauthd"

```
The version in the post above was just cuz of a problem with my mouse button 3 (keeps pasting when rolling!) ](*,)

I've got a bit further now - I removed 

```
smtpd_sasl_authenticated_header = yes
```

from main.cf and now from Thunderbird it works with these settings:

```
Port: 465
Secure Authentication: No
Connection Security: SSL/TLS
```

I'm not sure if this means it is working or whether I need to have 

```
Secure Authentication: Yes
```

If I switch it to yes it no longer works.

Thanks!

---

### Post by flurdy on 2010-06-18
:p

Any particular reason for why you have the contents of **/etc/postfix/sasl/smtpd.conf** in the middle of **/etc/default/saslauthd** ?? :confused:

---

### Post by Mckormick on 2010-06-18
Yes - because I need to buy a new mouse with a wheel that doesn't paste when I spin it :p

```
DESC="SASL Authentication Daemon"
NAME="saslauthd"
MECHANISMS="pam"
MECH_OPTIONS=""
THREADS=5
OPTIONS="-r -c -m /var/spool/postfix/var/run/saslauthd"
```

```
mech_list: plain login cram-md5 digest-md5
log_level: 7
allow_plaintext: true
auxprop_plugin: mysql
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: mail
sql_passw: MY_MAIL_PASS
sql_database: maildb
sql_select: select crypt from users where id='%u@%r' and enabled = 1
```

---

### Post by mcfly1204 on 2010-06-20
I have not had any luck with resolving that issue.  At this point, I am waiting for the next edition of the guide in hopes that I can start from the beginning and work my way through it successfully.

---

### Post by tahiriman on 2010-06-21
Hello,

How can i create other folder for sent, trash, drafts, ... mails in the maildir and onfigure courier imap to use them.

Thanks in advance

---

### Post by tahiriman on 2010-06-22
No idea?!!

---

### Post by oziemike on 2010-07-03
I have started again, this time using Ubuntu Server 10.04. I need to replace my old Ubuntu 6.06 server before the support runs out. I have set this one up on the bench to get it going before the swap over. I am getting the following error when trying to login from roundcube.

I did copy all the mail directories over from the old server and checked permissions etc, but keep getting this:

Jul  3 14:54:48 mail authdaemond: Installing libauthmysql
Jul  3 14:54:48 mail authdaemond: Installation complete: authmysql
Jul  3 14:54:49 mail postfix/master[1730]: daemon started -- version 2.7.0, configuration /etc/postfix
Jul  3 14:56:10 mail imapd-ssl: Connection, ip=[::1]
Jul  3 14:56:10 mail authdaemond: received auth request, service=imap, authtype=cram-md5
Jul  3 14:56:10 mail authdaemond: authmysql: trying this module
Jul  3 14:56:10 mail authdaemond: cram: challenge=PDFENDE0Q0M1REU3NDk2RjFDMjBDMUZFRkU4NTE1QTA3QG1haWwudGJwbC5jb20uYXU+, response=b3ppZW1pa2VAdGJwbC5jb20uYXUgZDA0NmM2MmE0YTg2MDVhYmU2MzFlZTkyZGVkY2IwNTE=
Jul  3 14:56:10 mail authdaemond: cram: decoded challenge/response, username 'oziemike@tbpl.com.au'
Jul  3 14:56:10 mail authdaemond: authmysqllib: connected. Versions: header 50137, client 50141, server 50141
Jul  3 14:56:10 mail authdaemond: SQL query: SELECT id, crypt, "", uid, gid, "/var/spool/mail/virtual", CONCAT(home,'/',maildir), "", name, "" FROM users WHERE id = 'oziemike@tbpl.com.au'  AND (enabled=1)
Jul  3 14:56:10 mail authdaemond: authmysql: REJECT - try next module
Jul  3 14:56:10 mail authdaemond: FAIL, all modules rejected
Jul  3 14:56:10 mail imapd-ssl: LOGIN FAILED, method=CRAM-MD5, ip=[::1]
Jul  3 14:56:15 mail imapd-ssl: Disconnected, ip=[::1], time=5, starttls=1

Roundcube naturally reports that the login failed.

Any help would be seriously appreciated.

Mike

---

### Post by Ontolog on 2010-07-14
There is a pretty major problem with the way MySQL's ENCRYPT() function is being used in conjunction with the mail server setups. Actually I had to revert to using the plaintext password for both Postfix and Courier. In the case of Postfix I also had to restrict the AUTH types to 'LOGIN' because programs that were using CRAM-MD5 were failing authentication. One major problem here is that ENCRYPT is using whatever the OS's low-level crypt() is which can be anything. Furthermore since we are not supplying any salt, the salt is random! So now we can't reproduce the crypted string since we don't know the salt.

[http://dev.mysql.com/doc/refman/5.1/en/encryption-functions.html#function_encrypt](http://dev.mysql.com/doc/refman/5.1/en/encryption-functions.html#function_encrypt)

---

### Post by liquid1911 on 2010-07-16
Did this just change with MySQL? I've spent the better part of 2 days pulling my hair out trying to understand wtf was going on. I have it working fine on 9.10 and 9.04 boxes, but 10.04 boxes get no love.

---

### Post by Ontolog on 2010-07-16
> **liquid1911 said:**
> Did this just change with MySQL? I've spent the better part of 2 days pulling my hair out trying to understand wtf was going on. I have it working fine on 9.10 and 9.04 boxes, but 10.04 boxes get no love.

It could very well be a difference in the way MySQL's ENCRYPT() worked in previous versions of Ubuntu vs. the way it works on 10.04. Again, since MySQL's ENCRYPT()'s behavior depends on the lower-level crypt() call, it can not be used reliably (unless you know exactly what crypt() is doing, you store your salt, etc).

Solutions:

a) Fall back to using the 'clear' field and switching passwords to cleartext in both Postfix and Courier. As long as you have TLS or SSL setup then the password won't be traveling over the network in cleartext. This is what I am doing.

b) Make a proper hash of the password and store that. Maybe use CRAM-MD5 for Postfix since that is pretty standard. Not sure what the standard hashing algorithms are for Courier. If I could choose any I would choose SHA-256 with random salt, and store the salt in the database along with the password to protect against rainbow table attacks.

:popcorn:

---

### Post by Ontolog on 2010-07-19
UPDATE: Actually I took out the 'crypt' column from the 'users' table since I thought I no longer needed it. In fact Postfix is still using this column and authentication was failing without it. So I guess my own understanding of the situation is lacking! LOL :( but still, I had to turn off CRAM-MD5 to get the SMTP server to work with some clients.

---

### Post by liquid1911 on 2010-07-23
Its definitely something wrong with 10.04. i followed the guide to a T, two or three times, same exact issue with the CRAM-MD5. I wiped the VM and stuck 9.10 on there, works perfectly fine with the guide. I too am lost as to what on earth is causing the crpyto to break, but something is.

---

### Post by matheszabi on 2010-07-24
I have installed an Ubuntu 10.4. I want to install a mail server to this machine.
I have google -it 2h and I didn't find a free Linux mail server all in one pack!
I need to install like 7-10 software and configure properly, test it, which I can't from the first try, for sure. I don't want to became administrator, I hate this job.

Is there any mail server bundle with free software like XAMP for web developers?

---

### Post by flurdy on 2010-07-25
> **tahiriman said:**
> Hello,

How can i create other folder for sent, trash, drafts, ... mails in the maildir and onfigure courier imap to use them.

Thanks in advance

Well I think it is more down to the mail client you use on top of courier. It is them that move/copy emails to sent,trash etc.

So e.g. if you run squirrelmail on top of courier then the option to  create special folders must be true, which I believe it is by default.

However if your intention are not to use the default names, then you should tweak the IMAP_TRASHFOLDERNAME in /etc/courier/imapd and in your mail gui for all the default special folders.

Hope that answers your question?

---

### Post by flurdy on 2010-07-25
> **liquid1911 said:**
> Its definitely something wrong with 10.04. i followed the guide to a T, two or three times, same exact issue with the CRAM-MD5. I wiped the VM and stuck 9.10 on there, works perfectly fine with the guide. I too am lost as to what on earth is causing the crpyto to break, but something is.

Ill look into this issue as well as I am trying to help oziemike with this specific issue.

My main servers are still running 9.10, due to no time to migrate them yet, so I may not have tested the 10.04 properly. :0 However when I set up a 10.04 test server (the ec2 AMIs) I did not encounter any problems.

---

### Post by zoo0828 on 2010-07-31
Hi, guys,

it might be a stupid question but it bothers me so much.

I followed this guide setting up a mail server serving multiple virtual domains, say:
domain1.com, domain2.com, domain3.com

but as for these hostnames: what name should I use?
/etc/hostname
/etc/mailname
$myhostname inside /etc/postfix/main.cf

and consequently, what EHLO will postfix submit while sending out emails to external domains?

Any ideas and thoughts will be appreciated.

---

### Post by wangkeit on 2010-07-31
how to connect the C programming language into MYSQL database..???

---

### Post by flurdy on 2010-07-31
> **zoo0828 said:**
> Hi, guys,

it might be a stupid question but it bothers me so much.

I followed this guide setting up a mail server serving multiple virtual domains, say:
domain1.com, domain2.com, domain3.com

but as for these hostnames: what name should I use?
/etc/hostname
/etc/mailname
$myhostname inside /etc/postfix/main.cf

and consequently, what EHLO will postfix submit while sending out emails to external domains?

Any ideas and thoughts will be appreciated.


There is no "right" answer, but you need to pick which is your "main" or infrastructure domain name, e.g. domain1.com, as the mail server will only respond with one fully qualified name.

Then choose  a desired name for the server and set hostname as eg. myserver.domain1.com.

Mailname and myhostname should be the same name and could reflect it is mail server so I would set them to e.g. 
mail.domain1.com. If you create your own SSL certificates, this is the name to use there as well.

If the server is only used as a mail server and nothing else then /etc/hostname could be mail.domain1.com as well.

---

### Post by zoo0828 on 2010-07-31
Great clarification, Ivar, thanks. :-)

Since the server is the only one also hosting LAMP services, I would better set all the hostnames to say, server.domain1.com

And it's a fantastic HOWTO, keep up the excellent work.

By the way, is it possible to include a few tips while using DOVECOT over Courier?

---

### Post by zoo0828 on 2010-07-31
Hi, Ivar,

One more question, :-)    looks like the localdomain mail is not working properly, please refers to the following log.

Thought it's probably because of the hostname settings.
Tried to add an alias entry like this 
@localhost.domain1.com ---> @localhost

--------------------------------------------------------------
Jul 31 12:34:12 server postfix/qmgr[2003]: F13B965A75: from=<rivers@server.domain1.com>, size=617, nrcpt=1 (queue active)
Jul 31 12:34:33 server postfix/smtp[2028]: connect to localhost.domain1.com[218.83.175.155]:25: Connection timed out
Jul 31 12:34:33 server postfix/smtp[2028]: F13B965A75: to=<root@localhost.domain1.com>, orig_to=<root@localhost>, relay=none, delay=21, delays=0.17/0.09/21/0, dsn=4.4.1, status=deferred (connect to localhost.domain1.com[218.83.175.155]:25: Connection timed out)
--------------------------------------------------------------

---

### Post by eihli on 2010-08-01
****UPDATE: FIXED****
Hopefully this will save someone else some time. Did I miss this step in the tutorial or something?
Looking back on it... this should have been a pretty easy fix.
On the last line of 
/etc/courier/imapd-ssl 
I changed 
MAILDIRPATH=Maildir 
to 
MAILDIRPATH=/var/spool/mail/virtual
********************


Thanks flurdy for the tutorial

I'm having a similar, if not the same, problem as DonGonzo and jvdl85.
When I try to login, I get:
[COLOR=#cc0000]**ERROR:**[/COLOR]** ERROR: Connection dropped by IMAP server.**

This is on 10.04

*Note: I have deleted characters from the usernames/domain names, so ignore that part of the copy/paste.

One thing I have noticed (if it makes any difference) is that if I change "MAILDIRPATH=Maildir" to "MAILDIRPATH=/var/spool/mail/virtual", then I am able to telnet to localhost:143, login, and list the folders. But, the only folder listed when i do an "a list "INBOX" "*"", it only shows as having a "SENT" folder.

Thanks ahead of time for any help.

When I try to log in to squirrelmail, here is what I get:
mail.log
```
Aug  1 11:33:50 server1 imapd-ssl: Connection, ip=[::1]
Aug  1 11:33:50 server1 imapd-ssl: chdir Maildir: No such file or directory
Aug  1 11:33:50 server1 imapd-ssl: adn@oga.com: No such file or directory

```mysql.log
```
100801 11:33:50   203 Connect   mail@localhost on
                  203 Init DB   maildb
                  203 Query     SELECT id, crypt, "", uid, gid, "/var/spool/mail/virtual", "", "", name, "" FROM users WHERE id = 'admin@owoga.com'  AND (enabled=1)

```Dir of /var/spool/mail/virtual/admin:
```
root@server1:/var/spool/mail/virtual/admin# ls -a
.  ..  cur  new  tmp

```There are several messages in new.

I have tried making DonGonzo's changes to authmysqlrc. I restarted all of the courier/postfix services (Don't know if that was necessary) but I continue to get the same errors.

Here is the entire process for a new username:
After I run the insert query for a new user:
mysql.log
```
100801 11:42:49      164 Query    INSERT INTO users (id,name,maildir,crypt) VALUES ('dli@oga.com','dli','dli/', encrypt('password') )

```After I send the new account an email:
mail.log:
```
Aug  1 11:45:54 server1 postfix/smtpd[29816]: connect from mail-iw0-f175.google.com[209.85.214.175]
Aug  1 11:45:54 server1 postfix/smtpd[29816]: 6E5FFD8334: client=mail-iw0-f175.google.com[209.85.214.175]
Aug  1 11:45:54 server1 postfix/cleanup[29820]: 6E5FFD8334: message-id=<AANLkTi=m9=bUvr9FViFqx5tULty9teYNFdF_wdn5UOU6@mail.gmail.com>
Aug  1 11:45:56 server1 postfix/qmgr[29704]: 6E5FFD8334: from=<lokah@gmail.com>, size=1832, nrcpt=1 (queue active)
Aug  1 11:45:56 server1 postfix/virtual[29821]: 6E5FFD8334: to=<di@oa.com>, relay=virtual, delay=2.1, delays=2/0.02/0/0.06, dsn=2.0.0, status=sent (delivered to maildir)
Aug  1 11:45:56 server1 postfix/qmgr[29704]: 6E5FFD8334: removed

```mysql.log:
```
100801 11:45:54   204 Connect   mail@localhost on maildb
                  204 Query     SELECT destination FROM aliases WHERE mail='gmail.com' and enabled = 1
                  205 Connect   mail@localhost on maildb
                  205 Query     SELECT domain FROM domains WHERE domain='gmail.com' and enabled = 1
                  204 Query     SELECT destination FROM aliases WHERE mail='oo.com' and enabled = 1
                  205 Query     SELECT domain FROM domains WHERE domain='oga.com' and enabled = 1
                  206 Connect   mail@localhost on maildb
                  206 Query     SELECT destination FROM aliases WHERE mail='dli@oga.com' and enabled = 1
                  206 Query     SELECT destination FROM aliases WHERE mail='dli' and enabled = 1
                  206 Query     SELECT destination FROM aliases WHERE mail='@oa.com' and enabled = 1
                  207 Connect   mail@localhost on maildb
                  207 Query     SELECT maildir FROM users WHERE id='d@ga.com' and enabled = 1
                  208 Connect   mail@localhost on maildb
                  208 Query     SELECT destination FROM aliases WHERE mail='di@oa.com' and enabled = 1

```Dir of /var/spool/mail/virtual:
```
root@server1:/var/spool/mail/virtual/d# ls -a
.  ..  cur  new  tmp
root@server1:/var/spool/mail/virtual/dli# cd new
root@server1:/var/spool/mail/virtual/dli/new# ls
1280681156.Vca01I1305f9M447310.server1.oa.com

```When I try to login to SquirrelMail:
[COLOR=#cc0000]**ERROR:**[/COLOR]** ERROR: Connection dropped by IMAP server.**

mail.log after trying to login:
```
Aug  1 11:45:56 server1 postfix/qmgr[29704]: 6E5FFD8334: removed
Aug  1 11:46:26 server1 postfix/smtpd[29816]: disconnect from mail-iw0-f175.google.com[209.85.214.175]
Aug  1 11:49:46 server1 postfix/anvil[29818]: statistics: max connection rate 1/60s for (smtp:209.85.214.175) at Aug  1 11:45:54
Aug  1 11:49:46 server1 postfix/anvil[29818]: statistics: max connection count 1 for (smtp:209.85.214.175) at Aug  1 11:45:54
Aug  1 11:49:46 server1 postfix/anvil[29818]: statistics: max cache size 1 at Aug  1 11:45:54
Aug  1 11:50:07 server1 imapd-ssl: Connection, ip=[::1]
Aug  1 11:50:07 server1 imapd-ssl: chdir Maildir: No such file or directory
Aug  1 11:50:07 server1 imapd-ssl: di@o.com: No such file or directory

```mysql.log after trying to login:
```
100801 11:50:07      210 Connect    mail@localhost on 
          210 Init DB    maildb
          210 Query    SELECT id, crypt, "", uid, gid, home, "", "", name, "" FROM users WHERE id = 'li@a.com'  AND (enabled=1)

```Telnet to localhost:143:
```
root@server1:/var/log# telnet localhost 143
Trying ::1...
Connected to localhost.localdomain.
Escape character is '^]'.
* OK [CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE ACL ACL2=UNION STARTTLS] Courier-IMAP ready. Copyright 1998-2008 Double Precision, Inc.  See COPYING for distribution information.
a login di@oa.com password
* BYE [ALERT] Fatal error: No such file or directory: No such file or directory
Connection closed by foreign host.

```

---

### Post by flurdy on 2010-08-02
> **zoo0828 said:**
> Hi, Ivar,

One more question, :-)    looks like the localdomain mail is not working properly, please refers to the following log.

Thought it's probably because of the hostname settings.
Tried to add an alias entry like this 
@localhost.domain1.com ---> @localhost

--------------------------------------------------------------
Jul 31 12:34:12 server postfix/qmgr[2003]: F13B965A75: from=<rivers@server.domain1.com>, size=617, nrcpt=1 (queue active)
Jul 31 12:34:33 server postfix/smtp[2028]: connect to localhost.domain1.com[218.83.175.155]:25: Connection timed out
Jul 31 12:34:33 server postfix/smtp[2028]: F13B965A75: to=<root@localhost.domain1.com>, orig_to=<root@localhost>, relay=none, delay=21, delays=0.17/0.09/21/0, dsn=4.4.1, status=deferred (connect to localhost.domain1.com[218.83.175.155]:25: Connection timed out)
--------------------------------------------------------------

If you intend to receive mail as [email]xxx@domain1.com[/email], then make sure you list domain1.com in the domains table. And if you prefer subdomains such as localhost.domain1.com as well make sure you list localhost.domain1.com in your domains as well, but you should perhaps just alias @localhost to @domain1.com?

---

### Post by flurdy on 2010-08-02
> **eihli said:**
> ****UPDATE: FIXED****
Hopefully this will save someone else some time. Did I miss this step in the tutorial or something?
Looking back on it... this should have been a pretty easy fix.
On the last line of 
/etc/courier/imapd-ssl 
I changed 
MAILDIRPATH=Maildir 
to 
MAILDIRPATH=/var/spool/mail/virtual
********************


Thanks flurdy for the tutorial

I'm having a similar, if not the same, problem as DonGonzo and jvdl85.
When I try to login, I get:
[COLOR=#cc0000]**ERROR:**[/COLOR]** ERROR: Connection dropped by IMAP server.**

This is on 10.04

*Note: I have deleted characters from the usernames/domain names, so ignore that part of the copy/paste.

One thing I have noticed (if it makes any difference) is that if I change "MAILDIRPATH=Maildir" to "MAILDIRPATH=/var/spool/mail/virtual", then I am able to telnet to localhost:143, login, and list the folders. But, the only folder listed when i do an "a list "INBOX" "*"", it only shows as having a "SENT" folder.

Thanks ahead of time for any help.

When I try to log in to squirrelmail, here is what I get:
mail.log
```
Aug  1 11:33:50 server1 imapd-ssl: Connection, ip=[::1]
Aug  1 11:33:50 server1 imapd-ssl: chdir Maildir: No such file or directory
Aug  1 11:33:50 server1 imapd-ssl: adn@oga.com: No such file or directory

```mysql.log
```
100801 11:33:50   203 Connect   mail@localhost on
                  203 Init DB   maildb
                  203 Query     SELECT id, crypt, "", uid, gid, "/var/spool/mail/virtual", "", "", name, "" FROM users WHERE id = 'admin@owoga.com'  AND (enabled=1)

```
....


It seems like you have not set up authmysqlrc properly. Such as 
```
MYSQL_MAILDIR_FIELD concat(home,'/',maildir)
```
because your select statement
```
SELECT id, crypt, "", uid, gid, "/var/spool/mail/virtual", "", "", name, "" FROM users WHERE id = 'admin@owoga.com'  AND (enabled=1)
```
should have been more like:
```
SELECT id, crypt, "", uid, gid, home, concat(home,'/',maildir), "", name, "" FROM users WHERE id = 'admin@owoga.com'  AND (enabled=1)
```

---

### Post by zoo0828 on 2010-08-02
> **flurdy said:**
> If you intend to receive mail as [email]xxx@domain1.com[/email], then make sure you list domain1.com in the domains table. And if you prefer subdomains such as localhost.domain1.com as well make sure you list localhost.domain1.com in your domains as well, but you should perhaps just alias @localhost to @domain1.com?

yes, that makes perfect sense, I will alias @localhost to one of the virtual domains right away. :p

---

### Post by Jose Miguel Samper on 2010-08-07
Hello,

I have just followed the Flurdy tutorial to set up a complete mail server successfully.

I programmed a simple PHP web application to manage domains and accounts.

The application is attached to this message, if someone is interested.

The application is not authenticated, so it must be protected using some web server mechanism, like AuthConfig in Apache.

---

### Post by duceduc on 2010-08-07
I am following the OP tutorial and I just finished the basic setup. Upon testing it via telnet, I get the followng error. Can someone tell me where to look at this point.
>  451 4.3.5 Server configuration error
Here is the mail.log.
```
Aug  8 00:40:09 web-server postfix/smtpd[2022]: connect from localhost[127.0.0.1]
Aug  8 00:40:47 web-server postfix/smtpd[2022]: warning: unknown smtpd restriction: **"permit_mynetwork"**
Aug  8 00:40:47 web-server postfix/smtpd[2022]: NOQUEUE: reject: RCPT from localhost[127.0.0.1]: 451 4.3.5 Server configuration error; from=<info@ducsu.com> to=<mailx@hotmail.com> proto=ESMTP helo=<web-server>
Aug  8 00:41:08 web-server postfix/smtpd[2022]: lost connection after RCPT from localhost[127.0.0.1]
Aug  8 00:41:08 web-server postfix/cleanup[2027]: E58752605BF: message-id=<20100807154108.E58752605BF@mail.domain.com>
Aug  8 00:41:09 web-server postfix/smtpd[2022]: disconnect from localhost[127.0.0.1]
Aug  8 00:41:09 web-server postfix/qmgr[1944]: E58752605BF: from=<double-bounce@mail.domain.com>, size=851, nrcpt=1 (queue active)
Aug  8 00:41:09 web-server postfix/virtual[2028]: E58752605BF: to=<root@localhost>, orig_to=<postmaster>, relay=virtual, delay=0.2, delays=0.11/0.01/0/0.08, dsn=2.0.0, status=sent (delivered to maildir)
Aug  8 00:41:09 web-server postfix/qmgr[1944]: E58752605BF: removed
Aug  8 00:47:55 web-server postfix/smtpd[2139]: connect from localhost[127.0.0.1]
Aug  8 00:48:47 web-server postfix/smtpd[2139]: warning: unknown smtpd restriction: **"permit_mynetwork"**
Aug  8 00:48:47 web-server postfix/smtpd[2139]: NOQUEUE: reject: RCPT from localhost[127.0.0.1]: 451 4.3.5 Server configuration error; from=<info@domain.com> to=<mailx@hotmail.com> proto=ESMTP helo=<web-server>

```

I've checked my typo in the postfix/main.cf files and I don't see anything wrong. Please help as I need this mail server setup.

**Edited:** I corrected my issue. There was a typo in my log highlighted in **bold**. Fixed it and now I am able to test telnet with success. I tested 3 emails each going to different accounts (gmail, hotmail, and yahoo). 
I received test emails from gmail and yahoo but not hotmail instantly. Do I have an error somewhere or it is just a delay from hotmail's end?

---

### Post by MoonArrow on 2010-08-08
Hi,

I just setup a complete server configuration using this guide and (almost) everything is working. In fact, I thought it was complete until the last test as always :)

First : Ubuntu 10.04, Postfix with MySQL backend, Courier  IMAP/POP, SMTP (authentificated) but no SSL, Amavis with clamav and Postgrey.

I succeed in creating accounts, IMAP/SMTP/POP with them. Then I setup a production configuration for the production domain and the catchup alias is broken. I configure two regular accounts. The first paul is as regular as possible. The second elric is regular but I wish also that he receive the 'catchup' emails.

So I have this :
```
mysql> describe aliases
    -> ;
+-------------+--------------+------+-----+---------+----------------+
| Field       | Type         | Null | Key | Default | Extra          |
+-------------+--------------+------+-----+---------+----------------+
| pkid        | smallint(3)  | NO   | PRI | NULL    | auto_increment |
| mail        | varchar(120) | NO   | UNI |         |                |
| destination | varchar(120) | NO   |     |         |                |
| enabled     | tinyint(1)   | NO   |     | 1       |                |
+-------------+--------------+------+-----+---------+----------------+
4 rows in set (0.00 sec)

mysql> select * from aliases;
+------+------------------------+------------------------+---------+
| pkid | mail                   | destination            | enabled |
+------+------------------------+------------------------+---------+
|    1 | postmaster@localhost   | root@localhost         |       1 |
|    2 | sysadmin@localhost     | root@localhost         |       1 |
|    3 | webmaster@localhost    | root@localhost         |       1 |
|    4 | abuse@localhost        | root@localhost         |       1 |
|    5 | root@localhost         | root@localhost         |       1 |
|    6 | @localhost             | root@localhost         |       1 |
|    7 | @localhost.localdomain | @localhost             |       1 |
|    8 | @DOMAINNAME.fr          | elric@DOMAINNAME.fr     |       1 |
+------+------------------------+------------------------+---------+
8 rows in set (0.00 sec)

```On the mail table, I have this:

```
mysql> describe users;
+-----------------+----------------------+------+-----+-------------------------+-------+
| Field           | Type                 | Null | Key | Default                 | Extra |
+-----------------+----------------------+------+-----+-------------------------+-------+
| id              | varchar(128)         | NO   | PRI |                         |       |
| name            | varchar(128)         | NO   |     |                         |       |
| uid             | smallint(5) unsigned | NO   |     | 5000                    |       |
| gid             | smallint(5) unsigned | NO   |     | 5000                    |       |
| home            | varchar(255)         | NO   |     | /var/spool/mail/virtual |       |
| maildir         | varchar(255)         | NO   |     | blah/                   |       |
| enabled         | tinyint(3) unsigned  | NO   |     | 1                       |       |
| change_password | tinyint(3) unsigned  | NO   |     | 1                       |       |
| clear           | varchar(128)         | NO   |     | ChangeMe                |       |
| crypt           | varchar(128)         | NO   |     | sdtrusfX0Jj66           |       |
| quota           | varchar(255)         | NO   |     |                         |       |
| procmailrc      | varchar(128)         | NO   |     |                         |       |
| spamassassinrc  | varchar(128)         | NO   |     |                         |       |
+-----------------+----------------------+------+-----+-------------------------+-------+
13 rows in set (0.00 sec)

mysql> select id, name, uid,gid, home, enabled from users where name like '%DOMAINNAME%';
+----------------------+----------------------+------+------+-------------------------+---------+
| id                   | name                 | uid  | gid  | home                    | enabled |
+----------------------+----------------------+------+------+-------------------------+---------+
| elric@DOMAINNAME.fr   | elric@DOMAINNAME.fr   | 5000 | 5000 | /var/spool/mail/virtual |       1 |
| paul@DOMAINNAME.fr     | paul@DOMAINNAME.fr     | 5000 | 5000 | /var/spool/mail/virtual |       1 |
+----------------------+----------------------+------+------+-------------------------+---------+


```My main.cf configuration file
```

root@sd-22214:/etc/postfix# more main.cf
# This is already done in /etc/mailname
#myhostname= mail.example.com

smtpd_banner = $myhostname ESMTP $mail_name

# leave blank to do it yourself
relayhost =

inet_interfaces = all
mynetworks_style = host


# masquerade_domains = mail.example.com www.example.com !sub.dyndomain.com 
masquerade_domains = mail.DOMAINNAME.fr www.DOMAINNAME.fr
# masquerade_exceptions = root

local_recipient_maps =
mydestination =

# how long if undelivered before sending warning update to sender
delay_warning_time = 4h
# will it be a permanent error or temporary
unknown_local_recipient_reject_code = 450
# how long to keep message on queue before return as failed.
# some have 3 days, I have 16 days as I am backup server for some people
# whom go on holiday with their server switched off.
maximal_queue_lifetime = 7d
# max and min time in seconds between retries if connection failed
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
# how long to wait when servers connect before receiving rest of data
smtp_helo_timeout = 60s
# how many address can be used in one message.
# effective stopper to mass spammers, accidental copy in whole address list
# but may restrict intentional mail shots.
smtpd_recipient_limit = 16
# how many error before back off.
smtpd_soft_error_limit = 3
# how many max errors before blocking it.
smtpd_hard_error_limit = 12


# Requirements for the HELO statement
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit

# Requirements for the sender details
# smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_u
nauth_pipelining, permit
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknow
n_sender_domain, reject_unauth_pipelining, permit

# Requirements for the connecting server
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dns
bl.njabl.org

# Requirement for the recipient address
smtpd_data_restrictions = reject_unauth_pipelining

smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipie
nt, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:10023, permit

# require proper helo at connections
smtpd_helo_required = yes
# waste spammers time before rejecting them
smtpd_delay_reject = yes
disable_vrfy_command = yes

# not sure of the difference of the next two
# but they are needed for local aliasing
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
# this specifies where the virtual mailbox folders will be located
virtual_mailbox_base = /var/spool/mail/virtual
# this is for the mailbox location for each user
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
# and this is for aliases
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
# and this is for domain lookups
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
# this is how to connect to the domains (all virtual, but the option is there)
# not used yet
# transport_maps = mysql:/etc/postfix/mysql_transport.cf

# Changes for replace the virtual map par les vrais ids
#
# Block a reactiver
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
# this specifies where the virtual mailbox folders will be located
virtual_mailbox_base = /var/spool/mail/virtual
# End of block
#virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf
#virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
# End of replacement block

content_filter = amavis:[127.0.0.1]:10024

# SASL
smtpd_sasl_auth_enable = yes
# If your potential clients use Outlook Express or other older clients
# this needs to be set to yes
broken_sasl_auth_clients = no
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =

```Of course, I checked and the aliases are working. It is like as soon as the catchup is present all the emails for this domain go to the catchall.

Does anyone have a clue for me?

Thanks in advance.

M.

---

### Post by lisati on 2010-08-08
> **duceduc said:**
> I am following the OP tutorial and I just finished the basic setup. Upon testing it via telnet, I get the followng error. Can someone tell me where to look at this point.

Here is the mail.log.
```
Aug  8 00:40:09 web-server postfix/smtpd[2022]: connect from localhost[127.0.0.1]
Aug  8 00:40:47 web-server postfix/smtpd[2022]: warning: unknown smtpd restriction: **"permit_mynetwork"**
Aug  8 00:40:47 web-server postfix/smtpd[2022]: NOQUEUE: reject: RCPT from localhost[127.0.0.1]: 451 4.3.5 Server configuration error; from=<info@ducsu.com> to=<mailx@hotmail.com> proto=ESMTP helo=<web-server>
Aug  8 00:41:08 web-server postfix/smtpd[2022]: lost connection after RCPT from localhost[127.0.0.1]
Aug  8 00:41:08 web-server postfix/cleanup[2027]: E58752605BF: message-id=<20100807154108.E58752605BF@mail.domain.com>
Aug  8 00:41:09 web-server postfix/smtpd[2022]: disconnect from localhost[127.0.0.1]
Aug  8 00:41:09 web-server postfix/qmgr[1944]: E58752605BF: from=<double-bounce@mail.domain.com>, size=851, nrcpt=1 (queue active)
Aug  8 00:41:09 web-server postfix/virtual[2028]: E58752605BF: to=<root@localhost>, orig_to=<postmaster>, relay=virtual, delay=0.2, delays=0.11/0.01/0/0.08, dsn=2.0.0, status=sent (delivered to maildir)
Aug  8 00:41:09 web-server postfix/qmgr[1944]: E58752605BF: removed
Aug  8 00:47:55 web-server postfix/smtpd[2139]: connect from localhost[127.0.0.1]
Aug  8 00:48:47 web-server postfix/smtpd[2139]: warning: unknown smtpd restriction: **"permit_mynetwork"**
Aug  8 00:48:47 web-server postfix/smtpd[2139]: NOQUEUE: reject: RCPT from localhost[127.0.0.1]: 451 4.3.5 Server configuration error; from=<info@domain.com> to=<mailx@hotmail.com> proto=ESMTP helo=<web-server>

```

I've checked my typo in the postfix/main.cf files and I don't see anything wrong. Please help as I need this mail server setup.

**Edited:** I corrected my issue. There was a typo in my log highlighted in **bold**. Fixed it and now I am able to test telnet with success. I tested 3 emails each going to different accounts (gmail, hotmail, and yahoo). 
I received test emails from gmail and yahoo but not hotmail instantly. Do I have an error somewhere or it is just a delay from hotmail's end?
I think it should be **permit_mynetworks** (with an S on the end)

---

### Post by duceduc on 2010-08-08
> **lisati said:**
> I think it should be **permit_mynetworks** (with an S on the end)

Thank you. I got it fix now. My mail server seems to be working within my home network. I am able to send and receive emails.

I have followed the guide and the mail server seems to be working. I can send emails from squirrelmail but I **cannot** receive emails. I can only receive emails from the domains I have added.

I am able to **telnet localhost 25** from the server fine. I can receive and sent mails fine. However, if I try to test send an email from my yahoo, gmail, or hotmail account, I don't receive it. Did I miss a step somewhere? I retrace the steps and it seems I have gotten them all. What log files can I see for emails coming in. I've tried looking at these below, but I don't see anything out of the ordinary.
I have setup an MX for my mail server and is sitting at zoneedit; I haven't input that ip in my settings. I don't know where actually. Would that be the cause of why emails are not coming in?  

```
/var/log/system.log
/var/log/mail.log
/var/log/mysql.log
/var/log/apache2/access.log
```

---

### Post by duceduc on 2010-08-09
Further checking the mail server and mail.log, I noticed I am getting a: **Permission denied** for ClamAV for all incoming mails. How can I fix this error. I did not touch any settings upon installing clamav by the way.
```
Aug  9 16:26:49 web-server postfix/pickup[25884]: 91D802605D5: uid=33 from=<www-data>
Aug  9 16:26:49 web-server postfix/cleanup[26229]: 91D802605D5: message-id=<20100809072649.91D802605D5@mail.ducsu.com>
Aug  9 16:26:49 web-server postfix/qmgr[25885]: 91D802605D5: from=<www-data@ducsu.com>, size=486, nrcpt=1 (queue active)
Aug  9 16:26:49 web-server amavis[25777]: (25777-01) ESMTP::10024 /var/lib/amavis/tmp/amavis-20100809T162649-25777: <www-data@ducsu.com> -> <info@ducsu.com> SIZE=486 Received: from mail.ducsu.com ([127.0.0.1]) by localhost (mail.ducsu.com [127.0.0.1]) (amavisd-new, port 10024) with ESMTP for <info@ducsu.com>; Mon,  9 Aug 2010 16:26:49 +0900 (JST)
Aug  9 16:26:49 web-server amavis[25777]: (25777-01) Checking: ZY7AEQ8VTSB0 <www-data@ducsu.com> -> <info@ducsu.com>
[b]Aug  9 16:26:49 web-server amavis[25777]: (25777-01) (!)run_av (ClamAV-clamd) FAILED - unexpected , output="/var/lib/amavis/tmp/amavis-20100809T162649-25777/parts: lstat() failed: Permission denied. ERROR\n"
Aug  9 16:26:49 web-server amavis[25777]: (25777-01) (!)ClamAV-clamd av-scanner FAILED: CODE(0xb387078) unexpected , output="/var/lib/amavis/tmp/amavis-20100809T162649-25777/parts: lstat() failed: Permission denied. ERROR\n" at (eval 115) line 594.
Aug  9 16:26:49 web-server amavis[25777]: (25777-01) (!!)WARN: all primary virus scanners failed, considering backups[/b]
Aug  9 16:26:56 web-server postfix/smtpd[26258]: connect from localhost.localdomain[127.0.0.1]
Aug  9 16:26:56 web-server postfix/smtpd[26258]: 1BEDC260690: client=localhost.localdomain[127.0.0.1]
Aug  9 16:26:56 web-server postfix/cleanup[26229]: 1BEDC260690: message-id=<20100809072649.91D802605D5@mail.ducsu.com>
Aug  9 16:26:56 web-server postfix/qmgr[25885]: 1BEDC260690: from=<www-data@ducsu.com>, size=927, nrcpt=1 (queue active)
Aug  9 16:26:56 web-server amavis[25777]: (25777-01) FWD via SMTP: <www-data@ducsu.com> -> <info@ducsu.com>,BODY=7BIT 250 2.0.0 Ok, id=25777-01, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 1BEDC260690
Aug  9 16:26:56 web-server amavis[25777]: (25777-01) Passed CLEAN, <www-data@ducsu.com> -> <info@ducsu.com>, Message-ID: <20100809072649.91D802605D5@mail.ducsu.com>, mail_id: ZY7AEQ8VTSB0, Hits: 0.01, size: 486, queued_as: 1BEDC260690, 6513 ms
Aug  9 16:26:56 web-server postfix/smtp[26231]: 91D802605D5: to=<info@ducsu.com>, orig_to=<weblog@ducsu.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=6.7, delays=0.12/0.02/0.01/6.5, dsn=2.0.0, status=sent (250 2.0.0 Ok, id=25777-01, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 1BEDC260690)
Aug  9 16:26:56 web-server postfix/qmgr[25885]: 91D802605D5: removed
Aug  9 16:26:56 web-server postfix/virtual[26259]: 1BEDC260690: to=<info@ducsu.com>, relay=virtual, delay=0.15, delays=0.07/0.02/0/0.06, dsn=2.0.0, status=sent (delivered to maildir)
Aug  9 16:26:56 web-server postfix/qmgr[25885]: 1BEDC260690: removed
Aug  9 16:31:56 web-server postfix/smtpd[26258]: timeout after END-OF-MESSAGE from localhost.localdomain[127.0.0.1]
Aug  9 16:31:56 web-server postfix/smtpd[26258]: disconnect from localhost.localdomain[127.0.0.1]
```

This is the log from clamav.log
```
Mon Aug  9 12:30:45 2010 -> WARNING: lstat() failed on: /var/lib/amavis/tmp/amavis-20100809T123045-23348/parts
Mon Aug  9 13:30:45 2010 -> SelfCheck: Database status OK.
Mon Aug  9 13:42:43 2010 -> WARNING: lstat() failed on: /var/lib/amavis/tmp/amavis-20100809T134243-23349/parts
Mon Aug  9 13:43:22 2010 -> WARNING: lstat() failed on: /var/lib/amavis/tmp/amavis-20100809T123045-23348/parts
Mon Aug  9 13:59:36 2010 -> WARNING: lstat() failed on: /var/lib/amavis/tmp/amavis-20100809T134243-23349/parts
Mon Aug  9 14:19:01 2010 -> WARNING: lstat() failed on: /var/lib/amavis/tmp/amavis-20100809T123045-23348/parts
Mon Aug  9 14:23:10 2010 -> WARNING: lstat() failed on: /var/lib/amavis/tmp/amavis-20100809T134243-23349/parts
Mon Aug  9 14:37:51 2010 -> SelfCheck: Database status OK.
Mon Aug  9 14:37:51 2010 -> WARNING: lstat() failed on: /var/lib/amavis/tmp/amavis-20100809T123045-23348/parts
Mon Aug  9 15:37:51 2010 -> SelfCheck: Database status OK.
Mon Aug  9 16:26:49 2010 -> WARNING: lstat() failed on: /var/lib/amavis/tmp/amavis-20100809T162649-25777/parts
Mon Aug  9 17:06:11 2010 -> SelfCheck: Database modification detected. Forcing reload.
Mon Aug  9 17:06:12 2010 -> Reading databases from /var/lib/clamav
Mon Aug  9 17:06:17 2010 -> Database correctly reloaded (813045 signatures)
Mon Aug  9 17:06:17 2010 -> WARNING: lstat() failed on: /var/lib/amavis/tmp/amavis-20100809T170611-25778/parts
Mon Aug  9 17:13:09 2010 -> WARNING: lstat() failed on: /var/lib/amavis/tmp/amavis-20100809T171309-27950/parts

```

I may found the answer; however, I am not sure what it is asking.
This is the link from [wiki.clamav.net]("WARNING: lstat() failed on: /var/lib/amavis/tmp/amavis-20100809T171309-27950/parts").

**edit: solved**
This [link]("http://wiki.clamav.net/bin/view/Main/FAQ#I_m_running_ClamAV_amavisd_new_a") explains it more clearly on how to fix the _permission denied_ in clamav

You need to add this to /etc/group
```
 amavis:x:105:clamav
```

Also, make sure you have this in /etc/clamav/clamd.conf
```
AllowSupplementaryGroups true
```

Restart clamav 
```
sudo /etc/init.d/clamav-daemon restart
```

---

### Post by Fludizz on 2010-08-11
No real addition to this thread but I think I have to say this:
Thanks a million for this guide, I started using this configuration guide years ago (and yes implemented it in a corporate environment as well :D) and I am still happily using this configuration. Very good guide, very clear which results in a very stable and clean mail system which is easy to manage using phpmyadmin!

---

### Post by duceduc on 2010-08-11
[Relocation notice]("http://flurdy.com/docs/postfix/#ext_reloc")
Anyone did this part? It says the sender will get a notice of new  address. 
When I tested mine, I didn't get a notice email but the new relocated address was sent. Not a big deal it didn't sent a notice to sender.

---

### Post by delaTorre on 2010-08-18
**//Update**
I read the solutions of Eihi and DonGonzo but none of them work for my, I realized that my sql query is not getting the concat(home,'/',maildir) field, but the line MYSQL_MAILDIR_FIELD concat(home,'/',maildir) is well formed. Any ideas??? Please!!!
Thanks
Here is the query:
> SELECT id, crypt, "", uid, gid, home, "", "", name, "" FROM users WHERE id = 'user1@home.local'  AND (enabled=1)
**//**

Hello, I'm having some issues with courier-imap, my server can recieve emails,  courier creates the folder with the name of the account and put the email file inside but my client (thunderbird-evolution-out.express) can not get it, this is my log file

```
Aug 18 21:08:29 home imapd: chdir Maildir: No such file or directory
Aug 18 21:08:29 home imapd: user1@home.local: No such file or directory
```The folder [EMAIL="user1@home.local"]user1@home.local[/EMAIL] exists and the folder Maildir do not exists, if I create it the client and the log do not show any error, but I still can get user1 emails. 

I guess something is wrong with the MAILDIRPATH=Maildir line in Imapd file. 

Any ideas?, 

Thank you Flurdy for this great tutorial, hope someone can help with this problem.

Sorry for my terrible english.

---

### Post by slarti42 on 2010-08-19
Hmmmm,

I have spent about 3 days on this, and read everything I can find.](*,)

These logs show two attempts to send, the first from outlook express on windoze and the other from evolution.

Server is Ubuntu 10.04

Mail log shows.
```

Aug 20 01:13:37 zarquon postfix/smtpd[27947]: connect from unknown[190.255.90.53]
Aug 20 01:13:43 zarquon postfix/smtpd[27947]: NOQUEUE: reject: RCPT from unknown[190.255.90.53]: 554 5.7.1 <unknown[190.255.90.53]>: Client host rejected: Access denied; from=<MYNEWADDRESS@sellmatix.com> to=<MYOLDADDRESS@himatix.com> proto=SMTP helo=<slarti>
Aug 20 01:13:43 zarquon postfix/smtpd[27947]: disconnect from unknown[190.255.90.53]
Aug 20 01:14:37 zarquon postfix/smtpd[27947]: connect from unknown[190.255.90.53]
Aug 20 01:14:38 zarquon postfix/smtpd[27947]: disconnect from unknown[190.255.90.53]
Aug 20 01:14:55 zarquon postfix/anvil[27954]: statistics: max connection rate 2/60s for (smtp:190.255.90.53) at Aug 20 01:05:22
Aug 20 01:14:55 zarquon postfix/anvil[27954]: statistics: max connection count 2 for (smtp:190.255.90.53) at Aug 20 01:06:19

```
auth.log shows
```

Aug 20 01:06:19 zarquon postfix/smtpd[3209]: sql auxprop plugin using mysql engine
Aug 20 01:08:19 zarquon sshd[9873]: Accepted password for root from 190.255.90.53 port 57450 ssh2
Aug 20 01:08:19 zarquon sshd[9873]: pam_unix(sshd:session): session opened for user root by (uid=0)
Aug 20 01:09:01 zarquon CRON[15500]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 20 01:09:03 zarquon CRON[15500]: pam_unix(cron:session): session closed for user root
Aug 20 01:10:44 zarquon sshd[9873]: Received disconnect from 190.255.90.53: 11: disconnected by user
Aug 20 01:10:44 zarquon sshd[9873]: pam_unix(sshd:session): session closed for user root
Aug 20 01:11:20 zarquon sshd[25847]: Accepted password for root from 190.255.90.53 port 47078 ssh2
Aug 20 01:11:20 zarquon sshd[25847]: pam_unix(sshd:session): session opened for user root by (uid=0)
Aug 20 01:17:01 zarquon CRON[21999]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 20 01:17:01 zarquon CRON[21999]: pam_unix(cron:session): session closed for user root

```mysql.log show
```

100820  1:12:32      189 Connect    mail@localhost on maildb
          190 Connect    mail@localhost on maildb
          189 Query    SELECT destination FROM aliases WHERE mail='sellmatix.com' and enabled = 1
          191 Connect    mail@localhost on maildb
          191 Query    SELECT domain FROM domains WHERE domain='sellmatix.com' and enabled = 1
          190 Query    SELECT destination FROM aliases WHERE mail='sellmatix.com' and enabled = 1
          192 Connect    mail@localhost on maildb
          192 Query    SELECT domain FROM domains WHERE domain='sellmatix.com' and enabled = 1
100820  1:13:32      189 Quit    
          191 Quit    
          190 Quit    
          192 Quit    
100820  1:13:43      193 Connect    mail@localhost on maildb
          193 Query    SELECT destination FROM aliases WHERE mail='himatix.com' and enabled = 1
          194 Connect    mail@localhost on maildb
          194 Query    SELECT domain FROM domains WHERE domain='himatix.com' and enabled = 1
100820  1:14:43      193 Quit    
          194 Quit    

```/etc/postfix.main.cf is:-
```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
myorigin = /etc/mailname
myhostname = mail.sellmatix.com

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

relayhost = 
inet_protocols = all
inet_interfaces = all
#mynetworks_style = host
#mynetworks = 127.0.0.0/8
#mynetworks = all
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128

#mydestination = sellmatix.com,localhost.sellmatix.com,localhost
local_recipient_maps =
mydestination = 

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
delay_warning_time = 4h

readme_directory = no



unknown_local_recipient_reject_code = 450

#how long to keep in queue before return as failed
maximal_queue_lifetime = 7d

#min and max time in seconds between retries if connection failed
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s

#how long to wait when servers connect before receiving rest of data
smtp_helo_timeout = 60s

#how many addresses can be stored in one message
smtpd_recipient_limit = 16

#how many soft errors before back off
smtpd_soft_error_limit = 3

#how many hard errors before blocking it
smtpd_hard_error_limit = 12

#requirements for the HELO statement
#smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
#smtpd_helo_restrictions = permit_mynetworks, reject_invalid_hostname, permit

#requirements for sender details
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit

#requirements for the connecting server
#smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
smtpd_client_restrictions = permit_sasl_authenticated, reject

#requirements for recipient address
#smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, permit
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:60000, permit

smtpd_data_restrictions = reject_unauth_pipelining

#require proper helo at connections
smtpd_helo_required = yes
# reject all connections from unauthenticated clients
smtpd_delay_reject = yes
#disable_vrfy_command = yes


# Virtual Mailbox Domain Settings
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases

#this specifies where the virtual mailbox folders will be located
virtual_mailbox_base = /var/spool/mail/virtual

#this is the for the mailbox location for each user
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf

#this is for the aliases
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf

#this is for the domain lookups
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf

#virtual_mailbox_limit = 51200000
#virtual_minimum_uid = 5000
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
virtual_transport = virtual

#additional for quota support

virtual_create_maildirsize = yes
virtual_mailbox_extended = yes
virtual_mailbox_limit_maps = mysql:/etc/postfix/mysql_virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = Your maildir has overdrawn your diskspace quota, so you need to free up some space you clot.
virtual_overquota_bounce = yes

# SASL
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.


mailbox_size_limit = 0
recipient_delimiter = +
home_mailbox = Maildir/

```Any ideas????

---

### Post by duceduc on 2010-08-19
slarti42,
Have you checked if ur isp is not blocking port 25? Try relaying to your isp and see if that works.

---

### Post by slarti42 on 2010-08-20
> **duceduc said:**
> slarti42,
Have you checked if ur isp is not blocking port 25? Try relaying to your isp and see if that works.


Thanks for the suggestion, but no, the ISP is NOT blocking port 25. I am using that all the time to connect to the old mail server.

---

### Post by slarti42 on 2010-08-20
Some progress...

/etc/init.d/saslauthd restart was generating an error, so I uninstalled sasl, and tried to reinstall, but that failed with and error:-
dpkg: syntax error: unknown user `amavis' in statoverride file

I had previously uninstalled amavis trying to eliminate possible causes. After removing the amavis entries in 
/var/lib/dpkg/statoverride I was able to reinstall sasl clean, and, suddenly IMAP started working:D

But SMTP is still failing and auth.log now shows:-
```

Aug 20 17:14:05 zarquon postfix/smtpd[5402]: sql auxprop plugin using mysql engine
Aug 20 17:14:07 zarquon saslauthd[7187]: pam_mysql - MySQL error(You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'WHERE id = 'MYNEWMAIL@sellmatix.com'' at line 1)
Aug 20 17:14:07 zarquon saslauthd[7187]: DEBUG: auth_pam: pam_authenticate failed: Error in service module
Aug 20 17:14:07 zarquon saslauthd[7187]: do_auth         : auth failure: [user=MYNEWMAIL@sellmatix.com] [service=smtp] [realm=sellmatix.com] [mech=pam] [reason=PAM auth error]

```

That seems to be referring to /etc/postfix/sasl/smtpd.conf which contains:-


```

pwcheck_method: saslauthd
mech_list: plain login cram-md5 digest-md5
log_level: 7
allow_plaintext: true
auxprop_plugin: mysql
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: mail
sql_passwd: PASSWORD
sql_database: maildb
sql_select: select crypt from users where id='%u@%r' and enabled = 1

```


Any ideas?

---

### Post by slarti42 on 2010-08-20
SOLVED!

Missing "table=users" in /etc/pam.d/smtp

---

### Post by duceduc on 2010-08-22
Checking my apache error log, I noticed this error. I have no idea what this means. Any one? 
> [Sun Aug 22 08:12:29 2010] [error] [client 127.0.0.1] PHP Notice:  unserialize(): Error at offset 255 of 255 bytes in /usr/share/squirrelmail/functions/strings.php on line 1284, referer: [http://mymaildomain.com/src/webmail.php](http://mymaildomain.com/src/webmail.php)


---

### Post by delaTorre on 2010-08-24
Does anyone know why postfix is not reading the smtp_sasl_password_maps entry?? ,my isp can not authenticated my mails because postfix is not geting the data from sasl_passwd.db. I´m at this point since 4 days ago, any ideas are welcome!
** PLEASE** someone give a hand on this !!!!!!!!!! 
this is my configuration file

```

myorigin = /etc/mailname
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
# this specifies where the virtual mailbox folders will be located 
virtual_mailbox_base = /var/spool/mail/virtual 
# this is for the mailbox location for each user 
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf 
# and this is for aliases 
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf 
# and this is for domain lookups 
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf 
# this is how to connect to the domains (all virtual, but the option is there) 
# not used yet 
# transport_maps = mysql:/etc/postfix/mysql_transport.cf

virtual_uid_maps = static:5000 
virtual_gid_maps = static:5000

myorigin = /etc/mailname
mydestination =
local_recipient_maps =
relayhost = mail.myiso.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mynetworks_style = host

##relay
smtp_sasl_auth_enabled = yes
**smtp_sasl_password_maps** = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = 
##
smtp_sasl_mechanism_filter = login
##
# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
delay_warning_time = 4h
unknown_local_recipient_reject_code = 450
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
smtp_helo_timeout = 60s
smtp_recipient_limit = 16
smtp_soft_error_limit = 3
smtpd_hard_error_limit = 12

# Requirements for the HELO statement 
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit 
# Requirements for the sender details 
#smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit 
# Add permit_sasl_authenticated to you existing  
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit 
# Requirements for the connecting server 
#smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org 
smtpd_client_restrictions = 
# Requirement for the recipient address 
#smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, permit smtpd_data_restrictions = reject_unauth_pipelining
#smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:10023, permit
# Add permit_sasl_authenticated to you existing  
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:10023, permit
# require proper helo at connections 
smtpd_helo_required = yes 
# waste spammers time before rejecting them 
smtpd_delay_reject = yes 
disable_vrfy_command = yes

readme_directory = no

# TLS parameters
#smtp_use_tls = no 
smtp_tls_security_level = may 
#smtpd_use_tls=yes 
smtpd_tls_security_level = may
#smtpd_tls_auth_only = no 
smtp_tls_note_starttls_offer = yes 
smtpd_tls_loglevel = 1 
smtpd_tls_received_header = yes 
smtpd_tls_session_cache_timeout = 3600s 
tls_random_source = dev:/dev/urandom 
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
#smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
#smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.



content_filter = amavis:[127.0.0.1]:10024

# SASL 
smtpd_sasl_auth_enable = yes
## If your potential clients use Outlook Express or other older clients 
## this needs to be set to yes 
broken_sasl_auth_clients = yes
smtpd_sasl_security_options = noanonymous 
smtpd_sasl_local_domain = 
##smtpd_sasl_local_domain = $myhostname
smtpd_sasl_path = smtpd
smtpd_sasl_password_maps = hash:/etc/postfix/sasl_passwd

```

---

### Post by 10ghost on 2010-08-28
After following the howto By flurdy
 I checked mail.log
```


 to=<ghost@domain.net>, relay=local, delay=43, delays=43/0.01/0/0.07, dsn=2.0.0, status=sent (delivered to maildir)

```

In how to if this received it mail was sent
But the folder to be created in /var/mail/virtual was not created  that is ghost.
How can one troubleshoot this problem?

---

### Post by scrooge_74 on 2010-08-29
This tutorial is sourceforge works perfectly. I used it on Friday to setup a webmail server

[http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu-10.04](http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu-10.04)

I had problems with the one at the begining of this thread.

---

### Post by q.dinar on 2010-08-31
flurdy, maybe, would be good, if you write in the tutorial, that PTR DNS record is needed to send e-mail to some mail servers. And that setting PTR record is not just like setting regular DNS records, to set PTR contact to IP address owner is needed.

---

### Post by three_jeeps on 2010-08-31
> **Mckormick said:**
> Yes - because I need to buy a new mouse with a wheel that doesn't paste when I spin it :p


Well, at least check your post carefully before you hit the send button....inaccurate postings make for a lot of 'noise' as well as
wasted time. What could have been addresses with a single exchange took 5....

---

### Post by duceduc on 2010-09-01
I got a weird problem now. My mail server was running fine until today when I used thunderbird to sent mail outside my network. The log shows that my router(GOD) is rejecting the mail? Relay access denied. I haven't changed any settings, other than updated my router's firwmare. Is there a setting in the router that I should look for? I don't understand why thunderbird is showing logs about my router where if I use squirrelmail webgui, it doesn't and my mail sent fine.

> Sep  1 23:37:10 web-server postfix/smtp[831]: D0033261268: to=<xxxx@ducsu.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=1.1, delays=0.14/0.01/0/0.9, dsn=2.0.0, status=sent (250 2.0.0 Ok, id=30126-07, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as B43D7260726)
Sep  1 23:37:10 web-server postfix/smtp[831]: D0033261268: to=<xxxx@gmail.com>, orig_to=<xxx@ducsu.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=1.1,delays=0.14/0.01/0/0.9, dsn=2.0.0, status=sent (250 2.0.0 Ok, id=30126-07, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as B43D7260726)
Sep  1 23:37:10 web-server postfix/qmgr[1837]: D0033261268: removed
Sep  1 23:37:10 web-server postfix/virtual[836]: B43D7260726: to=<xxx@ducsu.com>, relay=virtual, delay=0.18, delays=0.08/0.03/0/0.07, dsn=2.0.0, status=sent (delivered to maildir)
Sep  1 23:37:10 web-server postfix/smtp[835]: B43D7260726: to=<xxx@gmail.com>,relay=smtp.xxx.xxx.xx.jp[125.206.148.148]:25, delay=0.26 delays=0.08/0.04/0.06/0.09, dsn=2.0.0, status=sent (250 Ok: queued as E26872324)
Sep  1 23:37:11 web-server postfix/qmgr[1837]: B43D7260726: removed
Sep  1 23:38:15 web-server postfix/smtpd[32669]: connect from GOD[192.168.1.1]
Sep  1 23:38:15 web-server postfix/smtpd[32669]: NOQUEUE: reject: RCPT from GOD[192.168.1.1]: 554 5.7.1 <xxxx@hotmail.com>: Relay access denied; from=<xxxx@ducsu.com> to=<xxxx@hotmail.com> proto=ESMTP helo=<[127.0.0.1]>
Sep  1 23:39:00 web-server postfix/smtpd[32669]: disconnect from GOD[192.168.1.1]

---

### Post by phaZe~collapse on 2010-09-04
FYI for those of you using this great tutorial.  When setting up shorewall, the files in ```
/usr/share/doc/shorewall-common/default-config/
``` have moved to ```
/usr/share/doc/shorewall/default-config/
```

---

### Post by Sparky12488 on 2010-09-17
Hi I was trying to download all the programs i need from your How to guide but i am having some problems with two of them.

 
1: Authentication: Cyrus SASL
2: Encryption: TLS

I cant seem to find the downloads for these program any help would be great 

many thanks nick

---

### Post by NightFlyer_ on 2010-09-17
Hi.

Thanks for an excellent guide for setting up a complete mail-server.

I have followed your guide and now has a complete mail server set up.

Now I am thinking about backup... Yes, backup... I mean, since the server holds all my e-mails (And I have quite many) maybe I should implement a backup system.

Problem is, I don't know anything about doing so....

Anybody out there with any ideas of how to to backup the e-mails stored on the server ?

Sincerely,

Martin B.


> **flurdy said:**
> A how to for a complete step by step guide to install, configure and run 
a mail server on a GNU / Linux system 

The server includes theses programs:
Ubuntu + Postfix + Courier IMAP + MySQL + Amavisd-new + SpamAssassin + ClamAV + SASL + TLS + SquirrelMail + Postgrey



---

### Post by mmxbass on 2010-10-19
The configuration worked well for me but the spam detection is so hypersensitive that it's marking internal mail as spam. Is there a way to easily disable spam checking for mail originating from users logged in locally?

---

### Post by scrooge_74 on 2010-10-19
Yes you can setup the level of detection in SpamAssassin.

Sorry I just got home and Im too tired to think straight pass the Yes

---

### Post by Nunana on 2010-10-21
I build an E-mail server following the Step by step guide to install Postfix. All works fine. Thnx for that.
Except one thing is keeping my busy for two whole days now.
HOW DO I OPEN MORE PORTS?
I added ports in the /etc/shorewall/rules, i see them back in iptables --list-rules but it's not coming through.
SSH is going fine. But ping 10.1.0.x is unreachable.
I build a base Ubuntu server in the same 10.76.70.x than i dont have a problem to reach.

```
# Shorewall version 4 - Rules File
#
# For information on the settings in this file, type "man shorewall-rules"
#
# The manpage is also online at
# http://www.shorewall.net/manpages/shorewall-rules.html
#
####################################################################################################################################################
#ACTION         SOURCE          DEST            PROTO   DEST    SOURCE          ORIGINAL        RATE            USER/   MARK    CONNLIMIT    TIME
#                                                       PORT    PORT(S)         DEST            LIMIT           GROUP
#SECTION ESTABLISHED
#SECTION RELATED
#SECTION NEW
#
SSH/ACCEPT      net             $FW
Ping/ACCEPT     net             $FW

# Permit all ICMP traffic FROM the firewall TO the net zone
ACCEPT          $FW             net             icmp
# mail lines
SMTP/ACCEPT     net             $FW
SMTPS/ACCEPT    net             $FW
Submission/ACCEPT       net     $FW
IMAP/ACCEPT     net             $FW
IMAPS/ACCEPT    net             $FW
#web Web/
ACCEPT          net             $FW
# ntlmaps
ACCEPT          net             $FW             tcp     5865
ACCEPT          net             $FW             udp     5865
###############################################################################
```

---

### Post by Nunana on 2010-10-22
I learned to put my networks in the /etc/shorewall/zones
```
loc     eth0:10.1.0.0/24,10.70.76.0/24
```
The port I want to open in /etc/shorewall/rules
```
ACCEPT          loc             $FW             tcp     5865
ACCEPT          $FW             loc             tcp     5865
```
Restart shorewall
```
/etc/init.d/shorewall restart
```
For me this works.

---

### Post by cent.mox on 2010-10-25
MYSQL_MAILDIR_FIELD concat(home,'/',maildir)
made my day ;-)
I am Happy!!!!
thanks

---

### Post by maxB2510 on 2010-11-23
First of all I'd like to thank so much for flurdy's great tutorial and all the other help from the posts in this thread!

I've on very specific and short question left: Is it possible to allow IMAP and/or POP3 protocol specifically for each user? 
It may happen that I don't want some user to use space on my server and for that only allow him to use the POP3-protocol.

I'd really appreciate some help :-)

---

### Post by duceduc on 2010-11-30
I've noticed clamav has issue an update recommendation version of 96.5. We are currently at 9.6.3. Has anyone updated their clamav app, if so can you provided a run down on how you upgrade and reconfigure the mail server to scan your emails? I failed to make it work.

---

### Post by Tom_T on 2011-02-21
As someone who is considering coming from a Windows Mail Server to Linux, this looks a great guide.

Couple of questions :

can inbound mail be filtered and stopped using a simple if "EHLO/HELO doesn't contain . " drop and blacklist

Can we do IMAP Filtering, check headers, body and subject and then move specific matching mail to a users IMAP / SubFolder ?

Last one. Is there an option for a simple GUI for the logs ?

Thanks

---

### Post by fedef63 on 2011-02-27
> **Villu said:**
> Thanks for a great tutorial, Flurdy!
 
I have managed to complement Flurdy's tutorial such that virtual transport is swapped for maildrop and spam is automatically delivered to a spam folder.
 
It is based on the excellent tutorial by Flurdy and complemented by parts of the tutorial found here: [http://daemonforums.org/showthread.php?t=193](http://daemonforums.org/showthread.php?t=193)
 
The latter tutorial also contains methods to implement vacation messaging.
 
If in doubt, check out the forementioned tutorial.
 
Here's what I did:
 
Complete Flurdy's tutorial and install maildrop
 
uncomment in main.cf:
```
transport_maps = mysql:/etc/postfix/mysql_transport.cf
```and add
```
maildrop_destination_recipient_limit = 1
```Master.cf file should contain the following line, change the user field to virtual:
```
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=virtual argv=/usr/bin/maildrop -d ${recipient}
```create mysql_transport.cf file and set the correct owner and permissions:
```
user=mail
password=changeme
dbname=maildb
table=domains
select_field=transport
where_field=domain
hosts=127.0.0.1
additional_conditions = and enabled = 1
```
create:
```
# cd /var/spool/mail/virtual/
# chmod +s /usr/bin/maildrop
# touch .mailfilter
# chmod 600 .mailfilter
# mkdir mailfilters
# chmod 700 mailfilters
# chown -R virtual:virtual .mailfilter mailfilters
```test maildrop and check logs:
```
echo "test" | maildrop -V 9 -d you@example.com
```Edit the ...virtual/.mailfilter file (haven't tested this bit):
```
# Deliver to Inbox or Spam box (create spam box if it does not exist)
if (/^X-Spam-Flag: YES/:h)
{
    `test -d $DEFAULT/.junkmail`
    if ($RETURNCODE == 1)
    {
        `/usr/bin/maildirmake -f junkmail $DEFAULT`
        `echo "junkmail" >> $DEFAULT/subscriptions`
    }
    exception {
        to "$DEFAULT/.junkmail"
    }
    # if all else fails, do regular delivery
    exception {
        to "$DEFAULT"
    }
}

```Now use phpmyadmin and change domain transport field from "virtual:" to "maildrop:"
 
Restart postfix, check log files and pray :)
 
Much of the code here is curtesy of hamba from daemonforums.org
 
Hope this helps!
 
Cheers, Villu
 
 
Hello,
I've installed a mailserver followinhg Flurdy's document. Thanks Flurdy.
Next i have followed your instructions about maildrop, but I'm unable to make it working.
 
Before all, I've have a doubt:
 
during the install of the mailserver the package it's not installed.
 
what package do you have used: ?
 
maildrop or courier-maildrop
 
I've tried both with two differenent result.
Using courier-maildrop, when i execute the test:
echo "test" | maildrop -V 9 -d myemail@mydomain
 
in the mailbox i get a mail
 
as soon i change the transport in mysql from "virtual:" to "maildrop:"
I don't get anymore mail  i sent to myself.
 
on the mail log there is: delivered via maildrop service
 
What I noticed, under the directory: /var/spool/mail/virtual a file called "Maildir" get created and it's containing the mail i sent.
 
 
Any idea ?
 
Thanks
regards
federico

---

### Post by fedef63 on 2011-02-27
> **Villu said:**
> Thanks for a great tutorial, Flurdy!

I have managed to complement Flurdy's tutorial such that virtual transport is swapped for maildrop and spam is automatically delivered to a spam folder.

It is based on the excellent tutorial by Flurdy and complemented by parts of the tutorial found here: [http://daemonforums.org/showthread.php?t=193](http://daemonforums.org/showthread.php?t=193)

The latter tutorial also contains methods to implement vacation messaging.

If in doubt, check out the forementioned tutorial.

Here's what I did:

Complete Flurdy's tutorial and install maildrop

uncomment in main.cf:
```
transport_maps = mysql:/etc/postfix/mysql_transport.cf
```and add
```
maildrop_destination_recipient_limit = 1
```Master.cf file should contain the following line, change the user field to virtual:
```
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=virtual argv=/usr/bin/maildrop -d ${recipient}
```create mysql_transport.cf file and set the correct owner and permissions:
```
user=mail
password=changeme
dbname=maildb
table=domains
select_field=transport
where_field=domain
hosts=127.0.0.1
additional_conditions = and enabled = 1
```
create:
```
# cd /var/spool/mail/virtual/
# chmod +s /usr/bin/maildrop
# touch .mailfilter
# chmod 600 .mailfilter
# mkdir mailfilters
# chmod 700 mailfilters
# chown -R virtual:virtual .mailfilter mailfilters
```test maildrop and check logs:
```
echo "test" | maildrop -V 9 -d you@example.com
```Edit the ...virtual/.mailfilter file (haven't tested this bit):
```
# Deliver to Inbox or Spam box (create spam box if it does not exist)
if (/^X-Spam-Flag: YES/:h)
{
    `test -d $DEFAULT/.junkmail`
    if ($RETURNCODE == 1)
    {
        `/usr/bin/maildirmake -f junkmail $DEFAULT`
        `echo "junkmail" >> $DEFAULT/subscriptions`
    }
    exception {
        to "$DEFAULT/.junkmail"
    }
    # if all else fails, do regular delivery
    exception {
        to "$DEFAULT"
    }
}

```Now use phpmyadmin and change domain transport field from "virtual:" to "maildrop:"

Restart postfix, check log files and pray :)

Much of the code here is curtesy of hamba from daemonforums.org

Hope this helps!

Cheers, Villu
Hello,
I've installed a mailserver followinhg Flurdy's document. Thanks Flurdy.
Next i have followed your instructions about maildrop, but I'm unable to make it working.

Before all, I've have a doubt:

during the install of the mailserver the package it's not installed.

what package do you have used: ?

maildrop or courier-maildrop

I've tried both with two differenent result.
Using courier-maildrop, when i execute the test:
echo "test" | maildrop -V 9 -d myemail@mydomain

in the mailbox i get a mail

as soon i change the transport in mysql from "virtual:" to "maildrop:"
I don't get anymore mail i sent to myself.

on the mail log there is: delivered via maildrop service

What I noticed, under the directory: /var/spool/mail/virtual a file called "Maildir" get created and it's containing the mail i sent.


Any idea ?

Thanks
regards
federico

---

### Post by tonyofthewoods on 2011-02-27
I've gone through the tutorial up to where all the basics should be up and running. From the server box itself I can telnet in and send email. I can receive email. I can see my received email from a client machine in Thunderbird. But I cannot send email from Thunderbird. I get "The mail server responded:  5.7.1 <test@destination.com>: Relay access denied. Please check the message recipient [email]test@destination.com[/email] and try again.". I'm guessing that it's not the recipient that's really causing the problem - I think that courier isn't talking nicely to postfix. I've turned on verbose debugging in postfix/smtpd and I see this sort of conversation going on:


```
EHLO [192.168.1.2]
 > unknown[80.175.115.177]: 250-bagpuss.localdomain
 > unknown[80.175.115.177]: 250-PIPELINING
 > unknown[80.175.115.177]: 250-SIZE 10240000
 match_list_match: unknown: no match
 match_list_match: 80.175.115.177: no match
 > unknown[80.175.115.177]: 250-ETRN
 > unknown[80.175.115.177]: 250-ENHANCEDSTATUSCODES
 > unknown[80.175.115.177]: 250-8BITMIME
 > unknown[80.175.115.177]: 250 DSN
 < unknown[80.175.115.177]: MAIL FROM:<sender@mynewdomain.com> SIZE=454
 extract_addr: input: <sender@mynewdomain.com>
 smtpd_check_addr: addr=sender@mynewdomain.com
 connect to subsystem private/rewrite
 send attr request = rewrite
 send attr rule = local
 send attr address = sender@mynewdomain.com
 private/rewrite socket: wanted attribute: flags
 input attribute name: flags
 input attribute value: 0
 private/rewrite socket: wanted attribute: address
 input attribute name: address
 input attribute value: sender@mynewdomain.com
 private/rewrite socket: wanted attribute: (list terminator)
 input attribute name: (end)
 rewrite_clnt: local: sender@mynewdomain.com -> sender@mynewdomain.com
 send attr request = resolve
 send attr sender =
 send attr address = sender@mynewdomain.com
 private/rewrite socket: wanted attribute: flags
 input attribute name: flags
 input attribute value: 0
 private/rewrite socket: wanted attribute: transport
 input attribute name: transport
 input attribute value: virtual
 private/rewrite socket: wanted attribute: nexthop
 input attribute name: nexthop
 input attribute value: mynewdomain.com
 private/rewrite socket: wanted attribute: recipient
 input attribute name: recipient
 input attribute value: sender@mynewdomain.com
 private/rewrite socket: wanted attribute: flags
 input attribute name: flags
 input attribute value: 1024
 private/rewrite socket: wanted attribute: (list terminator)
 input attribute name: (end)
 resolve_clnt: `' -> `sender@mynewdomain.com' -> transp=`virtual' host=`mynewdomain.com' rcpt=`sender@mynewdomain.com' flags= class=virtual
 ctable_locate: install entry key sender@mynewdomain.com
 extract_addr: in: <sender@mynewdomain.com>, result: sender@mynewdomain.com
 fsspace: .: block size 1024, blocks free 3696436
 smtpd_check_queue: blocks 1024 avail 3696436 min_free 0 msg_size_limit 10240000
 > unknown[80.175.115.177]: 250 2.1.0 Ok
 < unknown[80.175.115.177]: RCPT TO:<test@destination.com>
 extract_addr: input: <test@destination.com>
 smtpd_check_addr: addr=test@destination.com
 send attr request = rewrite
 send attr rule = local
 send attr address = test@destination.com
 private/rewrite socket: wanted attribute: flags
 input attribute name: flags
 input attribute value: 0
 private/rewrite socket: wanted attribute: address
 input attribute name: address
 input attribute value: test@destination.com
 private/rewrite socket: wanted attribute: (list terminator)
 input attribute name: (end)
 rewrite_clnt: local: test@destination.com -> test@destination.com
 send attr request = resolve
 send attr sender =
 send attr address = test@destination.com
 private/rewrite socket: wanted attribute: flags
 input attribute name: flags
 input attribute value: 0
 private/rewrite socket: wanted attribute: transport
 input attribute name: transport
 input attribute value: smtp
 private/rewrite socket: wanted attribute: nexthop
 input attribute name: nexthop
 input attribute value: techie.com
 private/rewrite socket: wanted attribute: recipient
 input attribute name: recipient
 input attribute value: test@destination.com
 input attribute value: test@destination.com
 private/rewrite socket: wanted attribute: flags
 input attribute name: flags
 input attribute value: 4096
 private/rewrite socket: wanted attribute: (list terminator)
 input attribute name: (end)
 resolve_clnt: `' -> `test@destination.com' -> transp=`smtp' host=`techie.com' rcpt=`test@destination.com' flags= class=default
 ctable_locate: install entry key test@destination.com
 extract_addr: in: <test@destination.com>, result: test@destination.com
 send attr request = rewrite
 send attr rule = local
 send attr address = double-bounce
 private/rewrite socket: wanted attribute: flags
 input attribute name: flags
 input attribute value: 0
 private/rewrite socket: wanted attribute: address
 input attribute name: address
 input attribute value: double-bounce@mynewdomain.com
 private/rewrite socket: wanted attribute: (list terminator)
 input attribute name: (end)
 rewrite_clnt: local: double-bounce -> double-bounce@mynewdomain.com
 >>> START Recipient address RESTRICTIONS <<<
 generic_checks: name=permit_mynetworks
 permit_mynetworks: unknown 80.175.115.177
 match_hostname: unknown ~? 127.0.0.0/8
 match_hostaddr: 80.175.115.177 ~? 127.0.0.0/8
 match_hostname: unknown ~? [::ffff:127.0.0.0]/104
 match_hostaddr: 80.175.115.177 ~? [::ffff:127.0.0.0]/104
 match_hostname: unknown ~? [::1]/128
 match_hostaddr: 80.175.115.177 ~? [::1]/128
 match_list_match: unknown: no match
 match_list_match: 80.175.115.177: no match
 generic_checks: name=permit_mynetworks status=0
 generic_checks: name=reject_unauth_destination
 reject_unauth_destination: test@destination.com
 permit_auth_destination: test@destination.com
 ctable_locate: leave existing entry key test@destination.com
 NOQUEUE: reject: RCPT from unknown[80.175.115.177]: 554 5.7.1 <test@destination.com>: Relay access denied; from=<sender@mynewdomain.com> to=<test@destination.com> proto=ESMTP helo=<[192.168.1.2]>
```

I think this is trying to tell me that courier isn't successfully starting a TLS session. But I'm not really sure. If not - why would that be? Your input much appreciated.

---

### Post by fedef63 on 2011-02-28
> 
[ >>> START Recipient address RESTRICTIONS <<<
generic_checks: name=permit_mynetworks
permit_mynetworks: unknown 80.175.115.177
match_hostname: unknown ~? 127.0.0.0/8
match_hostaddr: 80.175.115.177 ~? 127.0.0.0/8
match_hostname: unknown ~? [::ffff:127.0.0.0]/104
match_hostaddr: 80.175.115.177 ~? [::ffff:127.0.0.0]/104
match_hostname: unknown ~? [::1]/128
match_hostaddr: 80.175.115.177 ~? [::1]/128
match_list_match: unknown: no match
match_list_match: 80.175.115.177: no match
generic_checks: name=permit_mynetworks status=0
generic_checks: name=reject_unauth_destination
reject_unauth_destination: [EMAIL="test@destination.com"]test@destination.com[/EMAIL]
permit_auth_destination: [EMAIL="test@destination.com"]test@destination.com[/EMAIL]
ctable_locate: leave existing entry key [EMAIL="test@destination.com"]test@destination.com[/EMAIL]
NOQUEUE: reject: RCPT from unknown[80.175.115.177]: 554 5.7.1 <test@destination.com>: Relay access denied; from=<sender@mynewdomain.com> to=<test@destination.com> proto=ESMTP helo=<[192.168.1.2]>[/CODE]
 
I think this is trying to tell me that courier isn't successfully starting a TLS session. But I'm not really sure. If not - why would that be? Your input much appreciated.
 
 
Hello,
for a test purpose, i think you can just add the Ip address (80.175.115.177) or the subnet where you are coming 80.175.115.0/24 in the file /etc/postfix/main.cf and reload postfix   sudo /etc/init.d/postfix reload
 
 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 80.175.115.177/32 
 
This shoudl fix your issue, since the address will be considered a local address and not blocked by the restriction. Obviously this is not a good config for a production server.
 
Hope this help.
Regards
Federico

---

### Post by tonyofthewoods on 2011-02-28
Huge thanks for this Federico - I can't tell you what a pleasure it is just to see something working. Quite right this is not enough for a production system, though.

What I can't quite understand - cos there are a few bits where Flurdy's doc is just a tiny bit vague - having got to the minimally configured stage should I be able to use a mail client to send mail using smtp/starttls or is that only going to be possible once I've got all the sasl stuff configured up?

Because now I don't know whether to try and debug my current setup or to push on with the next area of work in the doc.

Many thanks, beautiful people.

---

### Post by fedef63 on 2011-02-28
Hello,
I've followed all the Flurdy's document and  he  did really a big work.
I've been able to make working almost everything listed there, except SASL, since I think I've not understood what password to use.  Anyhow, i do not want use SASL for users authentication. TLS/SSL would be ok and it do not require SASL.
To answer to your question: Yes you will be able to implement smtp/starttls/ssl. Without Sasl
Regards
Federico

---

### Post by duceduc on 2011-02-28
fedef63:

Did you ever got maildrop to work? If so which of the maildrop version you used? I am about to setup this up and would like to know the steps. Thanks.

---

### Post by fedef63 on 2011-03-01
Hi Duceduc,
unfortunately I've not been able to make Maildrop working, in the post #364 or 365 above indeed I'm asking help about, since the document lack of some informations..example what maildrop has been used if courier-maildrop or standalone package..
 the doc i followed is linked to Flurdy's document...
here the link  [http://ubuntuforums.org/showpost.php?p=7278296&postcount=223](http://ubuntuforums.org/showpost.php?p=7278296&postcount=223) 
it is in the same in my post post above
 
Regards

---

### Post by fedef63 on 2011-03-01
> **tonyofthewoods said:**
> Huge thanks for this Federico - I can't tell you what a pleasure it is just to see something working. Quite right this is not enough for a production system, though.
 
What I can't quite understand - cos there are a few bits where Flurdy's doc is just a tiny bit vague - having got to the minimally configured stage should I be able to use a mail client to send mail using smtp/starttls or is that only going to be possible once I've got all the sasl stuff configured up?
 
Because now I don't know whether to try and debug my current setup or to push on with the next area of work in the doc.
 
Many thanks, beautiful people.
 
Hi,
I wish just to tell you, that I've also Sasl working.
The value in the field "user" and "password" in the file /etc/pam.d/smtp are the same used to access maildb. And now it 's working.
I was thinking i must select "use crypted password" in the smtp panel of thunderbird. probably it was a bad assumption.
 
Mar  2 00:00:27 mail postfix/smtpd[2940]: 4508DC150E: client=unknown[192.168.254.2], sasl_method=PLAIN, [EMAIL="sasl_username=pluto@xxx.it"]sasl_username=pluto@xxx.it[/EMAIL] 
 
Regards

---

### Post by khaeru on 2011-03-05
I'm curious&#8212;is everyone implementing this guide on EC2 using 'small' instances? Has anyone tried on a 'micro' instance, or any other size? If so, please share.

---

### Post by flurdy on 2011-03-07
> **khaeru said:**
> I'm curious—is everyone implementing this guide on EC2 using 'small' instances? Has anyone tried on a 'micro' instance, or any other size? If so, please share.

My current server postfix servers on ec2 are all micro. The memory footprint of postfix++ is tiny.

---

### Post by jlsm on 2011-03-10
Hi,

Firstly, I would like to give a big Kudos to flurdy for an excellent how to.

I am relatively a beginner Ubuntu user, and was currently tasked to create a mail server for our small office. The how-to was a great resource for this project.

Initally, I was able to make the setup work until the Basic setup, I tested everything and it works: using telnet to EHLO and send mail, using webmail both within the network and outside the network, and even using Outlook on my Windoze laptop, again both from inside and outside the network.

My problem arose when I proceeded to the Advanced Mail Setup. Everything still seems to be working except when using a mail client on another PC. When using Thunderbird on the server to test, I can send and receive mail without any problems. When using Outlook or Thunderbird on my laptop, I can't login, but webmail (and even telnet) on the same laptop works. Upon setting up Thunderbird, it can automatically detect the servers, IMAP on port 143 and SMTP on port 25, but cannot login to the server. I'm guessing authentication is causing the problems. I've been working on this for days now and reading on different posts and sites, but still with no luck.

I can post the config files if anyone should need it. Any help would be greatly appreciated.

Thanks again for the invaluable how-to.


jlsm

---

### Post by jlsm on 2011-03-10
Bump.

Hope someone could help. I really need this coz i've driven to a blank right now.

Thanks.

jlsm

---

### Post by fedef63 on 2011-03-11
> **fedef63 said:**
> Hi,
I wish just to tell you, that I've also Sasl working.
The value in the field "user" and "password" in the file /etc/pam.d/smtp are the same used to access maildb. And now it 's working.
I was thinking i must select "use crypted password" in the smtp panel of thunderbird. probably it was a bad assumption.
 
Mar 2 00:00:27 mail postfix/smtpd[2940]: 4508DC150E: client=unknown[192.168.254.2], sasl_method=PLAIN, [EMAIL="sasl_username=pluto@xxx.it"]sasl_username=pluto@xxx.it[/EMAIL] 
 
Regards
 
If somebody using roundcube after SASL is enabled, if using SMTPS  port  465 to send mail will get an error SMTP Error 554.
To solve it..here the few changes required in roundcube config:
 
// use this host for sending mails.
// to use SSL connection, set ssl://smtp.host.com
// if left blank, the PHP mail() function is used
// Use %h variable as replacement for user's IMAP hostname
$rcmail_config['smtp_server'] = 'ssl://localhost';
 
// SMTP port (default is 25; 465 for SSL)
$rcmail_config['smtp_port'] = 465;
// SMTP username (if required) if you use %u as the username RoundCube
// will use the current username for login
$rcmail_config['smtp_user'] = '%u';
// SMTP password (if required) if you use %p as the password RoundCube
// will use the current user's password for login
$rcmail_config['smtp_pass'] = '%p';
// SMTP AUTH type (DIGEST-MD5, CRAM-MD5, LOGIN, PLAIN or empty to use
// best server supported one)
$rcmail_config['smtp_auth_type'] = 'PLAIN';

---

### Post by fedef63 on 2011-03-11
Hi jlsm,
please post your postifx config: master.cf and main.cf , 
and /etc/shorewall/rules
 
Do you have enabled the ports required in the firewall (shorewall) ?
 
I'm not an expert but i will have a look if I can Help.
regards
Federico

---

### Post by jlsm on 2011-03-14
Thanks so much for looking into this Federico.

I also tried using clear passwd, but it's still not authenticating. I was able to make it work using POP3, but not using SASL, i'm afraid it might be prone to attacks or interception.

I'm still working on a testbed, not the production server yet, until I'm sure it is secure and stable.

Following are the main and master config files, as well the the shorewall rules.

*I removed some of the commented lines in the config files (not all to retain section breaks)*

*main.cf*
```

myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

append_dot_mydomain = no

readme_directory = no

smtp_tls_security_level = may
smtpd_tls_security_level = may
smtp_tls_note_starttls_offer = yes
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt

smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes

btree:${data_directory}/smtpd_scache
btree:${data_directory}/smtp_scache


myhostname = subdomain.domain.com  #I used a subdomain with an A and MX record, registered at freedns.afraid.org
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination =
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
home_mailbox = Maildir/
mailbox_command =

mynetworks_style = host

masquerade_domains = mail.subdomain.domain.com
masquerade_exceptions = root

local_recipient_maps =

delay_warning_time = 4h

unknown_local_recipient_reject_code = 450

maximal_queue_lifetime = 3d
bounce_queue_lifetime = 3d

minimal_backoff_time = 900s
maximal_backoff_time = 1800s

smtp_helo_timeout = 60s

smtpd_recipient_limit = 16

smtpd_soft_error_limit = 3

smtpd_hard_error_limit = 12

smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit

smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit

smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org

smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:10023, permit
smtpd_data_restrictions = reject_unauth_pipelining

smtpd_helo_required = yes

smtpd_delay_reject = yes
disable_vrfy_command = yes
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
option is there) 

virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
inet_protocols = all

content_filter = amavis:[127.0.0.1]:10024
Secure mail server, authentication section

smtpd_sasl_auth_enable = no  # I changed this to no to accept clear passwd

broken_sasl_auth_clients = no
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =
```


*master.cf*
```

==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd
submission inet n       -       n       -       -       smtpd
#  -o smtpd_tls_security_level=encrypt
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_tls_auth_only=yes
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject_unauth_destination, reject
  -o smtpd_sasl_security_options=noanonymous,noplaintext
  -o smtpd_sasl_tls_security_options=noanonymous
#  -o milter_macro_daemon_name=ORIGINATING
smtps     inet  n       -       -       -       -       smtpd
  -o smtpd_tls_wrappermode=yes
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_tls_auth_only=yes
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
  -o smtpd_sasl_security_options=noanonymous,noplaintext
  -o smtpd_sasl_tls_security_options=noanonymous
#  -o milter_macro_daemon_name=ORIGINATING
#628       inet  n       -       -       -       -       qmqpd


pickup    fifo  n       -       -       60      1       pickup

#### added below 'pickup' transport service as prescribed by the tutorial
	-o content_filter=
	-o receive_override_options=no_header_body_checks
#### end of addition

cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       -       300     1       oqmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
proxywrite unix -       -       n       -       1       proxymap
smtp      unix  -       -       -       -       -       smtp
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay     unix  -       -       -       -       -       smtp
	-o smtp_fallback_relay=
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
#
# ====================================================================
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
====================================================================
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
#
# Other external delivery methods.
#
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix	-	n	n	-	2	pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}

#### This section is added as prescribed in the tutorial
amavis	unix	-	-	-	-	2	smtp
	-o smtp_data_done_timeout=1200
	-o smtp_send_xforward_command=yes
	-o disable_dns_lookups=yes
	-o max_use=20

#### Continuation of added section
127.0.0.1:10025	inet	n	-	-	-	-	smtpd
	-o content_filter=
	-o local_recipient_maps=
	-o relay_recipient_maps=
	-o smtpd_restriction_classes=
	-o smtpd_delay_reject=no
	-o smtpd_client_restrictions=permit_mynetworks,reject
	-o smtpd_helo_restrictions=
	-o smtpd_sender_restrictions=
	-o smtpd_recipient_restrictions=permit_mynetworks,reject
	-o smtpd_data_restrictions=reject_unauth_pipelining
	-o smtpd_end_of_data_restrictions=
	-o mynetworks=127.0.0.0/8
	-o smtpd_error_sleep_time=0
	-o smtpd_soft_error_limit=1001
	-o smtpd_hard_error_limit=1000
	-o smtpd_client_connection_count_limit=0
	-o smtpd_client_connection_rate_limit=0
	-o receive_override_options=no_header_body_checks,no_unknown_recipient_checks
#### End of added section

```

*shorewall rules*
```
#
# Shorewall version 4 - Rules File
#
# For information on the settings in this file, type "man shorewall-rules"
#
# The manpage is also online at
# http://www.shorewall.net/manpages/shorewall-rules.html
#
####################################################################################################################################################
#ACTION		SOURCE		DEST		PROTO	DEST	SOURCE		ORIGINAL	RATE		USER/	MARK	CONNLIMIT	TIME
#							PORT	PORT(S)		DEST		LIMIT		GROUP
#SECTION ESTABLISHED
#SECTION RELATED
SECTION NEW
SSH/ACCEPT	net		$FW

Ping/ACCEPT 	net 		$FW 

# Permit all ICMP traffic FROM the firewall TO the net zone 
ACCEPT 		$FW 		net 	icmp 

# mail lines 
SMTP/ACCEPT 	net 		$FW 
SMTPS/ACCEPT 	net 		$FW 
Submission/ACCEPT net 		$FW 
IMAP/ACCEPT 	net 		$FW 
IMAPS/ACCEPT 	net 		$FW 
POP3/ACCEPT	net		$FW

#web 
Web/ACCEPT 	net 		$FW

```

Again, thank you for taking time to look into this. Kindly let me know if you need anything else.


jlsm

---

### Post by sixstorm on 2011-03-14
I followed the basic Dovecot+Postfix+SquirrelMail how-tos over at help.ubuntu.com and I now have a sandbox, internal only email server.  Very easy to setup, I figured it would be something extremely complicated TBH.  I'm not tempted to buy a domain name and SSL to try and get to work with it.

---

### Post by fedef63 on 2011-03-14
> **jlsm said:**
> Thanks so much for looking into this Federico.
 
I also tried using clear passwd, but it's still not authenticating. I was able to make it work using POP3, but not using SASL, i'm afraid it might be prone to attacks or interception.
 
I'm still working on a testbed, not the production server yet, until I'm sure it is secure and stable.
 
Following are the main and master config files, as well the the shorewall rules.
 
*I removed some of the commented lines in the config files (not all to retain section breaks)*
 
*main.cf*
```

myorigin = /etc/mailname
 
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
 
append_dot_mydomain = no
 
readme_directory = no
 
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtp_tls_note_starttls_offer = yes
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt
 
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
 
btree:${data_directory}/smtpd_scache
btree:${data_directory}/smtp_scache
 
 
myhostname = subdomain.domain.com  #I used a subdomain with an A and MX record, registered at freedns.afraid.org
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination =
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
home_mailbox = Maildir/
mailbox_command =
 
mynetworks_style = host
 
masquerade_domains = mail.subdomain.domain.com
masquerade_exceptions = root
 
local_recipient_maps =
 
delay_warning_time = 4h
 
unknown_local_recipient_reject_code = 450
 
maximal_queue_lifetime = 3d
bounce_queue_lifetime = 3d
 
minimal_backoff_time = 900s
maximal_backoff_time = 1800s
 
smtp_helo_timeout = 60s
 
smtpd_recipient_limit = 16
 
smtpd_soft_error_limit = 3
 
smtpd_hard_error_limit = 12
 
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
 
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
 
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
 
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:10023, permit
smtpd_data_restrictions = reject_unauth_pipelining
 
smtpd_helo_required = yes
 
smtpd_delay_reject = yes
disable_vrfy_command = yes
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
option is there) 
 
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
inet_protocols = all
 
content_filter = amavis:[127.0.0.1]:10024
Secure mail server, authentication section
 
smtpd_sasl_auth_enable = no  # I changed this to no to accept clear passwd
 
broken_sasl_auth_clients = no
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =
```
 
 
*master.cf*
```

==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd
submission inet n       -       n       -       -       smtpd
#  -o smtpd_tls_security_level=encrypt
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_tls_auth_only=yes
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject_unauth_destination, reject
  -o smtpd_sasl_security_options=noanonymous,noplaintext
  -o smtpd_sasl_tls_security_options=noanonymous
#  -o milter_macro_daemon_name=ORIGINATING
smtps     inet  n       -       -       -       -       smtpd
  -o smtpd_tls_wrappermode=yes
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_tls_auth_only=yes
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
  -o smtpd_sasl_security_options=noanonymous,noplaintext
  -o smtpd_sasl_tls_security_options=noanonymous
#  -o milter_macro_daemon_name=ORIGINATING
#628       inet  n       -       -       -       -       qmqpd
 
 
pickup    fifo  n       -       -       60      1       pickup
 
#### added below 'pickup' transport service as prescribed by the tutorial
    -o content_filter=
    -o receive_override_options=no_header_body_checks
#### end of addition
 
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       -       300     1       oqmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
proxywrite unix -       -       n       -       1       proxymap
smtp      unix  -       -       -       -       -       smtp
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay     unix  -       -       -       -       -       smtp
    -o smtp_fallback_relay=
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
#
# ====================================================================
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
====================================================================
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
#
# Other external delivery methods.
#
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix    -    n    n    -    2    pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}
 
#### This section is added as prescribed in the tutorial
amavis    unix    -    -    -    -    2    smtp
    -o smtp_data_done_timeout=1200
    -o smtp_send_xforward_command=yes
    -o disable_dns_lookups=yes
    -o max_use=20
 
#### Continuation of added section
127.0.0.1:10025    inet    n    -    -    -    -    smtpd
    -o content_filter=
    -o local_recipient_maps=
    -o relay_recipient_maps=
    -o smtpd_restriction_classes=
    -o smtpd_delay_reject=no
    -o smtpd_client_restrictions=permit_mynetworks,reject
    -o smtpd_helo_restrictions=
    -o smtpd_sender_restrictions=
    -o smtpd_recipient_restrictions=permit_mynetworks,reject
    -o smtpd_data_restrictions=reject_unauth_pipelining
    -o smtpd_end_of_data_restrictions=
    -o mynetworks=127.0.0.0/8
    -o smtpd_error_sleep_time=0
    -o smtpd_soft_error_limit=1001
    -o smtpd_hard_error_limit=1000
    -o smtpd_client_connection_count_limit=0
    -o smtpd_client_connection_rate_limit=0
    -o receive_override_options=no_header_body_checks,no_unknown_recipient_checks
#### End of added section

```
 
*shorewall rules*
```
#
# Shorewall version 4 - Rules File
#
# For information on the settings in this file, type "man shorewall-rules"
#
# The manpage is also online at
# http://www.shorewall.net/manpages/shorewall-rules.html
#
####################################################################################################################################################
#ACTION        SOURCE        DEST        PROTO    DEST    SOURCE        ORIGINAL    RATE        USER/    MARK    CONNLIMIT    TIME
#                            PORT    PORT(S)        DEST        LIMIT        GROUP
#SECTION ESTABLISHED
#SECTION RELATED
SECTION NEW
SSH/ACCEPT    net        $FW
 
Ping/ACCEPT     net         $FW 
 
# Permit all ICMP traffic FROM the firewall TO the net zone 
ACCEPT         $FW         net     icmp 
 
# mail lines 
SMTP/ACCEPT     net         $FW 
SMTPS/ACCEPT     net         $FW 
Submission/ACCEPT net         $FW 
IMAP/ACCEPT     net         $FW 
IMAPS/ACCEPT     net         $FW 
POP3/ACCEPT    net        $FW
 
#web 
Web/ACCEPT     net         $FW

```
 
Again, thank you for taking time to look into this. Kindly let me know if you need anything else.
 
 
jlsm
 
 
Hi,
 
I had a look to your configuration and the only strange things i seen so far are: (on /etc/postfix/main.cf)
 
>home_mailbox = Maildir/
 
>mailbox_command =
 
>inet_protocols = all
 
>smtpd_sasl_auth_enable = no # I changed this to no to accept clear passwd
 
 
 
 
my working SASL is configured as the guide.
 
etc/postfix/main.cf 
# SASL
smtpd_sasl_auth_enable = yes
# If your potential clients use Outlook Express or other older clients
# this needs to be set to yes
broken_sasl_auth_clients = no
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =
 
/etc/postfix/sasl/smtpd.conf
pwcheck_method: saslauthd
mech_list: plain login cram-md5 digest-md5
log_level: 7
allow_plaintext: true
auxprop_plugin: mysql
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: mail
sql_passw: mailPASSWORD
sql_database: maildb
sql_select: select crypt from users where id='%u@%r' and enabled = 1
 
/etc/pam.d/smtp
auth required pam_mysql.so user=mail passwd=mailPASSWORD host=127.0.0.1 db=maildb table=users usercolumn=id passwdcolumn=crypt crypt=1
account sufficient pam_mysql.so user=mail passwd=mailPASSWORD host=127.0.0.1 db=maildb table=users usercolumn=id passwdcolumn=crypt crypt=1
 
 
what do you see in the logs when trying to connect ?
 
tail -f /var/log/mail.log 
 
must be something helpful there ...
 
I would aso suggest to ad your local network   to the end of  this setting in main.cf
 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
 
If SASL is not working i doubt you can connect from other computer without your local network there.
 
 
Regards

---

### Post by jlsm on 2011-03-15
Hi again fed,

I'm out of the office right now where I have my mail server testbed. I'll post the mail.log when I get back next week. Hope you can still help me by then.

Thanks.

jlsm

---

### Post by lister171254 on 2011-03-19
Followed the Guide and setup virtuals, so the postconf -n output does not show everything, I guess

I have tested the server internal via telnet and it works.

As my ISP blocks inbound smtp I'm using Mail Reflector to forward the mails to my server

Following are some of the errors I get

Mar 20 10:25:18 MusicPc postfix/smtpd[6861]: NOQUEUE: reject: RCPT from mail1.no-ip.com[204.16.252.100]: 451 4.3.5 Server configuration problem; from=<thelists@optusnet.com.au> to=<poldi@zudiewiener.com> proto=ESMTP helo=<mail1.no-ip.com>
Mar 20 10:25:18 MusicPc postfix/smtpd[6861]: disconnect from mail1.no-ip.com[204.16.252.100]
Mar 20 10:26:58 MusicPc postfix/smtpd[6861]: connect from mail1.no-ip.com[204.16.252.100]
Mar 20 10:27:00 MusicPc postfix/smtpd[6864]: lost connection after UNKNOWN from localhost[127.0.0.1]
Mar 20 10:27:00 MusicPc postfix/smtpd[6864]: disconnect from localhost[127.0.0.1]


Postfix config is
-------------------------------
alias_database = hash:/etc/postfix/aliases
alias_maps = hash:/etc/postfix/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
content_filter = amavis:[127.0.0.1]:10024
disable_vrfy_command = yes
html_directory = /usr/share/doc/postfix/html
inet_interfaces = all
local_recipient_maps = 
mailbox_size_limit = 0
maximal_backoff_time = 8000s
maximal_queue_lifetime = 7d
message_size_limit = 102400
minimal_backoff_time = 1000s
mydestination = 
myhostname = ml.zudiewiener.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mynetworks_style = host
myorigin = /etc/mailname
readme_directory = /usr/share/doc/postfix
recipient_delimiter = +
relayhost = 
smtp_helo_timeout = 60s
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_delay_reject = yes
smtpd_hard_error_limit = 12
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
smtpd_recipient_limit = 40
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:10025, permit
smtpd_sasl_local_domain = 
smtpd_sasl_security_options = noanonymous
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_soft_error_limit = 3
smtpd_tls_cert_file = /etc/postfix/postfix.cert
smtpd_tls_key_file = /etc/postfix/postfix.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
unknown_local_recipient_reject_code = 450
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_gid_maps = static:5000
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = static:5000
-------------------------------------

the domains in mysql are localhost, localhost.localdomain, zudiewiener.com, ml.zudiewiener.com

Appreciate any help in solving this.

Thanks

---

### Post by 2briancox on 2011-03-24
I have been using this guide and I am at the point where I was doing the mysql setup where the instructions read:

# If not already done (in package installation)... 
mysqladmin -u root password *new_password* 
# log in as root 
mysql -u root -p 
# then enter password for the root account when prompted Enter password: 
# then we create the mail database 
create database maildb; 
# then we create a new user: "mail" 
GRANT SELECT,INSERT,UPDATE,DELETE,CREATE,DROP 
ON maildb.* TO 'mail'@'localhost' IDENTIFIED by '*mailPASSWORD*'; 
GRANT SELECT,INSERT,UPDATE,DELETE,CREATE,DROP 
ON maildb.* TO 'mail'@'%' IDENTIFIED by '*mailPASSWORD*'; 
exit;

Well, I have never edited a mysql input so I didn't know much about it.  I had messed up on one of the lines didn't put in a semi-colon.  I tried to retype the line to fix it.  But I couldn't tell if that worked.  Then even "exit;" didn't do anything.  I finally couldn't figure out how to change anything so I thought I'd just quit the terminal window and start again.

But when I get back into mysql I can't create database maildb; because it already exists.

How do I approach getting back on track here?

---

### Post by fedef63 on 2011-03-25
Hello,
do the following:
mysql -u root -p
when asked type the password you have used during setup
drop database maildb;
create database maildb;
 
[FONT=Courier New]GRANT SELECT,INSERT,UPDATE,DELETE,CREATE,DROP ON maildb.* TO 'mail'@'localhost' IDENTIFIED by '*mailPASSWORD*'; GRANT SELECT,INSERT,UPDATE,DELETE,CREATE,DROP ON maildb.* TO 'mail'@'%' IDENTIFIED by '*mailPASSWORD*'; exit;[/FONT]
[FONT=Courier New][/FONT] 
[FONT=Courier New]whith it you will create the maildb DB[/FONT]
[FONT=Courier New]next [/FONT]
[FONT=Courier New]mysql -u mail -p maildb [/FONT]
[FONT=Courier New]as password type mailPASSWORD[/FONT]
[FONT=Courier New][/FONT] 
[FONT=Courier New]next [/FONT]you can proceed adding the rest of the db setting
 
Regards
Fedef

---

### Post by 2briancox on 2011-03-25
Thanks.

Just got the book PHP & MySQL for Dummies to get that line "drop database maildb;"

I think I better do some reading to be my own email admin.  =)

---

### Post by lucaspr on 2011-03-28
Why should you drop a database which is already there? 

Correct me if I'm wrong but just don't recreate the database and just grant the user the appropriate rights.

---

### Post by lucaspr on 2011-03-28
> **lister171254 said:**
> Followed the Guide and setup virtuals, so the postconf -n output does not show everything, I guess

I have tested the server internal via telnet and it works.

As my ISP blocks inbound smtp I'm using Mail Reflector to forward the mails to my server

Following are some of the errors I get

Mar 20 10:25:18 MusicPc postfix/smtpd[6861]: NOQUEUE: reject: RCPT from mail1.no-ip.com[204.16.252.100]: 451 4.3.5 Server configuration problem; from=<thelists@optusnet.com.au> to=<poldi@zudiewiener.com> proto=ESMTP helo=<mail1.no-ip.com>
Mar 20 10:25:18 MusicPc postfix/smtpd[6861]: disconnect from mail1.no-ip.com[204.16.252.100]
Mar 20 10:26:58 MusicPc postfix/smtpd[6861]: connect from mail1.no-ip.com[204.16.252.100]
Mar 20 10:27:00 MusicPc postfix/smtpd[6864]: lost connection after UNKNOWN from localhost[127.0.0.1]
Mar 20 10:27:00 MusicPc postfix/smtpd[6864]: disconnect from localhost[127.0.0.1]


Postfix config is
-------------------------------
alias_database = hash:/etc/postfix/aliases
alias_maps = hash:/etc/postfix/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
content_filter = amavis:[127.0.0.1]:10024
disable_vrfy_command = yes
html_directory = /usr/share/doc/postfix/html
inet_interfaces = all
local_recipient_maps = 
mailbox_size_limit = 0
maximal_backoff_time = 8000s
maximal_queue_lifetime = 7d
message_size_limit = 102400
minimal_backoff_time = 1000s
mydestination = 
myhostname = ml.zudiewiener.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mynetworks_style = host
myorigin = /etc/mailname
readme_directory = /usr/share/doc/postfix
recipient_delimiter = +
relayhost = 
smtp_helo_timeout = 60s
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_delay_reject = yes
smtpd_hard_error_limit = 12
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
smtpd_recipient_limit = 40
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:10025, permit
smtpd_sasl_local_domain = 
smtpd_sasl_security_options = noanonymous
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_soft_error_limit = 3
smtpd_tls_cert_file = /etc/postfix/postfix.cert
smtpd_tls_key_file = /etc/postfix/postfix.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
unknown_local_recipient_reject_code = 450
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_gid_maps = static:5000
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = static:5000
-------------------------------------

the domains in mysql are localhost, localhost.localdomain, zudiewiener.com, ml.zudiewiener.com

Appreciate any help in solving this.

Thanks

Are you using SSL?

---

### Post by 2briancox on 2011-04-06
I'm at this point in the guide: 

```
cd /etc/courier 

openssl req -x509 -newkey rsa:1024 -keyout imapd.pem \ -out imapd.pem -nodes -days 999 
```
I get the following error:

```
unknown option  -out
req [options] <infile >outfile

```I have no idea what to do.  I'm stuck.

---

### Post by 2briancox on 2011-04-10
I should explain that the section being referred to in that question is in the section regarding encryption (TLS). 

Also, on a side note, I am trying to add a CUPS print server to this same machine.  Does anyone know the firewall settings that would need to be added to the shorewall settings listed in this guide to get it to work?  I can't discover the shared printer here yet.  Thanks.

---

### Post by cazador2011 on 2011-04-13
> **2briancox said:**
> I'm at this point in the guide: 

```
cd /etc/courier 

openssl req -x509 -newkey rsa:1024 -keyout imapd.pem \ -out imapd.pem -nodes -days 999 
```I get the following error:

```
unknown option  -out
req [options] <infile >outfile

```I have no idea what to do.  I'm stuck.


This is what you want:

```
cd /etc/courier 

openssl req -x509 -newkey rsa:1024 -keyout imapd.pem -out imapd.pem -nodes -days 999 
```

---

### Post by spackard on 2011-04-25
I built a server using ami-c0ee06a9 and was seeing errors attributed to authdaemond.

mail.log.1:Apr 21 17:02:56 ip-10-212-82-179 authdaemond: SQL query: SELECT id, crypt, "", uid, gid, home, contact(home,'/',maildir), "", name, "" FROM users WHERE id = 'packard'  AND (enabled=1)
mail.log.1:Apr 21 17:02:56 ip-10-212-82-179 authdaemond: mysql_query failed, reconnecting: FUNCTION maildb.contact does not exist
mail.log.1:Apr 21 17:02:56 ip-10-212-82-179 authdaemond: mysql_query failed second time, giving up: FUNCTION maildb.contact does not exist

I traced the problem to /etc/courier/authmysqlrc.
Original: MYSQL_MAILDIR_FIELD   contact(home,'/',maildir)
Correction:  MYSQL_MAILDIR_FIELD   CONCAT(home,'/',maildir)

I guess this was noticed/posted about on page 30.  Sorry for the duplicate info.

---

### Post by glacebeast on 2011-06-14
Has anyone figured out an elegant solution to the problem outlined by Ontolog and oziemike a few pages back that *isn't* reverting to storing plaintext passwords and dropping down to PLAIN and LOGIN auth methods?

> There is a pretty major problem with the way MySQL's ENCRYPT() function  is being used in conjunction with the mail server setups. Actually I had  to revert to using the plaintext password for both Postfix and Courier.  In the case of Postfix I also had to restrict the AUTH types to 'LOGIN'  because programs that were using CRAM-MD5 were failing authentication.  One major problem here is that ENCRYPT is using whatever the OS's  low-level crypt() is which can be anything. Furthermore since we are not  supplying any salt, the salt is random! So now we can't reproduce the  crypted string since we don't know the salt.I found myself running into the same issues when trying to negotiate an authorized login via any method that was not LOGIN. For example, trying to login through roundcube:

```
Jun 14 01:59:03 authdaemond: received auth request, service=imap, authtype=cram-md5
Jun 14 01:59:03 authdaemond: authmysql: trying this module
Jun 14 01:59:03 authdaemond: cram: challenge=PDczQTVGNEI0NjI2NkVBQjE3NTQxMjY4QzYwMEFFQTRBQHNtdHAuZHJ1bmtiYWJpZXMuY29tPg==, response=Zm9ydW1zQGRydW5rYmFiaWVzLmNvbSBiNGVhOGI5ZThlMzdjMDE3NjAxOWUxOTIyZGRjZTM5Nw==
Jun 14 01:59:03 authdaemond: cram: decoded challenge/response, username 'forums@xxxxx.com'
Jun 14 01:59:03 authdaemond: authmysqllib: connected. Versions: header 50137, client 50141, server 50141
Jun 14 01:59:03 authdaemond: SQL query: SELECT id, crypt, "", uid, gid, home, concat(home,'/',maildir), "", name, "" FROM users WHERE id = 'forums@xxxx.com'  AND (enabled=1 )
Jun 14 01:59:03 authdaemond: authmysql: REJECT - try next module
Jun 14 01:59:03 authdaemond: FAIL, all modules rejected
Jun 14 01:59:03 imapd-ssl: LOGIN FAILED, method=CRAM-MD5, ip=[::1]
Jun 14 01:59:08 imapd-ssl: Disconnected, ip=[::1], time=5, starttls=1

```Also, when trying to send a mass e-mail through my phpBB3 setup with any auth method other than LOGIN, I get:

```
Jun 14 02:09:41 postfix/smtpd[1985]: connect from xxxxx.com[127.0.1.1]
Jun 14 02:09:41 postfix/smtpd[1985]: warning: SASL authentication failure: no secret in database
Jun 14 02:09:41 postfix/smtpd[1985]: warning: xxxx.com[127.0.1.1]: SASL CRAM-MD5 authentication failed: authentication failure
Jun 14 02:09:41 postfix/smtpd[1985]: lost connection after AUTH from xxxxx.com[127.0.1.1]
Jun 14 02:09:41 postfix/smtpd[1985]: disconnect from xxxx.com[127.0.1.1]

```I must say, I'm a little disappointed that:

1) the problems were brought up ~10 pages ago and kind of faded away with out any more dialogue about them
2) I spent the better part of 4 days scouring my configuration and setup thinking I did something wrong and just stumbled on those tidbits... haha.

Thoughts?

*Edit: As an edit, I just wanted to reiterate that, although not a newcomer to computing in any facet, I'm very new to ubuntu and mailservers in general so I wanted to ensure that my server and it's users would be free from possible malicious activity. Thanks.

*Edit 2: Does 11.04 better support this deployment? I noticed in earlier pages people were claiming no issues with 9.xx ubuntu but as soon as they upgraded to 10.xx problems started.

---

### Post by highbomber on 2011-06-19
My mail server currently can't make any folders. It is only creating the inbox. If I try to create a folder remotely I get an error, and if I try to e-mail I get an error saying something along the lines of, "Could not create sendmail folder." Has anyone experienced this? Can someone help me with this? Thanks.

---

### Post by highbomber on 2011-06-20
Bump.

---

### Post by sprior on 2011-06-22
I've also run into the CRAM problem mentioned above when setting up SASL/TLS on an Ubuntu 10.04 machine (64 bit).  Is there a current best recommendation to work around this problem?  Is SASL actually necessary when TLS is required for all connections?  There is a strong desire to use an Ubuntu LTS release when setting up a mail server, but has anyone checked yet to see if this problem persists with Ubuntu 11.04?

---

### Post by glacebeast on 2011-06-22
> I've also run into the CRAM problem mentioned above when setting up  SASL/TLS on an Ubuntu 10.04 machine (64 bit).  Is there a current best  recommendation to work around this problem?

I just disabled CRAM-MD5 in the courier-imap config and all seems to be  running smooth; whether or not that is a smart solution, I can't really  answer that. I do have a webmail client running and this is the only way  I could make it work, but the data isn't sensitive and as long as the  passwords aren't transmitted in plaintext I'm ok with it.

  > Is SASL actually necessary  when TLS is required for all connections? 

I was thinking the same thing; per my understanding, SASL is just another layer of protection... a compliment if you will. Most of us are paranoid enough to probably want maximum security though, lol.

> There is a strong desire to  use an Ubuntu LTS release when setting up a mail server, but has anyone  checked yet to see if this problem persists with Ubuntu 11.04?

My thoughts exactly. I haven't cause I run a completely headless server sans an ethernet connection, so upgrading is a bit of a hassle. However, if it would enable a ramp up in security I'd almost definitely do it.

With that said, my knowledge of all of this is probably amateur at best compared to some of those lurking out there, and I was hoping we could suck some of those folk in here to answer some of these concerns.

---

### Post by airtonix on 2011-06-23
It would be useful if you started your guide with : 

> 
**Customise the editor you want**

    ```
export $EDITOR=nano
```



Then through out the document use 

```
$EDITOR something something something
```

instead of assuming people want to use vi...

vi makes me rage HARD. I want to kill kittens when i use it.

---

### Post by mikeleonard on 2011-06-23
SO valuable information .i also searching for these valuable informations.

---

### Post by karka91 on 2011-06-29
I followed your instructions on the tutorial however when I want to send an email not from the server (using an email client) I get rejected:
> Jun 30 00:54:30 servername postfix/smtpd[32289]: NOQUEUE: reject: RCPT from --.kava.lt[my-ip]: 554 5.7.1 <--@gmail.com>: Relay access denied; from=<karolis@--.ie> to=<--@gmail.com> proto=ESMTP helo=<[server-ip]>


```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = --.ie
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = --.ie
mydestination =
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mynetworks_style = host
local_recipient_maps =

# how long if undelivered before sending warning update to sender
delay_warning_time = 4h
# will it be a permanent error or temporary
unknown_local_recipient_reject_code = 450
# how long to keep message on queue before return as failed.
# some have 3 days, I have 16 days as I am backup server for some people
# whom go on holiday with their server switched off.
maximal_queue_lifetime = 7d
# max and min time in seconds between retries if connection failed
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
# how long to wait when servers connect before receiving rest of data
smtp_helo_timeout = 60s
# how many address can be used in one message.
# effective stopper to mass spammers, accidental copy in whole address list
# but may restrict intentional mail shots.
smtpd_recipient_limit = 16
# how many error before back off.
smtpd_soft_error_limit = 3
# how many max errors before blocking it.
smtpd_hard_error_limit = 12

# Requirements for the HELO statement
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
# Requirements for the sender details
smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
# Requirements for the connecting server
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
# Requirement for the recipient address
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, perm$
smtpd_data_restrictions = reject_unauth_pipelining

# require proper helo at connections
smtpd_helo_required = yes
# waste spammers time before rejecting them
smtpd_delay_reject = yes
disable_vrfy_command = yes

# not sure of the difference of the next two
# but they are needed for local aliasing
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
# this specifies where the virtual mailbox folders will be located
virtual_mailbox_base = /var/spool/mail/virtual
# this is for the mailbox location for each user
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
# and this is for aliases
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
# and this is for domain lookups
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
# this is how to connect to the domains (all virtual, but the option is there)
# not used yet
# transport_maps = mysql:/etc/postfix/mysql_transport.cf

virtual_uid_maps = static:5000
virtual_gid_maps = static:5000


```
What should be changed so that sending email via client would be possible? Not only for me but for registered users in the database

---

### Post by sprior on 2011-07-03
After getting the described server setup working I discovered that Courier has a hardcoded IMAP namespace which the default Android email client does not handle properly.  Because Android is a strong requirement for my server I have decided to replace Courier with Dovecot.

So far I'm having trouble getting started in how to configure Dovecot for the same MySQL based authentication described in this article with Ubuntu 10.04.  Does anyone know if a variation of this article exists with Dovecot support?

---

### Post by highbomber on 2011-07-31
I am trying to do the same with Dovecot. 

I am following this guide: [http://wiki.dovecot.org/HowTo/DovecotLDAPostfixAdminMySQL](http://wiki.dovecot.org/HowTo/DovecotLDAPostfixAdminMySQL)

I am trying to meld it with Flurdy's tutorial but so far I am having no luck. This guide has a poor explanation of the variables it needs.

So far I do have Dovecot talking to MySQL, but I still can't authorize any accounts against my database.

EDIT

It's now working. Two things that were stopping me:

1. Make sure "disable_plaintext_auth = no" It makes no sense to try debugging your server while using certificates. You can do that stuff after your SMTP, IMAP, and POP3 servers are working correctly
2. Your crypt field must have used MD5() and not encrypt() like in Flurdy's guide.

Here are the two query's I modified to work with Flurdy's database model.

user_query = SELECT concat('/var/spool/mail/virtual/', maildir) as home, concat('maildir:/var/spool/mail/virtual/', maildir) as mail, 5000 as uid, 5000 as gid, concat('maildir:storage=', quota) AS quota FROM users WHERE id = '%u' AND enabled = '1'

password_query = SELECT id as user, crypt as password, concat('/var/spool/mail/virtual/', maildir) as userdb_home, concat('maildir:/var/spool/mail/virtual/', maildir) as userdb_mail, uid as userdb_uid, gid as userdb_gid FROM users WHERE id = '%u' AND enabled = '1'

I hope that helps. Follow the guide I linked very carefully and you should be able to figure it out. If anyone wants a more detailed explanation to supplement Flurdy's guide then I will make one.

EDIT2

After working more with Dovecot, I feel I have to mention a few more things:

3. "disable_plaintext_auth = no" should only be off if you are using TLS, and even then you should be hashing your password.
4. Don't use MD5, since it has inherit weaknesses. Use Dovecot's SSHA256 scheme. It is safer, however, I am having difficulty making it compatible with other programs.

Right now I am trying to get Dovecot to use a custom scheme. If anyone has experience with Hash functions, Crypt, and libc let me know please.

EDIT3

Also, one big plus to using Dovecot is you do not need saslauthd. One less application is one less point of failure IMO.

---

### Post by dfansler on 2011-08-15
Hi delaTorre - did you ever get an answer or figure out the reason behind :
Aug 18 21:08:29 home imapd: chdir Maildir: No such file or directory
Aug 18 21:08:29 home imapd: [email]user1@home.local[/email]: No such file or directory
 
I have the same problem.
Thanks,
David

---

### Post by crnieto05 on 2011-09-21
Sorry.

---

### Post by crnieto05 on 2011-09-21
Hello.
I will like to know how resolve this problem.

---

### Post by crnieto05 on 2011-09-21
> **hctopcu said:**
> I'm a newbee. Your guide is extremely helpfull thank you.
I have a running apache server on my machine. I am afraid of messing up so I skipped setting up firewall for now.

I managed to set up Courier IMAP. I can log in through imap but when I try to send mails, I get:
```
Dec 17 13:09:13 mygitarapp postfix/smtpd[24035]: connect from unknown[88.235.53.100]
Dec 17 13:09:13 mygitarapp postfix/smtpd[24035]: NOQUEUE: reject_warning: RCPT from unknown[88.235.53.100]: 504 5.5.2 <ArGoNNB>: Helo command rejected: need fully-qualified hostname; from=<gunman@mygitar.com> to=<c@gri.in> proto=ESMTP helo=<ArGoNNB>
Dec 17 13:09:13 mygitarapp postfix/smtpd[24035]: NOQUEUE: reject: RCPT from unknown[88.235.53.100]: 554 5.7.1 <c@gri.in>: Relay access denied; from=<gunman@mygitar.com> to=<c@gri.in> proto=ESMTP helo=<ArGoNNB>
Dec 17 13:09:13 mygitarapp postfix/smtpd[24035]: NOQUEUE: reject_warning: RCPT from unknown[88.235.53.100]: 504 5.5.2 <ArGoNNB>: Helo command rejected: need fully-qualified hostname; from=<gunman@mygitar.com> to=<c@gri.in> proto=ESMTP helo=<ArGoNNB>
Dec 17 13:09:13 mygitarapp postfix/smtpd[24035]: NOQUEUE: reject: RCPT from unknown[88.235.53.100]: 554 5.7.1 <c@gri.in>: Relay access denied; from=<gunman@mygitar.com> to=<c@gri.in> proto=ESMTP helo=<ArGoNNB>
Dec 17 13:09:13 mygitarapp postfix/smtpd[24035]: NOQUEUE: reject_warning: RCPT from unknown[88.235.53.100]: 504 5.5.2 <ArGoNNB>: Helo command rejected: need fully-qualified hostname; from=<gunman@mygitar.com> to=<hctopcu@gmail.com> proto=ESMTP helo=<ArGoNNB>
Dec 17 13:09:13 mygitarapp postfix/smtpd[24035]: NOQUEUE: reject: RCPT from unknown[88.235.53.100]: 554 5.7.1 <hctopcu@gmail.com>: Relay access denied; from=<gunman@mygitar.com> to=<hctopcu@gmail.com> proto=ESMTP helo=<ArGoNNB>
Dec 17 13:09:14 mygitarapp postfix/smtpd[24035]: disconnect from unknown[88.235.53.100]
```I can't understand why a client need to have a hostname. (As I said I'm a rookie)

I will like to know how resolve this problem.

---

### Post by KriBaBa on 2011-09-22
Hiya, I'm trying to get a hang on this.. But there's a lof of stuff I don't understand. 
Well.. 
I followed the guide, but for some reason it's not working. 
I only did the first part so far (the basic setup) and without firewall (It's a cloud server and I can change firewall setting elsewhere). 
For now I have not restricted port 25 at all. 

Anyway, I tried to use telnet to send a mail as the guide tell you to, but something is wrong. 
Here's the result of the tails
```

root@ubuntu:/# tail -f /var/log/mail.log
Sep 22 14:21:29 ubuntu postfix/qmgr[12335]: 7D23A21C1E: removed
Sep 22 14:21:57 ubuntu postfix/smtpd[20677]: disconnect from localhost[127.0.0.1]
Sep 22 14:26:32 ubuntu imapd: Connection, ip=[::ffff:127.0.0.1]
Sep 22 14:28:11 ubuntu postfix/smtpd[20792]: warning: 186.213.77.50: hostname 186.213.77.50.static.host.gvt.net.br verification failed: Name or service not known
Sep 22 14:28:11 ubuntu postfix/smtpd[20792]: connect from unknown[186.213.77.50]
Sep 22 14:28:33 ubuntu postfix/smtpd[20792]: lost connection after UNKNOWN from unknown[186.213.77.50]
Sep 22 14:28:33 ubuntu postfix/smtpd[20792]: disconnect from unknown[186.213.77.50]
Sep 22 14:31:53 ubuntu postfix/anvil[20793]: statistics: max connection rate 1/60s for (smtp:186.213.77.50) at Sep 22 17:28:11
Sep 22 14:31:53 ubuntu postfix/anvil[20793]: statistics: max connection count 1 for (smtp:186.213.77.50) at Sep 22 17:28:11
Sep 22 14:31:53 ubuntu postfix/anvil[20793]: statistics: max cache size 1 at Sep 22 17:28:11
Sep 22 14:54:12 ubuntu postfix/smtpd[21121]: connect from localhost[127.0.0.1]
Sep 22 14:56:28 ubuntu postfix/smtpd[21121]: 58A6B21B62: client=localhost[127.0.0.1]
Sep 22 14:56:38 ubuntu postfix/cleanup[21138]: 58A6B21B62: message-id=<20110922175628.58A6B21B62@mail.envisionenglish.com.br>
Sep 22 14:56:38 ubuntu postfix/qmgr[12335]: 58A6B21B62: from=<kristianbbach@gmail.com>, size=360, nrcpt=1 (queue active)
Sep 22 14:56:38 ubuntu postfix/virtual[21142]: 58A6B21B62: to=<klaus/@envisionenglish.com.br>, orig_to=<klaus@envisionenglish.com.br>, relay=virtual, delay=41, delays=41/0.02/0/0.05, dsn=5.1.1, status=bounced (unknown user: "klaus/@envisionenglish.com.br")
Sep 22 14:56:38 ubuntu postfix/cleanup[21138]: CC51B21C12: message-id=<20110922175638.CC51B21C12@mail.envisionenglish.com.br>
Sep 22 14:56:38 ubuntu postfix/qmgr[12335]: CC51B21C12: from=<>, size=2376, nrcpt=1 (queue active)
Sep 22 14:56:38 ubuntu postfix/bounce[21144]: 58A6B21B62: sender non-delivery notification: CC51B21C12
Sep 22 14:56:38 ubuntu postfix/qmgr[12335]: 58A6B21B62: removed
Sep 22 14:56:41 ubuntu postfix/smtp[21145]: CC51B21C12: to=<kristianbbach@gmail.com>, relay=gmail-smtp-in.l.google.com[74.125.45.27]:25, delay=2.6, delays=0.01/0.02/0.96/1.6, dsn=2.0.0, status=sent (250 2.0.0 OK 1316714201 i16si4239653yba.88)
Sep 22 14:56:41 ubuntu postfix/qmgr[12335]: CC51B21C12: removed
Sep 22 14:56:43 ubuntu postfix/smtpd[21121]: disconnect from localhost[127.0.0.1]


```

And: 
```

 * Documentation:  https://help.ubuntu.com/
You have new mail.
Last login: Thu Sep 22 17:17:25 2011 from 186.213.77.50
root@ubuntu:~# tail -f /var/log/mysql.log

(there's nothing happening) 


```

Could anyone guide me to a way to fix this?
One thing I noticed is that it seems to add "/" after the recipients name for some reason...

Could it be a rights problem? 
```

root@ubuntu:/# ls -l /var/mail/virtual
total 0
root@ubuntu:/# ls -l /var/mail/
total 8
-rw------- 1 root    mail    1444 2011-09-22 16:01 root
drwxr-sr-x 2 virtual virtual 4096 2011-09-22 16:44 virtual
root@ubuntu:/#

```

---

### Post by KriBaBa on 2011-09-22
I'm getting more and more sure the problem is with the trailing slash since postfix appears to be able to send emails. 
I received the following in my private inbox: 
FROM: Mail Delivery System <MAILER-DAEMON@envisionenglish.com.br>

Reporting-MTA: dns; mail.envisionenglish.com.br
X-Postfix-Queue-ID: 7FF8421B62
X-Postfix-Sender: rfc822; [email]kristianbbach@gmail.com[/email]
Arrival-Date: Thu, 22 Sep 2011 21:33:38 +0000 (UTC)

Final-Recipient: rfc822; klaus**/**@envisionenglish.com.br
Original-Recipient: rfc822;klaus@envisionenglish.com.br
Action: failed
Status: 5.1.1
Diagnostic-Code: X-Postfix; unknown user: "klaus**/**@envisionenglish.com.br"

---

### Post by fade2gray on 2011-09-22
To anyone having problems with this guide, I suggest considering installing Ubuntu server 10.04.3 LTS and Virtualmin. Virtualmin gives you a browser type front-end for managing your web-server, mail-server and much more. Read [_this guide_]("http://ubuntuforums.org/showthread.php?t=1197883") for starters.

NOTE: If you do follow the guide, when you get to the section where you are told to do the following:-```
sudo ./install.sh
```

... after the Virtualmin installation script has completed successfully, you will need to perform the following commands:-```
sudo update-rc.d webmin defaults
sudo update-rc.d usermin defaults
```
... this is because Virtualmin also installs Webmin 1.560 and Usermin 1.480 - for which the Upstart Jobs for both are slightly bugged and the latter two commands rectify this (see [_this thread_]("http://www.virtualmin.com/node/19092")).

[COLOR="Red"]Addendum: Since posting this, I notice that Virualmin has been updated from version 3.87 to 3.88, but I'm unsure if this eliminates the need to run the extra commands. The best thing to do (after running the install script) is to try accessing the browser interface first:-```
[https://your_server_ip:10000](https://your_server_ip:10000)
```... if you get an error - then run the extra commands.[/COLOR]
HTH.

---

### Post by KriBaBa on 2011-09-22
Sounds like it's worth a try... Thanks for the tip :)

---

### Post by KriBaBa on 2011-09-23
> **fade2gray said:**
> 
[COLOR="Red"]Addendum: Since posting this, I notice that Virualmin has been updated from version 3.87 to 3.88, but I'm unsure if this eliminates the need to run the extra commands. The best thing to do (after running the install script) is to try accessing the browser interface first:-```
[https://your_server_ip:10000](https://your_server_ip:10000)
```... if you get an error - then run the extra commands.[/COLOR]
HTH.

For me it appears to run smoothly without these extra commands

---

### Post by fade2gray on 2011-09-23
> **KriBaBa said:**
> For me it appears to run smoothly without these extra commands

That's really odd - I just performed a clean install of Ubuntu server 10.04.3 and Virtualmin 3.88 GPL on a virtual-machine and found I still had to perform the extra commands to fix the upstart jobs for Webmin and Usermin.

Any further queries regarding this should be discussed in [_this thread_]("https://www.virtualmin.com/node/19581") and [_this thread_]("http://www.virtualmin.com/node/19092") in the Virtualmin forums, or at least a separate Ubuntu thread, so as not to go off topic.

---

### Post by rougueboy on 2011-09-27
Followed the 10th version (Ubuntu 10.04) for setting up basic mail server. 
Moving to the Authentication: Cyrus SASL client section and SASL.

Can't get past the following error...
**mail.log:Sep 26 10:02:20 rougserver postfix/smtpd[16920]: warning: SASL authentication failure: cannot connect to saslauthd server: No such file or directory**
saslauthd is running...
**18919 ?        Ss     0:00 /usr/sbin/saslauthd -a pam -r -c -m /var/spool/postfix/var/run/saslauthd -n 5**
Here's the socket...
**auth.log:Sep 27 13:34:07 rougserver saslauthd[18919]: ipc_init        : listening on socket: /var/spool/postfix/var/run/saslauthd/mux**
master.cf has the saslauthd running in chroot...
**smtp      inet  n       -       -       -       -       smtpd -v**

I'm at a loss this point to understand why smtpd does not find saslauthd...
Any suggestions much appreciated...

---

### Post by rougueboy on 2011-09-29
Update the subject to be the error...
Found out what the problem was...
I had set 
**queue_directory = /mnt/rougshare/spool/postfix**
in main.cf
I followed flurdy's directions and setup as in my post saslauthd directory (-m option) to run out of 
**/var/spool/postfix/var/run/saslauthd**
Need to be out of
**/mnt/rougshare/spool/postfix/var/run/saslauthd**
I had changed them to be off my boot disk to my raid array.
May want to include in a future update of your guide the change to where the mail and queue directories are.
It would be very helpful if smtpd also put the directory in the warning.   I saw many posts on this warning that would have been easier to resolve if the directories were printed.   Maybe I should make this change to postfix and  submit it? :)

---

### Post by rougueboy on 2011-09-30
One addition problem I noted that was not discussed in the setup.
Courier-imap does not setup its own maildirs for new accounts.
That has to be done manually for every added account.
Courier has a command call maildirmake that can be used to setup new maildirs as you add new accounts.  This is especially meaningful for imap to get the sent, drafts and trash folders in place which are the defaults maildirmake setups up.   I also found out for mac outlook 2011, it requires a Junk E-mail folder to be created.   That can be done through the maildirmake -f command.  

Once I had an empty mailbox setup correctly, it was easier just to do a "cp -a" for that mailbox when I created new users.   Interested in if their is any more integrated way - e.g. from a sql web interface with php to do all this every time a user is added.

---

### Post by trenje on 2011-10-11
Hello flurdy,

First of all thanks for great tutorial, it really helped me setting up my mailserver. 

I have two suggestions for tutorial.  First one is that you didn't cover Courier POP and installing/settingup Courier POP packages, I had to do that manually and to open POP3 and POP3S in shorewall.

The second is that most of the spam servers check reverse DNS when sending email and you didn't cover that (I had to set up bind with reverse dns for that).

Nevertheless, this is the best tutorial I have seen for creating mailserver, thank you!

---

### Post by The Sorrow on 2011-10-12
Been wanting to set one of these up! Definitely coming in handy.

---

### Post by flurdy on 2011-11-10
> **rougueboy said:**
> One addition problem I noted that was not discussed in the setup.
Courier-imap does not setup its own maildirs for new accounts.
That has to be done manually for every added account.
Courier has a command call maildirmake that can be used to setup new maildirs as you add new accounts.  This is especially meaningful for imap to get the sent, drafts and trash folders in place which are the defaults maildirmake setups up.   I also found out for mac outlook 2011, it requires a Junk E-mail folder to be created.   That can be done through the maildirmake -f command.  

Once I had an empty mailbox setup correctly, it was easier just to do a "cp -a" for that mailbox when I created new users.   Interested in if their is any more integrated way - e.g. from a sql web interface with php to do all this every time a user is added.

Creating the folders manually is not neccessary. 
As long as the root exists postfix will create these folders once  each user receives its first email.([http://flurdy.com/docs/postfix/#app_faq](http://flurdy.com/docs/postfix/#app_faq))

However as you state the additional folders courier uses will not be created by postfix as it does not use them. But those extra ones can be created by eg roundcube or squirrelmail by default: in [http://flurdy.com/docs/postfix/#ext_round](http://flurdy.com/docs/postfix/#ext_round) the 
> $rcmail_config['create_default_folders'] = TRUE;

---

### Post by gestalts on 2011-11-23
A while ago before getting started I purchased the official "book of postfix" and taken time to read thru the ubuntu documentation for postfix.  And i've installed all of the necessary/related packages.  Presently I have postfix configured as an "internet site"; mail service for my primary (default) server/hostname "server.example.net", "localhost", etc..

Bind9/DNS, zone files, everything is all set.

My primary (default) server/hostname is set up on a dedicated box with about 20 dedicated ip's - though only a few are currently in-use -- (3) websites w/dedicated ip's + SSL.

Just to be clear, let me illustrate:
"server.example.NET" = primary server/hostname + dns zone file; 170.160.150.140
"example.COM" = website #1 + dns zone file; 170.160.150.141
"pretendco.com" = website #2 + dns zone file; 170.160.150.142
"greedyco.com" = website #3 + dns zone file; 170.160.150.143 

I just recently added "imap.example.com" + "smtp.example.com" + corresponding zone file entries, each with its own unique/dedicated ip.  So in-addition to above, now I've got:
"imap.example.net" + entry added to corresponding dns zone file; 170.160.150.144
"smtp.example.net" + entry added to corresponding dns zone file; 170.160.150.145

Here's my question:
Up to this point I've been using google's (mx) to provide mail service for all of the above domains + dns zone files with corresponding google mx entries.  I suppose what I'm trying to do here - essentially replicate google's configuration (imap.gmail.com, smtp.gmail.com) on my server with postfix/courier - allowing me to send and receive mail(boxes) from my desktop mail program configured with my own server(s) "imap.example.net, smtp.example.net" to send and receive mail(boxes) -- not google's (imap;smtp.gmail.com).

Does that make sense?
In your own words, can anyone kindly help explain how I can accomplish this?
Please, please, no links to documentation or blogs filled with garbage advertising.
Greatly appreciated!  Thanks y'all!

---

### Post by dstein766 on 2011-11-24
Thanks for the excellent documentation - I've been working to replace a dying mail server with a new one and this has been invaluable!  I have one problem, however, that I'm hoping has an obvious solution.

I relay all my incoming (home) email to my work address via my ISP.  My current email server (built a long time ago using standard packages and another Postfix HowTo) works fine (if one overlooks the dying hardware :)), but the new setup keeps giving me 553 rejections when I try to relay.  I *think* the root of the problem is found in this representative message from mail.log, which appears just prior to the 553 errors:

Nov 24 11:03:44 mailhost postfix/qmgr[7878]: 21F2DC1F21: from=<>, size=9657, nrcpt=1 (queue active)

Note the "from=<>" entry - as far as I can tell, on my working server this field isn't blank but shows my home email (which is, in turn, a valid address as far as my ISP is concerned).  So as far as I can tell I'm passing an empty MAIL FROM field to the relay host and being rejected.  

Is there an obvious reason why the from address would be empty?  I've attempted to do side-by-side comparison of my working setup (particularly on the various SASL parameters, which are in agreement), but the old setup uses .procmailrc as the fowarding mechanism while the new setup uses the mysql aliases approach.  This may be a red herring, but my own skills in this area are limited so I really don't know where to look to try to solve.

---

### Post by georgian_craciun on 2011-11-26
[Here]("http://scripturi-instalare-ubuntu.blogspot.com/2011/10/in-lucru-un-server-de-mail-in-4-minute.html#more") you can find a script that installs and configures postfix-courier-SquirrelMail in 4 minutes. Perhaps you are useful for someone ...

---

### Post by fade2gray on 2011-11-26
> **georgian_craciun said:**
> [Here]("http://scripturi-instalare-ubuntu.blogspot.com/2011/10/in-lucru-un-server-de-mail-in-4-minute.html#more") you can find a script that installs and configures postfix-courier-SquirrelMail in 4 minutes. Perhaps you are useful for someone ...
Should anyone need to translate the page the link leads to; it's in Romanian.

---

### Post by georgian_craciun on 2011-11-26
It is not difficult ...
 Download the script from **[HERE]("https://docs.google.com/open?id=0BzdgJBgHUlPrNTQ1ZmFkZGItOTczYS00NjYxLTk2MjQtNDEyYjA2ZTY0NjJm")** ;
make it executable (ex:   sudo chmod +x /home/servermail ), 
change the content lines from 105 to 125
launch script execution (ex: sudo /home/servermail )           

... or you can write in Google [COLOR=DarkGreen]**[http://scripturi-instalare-ubuntu.blogspot.com/2011/10/in-lucru-un-server-de-mail-in-4-minute.html](http://scripturi-instalare-ubuntu.blogspot.com/2011/10/in-lucru-un-server-de-mail-in-4-minute.html)**[/COLOR] and then click Translate Page.

**[COLOR=Navy]The script will install and configure postfix - courier - SquirrelMail. After that you have a fully functional mail server.[/COLOR]**

---

### Post by jspiegel187 on 2011-12-15
Hey, I'm having trouble getting the basic mail server running. I can telnet in but when I try to send an email the "RCPT TO:" portion denies it no matter what I type in. Below is the tail of the mail log:

Dec 15 12:13:20 zero postfix/smtpd[2304]: connect from localhost.localdomain[127.0.0.1]
Dec 15 12:14:05 zero postfix/smtpd[2304]: NOQUEUE: reject: RCPT from localhost.localdomain[127.0.0.1]: 554 5.7.1 <localhost.localdomain[127.0.0.1]>: Client host rejected: Access denied; from=<master@zero.local> to=<jripeastwest@yahoo.com> proto=ESMTP helo=<zero.local>
Dec 15 12:14:05 zero postfix/smtpd[2304]: warning: restriction `rbl_client' after `reject' is ignored
Dec 15 12:14:08 zero postfix/smtpd[2304]: disconnect from localhost.localdomain[127.0.0.1]

My username on the box is "master" and my hostname is zero.local 
The firewall is closed as per the instructions.

Below is my main.cf


# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname
myorigin= zero.local


smtpd_banner = $myhostname ESMTP Welcome, XNasty at your service.....
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname =zero.local
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = zero.local, zero, localhost.localdomain, localhost
relayhost =smtp-server.nyc.rr.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mynetworks_style = host
masquerade_domains =
masquerade_exceptions = rootlocal_recipient_maps =
mydestination =

# MAIL SETTINGS

delay_warning_time = 4h
unknown_local_recipient_reject_code = 450
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
smtp_helo_timeout = 60s
smtpd_recipient_limit = 16
smtpd_soft_error_limit = 3
smtpd_hard_error_limit = 12


# RESTRICTIONS

smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
#

smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit


smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org

smtpd_recipient_restrictions = reject_unauth_pipelinig, permit_mynetworks, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, permit

smtpd_data_restrictions = reject_unauth_pipelining

smptd_helo_required = yes

smptd_delay_reject = yes

disable_vrfy_command = yes

#######

alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000


I'd love to get this running. Not sure what the next step is to get this past the testing phase.

Any help is appreciated..

---

### Post by TJRana on 2011-12-25
Thank you.

---

### Post by georgian_craciun on 2011-12-28
> **TJRana said:**
> 
Now it tells me to add users and domains. It says ```
# Use phpMyAdmin or command line mysql
INSERT INTO domains (domain) VALUES
    ('localhost'),
    ('localhost.localdomain');
```I don't know how to do that. What do it mean by "Use phpMyAdmin? Or command line mysql? How do I do that? What should I do? 

```
echo "USE maildb;" > /home/createdb
echo "INSERT INTO domains (domain) VALUES ('$domeniulmeu');" >> /home/createdb
echo "quit" >> /home/createdb
mysql -uroot -p$passroot </home/createdb

```where :
 $domeniulmeu = yours domain name (ex: ubuntuforums.org)
 $passroot = password for MySQL root user

---

### Post by rhyancute on 2012-01-10
i install ubuntu 11.10 32bit server.
i can send email using php script

my webmail client ([http://www.afterlogic.com](http://www.afterlogic.com)) and roundcube is successfully installed.


my problem is how to create a email account?

any one can help me?

---

### Post by jongers on 2012-01-19
> **eihli said:**
> ****UPDATE: FIXED****
Hopefully this will save someone else some time. Did I miss this step in the tutorial or something?
Looking back on it... this should have been a pretty easy fix.
On the last line of 
/etc/courier/imapd-ssl 
I changed 
MAILDIRPATH=Maildir 
to 
MAILDIRPATH=/var/spool/mail/virtual


That has saved me some time thanks!:KS

---

### Post by ckuecker on 2012-01-23
Hello,

First, thanks for the thorough howto. It really helps to see examples of how to do things.

I used this howto to install a mail server on my Ubuntu 11.10 system. I had a working system until I upgraded from Ubuntu 10, and lost the ability to boot off my main drive. I had to reinstall from the CD to get a working system back, and I lost my original mail system.

I can telnet into the system and connect to ports 25 and 143 if I use 'localhost'. When I try to telnet in using my FQDN, I get 'telnet: Unable to connect to remote host: Connection refused'. 

I tried using tail on the mysql and mail log files. I see activity on the mail log when I try via telnet, but no activity at all on the mysql log.

I read through the Shorewall documentation and cannot see where that could be causing my problems. 

Another strange thing that might be syptomatic - my Apache web server was working on the Ubuntu machine, and was accessible from the Ubuntu machine and other Windows machines on my local network until I started with this installation. Now, it apparently is accessible only from the Internet - I had a friend access it while I was unable to load the pages.

Any idea how to proceed? I am starting to suffer from email withdrawal.

---

### Post by ckuecker on 2012-01-24
Found one problem - my bind9 config files had some comments in them that were being interpreted as errors. Bind9 is working now.

I can access my website on 127.0.0.1, but still not from outside.

---

### Post by ckuecker on 2012-01-25
Reloaded Ubuntu from scratch and went through the install again. Everything works properly from localhost, but I cannot access anything from outside the Linux machine. 

I installed gufw and turned off the firewall - still cannot access from outside. 

Telnet localhost works - telnet <FQDN> works. Telnet to my Internet IP fails.

Some config files - 

/etc/hosts:
```

127.0.0.1    localdomain.localhost localhost
192.168.0.200    ckenterprises.ckent.org smtp

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```/etc/interfaces:
```

auto lo
iface lo inet loopback
  pre-up iptables-restore < /etc/iptables.rules
  post-down iptables-restore < /etc/iptables.downrules

auto eth0
iface eth0 inet static
  address 192.168.0.200
  network 192.168.0.0
  netmask 255.255.255.0
  broadcast 192.168.0.255
  gateway 192.168.0.2

```/etc/hostname:
```

<my.full.domain>

```Any help would be very appreciated.

---

### Post by ckuecker on 2012-01-25
In case it helps:
```

root@ckuecker:/home/chuck# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:4d:71:ad:69  
          inet addr:192.168.0.200  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::218:4dff:fe71:ad69/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24592 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18626 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15637039 (15.6 MB)  TX bytes:2852932 (2.8 MB)
          Interrupt:11 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4596 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4596 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:217754 (217.7 KB)  TX bytes:217754 (217.7 KB)

```

---

### Post by ckuecker on 2012-01-25
Further information - I can get Thunderbird to connect to the servers using 127.0.0.1, but it keeps telling me my email password is invalid. 

From looking at log activity, I think the system is receiving emails from outside servers, so if I can access this system locally i can at least delete my spam and send emails out. Ultimately, I need to be able to access the system from any computer on my local network, as I host email for several people.

---

### Post by ckuecker on 2012-01-26
OK. I am in the home stretch, I think. Disabling the firewall with iptables -F allowed my webserver to work, and I was able to send email from Thunderbird on both my local Windows machine and from this Ubuntu machine. Email sent from outside gets into the /var/mail/virtual/<user> folder, and I can look at it with gedit and see my messages.

What I can't do - yet - is connect with Thunderbird to read what's in the mailbox. Thunderbird wants a password, and tells me it's incorrect when I supply the password I used in the setup process.

So, what I need now is to find out where postfix hides that password, and gedit to send those accumulating emails out to Thunderbird, and I can put this mess to bed.

Then, I need to re-enable a proper firewall.

---

### Post by AntaresDaha on 2012-01-27
So yesterday we followed the tutorial and managed to setup a core/simple mailserver.
All in all it does what we would expect the server to do.
It can receive emails and store them under the associated virtual user accounts.
It's also able to match different mail aliases against each other using the mysql tables etc.
But concerning outgoing/forwarding emails we got a peculiar problem.
If we locally run telnet on our server, we can emulate another machine requesting to send/forward mails for us, like that:
```

helo we.are.an.extern.server.com
-> 250 ourserver.net
mail from: d.k@googlemail.com
-> 250 2.1.0 Ok
rcpt to: antares@lazias.com
-> 250 2.1.5 Ok
data
-> End data with <CR><LF>.<CR><LF>
somerandomtext
foobar
.
-> 250 2.0.0 Ok queued as 9E05517F808B
quit
-> 221 2.0.0 Bye

```Moments later [EMAIL="antares@lazias.com"]antares@lzias.com[/EMAIL] will be resolved to [EMAIL="cdomi@web.de"]cdomi@web.de[/EMAIL] and the testmail will be received in that (extern) mailbox.
Now if we contact our server via telnet from an EXTERN machine and run the exact same commands our server will respond in the exact same way, it will try to send out the created mail to [EMAIL="cdomi@web.de"]cdomi@web.de[/EMAIL] but awkwardly enough when we login on that extern mailbox the mail is never received.
Now if we look into the logfiles of our server, we can see that our mailserver seems to be doing the exact same thing, trying to sent/forward a mail to [EMAIL="cdomi@web.de"]cdomi@web.de[/EMAIL] and it doesn't seem to have any troubles doing so.
Here the corresponding logfile entries:
> 
Jan 27 16:20:46 ourserver postfix/smtpd[15487]: connect from localhost.localdomain[127.0.0.1]
Jan 27 16:23:21 ourserver postfix/smtpd[15487]: 9E05517F808B: client=localhost.localdomain[127.0.0.1]
Jan 27 16:24:58 ourserver postfix/cleanup[15492]: 9E05517F808B: message-id=<20120127152321.9E05517F808B@ourserver.net>
Jan 27 16:24:58 ourserver postfix/qmgr[9946]: 9E05517F808B: from=<d.k@googlemail.com>, size=392, nrcpt=1 (queue active)
Jan 27 16:24:59 ourserver postfix/smtp[15496]: 9E05517F808B: to=<cdomi@web.de>, orig_to=<antares@lzias.com>, relay=mx-ha01.web.de[217.72.192.149]:25, delay=170, delays=170/0.01/0.07/0.15, dsn=2.0.0, status=sent (250 OK id=1Rqnff-0003jD-00)
Jan 27 16:24:59 ourserver postfix/qmgr[9946]: 9E05517F808B: removed
Jan 27 16:26:59 ourserver postfix/smtpd[15487]: disconnect from localhost.localdomain[127.0.0.1]


Jan 27 16:33:56 ourserver postfix/smtpd[15511]: connect from mail-wi0-f176.google.com[209.85.212.176]
Jan 27 16:33:58 ourserver postfix/smtpd[15511]: 5BC9117F808B: client=mail-wi0-f176.google.com[209.85.212.176]
Jan 27 16:33:58 ourserver postfix/cleanup[15514]: 5BC9117F808B: message-id=<4F22C3E5.2060602@googlemail.com>
Jan 27 16:33:58 ourserver postfix/qmgr[9946]: 5BC9117F808B: from=<d.k@googlemail.com>, size=1649, nrcpt=1 (queue active)
Jan 27 16:33:58 ourserver postfix/smtp[15515]: 5BC9117F808B: to=<cdomi@web.de>, orig_to=<antares@lzias.com>, relay=mx-ha02.web.de[217.72.192.188]:25, delay=2.3, delays=2.2/0.01/0.06/0.05, dsn=2.0.0, status=sent (250 OK id=1RqnoM-0000Kh-00)
Jan 27 16:33:58 ourserver postfix/qmgr[9946]: 5BC9117F808B: removed
As we can easily see the server does handle both request in the same way, only one mail will actually reach [EMAIL="cdomi@web.de"]cdomi@web.de[/EMAIL] while the other one won't.

Could anyone explain us how that comes? or atleast give us a hint?
Does the web.de mailserver reject our (server's) attempt to forward an email (for whatever reasons) while it seems to be ok with it being the original creator of an email?
How could we check whether the mail gets rejected later after postfix sent it out confidently?

Any help would be appreciated,
regards Antares

---

### Post by AmirM on 2012-02-10
hi,
can I get a VPS for this or its better to do it on my home computer?
since I have a really bad internet connection and I want my server to be up 24/7 I want to deploy it on a VPS.
is it possible? it is very different or just a bit?

---

### Post by duceduc on 2012-02-12
I got the mail server setup and and it seems to be sending mails but I have this error fro spamd that it cannot create defaults_prefs. Here is my log.
> Feb 13 01:48:37 revomix spamd[19468]: prefork: child states: II
Feb 13 01:48:44 revomix postfix/smtpd[19473]: connect from localhost.localdomain[127.0.0.1]
Feb 13 01:49:07 revomix postfix/smtpd[19473]: 1B5F384118B: client=localhost.localdomain[127.0.0.1]
Feb 13 01:49:11 revomix postfix/cleanup[19476]: 1B5F384118B: message-id=<20120212164907.1B5F384118B@mail.ducsu.com>
Feb 13 01:49:11 revomix postfix/qmgr[14379]: 1B5F384118B: from=<support@ducsu.com>, size=325, nrcpt=1 (queue active)
Feb 13 01:49:11 revomix spamd[19469]: spamd: connection from localhost.localdomain [127.0.0.1] at port 39918
Feb 13 01:49:11 revomix spamd[19469]: spamd: setuid to spamfilter succeeded
Feb 13 01:49:11 revomix spamd[19469]: spamd: creating default_prefs: /home/spamfilter/.spamassassin/user_prefs
Feb 13 01:49:11 revomix spamd[19469]: spamd: failed to create readable default_prefs: /home/spamfilter/.spamassassin/user_prefs
Feb 13 01:49:11 revomix spamd[19469]: spamd: processing message <20120212164907.1B5F384118B@mail.ducsu.com> for spamfilter:5001
Feb 13 01:49:12 revomix spamd[19469]: spamd: clean message (1.9/2.0) for spamfilter:5001 in 0.3 seconds, 350 bytes.
Feb 13 01:49:12 revomix spamd[19469]: spamd: result: . 1 - ALL_TRUSTED,MISSING_HEADERS,MISSING_SUBJECT,TVD_SPACE_RATIO scantime=0.3,size=350,user=spamfilter,uid=5001,required_score=2.0,rhost=localhost.localdomain,raddr=127.0.0.1,rport=39918,mid=<20120212164907.1B5F384118B@mail.ducsu.com>,autolearn=no
Feb 13 01:49:12 revomix postfix/pickup[14378]: 29CFF841190: uid=5001 from=<support@ducsu.com>
Feb 13 01:49:12 revomix postfix/pipe[19477]: 1B5F384118B: to=<noreply@ducsu.com>, relay=spamfilter, delay=15, delays=14/0/0/0.36, dsn=2.0.0, status=sent (delivered via spamfilter service)
Feb 13 01:49:12 revomix postfix/qmgr[14379]: 1B5F384118B: removed
Feb 13 01:49:12 revomix postfix/cleanup[19476]: 29CFF841190: message-id=<20120212164907.1B5F384118B@mail.ducsu.com>
Feb 13 01:49:12 revomix spamd[19468]: prefork: child states: II
Feb 13 01:49:12 revomix postfix/qmgr[14379]: 29CFF841190: from=<support@ducsu.com>, size=672, nrcpt=1 (queue active)
Feb 13 01:49:12 revomix postfix/smtpd[19487]: connect from localhost.localdomain[127.0.0.1]
Feb 13 01:49:12 revomix postfix/smtpd[19487]: 4666D84118B: client=localhost.localdomain[127.0.0.1]
Feb 13 01:49:12 revomix postfix/cleanup[19476]: 4666D84118B: message-id=<20120212164907.1B5F384118B@mail.ducsu.com>
Feb 13 01:49:12 revomix postfix/smtpd[19487]: disconnect from localhost.localdomain[127.0.0.1]
Feb 13 01:49:12 revomix postfix/qmgr[14379]: 4666D84118B: from=<support@ducsu.com>, size=1067, nrcpt=1 (queue active)
Feb 13 01:49:12 revomix amavis[912]: (00912-16) Passed CLEAN, [127.0.0.1] <support@ducsu.com> -> <noreply@ducsu.com>, Message-ID: <20120212164907.1B5F384118B@mail.ducsu.com>, mail_id: HeSBLkNyca6R, Hits: -, size: 672, queued_as: 4666D84118B, 115 ms
Feb 13 01:49:12 revomix postfix/smtp[19485]: 29CFF841190: to=<noreply@ducsu.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=0.21, delays=0.08/0.01/0/0.12, dsn=2.0.0, status=sent (250 2.0.0 from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 4666D84118B)
Feb 13 01:49:12 revomix postfix/qmgr[14379]: 29CFF841190: removed
Feb 13 01:49:12 revomix postfix/virtual[19488]: 4666D84118B: to=<noreply@ducsu.com>, relay=virtual, delay=0.09, delays=0.04/0/0/0.04, dsn=2.0.0, status=sent (delivered to maildir)
Feb 13 01:49:12 revomix postfix/qmgr[14379]: 4666D84118B: removed
Feb 13 01:53:32 revomix postfix/smtpd[19473]: disconnect from localhost.localdomain[127.0.0.1]



---

### Post by duceduc on 2012-02-12
I got the above post fix by creating a .spamassassin folder in /home/spamfilter/. Assign spamd owner to that folder. Gave permission to write.
> 
sudo mkdir /home/spamfilter/.spamassassin
sudo chmod 775 /home/spamfilter/.spamassassin
sudo chown spamd:spamd /home/spamfilter/

If you don't have spamd as a user yet. Create one with no shell.
> 
sudo groupadd spamd
sudo useradd -g spamd -s /bin/false -d /home/spamfilter/.spamassassin

**My other problem is this error whenever I start spamassassin.**
> 
Mon Feb 13 03:46:29 2012 [22333] info: config: failed to parse line, skipping, i                          n "/etc/spamassassin/local.cf": use_dcc 0


---

### Post by spezticle on 2012-03-23
Hey, i'm following your guide,but i'm concerned with the following code in the mysql database section
```

CREATE TABLE `users` (
`id` varchar(128) NOT NULL default '',
`name` varchar(128) NOT NULL default '',
`uid` smallint(5) unsigned NOT NULL default '5000',
`gid` smallint(5) unsigned NOT NULL default '5000',
`home` varchar(255) NOT NULL default '/var/spool/mail/virtual',
`maildir` varchar(255) NOT NULL default 'blah/',
`enabled` tinyint(3) unsigned NOT NULL default '1',
`change_password` tinyint(3) unsigned NOT NULL default '1',
`clear` varchar(128) NOT NULL default 'ChangeMe',
`crypt` varchar(128) NOT NULL default 'sdtrusfX0Jj66',
`quota` varchar(255) NOT NULL default '',
`procmailrc` varchar(128) NOT NULL default '',
`spamassassinrc` varchar(128) NOT NULL default '',
PRIMARY KEY  (`id`),
UNIQUE KEY `id` (`id`)
) ;

```

specifically:
```
`clear` varchar(128) NOT NULL default 'ChangeMe',
```
and
```
`maildir` varchar(255) NOT NULL default 'blah/',
```

What is this blah/ and ChangeMe
Should I change these to something else?

---

### Post by Solitary_ on 2012-04-11
I seem to be having trouble with installing some of the packages.

A fair few have come back with "Couldn't find any package whose name of description matched "packagenamehere"

I am using Ubuntu 11.10, does that make a difference?

---

### Post by spezticle on 2012-04-11
check your software sources.
[http://flurdy.com/docs/postfix/#install_repos](http://flurdy.com/docs/postfix/#install_repos)
which packages can't you find?
> **Solitary_ said:**
> I seem to be having trouble with installing some of the packages.

A fair few have come back with "Couldn't find any package whose name of description matched "packagenamehere"

I am using Ubuntu 11.10, does that make a difference?

---

### Post by Solitary_ on 2012-04-12
My sources.list is showing main, universe, restricted and multiverse, in ubuntu 9.04 and later they are all enabled by default.

The following are packages it stated "Couldn't find any package whose name or description matched "packagenamehere"

libgsasl7 libauthen-sasl-cyrus-perl
postgrey
ShoreWall
Courier



The Entire command line for ClamAV says "No packages will be installed, upgraded, or removed", the same for amavis & spamassassin.

---

### Post by Solitary_ on 2012-04-14
Any help would be greatly appreciated :)

---

### Post by WinterWren on 2012-05-03
**Outlook and self-signed certificates**

These are the steps I took to stop the annoying pop up from MS Outlook constantly asking to allow the security certificate from my email server.  Warning: I am a novice user so please verify that these steps are secure before using them on your system.

First, I create a working directory.  I use a directory in the home path but you may want to place them somewhere else.  I am the only user/administrator of my server so I consider this directory secure.
```
cd ~
mkdir certs
cd certs
sudo chmod 700 .
```Generate a key file.  This will ask you to create a password.  You will only need to remember this password for the next two steps.
```
sudo openssl genrsa -des3 -out server.key 1024
```[I]Sample output:
Generating RSA private key, 1024 bit long modulus
.................................................++++++
.++++++
e is 65537 (0x10001)
Enter pass phrase for server.key: [COLOR=Red]somepass[/COLOR]
Verifying - Enter pass phrase for server.key: [COLOR=Red]somepass[/COLOR]
[/I]
Create your self-signed certificate file.  This will ask for the password that you used in the last step along with some other questions about your location. For "Common Name (eg, YOUR name) []:" you must enter your server's FQDN.
```
sudo openssl req -new -x509 -nodes -sha256 -days 3650 -key server.key -out server.crt

```[I]Sample output:
Enter pass phrase for server.key: [COLOR=Red]somepass[/COLOR]
You are about to be asked to enter information that will be incorporated
into your certificate request.
What you are about to enter is what is called a Distinguished Name or a DN.
There are quite a few fields but you can leave some blank
For some fields there will be a default value,
If you enter '.', the field will be left blank.
-----
Country Name (2 letter code) [AU]:[COLOR=Red]US[/COLOR]
State or Province Name (full name) [Some-State]:[COLOR=Red]WI[/COLOR]
Locality Name (eg, city) []:[COLOR=Red]Milwaukee[/COLOR]
Organization Name (eg, company) [Internet Widgits Pty Ltd]:[COLOR=Red]Some Company[/COLOR]
Organizational Unit Name (eg, section) []:[COLOR=Red]IT Department[/COLOR]
Common Name (eg, YOUR name) []:[COLOR=Red]mail.domain.com [COLOR=Black](this must be the FQDN)[/COLOR][/COLOR]
Email Address []:[COLOR=Red]postmasters@domain.com[COLOR=Black]

[/COLOR][/COLOR][/I][COLOR=Red][COLOR=Black]Remove the password from "server.key"[/COLOR][/COLOR][I][COLOR=Red][COLOR=Black]
[/COLOR][/COLOR][/I]```
cp server.key server.key.orig
sudo openssl rsa -in server.key.orig -out server.key

```[I]Sample output:
Enter pass phrase for server.key.orig: [COLOR=Red]somepass[/COLOR]
writing RSA key
[/I][I][COLOR=Red][COLOR=Black]
[/COLOR][/COLOR][/I][COLOR=Red][COLOR=Black]Generate a public file for clients.  This will prompt for a password.  If you want your clients to have to enter a password when they install this certificate enter something here.  If not, leave it blank.
[/COLOR][/COLOR]```
sudo openssl pkcs12 -export -in server.crt -inkey server.key -out Outlook.p12

```[I]Sample output:
Enter Export Password: [COLOR=Red]clientpassword[/COLOR]
Verifying - Enter Export Password: [COLOR=Red]clientpassword[/COLOR][/I]

I'm certain there is a better way to do this next step but I couldn't figure out the correct switch for the openssl command so I did this to create the certificate in pem format.
```
cp server.crt server.pem
cat server.key >> server.pem

```I then modified main.cf to use the new certificates.
```
sudo vi /etc/postfix/main.cf
``````
smtpd_tls_cert_file = /home/[COLOR=Red]username[/COLOR]/certs/server.crt
smtpd_tls_key_file = /home/[COLOR=Red]username[/COLOR]/certs/server.key 

```Also modified imapd-ssl to use the same certificates.
```
sudo vi /etc/courier/imapd-ssl
``````
TLS_CERTFILE=/home/[COLOR=Red]username[/COLOR]/certs/server.pem
TLS_TRUSTCERTS=/home/[COLOR=Red]username[/COLOR]/certs

```You must restart affected services for the changes to take place on your server.

Provide the file "Outlook.p12" to your clients.  They should be able to start installation of this certificate by double clicking or right click and install.  If you used a password to create Outlook.p12 you must provide it to your clients and they must enter it when they install the certificate.  The certificate must be stored in the "[FONT=&quot]Trusted Root Certification Authorities"[/FONT] during the installation of the certificate (choose "Place certs in following store" not "Automatic ....")

It would be nice if Outlook would allow this file to be sent in an email but it doesn't.  You will have to zip it to send or set it up on some web/ftp server somewhere.

[I][COLOR=Red]

[/COLOR][/I]

---

### Post by duceduc on 2012-05-19
I successfully setup the mail server and am able to send and receive via the telnet test. However, I cannot setup my mail client (thunderbird) to send outgoing mails. I can receive just fine. It maybe my smtp settings are incorrect.

In the thunderbird smtp settings. I have the following.

server name: mail.mydomain.com
port: 25
connection security: starttls
authentication method: no authentication
user name: [email]somename@mydomain.com[/email]

When I try to send a test mail, I get the following errors.

error from thunderbird.
> 
An error occurred while sending mail. The mail server responded:  5.7.1 <somename@yahoo.com>: Relay access denied. Please check the message recipient [email]someone@yahoo.com[/email] and try again.


error log in my mail.log
> 

May 20 10:34:54 revomix postfix/smtpd[19016]: connect from unknown[192.168.1.1]
May 20 10:34:54 revomix postfix/smtpd[18991]: disconnect from unknown[192.168.1.1]
May 20 10:34:54 revomix postfix/smtpd[19016]: setting up TLS connection from unknown[192.168.1.1]
May 20 10:34:54 revomix postfix/smtpd[19016]: Anonymous TLS connection established from unknown[192.168.1.1]: TLSv1 with cipher ECDHE-RSA-AES256-SHA (256/256 bits)
May 20 10:34:54 revomix postfix/smtpd[19016]: NOQUEUE: reject: RCPT from unknown[192.168.1.1]: 554 5.7.1 <somename@yahoo.com>: Relay access denied; from=<somename@mydomain.com> to=<somename@yahoo.com> proto=ESMTP helo=<[127.0.0.1]>



---

### Post by darkspook on 2012-05-24
Thank you for this tutorial.

[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

Its about a year since I started following this tutorial.
At first it seems like it will not work coz you will got lots of errors. But after several tailing/testing/telnet I finally built an impregnable mail server. And since then I haven't encounter any problem.

I'm in your debt. Cheers! :popcorn:

---

### Post by darkspook on 2012-05-24
> **spezticle said:**
> Hey, i'm following your guide,but i'm concerned with the following code in the mysql database section
```

CREATE TABLE `users` (
`id` varchar(128) NOT NULL default '',
`name` varchar(128) NOT NULL default '',
`uid` smallint(5) unsigned NOT NULL default '5000',
`gid` smallint(5) unsigned NOT NULL default '5000',
`home` varchar(255) NOT NULL default '/var/spool/mail/virtual',
`maildir` varchar(255) NOT NULL default 'blah/',
`enabled` tinyint(3) unsigned NOT NULL default '1',
`change_password` tinyint(3) unsigned NOT NULL default '1',
`clear` varchar(128) NOT NULL default 'ChangeMe',
`crypt` varchar(128) NOT NULL default 'sdtrusfX0Jj66',
`quota` varchar(255) NOT NULL default '',
`procmailrc` varchar(128) NOT NULL default '',
`spamassassinrc` varchar(128) NOT NULL default '',
PRIMARY KEY  (`id`),
UNIQUE KEY `id` (`id`)
) ;

```

specifically:
```
`clear` varchar(128) NOT NULL default 'ChangeMe',
```
and
```
`maildir` varchar(255) NOT NULL default 'blah/',
```

What is this blah/ and ChangeMe
Should I change these to something else?
> `maildir` varchar(255) NOT NULL default 'blah/',
You have to change blah/ with a proper directory name.

What I did is:
[email]emailadd@example.com[/email] - this is my email address
emailadd/ - this is the name of directory.

You have to change it all the time when you create new account/user.

> `clear` varchar(128) NOT NULL default 'ChangeMe', -- I just ignore this, leave it as is.

---

### Post by theluli on 2012-05-25
l have same problem , l am unable to login at squirrelmail 
Any one has idea ?

---

### Post by sprior on 2012-06-17
Back in reply# 223 Villu was nice enough to post instructions on getting maildrop to work with Flurdy's guide.  I think I've found a minor correction.  I'm setting up the mailserver on Ubuntu 12.04.

After I made the maildrop changes I could no longer receive mail which had been working before.  I think that in the maildrop line added to master.cf the part at the end:

-d ${recipient}

Only works when the to address of the email matches the userid in the user table - if the to address is redirected by an alias to a different userid I think this would fail.
I changed it to:

-d ${user}

 and things stated working again.  In my case this was necessary because in my user table I don't use a full email address for the userid, I just use a simple username (I had to made config changes elsewhere to account for this), however this pointed out to me that the previous config wasn't being translated through the aliases table.

---

### Post by sprior on 2012-06-17
Just FYI is anyone is trying to follow the Flurdy guide with Ubuntu 11.* to 12.04, there is one change I noticed that needed to be made to the section on setting up SASL.

In the file:
/etc/postfix/sasl/smtpd.conf

the line:
auxprop_plugin: mysql

needs to be changed to:
auxprop_plugin: sql

---

### Post by dbileck on 2012-06-22
Also, when configuring SASL in Ubuntu 12.04 in /etc/postfix/sasl/smtpd.conf "sql_passw" should be "sql_passwd".

---

### Post by dchen on 2012-06-25
> **sprior said:**
> Just FYI is anyone is trying to follow the Flurdy guide with Ubuntu 11.* to 12.04, there is one change I noticed that needed to be made to the section on setting up SASL.

In the file:
/etc/postfix/sasl/smtpd.conf

the line:
auxprop_plugin: mysql

needs to be changed to:
auxprop_plugin: sql

How successful did you follow the current Flurdy guide to build for 12.04 ?  I'm trying to, but not sure if ALL info can apply to 12.04 lts server ! 

Another question: do you know if the Flurdy guide can apply to build for a Local domain in which the existing Linux users have their own mailboxes in ~/Maildir for example (Not the Virtual domain) ?

---

### Post by j_data on 2012-07-15
Hi,

I have followed this guide up until the point where it is strongly suggested that we test everything thoroughly before continuing.


I can send mail to any domain on my local network and it works, however, if I try to send mail to a domain outside my network I just see errors in mail.log that say:

No route to host.

any help would be greatly appreciated.

Thank you,
-Jason

---

### Post by agiom on 2012-08-20
Hi,

I installed the mail server following your advices and everything is working perfectly excepting one stuff : imap attachment downloads. There are very slow. With pop or squirrel it's ok and speed is normal but with imap even for one mega it took too much time and then the connection times out.

Did you already meet this problem? Thanks for help!

Tim from agiom.

---

### Post by ken_ham on 2012-08-28
> **j_data said:**
> Hi,
I can send mail to any domain on my local network and it works, however, if I try to send mail to a domain outside my network I just see errors in mail.log that say:

No route to host.


It's been a while, so you've probably already solved your problem, but that looks likely to be a problem with your networking in general, rather than Postfix in particular.

In this case you could try testing your networking by running:

```

ping google.com

```

from the command line, if the everything is working there should be a response. Next I would try editing /etc/postfix/master.cf and change the smtp line so it looks like this:

```

smtp      inet  n       -       -       -       -       smtpd -v

```

Save and restart Postfix, try to send the mail again, then check mail.log for the output, that may include some clues as to what went wrong.

---

### Post by Ron Jones on 2012-10-13
Aside from posts [http://ubuntuforums.org/showpost.php?p=12035520&postcount=450](http://ubuntuforums.org/showpost.php?p=12035520&postcount=450) and [http://ubuntuforums.org/showpost.php?p=12035520&postcount=450](http://ubuntuforums.org/showpost.php?p=12035520&postcount=450) 

Has anyone had success with the 10th edition of [http://flurdy.com/docs/postfix/index.html](http://flurdy.com/docs/postfix/index.html) using Ubuntu Server 12.04 LTS?

If so, are there any additional steps or 'gotchas' to be aware of?

And, is there a link to the 11th edition (draft) on the flurdy site (above)?

Thanks,

Jones

---

### Post by Oguz286 on 2013-01-01
So I've followed the guide as well, and everything seems to work except for one thing.

I cannot send mails from the server when I have

-o smtpd_client_restrictions=permit_sasl_authenticated,reject

in /etc/postfix/master.cf. Buf if I remove the ',reject' part:

-o smtpd_client_restrictions=permit_sasl_authenticated

then I can send mails. /var/log/mail.log states:

```
postfix/smtpd[8346]: connect from localhost[127.0.0.1]
postfix/smtpd[8346]: Anonymous TLS connection established from localhost[127.0.0.1]: TLSv1.1 with cipher ECDHE-RSA-AES256-SHA (256/256 bits)
postfix/smtpd[8346]: E4BDA62BD: client=localhost[127.0.0.1]
postfix/cleanup[8351]: E4BDA62BD: message-id=<6258d6190d2ece5e505c78b4d0894c84@blablabla.com>
postfix/qmgr[8340]: E4BDA62BD: from=<oguz286@blablabla.com>, size=700, nrcpt=1 (queue active)
postfix/smtpd[8346]: disconnect from localhost[127.0.0.1]
imapd-ssl: LOGOUT, user=oguz286@localhost, ip=[::ffff:127.0.0.1], headers=0, body=0, rcvd=696, sent=654, time=1, starttls=1
postfix/smtp[8354]: E4BDA62BD: to=<bla@gmail.com>, relay=gmail-smtp-in.l.google.com[2a00:1450:400c:c03::1a]:25, delay=0.87, delays=0.24/0.05/0.13/0.45, dsn=2.0.0, status=sent (250 2.0.0 OK 1357083867 w5si63967327wjx.48)
postfix/qmgr[8340]: E4BDA62BD: removed
```

As you can see an anonymous TLS connection is being made, whereas I thought that that my mail user should 'login' and authenticate.

With the reject part, mail.log contains:

```
imapd-ssl: Connection, ip=[::ffff:127.0.0.1]
imapd-ssl: LOGIN, user=oguz286@localhost, ip=[::ffff:127.0.0.1], port=[52331], protocol=IMAP
postfix/smtpd[8050]: connect from localhost[127.0.0.1]
postfix/smtpd[8050]: Anonymous TLS connection established from localhost[127.0.0.1]: TLSv1.1 with cipher ECDHE-RSA-AES256-SHA (256/256 bits)
postfix/smtpd[8050]: NOQUEUE: reject: RCPT from localhost[127.0.0.1]: 554 5.7.1 <localhost[127.0.0.1]>: Client host rejected: Access denied; from=<oguz286@blablabla.com> to=<bla@gmail.com> proto=ESMTP helo=<blablabla.com>
postfix/smtpd[8050]: disconnect from localhost[127.0.0.1]
```

Hours of searching on the web got me nowhere :( Does anyone have a clue as what's going on here?

---

### Post by bovo13 on 2013-03-13
If this is logged when you try to send from roundcube then you need to set following things:
[COLOR=#FFFFFF][FONT=monospace][B]vi /etc/roundcube/main.inc.php
[/B][/FONT][/COLOR]$rcmail_config['smtp_server'] = 'ssl://localhost';
$rcmail_config['smtp_port'] = 465;
$rcmail_config['smtp_user'] = '%u';
$rcmail_config['smtp_pass'] = '%p';


Hope this will help.

---

### Post by bovo13 on 2013-03-13
Has anyone installed PostVis Admin in addition of this tutorial?

---

### Post by dakong27 on 2013-04-15
Hi All--I followed Flurdy's guide for Ubuntu 12.04, though I have Ubuntu 12.10 64-bit.  Everything works but I cannot send from a mail client or Squirrelmail.  I've been tweaking and googling and tail-ing logs for a solid week and can't crack it, so I'm hoping you folks can help me out.

My /etc/postfix/main.cf:

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
#smtpd_use_tls=no
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.me.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = me.com
mydestination = mail.me.com, me-main.Datian, localhost.Datian, localhost
#mydestination =
#mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128,192.168.2.0/24
mailbox_command = 
mailbox_size_limit = 30000000
recipient_delimiter = +
inet_interfaces = all

masquerade_domains = mail.me.com
local_recipient_maps = 

# how long if undelivered before sending warning update to sender 
delay_warning_time = 4h 
# will it be a permanent error or temporary 
unknown_local_recipient_reject_code = 450 
# how long to keep message on queue before return as failed. 
# some have 3 days, I have 16 days as I am backup server for some people 
# whom go on holiday with their server switched off. 
maximal_queue_lifetime = 7d 
# max and min time in seconds between retries if connection failed 
minimal_backoff_time = 1000s 
maximal_backoff_time = 8000s 
# how long to wait when servers connect before receiving rest of data 
smtp_helo_timeout = 60s 
# how many address can be used in one message. 
# effective stopper to mass spammers, accidental copy in whole address list 
# but may restrict intentional mail shots. 
smtpd_recipient_limit = 16 
# how many error before back off. 
smtpd_soft_error_limit = 3 
# how many max errors before blocking it. 
smtpd_hard_error_limit = 12

# Requirements for the HELO statement 
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, 
        reject_invalid_hostname, permit 
# Requirements for the sender details 
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit 
# Requirements for the connecting server 
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, 
        reject_rbl_client blackholes.easynet.nl, 
        reject_rbl_client dnsbl.njabl.org 
# Requirement for the recipient address 
smtpd_recipient_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_unauth_pipelining,  
        reject_non_fqdn_recipient, reject_unknown_recipient_domain, 
        reject_unauth_destination, permit 
smtpd_data_restrictions = reject_unauth_pipelining

# require proper helo at connections 
smtpd_helo_required = yes 
# waste spammers time before rejecting them 
smtpd_delay_reject = yes 
disable_vrfy_command = yes

# not sure of the difference of the next two 
# but they are needed for local aliasing 
alias_maps = hash:/etc/postfix/aliases 
alias_database = hash:/etc/postfix/aliases 
# this specifies where the virtual mailbox folders will be located 
virtual_mailbox_base = /var/spool/mail/virtual 
# this is for the mailbox location for each user 
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf 
# and this is for aliases 
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf 
# and this is for domain lookups 
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf 
# this is how to connect to the domains (all virtual, but the option is there) 
# not used yet 
# transport_maps = mysql:/etc/postfix/mysql_transport.cf

virtual_uid_maps = static:5000 
virtual_gid_maps = static:5000
home_mailbox = Maildir/


#SASL 
smtpd_sasl_auth_enable = yes 
smtpd_sasl_type = cyrus
#smtpd_sasl_path=/etc/postfix/sasl:/usr/lib/sasl2
smtpd_sasl_path= smtpd
# If your potential clients use Outlook Express or other older clients 
# this needs to be set to yes 
broken_sasl_auth_clients = yes 
smtpd_sasl_security_options = noanonymous 
smtpd_sasl_local_domain =

#SCP: adding this to try to correct ERROR: IMAP dropped the connection
mailbox_transport = virtual
     
my /etc/postfix/master.cf:

#
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       n       -       -       smtpd
#submission inet n       -       -       -       -       smtpd
#  -o smtpd_tls_security_level=encrypt
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#smtps     inet  n       -       -       -       -       smtpd
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#628       inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       -       300     1       oqmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
proxywrite unix -       -       n       -       1       proxymap
smtp      unix  -       -       y       -       -       smtp -v
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay     unix  -       -       y       -       -       smtp
    -o smtp_fallback_relay=
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
#
# ====================================================================
# Interfaces to non-Postfix software. Be sure to examine the manual
# pages of the non-Postfix software to find out what options it wants.
#
# Many of the following services use the Postfix pipe(8) delivery
# agent.  See the pipe(8) man page for information about ${recipient}
# and other message envelope options.
# ====================================================================
#
# maildrop. See the Postfix MAILDROP_README file for details.
# Also specify in main.cf: maildrop_destination_recipient_limit=1
#
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
#
# ====================================================================
#
# Recent Cyrus versions can use the existing "lmtp" master.cf entry.
#
# Specify in cyrus.conf:
#   lmtp    cmd="lmtpd -a" listen="localhost:lmtp" proto=tcp4
#
# Specify in main.cf one or more of the following:
#  mailbox_transport = lmtp:inet:localhost
#  virtual_transport = lmtp:inet:localhost
#
# ====================================================================
#
# Cyrus 2.1.5 (Amos Gouaux)
# Also specify in main.cf: cyrus_destination_recipient_limit=1
#
#cyrus     unix  -       n       n       -       -       pipe
#  user=cyrus argv=/cyrus/bin/deliver -e -r ${sender} -m ${extension} ${user}
#
# ====================================================================
# Old example of delivery via Cyrus.
#
#old-cyrus unix  -       n       n       -       -       pipe
#  flags=R user=cyrus argv=/cyrus/bin/deliver -e -m ${extension} ${user}
#
# ====================================================================
#
# See the Postfix UUCP_README file for configuration details.
#
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
#
# Other external delivery methods.
#
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix    -    n    n    -    2    pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}

submission inet n - y - - smtpd 
 -o smtpd_sasl_auth_enable=yes 
# if you do not want to restrict it encryption only, comment out next line< 
 -o smtpd_tls_auth_only=yes 
# -o smtpd_tls_security_level=encrypt 
# -o header_checks= 
# -o body_checks=< 
 -o smtpd_client_restrictions=permit_sasl_authenticated,reject_unauth_destination,reject 
 -o smtpd_sasl_security_options=noanonymous,noplaintext 
 -o smtpd_sasl_tls_security_options=noanonymous 
# -o milter_macro_daemon_name=ORIGINATING< 
smtps inet n - y - - smtpd 
 -o smtpd_tls_wrappermode=yes 
 -o smtpd_sasl_auth_enable=yes 
 -o smtpd_tls_auth_only=yes 
 -o smtpd_client_restrictions=permit_sasl_authenticated,reject 
 -o smtpd_sasl_security_options=noanonymous,noplaintext 
 -o smtpd_sasl_tls_security_options=noanonymous 
# -o milter_macro_daemon_name=ORIGINATING
#smtp      inet  n       -       n       -       1       postscreen
#smtpd     pass  -       -       n       -       -       smtpd
#dnsblog   unix  -       -       n       -       0       dnsblog
#tlsproxy  unix  -       -       n       -       0       tlsproxy

My /etc/postfix/sasl/smtp.conf:

pwcheck_method: saslauthd
#mech_list: plain login pam
#mech_list: plain login
mech_list: plain login cram-md5 digest-md5
#saslauthd_path: /var/run/saslauthd/mux
#saslauthd_path: /var/spool/postfix/var/run/saslauthd/mux
#authdaemond_path: /var/spool/authdaemon/socket
log_level: 7
allow_plaintext: true
auxprop_plugin: sql
#auxprop_plugin: mysql
sql_engine: mysql
sql_hostnames: localhost
#sql_hostnames: 127.0.0.1
sql_user: mail
#sql_passw: password
sql_passwd: password
sql_database: maildb
#sql_select: select crypt from users where id='%u@%r' and enabled=1
sql_select: select crypt from users where id='%u' and enabled=1

My /var/log/mail.log:

Apr 15 14:07:18 me-main postfix/smtpd[18339]: connect from dsl081-198-066.nyc2.dsl.isp.net[8.8.8.8]
Apr 15 14:07:23 me-main postfix/smtpd[18339]: warning: dsl081-198-066.nyc2.dsl.isp.net[8.8.8.8]: SASL PLAIN authentication failed: generic failure
Apr 15 14:07:25 me-main postfix/smtpd[18339]: disconnect from dsl081-198-066.nyc2.dsl.isp.net[8.8.8.8]
Apr 15 14:10:45 me-main postfix/anvil[18341]: statistics: max connection rate 1/60s for (submission:8.8.8.8) at Apr 15 14:07:18
Apr 15 14:10:45 me-main postfix/anvil[18341]: statistics: max connection count 1 for (submission:8.8.8.8) at Apr 15 14:07:18
Apr 15 14:10:45 me-main postfix/anvil[18341]: statistics: max cache size 1 at Apr 15 14:07:18
                                                                                  
My /var/log/auth.log:

Apr 15 14:07:23 me-main postfix/smtpd[18339]: sql plugin trying to open db 'maildb' on host 'localhost'
Apr 15 14:07:23 me-main postfix/smtpd[18339]: sql plugin could not connect to host localhost
Apr 15 14:07:23 me-main postfix/smtpd[18339]: sql plugin couldn't connect to any host
Apr 15 14:07:23 me-main postfix/smtpd[18339]: sql plugin Parse the username [EMAIL="user@me.com"]user@me.com[/EMAIL]
Apr 15 14:07:23 me-main postfix/smtpd[18339]: sql plugin try and connect to a host
Apr 15 14:07:23 me-main postfix/smtpd[18339]: sql plugin trying to open db 'maildb' on host 'localhost'
Apr 15 14:07:23 me-main postfix/smtpd[18339]: sql plugin could not connect to host localhost
Apr 15 14:07:23 me-main postfix/smtpd[18339]: sql plugin couldn't connect to any host

I've read everything I can get my hands on from Falko Timme's threads, explored the possibility chroot being at the source of my troubles, and even tried downgrading sasl per an earlier guide for Ubuntu 11.10, but I'm getting nowhere.  I'm really stumped, so any help would be much appreciated.

---

### Post by bovo13 on 2013-04-15
Try to use 127.0.0.1 for sql_hostname in smtp.conf 
> **dakong27 said:**
> Hi All--I followed Flurdy's guide for Ubuntu 12.04, though I have Ubuntu 12.10 64-bit.  Everything works but I cannot send from a mail client or Squirrelmail.  I've been tweaking and googling and tail-ing logs for a solid week and can't crack it, so I'm hoping you folks can help me out.

My /etc/postfix/main.cf:

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
#smtpd_use_tls=no
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.me.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = me.com
mydestination = mail.me.com, me-main.Datian, localhost.Datian, localhost
#mydestination =
#mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128,192.168.2.0/24
mailbox_command = 
mailbox_size_limit = 30000000
recipient_delimiter = +
inet_interfaces = all

masquerade_domains = mail.me.com
local_recipient_maps = 

# how long if undelivered before sending warning update to sender 
delay_warning_time = 4h 
# will it be a permanent error or temporary 
unknown_local_recipient_reject_code = 450 
# how long to keep message on queue before return as failed. 
# some have 3 days, I have 16 days as I am backup server for some people 
# whom go on holiday with their server switched off. 
maximal_queue_lifetime = 7d 
# max and min time in seconds between retries if connection failed 
minimal_backoff_time = 1000s 
maximal_backoff_time = 8000s 
# how long to wait when servers connect before receiving rest of data 
smtp_helo_timeout = 60s 
# how many address can be used in one message. 
# effective stopper to mass spammers, accidental copy in whole address list 
# but may restrict intentional mail shots. 
smtpd_recipient_limit = 16 
# how many error before back off. 
smtpd_soft_error_limit = 3 
# how many max errors before blocking it. 
smtpd_hard_error_limit = 12

# Requirements for the HELO statement 
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, 
        reject_invalid_hostname, permit 
# Requirements for the sender details 
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit 
# Requirements for the connecting server 
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, 
        reject_rbl_client blackholes.easynet.nl, 
        reject_rbl_client dnsbl.njabl.org 
# Requirement for the recipient address 
smtpd_recipient_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_unauth_pipelining,  
        reject_non_fqdn_recipient, reject_unknown_recipient_domain, 
        reject_unauth_destination, permit 
smtpd_data_restrictions = reject_unauth_pipelining

# require proper helo at connections 
smtpd_helo_required = yes 
# waste spammers time before rejecting them 
smtpd_delay_reject = yes 
disable_vrfy_command = yes

# not sure of the difference of the next two 
# but they are needed for local aliasing 
alias_maps = hash:/etc/postfix/aliases 
alias_database = hash:/etc/postfix/aliases 
# this specifies where the virtual mailbox folders will be located 
virtual_mailbox_base = /var/spool/mail/virtual 
# this is for the mailbox location for each user 
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf 
# and this is for aliases 
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf 
# and this is for domain lookups 
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf 
# this is how to connect to the domains (all virtual, but the option is there) 
# not used yet 
# transport_maps = mysql:/etc/postfix/mysql_transport.cf

virtual_uid_maps = static:5000 
virtual_gid_maps = static:5000
home_mailbox = Maildir/


#SASL 
smtpd_sasl_auth_enable = yes 
smtpd_sasl_type = cyrus
#smtpd_sasl_path=/etc/postfix/sasl:/usr/lib/sasl2
smtpd_sasl_path= smtpd
# If your potential clients use Outlook Express or other older clients 
# this needs to be set to yes 
broken_sasl_auth_clients = yes 
smtpd_sasl_security_options = noanonymous 
smtpd_sasl_local_domain =

#SCP: adding this to try to correct ERROR: IMAP dropped the connection
mailbox_transport = virtual
     
my /etc/postfix/master.cf:

#
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       n       -       -       smtpd
#submission inet n       -       -       -       -       smtpd
#  -o smtpd_tls_security_level=encrypt
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#smtps     inet  n       -       -       -       -       smtpd
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#628       inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       -       300     1       oqmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
proxywrite unix -       -       n       -       1       proxymap
smtp      unix  -       -       y       -       -       smtp -v
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay     unix  -       -       y       -       -       smtp
    -o smtp_fallback_relay=
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
#
# ====================================================================
# Interfaces to non-Postfix software. Be sure to examine the manual
# pages of the non-Postfix software to find out what options it wants.
#
# Many of the following services use the Postfix pipe(8) delivery
# agent.  See the pipe(8) man page for information about ${recipient}
# and other message envelope options.
# ====================================================================
#
# maildrop. See the Postfix MAILDROP_README file for details.
# Also specify in main.cf: maildrop_destination_recipient_limit=1
#
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
#
# ====================================================================
#
# Recent Cyrus versions can use the existing "lmtp" master.cf entry.
#
# Specify in cyrus.conf:
#   lmtp    cmd="lmtpd -a" listen="localhost:lmtp" proto=tcp4
#
# Specify in main.cf one or more of the following:
#  mailbox_transport = lmtp:inet:localhost
#  virtual_transport = lmtp:inet:localhost
#
# ====================================================================
#
# Cyrus 2.1.5 (Amos Gouaux)
# Also specify in main.cf: cyrus_destination_recipient_limit=1
#
#cyrus     unix  -       n       n       -       -       pipe
#  user=cyrus argv=/cyrus/bin/deliver -e -r ${sender} -m ${extension} ${user}
#
# ====================================================================
# Old example of delivery via Cyrus.
#
#old-cyrus unix  -       n       n       -       -       pipe
#  flags=R user=cyrus argv=/cyrus/bin/deliver -e -m ${extension} ${user}
#
# ====================================================================
#
# See the Postfix UUCP_README file for configuration details.
#
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
#
# Other external delivery methods.
#
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix    -    n    n    -    2    pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}

submission inet n - y - - smtpd 
 -o smtpd_sasl_auth_enable=yes 
# if you do not want to restrict it encryption only, comment out next line< 
 -o smtpd_tls_auth_only=yes 
# -o smtpd_tls_security_level=encrypt 
# -o header_checks= 
# -o body_checks=< 
 -o smtpd_client_restrictions=permit_sasl_authenticated,reject_unauth_destination,reject 
 -o smtpd_sasl_security_options=noanonymous,noplaintext 
 -o smtpd_sasl_tls_security_options=noanonymous 
# -o milter_macro_daemon_name=ORIGINATING< 
smtps inet n - y - - smtpd 
 -o smtpd_tls_wrappermode=yes 
 -o smtpd_sasl_auth_enable=yes 
 -o smtpd_tls_auth_only=yes 
 -o smtpd_client_restrictions=permit_sasl_authenticated,reject 
 -o smtpd_sasl_security_options=noanonymous,noplaintext 
 -o smtpd_sasl_tls_security_options=noanonymous 
# -o milter_macro_daemon_name=ORIGINATING
#smtp      inet  n       -       n       -       1       postscreen
#smtpd     pass  -       -       n       -       -       smtpd
#dnsblog   unix  -       -       n       -       0       dnsblog
#tlsproxy  unix  -       -       n       -       0       tlsproxy

My /etc/postfix/sasl/smtp.conf:

pwcheck_method: saslauthd
#mech_list: plain login pam
#mech_list: plain login
mech_list: plain login cram-md5 digest-md5
#saslauthd_path: /var/run/saslauthd/mux
#saslauthd_path: /var/spool/postfix/var/run/saslauthd/mux
#authdaemond_path: /var/spool/authdaemon/socket
log_level: 7
allow_plaintext: true
auxprop_plugin: sql
#auxprop_plugin: mysql
sql_engine: mysql
sql_hostnames: localhost
#sql_hostnames: 127.0.0.1
sql_user: mail
#sql_passw: password
sql_passwd: password
sql_database: maildb
#sql_select: select crypt from users where id='%u@%r' and enabled=1
sql_select: select crypt from users where id='%u' and enabled=1

My /var/log/mail.log:

Apr 15 14:07:18 me-main postfix/smtpd[18339]: connect from dsl081-198-066.nyc2.dsl.isp.net[8.8.8.8]
Apr 15 14:07:23 me-main postfix/smtpd[18339]: warning: dsl081-198-066.nyc2.dsl.isp.net[8.8.8.8]: SASL PLAIN authentication failed: generic failure
Apr 15 14:07:25 me-main postfix/smtpd[18339]: disconnect from dsl081-198-066.nyc2.dsl.isp.net[8.8.8.8]
Apr 15 14:10:45 me-main postfix/anvil[18341]: statistics: max connection rate 1/60s for (submission:8.8.8.8) at Apr 15 14:07:18
Apr 15 14:10:45 me-main postfix/anvil[18341]: statistics: max connection count 1 for (submission:8.8.8.8) at Apr 15 14:07:18
Apr 15 14:10:45 me-main postfix/anvil[18341]: statistics: max cache size 1 at Apr 15 14:07:18
                                                                                  
My /var/log/auth.log:

Apr 15 14:07:23 me-main postfix/smtpd[18339]: sql plugin trying to open db 'maildb' on host 'localhost'
Apr 15 14:07:23 me-main postfix/smtpd[18339]: sql plugin could not connect to host localhost
Apr 15 14:07:23 me-main postfix/smtpd[18339]: sql plugin couldn't connect to any host
Apr 15 14:07:23 me-main postfix/smtpd[18339]: sql plugin Parse the username [EMAIL="user@me.com"]user@me.com[/EMAIL]
Apr 15 14:07:23 me-main postfix/smtpd[18339]: sql plugin try and connect to a host
Apr 15 14:07:23 me-main postfix/smtpd[18339]: sql plugin trying to open db 'maildb' on host 'localhost'
Apr 15 14:07:23 me-main postfix/smtpd[18339]: sql plugin could not connect to host localhost
Apr 15 14:07:23 me-main postfix/smtpd[18339]: sql plugin couldn't connect to any host

I've read everything I can get my hands on from Falko Timme's threads, explored the possibility chroot being at the source of my troubles, and even tried downgrading sasl per an earlier guide for Ubuntu 11.10, but I'm getting nowhere.  I'm really stumped, so any help would be much appreciated.

---

### Post by m_gustafsson on 2013-07-02
Hi,

thanks for a very nice guide!
I have one issue that I can't seem to solve.

If I log in locally with telnet on my mail server and try to send an email to root@localhost it looks to me like the email address is mapped to [EMAIL="root@localhost.mydomain.com"]root@localhost.mydomain.com[/EMAIL]. I would have expected that it should be mapped to [EMAIL="root@mydomain.com"]root@mydomain.com[/EMAIL]. In my mail log I see this:
```

 Jul  2 09:56:31 mailserver postfix/smtp[8085]: A966FCC046F: to=<root@localhost.mydomin.com>, orig_to=<root@localhost>, relay=127.0.0.1[127.0.0.1]:10024, delay=18, delays=12/0.02/0/5.5, dsn=2.0.0, status=sent (250 2.0.0 from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as B508ECC1167)

```

The mail does not arrive in /var/mail/virtual/root/new.

My aliases table looks like follows:
```

mysql> select * from aliases;
+------+---------------------------------------+---------------------------------+---------+
| pkid | mail                                  | destination                     | enabled |
+------+---------------------------------------+---------------------------------+---------+
|    1 | postmaster@localhost            | root@localhost                  |       1 |
|    2 | sysadmin@localhost               | root@localhost                  |       1 |
|    3 | webmaster@localhost             | root@localhost                  |       1 |
|    4 | abuse@localhost                     | root@localhost                  |       1 |
|    5 | root@localhost                         | [EMAIL="root@mydomain.com"]root@mydomain.com[/EMAIL] |       1 |
|    6 | @localhost                               | @mydomain.com     |       1 |
|    7 | @localhost.localdomain           | @localhost                      |       1 |
|    8 | @mydomain.com                     | postmaster@localhost            |       1 |
|    9 | [EMAIL="postmaster@mydomain.com"]postmaster@mydomain.com[/EMAIL]  | postmaster@localhost            |       1 |
|   10 | [EMAIL="abuse@mydomain.com"]abuse@mydomain.com[/EMAIL]         | abuse@localhost                 |       1 |
|   11 | [EMAIL="mats@mydomain.com"]mats@mydomain.com[/EMAIL]           | [EMAIL="mats@mydomain.com"]mats@mydomain.com[/EMAIL] |       1 |
+------+---------------------------------------+---------------------------------+---------+

```

My users table:

```

mysql> select * from users;
+---------------------------------+------+------+------+-------------------------+---------+---------+-----------------+----------+-------------------------+-------+------------+----------------+
| id                              | name | uid  | gid  | home                    | maildir | enabled | change_password | clear    | crypt                   | quota | procmailrc | spamassassinrc |
+---------------------------------+------+------+------+-------------------------+---------+---------+-----------------+----------+-------------------------+-------+------------+----------------+
| mats@mydomain.com | mats | 5000 | 5000 | /var/spool/mail/virtual | mats/   |       1 |               1 | ChangeMe | *************** |       |            |                |
| root@mydomain.com | root | 5000 | 5000 | /var/spool/mail/virtual | root/   |       1 |               1 | ChangeMe | ************           |       |            |                |
+---------------------------------+------+------+------+-------------------------+---------+---------+-----------------+----------+-------------------------+-------+------------+----------------+

```

My domains table:
```

mysql> select * from domains;
+------+----------------------------+-----------+---------+
| pkid | domain                     | transport | enabled |
+------+----------------------------+-----------+---------+
|    1 | localhost                  | virtual:  |       1 |
|    2 | localhost.localdomain      | virtual:  |       1 |
|    3 | mydomain.com | virtual:  |       1 |
|    4 | mydomain.com | virtual:  |       1 |
+------+----------------------------+-----------+---------+

```

If I try to email to postmaster@localhost it will be mapped to  [EMAIL="postmaster@localhost.mydomain.com"]postmaster@localhost.mydomain.com[/EMAIL] while I would have expected it to be mapped to root@localhost and then to [EMAIL="root@mydomain.com"]root@mydomain.com[/EMAIL].
An email to mats@localhost will be mapped to [EMAIL="mats@localhost.mydomain.com"]mats@localhost.mydomain.com[/EMAIL], while an email sent to [EMAIL="mats@mydomain.com"]mats@mydomain.com[/EMAIL] is delivered to [EMAIL="mats@mydomain.com"]mats@mydomain.com[/EMAIL], as I would expect.

Any idea on what I am doing wrong? Why is "localhost" being added to the addresses?

Many thanks for any help.

/Mats

---

### Post by flurdy on 2013-07-05
> **m_gustafsson said:**
> Hi,


My aliases table looks like follows:
```

mysql> select * from aliases;
+------+---------------------------------------+---------------------------------+---------+
| pkid | mail                                  | destination                     | enabled |
+------+---------------------------------------+---------------------------------+---------+
|    1 | postmaster@localhost            | root@localhost                  |       1 |
|    2 | sysadmin@localhost               | root@localhost                  |       1 |
|    3 | webmaster@localhost             | root@localhost                  |       1 |
|    4 | abuse@localhost                     | root@localhost                  |       1 |
|    5 | root@localhost                         | [EMAIL="root@mydomain.com"]root@mydomain.com[/EMAIL] |       1 |
|    6 | @localhost                               | @mydomain.com     |       1 |
|    7 | @localhost.localdomain           | @localhost                      |       1 |
|    8 | @mydomain.com                     | postmaster@localhost            |       1 |
|    9 | [EMAIL="postmaster@mydomain.com"]postmaster@mydomain.com[/EMAIL]  | postmaster@localhost            |       1 |
|   10 | [EMAIL="abuse@mydomain.com"]abuse@mydomain.com[/EMAIL]         | abuse@localhost                 |       1 |
|   11 | [EMAIL="mats@mydomain.com"]mats@mydomain.com[/EMAIL]           | [EMAIL="mats@mydomain.com"]mats@mydomain.com[/EMAIL] |       1 |
+------+---------------------------------------+---------------------------------+---------+

```




If this is your aliases table I think you have some cyclical routing.

root@localhost goes to [email]root@mydomain.com[/email]
[email]root@mydomain.com[/email] is not specified but is caught by catchall @mydomain.com
@mydomain.com goes to postmaster@localhost
postmaster@localhost goes to root@localhost and round again...

---

### Post by m_gustafsson on 2013-07-08
> **flurdy said:**
> If this is your aliases table I think you have some cyclical routing.

root@localhost goes to [EMAIL="root@mydomain.com"]root@mydomain.com[/EMAIL]
[EMAIL="root@mydomain.com"]root@mydomain.com[/EMAIL] is not specified but is caught by catchall @mydomain.com
@mydomain.com goes to postmaster@localhost
postmaster@localhost goes to root@localhost and round again...

Thanks for the reply :P. I see your point and I will correct this.

By the way, do you have any clue to my other question, see below:
> 
[COLOR=#000000]An email to mats@localhost will be mapped to [/COLOR][mats@localhost.mydomain.com]("https://mail.google.com/mail/?view=cm&fs=1&tf=1&to=mats@localhost.mydomain.com")[COLOR=#000000], while an email sent to [/COLOR][mats@mydomain.com]("https://mail.google.com/mail/?view=cm&fs=1&tf=1&to=mats@mydomain.com")[COLOR=#000000] is delivered to [/COLOR][mats@mydomain.com]("https://mail.google.com/mail/?view=cm&fs=1&tf=1&to=mats@mydomain.com")[COLOR=#000000], as I would expect.[/COLOR]
[COLOR=#000000]Any idea on what I am doing wrong? Why is "localhost" being added to the addresses?[/COLOR]


I could only think of my /etc/mailname,  /etc/hosts and /etc/hostname being involved here, and they looks like this:
```

$ cat /etc/mailname 
server4.mydomain.com

 $ cat /etc/hosts
127.0.0.1    localhost.localdomain localhost
192.168.0.13    server4.mydomain.com server4


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

$ cat /etc/hostname
server4.mydomain.com




```

Best regards, Mats

---

### Post by wmellema on 2013-07-09
Hello setting up my first email server using the awesome HowTo. I'm setting it up on a vanilla Ubuntu machine on Amazon AWS. I ran into a problem during testing. I can receive OK but when I try to send I see this error message in the mail log:

Jul  9 18:37:10 ip-172-31-45-190 postfix/smtp[10432]: D5DD56DAAA: to=<xxxxxx@gmail.com>, relay=email-smtp.us-east-1.amazonaws.com[107.21.238.216]:25, delay=87, delays=86/0.01/0.38/0.08, dsn=5.0.0, status=bounced (host email-smtp.us-east-1.amazonaws.com[107.21.238.216] said: 530 Authentication required (in reply to MAIL FROM command)).

This is what appears in the terminal window:

ubuntu@ip-172-31-45-190:~/121mailr$ openssl s_client -crlf -quiet -connect email-smtp.us-east-1.amazonaws.com:465
depth=2 C = US, O = "VeriSign, Inc.", OU = VeriSign Trust Network, OU = "(c) 2006 VeriSign, Inc. - For authorized use only", CN = VeriSign Class 3 Public Primary Certification Authority - G5
verify error:num=20:unable to get local issuer certificate
verify return:0
220 email-smtp.amazonaws.com ESMTP SimpleEmailService-376766033
421 Timeout waiting for data from client.

This isn't mentioned in the How To. I've googled it but haven't found anything helpful. It pauses briefly at the "220" line, before displaying the "421 line so I'm guessing it's waiting for my SMTP credentials or something? This isn't mentioned in the How To so I'm wondering if I missed a configuration step or if there's one missing? Thanks in advance for the help.

UPDATE: I just realized why it's not covered in the How To. I'm using Amazon SES for outbound mail. Anyone know how to configure for this? Thanks.

UPDATE2: SOLVED OK figured it out myself. Sometimes it helps to go do something else for a while and come back to it : )
[Here's where I found the info about configuring postfix to use SES for outgoing mail]("http://docs.aws.amazon.com/ses/latest/DeveloperGuide/postfix.html")

---

### Post by m_gustafsson on 2013-07-10
> **m_gustafsson said:**
> [COLOR=#000000][COLOR=#000000]*An email to mats@localhost will be mapped to *[/COLOR][/COLOR][mats@localhost.mydomain.com]("https://mail.google.com/mail/?view=cm&fs=1&tf=1&to=mats@localhost.mydomain.com")[COLOR=#000000][COLOR=#000000]*, while an email sent to *[/COLOR][/COLOR][mats@mydomain.com]("https://mail.google.com/mail/?view=cm&fs=1&tf=1&to=mats@mydomain.com")[COLOR=#000000][COLOR=#000000]* is delivered to *[/COLOR][/COLOR][mats@mydomain.com]("https://mail.google.com/mail/?view=cm&fs=1&tf=1&to=mats@mydomain.com")[COLOR=#000000][COLOR=#000000]*, as I would expect.*[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][I]Any idea on what I am doing wrong? Why is "localhost" being added to the addresses?
[/I][/COLOR][/COLOR]

I can now send emails to [EMAIL="mats@mydomain.com"]mats@mydomain.com[/EMAIL], mats@localhost, root@localhost and postmaster@localhost. What I did was to set my domains, aliases and users tables as below:
```


mysql> select * from domains;
+------+----------------------------+-----------+---------+
| pkid | domain                     | transport | enabled |
+------+----------------------------+-----------+---------+
|    9 | mydomain.com               | virtual:  |       1 |
+------+----------------------------+-----------+---------+

mysql> select * from aliases;
+------+---------------------------------------+-----------------------------+---------+
| pkid | mail                                  | destination                 | enabled |
+------+---------------------------------------+-----------------------------+---------+
|    8 | @localhost.mydomain.com               | @mydomain.com               |       1 |
|    9 | postmaster@mydomain.com               | root@localhost              |       1 |

mysql> select * from users;
+---------------------------------+------+------+------+-------------------------+---------+---------+-----------------+----------+-------------------------+-------+------------+----------------+
| id                              | name | uid  | gid  | home                    | maildir | enabled | change_password | clear    | crypt                   | quota | procmailrc | spamassassinrc |
+---------------------------------+------+------+------+-------------------------+---------+---------+-----------------+----------+-------------------------+-------+------------+----------------+
| mats@mydomain.com               | mats | 5000 | 5000 | /var/spool/mail/virtual | mats/   |       1 |               1 | ChangeMe | *********************** |       |            |                |
| root@mydomain.com               | root | 5000 | 5000 | /var/spool/mail/virtual | root/   |       1 |               1 | ChangeMe | *******************     |       |            |                |
+---------------------------------+------+------+------+-------------------------+---------+---------+-----------------+----------+-------------------------+-------+------------+----------------+


```

So, as I understand it, everything sent to "xxx@localhost" gets mapped to "xxx@localhost.mydomain.com" (do not know why). Thus an email sent to postmaster@localhost will, through the aliases tables, get mapped to: [EMAIL="postmaster@mydomain.com"]postmaster@mydomain.com[/EMAIL] -> root@localhost -> [EMAIL="root@localhost.mydomain.com"]root@localhost.mydomain.com[/EMAIL] -> [EMAIL="root@mydomain.com"]root@mydomain.com[/EMAIL]. [EMAIL="root@mydomain.com"]root@mydomain.com[/EMAIL] will then be delivered to the user root.

Don't know if I am totally at lost now, but it seems to work like this.

/Mats

---

### Post by m_gustafsson on 2013-07-17
Hi,
I have decided to go for RoundCube for my webmail.
When configuring RoundCube I understand that it sets up its own database and that that database does not match with the one set up in this guide, e.g. the users tables.
Is there a "recommended" way to deal with this? Do you use the database created by RoundCube and put it into use for postfix through the main.cf file, or is there a way to get RoundCube to use another database, for example the database set up in this guide?
Or, have I done a mistake configuring RoundCube, when using (in Ubuntu):
```

# dpkg-reconfigure roundcube-core

```

Mats

---

### Post by m_gustafsson on 2013-07-19
> **m_gustafsson said:**
> Hi,
I have decided to go for RoundCube for my webmail.
When configuring RoundCube I understand that it sets up its own database and that that database does not match with the one set up in this guide, e.g. the users tables.
Is there a "recommended" way to deal with this? Do you use the database created by RoundCube and put it into use for postfix through the main.cf file, or is there a way to get RoundCube to use another database, for example the database set up in this guide?
Or, have I done a mistake configuring RoundCube, when using (in Ubuntu):
```

# dpkg-reconfigure roundcube-core

```

Mats

The reason for my question above was that I could not log in to roundcube using my "mail" user. When looking into the mail log I saw that there was a mismatch in the field name of the users table, i.e. the field name carrying my email address was "id" while roundcube was asking for "username". I then misunderstood the way the databases are used, hence my question.
Anyway, tonight I modified the field name of my users table:
```

mysql> alter table users change id username varchar (128);

```
After that I was able to log in.

/Mats

---

### Post by m_gustafsson on 2013-07-31
Dakong27,

did you find a solution to your problem?
I believe that I have a similar issue.
If I remove the line:```
 [COLOR=#000000]-o smtpd_client_restrictions=permit_sasl_authenticated,reject [/COLOR]
```
from my master.cf I am able to send emails (from RoundCube). Is it the same in your case? 
Btw, I think it should be "[COLOR=#000000]permit_sasl_authenticated", it looks like you have "[/COLOR][COLOR=#000000]permit_sasl_authenticate d", with a space before "d".[/COLOR]

/M
 
> **dakong27 said:**
> Hi All--I followed Flurdy's guide for Ubuntu 12.04, though I have Ubuntu 12.10 64-bit.  Everything works but I cannot send from a mail client or Squirrelmail.  I've been tweaking and googling and tail-ing logs for a solid week and can't crack it, so I'm hoping you folks can help me out.

My /etc/postfix/main.cf:

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
#smtpd_use_tls=no
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.me.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = me.com
mydestination = mail.me.com, me-main.Datian, localhost.Datian, localhost
#mydestination =
#mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128,192.168.2.0/24
mailbox_command = 
mailbox_size_limit = 30000000
recipient_delimiter = +
inet_interfaces = all

masquerade_domains = mail.me.com
local_recipient_maps = 

# how long if undelivered before sending warning update to sender 
delay_warning_time = 4h 
# will it be a permanent error or temporary 
unknown_local_recipient_reject_code = 450 
# how long to keep message on queue before return as failed. 
# some have 3 days, I have 16 days as I am backup server for some people 
# whom go on holiday with their server switched off. 
maximal_queue_lifetime = 7d 
# max and min time in seconds between retries if connection failed 
minimal_backoff_time = 1000s 
maximal_backoff_time = 8000s 
# how long to wait when servers connect before receiving rest of data 
smtp_helo_timeout = 60s 
# how many address can be used in one message. 
# effective stopper to mass spammers, accidental copy in whole address list 
# but may restrict intentional mail shots. 
smtpd_recipient_limit = 16 
# how many error before back off. 
smtpd_soft_error_limit = 3 
# how many max errors before blocking it. 
smtpd_hard_error_limit = 12

# Requirements for the HELO statement 
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, 
        reject_invalid_hostname, permit 
# Requirements for the sender details 
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit 
# Requirements for the connecting server 
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, 
        reject_rbl_client blackholes.easynet.nl, 
        reject_rbl_client dnsbl.njabl.org 
# Requirement for the recipient address 
smtpd_recipient_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_unauth_pipelining,  
        reject_non_fqdn_recipient, reject_unknown_recipient_domain, 
        reject_unauth_destination, permit 
smtpd_data_restrictions = reject_unauth_pipelining

# require proper helo at connections 
smtpd_helo_required = yes 
# waste spammers time before rejecting them 
smtpd_delay_reject = yes 
disable_vrfy_command = yes

# not sure of the difference of the next two 
# but they are needed for local aliasing 
alias_maps = hash:/etc/postfix/aliases 
alias_database = hash:/etc/postfix/aliases 
# this specifies where the virtual mailbox folders will be located 
virtual_mailbox_base = /var/spool/mail/virtual 
# this is for the mailbox location for each user 
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf 
# and this is for aliases 
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf 
# and this is for domain lookups 
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf 
# this is how to connect to the domains (all virtual, but the option is there) 
# not used yet 
# transport_maps = mysql:/etc/postfix/mysql_transport.cf

virtual_uid_maps = static:5000 
virtual_gid_maps = static:5000
home_mailbox = Maildir/


#SASL 
smtpd_sasl_auth_enable = yes 
smtpd_sasl_type = cyrus
#smtpd_sasl_path=/etc/postfix/sasl:/usr/lib/sasl2
smtpd_sasl_path= smtpd
# If your potential clients use Outlook Express or other older clients 
# this needs to be set to yes 
broken_sasl_auth_clients = yes 
smtpd_sasl_security_options = noanonymous 
smtpd_sasl_local_domain =

#SCP: adding this to try to correct ERROR: IMAP dropped the connection
mailbox_transport = virtual
     
my /etc/postfix/master.cf:

#
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       n       -       -       smtpd
#submission inet n       -       -       -       -       smtpd
#  -o smtpd_tls_security_level=encrypt
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#smtps     inet  n       -       -       -       -       smtpd
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#628       inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       -       300     1       oqmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
proxywrite unix -       -       n       -       1       proxymap
smtp      unix  -       -       y       -       -       smtp -v
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay     unix  -       -       y       -       -       smtp
    -o smtp_fallback_relay=
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
#
# ====================================================================
# Interfaces to non-Postfix software. Be sure to examine the manual
# pages of the non-Postfix software to find out what options it wants.
#
# Many of the following services use the Postfix pipe(8) delivery
# agent.  See the pipe(8) man page for information about ${recipient}
# and other message envelope options.
# ====================================================================
#
# maildrop. See the Postfix MAILDROP_README file for details.
# Also specify in main.cf: maildrop_destination_recipient_limit=1
#
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
#
# ====================================================================
#
# Recent Cyrus versions can use the existing "lmtp" master.cf entry.
#
# Specify in cyrus.conf:
#   lmtp    cmd="lmtpd -a" listen="localhost:lmtp" proto=tcp4
#
# Specify in main.cf one or more of the following:
#  mailbox_transport = lmtp:inet:localhost
#  virtual_transport = lmtp:inet:localhost
#
# ====================================================================
#
# Cyrus 2.1.5 (Amos Gouaux)
# Also specify in main.cf: cyrus_destination_recipient_limit=1
#
#cyrus     unix  -       n       n       -       -       pipe
#  user=cyrus argv=/cyrus/bin/deliver -e -r ${sender} -m ${extension} ${user}
#
# ====================================================================
# Old example of delivery via Cyrus.
#
#old-cyrus unix  -       n       n       -       -       pipe
#  flags=R user=cyrus argv=/cyrus/bin/deliver -e -m ${extension} ${user}
#
# ====================================================================
#
# See the Postfix UUCP_README file for configuration details.
#
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
#
# Other external delivery methods.
#
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix    -    n    n    -    2    pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}

submission inet n - y - - smtpd 
 -o smtpd_sasl_auth_enable=yes 
# if you do not want to restrict it encryption only, comment out next line< 
 -o smtpd_tls_auth_only=yes 
# -o smtpd_tls_security_level=encrypt 
# -o header_checks= 
# -o body_checks=< 
 -o smtpd_client_restrictions=permit_sasl_authenticated,reject_unauth_destination,reject 
 -o smtpd_sasl_security_options=noanonymous,noplaintext 
 -o smtpd_sasl_tls_security_options=noanonymous 
# -o milter_macro_daemon_name=ORIGINATING< 
smtps inet n - y - - smtpd 
 -o smtpd_tls_wrappermode=yes 
 -o smtpd_sasl_auth_enable=yes 
 -o smtpd_tls_auth_only=yes 
 -o smtpd_client_restrictions=permit_sasl_authenticated,reject 
 -o smtpd_sasl_security_options=noanonymous,noplaintext 
 -o smtpd_sasl_tls_security_options=noanonymous 
# -o milter_macro_daemon_name=ORIGINATING
#smtp      inet  n       -       n       -       1       postscreen
#smtpd     pass  -       -       n       -       -       smtpd
#dnsblog   unix  -       -       n       -       0       dnsblog
#tlsproxy  unix  -       -       n       -       0       tlsproxy

My /etc/postfix/sasl/smtp.conf:

pwcheck_method: saslauthd
#mech_list: plain login pam
#mech_list: plain login
mech_list: plain login cram-md5 digest-md5
#saslauthd_path: /var/run/saslauthd/mux
#saslauthd_path: /var/spool/postfix/var/run/saslauthd/mux
#authdaemond_path: /var/spool/authdaemon/socket
log_level: 7
allow_plaintext: true
auxprop_plugin: sql
#auxprop_plugin: mysql
sql_engine: mysql
sql_hostnames: localhost
#sql_hostnames: 127.0.0.1
sql_user: mail
#sql_passw: password
sql_passwd: password
sql_database: maildb
#sql_select: select crypt from users where id='%u@%r' and enabled=1
sql_select: select crypt from users where id='%u' and enabled=1

My /var/log/mail.log:

Apr 15 14:07:18 me-main postfix/smtpd[18339]: connect from dsl081-198-066.nyc2.dsl.isp.net[8.8.8.8]
Apr 15 14:07:23 me-main postfix/smtpd[18339]: warning: dsl081-198-066.nyc2.dsl.isp.net[8.8.8.8]: SASL PLAIN authentication failed: generic failure
Apr 15 14:07:25 me-main postfix/smtpd[18339]: disconnect from dsl081-198-066.nyc2.dsl.isp.net[8.8.8.8]
Apr 15 14:10:45 me-main postfix/anvil[18341]: statistics: max connection rate 1/60s for (submission:8.8.8.8) at Apr 15 14:07:18
Apr 15 14:10:45 me-main postfix/anvil[18341]: statistics: max connection count 1 for (submission:8.8.8.8) at Apr 15 14:07:18
Apr 15 14:10:45 me-main postfix/anvil[18341]: statistics: max cache size 1 at Apr 15 14:07:18
                                                                                  
My /var/log/auth.log:

Apr 15 14:07:23 me-main postfix/smtpd[18339]: sql plugin trying to open db 'maildb' on host 'localhost'
Apr 15 14:07:23 me-main postfix/smtpd[18339]: sql plugin could not connect to host localhost
Apr 15 14:07:23 me-main postfix/smtpd[18339]: sql plugin couldn't connect to any host
Apr 15 14:07:23 me-main postfix/smtpd[18339]: sql plugin Parse the username [EMAIL="user@me.com"]user@me.com[/EMAIL]
Apr 15 14:07:23 me-main postfix/smtpd[18339]: sql plugin try and connect to a host
Apr 15 14:07:23 me-main postfix/smtpd[18339]: sql plugin trying to open db 'maildb' on host 'localhost'
Apr 15 14:07:23 me-main postfix/smtpd[18339]: sql plugin could not connect to host localhost
Apr 15 14:07:23 me-main postfix/smtpd[18339]: sql plugin couldn't connect to any host

I've read everything I can get my hands on from Falko Timme's threads, explored the possibility chroot being at the source of my troubles, and even tried downgrading sasl per an earlier guide for Ubuntu 11.10, but I'm getting nowhere.  I'm really stumped, so any help would be much appreciated.

---

### Post by gidden2 on 2013-07-31
I can send mail from local Squaremail but i cant send mail from thunderbird / other remote mail client.

in /var/log/mail.log:
Aug  1 01:41:41 mail postfix/smtpd[6729]: warning: SASL authentication failure: incorrect digest response
Aug  1 01:41:41 mail postfix/smtpd[6729]: warning: ******[***.***.***.***]: SASL CRAM-MD5 authentication failed: authentication failure
in /var/log/auth.log:
Aug  1 01:41:41 mail postfix/smtpd[6729]: sql plugin Parse the username [EMAIL="mydomain@mydomain.com"]mydomain@mydomain.com[/EMAIL]
Aug  1 01:41:41 mail postfix/smtpd[6729]: sql plugin try and connect to a host
Aug  1 01:41:41 mail postfix/smtpd[6729]: sql plugin trying to open db 'maildb' on host '127.0.0.1'
Aug  1 01:41:41 mail postfix/smtpd[6729]: begin transaction
Aug  1 01:41:41 mail postfix/smtpd[6729]: sql plugin create statement from userPassword mydomain mydomain.com
Aug  1 01:41:41 mail postfix/smtpd[6729]: sql plugin doing query select crypt from users where id='mydomain@mydomain.com' and enabled = 1;
Aug  1 01:41:41 mail postfix/smtpd[6729]: sql plugin create statement from cmusaslsecretCRAM-MD5 mydomain mydomain.com
Aug  1 01:41:41 mail postfix/smtpd[6729]: sql plugin doing query select crypt from users where id='mydomain@mydomain.com' and enabled = 1;
Aug  1 01:41:41 mail postfix/smtpd[6729]: commit transaction
Aug  1 01:41:41 mail postfix/smtpd[6729]: sql plugin Parse the username [EMAIL="mydomain@mydomain.com"]mydomain@mydomain.com[/EMAIL]
Aug  1 01:41:41 mail postfix/smtpd[6729]: sql plugin try and connect to a host
Aug  1 01:41:41 mail postfix/smtpd[6729]: sql plugin trying to open db 'maildb' on host '127.0.0.1'

cfgs:
/etc/postfix/main.cf
[http://paste.ubuntu.com/5934610/](http://paste.ubuntu.com/5934610/)
/etc/postfix/master.cf
[http://paste.ubuntu.com/5934613/](http://paste.ubuntu.com/5934613/)
/etc/postfix/sasl/smtpd.conf
[http://paste.ubuntu.com/5934617/](http://paste.ubuntu.com/5934617/)
/etc/pam.d/smtp
[http://paste.ubuntu.com/5934623/](http://paste.ubuntu.com/5934623/)
/etc/courier/imapd
[http://paste.ubuntu.com/5954496/](http://paste.ubuntu.com/5954496/)

---

### Post by m_gustafsson on 2013-08-04
gidden2,

I can send mail from RoundCube (have not tried SquirrelMail), but not from Thunderbird and I see the same in my mail.log and auth.log as you describe.
May I ask what you have set the parameter "IMAP_CAPABILITY" to in /etc/courier/imapd? Mine is set to:
```
IMAP_CAPABILITY="IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE"
```

/Mats

---

### Post by gidden2 on 2013-08-06
hi m_gustafsson,

I added full /etc/courier/imapd to my previous post. In that parameter I have this :
```
IMAP_CAPABILITY="IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA AUTH=CRAM-MD5 AUTH=CRAM-SHA1 IDLE"
```

---

### Post by m_gustafsson on 2013-08-06
gidden2,

I think I got it working on my end now and I can now send emails from both Thunderbird and my iPad via my own server.

I started out by changing my outgoing server in Thunderbird to the local IP of my mail server and tried different combinations of ports etc. When that was working I switched back to the real domain name of my server and then it just worked. Don't know if you have the same problem as I had, and if the client settings are your problem as well. 
Anyway, I ended up with the following settings in Thunderbird.
[B]
IMAP server
[/B]Port: 993
Connection security: SSL/TLS
Authentication method: Normal password

[B]SMTP server
[/B]Port: 465
Connection security: SSL/TLS
Authentication method: Normal password

I can hardly believe that it is actually working now, after weeks of work, so I guess that it will not work when I wake up tomorrow ;)

/Mats

---

### Post by chibikun on 2013-09-04
Hi there!

First of all I want to express my thanks and respect to the people that provide such great source of information and share knowledge. Kudos to flurdy! I have the set up running since 2 years perfectly.

Just recently I came across the 8 character limitation due to the encrypt() I guess. Now I want to change to stronger passwords but am not really sure what to do. I tried just to use md5() in the sql to encrypt differently but it does not seem to work in the backend (I see that the password is encrypted differently in the db though).

has anyone some hints for me? I have the super standard setup as per flurdys guide.

Thanks a lot!

David

---

### Post by alex119 on 2013-10-06
Thanks for this great tutorial: [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)
That was a big help.

Only two little things, I stumbled on when going through step by step, starting off with Bitnami Tomcat/MySQL AMI:
- "sudo adduser clamav amavis" you should not try to create the clamav user before clamAV is installed, else installation of clamAV will break. So move this one down to clamAV procedure.
- Amavis: "content_filter = amavis:[127.0.0.1]:10024" should be 10025  (or also 10024 in the master.cf)

---

### Post by ST@R*T on 2013-10-07
Thanks for this great tutorial: [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)
That really appreciate. 
I want to ask one question. I configured all configuration and testing them step by step. When i configure SASL, that's working. I can send mail and recieve mail too and i can enter too my roundcube webmail. Then next i configure TLS. I can't enter to my roundcube using my client user and password. ROundcube says "connection to imap server failed"  That is my log file 
/var/log/mail.log  
email imapd: Connection, ip=[::ffff:192.168.30.30] 
 email imapd: LOGOUT, ip=[::ffff:192.168.30.30], rcvd=14, sent=353

---

### Post by ST@R*T on 2013-10-08
Here's my netstat and iptable status
root@email:~# netstat -tap
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 *:submission            *:*                     LISTEN      1966/master
tcp        0      0 localhost:spamd         *:*                     LISTEN      1316/spamd.pid
tcp        0      0 *:http                  *:*                     LISTEN      2051/apache2
tcp        0      0 *:ssmtp                 *:*                     LISTEN      1966/master
tcp        0      0 *:ssh                   *:*                     LISTEN      651/sshd
tcp        0      0 *:smtp                  *:*                     LISTEN      1966/master
tcp        0      0 localhost:10023         *:*                     LISTEN      1301/postgrey.pid -
tcp        0      0 localhost:10024         *:*                     LISTEN      1279/amavisd (maste
tcp        0      0 localhost:10025         *:*                     LISTEN      1966/master
tcp        0      0 localhost:mysql         *:*                     LISTEN      1093/mysqld
tcp        0     52 192.168.30.30:ssh       192.168.30.31:54957     ESTABLISHED 2087/sshd: test [pr
tcp6       0      0 [::]:submission         [::]:*                  LISTEN      1966/master
tcp6       0      0 [::]:imap2              [::]:*                  LISTEN      1834/couriertcpd
tcp6       0      0 [::]:ssmtp              [::]:*                  LISTEN      1966/master
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN      651/sshd
tcp6       0      0 [::]:smtp               [::]:*                  LISTEN      1966/master
tcp6       0      0 [::]:imaps              [::]:*                  LISTEN      1862/couriertcpd




root@email:~# iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination
dynamic    all  --  anywhere             anywhere             ctstate INVALID,NEW
net2fw     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
Reject     all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere             LOG level info prefix "Shorewall:INPUT:REJECT:"
reject     all  --  anywhere             anywhere            [goto]

Chain FORWARD (policy DROP)
target     prot opt source               destination
Reject     all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere             LOG level info prefix "Shorewall:FORWARD:REJECT:"
reject     all  --  anywhere             anywhere            [goto]

Chain OUTPUT (policy DROP)
target     prot opt source               destination
fw2net     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
Reject     all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere             LOG level info prefix "Shorewall:OUTPUT:REJECT:"
reject     all  --  anywhere             anywhere            [goto]

Chain Broadcast (2 references)
target     prot opt source               destination
DROP       all  --  anywhere             anywhere             ADDRTYPE match dst-type BROADCAST
DROP       all  --  anywhere             anywhere             ADDRTYPE match dst-type MULTICAST
DROP       all  --  anywhere             anywhere             ADDRTYPE match dst-type ANYCAST
DROP       all  --  anywhere             base-address.mcast.net/4

Chain Drop (1 references)
target     prot opt source               destination
           all  --  anywhere             anywhere
reject     tcp  --  anywhere             anywhere             tcp dpt:auth /* Auth */
Broadcast  all  --  anywhere             anywhere
ACCEPT     icmp --  anywhere             anywhere             icmp fragmentation-needed /* Needed ICMP types */
ACCEPT     icmp --  anywhere             anywhere             icmp time-exceeded /* Needed ICMP types */
Invalid    all  --  anywhere             anywhere
DROP       udp  --  anywhere             anywhere             multiport dports loc-srv,microsoft-ds /* SMB */
DROP       udp  --  anywhere             anywhere             udp dpts:netbios-ns:netbios-ssn /* SMB */
DROP       udp  --  anywhere             anywhere             udp spt:netbios-ns dpts:1024:65535 /* SMB */
DROP       tcp  --  anywhere             anywhere             multiport dports loc-srv,netbios-ssn,microsoft-ds /* SMB */
DROP       udp  --  anywhere             anywhere             udp dpt:1900 /* UPnP */
NotSyn     tcp  --  anywhere             anywhere
DROP       udp  --  anywhere             anywhere             udp spt:domain /* Late DNS Replies */

Chain Invalid (2 references)
target     prot opt source               destination
DROP       all  --  anywhere             anywhere             ctstate INVALID

Chain NotSyn (2 references)
target     prot opt source               destination
DROP       tcp  --  anywhere             anywhere             tcpflags:! FIN,SYN,RST,ACK/SYN

Chain Reject (3 references)
target     prot opt source               destination
           all  --  anywhere             anywhere
reject     tcp  --  anywhere             anywhere             tcp dpt:auth /* Auth */
Broadcast  all  --  anywhere             anywhere
ACCEPT     icmp --  anywhere             anywhere             icmp fragmentation-needed /* Needed ICMP types */
ACCEPT     icmp --  anywhere             anywhere             icmp time-exceeded /* Needed ICMP types */
Invalid    all  --  anywhere             anywhere
reject     udp  --  anywhere             anywhere             multiport dports loc-srv,microsoft-ds /* SMB */
reject     udp  --  anywhere             anywhere             udp dpts:netbios-ns:netbios-ssn /* SMB */
reject     udp  --  anywhere             anywhere             udp spt:netbios-ns dpts:1024:65535 /* SMB */
reject     tcp  --  anywhere             anywhere             multiport dports loc-srv,netbios-ssn,microsoft-ds /* SMB */
DROP       udp  --  anywhere             anywhere             udp dpt:1900 /* UPnP */
NotSyn     tcp  --  anywhere             anywhere
DROP       udp  --  anywhere             anywhere             udp spt:domain /* Late DNS Replies */

Chain dynamic (3 references)
target     prot opt source               destination

Chain eth0_fwd (0 references)
target     prot opt source               destination
dynamic    all  --  anywhere             anywhere             ctstate INVALID,NEW
smurfs     all  --  anywhere             anywhere             ctstate INVALID,NEW
tcpflags   tcp  --  anywhere             anywhere

Chain fw2net (1 references)
target     prot opt source               destination
ACCEPT     udp  --  anywhere             anywhere             udp dpts:bootps:bootpc
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ACCEPT     icmp --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere

Chain logdrop (0 references)
target     prot opt source               destination
DROP       all  --  anywhere             anywhere

Chain logflags (5 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             LOG level info ip-options prefix "Shorewall:logflags:DROP:"
DROP       all  --  anywhere             anywhere

Chain logreject (0 references)
target     prot opt source               destination
reject     all  --  anywhere             anywhere

Chain net2fw (1 references)
target     prot opt source               destination
dynamic    all  --  anywhere             anywhere             ctstate INVALID,NEW
smurfs     all  --  anywhere             anywhere             ctstate INVALID,NEW
ACCEPT     udp  --  anywhere             anywhere             udp dpts:bootps:bootpc
tcpflags   tcp  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh /* SSH */
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request /* Ping */
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:smtp /* SMTP */
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssmtp /* SMTPS */
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:submission /* Submission */
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:imap2 /* IMAP */
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:imaps /* IMAPS */
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:http /* Web */
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:https /* Web */
Drop       all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere             LOG level info prefix "Shorewall:net2fw:DROP:"
DROP       all  --  anywhere             anywhere

Chain reject (10 references)
target     prot opt source               destination
DROP       all  --  anywhere             anywhere             ADDRTYPE match src-type BROADCAST
DROP       all  --  base-address.mcast.net/4  anywhere
DROP       igmp --  anywhere             anywhere
REJECT     tcp  --  anywhere             anywhere             reject-with tcp-reset
REJECT     udp  --  anywhere             anywhere             reject-with icmp-port-unreachable
REJECT     icmp --  anywhere             anywhere             reject-with icmp-host-unreachable
REJECT     all  --  anywhere             anywhere             reject-with icmp-host-prohibited

Chain shorewall (0 references)
target     prot opt source               destination

Chain smurflog (2 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere             LOG level info prefix "Shorewall:smurfs:DROP:"
DROP       all  --  anywhere             anywhere

Chain smurfs (2 references)
target     prot opt source               destination
RETURN     all  --  0.0.0.0              anywhere
smurflog   all  --  anywhere             anywhere            [goto]  ADDRTYPE match src-type BROADCAST
smurflog   all  --  base-address.mcast.net/4  anywhere            [goto]

Chain tcpflags (2 references)
target     prot opt source               destination
logflags   tcp  --  anywhere             anywhere            [goto]  tcpflags: FIN,SYN,RST,PSH,ACK,URG/FIN,PSH,URG
logflags   tcp  --  anywhere             anywhere            [goto]  tcpflags: FIN,SYN,RST,PSH,ACK,URG/NONE
logflags   tcp  --  anywhere             anywhere            [goto]  tcpflags: SYN,RST/SYN,RST
logflags   tcp  --  anywhere             anywhere            [goto]  tcpflags: FIN,SYN/FIN,SYN
logflags   tcp  --  anywhere             anywhere            [goto]  tcp spt:0flags: FIN,SYN,RST,ACK/SYN

---

### Post by oliver6 on 2013-11-11
> **m_gustafsson said:**
> gidden2,

I think I got it working on my end now and I can now send emails from both Thunderbird and my iPad via my own server.

I started out by changing my outgoing server in Thunderbird to the local IP of my mail server and tried different combinations of ports etc. When that was working I switched back to the real domain name of my server and then it just worked. Don't know if you have the same problem as I had, and if the client settings are your problem as well. 
Anyway, I ended up with the following settings in Thunderbird.
[B]
IMAP server
[/B]Port: 993
Connection security: SSL/TLS
Authentication method: Normal password

[B]SMTP server
[/B]Port: 465
Connection security: SSL/TLS
Authentication method: Normal password

I can hardly believe that it is actually working now, after weeks of work, so I guess that it will not work when I wake up tomorrow ;)

/Mats

I got thunderbird working with this settings too, but how can i get rid of the "normal password" authentication method? I strictly followed the tutorial and got the impression that it would allow me to use encrypted autentication, like CRAM-MD5 instead of "normal password". Is this assumtion correct or did i misunderstood and "normal password" is the way to go?

If it should allow to use encrypted authentication, what are the parts in the tutorial i should take a closer look? 
Btw. i added  CRAM-MD5 to the imap_capability in the /etc/courier/imapd.

I tried roundcube and even here i can only use "LOGIN" as authentication method, but the roundcube detects that there should be CRAM-MP5 availabe (probably because it is enabled in courier) but resulting in "login failed".

I even looked in the courier documentation and it says that CRAM-MD5 authentication only works with plain passwords in the database, but if i understand correctly whats described in the tutorial that there is a workaround using SASL and PAM, i did whats described in the tutorial but either i made a mistake or it did not work.

Can someone help me?

---

### Post by tehownt on 2013-11-26
First, thanks **_a lot_** for the guide, I followed it and it worked nearly flawlessly. I only had issues with **SASL** and **Roundcube** playing nice together (over TLS), which seems to be the main headache anyways :)

Maybe it's because the guide does non-TLS config first and then specifies changes to have a TLS config but since the final configuration states that the smtps/submission listener should restrict to sasl authenticated (logical) and does not allow unauthenticated local webclients by default I had to change a couple of things.

Of course, I could have just added 

```
permit_mynetworks
``` to ```
-o smtpd_client_restrictions=permit_sasl_authenticated,reject_unauth_destination,reject
``` in **/etc/postfix/master.cf** for both smtps and submission, **but** it would not have been as clean.

**Instead**, I first changed the submission to launch in chroot, since the guide does not have it chrooted. Plus submission on port 587 is much newer than smtps on port 465 and should be used for Roundcube.

In **/etc/postfix/master.cf** use the following line (remove the second 'n' from the guide).
```
submission inet n       -       -       -       -       smtpd
```

Then make sure that in **/etc/default/saslauthd** you follow the guide (The different path for the socket are described just above in the same file):
```
OPTIONS="-r -c -m /var/spool/postfix/var/run/saslauthd"
```

Then Roundcube needs to be modified in order to use submission on the correct port, and this is the big difference : **authenticate itself**.

So in **main.inc.php** (whatever your location is, if you're using Ubuntu 12.04 LTS and do not want the old 0.7.x version, you can just use a manual installation following Roundcube's own guide and point your webserver to it).
```

$rcmail_config['smtp_server'] = 'tls://localhost';
$rcmail_config['smtp_port'] = 587;
$rcmail_config['smtp_user'] = '%u';
$rcmail_config['smtp_pass'] = '%p';
$rcmail_config['smtp_auth_type'] = 'LOGIN';

```
- You must use tls:// for port 587 and ssl:// for port 465 since they are different protocols and won't work interchangeably.
- You must tell Roundcube to give login/pw info to the smtp server, otherwise it will not be authenticated and since you only allow sasl authenticated clients, it will fail.
- The only method that worked for me was "LOGIN", using CRAM-MD5 or MD5-DIGEST had the pam authentication fail (I guess maybe because it's stored in the DB as a crypt token derived directly from a plaintext and not from an MD5 digest but I might be wrong). Eventhough this is not the most secure login type since it's basically plaintext/base64, it goes through TLS (if you force submission TLS only as described in the guide) and therefore shouldn't be that much of an issue.

If anyone has a way to get any of the digest method to work, please do reply.

Also things to consider that weren't mentionned in the guide :

- Make sure** /etc/pam.d/smtp** is empty from anything else than what the guide mentions.

- You can test SASL with **testsaslauthd ** command such as
```
testsaslauthd testsaslauthd -r <DOMAIN> -u <USER_WITHOUT_@DOMAIN> -p '<CLEARTEXT_PASSWORD>' -f /var/spool/postfix/var/run/saslauthd/mux -s smtp
```
and see what goes on in sasl (/var/log/mail.log), the pam.d (/var/log/auth.log) module and mysql (/var/log/mysql/mysql.log) database getting hit with the SELECT query.

- Some options that are worth considering since they help a lot debugging postfix :
```

debug_peer_list=<IP_OF_PEER_TO_DEBUG>
debug_peer_level=3
```

One last thing concerning the guide, at one point the term 'apassword' is used for both the mail users themselves (when generating the encrypt/salted string) and the database user for the maildb (virtual hosts files etc.), it could become a bit confusing.

---

### Post by oliver6 on 2013-11-27
@tehownt
hey, could you please check if your post is related to my question i posted right above it? I am not sure if i understand what you wrote but it seems related to me. Does it solve my problem?

---

### Post by forsakenrider on 2013-11-29
This seems like the best tutorial on the net! I've been pulling my hair out for days though. Took me forever to figure out my ISP blocks port 25!

I have a service with my dynamic DNS provider that should solve just this problem, an e-mail port forwarder. I can use a different port like 2525 or 26. Im not sure how to implement this with postfix. I have tried "relayhost = waterlowphotography.com:2525" But it doesnt seem to work. Does anyone know what I should do? I have started my install fresh and am now at the first "test" point after a simple server install.

---

### Post by roberto32 on 2014-02-09
try to forward port at your router - outside 2526 WAN : inside (LAN) 25

---

### Post by roberto32 on 2014-02-09
I edited the configuration files restart postfix and this is what i get ```
Feb 09 15:26:01 linux-clui.site postfix/sendmail[30911]: fatal: chdir /var/spool/postfix : No such file or directory


``` but that directory exists maybe some permission issue? ```
ls -la /var/spool/postfix
``` ```
/var/spool/postfix:                                                                                                                                   
total 0                                                                                                                                               
drwxr-xr-x 1 root    root      166 Nov  6 16:36 .                                                                                                     
drwxr-xr-x 1 root    root      138 Jan 20 12:48 ..
drwx------ 1 postfix root        0 Oct 18 15:11 active
drwx------ 1 postfix root        0 Oct 18 15:11 bounce
drwx------ 1 postfix root        0 Oct 18 15:11 corrupt
drwx------ 1 postfix root        0 Oct 18 15:11 defer
drwx------ 1 postfix root        0 Oct 18 15:11 deferred
drwx------ 1 postfix root        0 Oct 18 15:11 flush
drwx------ 1 postfix root        0 Oct 18 15:11 hold
drwx------ 1 postfix root        0 Oct 18 15:11 incoming
drwx-wx--- 1 postfix maildrop 8000 Feb  3 16:29 maildrop
drwxr-xr-x 1 root    root        0 Jan 19 10:06 pid
drwx------ 1 postfix root      200 Jan 19 09:32 private
drwx--x--- 1 postfix maildrop   54 Jan 19 09:32 public
drwx------ 1 postfix root        0 Oct 18 15:11 saved
drwx------ 1 postfix root        0 Oct 18 15:11 trace
```   and the only variable with that value is : queue directory so it should be fine, or could it be some permission issue?

---

### Post by roberto32 on 2014-02-09
actually it was problem that I've commnet on that line, delete command and it restarted like breeze, little weird. though..

---

### Post by roberto32 on 2014-02-10
```
linux-clui:~ # ps -ef| grep "postfix"
postfix   2571 31498  0 Feb09 ?        00:00:00 pickup -l -t fifo -u
postfix   3992 31498  0 Feb09 ?        00:00:00 cleanup -z -t unix -u
postfix   4909 31498  0 Feb09 ?        00:00:00 cleanup -z -t unix -u
postfix   7578 31498  0 Feb09 ?        00:00:00 cleanup -z -t unix -u
postfix   9774 31498  0 08:17 ?        00:00:00 qmgr -l -t fifo -u
robert   30877  1678  0 Feb09 ?        00:00:07 /usr/bin/okular /var/run/media/robert/data/robert/Public/postfix_the_definitive_guide.pdf --icon okular -caption Okular                                                                                                                                     
root     31498     1  0 Feb09 ?        00:00:00 /usr/lib/postfix/master
```
```
linux-clui:~ # netstat -tupln | grep "25"
tcp        8      0 127.0.0.1:25            0.0.0.0:*               LISTEN      31498/master
```  so running as expected 
```
telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
``` but no output telnet hangs here

---

### Post by TheWayno104 on 2014-02-10
I need help everything works flawlessly apart from being able to sent email from a mail client i get relay access denied, the only way i can get it to work is if i add my ip or and external ip (if i want to access from another location), to the mynetworks in postfix/main.cf 
I started another thread before i realised this one existed. [http://ubuntuforums.org/showthread.php?t=2204556&p=12924217#post12924217](http://ubuntuforums.org/showthread.php?t=2204556&p=12924217#post12924217)

once everything is up and running smooth i will donate for your fabulous tutorial flurdy

My configs are posted in the other thread as well as the error message.

---

### Post by Pau_Peris on 2014-02-13
Hi,

i've just followed this freaking awesome HowTo [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/) and everything is working fine for the last six weeks but i also realized everyone can send emails through telnet on port 25 without the need of authenticating. Could someone explain me if that's been made on purpose?

Thanks a lot mates!

---

### Post by roberto32 on 2014-02-13
also solved that but another problem comes at the mysql - postfix "binding",  ```
/etc/postfix/mysql_mailbox.cf
``` is this ```

user=mail 
password=*mailPASSWORD* 
dbname=maildb 
table=users 
select_field=maildir 
where_field=id 
hosts=127.0.0.1 
additional_conditions = and enabled = 1  
```, so that looks like every will have same password.....???

and what's that filed crypt in users table for? like sholdn't it bee like that    
```
 AES_ENCRYPT('password_for_particular-user',SHA2('mailPASSWORD',512)) 
```so that mailPASSWORD is meant like encryption key ?

---

### Post by TheWayno104 on 2014-02-18
just a note for the people who are adding roundcube this will save you a small headache.
if roundcube cant send an email you need to do this. 

**Adding User Accounts**

[COLOR=#000000][FONT=sans-serif]**Note**: If you set $rcmail_config['smtp_user'] and $rcmail_config['smtp_pass'] to '%u' and '%p' respectively in config/main.inc.php, you **do not** have to do the following steps.[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]Unfortunately, due to how Dreamhost has its email account system set up, RoundCube will not work out-of-the-box as it usually does. We have to manually add any accounts we want to be able to log in with to the **users** table in our MySQL database. Hopefully, an Admin interface that makes this easier will be added in the future. Until then, we get to do it the old-fashioned way.[/FONT][/COLOR]

[LIST=1]
[*]Log into your database via phpMyAdmin ([http://rcdb.yourdomain.com]("http://rcdb.yourdomain.com/") in our installation example).
[*]Click on the link to the users table in the left frame after you've selected your database from the dropdown menu.
[*]Click on the "Insert" link at the top of the right frame.
[*]The only fields you need to enter information in are **username**, **mail_host**, and **alias**. Username is [EMAIL="user@domain.com"]user@domain.com[/EMAIL] (the same username this user would use for a normal email client), mail_host is mail.yourdomain.com, and alias is whatever you want the user to enter in the username field when logging into RoundCube.
[*]Hit the Go button at the bottom of the page to submit the form after you've supplied the correct information.
[*]Repeat for each user you want to have access to your RoundCube installation.
[*]Log into RoundCube and add the following folders on the options page.
[LIST]
[*]Drafts
[*]Sent
[*]Junk
[*]Trash
[/LIST]

[*]To activate mail sending, you will also need to create an identity under Personal Settings --> Identities.
[/LIST]

---

### Post by TheWayno104 on 2014-02-18
if roundcube cant log into the server you need to make these changes

$rcmail_config['imap_auth_type'] = LOGIN;
$rcmail_config['smtp_server'] = 'ssl://localhost';
$rcmail_config['default_host'] = 'ssl://localhost:993';

---

### Post by gidden2 on 2014-03-03
I found out error in my configuration:
[http://ubuntuforums.org/showthread.php?t=185913&p=12741127#post12741127](http://ubuntuforums.org/showthread.php?t=185913&p=12741127#post12741127)

It did not work because I had password to database with symbol "#".
Do not use special symbols in database password. :)

---

### Post by Lead_Magnet on 2014-03-18
I'd like to try this tutorial on a hosted server. WHile there is mention of EC2 services, there is no "recommended minimum spec" that I can find anywhere.

Can someone give me their opinion as to what physical hardware (min or recommended) this should have?

Can the tutorial be updated with this info?

Thanks :)

---

### Post by Jen_Nussbaum on 2014-03-25
I've closely followed the great instructions at flurdy.com for how to set up a mail serve.r It's been a real struggle, though most of the time the problems were because i made wrong assumptions and thus made mistakes, not because the instructions were wrong.

But I do finally have things working. My question is about how the alias tables work, and specifically, how i can get a simple user name to log in with on Roundcube, for example. Let me explain.

I have only a single domain for this mail server. I don't need to alias a bunch of domains, i just want to host @example.com. I set up my users and aliases like flurdy.com suggests, so for example i have a "users" table with one entry "jen@localhost" for myself. Then the aliases table has mail "jen@localhost" with destination "jen@localhost". (I wish this weren't necessary, but flurdy instructions show this too.) This all works just fine. The problem is that with Roundcube, for my user I have to enter "jen@localhost". I want to just enter "jen". And to be honest, I havent moved beyond this to check if it will be a problem with @example.com instead of localhost.

So I guess the simple question is, what's the right way to add users/aliases so that i can as easily as possible add new users for the username @ example.com domain, and how can they log in using just "username" instead of something longer? (I'm happy to show tables etc., but they're just as in the example docs.)

Thank you.

---

### Post by MorningWood on 2014-03-31
hmm, have an old dell laptop laying around. Will have to play with this.

---

### Post by m_gustafsson on 2014-05-01
Hi,

I have setup my mail server to use maildrop the way it was described by Villu in comment #223 in this thread, 
[http://ubuntuforums.org/showthread.php?t=185913&page=23&p=7278296#post7278296](http://ubuntuforums.org/showthread.php?t=185913&page=23&p=7278296#post7278296)
I did this on a server running Ubuntu 12.04. Now I updated the server to Ubuntu 14.04 and since then I cannot get reception of email working.
Emails are bounced with the following message:
```
 user unknown. Command output: ERR:
    authdaemon: s_connect() failed: Permission denied Invalid user specified. 
```

If I run:
```
  $ echo "test" | maildrop -V 9 -d test@myserver.netERR: authdaemon: s_connect() failed: Permission denied
Invalid user specified. 
```

And:
```
  $ sudo authtest test@myserver.net
Authentication succeeded.   
```

My mail.log:
```
   Apr 29 23:04:40 server4 postfix/pipe[15130]: D0B4DCC0E28: to=<test@myserver.net>, relay=maildrop, delay=0.08, delays=0.04/0/0/0.04, dsn=5.1.1, status=bounced (user unknown. Command output: ERR: authdaemon: s_connect() failed: Permission denied Invalid user specified. )
```

Anyone got any ideas what might be wrong?

/M

---

### Post by codyday88 on 2014-05-07
I am having troubles receiving emails. I can send though. I am Using Postfix for SMTP which works since I can send. I am using Courier for IMAP and POP3. I can connect to the server with a email client no issues, but when I sync mail with the server it reads that I have no mail. I looked in /var/spool/mail/usr and can see the emails at the bottom of the file using vim. The "mail.log" file also received the emails. I have no entries in the "mail.err" file.

I can sign into roundcube webmail also but with same problem as with the email clients.

Any ideas.

---

### Post by codyday88 on 2014-05-07
I fixed the issue. In the mail.log file is was moving to procmail due to the mail command. In the postfix main.cf I made sure "mail_command = ".

---

### Post by m_gustafsson on 2014-05-08
> **m_gustafsson said:**
> Hi,

I have setup my mail server to use maildrop the way it was described by Villu in comment #223 in this thread, 
[http://ubuntuforums.org/showthread.php?t=185913&page=23&p=7278296#post7278296](http://ubuntuforums.org/showthread.php?t=185913&page=23&p=7278296#post7278296)
I did this on a server running Ubuntu 12.04. Now I updated the server to Ubuntu 14.04 and since then I cannot get reception of email working.
Emails are bounced with the following message:
```
 user unknown. Command output: ERR:
    authdaemon: s_connect() failed: Permission denied Invalid user specified. 
```

If I run:
```
  $ echo "test" | maildrop -V 9 -d test@myserver.netERR: authdaemon: s_connect() failed: Permission denied
Invalid user specified. 
```

And:
```
  $ sudo authtest test@myserver.net
Authentication succeeded.   
```

My mail.log:
```
   Apr 29 23:04:40 server4 postfix/pipe[15130]: D0B4DCC0E28: to=<test@myserver.net>, relay=maildrop, delay=0.08, delays=0.04/0/0/0.04, dsn=5.1.1, status=bounced (user unknown. Command output: ERR: authdaemon: s_connect() failed: Permission denied Invalid user specified. )
```

Anyone got any ideas what might be wrong?

/M

I solved this by setting the sticky bit on the maildrop executable. It had been removed during the update of Ubuntu.
```
  $ sudo chmod +s /usr/bin/maildrop 
```

---

### Post by wouter6 on 2014-05-18
Hi,

i've got a problem with authenticating to imap using this tutorial. I've been stuck on it for several days now and can't seem to find an answer to my problem. I hope someone here might lead me in the right way.

authmysqlrc:
```
 
MYSQL_USERNAME mail
MYSQL_DATABASE maildb
MYSQL_USER_TABLE users
MYSQL_CRYPT_PWFIELD crypt
 MYSQL_MAILDIR_FIELD    concat(home,"/",maildir)
MYSQL_WHERE_CLAUSE enabled=1

```

mysql usertbal
```
mysql> describe users;
+-----------------+----------------------+------+-----+-------------------------                                                                                        +-------+
| Field           | Type                 | Null | Key | Default                                                                                                         | Extra |
+-----------------+----------------------+------+-----+-------------------------                                                                                        +-------+
| id              | varchar(128)         | NO   | PRI |                                                                                                                 |       |
| name            | varchar(128)         | NO   |     |                                                                                                                 |       |
| uid             | smallint(5) unsigned | NO   |     | 5000                                                                                                            |       |
| gid             | smallint(5) unsigned | NO   |     | 5000                                                                                                            |       |
| home            | varchar(255)         | NO   |     | /var/spool/mail/virtual                                                                                         |       |
| maildir         | varchar(255)         | NO   |     | blah/                                                                                                           |       |
| enabled         | tinyint(3) unsigned  | NO   |     | 1                                                                                                               |       |
| change_password | tinyint(3) unsigned  | NO   |     | 1                                                                                                               |       |
| clear           | varchar(128)         | NO   |     | ChangeMe                                                                                                        |       |
| crypt           | varchar(128)         | NO   |     | sdtrusfX0Jj66                                                                                                   |       |
| quota           | varchar(255)         | NO   |     |                                                                                                                 |       |
| procmailrc      | varchar(128)         | NO   |     |                                                                                                                 |       |
| spamassasinrc   | varchar(128)         | NO   |     |                                                                                                                 |       |
+-----------------+----------------------+------+-----+-------------------------                                                                                        +-------+
13 rows in set (0.00 sec)

```

content of table users:
```
mysql> select * from users;
+-----------------+--------+------+------+-------------------------+---------+---------+-----------------+----------+-----------------------------------------------------------------+-------+------------+---------------+
| id              | name   | uid  | gid  | home                    | maildir | enabled | change_password | clear    | crypt                                                           | quota | procmailrc | spamassasinrc |
+-----------------+--------+------+------+-------------------------+---------+---------+-----------------+----------+-----------------------------------------------------------------+-------+------------+---------------+
| admin@cmail.be  | admin  | 5000 | 5000 | /var/spool/mail/virtual | admin/  |       1 |               1 | ChangeMe | $5$00b39a2239d67d48$d.yqU1saUnXgTRgz6Xs9nEPIIhsA8VcIo2gASc4/CZ7 |       |            |               |
| root@localhost  | root   | 5000 | 5000 | /var/spool/mail/virtual | root/   |       1 |               1 | ChangeMe | $5$a2df96b36d068c35$9W6ROj17mIMEpCvJtTNHNTQYauVrCcAR7iWdOG13gw9 |       |            |               |
| test@cmail.be   | test   | 5000 | 5000 | /var/spool/mail/virtual | test/   |       1 |               1 | ChangeMe | $5$742378da04f3f6c0$i4JPAE0nmEiLm0SvZw1qrfJp0vQQo4Tu8RTk5iXo548 |       |            |               |
| wouter@cmail.be | wouter | 5000 | 5000 | /var/spool/mail/virtual | wouter/ |       1 |               1 | ChangeMe | $5$bd03e239e166bb10$9i2ggdd9/sRJU.wDmAMBr0PIesUhjFCwu.PQGOfqSS4 |       |            |               |
+-----------------+--------+------+------+-------------------------+---------+---------+-----------------+----------+-----------------------------------------------------------------+-------+------------+---------------+
4 rows in set (0.00 sec)

```

after a test in telnet syslog:
```
May 18 13:02:16 debian imapd: LOGIN FAILED, user=wouter@cmail.be, ip=[::1]
May 18 13:02:16 debian imapd: authentication error: Input/output error

```

mysql log:
```
 86 Connect   mail@localhost on
                   86 Init DB   maildb
                   86 Query     SELECT id, crypt, "", , gid, home, "", "", "", "" FROM users WHERE id = 'test@cmail.be'
                   86 Quit

```

---

### Post by anderhoff on 2014-10-03
Ubuntu 14.04 64-bit (60GB VHDD, 2x 2 Cores, 2GB, 16MB video all as a VM on WMware ESXi server)
Shorewall (4.5.21.6-1 -- I think?)

I started to going through this how-to with another distro thinking it was pretty straight forward, but I quicklky ran into hipcups not finding any available source code for several packages (i.e. PostGrey - it's just gone) and confused about other items.  Seeking a slightly easier road for success, I decided to simply do it by the book only to find versioning (directory and layout) problems.

The documentation doesn't seem to line up with with the 'apt-get install shorewall shorewall-doc' delivered goods.  
The "/default-config" folder just doesn't exist within "/usr/share/doc/shorewall", but instead I have "/examples" with sub-folders "/Universal", "/one-interface", "/two-interfaces", and "/three-interfaces". There is no example "hosts" files to work with, and I'm not keen on making one up not knowing what the format inside the file ought to be.  Some of the steps seem depreciated as Shorewall appears to prefer "Format 2" now, while the how-to appears to be using "Format 1" (the "detect" parameter tipped me off and I didn't know where to put it).  Getting web servers up is fairly easy and straight forward.

---

### Post by wantdownload on 2014-10-04
Thanks man it worked for me. I appreciate it!

---

### Post by crossRT on 2014-10-11
This tutorial is great!! So far my server is able to send and receive mail by telnet. 
But there is some problem while log in with SquirrelMail, it show "unknown user or password incorrect".
i log in with 
[FONT=courier new]username@mydomain.com
[/FONT]but it doesn't work.
 Anyone having same problem but solved can give me some clues?

---

### Post by crossRT on 2014-10-12
> **crossRT said:**
> This tutorial is great!! So far my server is able to send and receive mail by telnet. 
But there is some problem while log in with SquirrelMail, it show "unknown user or password incorrect".
i log in with 
[FONT=courier new]username@mydomain.com
[/FONT]but it doesn't work.
 Anyone having same problem but solved can give me some clues?

Sorry guys, it is work after i restart my server. Problem solved.

---

### Post by David_Goodnature on 2014-10-14
> **anderhoff said:**
> Ubuntu 14.04 64-bit (60GB VHDD, 2x 2 Cores, 2GB, 16MB video all as a VM on WMware ESXi server)
Shorewall (4.5.21.6-1 -- I think?)

I started to going through this how-to with another distro thinking it was pretty straight forward, but I quicklky ran into hipcups not finding any available source code for several packages (i.e. PostGrey - it's just gone) and confused about other items.  Seeking a slightly easier road for success, I decided to simply do it by the book only to find versioning (directory and layout) problems.

The documentation doesn't seem to line up with with the 'apt-get install shorewall shorewall-doc' delivered goods.  
The "/default-config" folder just doesn't exist within "/usr/share/doc/shorewall", but instead I have "/examples" with sub-folders "/Universal", "/one-interface", "/two-interfaces", and "/three-interfaces". There is no example "hosts" files to work with, and I'm not keen on making one up not knowing what the format inside the file ought to be.  Some of the steps seem depreciated as Shorewall appears to prefer "Format 2" now, while the how-to appears to be using "Format 1" (the "detect" parameter tipped me off and I didn't know where to put it).  Getting web servers up is fairly easy and straight forward.

Can you be more specific on how you got this to work? I've been stuck on this all morning. Thank you!

---

### Post by spraitas on 2014-11-04
I have a mail server setup and the manual by Ivar was great resource in helping me. 

But issues with the Cyrus/saslauthd service started... The service started to act weird after working for a while and i needed to restart it from time to time. This error was generated in the logs:
DEBUG: auth_pam: pam_authenticate failed: Memory buffer error

After checking some forums and documentation, I've found out that there are some configuration mistakes present in the guide:
In */etc/postfix/sasl/smtpd.conf* i had to change from:
> pwcheck_method: saslauthd
mech_list: plain login cram-md5 digest-md5
log_level: 7
allow_plaintext: true
auxprop_plugin: sql
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: mail
sql_passwd: mailPASSWORD
sql_database: maildb
sql_select: select crypt from users where id='%u@%r' and enabled = 1
to:
> 
pwcheck_method: saslauthd
mech_list: plain login

Here is the related doc that explains why the configuration of saslauthd needs only two mechanisms when pwcheck_method is saslauthd:
[http://www.postfix.org/SASL_README.html#saslauthd]("http://www.postfix.org/SASL_README.html#saslauthd")

I guess an alternative way of configuration fix would be to use:
> pwcheck_method: auxprop
But then we would need to skip the "pam" config entirely...

Also to fix the "auxpropfunc error no mechanism available" error remove the libsasl sql module:
sudo apt-get remove libsasl2-modules-sql

---

### Post by NielsNL on 2015-01-21
Just did an install on a fresh ubuntu server. Didn't totally work out as I hoped, at first there was a space after my password, my bad.
I had to configure roundcube to use a plain password, while the mySQL only has encrypted passwords in the database. The same goes for firebird/IceDove.
Also IceDove doesn't create the draft, sent etc... folders, that only happens when I log in with Roundcube.

Now I still can't send mail I get [B]SMTP Error (554): Failed to add recipient "name@domain.tld" (5.7.1 <localhost[::1]>: Client host rejected: Access denied).
[/B]When I do a telnet to port 25, I can sent mail manualy, but when I try port 587, I get that error... Kind a strange...

Maybe I am going to fix the cram-md5, or going to use a tutorial with dovecot...
I guess it didn't work because my passwords start with $5$, which is [SHA256-crypt]("http://wiki2.dovecot.org/Authentication/PasswordSchemes")...

---

