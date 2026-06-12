---
title: "Postfix relay problem"
date: 2008-10-12
forum: Server Platforms
---

### Post by Aeros84 on 2008-10-12
I set up my Ubuntu server to run the Postfix for SMTP, mainly as an SMTP relay. In other words, the PC's on the LAN can specify the Ubuntu box's IP as their SMTP server, and the server in turn relays the mails via the ISP's relayhost to wherever they need to go.

This works fine when sending mail from a LAN PC. The problem comes in, however, when I try to send a mail from the Ubuntu pc itself (which I have to do for server reports that have to go to external addresses, etc). Since the hostname and domain of the Ubuntu box are custom (as in, they don't really exist on the WWW), the ISP's smtp server rejects all mails coming from that box.

Here is what I have in my main.cf:

```

append_dot_mydomain = no

smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

myhostname = miranda
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = miranda, localhost.localdomain, localhost
relayhost = SMTP.OF.MY.ISP.HERE
mynetworks = 127.0.0.0/8, 10.0.0.0/24
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = 127.0.0.1, 10.0.0.1

home_mailbox = Maildir/

```

"Miranda" is the name of the server.

Not that it matters, but the Ubuntu has two ethernet interfaces. eth0 goes to the ADSL router, and has IP 192.168.0.1. eth1 goes to the LAN, and has IP 10.0.0.1.

I assume I have to somehow masquerade all mails coming from the Ubuntu server directly as an existing email address. Or something. I thought of changing "myhostname" to myisp.com, but obviously that won't do, least of all because mails sent from the Ubuntu root would appear to come from [email]root@myisp.com[/email].. which is definitely a Bad Idea (TM). So, I don't know.

Can anyone advise?

---

### Post by skunkbad on 2008-10-12
myhostname needs to be a FQDN

---

### Post by Aeros84 on 2008-10-13
Yes, I figured :) But what would qualify as a FQDN when the domain doesn't actually exist, as in, the server is completely local?

---

