---
title: "Postfix no route to host"
date: 2012-05-07
forum: Server Platforms
---

### Post by and1hotsauce on 2012-05-07
Hello All,

I've installed our new server under Ubuntu 11.10. I've installed postfix (according to the docs [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)).

Sending emails from our server is OK for most of destinations. But for some destinations i got a "No route to host".

```
server:~$ mailq
-Queue ID- --Size-- ----Arrival Time---- -Sender/Recipient-------
0C5F79A390     6592 Thu May  3 10:13:52  ****@sender.com
       (connect to asp-mxa.belnet.be[2001:6a8:3c80::155]:25: No route to host)
                                         ***@receiver.com
```

I don't know why i can't send emails to this one (with our previous server on Freebsd, not configured by me, all went ok). Someone can help me ? 

Thanks ! ;-)

Here are some commands that i've read on the french and english ubuntu forums that can help.

I can ping the domain "asp-mxa.belnet.be"
```
server:~$ ping asp-mxa.belnet.be
PING asp-mxa.belnet.be (193.190.198.178) 56(84) bytes of data.
64 bytes from asp-mxa.belnet.be (193.190.198.178): icmp_req=1 ttl=59 time=7.31 ms
64 bytes from asp-mxa.belnet.be (193.190.198.178): icmp_req=2 ttl=59 time=7.46 ms
64 bytes from asp-mxa.belnet.be (193.190.198.178): icmp_req=3 ttl=59 time=7.35 ms
```

I can also connect to it using telnet on port 25
```
server:~$ telnet asp-mxa.belnet.be 25
Trying 193.190.198.178...
Connected to asp-mxa.belnet.be.
Escape character is '^]'.
220 asp-scan3.belnet.be ESMTP CanIt-Appliance
HELO asp-mxa.belnet.be
250 asp-scan3.belnet.be Hello ******.ovh.net [***.**.***.***], pleased to meet you
```

Here is the result of the command "postconf -n" :
```
server:~$ postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = all
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
mydestination = mail2.****.eu, ****.eu, ****.ovh.net, localhost.ovh.net, localhost
myhostname = *****.eu
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost = 
smtp_tls_note_starttls_offer = yes
smtp_tls_security_level = may
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = 
smtpd_sasl_security_options = noanonymous
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
```

Here is my resolv.conf:
```
server:~$ sudo cat /etc/resolv.conf
[sudo] password for ****: 
nameserver 127.0.0.1
nameserver 213.186.33.99
search ovh.net
```

Here is a tracroute to asp-mxa-belnet.be
```
server:~$ sudo traceroute -T -p 25 asp-mxa.belnet.be
traceroute to asp-mxa.belnet.be (193.190.198.178), 30 hops max, 60 byte packets
 1  vss-5a-6k.fr.eu (176.31.245.253)  0.760 ms * *
 2  rbx-g2-a9.fr.eu (178.33.100.70)  1.856 ms  1.865 ms  1.861 ms
 3  bru-1-6k.be.eu (94.23.122.138)  2.707 ms  2.708 ms  2.702 ms
 4  10ge.cr2.brueve.belnet.net (194.53.172.65)  6.442 ms  6.153 ms  6.132 ms
 5  10ge.cr1.brueve.belnet.net (193.191.16.21)  6.104 ms  6.119 ms  6.118 ms
 6  belnetlan.cr1.brueve.belnet.net (193.191.2.30)  6.358 ms  6.222 ms  6.299 ms
 7  asp-mxa.belnet.be (193.190.198.178)  7.270 ms  7.280 ms  7.082 ms
```

---

### Post by SeijiSensei on 2012-05-07
> (connect to asp-mxa.belnet.be[2001:6a8:3c80::155]:25: No route to host)

It looks like it's using the IPv6 address to reach this host.  I have no idea why that would be.  You could fix the problem by creating an entry in /etc/hosts for that machines IPv4 address.

---

### Post by elico on 2012-05-07
or to disable the ipv6 stack
or to config ipv6 stack\routing correctly.

are you using ipv6 on the machine?

---

