---
title: "Apache2 w/ Dovecot &amp; Samba"
date: 2012-10-09
forum: Server Platforms
---

### Post by Crafty Kisses on 2012-10-09
I have configured Sendmail as my SMTP server at port 25 via Samba. I execute the command and it says it's locked from another process so I run
```
rm /var/lock/subsys/dovecot
```
Once I retry, there seems to be an SSL problem
```
prowl2 pop3-login: Can't load private key file /usr/share/ssl/private/dovecot.pem: error:0B080074:x509 
```
I open the TLS/SSL and submission ports in Postfix:
```
[...]
submission inet n       -       -       -       -       smtpd
  -o syslog_name=postfix/submission
  -o smtpd_tls_security_level=encrypt
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
smtps     inet  n       -       -       -       -       smtpd
  -o syslog_name=postfix/smtps
  -o smtpd_tls_wrappermode=yes
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
[...]
```
Then I see if the network is enabled (checking my MySQL databases)
```
netstat -tap | grep mysql
```
Results are as follows
```
root@server1:~# netstat -tap | grep mysql
tcp        0      0 *:mysql                 *:*                     LISTEN      21298/mysqld
root@server1:~#

```
Which is good, so I try again and again I get this error from Dovecot
```
The server responded ['NOPERM]
```
So it's a permission issue, I've checked the permissions and they all seem good. Any ideas?

---

