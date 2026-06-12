---
title: "SMTP server not working"
date: 2011-02-16
forum: Server Platforms
---

### Post by MrNatewood on 2011-02-16
Hello,

We have Ubuntu 8.04 running on our mail server and remote smtp connection does not work.

When trying to send with a client such as Thunderbird it complains about a wrong username\password.

Receiving mail  with IMAP and POP3 works fine through Thunderbird. Both receiving and sending mail through a web interface(horde) works.

I can remotely telnet the server at port 25 and this is the output of ehlo:
```
250-**server address**
250-PIPELINING
250-SIZE 25000000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN


```

Also, the following is the content of /etc/postfix/main.cf
(Whenever there are ***** it's a server address)
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
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = *****
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = *****, *****, localhost, *****, *****
relayhost =
mynetworks = 127.0.0.0/8, *****, *****
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
home_mailbox = Maildir/
message_size_limit = 25000000
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

Can anyone try to help me make SMTP mail sending work?

---

### Post by rudelgurke on 2011-02-16
Did you read [http://www.postfix.org/SASL_README.html](http://www.postfix.org/SASL_README.html) ?

Depends on your IMAP Server, you may use Dovecot's SASL and skip the entire Cyrus part or - if not - setting up Cyrus SASL's backend to authenticate your users.
Additionally checking your logfiles for the errors Postfix will output might help to find the source of the error.

And a note:

```

smtpd_tls_security_level = may
smtpd_tls_auth_only = no

```

Maybe set these to "encrypt" and "yes" to enforce usage of the TLS layer to prevent your clients from sending their auth in plaintext over the net.

And - Horde uses PHP and PHP uses /usr/sbin/sendmail by default. There's no SMTP authentication done, except of course you've manually changed something which I would recommend to prevent anyone from sending Spam over a bad PHP script by abusing the mail() function.

---

### Post by elico on 2011-02-16
try to tail the mail log for more info with the command:

tail -f /var/log/mail.log

while you are trying to login the server.
i think it somekind of sasl problem.

---

### Post by MrNatewood on 2011-02-17
Okay so this is what shows up on the mail.log when trying to send an email:
```
Feb 17 11:09:53 servername postfix/smtpd[24024]: connect from unknown[my.ip]
Feb 17 11:09:53 servername postfix/smtpd[24024]: setting up TLS connection from unknown[my.ip]
Feb 17 11:09:53 servername postfix/smtpd[24024]: Anonymous TLS connection established from unknown[my.ip]: TLSv1 with cipher DHE-RSA-AES256-SHA (256/256 bits)
Feb 17 11:09:53 servername postfix/smtpd[24024]: warning: SASL authentication failure: cannot connect to saslauthd server: No such file or directory
Feb 17 11:09:53 servername postfix/smtpd[24024]: warning: SASL authentication failure: Password verification failed
Feb 17 11:09:53 servername postfix/smtpd[24024]: warning: unknown[my.ip]: SASL PLAIN authentication failed: generic failure
Feb 17 11:09:53 servername postfix/smtpd[24024]: warning: SASL authentication failure: cannot connect to saslauthd server: No such file or directory
Feb 17 11:09:53 servername postfix/smtpd[24024]: warning: unknown[my.ip]: SASL LOGIN authentication failed: generic failure
Feb 17 11:09:56 servername postfix/smtpd[24024]: disconnect from unknown[my.ip]
```

I should note that starting the SASL daemon gives off no warnings or errors.

My IMAP/POP3 server is courier and not dovecot. I am aware horde does not use SMTP, I was just pointing out that sending mail in general does work.

---

### Post by rudelgurke on 2011-02-17
Does saslauthd run ? And is Postfix able to connect to the socket this daemon creates ?
Looks like it can't so you can manually set in Postfix's main.cf where the socket of saslauthd is located by setting smtpd_sasl_path.

---

### Post by MrNatewood on 2011-02-17
I set smtpd_sasl_path in the config file and now I get a different error:

```
warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: Permission denied

```

I tried chmod +r to /erc/sasldb2 but it didn't help.

---

### Post by elico on 2011-02-28
you can you try using the dovecot daemon as your sasl auth aget.
or in howtoforge.com they have a nice manual on installing this thing.
[http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu-10.04](http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu-10.04)

---

