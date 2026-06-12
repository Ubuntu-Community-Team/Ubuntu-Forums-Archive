---
title: "Posts merged into one"
date: 2014-12-01
forum: Server Platforms
---

### Post by astarmathsandphysics on 2014-12-01
Apache 2.4.10

Now think the problem may be with php.
when I try to load a page in php the broser tries to load a file

Every line in apache access log shows a 500 error

Something to do with .htaccess
When I deleted them, my sites loaded

Something to do with .htaccess
When I deleted them, my sites loaded

How do I fix this so I don't get the errors?

Think related to apache modules.
Am finding which apache modulkes to install.

Here is a part of my mail.log

```
Feb 24 16:27:02 server11362 postfix/pickup[3461]: 5CD04AE2AAD: uid=1007 from=<theeducationchannel>
Feb 24 16:27:02 server11362 postfix/cleanup[27520]: 5CD04AE2AAD: message-id=<20150224162702.5CD04AE2AAD@server11362>
Feb 24 16:27:02 server11362 postfix/qmgr[3462]: 5CD04AE2AAD: from=<theeducationchannel@server11362.abc.com>, size=632, nrcpt=1 (queue active)
Feb 24 16:27:02 server11362 postfix/error[20640]: 5CD04AE2AAD: to=<theeducationchannel@server11362.abc.com>, orig_to=<theeducationchannel>, relay=none, delay=0.32, delays=0.2/0/0/0.13, dsn=4.4.1, status=deferred (delivery temporarily suspended: connect to server11362.abc.com[218.93.250.18]:25: Connection timed out)
Feb 24 16:28:01 server11362 postfix/pickup[3461]: 6F844AE2AAF: uid=1006 from=<astarmathsandphysics>
Feb 24 16:28:01 server11362 postfix/cleanup[27520]: 6F844AE2AAF: message-id=<20150224162801.6F844AE2AAF@server11362>
Feb 24 16:28:01 server11362 postfix/qmgr[3462]: 6F844AE2AAF: from=<astarmathsandphysics@server11362.abc.com>, size=700, nrcpt=1 (queue active)
Feb 24 16:28:01 server11362 postfix/error[20636]: 6F844AE2AAF: to=<astarmathsandphysics@server11362.abc.com>, orig_to=<astarmathsandphysics>, relay=none, delay=0.35, delays=0.27/0/0/0.08, dsn=4.4.1, status=deferred (delivery temporarily suspended: connect to server11362.abc.com[218.93.250.18]:25: Connection timed out)
Feb 24 16:28:01 server11362 postfix/pickup[3461]: DBD26AE2AB1: uid=1007 from=<theeducationchannel>
Feb 24 16:28:02 server11362 postfix/cleanup[27520]: DBD26AE2AB1: message-id=<20150224162801.DBD26AE2AB1@server11362>
Feb 24 16:28:02 server11362 postfix/qmgr[3462]: DBD26AE2AB1: from=<theeducationchannel@server11362.abc.com>, size=632, nrcpt=1 (queue active)
Feb 24 16:28:02 server11362 postfix/error[20198]: DBD26AE2AB1: to=<theeducationchannel@server11362.abc.com>, orig_to=<theeducationchannel>, relay=none, delay=0.37, delays=0.3/0/0/0.07, dsn=4.4.1, status=deferred (delivery temporarily suspended: connect to server11362.abc.com[218.93.250.18]:25: Connection timed out)
Feb 24 16:29:02 server11362 postfix/pickup[3461]: 6A7A6AE2AB3: uid=1007 from=<theeducationchannel>
Feb 24 16:29:02 server11362 postfix/cleanup[27520]: 6A7A6AE2AB3: message-id=<20150224162902.6A7A6AE2AB3@server11362>
Feb 24 16:29:02 server11362 postfix/qmgr[3462]: 6A7A6AE2AB3: from=<theeducationchannel@server11362.abc.com>, size=632, nrcpt=1 (queue active)
Feb 24 16:29:02 server11362 postfix/error[20198]: 6A7A6AE2AB3: to=<theeducationchannel@server11362.abc.com>, orig_to=<theeducationchannel>, relay=none, delay=0.27, delays=0.2/0/0/0.07, dsn=4.4.1, status=deferred (delivery temporarily suspended: connect to server11362.abc.com[218.93.250.18]:25: Connection timed out)
Feb 24 16:30:01 server11362 postfix/pickup[3461]: 8A7C9AE2AB5: uid=1006 from=<astarmathsandphysics>
Feb 24 16:30:01 server11362 postfix/cleanup[27520]: 8A7C9AE2AB5: message-id=<20150224163001.8A7C9AE2AB5@server11362>
Feb 24 16:30:01 server11362 postfix/qmgr[3462]: 8A7C9AE2AB5: from=<astarmathsandphysics@server11362.abc.com>, size=700, nrcpt=1 (queue active)
Feb 24 16:30:01 server11362 postfix/error[20198]: 8A7C9AE2AB5: to=<astarmathsandphysics@server11362.abc.com>, orig_to=<astarmathsandphysics>, relay=none, delay=0.33, delays=0.23/0/0/0.1, dsn=4.4.1, status=deferred (delivery temporarily suspended: connect to server11362.abc.com[218.93.250.18]:25: Connection timed out)
Feb 24 16:30:01 server11362 postfix/pickup[3461]: 000F9AE2AB7: uid=1007 from=<theeducationchannel>
Feb 24 16:30:02 server11362 postfix/cleanup[27520]: 000F9AE2AB7: message-id=<20150224163002.000F9AE2AB7@server11362>
Feb 24 16:30:02 server11362 postfix/qmgr[3462]: 000F9AE2AB7: from=<theeducationchannel@server11362.abc.com>, size=632, nrcpt=1 (queue active)
Feb 24 16:30:02 server11362 postfix/error[20198]: 000F9AE2AB7: to=<theeducationchannel@server11362.abc.com>, orig_to=<theeducationchannel>, relay=none, delay=0.3, delays=0.22/0/0/0.08, dsn=4.4.1, status=deferred (delivery temporarily suspended: connect to server11362.abc.com[218.93.250.18]:25: Connection timed out)

```

