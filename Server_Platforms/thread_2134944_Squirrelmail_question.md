---
title: "Squirrelmail question"
date: 2013-04-12
forum: Server Platforms
---

### Post by AvengerX9 on 2013-04-12
I have installed dovecot, postfix and squirrelmail now, but I'm unable to send or receive mail.

**Postfix main.cf file**
```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific: Specifying a file name will cause the first
# line of that file to be used as the name. The Debian default
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

myhostname = mail.truckstop24.no
mydomain = truckstop24.no
alias_maps = hash:/etc/aliases
mydestination = $mydomain, $myhostname
myorigin = $mydomain
#mynetworks = 79.161.88.0/24, 127.0.0.1/8
mynetworks = 127.0.0.0/8 79.161.88.0/32
relayhost = smtp.nenett.no
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
home_mailbox = Maildir/

# SASL SUPPORT FOR CLIENTS
# The following options set parameters needed by Postfix to enable 
# Cyrus-SASL support for authentication of mail clients. 
#smtpd_sasl_auth_enable = yes
#smtpd_sasl_security_options = noanonymous
#smtpd_sasl_local_domain = $myhostname
#broken_sasl_auth_clients = yes
#smtpd_recipient_restrictions = reject_non_fqdn_recipient, #reject_unknown_recipient_domain, permit_mynetworks, #permit_sasl_authenticated, reject_unauth_destination, #reject_non_fqdn_hostname, reject_invalid_hostname, check_helo_access, #pcre:/etc/postfix/helo_checks, check_sender_mx_access, #cidr:/etc/postfix/bogus_mx, reject_rbl_client, zen.spamhaus.org, #reject_rbl_client, cbl.abuseat.org, reject_rbl_client, dnsbl-1.uceprotect.net, #check_relay_domains permit

```

**Dovecot.conf file**
```

listen = *, ::
## Dovecot configuration file
!include_try local.conf
pop3_uidl_format = %08Xu%08Xv
protocols = imap pop3
mail_location = maildir:/home/%u/Maildir
disable_plaintext_auth = no

ssl = yes
ssl_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
ssl_key_file = /etc/ssl/private/ssl-cert-snakeoil.key

```


I'm doing *telnet localhost pop3* and *telnet localhost imap* and both are okay.

**Mail log file**
```

Apr 13 01:02:36 latonia dovecot: master: Warning: Killed with signal 15 (by pid=9217 uid=0 code=kill)
Apr 13 01:02:36 latonia dovecot: master: Dovecot v2.0.19 starting up (core dumps disabled)
Apr 13 01:02:46 latonia dovecot: imap-login: Login: user=<roger>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, mpid=9277, secured
Apr 13 01:02:46 latonia dovecot: imap(roger): Disconnected: Logged out bytes=79/681
Apr 13 01:02:48 latonia dovecot: imap-login: Login: user=<roger>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, mpid=9279, secured
Apr 13 01:02:48 latonia dovecot: imap(roger): Disconnected: Logged out bytes=79/681


```

Thanks for reading!

---

### Post by AvengerX9 on 2013-04-12
Update.

