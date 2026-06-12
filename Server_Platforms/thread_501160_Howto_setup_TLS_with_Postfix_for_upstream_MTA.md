---
title: "Howto setup TLS with Postfix for upstream MTA???"
date: 2007-07-14
forum: Server Platforms
---

### Post by markymarknz on 2007-07-14
Hi Everyone,

I have had this issue for a while now and have not had much luck getting it to work.
Basically I have a mailserver running Zimbra which I plan to connect to an upstream MTA which needs to use TLS. I have been given a username/password for the TLS authentication however I haven't been able to workout how to setup Postfix correctly to use TLS authentication.
If anyone has managed to get Postfix working in a similar manner I would really appreciate some help.
My main.cf file is this:

sender_canonical_maps = ldap:/opt/zimbra/conf/ldap-scm.cf
virtual_alias_domains = ldap:/opt/zimbra/conf/ldap-vad.cf
recipient_delimiter =
smtpd_tls_cert_file = /opt/zimbra/conf/smtpd.crt
smtpd_tls_auth_only = yes
myhostname = mail.xxxx.net
virtual_mailbox_domains = ldap:/opt/zimbra/conf/ldap-vmd.cf
mailbox_size_limit = 0
smtpd_client_restrictions = reject_unauth_pipelining
virtual_alias_maps = ldap:/opt/zimbra/conf/ldap-vam.cf
transport_maps = ldap:/opt/zimbra/conf/ldap-transport.cf
sendmail_path = /opt/zimbra/postfix-2.2.9/sbin/sendmail
message_size_limit = 10240000
broken_sasl_auth_clients = yes
alias_maps = hash:/etc/aliases
manpage_directory = /opt/zimbra/postfix-2.2.9/man
smtpd_helo_required = yes
daemon_directory = /opt/zimbra/postfix-2.2.9/libexec
virtual_transport = error
smtpd_recipient_restrictions = reject_non_fqdn_recipient, permit_sasl_authenticated, permit_mynetworks, reject_unlisted_recipient, reject_invalid_hostname, r
eject_non_fqdn_sender, reject_unauth_destination, permit
smtpd_tls_loglevel = 1
relayhost = [ip address]:25
disable_dns_lookups = no
content_filter = smtp-amavis:[127.0.0.1]:10024
virtual_mailbox_maps = ldap:/opt/zimbra/conf/ldap-vmm.cf
version = 2.2.9
mailq_path = /opt/zimbra/postfix-2.2.9/sbin/mailq
header_checks = pcre:/opt/zimbra/conf/postfix_header_checks
smtpd_use_tls = yes
queue_directory = /opt/zimbra/postfix-2.2.9/spool
newaliases_path = /opt/zimbra/postfix-2.2.9/sbin/newaliases
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_reject_unlisted_recipient = no
smtpd_tls_key_file = /opt/zimbra/conf/smtpd.key
command_directory = /opt/zimbra/postfix-2.2.9/sbin
smtpd_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/opt/zimbra/conf/relay_password
smtp_sasl_auth_enable = yes
smtp_use_tls = yes
smtp_tls_peer_match = no

When I check the logs for this I get messages about the certificate not being verified as well:

root@mail:/var/log# less zimbra.log | grep postfix
Jun 23 13:43:05 mail postfix/postqueue[4003]: fatal: Queue report unavailable - mail system is down
Jun 23 13:52:48 mail postfix/postqueue[4050]: fatal: Queue report unavailable - mail system is down
Jun 23 13:52:52 mail postfix/postfix-script: warning: not owned by root: /opt/zimbra/postfix-2.2.9/conf/main.cf
Jun 23 13:52:52 mail postfix/postfix-script: warning: not owned by root: /opt/zimbra/postfix-2.2.9/conf/main.cf.bk
Jun 23 13:52:52 mail postfix/postfix-script: starting the Postfix mail system
Jun 23 13:52:52 mail postfix/master[4272]: daemon started -- version 2.2.9, configuration /opt/zimbra/postfix-2.2.9/conf
Jun 23 14:42:24 mail postfix/smtpd[11877]: connect from mail.xxx.net[192.168.2.3]
Jun 23 14:42:24 mail postfix/smtpd[11877]: 2885A1E7877: client=mail.xxx.net[192.168.2.3]
Jun 23 14:42:24 mail postfix/cleanup[11881]: 2885A1E7877: message-id=<32482448.01182566543349.JavaMail.root@mail.xxx.net>
Jun 23 14:42:24 mail postfix/qmgr[4276]: 2885A1E7877: from=, size=548, nrcpt=1 (queue active)
Jun 23 14:42:24 mail postfix/smtpd[11877]: disconnect from mail.xxx.net[192.168.2.3]
Jun 23 14:42:25 mail postfix/smtpd[11885]: connect from localhost.localdomain[127.0.0.1]
Jun 23 14:42:25 mail postfix/smtpd[11885]: BA3E41E7885: client=localhost.localdomain[127.0.0.1]
Jun 23 14:42:25 mail postfix/cleanup[11881]: BA3E41E7885: message-id=<32482448.01182566543349.JavaMail.root@mail.xxx.net>
Jun 23 14:42:25 mail postfix/smtpd[11885]: disconnect from localhost.localdomain[127.0.0.1]
Jun 23 14:42:25 mail postfix/smtp[11882]: 2885A1E7877: to=, relay=127.0.0.1[127.0.0.1], delay=1, status=sent (250 2.6.0 Ok, id=04221-01, from MTA([127.0.0.1]:10025): 250 Ok: queued as BA3E41E7885)
Jun 23 14:42:25 mail postfix/qmgr[4276]: BA3E41E7885: from=, size=1132, nrcpt=1 (queue active)
Jun 23 14:42:25 mail postfix/qmgr[4276]: 2885A1E7877: removed
Jun 23 14:42:27 mail postfix/smtp[11886]: certificate verification failed for 65.99.222.183: num=20:unable to get local issuer certificate
Jun 23 14:42:27 mail postfix/smtp[11886]: certificate verification failed for 65.99.222.183: num=27:certificate not trusted
Jun 23 14:42:27 mail postfix/smtp[11886]: certificate verification failed for 65.99.222.183: num=21:unable to verify the first certificate
Jun 23 14:42:28 mail postfix/smtp[11886]: Server certificate could not be verified
Jun 23 14:42:29 mail postfix/smtp[11886]: BA3E41E7885: to=, relay=[upstream mta ip], delay=4, status=bounced (host [upstream mta ip] said: 550 relay not permitted (in reply to RCPT TO command))
Jun 23 14:42:29 mail postfix/cleanup[11881]: 452521E7886: message-id=<20070623024229.452521E7886@mail.xxx.net>
Jun 23 14:42:29 mail postfix/qmgr[4276]: 452521E7886: from=<>, size=3034, nrcpt=1 (queue active)
Jun 23 14:42:29 mail postfix/qmgr[4276]: BA3E41E7885: removed
Jun 23 14:42:29 mail postfix/lmtp[11888]: 452521E7886: to=, relay=mail.xxx.net[192.168.2.3], delay=0, status=sent (250 2.1.5 OK)
Jun 23 14:42:29 mail postfix/qmgr[4276]: 452521E7886: removed

Would this affect the TLS transaction? Would I have to install the root certificate which verifies his? [http://crt.litessl.com/LiteSSL_CA.crt](http://crt.litessl.com/LiteSSL_CA.crt)

Any help would be really appreciated.

Mark

---

### Post by Mr. C. on 2007-07-15
There are a fair number of steps here; for more information, refer to either the documentation on the postfix site ([www.postfix.org](www.postfix.org)) or purchase the excellent The Book of Postfix.

The server you are using apepars  to requires TLS before it presents the authentication mechanisms.  Therefore, you need to establish a TLS connection to it (client-side TLS).  The basic steps to configuring client-side TLS are essentially:

[LIST=1]
[*]Enable client-side TLS (you've done this with smtp_use_tls=yes)
[*]Config. postfix to verify server certificate
[*]Config random source generator
[/LIST]

You need to setup smtp_tls_CAfile to contain the chain of certificates that will allow validation of the remote server's certificate.  Postfix needs the CA certificate so it can validate the server's certificate against its public key.

```
smtp_tls_CAfile=/path/to/your/cabundle
```

For client-side certificate-based relaying, you need to configure smtp_tls_cert_file and smtp_tls_key_file.  The former is the path to the public key in pem format, and the latter is the client's (i.e.. your server's) private key in pem format.  Since you are also configured as a TLS server, you can use the same TLS certificate you use for the TLS server configuration.

TLS needs a random source generator:

```
smtp_random_source=dev:/dev/urandom
```

Configure:

```
smtp_tls_loglevel=2 
```

to get more detail about the TLS process.

You'll have to use the s_client program to determine which  auth mechanisms are supported by the server (or use a GUI client and determine from it which mechanisms are supported by relaying a message through the remote server).

This may be enough to get your going.  There are additional settings to ensure your credentials are never sent in plain text, and to configure the client to attempt TLS connections, but fall back gracefully should TLS fail.

MrC




The remote server's root certificate must be installed in the chain used by postfix to verify the remote server.

---

