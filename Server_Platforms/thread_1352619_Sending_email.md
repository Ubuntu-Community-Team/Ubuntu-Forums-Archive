---
title: "Sending email"
date: 2009-12-11
forum: Server Platforms
---

### Post by mykelm03 on 2009-12-11
got my postfix working at our office. sending and receiving is not a problem, but when im in travel or at home, sending is my biggest problem. i still need to connect to our vpn just to send email. what seems to be the problem? pls help me... thanks..:(****

---

### Post by volkswagner on 2009-12-12
I think you are needing secure authentication outside your LAN.  This [thread]("http://ubuntuforums.org/showthread.php?t=990582&highlight=saslauthd") may help.

---

### Post by mykelm03 on 2009-12-12
ive tried the link you gave me but still got no luck. cannot send an email without connecting to our vpn. here's my main.cf and can you pls take a look and check what is wrong... thanks..

[I]smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
readme_directory = no
smtpd_tls_cert_file = /etc/postfix/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/private/smtpd.key
smtp_use_tls = yes
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

myhostname = *my.mydomain.com*
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases

mydestination = *my.mydomain.com, localhost*

mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128, 192.168.2.0/24

inet_interfaces = all
mailbox_size_limit = 0
recipient_delimiter = +
inet_protocols = all
home_mailbox = Maildir/
mailbox_command = 
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes

policyd-spf_time_limit = 3600

smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom


append_dot_mydomain = no
swap_bangpath = no
append_at_myorigin = yes
myorigin = freyssinet.com.ph

content_filter = smtp-amavis:[127.0.0.1]:10024

body_checks = regexp:/etc/postfix/maps/body_checks
header_checks = regexp:/etc/postfix/maps/header_checks
mime_header_checks = regexp:/etc/postfix/maps/mime_header_checks 

smtpd_helo_required = yes
disable_vrfy_command = yes
smtpd_helo_required = yes
smtpd_error_sleep_time = 15s
smtpd_soft_error_limit = 10
smtpd_hard_error_limit = 20
allow_percent_hack = no

strict_rfc821_envelopes = yes

smtpd_recipient_restrictions = 
	permit_mynetworks, 
	reject_unauth_destination, 
	permit_sasl_authenticated,
	reject_non_fqdn_sender,
	reject_unknown_sender_domain,
	reject_unverified_sender,
	reject_multi_recipient_bounce,
	reject_unknown_recipient_domain,
	reject_unlisted_recipient,
        reject_unverified_recipient,
	reject_invalid_hostname,
    	reject_unauth_pipelining,
   	reject_non_fqdn_recipient,
    	reject_rhsbl_client blackhole.securitysage.com,
    	reject_rhsbl_sender blackhole.securitysage.com,
    	reject_rbl_client blackholes.easynet.nl,
    	reject_rbl_client cbl.abuseat.org,
    	reject_rbl_client proxies.blackholes.wirehub.net,
    	reject_rbl_client bl.spamcop.net,
    	reject_rbl_client sbl.spamhaus.org,
    	reject_rbl_client opm.blitzed.org,
    	reject_rbl_client dnsbl.njabl.org,
    	reject_rbl_client list.dsbl.org,
    	reject_rbl_client multihop.dsbl.org,
    	permit 

broken_sasl_auth_clients = yes[/I]

---

### Post by volkswagner on 2009-12-12
What are the results using the "Verify" section from the mentioned how-to?

What info can you find in your mail logs?

---

### Post by mykelm03 on 2009-12-12
whenever i try to issue, telnet *mail_server_i*p 25, "Could not open connection to the host, on port 25: Connect failed" .... and no error logs...:(

---

### Post by volkswagner on 2009-12-12
Can you verify port 25 is open via a site like [Canyouseeme.org]("http://canyouseeme.org/") ?

Any firewalls running?

If you ssh into the server can you```
 telnet localhost 25
```

Any thing listening to port 25 ?

```
sudo netstat -lnp
```

---

### Post by mykelm03 on 2009-12-13
mis@server-mail:~$ sudo netstat -lnp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:10024         0.0.0.0:*               LISTEN      8520/amavisd (maste
tcp        0      0 127.0.0.1:10025         0.0.0.0:*               LISTEN      8674/master
tcp        0      0 127.0.0.1:783           0.0.0.0:*               LISTEN      2237/spamd.pid
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      4212/apache2
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN      3446/perl
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      2227/sshd
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      3198/cupsd
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      8674/master
tcp6       0      0 :::5900                 :::*                    LISTEN      3910/vino-server
tcp6       0      0 :::110                  :::*                    LISTEN      2736/couriertcpd
tcp6       0      0 :::143                  :::*                    LISTEN      2715/couriertcpd
tcp6       0      0 :::22                   :::*                    LISTEN      2227/sshd
tcp6       0      0 ::1:631                 :::*                    LISTEN      3198/cupsd
tcp6       0      0 :::25                   :::*                    LISTEN      8674/master
udp        0      0 0.0.0.0:10000           0.0.0.0:*                           3446/perl
udp        0      0 0.0.0.0:49944           0.0.0.0:*                           3122/avahi-daemon:
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           3122/avahi-daemon:
udp        0      0 0.0.0.0:631             0.0.0.0:*                           3198/cupsd
[SIZE="4"][/SIZE]

and i didnt install the firewall...telnet to our server, "connection failed" is the response...checking port 25 using  Canyouseeme.org, "Error: I could not see your service on x.x.x.x on port (25) Reason: Connection refused"

---

### Post by volkswagner on 2009-12-13
> **mykelm03 said:**
> m...

and i didnt install the firewall...telnet to our server, "connection failed" is the response...checking port 25 using  Canyouseeme.org, "Error: I could not see your service on x.x.x.x on port (25) Reason: Connection refused"

Sounds like your ISP is blocking port 25.

---

### Post by mykelm03 on 2009-12-14
thanks so much for the info...

---

