---
title: "Postfix smpt problem"
date: 2014-05-30
forum: Server Platforms
---

### Post by Sky_rider on 2014-05-30
I have postfix dovecot running with local email system on thunderbird. I have two users on by ubuntu, mailuser 1 and mailuser 2 whom i added to thunderbird. Everything went fine, except the users dont have anything on their inbox on thunderbird and sent mails dont get through.
Im using maildir as well. Checking /var/log/mail.log reveals this
This what is happining: Restarting postfix and dovecot and then sending mail from one user to another user... 

I believe this line is the problem ```
 May 30 18:31:55 postfix/smtpd[12804]: disconnect from localhost[127.0.0.1] 
``` Why is it not connecting ? What could be wrong ?

/var/log/mail.log

> 
May 30 18:30:21  dovecot: imap: Warning: Killed with signal 15 (by pid=1 uid=0 code=kill)
May 30 18:30:21 dovecot: master: Warning: Killed with signal 15 (by pid=1 uid=0 code=kill)
May 30 18:30:21 dovecot: imap: Server shutting down. in=467 out=475
May 30 18:30:21 dovecot: config: Warning: Killed with signal 15 (by pid=1 uid=0 code=kill)
May 30 18:30:21 dovecot: log: Warning: Killed with signal 15 (by pid=1 uid=0 code=kill)
May 30 18:30:21 dovecot: anvil: Warning: Killed with signal 15 (by pid=1 uid=0 code=kill)
May 30 18:30:21 dovecot: master: Dovecot v2.2.9 starting up (core dumps disabled)
May 30 18:30:54 dovecot: imap-login: Login: user=<mailuser2>, method=PLAIN, rip=::1, lip=::1, mpid=12638, TLS, session=<xUfQkaD66gAAAAAAAAAAAAAAAAAAAAAB>
May 30 18:31:04 postfix/master[12245]: terminating on signal 15
May 30 18:31:04 postfix/master[12795]: daemon started -- version 2.11.0, configuration /etc/postfix
May 30 18:31:55 postfix/postscreen[12803]: CONNECT from [127.0.0.1]:33668 to [127.0.0.1]:25
May 30 18:31:55 postfix/postscreen[12803]: WHITELISTED [127.0.0.1]:33668
May 30 18:31:55 postfix/smtpd[12804]: connect from localhost[127.0.0.1]
May 30 18:31:55 postfix/smtpd[12804]: 1ED7120EB9: client=localhost[127.0.0.1]
May 30 18:31:55  postfix/cleanup[12809]: 1ED7120EB9: message-id=<5388B27A.7060709@s148134.com>
May 30 18:31:55 postfix/qmgr[12799]: 1ED7120EB9: from=<mailuser1@mysite.com>, size=546, nrcpt=1 (queue active)
May 30 18:31:55 postfix/local[12810]: 1ED7120EB9: to=<mailuser2@mysitecom>, relay=local, delay=0.03, delays=0.02/0.01/0/0, dsn=2.0.0, status=sent (delivered to maildir)
May 30 18:31:55  postfix/qmgr[12799]: 1ED7120EB9: removed
May 30 18:31:55  postfix/smtpd[12804]: disconnect from localhost[127.0.0.1]
May 30 18:31:55 dovecot: imap-login: Login: user=<mailuser1>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, mpid=12814, TLS, session=<sD9plaD6PgB/AAAB>




This is my postfix main.cf
> 
 See /usr/share/postfix/main.cf.dist for a commented, more complete version


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

smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = server
mydomain = mysite.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = $mydomain
mydestination = mysite.com
#relayhost = smtp.192.168.10.1.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.10.0/24
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
home_mailbox = Maildir /
mailbox_command =



All ports are listning
> 
tcp        0      0 *:imaps                 *:*                     LISTEN     
tcp        0      0 *:submission            *:*                     LISTEN     
tcp        0      0 *:imap2                 *:*                     LISTEN     
tcp        0      0 s148134.s148134.:domain *:*                     LISTEN     
tcp        0      0 192.168.56.101:domain   *:*                     LISTEN     
tcp        0      0 10.0.2.15:domain        *:*                     LISTEN     
tcp        0      0 localhost:domain        *:*                     LISTEN     
tcp        0      0 *:ssh                   *:*                     LISTEN     
tcp        0      0 *:smtp                  *:*                     LISTEN     
tcp        0      0 localhost:953           *:*                     LISTEN     
tcp6       0      0 [::]:imaps              [::]:*                  LISTEN     
tcp6       0      0 [::]:submission         [::]:*                  LISTEN     
tcp6       0      0 [::]:imap2              [::]:*                  LISTEN     
tcp6       0      0 [::]:domain             [::]:*                  LISTEN     
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN     
tcp6       0      0 [::]:smtp               [::]:*                  LISTEN     
tcp6       0      0 localhost:953           [::]:*                  LISTEN 



---

### Post by gtozzi on 2014-05-30
is /var/mail empty?

---

