---
title: "Postfix email hell."
date: 2018-08-17
forum: Server Platforms
---

### Post by dchurch24 on 2018-08-17
Hi all,

I'm currently in my 8th hour of continuously trying to configure Postfix/Dovecot etc... to be able to send and receive mail.

I can send mail now, although the sent mail never goes to the "sent" folder. Not all that worried about that at this stage.

I cannot receive mail. I can see it in the mail.log : 

```

Aug 17 14:10:24 guido postfix/qmgr[21691]: 281D380B8D: from=<David@ffx.co.uk>, size=5255, nrcpt=1 (queue active)
Aug 17 14:10:24 guido postfix/local[23121]: 281D380B8D: to=<dave@fifthcontinentescape.co.uk>, relay=local, delay=0.24, delays=0.23/0.01/0/0, dsn=2.0.0, status=sent (delivered to mailbox)
Aug 17 14:10:24 guido postfix/qmgr[21691]: 281D380B8D: removed


```

...but it never appears in the inbox or in cur/new/tmp in ~/Maildir.

I've tried multiple variations on smtpd_client_restrictions, and the only one that allows me to actually get this far is to remove it completely from main.cf.

I'm at the point of giving up. I've searched for alternatives, but finding them in forums, they appear to bring their own problems with them as well.

I also tried to get SquirrelMail up and running, but that was a complete disaster, so have left it and am simply trying to connect with Thunderbird now.

My main.cf:

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

# See http://www.postfix.org/COMPATIBILITY_README.html -- default to 2 on
# fresh installs.
compatibility_level = 2

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

#smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
#smtpd_client_restrictions = check_client_access hash:/etc/postfix/trusted_servers
#smtpd_client_restrictions=permit_sasl_authenticated,reject
myhostname = guido.default.dchurch24.uk0.bigv.io
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = $myhostname, xx.xxx.xxx.xxx, localhost, fifthxxxx.co.uk
relayhost =
mynetworks = x.x.x.x, y.y.y.y, 192.168.0.0/24, 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all


```

I've tried several solutions that I've found via google, but nothing seems to change it. I've been advised to update the MX record to *nothing*, which I've done...didn't seem to make any difference at all.

Can anyone shed any light on this?

I've asked a sys-admin friend, and he simply sighed and said, "yeah, email on linux is a nightmare".

---

### Post by TheFu on 2018-08-17
What OS?

Being an open relay will get your IP banned, if it isn't already.  Nobody will accept email from banned IPs, so you should strive NEVER to be an open relay.  There are websites that will test postfix for that and other problems for free.

I can't tell your level of expertise. Too hard to help without that bit of information. Should we be checking trivial problems with understanding SMTP/IMAP or something else?
Have you been running email servers for decades or is this your first attempt?  Do you understand SMTP &  IMAP differences?  Do you want email to work on the internet or just internally?  Did you address firewall and router settings?  Which ports have you setup for SMTP, POP3 and IMAP access for server-to-server and client-to-server connections?

That hostname looks really funny, BTW.  There are other inconsistencies in the IPs, hostname, and domains in the postfix conf file and current DNS records. Is that intentional or is a convoluted setup the goal?

Output from this:
```
$ postconf -n
```
would be helpful if you are seeing postfix issues in the logs.  Don't be an open relay.

 Not having an MX record is a total failure if you expect internet email to work.  The MX record is used both by senders and receivers for anti-spam uses.  A reverse DNS record is best, though not mandatory. Many email servers will reject email from servers without proper reverse DNS setups.

Dovecot  is where I'd concentrate for issues, though I haven't used dovecot in over a decade. So I won't be any help there.

There is a "perfect server" guide on howtoforge for 16.04. If you follow that for the email stuff, you should be fine. I wouldn't use 18.04 at this point and I definitely wouldn't have any desktop anything on a mail server. IMHO.

---

