---
title: "Postfix Issue (I posted lots of details :)"
date: 2007-10-25
forum: Server Platforms
---

### Post by notaloafer on 2007-10-25
To start off with I followed this tutorial exactly (I hope):
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

**With the following goals:**
1) To be able to download my mail messages through POP3
2) To be able to send mail to my mail server through SMTP with TLS

To start out with **here is my main.cf file:**

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
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.notaloafer.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.notaloafer.com, BEAST, localhost.localdomain, localhost, localhost.notaloafer.com
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_auth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

```

**My problems:**
1) I fail to do a "ehlo" test to telnet mail.notaloafer.com 25
Here is what I get:
```

telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
ehlo localhost

```
Then nothing happens... it just keeps making blank spaces after I hit enter and I get no reply.
2) I cannot telnet localhost 110 (for POP3 access) (I get a "Connection refused" error) nor can I login using any remote mail software (such as Thunderbird)

I hope this is enough information for someone to assist me! I need help as soon as I can get it (I don't get email until I can get this fixed :P)

Thanks!
-Eric

---

### Post by Koybe on 2007-10-25
1) It seems postfix isn't starting well at all. Try restarting hen get more information through the logs :
```
sudo /etc/init.d/postfix restart
tail /var/log/mail.log
```

2) The howto just give you information about postfix, no pop server is installed. You should have a look to courrier for example.

---

### Post by notaloafer on 2007-10-25
Hmm I just noticed that after I did a system reboot postfix is not starting at all right now from the following error:

```

sudo /etc/init.d/postfix start
postfix: fatal: file /etc/postfix/main.cf: parameter mail_owner: unknown user name value: postfix

```

It wasn't doing that before... any ideas? Now postfix won't start at all.

-Eric

---

### Post by notaloafer on 2007-10-25
Tail also produces this response:


Oct 24 23:05:50 BEAST postfix/master[8313]: warning: process /usr/lib/postfix/smtpd pid 9766 exit status 1
Oct 24 23:05:50 BEAST postfix/master[8313]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Oct 24 23:06:50 BEAST postfix/smtpd[9767]: fatal: file /etc/postfix/main.cf: parameter mail_owner: unknown user name value: postfix
Oct 24 23:06:51 BEAST postfix/master[8313]: warning: process /usr/lib/postfix/smtpd pid 9767 exit status 1
Oct 24 23:06:51 BEAST postfix/master[8313]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Oct 24 23:06:55 BEAST postfix[9794]: fatal: file /etc/postfix/main.cf: parameter mail_owner: unknown user name value: postfix
Oct 24 23:07:06 BEAST postfix[9826]: fatal: file /etc/postfix/main.cf: parameter mail_owner: unknown user name value: postfix
Oct 24 23:07:51 BEAST postfix/smtpd[9888]: fatal: file /etc/postfix/main.cf: parameter mail_owner: unknown user name value: postfix
Oct 24 23:07:52 BEAST postfix/master[8313]: warning: process /usr/lib/postfix/smtpd pid 9888 exit status 1
Oct 24 23:07:52 BEAST postfix/master[8313]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling


-Eric

---

### Post by robert_pectol on 2007-10-25
Looks like you somehow removed the postfix user.  To verify, do this at the command prompt:
```
grep postfix /etc/passwd
```
It should return something similar to:
```
postfix:x:105:110::/var/spool/postfix:/bin/false
```
If you get nothing back, then you need to recreate the user (man adduser).

---

### Post by notaloafer on 2007-10-25
Okay I re-added the postfix user and now with tail I am getting:


Oct 24 23:44:30 BEAST postfix/master[8313]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Oct 24 23:45:30 BEAST postfix/smtpd[10694]: fatal: file /etc/postfix/main.cf: parameter mail_owner: unknown user name value: postfix
Oct 24 23:45:31 BEAST postfix/master[8313]: warning: process /usr/lib/postfix/smtpd pid 10694 exit status 1
Oct 24 23:45:31 BEAST postfix/master[8313]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Oct 24 23:46:31 BEAST postfix/smtpd[10714]: fatal: file /etc/postfix/main.cf: parameter mail_owner: unknown user name value: postfix
Oct 24 23:46:32 BEAST postfix/master[8313]: warning: process /usr/lib/postfix/smtpd pid 10714 exit status 1
Oct 24 23:46:32 BEAST postfix/master[8313]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Oct 24 23:47:13 BEAST postfix/master[8313]: terminating on signal 15
Oct 24 23:47:13 BEAST postfix/master[10883]: fatal: fifo_listen: remove public/pickup: Permission denied
Oct 24 23:47:27 BEAST postfix/master[10952]: fatal: fifo_listen: remove public/pickup: Permission denied
general-lee@BEAST:~$ sudo tail /var/log/mail.log
Oct 24 23:45:30 BEAST postfix/smtpd[10694]: fatal: file /etc/postfix/main.cf: parameter mail_owner: unknown user name value: postfix
Oct 24 23:45:31 BEAST postfix/master[8313]: warning: process /usr/lib/postfix/smtpd pid 10694 exit status 1
Oct 24 23:45:31 BEAST postfix/master[8313]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Oct 24 23:46:31 BEAST postfix/smtpd[10714]: fatal: file /etc/postfix/main.cf: parameter mail_owner: unknown user name value: postfix
Oct 24 23:46:32 BEAST postfix/master[8313]: warning: process /usr/lib/postfix/smtpd pid 10714 exit status 1
Oct 24 23:46:32 BEAST postfix/master[8313]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Oct 24 23:47:13 BEAST postfix/master[8313]: terminating on signal 15
Oct 24 23:47:13 BEAST postfix/master[10883]: fatal: fifo_listen: remove public/pickup: Permission denied
Oct 24 23:47:27 BEAST postfix/master[10952]: fatal: fifo_listen: remove public/pickup: Permission denied
Oct 24 23:48:32 BEAST postfix/master[11065]: fatal: fifo_listen: remove public/pickup: Permission denied

but now postfix starts with "OK"..

-Eric

---

### Post by notaloafer on 2007-10-25
I believe the only failure is on the "fifo_listen" because the time before that was before I fixed the postfix login..

-Eric

---

### Post by notaloafer on 2007-10-25
Sorry for 3 posts in a row but:

the grep postfix /etc/passwd is now returning:
```

