---
title: "Postfix  SMTP no response ( no error either)"
date: 2009-06-21
forum: Server Platforms
---

### Post by Stuart1745 on 2009-06-21
ok so I have followed [this]("https://help.ubuntu.com/community/Postfix")guide and how ever when I test the configuration by telnet localhost 25 I get no response, I dont get a connection refused I just dont get any response. now I can send email to an external address, but when I respond to it I get no email and no error is created. here is my postfix config
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

myhostname = mail.pearcerobotics.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = pearcerobotics.com, pearcerobotics.com, robertrampy.com, officeretreat.com, aliensrus.com
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_protocols = all
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
smtp_use_tls = yes
virtual_maps = hash:/etc/postfix/virtusertable
home_mailbox = Maildir/
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/dovecot-auth
smtpd_sasl_authenticated_header = yes
smtpd_sender_restrictions = reject_unknown_sender_domain
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_mandatory_ciphers = medium, high
mailbox_command = 
relayhost = 
inet_interfaces = all

```
I did an nmap to see if smtp was listening and I got this 

```
stuart@Pearcerobotics:~$ nmap localhost

Starting Nmap 4.76 ( http://nmap.org ) at 2009-06-20 23:05 CDT
Interesting ports on localhost (127.0.0.1):
Not shown: 988 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
25/tcp    open  smtp
53/tcp    open  domain
80/tcp    open  http
110/tcp   open  pop3
139/tcp   open  netbios-ssn
143/tcp   open  imap
445/tcp   open  microsoft-ds
993/tcp   open  imaps
995/tcp   open  pop3s
3306/tcp  open  mysql
10000/tcp open  snet-sensor-mgmt

```
that looks normal smtp on port 25 however  I did a net stat and saw that master( how ever I have seen cups and sshd as well) is listening in to port 25
```
stuart@Pearcerobotics:~$ sudo netstat -plntu
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:993             0.0.0.0:*               LISTEN      21116/imap-login
tcp        0      0 0.0.0.0:995             0.0.0.0:*               LISTEN      21028/pop3-login
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN      3045/mysqld
tcp        0      0 127.0.0.1:139           0.0.0.0:*               LISTEN      3852/smbd
tcp        0      0 192.168.0.1:139         0.0.0.0:*               LISTEN      3852/smbd
tcp        0      0 0.0.0.0:110             0.0.0.0:*               LISTEN      21028/pop3-login
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN      21116/imap-login
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN      4827/perl
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      4524/apache2
tcp        0      0 0.0.0.0:53              0.0.0.0:*               LISTEN      2920/dnsmasq
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      20444/sshd
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      19112/master
tcp        0      0 127.0.0.1:445           0.0.0.0:*               LISTEN      3852/smbd
tcp        0      0 192.168.0.1:445         0.0.0.0:*               LISTEN      3852/smbd
tcp6       0      0 :::993                  :::*                    LISTEN      21116/imap-login
tcp6       0      0 :::995                  :::*                    LISTEN      21028/pop3-login
tcp6       0      0 :::110                  :::*                    LISTEN      21028/pop3-login
tcp6       0      0 :::143                  :::*                    LISTEN      21116/imap-login
tcp6       0      0 :::53                   :::*                    LISTEN      2920/dnsmasq
tcp6       0      0 :::22                   :::*                    LISTEN      20444/sshd
tcp6       0      0 :::25                   :::*                    LISTEN      19112/master
udp        0      0 192.168.0.1:137         0.0.0.0:*                           3848/nmbd
udp        0      0 0.0.0.0:137             0.0.0.0:*                           3848/nmbd
udp        0      0 192.168.0.1:138         0.0.0.0:*                           3848/nmbd
udp        0      0 0.0.0.0:138             0.0.0.0:*                           3848/nmbd
udp        0      0 0.0.0.0:10000           0.0.0.0:*                           4827/perl
udp        0      0 0.0.0.0:53              0.0.0.0:*                           2920/dnsmasq
udp        0      0 0.0.0.0:67              0.0.0.0:*                           6053/dhcpd3
udp        0      0 0.0.0.0:68              0.0.0.0:*                           3097/dhclient3
udp        0      0 0.0.0.0:38117           0.0.0.0:*                           4338/avahi-daemon:
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           4338/avahi-daemon:
udp6       0      0 :::53                   :::*                                2920/dnsmasq

```


what am I doing wrong? thank you in advance.

---

### Post by windependence on 2009-06-21
What is in your /var/log/mail.log?

-Tim

---

### Post by Stuart1745 on 2009-06-21
```
Jun 21 08:48:40 Pearcerobotics postfix/master[19112]: warning: /usr/lib/postfix/cleanup: bad command startup -- throttling
Jun 21 08:49:25 Pearcerobotics postfix/smtpd[26030]: fatal: open database /etc/postfix/virtusertable.db: No such file or directory
Jun 21 08:49:26 Pearcerobotics postfix/master[19112]: warning: process /usr/lib/postfix/smtpd pid 26030 exit status 1
Jun 21 08:49:26 Pearcerobotics postfix/master[19112]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Jun 21 08:49:40 Pearcerobotics postfix/cleanup[26035]: fatal: open database /etc/postfix/virtusertable.db: No such file or directory
Jun 21 08:49:41 Pearcerobotics postfix/master[19112]: warning: process /usr/lib/postfix/cleanup pid 26035 exit status 1
Jun 21 08:49:41 Pearcerobotics postfix/master[19112]: warning: /usr/lib/postfix/cleanup: bad command startup -- throttling
Jun 21 08:50:26 Pearcerobotics postfix/smtpd[26226]: fatal: open database /etc/postfix/virtusertable.db: No such file or directory
Jun 21 08:50:27 Pearcerobotics postfix/master[19112]: warning: process /usr/lib/postfix/smtpd pid 26226 exit status 1
Jun 21 08:50:27 Pearcerobotics postfix/master[19112]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling

```

looks like there is a lot of bad things going on in there

---

### Post by Stuart1745 on 2009-06-21
ok I followed [this]("http://www.mailinglistarchive.com/postfix-users@postfix.org/msg37786.html") mailing list archive

and issue was solved. I was not using virtual users.

in short this command fixed the issue.
```
sudo touch /etc/postfix/virtusertable
sudo postmap /etc/postfix/virtusertable

```

---

### Post by windependence on 2009-06-22
This is exactly what I was going to suggest. Good job finding the answer. In case you're not sure what you did, you just created the database file it couldn't find with the touch command and then told postfix where it was. Simple eh?

-Tim

---