My question is to do with myhostname
In /etc/postfix/main.cf I set myhostname to server11362 because that is the name in /etc/hostname 
but in /etc/hosts I see 
127.0.0.1	localhost
111.90.150.92	server11362.abc.com	server11362

When I type hostname into a terminal I get server11362
So in /etc/postfix/main.cf can I leave hostname as server11362

Also the ip of my serverr is 111.90.150.92 but the ip of server11362.abc.com in the above log is 218.93.250.18

I have a server with several domains and and trying to configure postfix/dovecot with emails for each domain.
At the moment all the emails go to and from root, even if I test by logging into mutt as a user with email and send a test email.
I think from what I have read that it is something to do with setting aliases in /etc/aliases
At the moment this file reads

# See man 5 aliases for format
postmaster:    root
clamav: root
devnull: /dev/null


Any advice?

Just found this error in the mail.warn file

Dec  9 15:32:35 server1 postfix/postmap[25915]: fatal: open aliases: No such file or directory

In /var/log/dovecot I got the following error

Fatal: service(pop3) access(/usr/lib/dovecot/pop3) failed: No such file or directory

I installed dovecot-pop3d at this point

In /etc/postfix/main.cf

there are these lines

alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases

/etc/aliases does exist and now reads

# See man 5 aliases for format
postmaster:    root, astarmathsandphysics
clamav: root
devnull: /dev/null

