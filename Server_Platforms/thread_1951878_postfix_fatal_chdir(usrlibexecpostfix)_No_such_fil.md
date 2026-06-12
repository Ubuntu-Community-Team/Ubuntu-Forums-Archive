---
title: "postfix: fatal: chdir(/usr/libexec/postfix): No such file or directory"
date: 2012-04-03
forum: Server Platforms
---

### Post by yngens on 2012-04-03
Have no idea how my postfix got broken on my Ubuntu 10.04 LTS, now trying to re-install it and seeing lot's of errors:

```
root@hoster:/etc/mail# apt-get install postfix
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  pwgen libnet-daemon-perl postgresql-8.4 bind9 proftpd-basic libdigest-sha1-perl sasl2-bin libnet-ip-perl
  db4.8-util irb1.8 libnet-dns-perl re2c clamav mysql-server bind9utils dovecot-common webmin-virtual-server
  libnet-xwhois-perl php5 awstats libdbi-perl webmin-security-updates apt-listchanges rdoc ri clamav-base
  mysql-server-core-5.1 libclamav6 apache2 procmail spamc libapache2-mod-fcgid php-pear procmail-wrapper
  apache2-suexec-custom scponly libreadline5 mysql-client-core-5.1 libpg-perl dovecot-imapd
  webmin-virtualmin-awstats irb clamav-docs postgresql-common libdbd-mysql-perl libapache2-svn postgresql
  webmin-virtualmin-htpasswd usermin-virtual-server-theme rdoc1.8 postgresql-client-8.4 liberror-perl webalizer
  libplrpc-perl webmin-virtualmin-dav libsocket6-perl libdbd-pg-perl clamav-freshclam apache2-doc
  postgresql-client-common libdb4.7 dovecot-pop3d libpq5 libtommath0 libnetaddr-ip-perl
  webmin-virtualmin-mailman webmin-virtual-server-theme libmail-spf-perl libreadline-ruby1.8 clamav-daemon
  libsys-hostname-long-perl openbsd-inetd mysql-server-5.1 libdigest-hmac-perl webmin-virtualmin-svn ri1.8
  libltdl7 spamassassin mysql-client-5.1 clamav-testfiles libio-socket-inet6-perl
Use 'apt-get autoremove' to remove them.
Suggested packages:
  postfix-mysql postfix-pgsql postfix-ldap postfix-pcre resolvconf postfix-cdb mail-reader
The following NEW packages will be installed:
  postfix
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1,404kB of archives.
After this operation, 3,572kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package postfix.
(Reading database ... 99945 files and directories currently installed.)
Unpacking postfix (from .../postfix_2.7.0-1ubuntu0.2_amd64.deb) ...
Processing triggers for ureadahead ...
Processing triggers for ufw ...
Processing triggers for man-db ...
Setting up postfix (2.7.0-1ubuntu0.2) ...

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
 * Stopping Postfix Mail Transport Agent postfix
   ...done.
 * Starting Postfix Mail Transport Agent postfix
postfix: fatal: chdir(/usr/libexec/postfix): No such file or directory
   ...fail!
invoke-rc.d: initscript postfix, action "restart" failed.
dpkg: error processing postfix (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Probably Virtualmin's settings got in the middle, but now I am trying to install postfix from a command line with no much joy. Would appreciate any suggestions.

---

### Post by nsnidanko on 2012-04-03
Looks like your postfix binaries not installing correctly. Backup your postfix config (/etc/posfix) and than run purge
**apt-get purge postfix**
after its done try to reinstall postfix again by **apt-get install postfix**

---

### Post by yngens on 2012-04-04
nsnidanko, thanks for your reply. Unfortunately, I didn't see your advice before I have re-installed the system from zero.

---

