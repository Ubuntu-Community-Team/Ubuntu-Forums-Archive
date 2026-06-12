---
title: "PHP5 Mail()"
date: 2007-06-23
forum: Server Platforms
---

### Post by doyler78 on 2007-06-23
Originally posted in Beginner's Talk and was advised this was possibly the place to put this here.

I have MailEnable installed on windows vista ultimate pc which I use to manage mail for the 3 domains which I have purchased. I have been using it for a long time and I am familiar with reading the log files, etc. My intention is eventually to move my mail server to Ubuntu however as I have only started using linux I do not feel comfortable doing so now. Once I become more familiar with linux I will then start to think about the move. Having said that I did install postfix, courier, courier-imap, courier-imap-ssl, courier-pop, courier pop-ssl, fetchmail via guides howtoforge.net. However I haven't opened any of the ports relating to the services in firestarter and my router maps the mail ports to my Vista machine.

My Vista pc is on 10.0.0.4
My Ubuntu machine is on 10.0.0.1

My php.ini under /etc/php5/apache2/php.ini has been amended to:

```
[mail function]
; For Win32 only.
SMTP = 10.0.0.4
smtp_port = 25

; For Win32 only.
sendmail_from = [EMAIL="webmaster@mydomain.net"]webmaster@mydomain.net[/EMAIL] 
```When I run phpinfo.php on the ubuntu webserver I see the following entries:

```
SMTP               10.0.0.4
smtp_port          25
```There is also line sendmail_from: which correctly gives [EMAIL="webmaster@mydomain.net"]webmaster@mydomain.net[/EMAIL]

However there is the following entry as well:

```
sendmail_path              /usr/sbin/sendmail -t -i
```Basically I thought when I had specified the SMTP Server and port to use in the php.ini file that php scripts using mail() would use this server however they don't. They send via postfix. Anything to external addresses ie not in my static ip address gets sent however anything to mydomain.net mail accounts doesn't get delivered. I know this is because when it is trying to send it is trying to send to those addresses by using the external ip and not the internal one ie not 10.0.0.4. I can tell this by looking in Webmin at the postfix config screen in servers section which shows mail queue info. It has entries showing my messages which show connection timed out next them and my static ip address next to it rather 10.0.0.4.

I amended the hosts file to try and correct this by putting the following entries:

mail.mydomain.net        mydomain.net

If I stop postfix then no php mail gets delivered.

Other things I have tried. I can telnet 10.0.0.4 25 and get a response from my MailEnable Server.

I can telnet to mydomain.net 25 and get a response from my MailEnable Server

I can telnet to mail.mydomain.net and get a response from my MailEnable Server.

I have even allowed 10.0.0.1 relay options on my MailEnable SMTP Server but that hasn't made any difference. The reason being that at the min php isn't even trying to use MailEnable it is using postfix.

As you can probably see I am very confused. Only new to trying this stuff. Well you have to start somewhere.

---

### Post by Mr. C. on 2007-06-23
Let's make this easier for you.

First, as the comment in the php.ini says, SMTP is for Win32 only.  On *nix systems, sendmail is used by the mail command.  So, you have to properly configure postfix since that's what you have instaled.

Next, show the output of:

```
postconf -n
```

and the error messages in your mail.log and mail.err files.

MrC

---

### Post by doyler78 on 2007-06-24
Thanks Mr C for the reply. I have obviously misinterpreted what the php.ini was asking for. I took it to mean that if the mail server resides on a windows machine then provide the smtp ip and port to be used. If it resides on linux then the sendmail path. As my server resided on a windows machine I set up php.ini as such.

What I now take it to mean if I am reading your response right is that it is saying that if php is installed on a linux machine then you must provide the sendmail path and if the installation is on a windows machine then smtp details.

My problem then is that if I  have to configure php mail to send my mail through postfix then what happens in this circumstance. I have a mail address [email]webmaster@mydomain.net[/email] which the script will send from postfix. As my mail server to all external addresses is setup for MailEnable on Windows then all responses to this will be sent to Windows box. Fair enough. I can pick them up Outlook as normal. However if the address is internal ie [email]user1@mydomain.com[/email] then it isn't getting routed through my MailEnable Account and therefore I will have some mail for user1 stored on Windows and some stored on postfix. How do I get round that? Is it to use postfix as relay to my Windows Mail Server and if so how on earth do I go about that?

