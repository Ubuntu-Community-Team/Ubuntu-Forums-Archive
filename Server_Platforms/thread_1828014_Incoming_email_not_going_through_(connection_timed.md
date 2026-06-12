---
title: "Incoming email not going through (connection timed out on mail server)"
date: 2011-08-18
forum: Server Platforms
---

### Post by MacFr on 2011-08-18
Hi all,

I have been trying to solve this problem for two days now looking at various forums and websites but can't really figure out what's going on here.

I have setup postfix on my ubuntu and I can send emails using "telnet localhost 25" and the ehlo thingy. Apache can also send emails. My problem is with incoming emails. 
When I try to send an email (through Gmail) I get the following error message:

```
Delivery to the following recipient has been delayed:

    root@example.com

Message will be retried for 2 more day(s)

Technical details of temporary failure:
The recipient server did not accept our requests to connect. Learn more at http://mail.google.com/support/bin/answer.py?answer=7720
[mail.example.com. (10): Connection timed out]
```

My postfix conf is as follows:


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

myhostname = example.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = example.com localhost.local localhost.localdomain localhost mail.example.com localhost.$mydomain
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 xxx.255.255.25/24
mailbox_size_limit = 1000000000
recipient_delimiter = +
inet_interfaces = all
myorigin = /etc/mailname
inet_protocols = all
home_mailbox = Maildir/
mailbox_command = 

```

A netstat -an | grep "LISTEN " gives me the following for the SMTP port, showing that postfix is listening on port 25:
```
tcp    0      0   0.0.0.0:25    0.0.0.0:*     LISTEN
tcp    0      0   :::25             :::*              LISTEN
```

iptables does not seem to show any port being blocked.

I have also a MX record for mail.example.com and A and AAAA records for IPv4 and IPv6.

Any idea where the problem is?

Thanks in advance for those who will take time to answer.

Cheers,
M

---

### Post by slugmax on 2011-08-18
The timeout would indicate a port block of some sort. Is this server directly connected to the internet? If so, your ISP may be blocking port 25 inbound. If you have a router/NAT device in between your server and the internet (it does not look that way based on your config, but you don't explicitly say), that may also be the issue. To verify that connections are even making it into your server, you can check your mail log (var/log/mail.log for postfix) and look for lines of the form 'postfix/smtpd[11886]: connect from...'.

---

### Post by MacFr on 2011-08-19
Checking again carefully (with ufw status) it turned out indeed that the port 25 was closed.
A quick ufw command corrected that.

Thanks a lot

---

