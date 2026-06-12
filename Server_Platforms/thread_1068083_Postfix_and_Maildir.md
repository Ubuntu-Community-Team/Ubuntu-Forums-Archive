---
title: "Postfix and Maildir"
date: 2009-02-12
forum: Server Platforms
---

### Post by rompstar on 2009-02-12
I have executed this command:

sudo postconf -e 'home_mailbox = Maildir/'

to add Maildir support, then I created the directories:



then I restarted with:

sudo /etc/init.d/postfix restart

when new email is received for a user raymond, it is placed into:

/var/mail/raymond

and not

/home/raymond/Maildir

am I doing something wrong or still need to do ?

---

### Post by hyper_ch on 2009-02-12
please post your whole main.cf

and also post the Maildir directories with permissions

---

### Post by rompstar on 2009-02-12
I set it up for local delivery currently, which is what I want (I think I did it right, not sure):

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

myhostname = dragonfly.kodiaktechnical.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = dragonfly.kodiaktechnical.net, localhost.kodiaktechnical.net, localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command =
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = loopback-only
default_transport = error
relay_transport = error
home_mailbox = Maildir/
inet_protocols = all




file permissions:

raymond@dragonfly:~$ ls -ls /home/raymond/Maildir
total 108
12 drwx------ 6 raymond raymond 12288 2009-02-02 17:54 cur
 0 -rwx------ 1 raymond raymond     0 2007-10-07 13:44 draftbox
80 -rwx------ 1 raymond raymond 76800 2009-02-12 12:05 folders.db
 4 drwx------ 2 raymond raymond  4096 2009-02-01 11:36 new
 0 -rwx------ 1 raymond raymond     0 2007-10-07 13:44 outbox
 0 -rwx------ 1 raymond raymond     0 2007-10-07 13:44 sentbox
 4 drwx------ 2 raymond raymond  4096 2009-02-01 11:36 tmp
 8 -rwx------ 1 raymond raymond  4259 2007-11-10 17:27 trash

---

### Post by hyper_ch on 2009-02-12
what does maillog say? how did you create maildir?

---

### Post by rompstar on 2009-02-12
last 100 lines from mail.log

just used mkdir commands when logged under raymond user

when a user enters data through a web browser when they visit my site, so I think it is working because it says 
wwwdata, and I receive the messages sent from user filled out forms.


Feb  9 08:02:15 dragonfly postfix/local[30644]: 18B815AC354: to=<raymond@dragonfly.kodiaktechnical.net>, orig_to=<root>, relay=local, delay=0.65, delays=0.56/0.01/0/0.08, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Feb  9 08:02:15 dragonfly postfix/qmgr[5351]: 18B815AC354: removed
Feb 10 07:58:48 dragonfly postfix/pickup[13596]: 7BDFA5AC354: uid=0 from=<root>
Feb 10 07:58:48 dragonfly postfix/cleanup[23318]: 7BDFA5AC354: message-id=<20090210155848.7BDFA5AC354@dragonfly.kodiaktechnical.net>
Feb 10 07:58:48 dragonfly postfix/qmgr[5351]: 7BDFA5AC354: from=<root@dragonfly.kodiaktechnical.net>, size=553, nrcpt=1 (queue active)
Feb 10 07:58:48 dragonfly postfix/local[23320]: 7BDFA5AC354: to=<raymond@dragonfly.kodiaktechnical.net>, orig_to=<root>, relay=local, delay=0.82, delays=0.72/0.01/0/0.08, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Feb 10 07:58:48 dragonfly postfix/qmgr[5351]: 7BDFA5AC354: removed
Feb 11 08:15:21 dragonfly postfix/pickup[20721]: E53845AC28B: uid=0 from=<root>
Feb 11 08:15:21 dragonfly postfix/cleanup[21751]: E53845AC28B: message-id=<20090211161521.E53845AC28B@dragonfly.kodiaktechnical.net>
Feb 11 08:15:22 dragonfly postfix/qmgr[5351]: E53845AC28B: from=<root@dragonfly.kodiaktechnical.net>, size=553, nrcpt=1 (queue active)
Feb 11 08:15:22 dragonfly postfix/local[21753]: E53845AC28B: to=<raymond@dragonfly.kodiaktechnical.net>, orig_to=<root>, relay=local, delay=1, delays=0.9/0.01/0/0.1, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Feb 11 08:15:22 dragonfly postfix/qmgr[5351]: E53845AC28B: removed
Feb 12 08:07:39 dragonfly postfix/pickup[8288]: 738555AC202: uid=0 from=<root>
Feb 12 08:07:39 dragonfly postfix/cleanup[13887]: 738555AC202: message-id=<20090212160739.738555AC202@dragonfly.kodiaktechnical.net>
Feb 12 08:07:39 dragonfly postfix/qmgr[5351]: 738555AC202: from=<root@dragonfly.kodiaktechnical.net>, size=553, nrcpt=1 (queue active)
Feb 12 08:07:39 dragonfly postfix/local[13889]: 738555AC202: to=<raymond@dragonfly.kodiaktechnical.net>, orig_to=<root>, relay=local, delay=0.69, delays=0.61/0.01/0/0.07, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Feb 12 08:07:39 dragonfly postfix/qmgr[5351]: 738555AC202: removed
Feb 12 12:17:25 dragonfly postfix/pickup[26007]: AC9F15AC2B2: uid=33 from=<www-data>
Feb 12 12:17:25 dragonfly postfix/cleanup[18131]: AC9F15AC2B2: message-id=<20090212201725.AC9F15AC2B2@dragonfly.kodiaktechnical.net>
Feb 12 12:17:25 dragonfly postfix/qmgr[5351]: AC9F15AC2B2: from=<www-data@dragonfly.kodiaktechnical.net>, size=630, nrcpt=1 (queue active)
Feb 12 12:17:25 dragonfly postfix/local[18134]: AC9F15AC2B2: to=<raymond@localhost>, relay=local, delay=0.28, delays=0.16/0.01/0/0.11, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Feb 12 12:17:25 dragonfly postfix/qmgr[5351]: AC9F15AC2B2: removed

---

### Post by hyper_ch on 2009-02-12
why does it get delivered to procmail? you don't address procmail in your main.cf

---

### Post by rompstar on 2009-02-12
I am not sure, never used procmail, that's some kind of filtering/sorting software that works with postfix ?

I would need a little help here, not sure.

---

### Post by rompstar on 2009-02-12
I uninstalled procmail and restarted postfix and now it is deliverying to Maildir.

Later I will have to read on procmail to learn it if I decide to open the MX to the outside world.

---

### Post by hyper_ch on 2009-02-13
well, procmail can be used as local delivery filter... e.g. if you use spamassassin and if a critical amount is reached you can procmail to /dev/null the mail automatically... or make some filtering directly on the mailserver and not by the client.

but in your main.cf you did not tell procmail to do filtering and in the logs it appears... strange...

---

