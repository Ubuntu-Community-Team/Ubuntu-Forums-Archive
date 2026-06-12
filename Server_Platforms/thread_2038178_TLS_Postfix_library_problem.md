---
title: "TLS Postfix library problem"
date: 2012-08-06
forum: Server Platforms
---

### Post by associates on 2012-08-06
Hi,

I have finally got my postfix, dovecot, MySQL and roundcubemail installed on Ubuntu Server 12.04 LTS 32bit and they seem to be working fine. I tested out to see if postfix is working by running telnet command as follows
$ telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 imap.example.com ESMTP Postfix
ehlo imap.example.com
250-imap.example.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
STARTTLS
220 2.0.0 Ready to start TLS

However, when I looked into /var/log/mail.log file, I saw the following errors
postfix/smtpd[3365]: error: open database /etc/aliases.db: No such file or directory
postfix/smtpd[3365]: initializing the server-side TLS engine
postfix/smtpd[3365]: connect from localhost[127.0.0.1]
postfix/smtpd[3365]: setting up TLS connection from localhost[127.0.0.1]
postfix/smtpd[3365]: localhost[127.0.0.1]: TLS cipher list "aNULL:-aNULL:ALL:!EXPORT:!LOW:+RC4:@STRENGTH"
postfix/smtpd[3365]: SSL_accept:before/accept initialization
sparepc1 postfix/smtpd[3365]: SSL_accept:error in unknown state
postfix/smtpd[3365]: SSL_accept error from localhost[127.0.0.1]: -1
postfix/smtpd[3365]: warning: TLS library problem: 3365:error:140760FC:SSL routines:SSL23_GET_CLIENT_HELLO:unknown protocol:s23_srvr.c:628:

TLS library problem?? would anyone be kind to tell me what this error means?

Any help would be appreciated

Thank you

---

### Post by associates on 2012-08-06
Hi again,

Just realized that telnet does not support TLS. I think that error is related to this problem.

Therefore, i run the following command via openssl
$ openssl s_client -connect localhost:25 -starttls smtp

CONNECTED(00000003)
depth=1 C = US, O = "GeoTrust, Inc.", CN = RapidSSL CA
verify error:num=20:unable to get local issuer certificate
verify return:0

something is wrong with my local issuer certificate :(

I've already had SSL certificates for my domains already.

Thank you

---

### Post by CharlesA on 2012-08-06
How do you have Postfix set up? You probably need to import your cert or something.

This might help:
[http://www.cyberciti.biz/tips/postfix-smtp-ssl-certificate-csr-installation-guide.html](http://www.cyberciti.biz/tips/postfix-smtp-ssl-certificate-csr-installation-guide.html)

---

### Post by associates on 2012-08-06
Thank you for your reply.

Here is my main.cf in terms of TLS
smtpd_use_tls = yes
smtpd_tls_cert_file = /etc/ssl/certs/mail.example.com.crt
smtpd_tls_cert_file = /etc/ssl/certs/example.com.crt
smtpd_tls_key_file = /etc/ssl/certs/mail.example.com.key
smtpd_tls_key_file = /etc/ssl/certs/example.com.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_tls_CAfile = /etc/ssl/certs/CA_bundle.pem
smtpd_tls_CAfile = /etc/ssl/certs/CA_bundle.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
tls_random_source = dev:/dev/urandom
smtpd_tls_auth_only = yes
smtpd_tls_session_cache_timeout = 3600s

Test it out by running telnet mail.example.com 25
Trying ....
Connected to example.com.
Escape character is '^]'.
220 mailserver.example.com ESMTP Postfix
ehlo mail.example.com
250-mailserver.example.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN

I can see the STARTTLS there. So I think the TLS is working but is not offering TLS. The hostname of my server is mailserver.example.com. The SSL certificates that I applied for are active for mail.example.com and example.com respectively. I think I might have stuffed up my SSL certificates application. Please correct me if I'm wrong.

Thank you so much for your help

---

### Post by CharlesA on 2012-08-06
Check the postfix log. It might tell you what exactly the problem is.

I haven't had to deal with SSL much, so I am not sure where to go from there.

---

