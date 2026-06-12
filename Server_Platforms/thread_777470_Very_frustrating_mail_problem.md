---
title: "Very frustrating mail problem"
date: 2008-05-01
forum: Server Platforms
---

### Post by t_ras on 2008-05-01
AMD 64, Kubuntu 7.10, Postfix 2.5.1. using ISPconfig to configure users.

I have a very annoying problem. I accidentally deleted a users home dir (through sudo...), for a user created through ISPConfig.
I wanted to recreate the user so I removed it from users\groups, but ISPConfig wouldn't let me to recreate it, claiming it already exists.
I tried recreating it through users/groups and it worked fine (but that has its own mailing issues when working with ISPConfig...). So I understood it is ISPC  problem. I created a user with a different name and then change its iname in ISPC tables, Users/groups, homedir. After getting rid of procmail and forward files created by Linux (ISPC creates its own), I managed to send mail (which actually reaches the sent mail  folder), but I can't get mail.
For other users created directly from ISPC without changes I do get mail.
Also - nothing wrong in log!
/etc/postfix/main.cf:
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

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:/var/lib/postfix/smtpd_scache
smtp_tls_session_cache_database = btree:/var/lib/postfix/smtp_scach
#smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
#smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = terrenisrv1.terrenis.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
#mydestination = terrenis.net, terrenisrv1, localhost.localdomain, localhost,mail.terrenis.net,terrenisrv1.terrenis.net
#relayhost = localhost 
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination,
# check_recipient_access hash:/etc/postfix/local-host-names
smtpd_tls_auth_only = No
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

virtual_maps = hash:/etc/postfix/virtusertable

mydestination = /etc/postfix/local-host-names

```

/etc/postfix/virtusertable:
```
###################################
#
# ISPConfig virtusertable Configuration File
#         Version 1.0
#
###################################
dbadmin@mysql.terrenis.net    dbadmin
webmaster@www.terrenis.net    webmaster
plugagimel@plugagimel.terrenis.net    plugagimel
moderator@forum.terrenis.net    moderator
pics@pics.terrenis.net    pics
shai@shai.terrenis.net    shai
blogmaster@blogs.terrenis.net    blogmaster
csight@creativesight.terrenis.net    csight
spma@softdev.terrenis.net    spma
bc_user@imtbo2008.terrenis.net    bc_user
martin@mail.terrenis.net    martin
yulia@mail.terrenis.net    yulia
postmaster@mail.terrenis.net    postmaster
#### MAKE MANUAL ENTRIES BELOW THIS LINE! ####
dbadmin@terrenis.net    dbadmin
webmaster@terrenis.net    webmaster
plugagimel@terrenis.net    plugagimel
moderator@.terrenis.net    moderator
pics@terrenis.net    pics
shai@terrenis.net    shai
blogmaster@terrenis.net    blogmaster
csight@terrenis.net    csight
spma@terrenis.net    spma
bc_user@terrenis.net    bc_user
martin@terrenis.net    martin
yulia@terrenis.net    yulia
postmaster@terrenis.net    postmaster
```

I tried reemoving the manual entries, but it didn't help.

/etc/postfix/local-host-names  :
```
###################################
#
# ISPConfig local-host-names Configuration File
#         Version 1.0
#
###################################
localhost
terrenisrv1
localhost.terrenisrv1
localhost.localdomain
mail.terrenis.net
mysql.terrenis.net
www.terrenis.net
plugagimel.terrenis.net
forum.terrenis.net
pics.terrenis.net
shai.terrenis.net
blogs.terrenis.net
creativesight.terrenis.net
softdev.terrenis.net
imtbo2008.terrenis.net
#### MAKE MANUAL ENTRIES BELOW THIS LINE! ####

```

tried also adding manually -terrenis.net.

It is very frustrating, since I'm getting no errors...

Any ideas?

---

### Post by HermanAB on 2008-05-01
Hmm, the origin of the problem is likely that the newly created user now has a different UID from the old user account.  So you can fix it by looking at the mail spool and changing the ownership of the mailbox (probably in /var/spool/mail) or by changing the UID of the user back to what it was before.

Cheers,

Herman

---

### Post by t_ras on 2008-05-01
In deed there where two boxwes there with the same owner but two diferent names. changed the owner fo one of them to something else and now ther is one box with owner "martin" and the homdir of martin where martin is owner.
I can see the mails reaching the box in /var/spool/mail, but yet they dont reach my inbox....

---

### Post by HermanAB on 2008-05-01
OK, the command 'ls -al' will show all the file attributes.

The command 'chown username:username filename' can be used to reset the ownership of the mailbox.

Look at the error logs in /var/log/mailsomethingorother to see what is going wrong with 'tail -f /var/log/mailsomethingorother', then send a message to see what errors and warnings pop up.

---

### Post by t_ras on 2008-05-02
Sadly all seems to be fine in logs (apart for Clamav being an old version)
This is what I see in log when receiving a mail:
```
05/02/2008 10:19:40 AM	terrenisrv1	postfix/smtpd[22226]	disconnect from unknown[212.143.241.131]

