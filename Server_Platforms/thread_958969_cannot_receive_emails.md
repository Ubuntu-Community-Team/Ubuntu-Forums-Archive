---
title: "cannot receive emails"
date: 2008-10-25
forum: Server Platforms
---

### Post by bbmatrix on 2008-10-25
I have ubuntu server 8.04. I have set postfix to use local users for email accounts. example: [email]info@mydomain.loca[/email]l goes to john doe user account. But when I try to receive the emails in a mail client it does not accept john doe's password. The mail is going to the server I checked through Webmin. But I can not receive the mail. I have courier installed.
Thanks

---

### Post by volkswagner on 2008-10-26
You can start by posting /etc/postfix/main.cf

What are you using for authentication?

Check /var/log/mail.log and /var/log/auth.log for any information.  Post any results.

Did you follow any guide or how to, if so which one?

---

### Post by MJN on 2008-10-26
> **volkswagner said:**
> You can start by posting /etc/postfix/main.cfAs the problem is with mail access by the clients it'll be the Courier config that's useful (unfortunately I've never used it so won't be help though!). 

Mathew

---

### Post by bbmatrix on 2008-10-26
Thank you all. Here is my main.cf file:
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

myhostname = server1
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = advancedpcnet.local, server1, localhost.localdomain, localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mydestination = $myhostname, /etc/postfix/virtual/domains
virtual_maps  = hash:/etc/postfix/virtual/addresses

This may be the problem of not receiveing the emails via pop3:
/var/log/mail.log:

.03/0.03/0/0.04, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Oct 25 16:49:00 server1 postfix/qmgr[6542]: 75C6719E26D: removed
Oct 25 16:49:09 server1 pop3d: Connection, ip=[::ffff:192.168.2.2]
Oct 25 16:49:10 server1 pop3d: chdir Maildir: No such file or directory
Oct 25 16:49:19 server1 pop3d: Connection, ip=[::ffff:192.168.2.2]
Oct 25 16:49:19 server1 pop3d: chdir Maildir: No such file or directory
Oct 25 16:49:38 server1 pop3d: Connection, ip=[::ffff:192.168.2.2]
Oct 25 16:49:38 server1 pop3d: chdir Maildir: No such file or directory
Oct 25 16:49:50 server1 pop3d: Connection, ip=[::ffff:192.168.2.2]
Oct 25 16:49:50 server1 pop3d: chdir Maildir: No such file or directory
Oct 25 16:50:14 server1 postfix/smtpd[7180]: disconnect from unknown[192.168.2.2]
Oct 25 16:50:14 server1 pop3d: Connection, ip=[::ffff:192.168.2.2]
Oct 25 16:50:14 server1 pop3d: chdir Maildir: No such file or directory
Oct 25 16:50:18 server1 pop3d: Connection, ip=[::ffff:192.168.2.2]
Oct 25 16:50:20 server1 pop3d: LOGIN FAILED, user=brandon, ip=[::ffff:192.168.2.2]
Oct 25 16:50:25 server1 pop3d: LOGOUT, ip=[::ffff:192.168.2.2]
Oct 25 16:50:25 server1 pop3d: Disconnected, ip=[::ffff:192.168.2.2]

/var/log/auth.log:
Oct 26 06:47:02 server1 CRON[7689]: pam_unix(cron:session): session closed for user root
Oct 26 06:49:38 server1 CRON[7620]: pam_unix(cron:session): session closed for user root
~
Here is the tutorial I used to set up virtual mail with virtual domains with postfix. [http://www.debian-administration.org/articles/243](http://www.debian-administration.org/articles/243)

Like I said before mail goes to the user's account but I cannot receive in a mail client via pop3. I have courier and dovecot should I uninstall one or the other?

---

### Post by bbmatrix on 2008-11-01
Ok I have went back to dovecot and still can't get any mail. It says authentiacation failed. How do I get it to authenticate?

---

