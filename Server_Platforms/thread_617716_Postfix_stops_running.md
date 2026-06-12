---
title: "Postfix stops running"
date: 2007-11-19
forum: Server Platforms
---

### Post by wxman on 2007-11-19
Has anyone had any problems with postfix just stopping working? I've been using monit to see how it works, and everything has been fine for a while now. Today I started to get email notices from monit that it couldn't get post fix to restart. I checked the syslog it it showed it trying to get it started, but no other errors showed up. I disabled monit, tried to restart postfix from a SSH connection, but nothing happens. In fact the syslog doesn't even show me trying to do a restart. I've done nothing to the server to change anything, so I just can't figure out what happened. I tried to do "dpkg-reconfigure postfixdpkg-reconfigure postfix" and it says "postfix is broken or not fully installed".
I also did:
```

telnet localhost 25
ehlo localhost

```

and got:
```

250-server1.tlthost.net Hello localhost.localdomain [127.0.0.1], pleased to meet you
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

```
I noticed "250-STARTTLS" is missing.

Can I reinstall postfix to fix this? Do I have to completely remove it first? If so, what's the trick to remove it without leaving behind something that might just mess it back up?

Thanks.

---

### Post by MJN on 2007-11-20
You'd need to post your Postfix config for us to ascertain what the TLS issue is.
 
As for monit, I've never used it (or even heard of it for that matter), but why is it even attempting to restart Postfix? Your posted output shows Postfix is running so I'd suspect a problem with Monit as oppsoed to Postfix itself.
 
Post the logs (/var/log/mail.log) showing what happens when you attempt to manually restart (and/or stop/start) Postfix.
 
Mathew

---

### Post by HermanAB on 2007-11-20
You can test using telnet:
$ telnet serveripaddress 25

If postfix answers, then it is running.

Cheers,

H.

---

### Post by wxman on 2007-11-20
Hi
Thanks for the replies. I'm running on a local connection on my network. I just tried to stop and start postfix, and both the mail, and the syslog showed nothing. Like I hadn't told it to do anything.

I then tried "telnet localhost 25" and got this:
```

root@server1:/home/admin# telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
220 server1.tlthost.net ESMTP Sendmail 8.13.5.20060308/8.13.5/Debian-3ubuntu1.1; Tue, 20 Nov 2007 19:14:02 -0500; (No UCE/UBE) logging access from: localhost.localdomain(OK)-localhost.localdomain [127.0.0.1]

```

Here's my postfix/main.cf:
```

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

myhostname = mail.tlthost.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.tlthost.net, server1.tlthost.net, localhost.tlthost.net, localhost
relayhost =
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

virtual_maps = hash:/etc/postfix/virtusertable

mydestination = /etc/postfix/local-host-names

```

Monit is just a system monitor that tests the server parts, and reports back if something isn't working. I've disabled it anyway for now at least till I find what went wrong. I did remember that I had just updated spamassassin the night before I found postfix not working. I think that was the only change made. I guess I'm glad this happened now. I was about ready to move our web sites to the new server. I can't do that if the mail server is this unstable. Again thanks for the help.

---

### Post by MJN on 2007-11-21
> **wxman said:**
> ```
220 server1.tlthost.net ESMTP Sendmail 8.13.5.20060308/8.13.5/Debian-3ubuntu1.1; Tue, 20 Nov 2007 19:14:02 -0500; (No UCE/UBE) logging access from: localhost.localdomain(OK)-localhost.localdomain [127.0.0.1]
```
 
...You're running Sendmail, not Postfix! Remove sendmail and start Postfix.
 
The errors relating to Postfix not being able to start will be because port 25 is already in use - this should've been reported in the logs.
 
Mathew
 
P.S. Your telnet output (banner and initial dialogue) differs between your first and last posts - howcome?

---

### Post by wxman on 2007-11-21
> **MJN said:**
> ...You're running Sendmail, not Postfix! Remove sendmail and start Postfix.
 
The errors relating to Postfix not being able to start will be because port 25 is already in use - this should've been reported in the logs.
 
Mathew
 
P.S. Your telnet output (banner and initial dialogue) differs between your first and last posts - howcome?

This is getting crazy. I don't even remember installing sendmail. I went in and did a apt remove, and it still shows it's using port 25. I checked ISPConfig and it says SMTP is running, and using postfix. My logs still show no activity when I start, stop, or restart postfix. I even tried a whole server reboot and it stayed the same.

The difference might be because one was from a remote connection, and the last one was while on the network.

I would just reinstall it as long as that won't mess things up even more.

---

### Post by wxman on 2007-11-21
I got brave and tried:
apt-get install --reinstall postfix

So far it looks like it might be working again.

---

### Post by wxman on 2007-11-21
I think things might be getting back to normal now - I hope. Right off I was getting in the mail log:
```

warning: database /etc/postfix/virtusertable.db is older than source file /etc/postfix/virtusertable

```

I just sent a bunch of tests using SquirrelMail to and from my test site, to my Google mail account. It seem to work just fine and no errors showed up on any logs.

What is odd though, is that I can't seem to get it to work using MS Outlook if I set up an account using the new email settings. But it does work, with the exact same setting, on Outlook Express. I can't complain though. at least I know now that a reinstall will not break the system.

---

### Post by MJN on 2007-11-22
> **wxman said:**
> I think things might be getting back to normal now - I hope. Right off I was getting in the mail log:
```

warning: database /etc/postfix/virtusertable.db is older than source file /etc/postfix/virtusertable

```

Fix that with **sudo postmap /etc/postfix/virtusertable** - all it means is that you've updated the virtusertable plaintext file but the binary version that Postfix uses (.db) hasn't been updated from it.

Mathew

---