I have webmin installed if that makes things any easier.

OK here is the content of postconf -e (I presume it is my postfix main.cf that we are talking about as that seems to be where it seems to go)

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

myhostname = ubuntu-server.mydomain.net (***mydomain has been changed for security reasons - is correct in main.cf***)
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = ubuntu-server.mydomain.net, localhost.mydomain.net, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mailbox_command = 
inet_protocols = all
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetwork,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
home_mailbox = Maildir/
```And here is mail.log (snapshot as it is rather long - took the lastest entries)

And here is the contents mail.log

```
Jun 23 10:18:10 ubuntu-server postfix/postfix-script: warning: /var/spool/postfix/etc/hosts and /etc/hosts differ
Jun 23 10:36:11 ubuntu-server postfix/smtpd[28946]: connect from localhost.localdomain[127.0.0.1]
Jun 23 10:36:21 ubuntu-server postfix/smtpd[28946]: disconnect from localhost.localdomain[127.0.0.1]
Jun 23 12:22:28 ubuntu-server postfix/pickup[30101]: BEE16742D2: uid=33 from=<www-data>
Jun 23 12:22:28 ubuntu-server postfix/cleanup[3600]: BEE16742D2: message-id=<20070623112228.BEE16742D2@ubuntu-server.mydomain.net>
Jun 23 12:22:28 ubuntu-server postfix/qmgr[20440]: BEE16742D2: from=<www-data@ubuntu-server.mydomain.net>, size=367, nrcpt=1 (queue active)
Jun 23 12:22:59 ubuntu-server postfix/smtp[3603]: connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out (port 25)
Jun 23 12:22:59 ubuntu-server postfix/smtp[3603]: BEE16742D2: to=<somebody@mydomain.net>, relay=none, delay=31, delays=0.06/0.01/31/0, dsn=4.4.1, status=deferred (connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out)
Jun 23 12:40:36 ubuntu-server postfix/qmgr[20440]: BEE16742D2: from=<www-data@ubuntu-server.mydomain.net>, size=367, nrcpt=1 (queue active)
Jun 23 12:41:06 ubuntu-server postfix/smtp[5124]: connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out (port 25)
Jun 23 12:41:06 ubuntu-server postfix/smtp[5124]: BEE16742D2: to=<somebody@mydomain.net>, relay=none, delay=1118, delays=1088/0.01/31/0, dsn=4.4.1, status=deferred (connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out)
Jun 23 13:13:56 ubuntu-server postfix/qmgr[20440]: BEE16742D2: from=<www-data@ubuntu-server.mydomain.net>, size=367, nrcpt=1 (queue active)
Jun 23 13:14:27 ubuntu-server postfix/smtp[6097]: connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out (port 25)
Jun 23 13:14:27 ubuntu-server postfix/smtp[6097]: BEE16742D2: to=<somebody@mydomain.net>, relay=none, delay=3118, delays=3088/0.01/30/0, dsn=4.4.1, status=deferred (connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out)
Jun 23 14:20:36 ubuntu-server postfix/qmgr[20440]: BEE16742D2: from=<www-data@ubuntu-server.mydomain.net>, size=367, nrcpt=1 (queue active)
Jun 23 14:21:07 ubuntu-server postfix/smtp[7812]: connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out (port 25)
Jun 23 14:21:07 ubuntu-server postfix/smtp[7812]: BEE16742D2: to=<somebody@mydomain.net>, relay=none, delay=7118, delays=7088/0.01/30/0, dsn=4.4.1, status=deferred (connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out)
Jun 23 15:43:56 ubuntu-server postfix/qmgr[20440]: BEE16742D2: from=<www-data@ubuntu-server.mydomain.net>, size=367, nrcpt=1 (queue active)
Jun 23 15:44:27 ubuntu-server postfix/smtp[9929]: connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out (port 25)
Jun 23 15:44:27 ubuntu-server postfix/smtp[9929]: BEE16742D2: to=<somebody@mydomain.net>, relay=none, delay=12119, delays=12088/0.01/30/0, dsn=4.4.1, status=deferred (connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out)
Jun 23 17:07:16 ubuntu-server postfix/qmgr[20440]: BEE16742D2: from=<www-data@ubuntu-server.mydomain.net>, size=367, nrcpt=1 (queue active)
Jun 23 17:07:46 ubuntu-server postfix/smtp[12664]: connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out (port 25)
Jun 23 17:07:46 ubuntu-server postfix/smtp[12664]: BEE16742D2: to=<somebody@mydomain.net>, relay=none, delay=17118, delays=17087/0.01/30/0, dsn=4.4.1, status=deferred (connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out)
Jun 23 18:30:36 ubuntu-server postfix/qmgr[20440]: BEE16742D2: from=<www-data@ubuntu-server.mydomain.net>, size=367, nrcpt=1 (queue active)
Jun 23 18:31:06 ubuntu-server postfix/smtp[14786]: connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out (port 25)
Jun 23 18:31:06 ubuntu-server postfix/smtp[14786]: BEE16742D2: to=<somebody@mydomain.net>, relay=none, delay=22118, delays=22087/0.01/30/0, dsn=4.4.1, status=deferred (connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out)
Jun 23 19:53:56 ubuntu-server postfix/qmgr[20440]: BEE16742D2: from=<www-data@ubuntu-server.mydomain.net>, size=367, nrcpt=1 (queue active)
Jun 23 19:54:26 ubuntu-server postfix/smtp[17635]: connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out (port 25)
Jun 23 19:54:26 ubuntu-server postfix/smtp[17635]: BEE16742D2: to=<somebody@mydomain.net>, relay=none, delay=27118, delays=27088/0.02/30/0, dsn=4.4.1, status=deferred (connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out)
Jun 23 21:17:16 ubuntu-server postfix/qmgr[20440]: BEE16742D2: from=<www-data@ubuntu-server.mydomain.net>, size=367, nrcpt=1 (queue active)
Jun 23 21:17:46 ubuntu-server postfix/smtp[19725]: connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out (port 25)
Jun 23 21:17:46 ubuntu-server postfix/smtp[19725]: BEE16742D2: to=<somebody@mydomain.net>, relay=none, delay=32118, delays=32088/0.01/30/0, dsn=4.4.1, status=deferred (connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out)
Jun 23 22:40:36 ubuntu-server postfix/qmgr[20440]: BEE16742D2: from=<www-data@ubuntu-server.mydomain.net>, size=367, nrcpt=1 (queue active)
Jun 23 22:41:06 ubuntu-server postfix/smtp[21797]: connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out (port 25)
Jun 23 22:41:06 ubuntu-server postfix/smtp[21797]: BEE16742D2: to=<somebody@mydomain.net>, relay=none, delay=37118, delays=37088/0.01/30/0, dsn=4.4.1, status=deferred (connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out)
Jun 24 00:03:56 ubuntu-server postfix/qmgr[20440]: BEE16742D2: from=<www-data@ubuntu-server.mydomain.net>, size=367, nrcpt=1 (queue active)
Jun 24 00:04:27 ubuntu-server postfix/smtp[23872]: connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out (port 25)
Jun 24 00:04:27 ubuntu-server postfix/smtp[23872]: BEE16742D2: to=<somebody@mydomain.net>, relay=none, delay=42118, delays=42088/0.01/31/0, dsn=4.4.1, status=deferred (connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out)
Jun 24 01:27:16 ubuntu-server postfix/qmgr[20440]: BEE16742D2: from=<www-data@ubuntu-server.mydomain.net>, size=367, nrcpt=1 (queue active)
Jun 24 01:27:47 ubuntu-server postfix/smtp[25945]: connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out (port 25)
Jun 24 01:27:47 ubuntu-server postfix/smtp[25945]: BEE16742D2: to=<somebody@mydomain.net>, relay=none, delay=47118, delays=47088/0.01/30/0, dsn=4.4.1, status=deferred (connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out)
Jun 24 02:50:36 ubuntu-server postfix/qmgr[20440]: BEE16742D2: from=<www-data@ubuntu-server.mydomain.net>, size=367, nrcpt=1 (queue active)
Jun 24 02:51:07 ubuntu-server postfix/smtp[28007]: connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out (port 25)
Jun 24 02:51:07 ubuntu-server postfix/smtp[28007]: BEE16742D2: to=<somebody@mydomain.net>, relay=none, delay=52119, delays=52088/0.01/31/0, dsn=4.4.1, status=deferred (connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out)
Jun 24 04:13:56 ubuntu-server postfix/qmgr[20440]: BEE16742D2: from=<www-data@ubuntu-server.mydomain.net>, size=367, nrcpt=1 (queue active)
Jun 24 04:14:26 ubuntu-server postfix/smtp[30089]: connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out (port 25)
Jun 24 04:14:26 ubuntu-server postfix/smtp[30089]: BEE16742D2: to=<somebody@mydomain.net>, relay=none, delay=57118, delays=57088/0.01/30/0, dsn=4.4.1, status=deferred (connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out)
Jun 24 05:37:16 ubuntu-server postfix/qmgr[20440]: BEE16742D2: from=<www-data@ubuntu-server.mydomain.net>, size=367, nrcpt=1 (queue active)
Jun 24 05:37:46 ubuntu-server postfix/smtp[32147]: connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out (port 25)
Jun 24 05:37:46 ubuntu-server postfix/smtp[32147]: BEE16742D2: to=<somebody@mydomain.net>, relay=none, delay=62118, delays=62088/0.01/30/0, dsn=4.4.1, status=deferred (connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out)
Jun 24 07:00:36 ubuntu-server postfix/qmgr[20440]: BEE16742D2: from=<www-data@ubuntu-server.mydomain.net>, size=367, nrcpt=1 (queue active)
Jun 24 07:01:07 ubuntu-server postfix/smtp[1734]: connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out (port 25)
Jun 24 07:01:07 ubuntu-server postfix/smtp[1734]: BEE16742D2: to=<somebody@mydomain.net>, relay=none, delay=67118, delays=67088/0.02/31/0, dsn=4.4.1, status=deferred (connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out)
Jun 24 08:23:56 ubuntu-server postfix/qmgr[20440]: BEE16742D2: from=<www-data@ubuntu-server.mydomain.net>, size=367, nrcpt=1 (queue active)
Jun 24 08:24:27 ubuntu-server postfix/smtp[4160]: connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out (port 25)
Jun 24 08:24:27 ubuntu-server postfix/smtp[4160]: BEE16742D2: to=<somebody@mydomain.net>, relay=none, delay=72119, delays=72088/0.2/30/0, dsn=4.4.1, status=deferred (connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out)
Jun 24 09:47:16 ubuntu-server postfix/qmgr[20440]: BEE16742D2: from=<www-data@ubuntu-server.mydomain.net>, size=367, nrcpt=1 (queue active)
Jun 24 09:47:46 ubuntu-server postfix/smtp[6312]: connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out (port 25)
Jun 24 09:47:46 ubuntu-server postfix/smtp[6312]: BEE16742D2: to=<somebody@mydomain.net>, relay=none, delay=77118, delays=77087/0.01/30/0, dsn=4.4.1, status=deferred (connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out)
Jun 24 11:10:36 ubuntu-server postfix/qmgr[20440]: BEE16742D2: from=<www-data@ubuntu-server.mydomain.net>, size=367, nrcpt=1 (queue active)
Jun 24 11:11:06 ubuntu-server postfix/smtp[8382]: connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out (port 25)
Jun 24 11:11:06 ubuntu-server postfix/smtp[8382]: BEE16742D2: to=<somebody@mydomain.net>, relay=none, delay=82118, delays=82088/0.01/30/0, dsn=4.4.1, status=deferred (connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out)
Jun 24 12:10:17 ubuntu-server postfix/postfix-script: warning: /var/spool/postfix/etc/hosts and /etc/hosts differ
Jun 24 12:11:46 ubuntu-server postfix/postfix-script: warning: /var/spool/postfix/etc/hosts and /etc/hosts differ
Jun 24 12:12:17 ubuntu-server postfix/postfix-script: warning: /var/spool/postfix/etc/hosts and /etc/hosts differ
Jun 24 12:17:04 ubuntu-server postfix/pickup[9572]: 27B43742DA: uid=33 from=<www-data>
Jun 24 12:17:04 ubuntu-server postfix/cleanup[10583]: 27B43742DA: message-id=<20070624111704.27B43742DA@ubuntu-server.mydomain.net>
Jun 24 12:17:04 ubuntu-server postfix/qmgr[20440]: 27B43742DA: from=<www-data@ubuntu-server.mydomain.net>, size=367, nrcpt=1 (queue active)
Jun 24 12:17:34 ubuntu-server postfix/smtp[10585]: connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out (port 25)
Jun 24 12:17:34 ubuntu-server postfix/smtp[10585]: 27B43742DA: to=<somebody@mydomain.net>, relay=none, delay=31, delays=0.52/0.01/31/0, dsn=4.4.1, status=deferred (connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out)
Jun 24 12:21:08 ubuntu-server postfix/postfix-script: warning: /var/spool/postfix/etc/hosts and /etc/hosts differ
Jun 24 12:21:31 ubuntu-server postfix/postfix-script: warning: /var/spool/postfix/etc/hosts and /etc/hosts differ
Jun 24 12:21:56 ubuntu-server postfix/postfix-script: warning: /var/spool/postfix/etc/hosts and /etc/hosts differ
Jun 24 12:23:41 ubuntu-server postfix/master[20420]: reload configuration /etc/postfix
Jun 24 12:23:41 ubuntu-server postfix/qmgr[11067]: BEE16742D2: from=<www-data@ubuntu-server.mydomain.net>, size=367, nrcpt=1 (queue active)
Jun 24 12:23:41 ubuntu-server postfix/smtp[11071]: BEE16742D2: to=<somebody@mydomain.net>, relay=none, delay=86473, delays=86472/0.21/0/0, dsn=4.4.3, status=deferred (Host or domain name not found. Name service error for name=mydomain.net type=MX: Host not found, try again)
Jun 24 12:23:50 ubuntu-server postfix/master[20420]: reload configuration /etc/postfix
Jun 24 12:23:50 ubuntu-server postfix/qmgr[11145]: 27B43742DA: from=<www-data@ubuntu-server.mydomain.net>, size=367, nrcpt=1 (queue active)
Jun 24 12:23:50 ubuntu-server postfix/qmgr[11145]: BEE16742D2: from=<www-data@ubuntu-server.mydomain.net>, size=367, nrcpt=1 (queue active)
Jun 24 12:24:21 ubuntu-server postfix/smtp[11151]: connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out (port 25)
Jun 24 12:24:21 ubuntu-server postfix/smtp[11159]: connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out (port 25)
Jun 24 12:24:21 ubuntu-server postfix/smtp[11151]: 27B43742DA: to=<somebody@mydomain.net>, relay=none, delay=437, delays=407/0.23/30/0, dsn=4.4.1, status=deferred (connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out)
Jun 24 12:24:21 ubuntu-server postfix/smtp[11159]: BEE16742D2: to=<somebody@mydomain.net>, relay=none, delay=86512, delays=86482/0.15/30/0, dsn=4.4.1, status=deferred (connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out)
Jun 24 12:24:36 ubuntu-server postfix/master[20420]: reload configuration /etc/postfix
Jun 24 12:24:38 ubuntu-server postfix/master[20420]: reload configuration /etc/postfix
Jun 24 12:24:38 ubuntu-server postfix/qmgr[11285]: 27B43742DA: from=<www-data@ubuntu-server.mydomain.net>, size=367, nrcpt=1 (queue active)
Jun 24 12:24:38 ubuntu-server postfix/qmgr[11285]: BEE16742D2: from=<www-data@ubuntu-server.mydomain.net>, size=367, nrcpt=1 (queue active)
Jun 24 12:24:49 ubuntu-server postfix/pickup[11284]: CF1B1742DC: uid=33 from=<www-data>
Jun 24 12:24:49 ubuntu-server postfix/cleanup[11307]: CF1B1742DC: message-id=<20070624112449.CF1B1742DC@ubuntu-server.mydomain.net>
Jun 24 12:24:50 ubuntu-server postfix/qmgr[11285]: CF1B1742DC: from=<www-data@ubuntu-server.mydomain.net>, size=367, nrcpt=1 (queue active)
Jun 24 12:25:03 ubuntu-server postfix/postfix-script: warning: /var/spool/postfix/etc/hosts and /etc/hosts differ
Jun 24 12:25:09 ubuntu-server postfix/smtp[11291]: connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out (port 25)
Jun 24 12:25:09 ubuntu-server postfix/smtp[11299]: connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out (port 25)
Jun 24 12:25:09 ubuntu-server postfix/smtp[11291]: 27B43742DA: to=<somebody@mydomain.net>, relay=none, delay=486, delays=455/0.08/30/0, dsn=4.4.1, status=deferred (connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out)
Jun 24 12:25:09 ubuntu-server postfix/smtp[11299]: BEE16742D2: to=<somebody@mydomain.net>, relay=none, delay=86560, delays=86530/0.06/30/0, dsn=4.4.1, status=deferred (connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out)
Jun 24 12:25:20 ubuntu-server postfix/smtp[11308]: connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out (port 25)
Jun 24 12:25:20 ubuntu-server postfix/smtp[11308]: CF1B1742DC: to=<somebody@mydomain.net>, relay=none, delay=31, delays=0.38/0.01/30/0, dsn=4.4.1, status=deferred (connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out)
Jun 24 12:25:22 ubuntu-server postfix/postsuper[11410]: 27B43742DA: requeued
Jun 24 12:25:22 ubuntu-server postfix/postsuper[11410]: Requeued: 1 message
Jun 24 12:25:22 ubuntu-server postfix/postsuper[11411]: BEE16742D2: requeued
Jun 24 12:25:22 ubuntu-server postfix/postsuper[11411]: Requeued: 1 message
Jun 24 12:25:22 ubuntu-server postfix/postsuper[11412]: CF1B1742DC: requeued
Jun 24 12:25:22 ubuntu-server postfix/postsuper[11412]: Requeued: 1 message
Jun 24 12:25:34 ubuntu-server postfix/postfix-script: warning: /var/spool/postfix/etc/hosts and /etc/hosts differ
Jun 24 12:25:38 ubuntu-server postfix/pickup[11284]: 402D2742DD: uid=108 from=<www-data@ubuntu-server.mydomain.net> orig_id=BEE16742D2
Jun 24 12:25:38 ubuntu-server postfix/cleanup[11307]: 402D2742DD: message-id=<20070623112228.BEE16742D2@ubuntu-server.mydomain.net>
Jun 24 12:25:38 ubuntu-server postfix/qmgr[11285]: 402D2742DD: from=<www-data@ubuntu-server.mydomain.net>, size=494, nrcpt=1 (queue active)
Jun 24 12:25:38 ubuntu-server postfix/pickup[11284]: 4F8D2742D2: uid=108 from=<www-data@ubuntu-server.mydomain.net> orig_id=CF1B1742DC
Jun 24 12:25:38 ubuntu-server postfix/cleanup[11307]: 4F8D2742D2: message-id=<20070624112449.CF1B1742DC@ubuntu-server.mydomain.net>
Jun 24 12:25:38 ubuntu-server postfix/qmgr[11285]: 4F8D2742D2: from=<www-data@ubuntu-server.mydomain.net>, size=494, nrcpt=1 (queue active)
Jun 24 12:25:38 ubuntu-server postfix/pickup[11284]: 50786742DC: uid=108 from=<www-data@ubuntu-server.mydomain.net> orig_id=27B43742DA
Jun 24 12:25:38 ubuntu-server postfix/cleanup[11307]: 50786742DC: message-id=<20070624111704.27B43742DA@ubuntu-server.mydomain.net>
Jun 24 12:25:38 ubuntu-server postfix/qmgr[11285]: 50786742DC: from=<www-data@ubuntu-server.mydomain.net>, size=494, nrcpt=1 (queue active)
Jun 24 12:26:08 ubuntu-server postfix/smtp[11291]: connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out (port 25)
Jun 24 12:26:08 ubuntu-server postfix/smtp[11299]: connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out (port 25)
Jun 24 12:26:08 ubuntu-server postfix/smtp[11308]: connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out (port 25)
Jun 24 12:26:08 ubuntu-server postfix/smtp[11308]: 50786742DC: to=<somebody@mydomain.net>, relay=none, delay=545, delays=515/0/30/0, dsn=4.4.1, status=deferred (connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out)
Jun 24 12:26:08 ubuntu-server postfix/smtp[11299]: 4F8D2742D2: to=<somebody@mydomain.net>, relay=none, delay=79, delays=49/0/30/0, dsn=4.4.1, status=deferred (connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out)
Jun 24 12:26:08 ubuntu-server postfix/smtp[11291]: 402D2742DD: to=<somebody@mydomain.net>, relay=none, delay=86620, delays=86590/0/30/0, dsn=4.4.1, status=deferred (connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out)
```

there is nothing in the mail.err file so haven't posted here.

---

### Post by Mr. C. on 2007-06-24
php on your linux machine will use the local sendmail binary (which on your system is postfix's).  You can see in your logs that email is being dropped via sendmail (postfix/pickup lines):

```
Jun 24 12:25:38 ubuntu-server postfix/pickup[11284]: 402D2742DD: uid=108 from=<www-data@ubuntu-server.mydomain.net> orig_id=BEE16742D2
```

Next you see that postfix cannot reach your mail.mydomain.net server, and it times out:
```
Jun 24 12:26:08 ubuntu-server postfix/smtp[11291]: connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out (port 25)
```

If I understand you correctly, you desire to have all mail relayed to your MailEnable system.  In that case, you need to figure out why postfix (or your Ubuntu machine in general) cannot connect to your mail.mydomain.net system on port 25. Firewall ?

I see from this:
```
Jun 24 12:25:34 ubuntu-server postfix/postfix-script: warning: /var/spool/postfix/etc/hosts and /etc/hosts differ
```
that your postfix is running chroot'd. Be sure that the correct files are being modified if you make modifications manually.  You mention below that you modified the hosts file.  Did you also modify the one listed above in the chroot directory?  Otherwise, postfix won't be able to translate the name mail.mydomain.net.

MrC

---

### Post by doyler78 on 2007-06-24
> you need to figure out why postfix (or your Ubuntu machine in general) cannot connect to your mail.mydomain.net system on port 25. Firewall ?```
eamonn@ubuntu-server:~$ telnet mail.mydomain.net 25
Trying 10.0.0.4...
Connected to mail.mydomain.net.
Escape character is '^]'.
220 mydomain.net ESMTP MailEnable Service, Version: 1.981-- ready at 06/24/07 18:51:32

