---
title: "Postfix can send email but is unable to recive it"
date: 2017-09-15
forum: Server Platforms
---

### Post by bobooo5 on 2017-09-15
Hi there,

My email server is not receiving email also the email that I am able to send ends up in spam in most accounts (Gmail, Outlook) 

Below is my main.cf file, Can some on will a little more experience help


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


smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = hoskin.online
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = $myhostname, hoskin.online, ubuntu, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/
mailbox_command =
smtpd_recipient_restrictions =
        permit_sasl_authenticated,
#       permit_mynetworks,
        reject_unauth_destination


smtpd_helo_required = yes
smtpd_helo_restrictions =
        permit_mynetworks,
        permit_sasl_authenticated,
        reject_invalid_helo_hostname,
        reject_non_fqdn_helo_hostname,
        reject_unknown_helo_hostname,
        check_helo_access hash:/etc/postfix/helo_access


smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_sasl_auth_enable = yes



```

Any help is much appreciated :D

---

### Post by lisati on 2017-09-15
Does Postfix "see" and process emails you send to it on your network? 

If you want to receive email from outside your network, you will need to open up access to the outside world, usually by redirecting port 25 on your public IP to your server. **Important:** it is essential that if you do this, you make sure that you have some protection against being used as a relay and against receiving spam - what I see in your main.cf file for smtpd_recipient_restrictions and smtpd_helo_restrictions is a good start.

---

### Post by bobooo5 on 2017-09-16
I have opened up port 25 (port forwarding) on my router, For the mail to redirected there will I have to edit the DNS Managment. if so what records would I have to create.

Thank you for your help

---

### Post by CharlesA on 2017-09-16
Please note: Postfix can only send mail, if you wish to receive it as well, you need to use Dovecot or a similar service.

---

### Post by levulamweb on 2017-09-19
Postfix can only send amil, using Dovecot to getting your mail on local inbox. :D

---

### Post by SeijiSensei on 2017-09-19
1)  Does your ISP allow incoming mail?

2)  What do you see in /var/log/mail.log when a message is sent?  Does postfix record its arrival?  

There are many reasons why mail may not arrive.  Without seeing logs it's pretty much impossible to determine which alternatives are plausible.

---

### Post by bobooo5 on 2017-09-22
```
Sep 22 22:17:11 hoskin postfix[2113]: Postfix is running with backwards-compatible default settings
Sep 22 22:17:11 hoskin postfix[2113]: See http://www.postfix.org/COMPATIBILITY_README.html for details
Sep 22 22:17:11 hoskin postfix[2113]: To disable backwards compatibility use "postconf compatibility_level=2" and "postfix reload"
Sep 22 22:17:11 hoskin postfix/master[2156]: daemon started -- version 3.1.0, configuration /etc/postfix
Sep 22 22:18:48 hoskin postfix/smtpd[4035]: connect from mail-lf0-f51.google.com[209.85.215.51]
Sep 22 22:18:48 hoskin postfix/smtpd[4035]: warning: SASL: Connect to private/auth failed: No such file or directory
Sep 22 22:18:48 hoskin postfix/smtpd[4035]: fatal: no SASL authentication mechanisms
Sep 22 22:18:49 hoskin postfix/master[2156]: warning: process /usr/lib/postfix/sbin/smtpd pid 4035 exit status 1
Sep 22 22:18:49 hoskin postfix/master[2156]: warning: /usr/lib/postfix/sbin/smtpd: bad command startup -- throttling

```
This is what I get in the log when I boot the server and tried to myself an email from external provider, Is this any help

---

### Post by CharlesA on 2017-09-22
Do you have Dovecot up and running? That is what should be providing your SASL authentication mechanism.

---

### Post by bobooo5 on 2017-09-23
This what I get in the terminal when I use "systemctl status dovecot.socket"

```
&#9679; dovecot.socket - Dovecot IMAP/POP3 email server activation socket   Loaded: loaded (/lib/systemd/system/dovecot.socket; disabled; vendor preset: enabled)
   Active: inactive (dead)
   Listen: 0.0.0.0:143 (Stream)
           [::]:143 (Stream)
           0.0.0.0:993 (Stream)
           [::]:993 (Stream)


Sep 22 22:54:53 hoskin.online systemd[1]: Closed Dovecot IMAP/POP3 email server activation socket.
Sep 22 22:55:09 hoskin.online systemd[1]: Listening on Dovecot IMAP/POP3 email server activation socket.
Sep 22 22:56:34 hoskin.online systemd[1]: Closed Dovecot IMAP/POP3 email server activation socket.
Sep 22 22:56:35 hoskin.online systemd[1]: Closed Dovecot IMAP/POP3 email server activation socket.
Sep 22 23:01:16 hoskin.online systemd[1]: dovecot.socket: Socket service dovecot.service already active, refusing.
Sep 22 23:01:16 hoskin.online systemd[1]: Failed to listen on Dovecot IMAP/POP3 email server activation socket.



```

---

