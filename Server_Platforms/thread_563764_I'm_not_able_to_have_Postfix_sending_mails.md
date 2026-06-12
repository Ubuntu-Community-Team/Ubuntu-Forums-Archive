---
title: "I'm not able to have Postfix sending mails"
date: 2007-09-30
forum: Server Platforms
---

### Post by thegeezus on 2007-09-30
Hi,

I'm trying to send a email with postmail running on my server to my gmail address, but I got the following error (I modified the email adresses to avoid spam) :

```

Sep 30 17:44:58 daimyo postfix/master[6522]: daemon started -- version 2.3.8, configuration /etc/postfix
Sep 30 17:44:58 daimyo postfix/qmgr[6526]: 2A11542A3: from=<www-data@stuffedmac.com>, size=819, nrcpt=1 (queue active)
Sep 30 17:45:10 daimyo postfix/smtpd[6530]: connect from unknown[192.168.0.100]
Sep 30 17:45:10 daimyo postfix/smtpd[6530]: NOQUEUE: reject: RCPT from unknown[192.168.0.100]: 554 5.7.1 <marc.@gmail.com>: Relay access denied; from=<marc.@polymtl.ca> to=<marc@gmail.com> proto=ESMTP helo=<[192.168.0.100]>
Sep 30 17:45:10 daimyo postfix/smtpd[6530]: disconnect from unknown[192.168.0.100]

```

I'm sending the mail with my Mac (IP address 192.168.0.100) and I don't know why I get the Relay access denied.


Thanks

---

### Post by HermanAB on 2007-09-30
Your Mac is behind a NAT firewall and has an unroutable private address in the 192.168 range.  Many (most?) public mail servers are configured to reject mail coming from private subnets, since those are almost guaranteed to be spam zombies.  

You have to configure postfix to relay outgoing mail through your ISP mail server using the relayhost setting in main.cf:
[http://www.postfix.org/postconf.5.html](http://www.postfix.org/postconf.5.html)

Cheers,

Herman

---

### Post by Parama on 2007-09-30
This problem could come from missing local networks in the /etc/postfix/main.cf. You should have a line that looks like this:
```
mynetworks = 192.168.0.0/24, 127.0.0.0/8
```

As always it's easier to help with the config files along (leaving out the things you really don't want to show) :)

---

### Post by thegeezus on 2007-09-30
Hi Parama,

I added my local network in mynetwork and the email went out of my Apple Mail mailbox (witch is good), but I didn't receive it. I got the following error :

```

Sep 30 22:33:03 daimyo postfix/smtp[7459]: connect to gmail-smtp-in.l.google.com[66.249.93.27]: No route to host (port 25)
Sep 30 22:33:11 daimyo postfix/smtpd[7463]: connect from unknown[192.168.0.100]
Sep 30 22:33:11 daimyo postfix/smtpd[7463]: 8DC5D1330: client=unknown[192.168.0.100]
Sep 30 22:33:11 daimyo postfix/cleanup[7465]: 8DC5D1330: message-id=<1DBE5B76-F1AC-4BD0-B616-514131648AAA@polymtl.ca>
Sep 30 22:33:11 daimyo postfix/qmgr[7457]: 8DC5D1330: from=<marc@polymtl.ca>, size=1713, nrcpt=1 (queue active)
Sep 30 22:33:24 daimyo postfix/smtp[7462]: connect to smtp3.polymtl.ca[132.207.4.227]: Connection timed out (port 25)
Sep 30 22:33:24 daimyo postfix/smtp[7461]: connect to gmail-smtp-in.l.google.com[66.249.93.27]: Connection timed out (port 25)
Sep 30 22:33:33 daimyo postfix/smtp[7459]: connect to gmail-smtp-in.l.google.com[66.249.93.114]: Connection timed out (port 25)
Sep 30 22:33:41 daimyo postfix/smtp[7466]: connect to gmail-smtp-in.l.google.com[66.249.93.114]: Connection timed out (port 25)

```

So I'll try to forward to my ISP SMTP. This is my current main.cf config file

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

disable_dns_lookup = no
smtp_host_lookup = dns
myhostname = stuffedmac.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = stuffedmac.com, daimyo, localhost.localdomain, localhost
relayhost =                                       
mynetworks = 127.0.0.0/8, 192.168.0.0/24
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

```

So I'll try to find the SMTP from my provider (I'm in sweden currently and I do not speak swedish) and try to do the relay. 

Rgds
TheGeezUs

---

### Post by thegeezus on 2007-09-30
Hi,

It does work great now, I just changed in the /etc/postfix/main.cf the line

relayhost =

to this one (for my provider, Bredband2 in Sweden, the smtp server is smtp.brikks.com) (do not put smtp. ! )

relayhost = brikks.com

And I was able to send the email and receive it sucessfully. It does work with PHP scripts now too. So thanks a lot guys!

Best regards,
TheGeezUs

---

### Post by MJN on 2007-10-01
That ought to be **relayhost = [smtp.brikks.com]**
 
The [] makes Postfix perform an A record lookup for the contents as opposed to an MX record query. You are lucky that your ISPs incoming mail server also serves as an outgoing MTA otherwise your current config would not work.
 
To be on the safe side (against MTA policy changes by your ISP) configure as above with the brackets.
 
Mathew

---