```As you can see from the terminal output I have copied I can telnet to port 25 using my domain name therefore if it isn't getting through it must be a postfix problem and the reason for that would seem to be because it is trying to resolve mail.mydomain.net to my external ip address and not my internal address and therefore it will never resolve hence the connection time out and this would be indicated by the message given in the mail log which you quoted:

```
Jun 24 12:25:34 ubuntu-server postfix/postfix-script: warning: /var/spool/postfix/etc/hosts and /etc/hosts differ
```

Here is a copy of my /var/spool/postfix/etc/hosts file:

```
127.0.0.1 localhost.localdomain localhost
10.0.0.1 ubuntu-server.mydomain.net ubuntu-server

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
10.0.0.4 mail.mydomain.net mydomain.net mail
```

And here is my /etc/hosts file:

```
127.0.0.1 localhost.localdomain localhost
10.0.0.1 ubuntu-server.mydomain.net ubuntu-server

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
10.0.0.4 mail.mydomain.net mydomain.net mail
```

Now I can't see any differences there so not quite sure why this message about them being different appears in my mail.log.

> If I understand you correctly, you desire to have all mail relayed to your MailEnable system

I really don't care so long as I can access all of my emails from Outlook as this is where all my emails are downloaded. To me it would just seem easier to relay them from postfix to my MailEnable and let MailEnable deal with all my emails instead of having two different emails processing and then having to gather my emails from two different places instead of the one. I don't know if that makes sense.

---

### Post by Mr. C. on 2007-06-24
I note that you did not obfuscates your mai system's IP 10.0.0.4, but did in the postfix connection logs.  Is postfix trying to connect to the MailEnable system via WAN IP ?

MrC

---

### Post by doyler78 on 2007-06-25
Yes

```
Jun 23 14:21:07 ubuntu-server postfix/smtp[7812]: connect to mail.mydomain.net[xxx.xxx.xxx.xxx]: Connection timed out (port 25)
```

The address that it is trying to send to (the xxx.xxx.xxx.xxx) is my public outward facing ip hence the reason why I have hidden this however as I have set both mail.mydomain.net up in my postfix and network hosts files to resolve to 10.0.0.4 I am confused as to why it is trying to send via my public ip. Is there something I am missing in getting to send via 10.0.0.4?

E

---

### Post by Mr. C. on 2007-06-25
In a chrooted environment, you have to make sure all your configurations are correct.

What's in your files:

> /var/spool/postfix/etc/resolv.conf
/var/spool/postfix/etc/nsswitch.conf

Consider postconf(5)'s man page entry:

> disable_dns_lookups (default: no)
       Disable  DNS  lookups  in  the Postfix SMTP and LMTP clients. When dis-
       abled, hosts are looked up with the getaddrinfo() system  library  rou-
       tine which normally also looks in /etc/hosts.

       DNS lookups are enabled by default.

MrC

---

### Post by doyler78 on 2007-06-25
Ok Mr C here is the contents of my rsolv.conf:

```
nameserver 212.159.13.49
nameserver 212.159.13.50
nameserver 212.159.6.9
nameserver 212.159.6.10
```These are my isps name servers who provide my static ip.

and nsswitch.conf

```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```Ok that says nothing to me - hope it makes sense to you.

---

### Post by doyler78 on 2007-06-25
As per the suggestion in the postfix man I have disabled dns lookup in main.cf

disable_dns_lookups = yes

[FONT=Tahoma,Sans,Arial,Helvetica,sans-serif]however this means that mail is no longer delivered to external accounts such my yahoo email account - tested it on three different external accounts (yahoo, googlemail & hotmail) and they all time out. I removed disable dns lookups, restarted Postfix and flushed the mail queue and all the messages were then sent.

Therefore doing that just substitutes one problem with another.](*,)
[/FONT]

---

### Post by Mr. C. on 2007-06-25
You're missing the point.

Disabling DNS lookup showed you *why* your var/spool/postfix/etc/hosts file was *not* consulted.

If you want your internal email to be forwarded to your MailEnable station, setup relay_host or use a transport map to forward all mail to that server, and use the no MX lookup syntax:

You have to decide which mail station is the *final destination* for your email for your domain.  Currently, you have your postfix as the final destination for.

You can set relayhost in main.cf as follows (this syntax will disable DNS MX lookups for that host):

relayhost = [10.0.0.4]

postfix reload as usual.

MrC

---

### Post by doyler78 on 2007-06-25
All sorted. I just set postfix to relay the mail to MailEnable and all works. I have checked my MailEnable setup to ensure that I didn't leave my mail system open as an open relay and all test came back without problems so very happy now.

Coming from windows where host files are checked first then dns records I expected the same in linux and that was what causing my confusion. Silly perhaps but a lesson learned nonetheless.

Anyway thanks MrC for all the hand holding.

Next problem to try and reverse engineer a mysql database on ubuntu using Microsoft Visio - should be fun :)

---

### Post by Mr. C. on 2007-06-25
You're welcome.

Linux/Unix *do* use the host lookup order specified in /etc/nsswitch.conf, and by default this is /etc/hosts (files) and DNS.  You'll note that in your nsswitch.conf file.

It is *postfix* that uses DNS strictly, unless otherwise told.  It needs to, as MX records are not available in the hosts files, and when an MX record does not exist, it falls back to A records.  Unless it performs DNS lookups, it cannot follow this strategy.

MrC

---

### Post by doyler78 on 2007-06-25
Ah that does indeed make perfect sense that mail servers need to check for specific mail records and the fact that they aren't a part of a host file means that their first point of reference should really be the dns records for the domain. That nsswitch.conf file still makes no sense whatsoever but I will google that as it has me curious now has to how you read it. Thanks again.

---

### Post by Mr. C. on 2007-06-25
Its a multi table switch file

man nsswitch.conf

will explain.

MrC

---

