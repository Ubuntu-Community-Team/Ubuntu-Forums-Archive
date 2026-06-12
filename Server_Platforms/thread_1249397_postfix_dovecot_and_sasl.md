---
title: "postfix dovecot and sasl"
date: 2009-08-25
forum: Server Platforms
---

### Post by scottybwoy on 2009-08-25
Hi Ubuntarians,

I have finally had enough of the ever resource hungry Microsoft SBS and Exchange mail server and I have decided to join the Ubuntu Server camp.  Please bare with my lack of understanding of both Ubuntu and much of the gubbins behind Mail Servers.

First I'd like to ask if I'm heading in the right direction.  Here's where I left off.

We have one file server (Win Adv Business Server 2000! lol) that has Active Directory integration with the client machines and the Exchange Server.

What I would like is to replace the Exchange Server with an Ubuntu Mail Server.

So far I have the Ubuntu Server integrating with Active Directory using Kerberos authentication and am now trying to set up the Mail Server.  Postfix and Dovecot are installed and running, but I'm having trouble getting SASL authentication mode running.

I'm quite new to this so I'm not even sure if thats what I need so please inform me if I'm wrong.

I'm using this [https://help.ubuntu.com/community/PostfixDovecotSASL](https://help.ubuntu.com/community/PostfixDovecotSASL) HowTo, and when I test it via Telnet, I only recieve a "220 mail.mri.local ESMTP Postfix (Ubuntu)" message and no "250-AUTH PLAIN LOGIN" message.

I tried having a look in "/var/spool/postfix/private/auth-client" file, but it doesn't let me, so I don't know where else to look.  I've folled all the instructions and checked them over a few times, but no joy.

Any help would be great, thanks.

---

### Post by scottybwoy on 2009-08-26
Still having trouble with this, here is my /etc/postfix/main.cf file.
```
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# SASL parameters
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth-client
smtpd_sasl_auth_enable = yes

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.mri.local
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
local_recipient_maps =
mydestination =
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mynetworks_style = host

delay_warning_time = 4h
unknown_local_recipient_reject_code = 450
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
smtp_helo_timeout = 60s
smtpd_soft_error_limit = 3
smtpd_hard_error_limit = 12

smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hos$
smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_s$
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_clie$
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_sasl_authentica$

smtpd_helo_required = yes
smtpd_delay_reject = yes
disable_vrfy_command = yes


```

What I would like to know is why the test failed to show 250 SASL line when connecting via telnet?  Even though I followed the example, I don't know where the thing thats stopping it could come from.

---

### Post by prshah on 2009-08-26
> **scottybwoy said:**
> but I'm having trouble getting SASL authentication mode running.

During installation of SASL authentication, did you notice this message and follow it?> To enable saslauthd, edit /etc/default/saslauthd and set START=yes

If not, you need to do that.

---

### Post by scottybwoy on 2009-08-26
cheers PRShah,

No I didn't see that notice, also I don't have that file.  Shall I create it or does that mean I don't have something installed.

I'm using Ubuntu Server 8.10 with postfix MTA and dovecot IMAP and am using Kerberos encryption for connecting to the Active Directory.

What else is required at this point?  Shall I just create the file "/etc/default/saslauthd" and put "START=yes" in it?

Thanks for your help.

---

### Post by TheFuturian on 2009-08-27
Hi There,

I seem to be having the same problem with Server 8.04.3 in that the 'auth-client' file is not where the serverguide specifies. I have been following this guide:-

