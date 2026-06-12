---
title: "Postfix/Dovecot -- Cannot send email from within a Client (i.e. Thunderbird, Outlook)"
date: 2012-04-02
forum: Server Platforms
---

### Post by amycjgrace on 2012-04-02
I recently made a new Ubuntu 11.04 LTS server after my Ubuntu 8.10 server bit the dust. As I recall, the most difficult thing to set up on the original server was smtp-authentication so I could send emails using an email client such as Thunderbird, Outlook, or my iPhone. It took me forever to figure out. Now, with the new server, I'm having the same issue. I'm using the standard installation of Dovecot-Postfix and set those up along with the installation of Ubuntu 11.04. I did setup using internet site using my domain name. I receive email perfectly fine, and can send email using a web interface with a setup SquirelMail site. My errors occur when I attempt to send (I have no issue receiving) emails from my iPhone, Thunderbird, or other outside client. I put in my username and password as always, and receive an error that SMTP authentication fails. I've tried entering my username and password both just the username and username with .domain, but neither works. I'm using the same Thunderbird setup as with the older Ubuntu 8.10 server (albeit with updated security certificates), yet cannot get passed this error. My questions are these:[LIST=1]Which software is my problem with (Dovecot or Postfix)? [*]How do I fix the SMTP authentication error?
[/LIST] 
I've attached my main.cf file information below:
> # See /usr/share/postfix/main.cf.dist for a commented, more complete version


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
smtpd_tls_cert_file = /etc/postfix/ssl/mail.crt
smtpd_tls_key_file = /etc/postfix/ssl/mail.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = gracefam.net
alias_maps = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = gracefam.net, claytonserver.gracefam.net, localhost.gracefam.net, localhost, oremrx.com, mysweetweb.com, oswaldnet.com, homemakeoveraf.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.0.0/24
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
smtpd_recipient_restrictions = permit_mynetworks reject_unauth_destination permit_sasl_authenticated
broken_sasl_auth_clients = yes
smtpd_sasl_auth_enable = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem

Any help anyone can give will be greatly appreciated. I'm sure it's something simple, just allowing my noobness show. Thanks.

---

### Post by webservervideos on 2012-04-02
most isps bock port 25, you need o mke sure u use a diff port on both ends

---

### Post by amycjgrace on 2012-04-02
Sorry. I meant to mention that port 25 is open. I was going to, but failed to. It worked fine with my old Ubuntu 8.10 server (just 2 days ago). I just ran a telnet test, and it's open.

---

