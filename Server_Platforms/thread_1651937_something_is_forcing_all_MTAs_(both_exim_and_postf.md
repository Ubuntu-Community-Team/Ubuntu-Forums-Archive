---
title: "*something* is forcing all MTAs (both exim and postfix) to ignore from addresses"
date: 2010-12-23
forum: Server Platforms
---

### Post by ritontor on 2010-12-23
The description above pretty much says it all. I've tried both Exim and Postfix, and both MTAs are ignoring the from: address while sending mail. I've removed and purged both MTAs, reinstalled, and they still do the same thing. I can't find anything in /etc that could be causing it, there's no mail.rc, is there some sort of magical system setting that forces Ubuntu to ignore the from address and use the local user's address instead? This is making me crazy, and when I find out the person responsible for writing the code that has caused this problem, I am going to send them a very stern email.

---

### Post by elico on 2010-12-24
can you post the config files for the postfix and also your hosts file?

---

### Post by ritontor on 2011-01-03
Names change to protect the innocent

Hosts file: 

```

root@cop-drupal-01:/home/jeremy# less /etc/hosts
127.0.0.1       localhost
my.ip.address     cop-drupal-01.my.domain   cop-drupal-01

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```


main.cf

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

myhostname = cop-drupal-01.my.domain
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = my.domain, cop-drupal-01.my.domain, localhost.my.domain, localhost
relayhost = my.local.network.relay.host
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = loopback-only

```

It's firing emails off to the relay host just fine, it's just rewriting or ignoring or whatevering the from address, and using a local unix version of it instead. I can't for the life of me understand why!

---

### Post by ritontor on 2011-01-03
Ok, don't bother with this one, the server has been rooted. No idea how, but it would seem default 10.4 is remotely exploitable.

---

