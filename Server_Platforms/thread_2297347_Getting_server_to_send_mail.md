---
title: "Getting server to send mail"
date: 2015-10-02
forum: Server Platforms
---

### Post by micahpage on 2015-10-02
I have an ubuntu server that i am trying to get to send email activations for WordPress. How would i go about doing it properly?

I did this tutorial
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

and when i do telnet localhost 25 i get this

```
metulburr ~ $ telnet localhost 25Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 python-gaming ESMTP Sendmail 8.14.4/8.14.4/Debian-4.1ubuntu1; Fri, 2 Oct 2015 23:26:58 -0400; (No UCE/UBE) logging access from: localhost(OK)-localhost [127.0.0.1]


500 5.5.1 Command unrecognized: ""
ehlo localhost


250-python-gaming Hello localhost [127.0.0.1], pleased to meet you
250-ENHANCEDSTATUSCODES
250-PIPELINING
250-EXPN
250-VERB
250-8BITMIME
250-SIZE
250-DSN
250-ETRN
250-AUTH DIGEST-MD5 CRAM-MD5
250-DELIVERBY
250 HELP
500 5.5.1 Command unrecognized: ""
quit
221 2.0.0 python-gaming closing connection
Connection closed by foreign host.



```
which supposedly means that its working. However user logins are not getting emails. What am i doing wrong?

