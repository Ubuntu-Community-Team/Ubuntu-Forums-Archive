---
title: "Dovecot ok for port 110, but not for SSL"
date: 2012-11-06
forum: Server Platforms
---

### Post by yc2 on 2012-11-06
Hello,
I just installed Dovecot. It works for plaintext autorization, port 110. It has connected with Telnet, Thunderbird and an on-line pop3 client.
Telnet:
```
+OK Dovecot ready.
user nnnnn
-ERR Unknown command.
user nnnnn
+OK
pass xxxxxxxxxx
+OK Logged in.
stat
+OK 1 1553
retr 1
+OK 1553 octets
Return-path: <sssssss@hotmail.com>
Envelope-to: nnnnnn@mydomain.com
Delivery-date: Tue, 06 Nov 2012 12:02:28 +0100
Received: from bay0-xcvxcv-xvxcv.bay333.hotmail.com ([123.123.123.123])
        by deb7.pc with esmtp (Exim 4.80)

```
But when I try ssl (port 995) with an on-line pop3 client, it will not work:
/var/log/mail.log
```
Nov  7 02:46:55 deb7 dovecot: pop3-login: Disconnected (no auth attempts in 0 secs): user=<>, rip=12.12.12.7, lip=123.123.123.123, TLS: Disconnected, session=<Iza75N3NlABBNykH>
Nov  7 02:46:56 deb7 dovecot: pop3-login: Disconnected (no auth attempts in 1 secs): user=<>, rip=12.12.12.7, lip=123.123.123.123, TLS: Disconnected, session=<nWTF5N3NlQBBNykH>
root@deb7:~#

```
```
root@deb7:~# doveconf -n
# 2.1.7: /etc/dovecot/dovecot.conf
# OS: Linux 3.2.0-3-686-pae i686
disable_plaintext_auth = no
mail_gid = mail
mail_location = mbox:~/mail:INBOX=/var/mail/%u
namespace inbox {
  inbox = yes
  location =
  prefix =
}
passdb {
  args = username_format=%u /etc/dovecot/users
  driver = passwd-file
}
plugin {
  sieve = ~/.dovecot.sieve
  sieve_dir = ~/sieve
}
protocols = " imap pop3"
ssl_cert = </etc/ssl/certs/dovecot.pem
ssl_key = </etc/ssl/private/dovecot.pem
userdb {
  args = username_format=%u /etc/dovecot/users
  driver = passwd-file
}
root@deb7:~#
```
I know very little about mail and ssl. I have assumed that ssl will be set up "automatically" when Dovecot is installed. But maybe I have missed something here. Please give me pointers.
The following two files contain ssl keys:
```
ssl_cert = </etc/ssl/certs/dovecot.pem
ssl_key = </etc/ssl/private/dovecot.pem

```
Thanks.

---

### Post by yc2 on 2012-11-09
I have discussed this with different people and got advice.
The problem seems to be that my ssl-certificate is not signed by an official part, some websites therefore refuse connecting to it over ssl. This thread is solved.

---

### Post by Killbam on 2012-12-21
Just to clarify, you can make your local computer trust the self-signed cert so that you can use it with Thunderbird or other email clients.  Make sure 100% for your OS that you're trusting the cert.

---