I was following a tutorial from here [https://help.ubuntu.com/community/Dovecot](https://help.ubuntu.com/community/Dovecot)

In this part I was told to chmod to 700 which didnt work so I tried 777 and that works, but am I supposed to chmod the Maildir 777 ?
```
sudo cp -r /etc/skel/Maildir /home/myuser/
sudo chown -R myuser:usergroup /home/myuser/Maildir
sudo chmod -R 700 /home/myuser/Maildir
```


**ls -alt /home/roger/Maildir**
```

total 56
drwxrwxrwx 5   700 users 4096 Apr 13 01:27 .Sent
drwxrwxrwx 9   700 users 4096 Apr 13 01:26 .
-rw-rw-rw- 1 roger roger    8 Apr 13 01:26 dovecot-uidvalidity
drwxrwxrwx 5   700 users 4096 Apr 13 01:26 .Drafts
drwxrwxrwx 5   700 users 4096 Apr 13 01:25 .Trash
-rw-rw-rw- 1 roger roger  156 Apr 13 01:25 dovecot.index.log
-rw-rw-rw- 1 roger roger   51 Apr 13 01:25 dovecot-uidlist
-rw-rw-rw- 1 roger roger   72 Apr 13 01:25 dovecot.mailbox.log
-r--r--r-- 1 roger roger    0 Apr 13 01:25 dovecot-uidvalidity.5168980a
-rw-rw-rw- 1 roger roger   18 Apr 13 01:25 subscriptions
drwxr-xr-x 5 roger roger 4096 Apr 12 23:28 ..
drwxrwxrwx 2   700 users 4096 Apr 12 23:09 cur
drwxrwxrwx 2   700 users 4096 Apr 12 23:09 new
drwxrwxrwx 5   700 users 4096 Apr 12 23:09 .Templates
drwxrwxrwx 2   700 users 4096 Apr 12 23:09 tmp


```

Now I can send emails, but I cannot receive. (first post is updated to the current settings)

---

### Post by AvengerX9 on 2013-04-14
This is the message I get in return

> 
Technical details of temporary failure:
The recipient server did not accept our requests to connect. Learn more at [http://support.google.com/mail/bin/answer.py?answer=7720](http://support.google.com/mail/bin/answer.py?answer=7720)
[(10) mail.truckstop24.no. [79.161.88.51]:25: Connection timed out]


---

### Post by AvengerX9 on 2013-04-15
I just noticed I can read my mail from webmin>servers>read user mail

That means the mail is coming through, but to the wrong mailbox. That mailbox is **/var/mail/%u** but I'm using Dovecot where the mail dir are **/home/%u/Maildir**. Is postfix main.cf the place to fix that ?

---

### Post by AvengerX9 on 2013-04-19
anyone out there ? :)

---

### Post by Vishal Agarwal on 2013-04-20
Did you configured squirrelmail ?
there also you need to configure your SMTP ports etc.

---

### Post by AvengerX9 on 2013-04-20
yeah they are set to localhost:25 for smtp and localhost:143 for the imap/dovecot and the domain is my domain


> 

SquirrelMail Configuration : Read: config.php (1.4.0)
---------------------------------------------------------
Server Settings

General
-------
1.  Domain                 : truckstop24.no
2.  Invert Time            : false
3.  Sendmail or SMTP       : SMTP

SMTP Settings
-------------
4.   SMTP Server           : mail.truckstop24.no
5.   SMTP Port             : 25
6.   POP before SMTP       : false
7.   SMTP Authentication   : none
8.   Secure SMTP (TLS)     : false
9.   Header encryption key :

A.  Update IMAP Settings   : mail.truckstop24.no:143 (dovecot)
H.  Hide SMTP Settings

R   Return to Main Menu
C   Turn color off
S   Save data
Q   Quit

Command >>



---

### Post by AvengerX9 on 2013-04-20
I changed the server settings to whats show above now and I get this when trying to access the squirrelmail

> Bad request: The IMAP server is reporting that plain text logins are disabled. Using CRAM-MD5 or DIGEST-MD5 authentication instead may work. Also, the use of TLS may allow SquirrelMail to login. Please contact your system administrator and report this error.


---

### Post by lilledavy on 2013-04-20
> **AvengerX9 said:**
> I just noticed I can read my mail from webmin>servers>read user mail

That means the mail is coming through, but to the wrong mailbox. That mailbox is **/var/mail/%u** but I'm using Dovecot where the mail dir are **/home/%u/Maildir**. Is postfix main.cf the place to fix that ?

Perhaps this page can help ("[Make Postfix talk to Dovecot]("http://workaround.org/ispmail/squeeze/postfix-dovecot")")? It describes how to create a "mail transport" specifically for Dovecot in Postfix. If you rely on the default mail delivery mechanisms the mails are placed typically in some general mailbox in the system, for example the one you noticed. If on the other hand you have defined a specific transport mechanism for the mail delivery the mails should be forwarded correctly and then visible in the imap mailer.
In the /etc/postfix/master.cf you specify the mechanism using the somewhat strange syntax for Postfix services, and in /etc/postfix/main.cf you specify that service as the "virtual_transport". (Alternatively, use the parameter "local_transport = dovecot" if the suggestion don't work.)

---

### Post by AvengerX9 on 2013-04-21
I have a  hard time to insert that 2nd line cause it generates an error in my dovecot.

> Failed to start Dovecot :
doveconf: Fatal: Error in configuration file /etc/dovecot/conf.d/10-master.conf line 113: Expecting '='

---

### Post by AvengerX9 on 2013-04-21
Its become worse now. I cant send because then squirrelmail are just loading and loading forever and I cant receive either. It became worse after I added my mailserver url to the squirrelmail-configure server settings. Its mail.truckstop24.no

---

