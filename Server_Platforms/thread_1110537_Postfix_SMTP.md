---
title: "Postfix SMTP"
date: 2009-03-29
forum: Server Platforms
---

### Post by asimons999 on 2009-03-29
Ubuntu 8.10:

So I'm trying to setup smtp so that we can send from locally, but go onto the internet. It doesn't need authentication, but just only accept from our local network. I just get a connection refused message from Thunderbird when trying to send emails. 

my **main.cf**
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

myhostname = dedserver
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = dedserver, localhost.localdomain, , localhost, mail.localdev
relayhost = 
mynetworks = 127.0.0.0/8, 192.168.1.0/20
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
myorigin = /etc/mailname
inet_protocols = all

```

I've been doing dpkg reconfigures, so there was the more default "mynetworks" there originally.

---

### Post by HermanAB on 2009-03-29
If you want to run a real mail server, then you need a proper DNS setup and a static IP address.  If you just want a mail forwarder, then you need to set the relayhost parameter to point to your ISP mail server, but if you do that, you can just as well let Tbird send to the ISP mail server directly.

If you want to run a real mail server, use either Zimbra or Citadel, since it is much easier to install a self contained mail system, than build a system from little pieces of Lego.  Installing Citadel takes about 20 minutes, while configuring Postfix and everything else it needs takes about 2 weeks.

[http://aeronetworks.ca/citadel-howto.html](http://aeronetworks.ca/citadel-howto.html)
[http://aeronetworks.ca/citadel-clients.html](http://aeronetworks.ca/citadel-clients.html)

---

### Post by asimons999 on 2009-03-30
> **HermanAB said:**
> If you want to run a real mail server, then you need a proper DNS setup and a static IP address.

yeah we have a domain, with externally hosted DNS pointing to our server. I'll check out those links

---

### Post by hyper_ch on 2009-03-30
static ip is not required for a real mail server - however highly recommended because you don't have to relay your outgoing mail through another mailserver.

---