[https://help.ubuntu.com/8.04/serverguide/C/postfix.html](https://help.ubuntu.com/8.04/serverguide/C/postfix.html)

I know the file isn't there as I've checked using a sudo'd Nautilus. I am only using the dovecot-common and dovecot-imapd packages as I do not wish to have POP support, not sure if this is relevant to the problem?

I am really keen to get a SMTP over TLS server configured and appreciate any guidance.

---

### Post by TheFuturian on 2009-08-27
I believe I have found my solution by following this guide:-

[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p5]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p5")

_My Postfix 'Main.cf':-_
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
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = localhost.localdomain.local
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = localhostname.localdomain.local, localhost.localdomain.local, , localhost
relayhost = 
mynetworks = 127.0.0.0/8
#mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
#inet_protocols = all
home_mailbox = Maildir/
#smtpd_sasl_type = dovecot
#smtpd_sasl_path = private/auth-client
smtpd_sasl_local_domain = 
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
#smtpd_sasl_authenticated_header = yes
#smtpd_sasl_auth_enable = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

```

_Telnet Session_
```
admin@Ubuntu-LTS:/etc/default$ telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 localhost.localdomain.local ESMTP Postfix (Ubuntu)
ehlo localhost
250-localhost.localdomain.local
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
```

---

### Post by prshah on 2009-08-28
> **scottybwoy said:**
> Shall I just create the file "/etc/default/saslauthd" and put "START=yes" in it?


> **TheFuturian said:**
> I know the file isn't there as I've checked using a sudo'd Nautilus. 

If the file is not present, then you have not installed the sasl related packages. The correct packages to be installed are mentioned in the guide linked in the previous post.

---

### Post by sh1ny on 2009-08-28
> **prshah said:**
> If the file is not present, then you have not installed the sasl related packages. The correct packages to be installed are mentioned in the guide linked in the previous post.

Please, do not mislead people. When using dovecot's sasl mech you don't need to install cyrus-sasl or sasl2-bin or start the saslauthd daemon or any of that stuff.

---

### Post by prshah on 2009-08-28
> **sh1ny said:**
> When using dovecot's sasl mech you don't need to install cyrus-sasl or sasl2-bin or start the saslauthd daemon or any of that stuff.

Dunno about Dovecot, but you do need it for postfix if you are using postfix as the mail delivery agent.

---

### Post by sh1ny on 2009-08-28
> **prshah said:**
> Dunno about Dovecot, but you do need it for postfix if you are using postfix as the mail delivery agent.

Wrong again. Read some docs. Dovecot has a built-in sasl authentication and you can use it directly instead of saslauthd for postfix.

[http://wiki.dovecot.org/]("http://wiki.dovecot.org/")

I'll leave you to read it up :)

---

### Post by TheFuturian on 2009-09-07
Although the solution I posted has allowed me to connect to my postfix server using SSL I have noticed that my telnet session is missing the '250-AUTH LOGIN PLAIN' line. I am concerned as my e-mail clients do not allow authentication to be used when connecting to send outbound mail. I am attempting to change from the cyrus to the dovecot sasl mechanism, however keep having problems as I believe the following line is wrong in my '/etc/postfix/main.cf':-

```
smtpd_sasl_path = private/auth-client
```

These entries in /var/log/mail.log further advocates that this is the line causing problems:-

```
Sep  7 12:33:35 Ubuntu-VM-LTS postfix/smtpd[31775]: warning: SASL: Connect to private/auth-client failed: No such file or directory
Sep  7 12:33:35 Ubuntu-VM-LTS postfix/smtpd[31775]: fatal: no SASL authentication mechanisms
Sep  7 12:33:36 Ubuntu-VM-LTS postfix/master[27218]: warning: process /usr/lib/postfix/smtpd pid 31775 exit status 1
Sep  7 12:33:36 Ubuntu-VM-LTS postfix/master[27218]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
```

Google isn't playing fair with the 'auth-client' search strings I'm putting in, starting to get frustrating.. ](*,)

---

### Post by tacom6 on 2010-06-14
> **TheFuturian said:**
> Although the solution I posted has allowed me to connect to my postfix server using SSL I have noticed that my telnet session is missing the '250-AUTH LOGIN PLAIN' line. I am concerned as my e-mail clients do not allow authentication to be used when connecting to send outbound mail. I am attempting to change from the cyrus to the dovecot sasl mechanism, however keep having problems as I believe the following line is wrong in my '/etc/postfix/main.cf':-

```
smtpd_sasl_path = private/auth-client
```

These entries in /var/log/mail.log further advocates that this is the line causing problems:-

```
Sep  7 12:33:35 Ubuntu-VM-LTS postfix/smtpd[31775]: warning: SASL: Connect to private/auth-client failed: No such file or directory
Sep  7 12:33:35 Ubuntu-VM-LTS postfix/smtpd[31775]: fatal: no SASL authentication mechanisms
Sep  7 12:33:36 Ubuntu-VM-LTS postfix/master[27218]: warning: process /usr/lib/postfix/smtpd pid 31775 exit status 1
Sep  7 12:33:36 Ubuntu-VM-LTS postfix/master[27218]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
```

Google isn't playing fair with the 'auth-client' search strings I'm putting in, starting to get frustrating.. ](*,)

[http://wiki.dovecot.org/HowTo/PostfixAndDovecotSASL](http://wiki.dovecot.org/HowTo/PostfixAndDovecotSASL)

private/auth

---

