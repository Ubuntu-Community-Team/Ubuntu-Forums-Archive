---
title: "Postfix relay behind firewall"
date: 2011-01-09
forum: Server Platforms
---

### Post by isiman on 2011-01-09
Hello,
I have installed Postfix under Ubunutu Server 10.04 and can telnet into postfix, send an email to myself which I can see is relayed through to our exchange server (using tail -f /var/log/mail.log) and then is received by my email client.
This is all on the local network.
We have a Snap Gear which is the border between the internet and our local network with port 25 inbound forwarded to the Ubuntu/Postfix server, however no mail comes through to this server (again, using tail -f /var/log/mail.log to view) that I can see.

I do not know if it is the Snap Gear which is blocking this, or the Ubuntu/Postfix pair which is stopping it.

Network looks like this:

Snap Gear (with public IP and private IP) --> Ubuntu/Postfix (with internal IP of 10.0.0.4) --> Exchange Server (with internal IP of 10.0.0.99)

For this setup, we are only wanting to receive mail through the Postfix server (as an anti spam gateway), sending is done through the exchange server directly.

I have looked around online for this, however all that is stated is to remove 
```
#relayhost = [firewall.example.com]
•Line 3: IMPORTANT: do not specify a relayhost in main.cf. 
```
([http://www.postfix.org/STANDARD_CONFIGURATION_README.html#intranet](http://www.postfix.org/STANDARD_CONFIGURATION_README.html#intranet))
however I would think I need that as I am relaying to an internal server.

My Postfix main.cf is below:

```

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
append_dot_mydomain = no
readme_directory = no

smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

mydomain = ****.com.au
myhostname = ****.com.au
myorigin = $mydomain

mydestination =
relayhost = 10.0.0.99
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 10.0.0.0/24
#mailbox_command = procmail -a "$EXTENSION"
#mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
#mynetwork_style = host
append_at_myorigin = no

#relay_recipient_maps = hash:/etc/postfix/relay_recipients
#show_user_unknown_table_name = no

local_recipient_maps =
# Timers:
smtpd_error_sleep_time = 1s
smtpd_soft_error_limit = 10
smtpd_hard_error_limit = 20
```

Could anyone point me in the right direction?

---

### Post by elico on 2011-01-10
take a look at the TCPDUMP output when yyou are gettign mail.
if it's only for spam and stuff then you should add amavis and other stuff.

---

### Post by isiman on 2011-01-12
FIXED!

Snapgears apparently do more than just enable NAT - they have more port forwarding options there, along with the packet filtering tab.

---

