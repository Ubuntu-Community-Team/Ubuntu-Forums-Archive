---
title: "Problem with postfix/postmap.  Any help?"
date: 2009-04-12
forum: Server Platforms
---

### Post by qaylin on 2009-04-12
Hi, I'm running ubuntu 8.10.  I'm having a problem with postfix delivering mail to a local user on my server.  The first user I setup during installation gets mail fine, but everytime I add a user its gives me errors when trying to deliever mail.  

Here is my main.cf
```

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

mydomain = okwellwhatevernevermind.com 
myhostname = server.okwellwhatevernevermind.com 
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = 127.0.0.1, localhost.localdomain, localhost, server.okwellwhatevernevermind.com, mail.okwellwhatevernevermind.com, okwellwhatevernevermind.com 
relayhost = mail.cableone.net 
mynetworks = 192.168.0.0/16, 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = 
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
home_mailbox = Maildir/

```

So I setup a random user (ex. Nmfzm7As).  And I

```
makemaildir Nmfzm7As
```

It makes the Maildir fine in the users home directory.  Here is my aliases file.
```

root@server:/etc# cat /etc/aliases
postmaster:	root
nmfzm7as: 	Nmfzm7As

```
But I get errors everytime I try to run postmap on it.
```

root@server:/etc# postmap aliases
postmap: warning: aliases, line 1: record is in "key: value" format; is this an alias file?
postmap: warning: aliases, line 2: record is in "key: value" format; is this an alias file?

root@server:/etc# /etc/init.d/postfix restart
 * Stopping Postfix Mail Transport Agent postfix                         [ OK ] 
 * Starting Postfix Mail Transport Agent postfix                         [ OK ] 

```

So I try to send an email from my gmail account to the user.  Here is what my log file says.
```

Apr 12 15:04:06 server postfix/master[19986]: daemon started -- version 2.5.5, configuration /etc/postfix
Apr 12 15:05:05 server postfix/smtpd[19994]: connect from mail-fx0-f178.google.com[209.85.220.178]
Apr 12 15:05:06 server postfix/smtpd[19994]: NOQUEUE: reject: RCPT from mail-fx0-f178.google.com[209.85.220.178]: 550 5.1.1 <nmfzm7as@okwellwhatevernevermind.com>: Recipient address rejected: User unknown in local recipient table; from=<cahlen@gmail.com> to=<nmfzm7as@okwellwhatevernevermind.com> proto=ESMTP helo=<mail-fx0-f178.google.com>
Apr 12 15:05:06 server postfix/smtpd[19994]: disconnect from mail-fx0-f178.google.com[209.85.220.178]

```

Any help on this?  I've been searching and troubleshooting and modding config files for about 10 hours to no avail.

Thanks.

---

### Post by dannyboy1121 on 2009-04-12
Hi there. Out of curiosity - why are you adding this new user to the aliases list? Have you tried postalias rather than postmap? 

By way of comparison (using Postfix and Dovecot) - I've created a standard template for my maildir structure. When I create a new local user through useradd procedure - I then cp the template Maildir in to the /home/newuser and then chmod permissions.

Job done. Works without issue for me anyway.

---

### Post by qaylin on 2009-04-12
I tried to create the alias because I was having such a problem for such a long time.  I know I don't even need the alias because I just want it to deliver to a local user but so far no good.

I have the mail directory structure in place.  It looks exactly the same as the structure for the user 'cahlen' which I can recieve mail on.  And the permissions are correct.

For some reason though, the newuser I add cannot recieve mail.  Strangest thing.

The problem is the 'unkown user in local recipient table'.  And how/what do I edit to show that there IS a local recipient?

---

### Post by hyper_ch on 2009-04-12
(1) take out that aliases thing

(2) add
```

virtual_maps = hash:/etc/postfix/virtual

```

(3) make entries like
```

postmaster	root
nmfzm7as 	Nmfzm7As

```

(4) run
```

postmap /etc/postfix/virtual

```

(5) restart postfix

---

