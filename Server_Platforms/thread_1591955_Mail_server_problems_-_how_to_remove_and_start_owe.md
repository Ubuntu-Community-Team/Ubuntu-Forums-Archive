---
title: "Mail server problems - how to remove and start ower"
date: 2010-10-10
forum: Server Platforms
---

### Post by windsxs on 2010-10-10
Hello,
I have installed theese packages:
```
aptitude install postfix postfix-mysql postfix-doc courier-authdaemon courier-authlib-mysql courier-pop courier-pop-ssl courier-imap courier-imap-ssl libsasl2-2 libsasl2-modules libsasl2-modules-sql sasl2-bin libpam-mysql openssl getmail4 rkhunter binutils maildrop
```

I have problam with dovecat. I try to reinstall it, but i get this:
```

root@evilpc:/home/evilpc# sudo apt-get install dovecot-common dovecot-imapd dovecot-pop3d
sudo: unable to resolve host evilpc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ntp
The following NEW packages will be installed:
  dovecot-common dovecot-imapd dovecot-pop3d
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/7,440kB of archives.
After this operation, 14.5MB of additional disk space will be used.
Selecting previously deselected package dovecot-common.
(Reading database ... 145344 files and directories currently installed.)
Unpacking dovecot-common (from .../dovecot-common_1%3a1.2.9-1ubuntu6.1_i386.deb) ...
Selecting previously deselected package dovecot-imapd.
Unpacking dovecot-imapd (from .../dovecot-imapd_1%3a1.2.9-1ubuntu6.1_i386.deb) ...
Selecting previously deselected package dovecot-pop3d.
Unpacking dovecot-pop3d (from .../dovecot-pop3d_1%3a1.2.9-1ubuntu6.1_i386.deb) ...
Processing triggers for ufw ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up dovecot-common (1:1.2.9-1ubuntu6.1) ...
Not replacing deleted config file /etc/dovecot/dovecot.conf
Not replacing deleted config file /etc/dovecot/dovecot-ldap.conf
Not replacing deleted config file /etc/dovecot/dovecot-sql.conf
grep: /etc/dovecot/dovecot.conf: No such file or directory
grep: /etc/dovecot/dovecot.conf: No such file or directory
Creating generic self-signed certificate: /etc/ssl/certs/dovecot.pem
(replace with hand-crafted or authorized one if needed).
hostname: Name or service not known
dpkg: error processing dovecot-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of dovecot-imapd:
 dovecot-imapd depends on dovecot-common (= 1:1.2.9-1ubuntu6.1); however:
  Package dovecot-common is not configured yet.
dpkg: error processing dovecot-imapd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dovecot-pop3d:
 dovecot-pop3d depends on dovecot-common (= 1:1.2.9-1ubuntu6.1); however:
  Package dovecot-common is not configured yet.
dpkg: error processing dovecot-pop3d (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 dovecot-common
 dovecot-imapd
 dovecot-pop3d
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Before i did ```
apt-get autoremove dovecot*
``` :-k

AND deletet /etc/dovecot..... becouse i thought if it installs next time it should recreate all configuration files, but it didn't... :confused:

What I want is to make email server to send mail via another smt server (my internet providers) and to be able to get.. So, how to remove everything in relation with mail servers ant start over? 

Thank You for replies :)

---

### Post by windsxs on 2010-10-10
Everthing seems OK. But still I cant receive emails from e.g. gmail.com. If I send it from my domain, mymachine (local), then, I receive email... What could be the problem???

---

