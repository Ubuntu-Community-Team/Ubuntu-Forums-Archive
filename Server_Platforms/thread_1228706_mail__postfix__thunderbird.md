---
title: "mail / postfix / thunderbird"
date: 2009-08-01
forum: Server Platforms
---

### Post by sw34963 on 2009-08-01
I have a working server with postfix email server configured.  I have horde groupware setup and running.
The problem lies with the thunderbird receiving the emails,  it was working fine but now I am getting the following error messages: 
> 
Aug  1 19:28:29 crimsonserver postfix/smtp[16572]: fatal: specify a password table via the `smtp_sasl_password_maps' configuration parameter
Aug  1 19:28:30 crimsonserver postfix/master[16395]: warning: process /usr/lib/postfix/smtp pid 16572 exit status 1
Aug  1 19:28:30 crimsonserver postfix/master[16395]: warning: /usr/lib/postfix/smtp: bad command startup -- throttling


Everything seems to be working fine except I cant get thunderbird to pull down the emails.

Thanks in advance

Stuart

---

### Post by sw34963 on 2009-08-01
Any ideas, hints or suggestions???

Thanks

---

### Post by fakrulalam on 2009-08-02
Hi,
Are you using SASL? For pull down the mail using Thunderbird (or any pop client), pop service need to configured. Please check if the pop service is running or not (Dovecot/CourierIMAP). For further troubleshoot you can check the output of netstat -nat.

---

### Post by sw34963 on 2009-08-02
Yes I am using SASL.  The service I am using is courier IMAP and it is running.

I ran netstat -nat,  I presume I should be seeing an entry listening on port 143?

cheers

---

### Post by fakrulalam on 2009-08-03
Hi,
Can you show the netstat -nat output. From your log it seems that postfix is not running.

Aug  1 19:28:30 crimsonserver postfix/master[16395]: warning: /usr/lib/postfix/smtp: bad command startup -- throttling 			 		

Please check if postfix is running or not.

---

### Post by sw34963 on 2009-08-03
netstat -nat output
> 
stuart@crimsonserver:~$ netstat -nat
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN
tcp        0      0 169.191.1.150:53        0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN
tcp        0      0 169.191.1.150:139       169.191.1.52:4054       ESTABLISHED
tcp6       0      0 :::993                  :::*                    LISTEN
tcp6       0      0 :::995                  :::*                    LISTEN
tcp6       0      0 :::110                  :::*                    LISTEN
tcp6       0      0 :::143                  :::*                    LISTEN
tcp6       0      0 :::53                   :::*                    LISTEN
tcp6       0      0 :::22                   :::*                    LISTEN
tcp6       0      0 :::25                   :::*                    LISTEN
tcp6       0      0 ::1:953                 :::*                    LISTEN
tcp6       0     52 169.191.1.150:22        169.191.1.52:4237       ESTABLISHED


postfix is running
> 
stuart@crimsonserver:~$ sudo /etc/init.d/postfix restart
[sudo] password for stuart:
 * Stopping Postfix Mail Transport Agent postfix                     [ OK ]
 * Starting Postfix Mail Transport Agent postfix                         [ OK ]


---

### Post by fakrulalam on 2009-08-03
Can you please post the maillog. From the previous maillog it seems that your postfix is having problem with smtp_sasl_password.

**Aug 1 19:28:29 crimsonserver postfix/smtp[16572]: fatal: specify a password table via the `smtp_sasl_password_maps' configuration parameter**

To make the the troubleshot more specific, try to disable the SASL support, run postfix and test your mail server with thunderbird. If it works than you are having problem with smtp_sasl_password parameter.

---

### Post by sw34963 on 2009-08-04
I stopped the sasl daemon
> 
xxxxxx@crimsonserver:/etc/init.d$ sudo /etc/init.d/saslauthd stop
 * Stopping SASL Authentication Daemon saslauthd                         [ OK ]
xxxxxx@crimsonserver:/etc/init.d$ sudo /etc/init.d/saslauthd start
 * Starting SASL Authentication Daemon saslauthd                         [ OK ]


With no result

Here is the latest mail.log entries (which are still the same
> 
Aug  4 22:06:41 crimsonserver postfix/smtp[13447]: fatal: specify a password table via the `smtp_sasl_password_maps' configuration parameter
Aug  4 22:06:42 crimsonserver postfix/master[6785]: warning: process /usr/lib/postfix/smtp pid 13447 exit status 1
Aug  4 22:06:42 crimsonserver postfix/master[6785]: warning: /usr/lib/postfix/smtp: bad command startup -- throttling


And the mail.err 
> 
Aug  2 07:17:07 crimsonserver postfix/smtp[22820]: fatal: specify a password table via the `smtp_sasl_password_maps' configuration parameter

This is leading me to believe - for whatever reason, that something has happened and now it requires me to create a 'smtp_sasl_password_maps' configuration file.
Does this sound fair....  if so what is the syntax for the password maps?

---

### Post by sw34963 on 2009-08-04
So I have created a sasl_passwd file  and I am still getting Thunderbird timeout reaching the server.

Here is my current main.cf
> 
#See /usr/share/postfix/main.cf.dist for a commented, more complete version

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
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = crimsonserver.crimsonmind.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination =  crimsonmind.net, mail.crimsonmind.net, crimsonserver.crimsonmind.net, localhost.crimsonmind.net, localhost
relayhost =
mynetworks = 127.0.0.0/8 ***.***.*.0/24
mailbox_command =
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtp_sasl_local_domain =
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtpd_sasl_security_options =
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
crimsonserver = crimsonserver.crimsonmind.net
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
home_mailbox = Maildir/


EDIT:  I followed the guide [Here]("http://postfix.state-of-mind.de/patrick.koetter/smtpauth/smtp_auth_mailservers.html")for the sasl_passwd setup

---

### Post by sw34963 on 2009-08-05
Would have installing Horde groupware caused any issues??
:confused:

---