postfix:x:89:123:postfix,,,,:/var/spool/postfix:/sbin/nologin

```

does that seem right?

-Eric

---

### Post by robert_pectol on 2007-10-25
> **notaloafer said:**
> Sorry for 3 posts in a row but:

the grep postfix /etc/passwd is now returning:
```

postfix:x:89:123:postfix,,,,:/var/spool/postfix:/sbin/nologin

```

does that seem right?

-Eric

Hmm... seems a little odd.  Is /sbin/nologin valid on your box?  Aside from that, it looks ok.  What do you have against, '/bin/false' for postfix's shell?  That *should* be present on your box.  Also, when you nuked the postfix user before, did you also manage to remove postfix's home directory?  In other words, did you have to re-create the home directory when you recreated the postfix user?  If so, you will probably be missing things.

---

### Post by notaloafer on 2007-10-25
Do you think I'd be better off if I just re-installed postfix? :P now that it will finally start-up I could remove it and reinstall it..

By the way /var/spool/postfix still has everything in it from the postfix install if that's what you mean. I re-created the user "postfix" and didn't specify anything special other than to add him to the postfix group. Everything went fine...

-Eric

---

### Post by robert_pectol on 2007-10-25
> **notaloafer said:**
> Do you think I'd be better off if I just re-installed postfix? :P now that it will finally start-up I could remove it and reinstall it..

-Eric

I was leaning in that direction anyway, just to save you time and frustration.  When you remove postfix, purge it completely by issuing the command:
```
sudo apt-get --purge remove --assume-yes "postfix"
```
Then, remove the /var/spool/postfix directory entirely (or just rename it to something else to get it out of the way for now).  The re-install *should* recreate/repopulate it with the appropriate directories, files, permissions, etc.  Lastly, make sure the postfix user has been removed from your system BEFORE attempting a reinstall of postfix.  Again, the reinstall will recreate the postfix user with sane options.  Once you get it reinstalled, it should behave better and you can continue from there.

---

### Post by notaloafer on 2007-10-25
Oops i posted at the same time as you... I'll just reinstall postfix :P.
-Eric

---

### Post by notaloafer on 2007-10-25
okay now this is getting a bit irritating. I followed your directions, but now this amavis program (I don't even remember installing it?) won't let me re-install postfix

Here is what I'm getting:

```

general-lee@BEAST:~$ sudo apt-get install postfix
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  postfix-mysql postfix-pgsql postfix-ldap postfix-pcre resolvconf postfix-cdb
Recommended packages:
  mail-reader
The following NEW packages will be installed:
  postfix
0 upgraded, 1 newly installed, 0 to remove and 10 not upgraded.
Need to get 0B/1092kB of archives.
After unpacking 2544kB of additional disk space will be used.
Preconfiguring packages ...
dpkg: syntax error: unknown user `amavis' in statoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)
general-lee@BEAST:~$

```

---

### Post by notaloafer on 2007-10-25
Nevermind, I found someone on the internet who had the same issue that gave me a hand.

-Eric 

Status: Installing postfix!

---

### Post by notaloafer on 2007-10-25
When following the tutorial (from my very first post) I run into a problem here:

echo 'pwcheck_method: saslauthd' >> /etc/postfix/sasl/smtpd.conf
echo 'mech_list: plain login' >> /etc/postfix/sasl/smtpd.conf

I get access denied when attempting to sudo to change those files... so I did su - root and did it directly from root... I don't know if this will cause any problems later.... just making sure I'm reporting it!

-Eric

---

### Post by notaloafer on 2007-10-25
Okay I can almost send mail now through Thunderbird, but I am still getting a "relay access denied".

Also in this part of the tutorial:
Testing

To see if SMTP-AUTH and TLS work properly now run the following command:

telnet localhost 25

After you have established the connection to your postfix mail server type

ehlo localhost

If you see the lines

250-STARTTLS
250-AUTH

among others, everything is working.

Type quit to return to the system's shell. 




I only see 250-STARTTLS and I do not see 250-AUTH... will that be a problem?

-Eric

Here is my new main.cf file:

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
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.notaloafer.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.notaloafer.com, BEAST, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom


```

---

### Post by notaloafer on 2007-10-25
Anything anybody..?

---

### Post by notaloafer on 2007-10-25
Okay so I have Thunderbird setup to Send SMTP with TLS and "use username and password".

When I attempt to send a email, I get a password box prompt but none of the users/passes on linux will allow me to authenicate to send the mail..

Any ideas?

Here's my new main.cf file:

```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

myhostname = mail.notaloafer.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.notaloafer.com, localhost.notaloafer.com, localhost
relayhost =
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject _unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtpd_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

```

---