05/02/2008 10:19:40 AM	terrenisrv1	postfix/smtpd[22226]	connect from unknown[212.143.241.131]

05/02/2008 10:19:40 AM	terrenisrv1	postfix/smtpd[22226]	6A4EF8B7AA: client=unknown[212.143.241.131], sasl_method=PLAIN, sasl_username=martin

05/02/2008 10:19:40 AM	terrenisrv1	postfix/qmgr[30325]	6A4EF8B7AA: removed

05/02/2008 10:19:40 AM	terrenisrv1	postfix/qmgr[30325]	6A4EF8B7AA: from=<martin_t@netvision.net.il>, size=538, nrcpt=1 (queue active)

05/02/2008 10:19:40 AM	terrenisrv1	postfix/local[22231]	6A4EF8B7AA: to=<martin@terrenis.net>, relay=local, delay=0.39, delays=0.13/0.01/0/0.25, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")

05/02/2008 10:19:40 AM	terrenisrv1	postfix/cleanup[22230]	6A4EF8B7AA: message-id=<481AC08B.1010605@netvision.net.il>


```

It reaches  ls  -la /var/spool/mail/martin box
for which permissions are:
```
martint@terrenisrv1:/$ ls  -la /var/spool/mail/
total 856
drwxrwsr-x  2 root         mail   4096 2008-05-02 10:19 .
drwxr-xr-x 16 root         root   4096 2007-11-16 18:50 ..
-rw-------  1 admispconfig mail      0 2007-11-10 21:44 admispconfig
-rw-rw----  1 dbadmin      mail      0 2008-04-29 18:13 dbadmin
**-rw-rw----  1 martin       mail 615018 2008-05-02 10:19 martin**
-rw-rw----  1 root         mail   3964 2008-05-01 20:51 martin~
-rw-rw----  1 martint      mail      0 2008-05-01 20:48 martin1
-rw-rw----  1 root         mail   6816 2008-05-01 20:33 martin1~
-rw-rw----  1 martint      mail 227563 2008-04-07 23:30 martint

```

But not the Maildir for which permissions are:
```
martint@terrenisrv1:/$ sudo ls  -la /home/www/web15/user/martin/
total 132
drwxrwxr-- 5 martin     web15  4096 2008-05-01 20:38 .
drwxr-xr-x 5 postmaster web15  4096 2008-05-01 20:57 ..
-rwxrwxr-- 1 martin     web15   103 2008-05-01 19:48 .antivirus.rc
-rwxrwxr-- 1 martin     web15   779 2008-05-01 19:48 .autoresponder.rc
-rwxrwxr-- 1 martin     web15    24 2008-05-01 19:48 .forward_bkp
-rwxrwxr-- 1 martin     web15 67866 2008-05-01 19:48 .html-trap.rc
-rwxrwxr-- 1 martin     web15  3889 2008-05-01 19:48 .local-rules.rc
**drwxrwxr-- 8 martin     web15  4096 2008-05-01 19:49 Maildir**
-rwxrwxr-- 1 martin     web15   204 2008-05-01 19:48 .mailsize.rc
-rwxrwxr-- 1 martin     web15   444 2008-05-01 19:48 .procmailrc_bkp
-rwxrwxr-- 1 martin     web15   656 2008-05-01 19:48 .quota.rc
drwxrwxr-- 2 martin     web15  4096 2008-05-01 20:05 .spamassassin
-rwxrwxr-- 1 martin     web15  1145 2008-05-01 19:48 .spamassassin.rc
-rwxrwxr-- 1 martin     web15  2039 2008-05-01 19:48 .user_prefs
-rwxrwxr-- 1 martin     web15    32 2008-05-01 19:48 .vacation.msg
drwxrwxr-- 2 martin     web15  4096 2008-05-01 19:47 web

```

A tried changing owner to www-data also - no can do...

Thanks for all the help pal!

---

### Post by MJN on 2008-05-02
I haven't read the detail of this thread but try repeating the above ls tests with the -n flag in order to show numeric user/group IDs. It may be that your old 'martin' is not the same as the new 'martin' as far as the system is concerned. if you have any old files that were definitely created by the old 'martin' then check the ID of that file owner too.
 
Mathew

---