Sod all that.
i FOLLOWED THIS TUTORIAL
[https://help.ubuntu.com/community/PostfixBasicSetupHowto]("https://help.ubuntu.com/community/PostfixBasicSetupHowto")

But now I know I have to set up a database because all emails are rejected with this sort of message

Recipient address rejected: User unknown in local recipient table;

apt-cache show libapache2-mod-spamhaus
Package: libapache2-mod-spamhaus
Priority: extra
Section: universe/web
Installed-Size: 96
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Giuseppe Iuculano <giuseppe@iuculano.it>
Architecture: amd64
Source: mod-spamhaus
Version: 0.7-1
Depends: libc6 (>= 2.4), apache2.2-common
Filename: pool/universe/m/mod-spamhaus/libapache2-mod-spamhaus_0.7-1_amd64.deb
Size: 9380
MD5sum: 4ad7a5b4c23b1e107e0e363637975a7f
SHA1: 63770347473c7007c8ba5eca56bf4b2a27742b5e
SHA256: 0159a362cc7d6c1d99d00266eb98be227989f66c2125cd8cd79706abc1cb79b0
Description-en: Apache DNSBL module that blocks listed IP addresses
 mod_spamhaus is an Apache module for DNS Block Listing that protects web
 services by denying access to particular IP addresses. It can stop spam
 relaying via web form URL injection, and block HTTP DDoS attacks from
 bot-nets.
 .
 It queries sbl-xbl.spamhaus.org, taking advantage of the Spamhaus Block
 List (SBL) and the Exploits Block List (XBL).
Homepage: [http://sourceforge.net/projects/mod-spamhaus/](http://sourceforge.net/projects/mod-spamhaus/)
Description-md5: 87ae530e0dfd90a8fbca6c801e62a41a
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu


 apt-cache show apache2.2-common
Package: apache2.2-common
Source: apache2
Priority: extra
Section: oldlibs
Installed-Size: 99
Maintainer: Debian Apache Maintainers <debian-apache@lists.debian.org>
Architecture: amd64
Version: 2.4.10-1+deb.sury.org~precise+1
Depends: apache2 (>= 2.3~)
Conflicts: libapache2-mod-bt, libapache2-mod-cband, libapache2-mod-php4, libapache2-mod-shib
Breaks: gridsite (<< 1.7.21-2), ikiwiki-hosting-web (<< 0.20140419), libapache-authenhook-perl (<< 2.00-04+pristine-5), libapache-singleton-perl (<< 0.15-2), libapache2-authcookie-perl (<< 3.19-2), libapache2-mod-annodex (<< 0.2.2-6+deb8), libapache2-mod-apparmor (<< 2.8.0-1), libapache2-mod-apreq2 (<< 2.13-2), libapache2-mod-auth-cas (<< 1.0.9.1-3), libapache2-mod-auth-kerb (<< 5.4-2.1), libapache2-mod-auth-memcookie (<< 1.0.2-8), libapache2-mod-auth-mysql (<< 4.3.9-13.1+deb8), libapache2-mod-auth-ntlm-winbind (<< 0.0.0.lorikeet+svn+801-2), libapache2-mod-auth-openid (<< 0.7-1), libapache2-mod-auth-pam (<< 1.1.1-9+deb8), libapache2-mod-auth-pgsql (<< 2.0.3-6), libapache2-mod-auth-plain (<< 2.0.52), libapache2-mod-auth-pubtkt (<< 0.8-2), libapache2-mod-auth-radius (<< 1.5.8-1.2), libapache2-mod-auth-sys-group (<< 1.1.1-9+deb8), libapache2-mod-auth-tkt (<< 2.1.0-7), libapache2-mod-authn-sasl (<< 1.2-2), libapache2-mod-authn-webid (<< 0~20110301-2), libapache2-mod-authn-yubikey (<< 1.0-1.1), libapache2-mod-authnz-external (<< 3.3.1-0.1), libapache2-mod-authz-unixgroup (<< 1.1.0-0.1), libapache2-mod-axis2c (<< 1.6.0-6), libapache2-mod-bw (<< 0.92-9), libapache2-mod-chroot (<< 0.5-7+deb8), libapache2-mod-dacs (<< 1.4.28b-2), libapache2-mod-defensible (<< 1.4-3.1), libapache2-mod-dnssd (<< 0.6-3.1~), libapache2-mod-encoding (<< 20040616-5.2), libapache2-mod-evasive (<< 1.10.1-2), libapache2-mod-fastcgi (<< 2.4.7~0910052141-1.1), libapache2-mod-fcgid (<< 1:2.3.6-1.3), libapache2-mod-geoip (<< 1.2.8-1), libapache2-mod-gnutls (<< 0.5.10-2), libapache2-mod-jk (<< 1:1.2.37-2), libapache2-mod-layout (<< 5.1-1+deb8), libapache2-mod-ldap-userdir (<< 1.1.19-2), libapache2-mod-line-edit (<< 1.0.0-1+deb8), libapache2-mod-lisp (<< 1.3.1-1.3), libapache2-mod-log-sql (<< 1.100-15), libapache2-mod-macro (<< 1.2.1-1), libapache2-mod-mime-xattr (<< 0.4-5), libapache2-mod-mono (<< 2.11+git20130708.6b73e85-2), libapache2-mod-musicindex (<< 1.4.1-1), libapache2-mod-neko (<< 2.0.0-1), libapache2-mod-nss (<< 1.0.8-3), libapache2-mod-ocamlnet (<< 3.5.1-1+deb8), libapache2-mod-parser3 (<< 3.4.2-7), libapache2-mod-passenger (<< 3.0.13debian-1.1), libapache2-mod-perl2 (<< 2.0.8+httpd24-r1449661-2), libapache2-mod-php5 (<< 5.5.0~beta4-3), libapache2-mod-php5filter (<< 5.5.0~beta4-3), libapache2-mod-proxy-html (<< 1:2.4.9-2), libapache2-mod-python (<< 3.3.1-11), libapache2-mod-qos (<< 10.15-3), libapache2-mod-random (<< 2.1-1+deb8), libapache2-mod-removeip (<< 1.0b-5.1), libapache2-mod-rivet (<< 2.1.1-3), libapache2-mod-rpaf (<< 0.6-11), libapache2-mod-ruby (<< 1.2.6-2+deb8), libapache2-mod-ruid2 (<< 0.9.8-3), libapache2-mod-ruwsgi (<< 1.9.13-1), libapache2-mod-scgi (<< 1.13-1.1), libapache2-mod-shib2 (<< 2.5.2+dfsg-2), libapache2-mod-spamhaus (<< 0.7-1.1), libapache2-mod-speedycgi (<< 2.22-13+deb8), libapache2-mod-suphp (<< 0.7.1-3.1+deb8), libapache2-mod-upload-progress (<< 0.2-1), libapache2-mod-uwsgi (<< 1.9.13-1), libapache2-mod-vhost-hash-alias (<< 1.0-2+deb8), libapache2-mod-vhost-ldap (<< 2.4.0-1), libapache2-mod-wsgi (<< 3.4-2), libapache2-mod-wsgi-py3 (<< 3.4-2), libapache2-mod-xsendfile (<< 0.12-2), libapache2-modsecurity (<< 2.8.0-1), libapache2-reload-perl (<< 0.12-2), libapache2-request-perl (<< 2.13-2), libapache2-svn (<< 1.7.9-1+nmu3), libapache2-webauth (<< 4.2.0-1), libapache2-webkdc (<< 4.2.0-1)
Filename: pool/main/a/apache2/apache2.2-common_2.4.10-1+deb.sury.org~precise+1_amd64.deb
Size: 64028
MD5sum: 605e837e72500c2cb2d7350f384cb9a0
SHA1: 341276f2d0fc2ed08303c060fe85165e8cd2492b
SHA256: e631c20a7f40e4019e431519f532da1e068646c791275d3b4f4052099e025392
Description-en: Transitional package for apache2
 This is a transitional package for apache2-bin, and can be safely removed
 after the installation is complete.
Description-md5: d1a1637f978337732292196147e06d59

Package: apache2.2-common
Priority: optional
Section: web
Installed-Size: 799
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Apache Maintainers <debian-apache@lists.debian.org>
Architecture: amd64
Source: apache2
Version: 2.2.22-1ubuntu1.7
Replaces: apache2-common
Depends: apache2.2-bin (= 2.2.22-1ubuntu1.7), apache2-utils, mime-support, lsb-base, procps, perl
Recommends: ssl-cert
Suggests: www-browser, apache2-doc, apache2-suexec | apache2-suexec-custom, ufw
Conflicts: apache, apache2-common
Filename: pool/main/a/apache2/apache2.2-common_2.2.22-1ubuntu1.7_amd64.deb
Size: 226292
MD5sum: 21f2ca2439c6741626c4a2b796b20a7f
SHA1: 71be3e48515644b3559c1aa6c8204ac0b334e8b0
SHA256: 0a87c2af1745c9976a1879c90de2346c092e80f37fda0a5d0d9163c538d9ac9d
Description-en: Apache HTTP Server common files
 The Apache Software Foundation's goal is to build a secure, efficient and
 extensible HTTP server as standards-compliant open source software. The
 result has long been the number one web server on the Internet.
 .
 This package contains the configuration and support scripts.
 However, it does *not* include the server itself; for this you need to
 install one of the apache2-mpm-* packages, such as worker or prefork.
Homepage: [http://httpd.apache.org/](http://httpd.apache.org/)
Original-Vcs-Browser: [http://anonscm.debian.org/gitweb/?p=pkg-apache/apache2.git](http://anonscm.debian.org/gitweb/?p=pkg-apache/apache2.git)
Original-Vcs-Git: git://git.debian.org/git/pkg-apache/apache2.git
Description-md5: 214ca4adfc4cb3d8083d736c7fe47647
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
Supported: 5y
Task: lamp-server, mythbuntu-frontend, mythbuntu-desktop, mythbuntu-backend-slave, mythbuntu-backend-master, mythbuntu-backend-master

Package: apache2.2-common
Priority: optional
Section: web
Installed-Size: 798
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Apache Maintainers <debian-apache@lists.debian.org>
Architecture: amd64
Source: apache2
Version: 2.2.22-1ubuntu1
Replaces: apache2-common
Depends: apache2.2-bin (= 2.2.22-1ubuntu1), apache2-utils, mime-support, lsb-base, procps, perl
Recommends: ssl-cert
Suggests: www-browser, apache2-doc, apache2-suexec | apache2-suexec-custom, ufw
Conflicts: apache, apache2-common
Filename: pool/main/a/apache2/apache2.2-common_2.2.22-1ubuntu1_amd64.deb
Size: 227924
MD5sum: b261e61225a75ccabd84ae3c2de70cce
SHA1: b5b3d6e0f7a12424d85f1d9a3f8fcb4583e82133
SHA256: 6283baea9ecbb3a27988fabf537fb7549c77c67b31e7d8f9503390a7a0368387
Description-en: Apache HTTP Server common files
 The Apache Software Foundation's goal is to build a secure, efficient and
 extensible HTTP server as standards-compliant open source software. The
 result has long been the number one web server on the Internet.
 .
 This package contains the configuration and support scripts.
 However, it does *not* include the server itself; for this you need to
 install one of the apache2-mpm-* packages, such as worker or prefork.
Homepage: [http://httpd.apache.org/](http://httpd.apache.org/)
Original-Vcs-Browser: [http://anonscm.debian.org/gitweb/?p=pkg-apache/apache2.git](http://anonscm.debian.org/gitweb/?p=pkg-apache/apache2.git)
Original-Vcs-Git: git://git.debian.org/git/pkg-apache/apache2.git
Description-md5: 214ca4adfc4cb3d8083d736c7fe47647
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
Supported: 5y
Task: lamp-server, mythbuntu-frontend, mythbuntu-desktop, mythbuntu-backend-slave, mythbuntu-backend-master, mythbuntu-backend-master

Lot of information there

---

### Post by lisati on 2015-02-25
Is the queued email intended for the same machine? If so, you need to tell Postfix that it accepts mail for *server11362.abc.com*. One way of doing this is with the [mydestination]("http://www.postfix.org/postconf.5.html#mydestination") parameter in main.cf.

If the IP address for server11362.abc.com showing in your logs is incorrect, you might need to review your DNS settings. Setting this is usually independent of your Postfix configuration.

---

### Post by astarmathsandphysics on 2015-02-25
the queued mail is intended for the same machine.
I have changed the desitination 
My log is nowFeb 25 11:48:33 server11362 postfix/local[2994]: 007E4AE335E: ```
to=<theeducationchannel@server11362.abc.com>, orig_to=<theeducationchannel>, relay=local, delay=27751, delays=27728/23/0/0.11, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Feb 25 11:48:33 server11362 postfix/qmgr[2953]: 007E4AE335E: removed
Feb 25 11:48:33 server11362 postfix/smtp[23555]: 8E2DCAE3938: to=<theeducationchannel@server11362.abc.com>, orig_to=<theeducationchannel>, relay=none, delay=31, delays=0.18/0/31/0, dsn=4.4.1, status=deferred (connect to server11362.abc.com[218.93.250.18]:25: Connection timed out)
Feb 25 11:48:33 server11362 postfix/local[2980]: 0E8A4AE32F9: to=<theeducationchannel@server11362.abc.com>, orig_to=<theeducationchannel>, relay=local, delay=29611, delays=29588/23/0/0.09, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Feb 25 11:48:33 server11362 postfix/qmgr[2953]: 0E8A4AE32F9: removed
Feb 25 11:48:33 server11362 postfix/local[2986]: 0304BAE32F0: to=<theeducationchannel@server11362.abc.com>, orig_to=<theeducationchannel>, relay=local, delay=29792, delays=29768/24/0/0.04, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Feb 25 11:48:33 server11362 postfix/qmgr[2953]: 0304BAE32F0: removed
Feb 25 11:48:33 server11362 postfix/local[2994]: 0C45DAE2DB4: to=<theeducationchannel@server11362.abc.com>, orig_to=<theeducationchannel>, relay=local, delay=54992, delays=54968/24/0/0.05, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Feb 25 11:48:33 server11362 postfix/qmgr[2953]: 0C45DAE2DB4: removed
Feb 25 11:48:33 server11362 postfix/local[2980]: 04263AE305A: to=<theeducationchannel@server11362.abc.com>, orig_to=<theeducationchannel>, relay=local, delay=42391, delays=42367/24/0/0.05, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Feb 25 11:48:33 server11362 postfix/qmgr[2953]: 04263AE305A: removed
Feb 25 11:48:33 server11362 postfix/local[2986]: 06A7CAE3219: to=<theeducationchannel@server11362.abc.com>, orig_to=<theeducationchannel>, relay=local, delay=33932, delays=33908/24/0/0.05, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Feb 25 11:48:33 server11362 postfix/qmgr[2953]: 06A7CAE3219: removed
Feb 25 11:48:33 server11362 postfix/local[2980]: 03EFBAE2F72: to=<theeducationchannel@server11362.abc.com>, orig_to=<theeducationchannel>, relay=local, delay=46592, delays=46568/24/0/0.05, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Feb 25 11:48:33 server11362 postfix/qmgr[2953]: 03EFBAE2F72: removed
Feb 25 11:48:33 server11362 postfix/local[2986]: 2261FAE2858: to=<theeducationchannel@server11362.abc.com>, relay=local, delay=7.7, delays=0.13/7.5/0/0.04, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Feb 25 11:48:33 server11362 postfix/qmgr[2953]: 2261FAE2858: removed
Feb 25 11:48:34 server11362 postfix/local[2990]: 13694AE32F5: to=<astarmathsandphysics@server11362.abc.com>, orig_to=<astarmathsandphysics>, relay=local, delay=29672, delays=29648/0.02/0/24, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Feb 25 11:48:34 server11362 postfix/qmgr[2953]: 13694AE32F5: removed
Feb 25 11:48:34 server11362 postfix/local[2963]: 1CBC7AE2E96: to=<theeducationchannel@server11362.abc.com>, orig_to=<theeducationchannel>, relay=local, delay=50792, delays=50768/16/0/8.1, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Feb 25 11:48:34 server11362 postfix/qmgr[2953]: 1CBC7AE2E96: removed
Feb 25 11:49:02 server11362 postfix/pickup[2954]: 2813AAE2863: uid=1007 from=<theeducationchannel>
Feb 25 11:49:02 server11362 postfix/cleanup[19072]: 2813AAE2863: message-id=<20150225114902.2813AAE2863@server11362>
Feb 25 11:49:02 server11362 postfix/qmgr[2953]: 2813AAE2863: from=<theeducationchannel@server11362.abc.com>, size=632, nrcpt=1 (queue active)
Feb 25 11:49:02 server11362 postfix/local[2980]: 2813AAE2863: to=<theeducationchannel@server11362.abc.com>, orig_to=<theeducationchannel>, relay=local, delay=0.23, delays=0.17/0/0/0.05, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Feb 25 11:49:02 server11362 postfix/qmgr[2953]: 2813AAE2863: removed
```

am testing

Extremely suspicious.
The ip is in china

I think it may be to with bind.
I found two files in /bind/
db.111

```
   ;
   ; BIND reverse data file for local loopback interface
   ;
   $TTL    604800
   @       IN      SOA     server11362.abc.hom. root.server11362.freeexampapers.com. (
                          44         ; Serial
                     604800         ; Refresh
                      86400         ; Retry
                    2419200         ; Expire
                     604800 )       ; Negative Cache TTL
   ;
        IN  NS  server11362.
   1    IN  PTR gateway.abc.com.
   92    IN  PTR server11362.abc.com.
```

and db.abc.com

```
;
; BIND data file for local loopback interface
;
$TTL	604800
@	IN	SOA	server.11362.abc.com. root.localhost. (
			     3		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;
@	IN	NS	server.11362.abc.com
@	IN	A	127.0.0.1
@	IN	AAAA	::1

```
; Below are A Record Addresses

server11362	IN	A	111.90.150.92

; Below are the CNAME Record Addresses (Aliases).

Also all the files in /bind/ belong to user root group pulse

---

### Post by lisati on 2015-02-25
> **astarmathsandphysics said:**
> Extremely suspicious.
The ip is in china

...and the other IP address appears to be based in Myanmar. I have a hunch that you are not located in either Myanmar or China.

---

### Post by astarmathsandphysics on 2015-02-25
I cant work out where abc.com is from on my server
that domain is nothing to do with me

---

### Post by lisati on 2015-02-25
> **astarmathsandphysics said:**
> I cant work out where abc.com is from on my server
that domain is nothing to do with me

It might be a good idea to undo any changes you have made that suggest that your machine accepts mail for email addressed to abc.com addresses if you have nothing to do with that domain. Your setup should only reflect domains that you have responsibility for.

---

### Post by astarmathsandphysics on 2015-02-25
I am not accepting any emails for *.abc.com.
the server ip is 111.90.150.92 and is in malaysia

ie my server

---

### Post by lisati on 2015-02-25
> **astarmathsandphysics said:**
> I cant work out where abc.com is from on my server
that domain is nothing to do with me

> **astarmathsandphysics said:**
> I am not accepting any emails for *.abc.com.
the server ip is 111.90.150.92 and is in malaysia

My apologies: nicotine withdrawal was getting the better of me earlier.

Try editing your /etc/hosts file to remove the reference to abc.com. I'm not familiar with configuring BIND, so someone else will have to assist in fixing the entries there.

---

### Post by astarmathsandphysics on 2015-02-25
I did that already.

The only ref to abc.com I can find is in /bind/ folder
I uninstalled bind9 and the files in /bind/ are not being used

Ichanged the fully qualified domain name to server.11362.xxxxxxxrs.xom but the ip address 218.93.250.18 is still in the logs

Feb 26 15:00:02 server11362 postfix/error[7704]: 8FB9CAE6A4A: to=<theeducationchannel@server11362.frxxxxxers.com>, orig_to=<theeducationchannel>, relay=none, delay=0.78, delays=0.75/0/0/0.04, dsn=4.4.1, status=deferred (delivery temporarily suspended: connect to server11362.frexxxxxxxxm[218.93.250.18]:25: Connection timed out)

I think I fixed it,
In the database I was using to store the virtual domins, users and passwords, one of the entries was server.11362.abc.com.
Seems ok now.

---