the site is 
[http://python-gaming.com/blog/wordpress/](http://python-gaming.com/blog/wordpress/)
if you register for the blog, you will never get an email.




then i tried setting up smpt via this link
[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-postfix-as-a-send-only-smtp-server-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-postfix-as-a-send-only-smtp-server-on-ubuntu-14-04)
however when i run the test i get that mail did not send
```
$ echo "This is the body of the email" | mail -s "This is the subject line" metulburr@gmail.com

mail: cannot send message: Process exited with a non-zero status



```

---

### Post by SeijiSensei on 2015-10-03
Many providers block outbound connections to port 25 on remote servers as an anti-spam measure.  Try
```
telnet gmail-smtp-in.l.google.com 25
```
Does that connect?

---

### Post by micahpage on 2015-10-03
```
metulburr /var/www/html $ telnet gmail-smtp-in.l.google.com 25Trying 64.233.171.26...
Connected to gmail-smtp-in.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP c73si14410021qka.13 - gsmtp
ehlo localhost
250-mx.google.com at your service, [198.199.80.192]
250-SIZE 35882577
250-8BITMIME
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-PIPELINING
250-CHUNKING
250 SMTPUTF8

```

Does that mean it connected?

---

### Post by SeijiSensei on 2015-10-03
Yup.  That's not the problem.

What do you see in /var/log/mail.log when you run your tests?

---

### Post by micahpage on 2015-10-03
```
metulburr /var/www/html $ sudo tail -f /var/log/mail.log
Oct  3 00:05:20 python-gaming postfix/sendmail[4430]: warning: valid_hostname: invalid character 64(decimal): metulburr@python-gaming.com
Oct  3 00:05:20 python-gaming postfix/sendmail[4430]: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: metulburr@python-gaming.com
Oct  3 00:05:21 python-gaming postfix/sendmail[4476]: warning: valid_hostname: invalid character 64(decimal): metulburr@python-gaming.com
Oct  3 00:05:21 python-gaming postfix/sendmail[4476]: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: metulburr@python-gaming.com
Oct  3 00:05:21 python-gaming postfix/sendmail[4483]: warning: valid_hostname: invalid character 64(decimal): metulburr@python-gaming.com
Oct  3 00:05:21 python-gaming postfix/sendmail[4483]: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: metulburr@python-gaming.com
Oct  3 00:05:21 python-gaming postfix/sendmail[4497]: warning: valid_hostname: invalid character 64(decimal): metulburr@python-gaming.com
Oct  3 00:05:21 python-gaming postfix/sendmail[4497]: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: metulburr@python-gaming.com
Oct  3 00:20:03 python-gaming postmulti[7587]: warning: valid_hostname: invalid character 64(decimal): metulburr@python-gaming.com
Oct  3 00:20:03 python-gaming postmulti[7587]: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: metulburr@python-gaming.com



```

 /etc/postfix/main.cf
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
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache


# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.


smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = metulburr@python-gaming.com
#alias_maps = hash:/etc/aliases
virtual_alias_maps = hash:/etc/postfix/virtual
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = python-gaming.com, python-gaming, localhost.localdomain, localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command =
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = localhost
inet_protocols = all
home_mailbox = Maildir/
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom




```
what is myhostname suppose to be?


but to be honest i am not exactly sure how to even test this

i tried
```
metulburr /var/www/html $ sudo echo "Subject: test" | /usr/lib/sendmail -v metulburr@gmail.com
ignoring system configuration file /etc/msmtprc: Permission denied
ignoring user configuration file /home/metulburr/.msmtprc: No such file or directory
falling back to default account
sendmail: account default not found: no configuration file available



```
EDIT:
oh wait i had to do that via root

```
root /home/metulburr # echo "Subject: test" | /usr/lib/sendmail -v metulburr@gmail.com > output.txt
sendmail: authentication failed (method PLAIN)
sendmail: server message: 535-5.7.8 Username and Password not accepted. Learn more at
sendmail: server message: 535 5.7.8  https://support.google.com/mail/answer/14257 f105sm7128272qgd.22 - gsmtp
sendmail: could not send mail (account default from /etc/msmtprc)



```

output.txt
```
loaded system configuration file /etc/msmtprc
ignoring user configuration file /root/.msmtprc: No such file or directory
falling back to default account
using account default from /etc/msmtprc
host                  = smtp.gmail.com
port                  = 587
timeout               = off
protocol              = smtp
domain                = localhost
auth                  = choose
user                  = metulbor@gmail
password              = *
passwordeval          = (not set)
ntlmdomain            = (not set)
tls                   = on
tls_starttls          = on
tls_trust_file        = /etc/ssl/certs/ca-certificates.crt
tls_crl_file          = (not set)
tls_fingerprint       = (not set)
tls_key_file          = (not set)
tls_cert_file         = (not set)
tls_certcheck         = on
tls_force_sslv3       = off
tls_min_dh_prime_bits = (not set)
tls_priorities        = (not set)
auto_from             = off
maildomain            = (not set)
from                  = metulbot@gmail
dsn_notify            = (not set)
dsn_return            = (not set)
keepbcc               = on
logfile               = /var/log/msmtp.log
syslog                = (not set)
aliases               = (not set)
reading recipients from the command line
<-- 220 smtp.gmail.com ESMTP f105sm7128272qgd.22 - gsmtp^M
--> EHLO localhost^M
<-- 250-smtp.gmail.com at your service, [198.199.80.192]^M
<-- 250-SIZE 35882577^M
<-- 250-8BITMIME^M
<-- 250-STARTTLS^M
<-- 250-ENHANCEDSTATUSCODES^M
<-- 250-PIPELINING^M
<-- 250-CHUNKING^M
<-- 250 SMTPUTF8^M
--> STARTTLS^M
<-- 220 2.0.0 Ready to start TLS^M
TLS certificate information:
    Owner:
        Common Name: smtp.gmail.com
        Organization: Google Inc
        Locality: Mountain View
        State or Province: California
        Country: US
    Issuer:
        Common Name: Google Internet Authority G2
        Organization: Google Inc
        Country: US
    Validity:
        Activation time: Wed 18 Feb 2015 05:19:56 AM EST
        Expiration time: Wed 30 Dec 2015 07:00:00 PM EST
    Fingerprints:
        SHA1: D3:7C:82:FC:D0:5F:8F:D7:DA:A2:59:8C:42:D7:B2:9F:C1:9F:7E:60
        MD5:  5A:01:9E:79:12:D4:BF:B1:68:79:ED:FA:9E:CD:C0:F5
--> EHLO localhost^M
<-- 250-smtp.gmail.com at your service, [198.199.80.192]^M
<-- 250-SIZE 35882577^M
<-- 250-8BITMIME^M
<-- 250-AUTH LOGIN PLAIN XOAUTH2 PLAIN-CLIENTTOKEN XOAUTH OAUTHBEARER^M
<-- 250-ENHANCEDSTATUSCODES^M
<-- 250-PIPELINING^M
<-- 250-CHUNKING^M
<-- 250 SMTPUTF8^M
--> AUTH PLAIN AG1ldHVsYm9yQGdtYWlsADk5ZHNvbTJy^M
<-- 535-5.7.8 Username and Password not accepted. Learn more at^M
<-- 535 5.7.8  https://support.google.com/mail/answer/14257 f105sm7128272qgd.22 - gsmtp^M




```

and then i tried this
```
metulburr ~ $  echo "test" | mail -s "test" metulburr@gmail.com
mail: cannot send message: Process exited with a non-zero status



```

---

### Post by SeijiSensei on 2015-10-03
1) myhostname = [email]metulburr@python-gaming.com[/email]
"Myhostname" refers to the name of the machine, not an email address.  "[Character 64 decimal]("http://ascii.cl/")" is the "@" sign.

2) user                  = metulbor@gmail
That's probably not right either.  Shouldn't it end in ".com" or just use the name part "metulbor"?  Did you read [https://support.google.com/mail/answer/14257](https://support.google.com/mail/answer/14257) like the error message suggests?

You probably need to read the documentation for these programs again.

---

### Post by micahpage on 2015-10-03
omg i dont know why i put an email address for hostname. The other was a typo. However i tried to resend an email and i got the similar output from above.

I do not get any more errors in mail log whne i try to send email. However no email gets sent. 

I have spend the past 3 days trying to get this server to send an email verification back to users. I changed so many files that i dont remember what i changed anymore. Ive read so many docs that i keep getting them mixed up....sendmail, mail, postfix, smtp, ssmtp. And i am still not sure how these all are related. I read a lot of different tutorials that have me changing files to and from different things. At this point i am worried that my server is so messed up from me changing values. Is there a way to ensure that i can start over?

EDIT:
one of these times i tried it. I got an email on gmail saying sign in attempt blocked. Is this relevant? 
It said for the reason: [COLOR=#202020][FONT=Roboto-Regular]doesn't meet modern security standards.

I informed it was me, and retried to send an email after, but still cannot get an email to send[/FONT][/COLOR]

---

### Post by micahpage on 2015-10-03
OK so i think i am getting closer to this...

Now when i try to send email i get this error in the logs
```
Oct  3 19:49:32 python-gaming postfix/postdrop[13557]: warning: unable to look up public/pickup: No such file or directory


```

from googling i found this
[http://www.databasically.com/2009/12/02/ubuntu-postfix-error-postdrop-warning-unable-to-look-up-publicpickup-no-such-file-or-directory/](http://www.databasically.com/2009/12/02/ubuntu-postfix-error-postdrop-warning-unable-to-look-up-publicpickup-no-such-file-or-directory/)

but i do not understand the output from his command?
```
metulburr ~ $ mkfifo /var/spool/postfix/public/pickup ps aux | grep mail kill sudo /etc/init.d/postfix restartmkfifo: cannot create fifo ‘/var/spool/postfix/public/pickup’: Permission denied
grep: kill: No such file or directory
grep: sudo: No such file or directory
/etc/init.d/postfix:# based on sendmail's init.d script
/etc/init.d/postfix:# Provides:          postfix mail-transport-agent
grep: restart: No such file or directory
metulburr ~ $ sudo !!
sudo mkfifo /var/spool/postfix/public/pickup ps aux | grep mail kill sudo /etc/init.d/postfix restart
grep: kill: No such file or directory
grep: sudo: No such file or directory
/etc/init.d/postfix:# based on sendmail's init.d script
/etc/init.d/postfix:# Provides:          postfix mail-transport-agent
grep: restart: No such file or directory
mkfifo: cannot create fifo ‘ps’: File exists
mkfifo: cannot create fifo ‘aux’: File exists
metulburr ~ $ 



```

---

### Post by CharlesA on 2015-10-03
> **micahpage said:**
> 
```
metulburr ~ $ telnet localhost 25Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 python-gaming ESMTP [COLOR="#FF0000"]**Sendmail**[/COLOR] 8.14.4/8.14.4/Debian-4.1ubuntu1; Fri, 2 Oct 2015 23:26:58 -0400; (No UCE/UBE) logging access from: localhost(OK)-localhost [127.0.0.1]
```

Are you actually using postfix or are you using sendmail?

---

### Post by micahpage on 2015-10-03
I am suppose ot be using postfix. I treid sendmail first.

now it shows:
```
metulburr ~ $ telnet localhost 25Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 python-gaming ESMTP Postfix (Ubuntu)
ehlo localhost
250-python-gaming
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN



```



after stopping sendmail daemon i restarted postfix and now i get this error in the logs
```
Oct  3 19:58:18 python-gaming postfix/pickup[15479]: C1EE51404F2: uid=1000 from=<metulburr@python-gaming>Oct  3 19:58:18 python-gaming postfix/cleanup[15481]: C1EE51404F2: message-id=<20151003235818.C1EE51404F2@python-gaming>
Oct  3 19:58:18 python-gaming postfix/qmgr[15480]: C1EE51404F2: from=<metulburr@python-gaming>, size=347, nrcpt=1 (queue active)
Oct  3 19:58:19 python-gaming postfix/smtp[15489]: C1EE51404F2: to=<metulburr@gmail.com>, relay=gmail-smtp-in.l.google.com[64.233.171.27]:25, delay=0.37, delays=0/0/0.22/0.14, dsn=2.0.0, status=sent (250 2.0.0 OK 1443916699 r68si16959538qkl.86 - gsmtp)
Oct  3 19:58:19 python-gaming postfix/qmgr[15480]: C1EE51404F2: removed
Oct  3 20:01:36 python-gaming postfix/scache[15490]: statistics: start interval Oct  3 19:58:16
Oct  3 20:01:36 python-gaming postfix/scache[15490]: statistics: domain lookup hits=0 miss=3 success=0%
Oct  3 20:01:43 python-gaming postfix/smtpd[16145]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled
Oct  3 20:01:43 python-gaming postfix/smtpd[16145]: cannot load Certificate Authority data: disabling TLS support
Oct  3 20:01:43 python-gaming postfix/smtpd[16145]: warning: TLS library problem: error:02001002:system library:fopen:No such file or directory:bss_file.c:169:fopen('/etc/ssl/certs/cacert.pem','r'):
Oct  3 20:01:43 python-gaming postfix/smtpd[16145]: warning: TLS library problem: error:2006D080:BIO routines:BIO_new_file:no such file:bss_file.c:172:
Oct  3 20:01:43 python-gaming postfix/smtpd[16145]: warning: TLS library problem: error:0B084002:x509 certificate routines:X509_load_cert_crl_file:system lib:by_file.c:274:
Oct  3 20:01:43 python-gaming postfix/smtpd[16145]: connect from localhost[127.0.0.1]
metulburr ~ $ 





```
I dont understand what it means?

---

### Post by micahpage on 2015-10-03
At this point i am willing to give server access for help because i think i messed this up bad.

---

### Post by CharlesA on 2015-10-03
Postfix cannot find the cert listed in main.cf.

Have you verified the file exists? It was in the howto under "Generate certificates to be used for TLS encryption and/or certificate Authentication:"
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

---

### Post by micahpage on 2015-10-03
Those are already in my main.cf 
```
# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache



```
and the files do exist
```
metulburr /var/www/html $ ls /etc/ssl/certs/ | grep smtp
smtpd.crt
metulburr /var/www/html $ ls /etc/ssl/private/ | grep smtp
ls: cannot open directory /etc/ssl/private/: Permission denied
metulburr /var/www/html $ sudo !!
sudo ls /etc/ssl/private/ | grep smtp
[sudo] password for metulburr: 
smtpd.key
metulburr /var/www/html $ 





```

---

### Post by micahpage on 2015-10-03
Im not sure what i did. Because i did not do anything. 
I gave this command:
```
metulburr ~ $ echo "Subject: test the tenth time" | /usr/lib/sendmail -v metulburr@gmail.comMail Delivery Status Report will be mailed to <metulburr>.



```
and it sends an email to  my gmail. Now looking at this knowing sendmail is off...i remember one tutorial saying to make symbolic links to sendmail for postfix. I do not remember the tutorial otherwise i would post it here. but i can give a history of related commands if that would help?

```
sudo vim /etc/postfix/main.cf  188  sudo service postfix restart
  189  echo "This is the body of the email" | mail -s "This is the subject line" metulburr@gmail.com
  190  mail -s "Hello world" metulburr@gmail.com
  191  sudo vim /etc/postfix/main.cf
  192  echo "This is the body of the email" | mail -s "This is the subject line" metulburr@gmail.com
  193  sudo vim /etc/php5/apache2/php.ini
  194  cd
  195  sudo apt-get install msmtp
  196  sudo vim /etc/msmtprc
  197  touch /etc/msmtprc
  198  sudo touch /etc/msmtprc
  199  sudo ufw allow 587
  200  sudo ufw allow 8888
 201  sudo vim /etc/msmtprc
  202  sudo chgrp mail /etc/msmtprc
  203  sudo chmod 660 /etc/msmtprc
  204  sudo adduser www-data mail
  205  sudo adduser metulburr mail
  206  sudo vim /etc/msmtprc
  207  sudo touch /var/log/msmtp.log
  208  sudo chgrp mail /var/log/msmtp.log
  209  sudo chmod 660 /var/log/msmtp.log
  210  sudo apt-get install msmtp-mta
  211  ln -s /usr/bin/msmtp /usr/sbin/sendmail
  212  ln -s /usr/bin/msmtp /usr/bin/sendmail
  213  sudo ln -s /usr/bin/msmtp /usr/bin/sendmail
  214  ln -s /usr/bin/msmtp /usr/lib/sendmail
  215  sudo vim /etc/php5/apache2/php.ini
  216  sudo service apache2 restart
  217  cd /var/www/html
218  ls
  219  touch testmail
  220  sudo touch testmail
  221  ls
  222  sudo vim testmail
  223  cat | testmail msmtp komu@domain.com
  224  cat testmail | msmtp komu@domain.com
  225  cat testmail | msmtp metulburr@python-gaming.com
  226  cat testmail | msmtp metulburr@gmail.com
  227  telnet gmail-smtp-in.l.google.com 25
  228  echo "This is the body of the email" | mail -s "This is the subject line" metulburr@gmail.com
  229  ssmtp metulburr@gmail.com
  230  smtp metulburr@gmail.com
  231  cd pygame/
  232  cd Dump/
  233  l
  234  ls | less
  235  cd ../..
  236  sudo vim index.html 
  237  ls
238  sudo vim script.js 
  239  sudo mv script.js scriptOLD.js
  240  ls
  241  sudo mv scriptOLD.js script.js
  242  sudo vim script.js 
  243  sudo vim index.html 
  244  sudo vim script.js 
  245  telnet gmail-smtp-in.l.google.com 25
  246  echo "Subject: test" | /usr/lib/sendmail -v metulburr@gmail.com
  247  netstat -t -a | grep LISTEN
  248  lsof -i tcp:25
  249  lsof -i tcp:587
250  postconf -n | wc -l
  251  cd /etc/postfix
  252  ls
  253  cat main.cf | wc -l
  254  postconf -n | wc -l
  255  sudo postconf -n | wc -l
  256  sudo vim main.cf 
  257  echo "Subject: test" | /usr/lib/sendmail -v metulburr@gmail.com
  258  echo "Subject: test the second time" | /usr/lib/sendmail -v metulburr@gmail.com

















```
specifically of that line 211


I am assuming that this is successful and i am done with the server side of postfix? However WordPress does not send an email verification on user registration. Does this mean there is a problem with Wordpress or is there still something i am doing wrong with postfix?

EDIT:
sending to [EMAIL="metulburr@gmail.com"]metulburr@gmail.com[/EMAIL] works, however if i send it to any other email it does not. I am at a total loss?
this is the log
```
metulburr /var/www/html $ sudo tail -f /var/log/mail.log[sudo] password for metulburr: Oct  3 21:03:41 python-gaming postfix/qmgr[15480]: CB15A140906: from=<metulburr@python-gaming.com>, size=302, nrcpt=1 (queue active)
Oct  3 21:03:42 python-gaming postfix/smtp[28059]: connect to gmail-smtp-in.l.google.com[2607:f8b0:400d:c03::1b]:25: Network is unreachable
Oct  3 21:03:42 python-gaming postfix/smtp[28059]: CB15A140906: to=<metulbot@gmail.com>, relay=gmail-smtp-in.l.google.com[64.233.171.27]:25, delay=0.63, delays=0.02/0.01/0.34/0.25, dsn=2.0.0, status=sent (250 2.0.0 OK 1443920622 p77si7878252qgp.69 - gsmtp)
Oct  3 21:03:42 python-gaming postfix/cleanup[28057]: 70EF8140907: message-id=<20151004010342.70EF8140907@python-gaming>
Oct  3 21:03:42 python-gaming postfix/qmgr[15480]: 70EF8140907: from=<>, size=1946, nrcpt=1 (queue active)
Oct  3 21:03:42 python-gaming postfix/bounce[28062]: CB15A140906: sender delivery status notification: 70EF8140907
Oct  3 21:03:42 python-gaming postfix/qmgr[15480]: CB15A140906: removed
Oct  3 21:03:42 python-gaming postfix/local[28064]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled
Oct  3 21:03:42 python-gaming postfix/local[28064]: 70EF8140907: to=<metulburr@python-gaming.com>, relay=local, delay=0.02, delays=0/0.01/0/0, dsn=2.0.0, status=sent (delivered to maildir)
Oct  3 21:03:42 python-gaming postfix/qmgr[15480]: 70EF8140907: removed



```

---

### Post by CharlesA on 2015-10-03
Is this the server that accepts mail for python-gaming.com?

---

### Post by micahpage on 2015-10-03
We have only one server. I dont remember setting anything up for mail to go to python-gaming.com

All i wanted for mail related was to give email activations for new user registrations for wordpress under the site. Otherwise i wouldnt even bother with any of the mail. I did a few tutorials for numerous mail related, including one to set up a mail-server, but then i realized i only needed smtp to give email activations.

---

### Post by CharlesA on 2015-10-03
> **micahpage said:**
> We have only one server. I dont remember setting anything up for mail to go to python-gaming.com

All i wanted for mail related was to give email activations for new user registrations for wordpress under the site. Otherwise i wouldnt even bother with any of the mail. I did a few tutorials for numerous mail related, including one to set up a mail-server, but then i realized i only needed smtp to give email activations.

OK.

Change this in main.cf:
```

mydestination = python-gaming.com, python-gaming, localhost.localdomain, localhost
```

To this:
```

mydestination = 
```

Restart postfix and test it.

---

### Post by micahpage on 2015-10-03
ok did that. Now i dont get an email at any email form the server
```
metulburr ~ $ echo "Subject: Hello Test" | /usr/lib/sendmail -v metulbot@gmail.com
Mail Delivery Status Report will be mailed to <metulburr>.
metulburr ~ $ echo "Subject: Hello Test" | /usr/lib/sendmail -v metulburr@gmail.com
Mail Delivery Status Report will be mailed to <metulburr>.



```
both fail to email addresses

the log file now shows this
```
Oct  3 23:05:09 python-gaming postfix/pickup[16137]: 1F89014090E: uid=1000 from=<metulburr>Oct  3 23:05:09 python-gaming postfix/cleanup[17004]: 1F89014090E: message-id=<20151004030509.1F89014090E@python-gaming>
Oct  3 23:05:09 python-gaming postfix/qmgr[16138]: 1F89014090E: from=<metulburr@python-gaming.com>, size=302, nrcpt=1 (queue active)
Oct  3 23:05:09 python-gaming postfix/smtp[17006]: connect to gmail-smtp-in.l.google.com[2607:f8b0:400d:c03::1b]:25: Network is unreachable
Oct  3 23:05:09 python-gaming postfix/smtp[17006]: 1F89014090E: to=<metulburr@gmail.com>, relay=gmail-smtp-in.l.google.com[64.233.171.27]:25, delay=0.48, delays=0.02/0.01/0.3/0.15, dsn=2.0.0, status=sent (250 2.0.0 OK 1443927909 l96si17464999qgl.119 - gsmtp)
Oct  3 23:05:09 python-gaming postfix/cleanup[17004]: 9511C14090F: message-id=<20151004030509.9511C14090F@python-gaming>
Oct  3 23:05:09 python-gaming postfix/qmgr[16138]: 9511C14090F: from=<>, size=1952, nrcpt=1 (queue active)
Oct  3 23:05:09 python-gaming postfix/bounce[17007]: 1F89014090E: sender delivery status notification: 9511C14090F
Oct  3 23:05:09 python-gaming postfix/qmgr[16138]: 1F89014090E: removed
Oct  3 23:05:10 python-gaming postfix/smtp[17006]: 9511C14090F: to=<metulburr@python-gaming.com>, relay=smtp.secureserver.net[68.178.213.37]:25, delay=0.77, delays=0/0/0.62/0.15, dsn=5.1.1, status=bounced (host smtp.secureserver.net[68.178.213.37] said: 550 5.1.1 <metulburr@python-gaming.com> Recipient not found.  <http://x.co/irbounce> (in reply to RCPT TO command))
Oct  3 23:05:10 python-gaming postfix/qmgr[16138]: 9511C14090F: removed



```
one part of that error message that catches me is 
> [COLOR=#000000][FONT=Ubuntu Mono] 550 5.1.1 <metulburr@python-gaming.com> Recipient not found.[/FONT][/COLOR]
I am not even sure where [EMAIL="metulburr@python-gaming.com"]metulburr@python-gaming.com[/EMAIL] is located anymore? And why would that be the recipient anyway?

EDIT:
Then researching online i saw logs being added on the mail log in the terminal without me doing anything. So i am not sure what is going on?
```
Oct  3 23:20:01 python-gaming postfix/pickup[16137]: CE06314090E: uid=108 from=<smmsp>Oct  3 23:20:01 python-gaming postfix/cleanup[19740]: CE06314090E: message-id=<20151004032001.CE06314090E@python-gaming>
Oct  3 23:20:01 python-gaming postfix/qmgr[16138]: CE06314090E: from=<smmsp@python-gaming.com>, size=700, nrcpt=1 (queue active)
Oct  3 23:20:02 python-gaming postfix/smtp[19742]: CE06314090E: to=<root@python-gaming.com>, orig_to=<root>, relay=smtp.secureserver.net[68.178.213.203]:25, delay=1.1, delays=0.03/0.02/0.74/0.29, dsn=5.1.1, status=bounced (host smtp.secureserver.net[68.178.213.203] said: 550 5.1.1 <root@python-gaming.com> Recipient not found.  <http://x.co/irbounce> (in reply to RCPT TO command))
Oct  3 23:20:03 python-gaming postfix/cleanup[19740]: 07A6214090F: message-id=<20151004032003.07A6214090F@python-gaming>
Oct  3 23:20:03 python-gaming postfix/qmgr[16138]: 07A6214090F: from=<>, size=2728, nrcpt=1 (queue active)
Oct  3 23:20:03 python-gaming postfix/bounce[19743]: CE06314090E: sender non-delivery notification: 07A6214090F
Oct  3 23:20:03 python-gaming postfix/qmgr[16138]: CE06314090E: removed
Oct  3 23:20:03 python-gaming postfix/smtp[19742]: 07A6214090F: to=<smmsp@python-gaming.com>, relay=smtp.secureserver.net[68.178.213.203]:25, delay=0.88, delays=0.01/0/0.72/0.15, dsn=5.1.1, status=bounced (host smtp.secureserver.net[68.178.213.203] said: 550 5.1.1 <smmsp@python-gaming.com> Recipient not found.  <http://x.co/irbounce> (in reply to RCPT TO command))
Oct  3 23:20:04 python-gaming postfix/qmgr[16138]: 07A6214090F: removed



```

---

### Post by CharlesA on 2015-10-03
Where is your email hosted? Judging from the MX records for python-gaming.com, it is hosted at "secureserver" whoever that is.

```
dig +short mx python-gaming.com
10 mailstore1.secureserver.net.
0 smtp.secureserver.net.

```

---

### Post by micahpage on 2015-10-03
The server is hosted by Digital Ocean

---

### Post by CharlesA on 2015-10-04
> **micahpage said:**
> The server is hosted by Digital Ocean

As far as I know, DO does not do email hosting, which would be why you are getting errors when you try to send mail.

Try sending mail to a valid gmail or yahoo or other address and see what happens.

---

### Post by micahpage on 2015-10-04
I did. I get the same result as previous.

I wasnt even aware of the host having the ability on whether you can do email activations. I thought it was all on the server and taht the server could send mail. It sent mail to my gmail that one time with settings, why couldnt it send mail out for email activations?

Also what doesnt make sense is wordpress requires email activation for users. They do not have an option to opt out of email and use captchas or security questions /etc. So why does digital ocean have a tutorial for wordpress setup? That would imply that digital ocean host can send email activations for wordpress servers.

---

### Post by CharlesA on 2015-10-04
Logs please.

---

### Post by micahpage on 2015-10-04
```
echo "Subject: test the tenth time" | /usr/lib/sendmail -v metulburr@gmail.com


```
```
Oct  4 17:30:08 python-gaming postfix/cleanup[12273]: 370DC1409DF: message-id=<20151004213008.370DC1409DF@python-gaming>Oct  4 17:30:08 python-gaming postfix/qmgr[23707]: 370DC1409DF: from=<metulburr@python-gaming.com>, size=261, nrcpt=1 (queue active)
Oct  4 17:30:08 python-gaming postfix/smtp[12275]: connect to gmail-smtp-in.l.google.com[2607:f8b0:400d:c03::1a]:25: Network is unreachable
Oct  4 17:30:09 python-gaming postfix/smtp[12275]: 370DC1409DF: to=<metulburr@gmail.com>, relay=gmail-smtp-in.l.google.com[64.233.171.26]:25, delay=1.2, delays=0.22/0.02/0.58/0.39, dsn=2.0.0, status=sent (250 2.0.0 OK 1443994209 w15si20324965qha.59 - gsmtp)
Oct  4 17:30:09 python-gaming postfix/cleanup[12273]: 3B3101409E0: message-id=<20151004213009.3B3101409E0@python-gaming>
Oct  4 17:30:09 python-gaming postfix/qmgr[23707]: 3B3101409E0: from=<>, size=1909, nrcpt=1 (queue active)
Oct  4 17:30:09 python-gaming postfix/bounce[12276]: 370DC1409DF: sender delivery status notification: 3B3101409E0
Oct  4 17:30:09 python-gaming postfix/qmgr[23707]: 370DC1409DF: removed
Oct  4 17:30:10 python-gaming postfix/smtp[12275]: 3B3101409E0: to=<metulburr@python-gaming.com>, relay=smtp.secureserver.net[68.178.213.203]:25, delay=1.2, delays=0/0/1/0.15, dsn=5.1.1, status=bounced (host smtp.secureserver.net[68.178.213.203] said: 550 5.1.1 <metulburr@python-gaming.com> Recipient not found.  <http://x.co/irbounce> (in reply to RCPT TO command))
Oct  4 17:30:10 python-gaming postfix/qmgr[23707]: 3B3101409E0: removed



```

```
metulburr ~ $ echo "Subject: test the tenth time" | /usr/lib/sendmail -v sondra.parkin@gmail.com
```

```
Oct  4 17:32:14 python-gaming postfix/qmgr[23707]: 370A21409DF: from=<metulburr@python-gaming.com>, size=261, nrcpt=1 (queue active)Oct  4 17:32:14 python-gaming postfix/smtp[12591]: connect to gmail-smtp-in.l.google.com[2607:f8b0:400d:c03::1a]:25: Network is unreachable
Oct  4 17:32:14 python-gaming postfix/smtp[12591]: 370A21409DF: to=<sondra.parkin@gmail.com>, relay=gmail-smtp-in.l.google.com[64.233.171.26]:25, delay=0.58, delays=0.2/0.01/0.31/0.06,    dsn=2.0.0, status=sent (250 2.0.0 OK 1443994334 f19si20349795qhe.2 - gsmtp)
Oct  4 17:32:14 python-gaming postfix/cleanup[12589]: 994041409E0: message-id=<20151004213214.994041409E0@python-gaming>
Oct  4 17:32:14 python-gaming postfix/qmgr[23707]: 994041409E0: from=<>, size=1915, nrcpt=1   (queue active)
Oct  4 17:32:14 python-gaming postfix/bounce[12592]: 370A21409DF: sender delivery status      notification: 994041409E0
Oct  4 17:32:14 python-gaming postfix/qmgr[23707]: 370A21409DF: removed
Oct  4 17:32:15 python-gaming postfix/smtp[12591]: 994041409E0: to=<metulburr@python-gaming.  com>, relay=smtp.secureserver.net[68.178.213.37]:25, delay=0.97, delays=0/0/0.7/0.27, dsn=5.1.1, status=bounced (host smtp.secureserver.net[68.178.213.37] said: 550 5.1.1 <metulburr@      python-gaming.com> Recipient not found.  <http://x.co/irbounce> (in reply to RCPT TO command))
Oct  4 17:32:15 python-gaming postfix/qmgr[23707]: 994041409E0: removed



```


```
echo "Subject: test the tenth time" | /usr/lib/sendmail -v micahpage911@yahoo.com


```
```
Oct  4 17:34:35 python-gaming postfix/pickup[7459]: 932341409DF: uid=1000 from=<metulburr>Oct  4 17:34:35 python-gaming postfix/cleanup[13152]: 932341409DF: message-id=<20151004213435.932341409DF@python-gaming>
Oct  4 17:34:35 python-gaming postfix/qmgr[23707]: 932341409DF: from=<metulburr@python-gaming.com>, size=261, nrcpt=1 (queue active)
Oct  4 17:34:36 python-gaming postfix/smtp[13154]: 932341409DF: to=<micahpage911@yahoo.com>, relay=mta6.am0.yahoodns.net[66.196.118.36]:25, delay=0.89, delays=0.23/0.02/0.11/0.53, dsn=2.0.0, status=sent (250 ok dirdel)
Oct  4 17:34:36 python-gaming postfix/cleanup[13152]: 478B31409E0: message-id=<20151004213436.478B31409E0@python-gaming>
Oct  4 17:34:36 python-gaming postfix/qmgr[23707]: 478B31409E0: from=<>, size=1824, nrcpt=1 (queue active)
Oct  4 17:34:36 python-gaming postfix/bounce[13155]: 932341409DF: sender delivery status notification: 478B31409E0
Oct  4 17:34:36 python-gaming postfix/qmgr[23707]: 932341409DF: removed
Oct  4 17:34:37 python-gaming postfix/smtp[13154]: 478B31409E0: to=<metulburr@python-gaming.com>, relay=smtp.secureserver.net[72.167.238.29]:25, delay=0.9, delays=0/0/0.74/0.15, dsn=5.1.1, status=bounced (host smtp.secureserver.net[72.167.238.29] said: 550 5.1.1 <metulburr@python-gaming.com> Recipient not found.  <http://x.co/irbounce> (in reply to RCPT TO command))
Oct  4 17:34:37 python-gaming postfix/qmgr[23707]: 478B31409E0: removed

```


```
metulburr /var/www/html $ echo "Subject: test the tenth time" | /usr/lib/sendmail -v micahpage912@yahoo.com
Mail Delivery Status Report will be mailed to <metulburr>.
metulburr /var/www/html $
```


```
Oct  4 17:36:49 python-gaming postfix/pickup[7459]: A10691409DF: uid=1000 from=<metulburr>Oct  4 17:36:49 python-gaming postfix/cleanup[13435]: A10691409DF: message-id=<20151004213649.A10691409DF@python-gaming>
Oct  4 17:36:49 python-gaming postfix/qmgr[23707]: A10691409DF: from=<metulburr@python-gaming.com>, size=291, nrcpt=1 (queue active)
Oct  4 17:36:51 python-gaming postfix/smtp[13437]: A10691409DF: to=<micahpage912@yahoo.com>, relay=mta7.am0.yahoodns.net[63.250.192.46]:25, delay=1.8, delays=0.02/0.01/0.51/1.2, dsn=2.0.0, status=sent (250 ok dirdel)
Oct  4 17:36:51 python-gaming postfix/cleanup[13435]: 6E2DD1409E0: message-id=<20151004213651.6E2DD1409E0@python-gaming>
Oct  4 17:36:51 python-gaming postfix/qmgr[23707]: 6E2DD1409E0: from=<>, size=1854, nrcpt=1 (queue active)
Oct  4 17:36:51 python-gaming postfix/bounce[13438]: A10691409DF: sender delivery status notification: 6E2DD1409E0
Oct  4 17:36:51 python-gaming postfix/qmgr[23707]: A10691409DF: removed
Oct  4 17:36:52 python-gaming postfix/smtp[13437]: 6E2DD1409E0: to=<metulburr@python-gaming.com>, relay=smtp.secureserver.net[68.178.213.37]:25, delay=0.98, delays=0/0/0.84/0.14, dsn=5.1.1, status=bounced (host smtp.secureserver.net[68.178.213.37] said: 550 5.1.1 <metulburr@python-gaming.com> Recipient not found.  <http://x.co/irbounce> (in reply to RCPT TO command))
Oct  4 17:36:52 python-gaming postfix/qmgr[23707]: 6E2DD1409E0: removed



```

---

### Post by CharlesA on 2015-10-04
Yahoo and Google work fine.

You need to see who handles email for python-gaming.com since it is obviously not smtp.secureserver.net.

I have my mail hosted at mxroute because I didn't want to host it myself.

---

### Post by micahpage on 2015-10-04
> [COLOR=#000000]Yahoo and Google work fine.[/COLOR]
except i dont get any emails at those addresses

> [COLOR=#000000]You need to see who handles email for python-gaming.com since it is obviously not smtp.secureserver.net.[/COLOR]
I personally bought the server, domain, and installed ubuntu, LAMP. I just assumed you could set up email hosting under the same server that is hosting your site. 

I dont understand. Is mxroute suppose to simplify this process? If i did get an mxroute plan, is it more than what i am looking for. I mean all i want to do is for one application, send email verifications. Its seems so minor. Paying for email hosting seems like for domains that would utilize email more, wouldnt it?

Of course, if i pay the 15/year plan to avoid this headache, i might. I just dont want to get into another headache trying to setup their email hosting.

---

### Post by CharlesA on 2015-10-04
> **micahpage said:**
> except i dont get any emails at those addresses

Even in the spam folder? The logs say the emails were sent.

> I personally bought the server, domain, and installed ubuntu, LAMP. I just assumed you could set up email hosting under the same server that is hosting your site.

I dont understand. Is mxroute suppose to simplify this process? If i did get an mxroute plan, is it more than what i am looking for. I mean all i want to do is for one application, send email verifications. Its seems so minor. Paying for email hosting seems like for domains that would utilize email more, wouldnt it?

Of course, if i pay the 15/year plan to avoid this headache, i might. I just dont want to get into another headache trying to setup their email hosting.

You only need a mail server if you intend to receive mail for your domain. If you are only sending mail, a simple install of Postfix should just work.

Have you purged postfix and tried starting from scratch?

You can also check your server using [mxtoolbox]("http://mxtoolbox.com/") and see if it is blacklisted or something else.

FWIW, I use Mxroute so I can receive mail via my domain. If I was just sending notifications out, I could just let Postfix handle it. It really sounds like a misconfiguration, but if you can post your main.cf and master.cf files, we could verify.

---

### Post by micahpage on 2015-10-04
> [COLOR=#000000]You only need a mail server if you intend to receive mail for your domain. If you are only sending mail, a simple install of Postfix should just work.[/COLOR]
i do not plan on receiving mail for the domain. I only need it to send out activation emails. 

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


# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache


# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.


smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = python-gaming
#alias_maps = hash:/etc/aliases
virtual_alias_maps = hash:/etc/postfix/virtual
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
#mydestination = python-gaming.com, python-gaming, localhost.localdomain, localhost
mydestination =
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command =
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = localhost
#inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom



```


master.cf
```
## Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master" or
# on-line: http://www.postfix.org/master.5.html).
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd
#smtp      inet  n       -       -       -       1       postscreen
#smtpd     pass  -       -       -       -       -       smtpd
#dnsblog   unix  -       -       -       -       0       dnsblog
#tlsproxy  unix  -       -       -       -       0       tlsproxy
#submission inet n       -       -       -       -       smtpd
#  -o syslog_name=postfix/submission
#  -o smtpd_tls_security_level=encrypt
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_reject_unlisted_recipient=no
#  -o smtpd_client_restrictions=$mua_client_restrictions
#  -o smtpd_helo_restrictions=$mua_helo_restrictions
#  -o smtpd_sender_restrictions=$mua_sender_restrictions
#  -o smtpd_recipient_restrictions=
#  -o smtpd_relay_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#smtps     inet  n       -       -       -       -       smtpd
#  -o syslog_name=postfix/smtps
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_reject_unlisted_recipient=no
#  -o smtpd_client_restrictions=$mua_client_restrictions
#  -o smtpd_helo_restrictions=$mua_helo_restrictions
#  -o smtpd_sender_restrictions=$mua_sender_restrictions
#  -o smtpd_recipient_restrictions=
#  -o smtpd_relay_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#628       inet  n       -       -       -       -       qmqpd
pickup    unix  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      unix  n       -       n       300     1       qmgr
#qmgr     unix  n       -       n       300     1       oqmgr
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
scalemail-backend unix  -   n   n   -   2   pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}



```


> [COLOR=#000000]Even in the spam folder? The logs say the emails were sent.[/COLOR]
omg i feel like an idiot. They are in spam.

Wordpress does not send email verifications after this process. I ahve been checking plugins. [https://wordpress.org/plugins/configure-smtp/screenshots/](https://wordpress.org/plugins/configure-smtp/screenshots/)

I am not  even sure what information to insert in these. Did i use SMTPAuth? Is the SMTP host python-game or localhost? They said most likely port 25, but would mine be 587? What is the SMTP username and password?

---

### Post by CharlesA on 2015-10-04
Ok. Those look right.

Check your server against mxtoolbox. It should tell you if you are blacklisted or if there are other issues that will cause issues with your mail being delivered.

---

### Post by micahpage on 2015-10-04
This is the smtp plugin for wordpress, in which when i tried to email a test to myself, it gave this error. 
[http://codepad.org/3dYADXkI](http://codepad.org/3dYADXkI)


and my settings for smtp on wordpress
[http://imgur.com/FhwkZRZ](http://imgur.com/FhwkZRZ)

am i doing something obviously wrong with smtp based on configuration of the server?

---

### Post by CharlesA on 2015-10-04
Yes. Your config is all wrong.

Server should be localhost
Port 25
No encryption
No authentication

Also: Be sure to set postfix to only listen to 127.0.0.1 by adding this to main.cf:
```
inet_interfaces = 127.0.0.1
```

You should still verify your server is not on any blacklists otherwise you will likely have sporadic mail delivery.

---

### Post by micahpage on 2015-10-05
changed inet_interfaces, restart postfix, changed smtp config on wordpress to localhost:25, tried to send a test email to [EMAIL="metulburr@gmail.com"]metulburr@gmail.com[/EMAIL] and this is the new error i get. There doesnt seem to be a lot of information on the error.
```
[COLOR=#444444]object(PHPMailer)#413 (73) {[/COLOR]  ["Version"]=>
  string(6) "5.2.10"
  ["Priority"]=>
  int(3)
  ["CharSet"]=>
  string(10) "iso-8859-1"
  ["ContentType"]=>
  string(10) "text/plain"
  ["Encoding"]=>
  string(4) "8bit"
  ["ErrorInfo"]=>
  string(0) ""
  ["From"]=>
  string(14) "root@localhost"
  ["FromName"]=>
  string(9) "Root User"
  ["Sender"]=>
  string(0) ""
  ["ReturnPath"]=>
  string(0) ""
  ["Subject"]=>
  string(0) ""
  ["Body"]=>
  string(0) ""
  ["AltBody"]=>
  string(0) ""
  ["Ical"]=>
  string(0) ""
  ["MIMEBody":protected]=>
  string(0) ""
  ["MIMEHeader":protected]=>
  string(0) ""
  ["mailHeader":protected]=>
  string(0) ""
  ["WordWrap"]=>
  int(0)
  ["Mailer"]=>
  string(4) "mail"
  ["Sendmail"]=>
  string(18) "/usr/sbin/sendmail"
  ["UseSendmailOptions"]=>
  bool(true)
  ["PluginDir"]=>
  string(0) ""
  ["ConfirmReadingTo"]=>
  string(0) ""
  ["Hostname"]=>
  string(0) ""
  ["MessageID"]=>
  string(0) ""
  ["MessageDate"]=>
  string(0) ""
  ["Host"]=>
  string(9) "localhost"
  ["Port"]=>
  int(25)
  ["Helo"]=>
  string(0) ""
  ["SMTPSecure"]=>
  string(0) ""
  ["SMTPAutoTLS"]=>
  bool(true)
  ["SMTPAuth"]=>
  bool(false)
  ["SMTPOptions"]=>
  array(0) {
  }
  ["Username"]=>
  string(0) ""
  ["Password"]=>
  string(0) ""
  ["AuthType"]=>
  string(0) ""
  ["Realm"]=>
  string(0) ""
  ["Workstation"]=>
  string(0) ""
  ["Timeout"]=>
  int(300)
  ["SMTPDebug"]=>
  bool(true)
  ["Debugoutput"]=>
  string(4) "echo"
  ["SMTPKeepAlive"]=>
  bool(false)
  ["SingleTo"]=>
  bool(false)
  ["SingleToArray"]=>
  array(0) {
  }
  ["do_verp"]=>
  bool(false)
  ["AllowEmpty"]=>
  bool(false)
  ["LE"]=>
  string(1) "
"
  ["DKIM_selector"]=>
  string(0) ""
  ["DKIM_identity"]=>
  string(0) ""
  ["DKIM_passphrase"]=>
  string(0) ""
  ["DKIM_domain"]=>
  string(0) ""
  ["DKIM_private"]=>
  string(0) ""
  ["action_function"]=>
  string(0) ""
  ["XMailer"]=>
  string(0) ""
  ["smtp":protected]=>
  NULL
  ["to":protected]=>
  array(0) {
  }
  ["cc":protected]=>
  array(0) {
  }
  ["bcc":protected]=>
  array(0) {
  }
  ["ReplyTo":protected]=>
  array(0) {
  }
  ["all_recipients":protected]=>
  array(0) {
  }
  ["attachment":protected]=>
  array(0) {
  }
  ["CustomHeader":protected]=>
  array(0) {
  }
  ["lastMessageID":protected]=>
  string(0) ""
  ["message_type":protected]=>
  string(0) ""
  ["boundary":protected]=>
  array(0) {
  }
  ["language":protected]=>
  array(0) {
  }
  ["error_count":protected]=>
  int(0)
  ["sign_cert_file":protected]=>
  string(0) ""
  ["sign_key_file":protected]=>
  string(0) ""
  ["sign_extracerts_file":protected]=>
  string(0) ""
  ["sign_key_pass":protected]=>
  string(0) ""
  ["exceptions":protected]=>
  bool(true)
  ["uniqueid":protected]=>
  string(0) ""
}



```


I tried mxtoolbox but i get an error saying its unable to connect to my server
[http://imgur.com/SEZR62P](http://imgur.com/SEZR62P)

---

### Post by CharlesA on 2015-10-05
If you are going to be using mxtoolbox, you would need to set postfix to listen on all interfaces instead of only on 127.0.0.1.

I told you to set it that way so no one from the outside could use your server as a relay (even tho if isn't set up to allow that atm).

On the bright side, the IP in your screenshot isn't blacklisted anywhere. :)

---

### Post by micahpage on 2015-10-05
i reverted the inet_address to all and got OK for all lists.

---

### Post by CharlesA on 2015-10-05
That error just looks like garbage to me. Can you get a screenshot?

---

### Post by micahpage on 2015-10-06
I used a plugin in wordpress to aid with smtp. After configuring that, and granting permissions with google, i am successfully sending email verifications. 
the plugin was
[https://wordpress.org/plugins/postman-smtp/](https://wordpress.org/plugins/postman-smtp/)

Is this using my server, and the settings i changed through this thread? OR is it bypassing and using my gmail account to send emails? I am assuming the latter as the email was from my gmail and not [email]python-gaming@python-gaming.com[/email]? I am not sure but my end goal is complete by sending email verification to new users.

---

### Post by CharlesA on 2015-10-06
It looks to be sending the mail thru your gmail, which is likely not what you want.

I don't use wordpress, so I don't know what that plugin is supposed to do.

---

### Post by micahpage on 2015-10-06
I definitely did not want to use wordpress. But i could not find software that allowed users to register on your site, create an account, and make their own page within a subdirectory of your site. Is there any other software that would do that?

---

### Post by CharlesA on 2015-10-06
I don't know. I don't use any CMS for my website.

Personally, I would suggest setting up a test server (maybe locally?) and make sure you have postfix working correctly before even touching the CMS.

Might be a good idea and start from scratch instead of following that howto you found on the Ubuntu help pages.

---

### Post by micahpage on 2015-10-12
OK thank you for the help.

---

